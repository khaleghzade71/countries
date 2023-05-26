<template>
  <div class="input">
    <input
      :placeholder="placeholder"
      class="input__text"
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
    />
    <font-awesome-icon :style="{ color: 'gray' }" :icon="icon" />
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
  box-shadow: var(--boxShadow);
  width: 500px;
  padding: 16px 24px;
  display: flex;
  border-radius: 4px;
  display: flex;
  flex-direction: row-reverse;
  input {
    background: inherit;
  }
  &__text {
    flex-grow: 1;
    margin-left: 20px;
  }
  @media (max-width: 768px) {
    width: 300px;
  }
}
</style>
