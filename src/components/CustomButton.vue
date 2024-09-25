<script setup lang="ts">
import ArrowIcon from '@assets/images/icon-arrow.svg'
</script>

<template>
  <button class="button">
    <div class="button__label">shop now</div>
    <ArrowIcon class="button__icon" />
  </button>
</template>

<style scoped lang="scss">
@import '@styles/base.scss';

.button {
  display: flex;
  gap: 20px;
  width: fit-content;
  align-items: center;
  background: transparent;
  border: none;
  margin-top: 1rem;
  transition: all 0.3s ease;

  &:hover {
    transform: translateX(10px);
    color: $color-dark-gray;

    .button__icon {
      fill: $color-dark-gray;
    }
  }
}

.button__label {
  text-transform: uppercase;
  font-weight: bold;
  letter-spacing: 0.5rem;
}

.button__icon {
  transition: fill 0.3s ease;
}
</style>
