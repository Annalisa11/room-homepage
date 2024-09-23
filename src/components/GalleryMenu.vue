<script setup lang="ts">
import { ref } from 'vue'

const navItems = ref<string[]>(['Home', 'Shop', 'About', 'Contact'])

import { Swiper, SwiperSlide } from 'swiper/vue'
import type { Swiper as SwiperInstance } from 'swiper'
import { Navigation, Pagination, Scrollbar, A11y, Autoplay } from 'swiper/modules'

import HamburgerIcon from '../assets/images/icon-hamburger.svg'
import CloseIcon from '../assets/images/icon-close.svg'

// Import Swiper styles
import 'swiper/css'
import 'swiper/css/navigation'
import 'swiper/css/pagination'
import 'swiper/css/scrollbar'
const modules = [Navigation, Pagination, Scrollbar, A11y, Autoplay]
const images = ref<string[]>([
  'desktop-image-hero-1.jpg',
  'desktop-image-hero-2.jpg',
  'desktop-image-hero-3.jpg'
])
const onSwiper = (swiper: SwiperInstance) => {
  swiperRef.value = swiper
}

const onSlideChange = () => {
  console.log('slide change')
}

const swiperRef = ref<SwiperInstance | null>(null)
const navigateToSlide = (index: number) => {
  if (swiperRef.value) {
    swiperRef.value.slideTo(index)
  }
}

const navOpen = ref(false)
console.log('navOpen: ', navOpen)

// defineExpose({ navigateToSlide })
</script>

<template>
  <div class="gallery">
    <header>
      <div id="sidemenu">
        <button
          class="sidemenu__btn"
          v-on:click="navOpen = !navOpen"
          v-bind:class="{ active: navOpen }"
        >
          <transition name="scale">
            <HamburgerIcon class="hamburger" v-show="!navOpen" />
          </transition>
          <transition name="translateX">
            <CloseIcon class="close" v-show="navOpen" />
          </transition>
        </button>
        <transition name="translateX">
          <nav v-show="navOpen" class="nav">
            <div class="sidemenu__wrapper">
              <ul class="sidemenu__items">
                <li class="sidemenu__item" v-for="(navItem, index) in navItems" :key="index">
                  <a href="#" @click="navigateToSlide(index)">
                    {{ navItem }}
                  </a>
                  <div class="nav__border link"></div>
                </li>
              </ul>
            </div>
          </nav>
        </transition>
      </div>
      <a href="#" class="logo">room</a>
      <!-- <nav>
        <ul class="nav__items">
          <li class="nav__item" v-for="(navItem, index) in navItems" :key="index">
            <a href="#" @click="navigateToSlide(index)">
              {{ navItem }}
            </a>
            <div class="nav__border link"></div>
          </li>
        </ul>
      </nav> -->
    </header>
    <swiper
      ref="swiperRef"
      :modules="modules"
      :slides-per-view="1"
      @swiper="onSwiper"
      @slideChange="onSlideChange"
      :autoplay="{ delay: 5000 }"
    >
      <swiper-slide v-for="image in images" :key="image">
        <img :src="`./images/${image}`" alt="Gallery Image" />
      </swiper-slide>
    </swiper>
  </div>
</template>
<style scoped lang="scss">
.gallery {
  background-image: url('../assets/images/desktop-image-hero-1.jpg');
  background-size: cover;
  grid-area: gallery;
  padding: 2rem;
  position: relative;
}
header {
  display: flex;
  align-items: baseline;
  color: white;
  position: relative;
  z-index: 100;

  .logo {
    font-size: xx-large;
    margin-right: 1rem;
  }
}
a {
  text-decoration: none;
}
// .nav {
//   &__items {
//     display: flex;
//     gap: 1.4rem;
//     list-style: none;
//   }

//   &__item {
//     position: relative;
//     display: flex;
//     justify-content: center;
//     color: white;

//     // Add hover on .nav__item to target .nav__border
//     &:hover .nav__border {
//       border-bottom: 2px solid white;
//     }
//   }

//   &__border {
//     position: absolute;
//     top: 0;
//     width: 70%;
//     height: calc(100% + 5px);
//   }
// }
img {
  height: 100%;
  width: 100%;
  object-fit: cover;
}

.swiper {
  position: absolute;
  inset: 0;
}

///////////////////////////

#sidemenu {
  .nav {
    // height: calc(100% - #{$headerHeight} - #{$footerHeight});
    background: white;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 99;
    // box-shadow: 2px 0 3px$grey-6;
    // overflow-y: scroll;
  }
  .sidemenu {
    &__wrapper {
      background-color: white;
    }

    &__btn {
      display: flex;
      width: 50px;
      height: 50px;
      border: none;
      background-color: transparent;
      position: relative;
      z-index: 100;
      appearance: none;

      justify-content: center;
      align-items: center;
    }

    &__wrapper {
      padding: 50px;
      padding-left: 0;
      display: flex;
      justify-content: flex-end;
    }

    &__items {
      display: flex;
      gap: 1.4rem;
      list-style: none;
      padding-top: 50px;
      list-style: none;
      padding: 0;
      margin: 0;
      width: fit-content;
    }

    &__item {
      position: relative;
      display: flex;
      justify-content: center;
    }

    &__item {
      a {
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

.translateX-enter {
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

.scale-enter-from,
.scale-leave-to {
  width: 0;
}

.scale-enter-active,
.scale-leave-active {
  transition: 1s ease-in-out;
}

.scale-enter-to,
.scale-leave-from {
  width: 100%;
}
</style>
