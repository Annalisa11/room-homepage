<script setup lang="ts">
import { ref } from 'vue'
import HamburgerIcon from '@assets/images/icon-hamburger.svg'
import CloseIcon from '@assets/images/icon-close.svg'
import '@styles/NavigationMenu.scss'

interface NavigationMenuProps {
  onMenuItemClick: (index: number) => void
}

const { onMenuItemClick } = defineProps<NavigationMenuProps>()

const navOpen = ref(false)

const toggleNav = () => {
  navOpen.value = !navOpen.value
}

const navItems = ref<string[]>(['Home', 'Shop', 'About', 'Contact'])
</script>

<template>
  <header>
    <!-- Mobile Menu -->
    <div id="mobile-menu" class="show-on-mobile">
      <div class="nav__container">
        <button
          class="nav__menu-btn"
          v-on:click="toggleNav"
          v-bind:class="{ 'nav__menu-btn--active': navOpen }"
        >
          <transition name="scale">
            <HamburgerIcon class="nav__icon nav__icon--hamburger" v-show="!navOpen" />
          </transition>
          <transition name="scale">
            <CloseIcon class="nav__icon nav__icon--close" v-show="navOpen" />
          </transition>
        </button>
        <a href="#" class="nav__logo">room</a>
        <transition name="translateX">
          <nav v-show="navOpen" class="nav">
            <div class="nav__wrapper">
              <ul class="nav__items">
                <li class="nav__item" v-for="(navItem, index) in navItems" :key="index">
                  <a href="#" @click="onMenuItemClick(index)" class="nav__link">
                    {{ navItem }}
                  </a>
                </li>
              </ul>
            </div>
          </nav>
        </transition>
      </div>
    </div>

    <!-- Desktop Menu -->
    <div id="desktop-menu" class="show-on-desktop">
      <div class="nav__container">
        <a href="#" class="nav__logo">room</a>
        <nav class="nav">
          <ul class="nav__items">
            <li class="nav__item" v-for="(navItem, index) in navItems" :key="index">
              <a href="#" @click="onMenuItemClick(index)" class="nav__link">
                {{ navItem }}
              </a>
              <div class="nav__border link"></div>
            </li>
          </ul>
        </nav>
      </div>
    </div>
  </header>
</template>
