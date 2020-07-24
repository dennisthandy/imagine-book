<template>
  <div class="nav">
    <div class="nav__navbar">
      <router-link to="/" class="nav__link">Home</router-link>
      <router-link to="/about" class="nav__link">About</router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: "navigation-bar",
};
</script>

<style scoped lang="scss">
.nav {
  height: 3.5rem;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 3px 3px 0 rgba($color: #000000, $alpha: 0.7);

  &__navbar {
    width: 100% - 50%;
    display: flex;
    justify-content: space-around;
  }

  &__link {
    color: green;
    text-decoration: none;
  }
}
</style>
