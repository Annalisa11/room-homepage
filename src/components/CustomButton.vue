<script setup lang="ts">
import ArrowIcon from '@assets/images/icon-arrow.svg'
</script>

<template>
  <button class="button">
    <div class="label">shop now</div>
    <ArrowIcon class="icon" />
  </button>
</template>

<style lang="scss" scoped>
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

    .icon {
      fill: $color-dark-gray;
    }
  }
}

.label {
  text-transform: uppercase;
  font-weight: bold;
  letter-spacing: 0.5rem;
}
</style>
