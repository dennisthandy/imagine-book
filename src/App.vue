<template>
 <div id="app">
  <navigation-bar></navigation-bar>
  <router-view />
 </div>
</template>

<script>
import NavigationBar from "@/components/NavigationBar.vue";
export default {
 components: {
  NavigationBar,
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
