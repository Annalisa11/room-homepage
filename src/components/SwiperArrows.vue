<script setup lang="ts">
import LeftChevron from '@assets/images/icon-angle-left.svg'
import RightChevron from '@assets/images/icon-angle-right.svg'
import '@styles/base.scss'
import '@styles/SwiperArrows.scss'

interface ComponentProps {
  showOnMobile: boolean
  navigateOneSlide: (toTheRight: boolean) => void
}

const { showOnMobile, navigateOneSlide } = defineProps<ComponentProps>()
</script>

<template>
  <div :class="showOnMobile ? 'show-on-mobile' : 'show-on-desktop'">
    <div :class="['swiper-arrows', showOnMobile ? 'swiper-arrows--right-position' : '']">
      <div class="swiper-arrows__left link" @click="navigateOneSlide(false)">
        <LeftChevron />
      </div>
      <div class="swiper-arrows__right link" @click="navigateOneSlide(true)">
        <RightChevron />
      </div>
    </div>
  </div>
</template>
