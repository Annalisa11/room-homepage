<script setup lang="ts">
import ArrowIcon from '../assets/images/icon-arrow.svg'
</script>

<template>
  <button class="button">
    <div class="label">shop now</div>
    <ArrowIcon />
  </button>
</template>

<style lang="scss" scoped>
.button {
  display: flex;
  gap: 20px;
  width: fit-content;
  padding: 0.5rem 1rem;
  align-items: center;

  &:hover {
    cursor: pointer;
  }
}

.label {
  text-transform: uppercase;
  letter-spacing: 0.5rem;
}
</style>
