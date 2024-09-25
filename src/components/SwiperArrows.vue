<script setup lang="ts">
import LeftChevron from '@assets/images/icon-angle-left.svg'
import RightChevron from '@assets/images/icon-angle-right.svg'
import '@styles/base.scss'

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

<style scoped lang="scss">
.arrows {
  color: white;
  display: flex;
  width: fit-content;

  &.right-position {
    position: absolute;
    bottom: 0;
    right: 0;
    z-index: 100;
  }
}

.left,
.right {
  width: 80px;
  height: 80px;
  display: flex;
  justify-content: center;
  align-items: center;
  background: black;

  &.right-position {
    z-index: inherit;
  }

  &:hover {
    background-color: grey;
  }
}
</style>
