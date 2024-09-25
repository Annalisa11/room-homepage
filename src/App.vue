<script setup lang="ts">
import '@styles/App.scss'
import Gallery from '@components/GalleryMenu.vue'
import CustomButton from '@components/CustomButton.vue'
import '@styles/base.scss'
import SwiperArrows from '@components/SwiperArrows.vue'

import { ref } from 'vue'
import type { Swiper as SwiperInstance } from 'swiper'

const swiperRef = ref<SwiperInstance | null>(null)
const onSwiper = (swiper: SwiperInstance) => {
  swiperRef.value = swiper
}

const navigateToSlide = (index: number) => {
  if (swiperRef.value) {
    swiperRef.value.slideTo(index)
  }
}

const navigateOneSlide = (toTheRight: boolean) => {
  if (swiperRef.value) {
    toTheRight ? swiperRef.value.slideNext() : swiperRef.value.slidePrev()
  }
}
</script>

<template>
  <div class="grid">
    <Gallery
      :on-swiper="onSwiper"
      :navigate-to-slide="navigateToSlide"
      :navigate-one-slide="navigateOneSlide"
    />
    <section class="content">
      <div class="text-section">
        <h1>Discover innovative ways to decorate</h1>
        <p>
          We provide unmatched quality, comfort, and style for property owners across the country.
          Our experts combine form and function in bringing your vision to life. Create a room in
          your own style with our collection and make your property a reflection of you and what you
          love.
        </p>
        <CustomButton />
      </div>

      <SwiperArrows :navigate-one-slide="navigateOneSlide" :show-on-mobile="false" />
    </section>

    <img src="@assets/images/image-about-dark.jpg" id="image-one" />
    <section class="content-two text-section compact">
      <h2>About our furniture</h2>
      <p>
        Our modern furniture store provide a high level of quality. Our company has invested in
        advanced technology to ensure that every product is made as perfect and as consistent as
        possible. With three decades of experience in this industry, we understand what customers
        want for their home and office.
      </p>
    </section>

    <img src="@assets/images/image-about-light.jpg" id="image-two" />
  </div>
</template>
