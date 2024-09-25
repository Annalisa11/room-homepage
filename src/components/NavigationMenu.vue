<script setup lang="ts">
import { ref } from 'vue'
import HamburgerIcon from '@assets/images/icon-hamburger.svg'
import CloseIcon from '@assets/images/icon-close.svg'

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

<style scoped lang="scss">
.nav__container {
  display: flex;
  color: white;
  position: relative;
  z-index: 100;
}

.nav__logo {
  font-size: x-large;
  color: white;
}

.swiper {
  position: absolute;
  inset: 0;
}

#desktop-menu {
  .nav__container {
    align-items: baseline;
  }

  .nav__logo {
    margin-right: 1rem;
  }

  .nav {
    &__items {
      display: flex;
      gap: 1.4rem;
      list-style: none;
    }

    &__item {
      position: relative;
      display: flex;
      justify-content: center;
      color: white;

      &:hover .nav__border {
        border-bottom: 2px solid white;
      }

      .nav__link {
        text-decoration: none;
        color: white;
      }
    }

    &__border {
      position: absolute;
      top: 0;
      width: 70%;
      height: calc(100% + 5px);
      z-index: -1;
    }
  }
}

// Mobile Menu Styles
#mobile-menu {
  .nav__container {
    align-items: center;
    padding: 2rem;
  }

  .nav__logo {
    display: flex;
    width: 100%;
    margin-right: 50px;
    justify-content: center;
    align-items: center;
  }

  .nav {
    background: white;
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    z-index: 99;

    &__wrapper {
      background-color: white;
      padding: 2rem;
      padding-left: 0;
      display: flex;
      justify-content: flex-end;
    }

    &__menu-btn {
      display: flex;
      width: 40px;
      height: 40px;
      border: none;
      background-color: transparent;
      position: relative;
      z-index: 100;
      appearance: none;
      justify-content: center;
      align-items: center;

      .nav__icon {
        position: absolute;
        height: inherit;
      }
    }

    &__items {
      display: flex;
      gap: 1.4rem;
      list-style: none;
      padding-top: 50px;
      padding: 0;
      margin: 0;
      width: fit-content;

      .nav__item {
        .nav__link {
          text-decoration: none;
          line-height: 1.6em;
          font-size: 1rem;
          padding: 0.5em;
          display: block;
          color: black;
          transition: 0.4s ease;

          &:hover {
            background: lightgrey;
            color: dimgrey;
          }
        }
      }
    }
  }
}

// Hamburger to Close Icon Animation
.scale-enter-active,
.scale-leave-active {
  transition: transform 0.2s ease;
}

.scale-enter-from,
.scale-leave-to {
  transform: scale(0);
}

.scale-enter-to,
.scale-leave-from {
  transform: scale(1);
}

// Menu sliding in from the left animation

.translateX-enter-from {
  transform: translateX(-200px);
  opacity: 0;
}

.translateX-enter-active,
.translateX-leave-active {
  transform-origin: top left 0;
  transition: 0.2s ease;
}

.translateX-leave-to {
  transform: translateX(-200px);
  opacity: 0;
}
</style>
