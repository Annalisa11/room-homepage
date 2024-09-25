<script setup lang="ts">
import SwiperArrows from '@components/SwiperArrows.vue'
import NavigationMenu from '@components/NavigationMenu.vue'
import GallerySwiper from '@components/GallerySwiper.vue'
import { Swiper as SwiperInstance } from 'swiper'
import '@styles/base.scss'
import '@styles/GalleryMenu.scss'

interface GalleryMenuProps {
  onSwiper: (swiper: SwiperInstance) => void
  navigateToSlide: (index: number) => void
  navigateOneSlide: (toTheRight: boolean) => void
}

const { onSwiper, navigateToSlide, navigateOneSlide } = defineProps<GalleryMenuProps>()

const onMenuItemClick = (index: number) => {
  navigateToSlide(index)
}
</script>

<template>
  <div class="gallery">
    <NavigationMenu :on-menu-item-click="onMenuItemClick" />
    <GallerySwiper :on-swiper="onSwiper" />
    <SwiperArrows :navigate-one-slide="navigateOneSlide" :show-on-mobile="true" />
  </div>
</template>

<style scoped lang="scss">
@import '@styles/base.scss';

.gallery {
  &__swiper {
    position: relative;
  }
}
</style>
