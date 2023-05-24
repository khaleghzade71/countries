<template>
  <NuxtLink :to="to" style="text-decoration: none; color: inherit">
    <span class="tag">
      {{ title }}
    </span>
  </NuxtLink>
</template>

<script setup>
const props = defineProps({
  title: { type: String },
  to: { type: String },
});
</script>

<style lang="scss" scoped>
.tag {
  padding: 5px 15px;
  background: hsl(0, 0%, 100%);
  box-shadow: rgba(0, 0, 0, 0.1) 0px 2px 12px;
  border-radius: 4px;
  width: fit-content;
  font-size: 0.75rem;
}
</style>
