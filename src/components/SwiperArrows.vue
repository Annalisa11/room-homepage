<script setup lang="ts">
import LeftChevron from '@assets/images/icon-angle-left.svg'
import RightChevron from '@assets/images/icon-angle-right.svg'
import '@styles/base.scss'
import '@styles/SwiperArrows.scss'

interface ComponentProps {
  showOnMobile: boolean
  navigateOneSlide: (toTheRight: boolean) => void
}

const { navigateOneSlide } = defineProps<ComponentProps>()
</script>

<template>
  <div :class="showOnMobile ? 'show-on-mobile ' : 'show-on-desktop'">
    <div :class="['arrows link', showOnMobile ? 'right-position' : '']">
      <div class="left" @click="navigateOneSlide(false)">
        <LeftChevron />
      </div>
      <div class="right" @click="navigateOneSlide(true)">
        <RightChevron />
      </div>
    </div>
  </div>
</template>
