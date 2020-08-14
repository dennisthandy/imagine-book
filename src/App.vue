<template>
  <div id="app" class="bg-purple-500">
    <navigation-bar :sliderState="slider"></navigation-bar>
    <router-view :sliderState="slider" @setSliderState="setSliderState" />
  </div>
</template>

<script>
import NavigationBar from "@/components/NavigationBar.vue";
export default {
  components: {
    NavigationBar,
  },
  data() {
    return {
      slider: false,
    };
  },
  methods: {
    setSliderState() {
      this.slider = true;
    },
  },
  created() {
    const sliderState = localStorage.getItem("slider");
    sliderState ? (this.slider = true) : (this.slider = false);
  },
};
</script>

<style>
*,
*::after,
*::before {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
}
</style>
