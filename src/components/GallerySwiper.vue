<script setup lang="ts">
import { Swiper, SwiperSlide } from 'swiper/vue'
import type { Swiper as SwiperInstance } from 'swiper'
import { Navigation, Pagination, Scrollbar, A11y, Autoplay } from 'swiper/modules'
import 'swiper/css'
import 'swiper/css/navigation'
import 'swiper/css/pagination'
import '@styles/base.scss'

interface GallerySwiperProps {
  onSwiper: (swiper: SwiperInstance) => void
}

const { onSwiper } = defineProps<GallerySwiperProps>()
const images = ['desktop-image-hero-1.jpg', 'desktop-image-hero-2.jpg', 'desktop-image-hero-3.jpg']
const modules = [Navigation, Pagination, Scrollbar, A11y, Autoplay]
</script>

<template>
  <swiper :modules="modules" :slides-per-view="1" @swiper="onSwiper" :autoplay="{ delay: 5000 }">
    <swiper-slide v-for="image in images" :key="image">
      <img :src="`./images/${image}`" alt="Gallery Image" />
    </swiper-slide>
  </swiper>
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
</style>
