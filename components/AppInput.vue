<template>
  <div class="input">
    <font-awesome-icon :style="{ color: 'gray' }" :icon="icon" />
    <input
      :placeholder="placeholder"
      class="input__text"
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
    />
  </div>
</template>

<script setup>
const props = defineProps({
  modelValue: { type: String },
  placeholder: { type: String },
  icon: { type: String },
});
</script>

<style lang="scss" scoped>
.input {
  background: var(--element);
  box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 12px;
  width: 300px;
  padding: 10px 20px;
  display: flex;
  border-radius: 4px;
  input {
    background: inherit;
  }
  &__text {
    flex-grow: 1;
    margin-left: 20px;
  }
}
</style>
