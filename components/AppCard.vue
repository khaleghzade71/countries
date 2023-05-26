<template>
  <div class="card">
    <img class="card__img" :src="src" />
    <div class="card__text">
      <p class="card__title">{{ title }}</p>
      <div v-for="(value, key) in details" :key="key">
        <div class="card__details">
          <p class="card__key">{{ key }} :</p>
          <p class="card__value">{{ value }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  src: { type: String, required: true },
  title: { type: String, required: true },
  details: { type: Object, required: true },
});
</script>

<style lang="scss" scoped>
.card {
  background: var(--element);
  box-shadow: var(--boxShadow);
  min-width: 300px;
  border-radius: 4px;
  &__img {
    width: 100%;
    height: 150px;
    object-fit: cover;
    border-radius: 4px;
  }
  &__text {
    padding: 10px 20px;
    line-height: 0.5rem;
  }
  &__title {
    font-weight: 800;
  }
  &__details {
    display: flex;
    font-size: 0.75rem;
  }
  &__key {
    font-weight: 800;
  }
}
</style>
