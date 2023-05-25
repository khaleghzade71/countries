<template>
  <div data-theme="light">
    <TheHeader />
    <div class="container">
      <NuxtPage />
    </div>
  </div>
</template>

<style lang="scss" scoped>
.container {
  padding: 40px 60px;
  @media (max-width: 992px) {
    padding: 20px;
  }
}
</style>
