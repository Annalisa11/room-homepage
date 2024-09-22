<script setup lang="ts">
import { ref } from 'vue'

const navItems = ref<string[]>(['Home', 'Shop', 'About', 'Contact'])

import { Swiper, SwiperSlide } from 'swiper/vue'
import type { Swiper as SwiperInstance } from 'swiper'
import { Navigation, Pagination, Scrollbar, A11y, Autoplay } from 'swiper/modules'

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

// defineExpose({ navigateToSlide })
</script>

<template>
  <div class="gallery">
    <header>
      <a href="#" class="logo">room</a>
      <nav>
        <ul class="nav__items">
          <li class="nav__item" v-for="(navItem, index) in navItems" :key="index">
            <a href="#" @click="navigateToSlide(index)">
              {{ navItem }}
            </a>
            <div class="nav__border link"></div>
          </li>
        </ul>
      </nav>
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
  color: white;
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

    // Add hover on .nav__item to target .nav__border
    &:hover .nav__border {
      border-bottom: 2px solid white;
    }
  }

  &__border {
    position: absolute;
    top: 0;
    width: 70%;
    height: calc(100% + 5px);
  }
}
img {
  height: 100%;
  width: 100%;
  object-fit: cover;
}

.swiper {
  position: absolute;
  inset: 0;
}
</style>
