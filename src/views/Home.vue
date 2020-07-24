<template>
  <div class="home">
    <input type="text" placeholder="Cari . . ." class="home__search" />
    <cover-slider :slider="slider" @openSlider="openSlider"></cover-slider>
    <div class="cards">
      <card></card>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import CoverSlider from "../components/CoverSlider";
import Card from "../components/Card";

export default {
  name: "Home",
  components: {
    CoverSlider,
    Card,
  },
  data() {
    return {
      slider: false,
    };
  },
  methods: {
    openSlider() {
      this.slider = !this.slider;
      localStorage.setItem("slider", this.slider);
    },
  },
  created() {
    const sliderState = localStorage.getItem("slider");
    sliderState ? (this.slider = true) : (this.slider = false);
  },
};
</script>

<style scoped lang="scss">
.home {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  &__search {
    margin: 2.5rem;
    width: 75%;
    padding: 0.75rem;
    border-radius: 0.5rem;
    border: 1px solid blue;
    box-shadow: 3px 3px 0 rgba($color: #000000, $alpha: 0.7);
    font-size: 12pt;
  }
}
</style>
