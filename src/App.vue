<script setup lang="ts">
import './App.scss'
import Gallery from './components/GalleryMenu.vue'
import CustomButton from './components/CustomButton.vue'
</script>

<template>
  <div class="grid">
    <Gallery />
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

      <div class="arrows">
        <div class="left">back</div>
        <div class="right">next</div>
      </div>
    </section>

    <img src="./assets/images/image-about-dark.jpg" id="image-one" />
    <section class="content-two text-section">
      <p>
        Our modern furniture store provide a high level of quality. Our company has invested in
        advanced technology to ensure that every product is made as perfect and as consistent as
        possible. With three decades of experience in this industry, we understand what customers
        want for their home and office.
      </p>
    </section>

    <img src="./assets/images/image-about-light.jpg" id="image-two" />
  </div>
</template>
