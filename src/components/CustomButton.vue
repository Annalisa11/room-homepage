<script setup lang="ts">
import ArrowIcon from '../assets/images/icon-arrow.svg'
</script>

<template>
  <button class="button">
    <div class="label">shop now</div>
    <ArrowIcon class="icon" />
  </button>
</template>

<style lang="scss" scoped>
.button {
  display: flex;
  gap: 20px;
  width: fit-content;
  align-items: center;
  background: transparent;
  border: none;
  margin-top: 1rem;

  &:hover {
    color: grey;

    .icon {
      fill: grey;
    }
  }
}

.label {
  text-transform: uppercase;
  font-size: bold;
  letter-spacing: 0.5rem;
}
</style>
