<template>
  <div
    v-if="sliderState"
    class="nav bg-white relative flex justify-center md:justify-between lg:justify-between items-center h-16 z-10 shadow-xl"
  >
    <div class="nav__brand hidden md:block lg:block ml-8 font-bold text-purple-600">
      <h3>IMAGINE SQUAD 2016</h3>
    </div>
    <div class="nav__navbar w-2/4 md:w-1/4 lg:w-1/4 flex justify-around">
      <router-link
        to="/"
        class="nav__link font-bold text-blue-500 no-underline focus:text-purple-500"
      >Home</router-link>
      <router-link
        to="/about"
        class="nav__link font-bold text-blue-500 no-underline focus:text-purple-500"
      >About</router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: "navigation-bar",
  props: {
    sliderState: {
      type: Boolean,
      required: true,
    },
  },
};
</script>
