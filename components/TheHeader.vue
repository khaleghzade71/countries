<template>
  <div class="header">
    <p class="header__title">Where in the world?</p>
    <AppButton
      @click="toggleTheme()"
      class="header__mode"
      id="theme-toggle"
      title="Dark Mode"
    ></AppButton>
  </div>
</template>

<script setup>
const toggleTheme = () => {
  let currentTheme =
    document.documentElement.getAttribute("data-theme") || "light";

  let targetTheme = currentTheme === "light" ? "dark" : "light";

  document.documentElement.setAttribute("data-theme", targetTheme);
};
</script>

<style lang="scss" scoped>
.header {
  background: var(--element);
  display: flex;
  align-items: center;
  box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 12px;
  justify-content: space-between;
  padding: 0px 40px;
  @media (max-width: 480px) {
    padding: 0 20px;
  }
  &__title {
    font-weight: 800;
    font-size: 1.4rem;
  }
  &__mode {
    font-weight: 600;
  }
}
</style>
