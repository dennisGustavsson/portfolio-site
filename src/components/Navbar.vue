<template>
  <nav>
    <div class="navbar">
      <RouterLink class="link" to="/">Home</RouterLink>
      <!-- <RouterLink class="link" to="/about">About</RouterLink> -->
    </div>
  </nav>
</template>

<style lang="scss" scoped>
.navbar {
  position: fixed;
  top: 0;
  display: flex;
  justify-content: center;
  width: 100%;
  z-index: 2;
  background-color: transparent;

  .link {
    margin-inline: 5px;
  }
}
</style>
