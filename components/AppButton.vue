<template>
  <span class="button">
    <font-awesome-icon :style="{ color: 'gray' }" :icon="icon" />
    <button>
      {{ title }}
    </button>
  </span>
</template>

<script setup>
const props = defineProps({
  title: { type: String },
  icon: { type: String },
});
</script>

<style lang="scss" scoped>
.button {
  padding: 10px 20px;
  background: var(--element);
  box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 12px;
  border-radius: 4px;
  width: fit-content;
  button {
    background: inherit;
  }
}
</style>
