<script setup lang="ts">
import { ref } from 'vue'

const navItems = ref(['Home', 'Shop', 'About', 'Contact'])
</script>

<template>
  <div class="grid">
    <header>
      <nav>
        <a href="#">room</a>
        <ul class="nav__items">
          <li class="nav__item" v-for="(navItem, index) in navItems" :key="index">
            {{ navItem }}
          </li>
        </ul>
      </nav>
    </header>

    <section class="content">
      <div class="text-section">
        <p>
          Discover innovative ways to decorate We provide unmatched quality, comfort, and style for
          property owners across the country. Our experts combine form and function in bringing your
          vision to life. Create a room in your own style with our collection and make your property
          a reflection of you and what you love. Shop now We are available all across the globe With
          stores all over the world, it's easy for you to find furniture for your home or place of
          business. Locally, we’re in most major cities throughout the country. Find the branch
          nearest you using our store locator. Any questions? Don't hesitate to contact us today.
        </p>
        <button>Click here</button>
      </div>

      <div class="arrows">
        <div class="left"><</div>
        <div class="right">></div>
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

<style scoped lang="scss">
header {
  background-image: url('./assets/images/desktop-image-hero-1.jpg');
  background-size: cover;
  grid-area: gallery;
}

img {
  height: 100%;
  width: 100%;
  object-fit: cover;
}

.arrows {
  background: black;
  color: white;
  display: flex;
  width: fit-content;
}
.left,
.right {
  width: 80px;
  height: 80px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.text-section {
  padding: 2rem;
}

.content {
  grid-area: content;
}
.content-two {
  grid-area: content2;
}
#image-one {
  grid-area: image1;
}

#image-two {
  grid-area: image2;
}
.nav {
  &__items {
    display: flex;
    gap: 1rem;
    list-style: none;
  }
}

.grid {
  display: grid;
  min-height: 100vh;
  grid-template-columns: repeat(7, 1fr);
  grid-template-rows: auto;
  gap: 0px 0px;
  grid-template-areas:
    'gallery gallery gallery gallery content content content'
    'image1 image1 content2 content2 content2 image2 image2';
}

@media (max-width: 879px) {
  .grid {
    grid-template-columns: 1fr;
    grid-template-rows: auto;
    grid-template-areas:
      'gallery'
      'content'
      'image1'
      'content2'
      'image2';
  }
}
</style>
