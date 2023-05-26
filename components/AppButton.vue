<template>
  <button class="button">
    {{ title }}
    <font-awesome-icon :style="{ color: 'gray' }" :icon="icon" />
  </button>
</template>

<script setup>
const props = defineProps({
  title: { type: String },
  icon: { type: String },
});
</script>

<style lang="scss" scoped>
.button {
  display: flex;
  flex-direction: row-reverse;
  cursor: pointer;
  grid-gap: 10px;
  padding: 10px 20px;
  background: var(--element);
  box-shadow: var(--boxShadow);
  border-radius: 4px;
  width: fit-content;
}
</style>
