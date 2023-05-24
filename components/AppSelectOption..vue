<template>
  <select
    class="select"
    :value="modelValue"
    @change="$emit('update:modelValue', $event.target.value)"
  >
    <option value="" disabled selected hidden>Filter by Region</option>
    <option v-for="option in options" :key="option" :value="option">
      {{ option }}
    </option>
  </select>
</template>

<script setup>
const props = defineProps({
  options: { type: Array },
  modelValue: { type: String },
});
</script>

<style lang="scss" scoped>
.select {
  background: hsl(0, 0%, 100%);
  box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 12px;
  padding: 10px;
}
</style>
