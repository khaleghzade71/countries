<template>
  <div class="header">
    <p class="header__title">Where in the world?</p>
    <p class="header__mode">Dark Mode</p>
  </div>
</template>

<style lang="scss" scoped>
.header {
  background: hsl(0, 0%, 100%);
  display: flex;
  align-items: center;
  box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 12px;
  padding: 0px 40px;
  justify-content: space-between;
  &__title {
    font-weight: 800;
    font-size: 1.4rem;
  }
  &__mode {
    font-weight: 600;
  }
}
</style>
