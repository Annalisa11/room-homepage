<script setup lang="ts">
import { ref } from 'vue'

const navItems = ref(['Home', 'Shop', 'About', 'Contact'])
</script>

<template>
  <div class="gallery">
    <header>
      <a href="#" class="logo">room</a>
      <nav>
        <ul class="nav__items">
          <li class="nav__item" v-for="(navItem, index) in navItems" :key="index">
            <a href="#">
              {{ navItem }}
            </a>
          </li>
        </ul>
      </nav>
    </header>
  </div>
</template>
<style scoped lang="scss">
.gallery {
  background-image: url('../assets/images/desktop-image-hero-1.jpg');
  background-size: cover;
  grid-area: gallery;
  padding: 2rem;
}
header {
  display: flex;
  align-items: baseline;
  color: white;

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
}
img {
  height: 100%;
  width: 100%;
  object-fit: cover;
}
</style>
