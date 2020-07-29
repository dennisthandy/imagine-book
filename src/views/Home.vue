<template>
  <div class="home">
    <button
      class="home__button home__button--search"
      :class="{close : searchState}"
      @click="searchState = !searchState"
    ></button>
    <div class="home__input home__input--box" v-show="searchState">
      <input
        type="text"
        placeholder="Cari Nama . . ."
        class="home__input home__input--search"
        v-model="searchName"
        @keypress.enter="searchMember"
      />
      <button class="home__button home__button--submit" @click="searchMember"></button>
      <button class="home__button home__button--clear" @click="clearSearch"></button>
    </div>
    <cover-slider :slider="slider" @openSlider="openSlider"></cover-slider>
    <div class="cards">
      <card v-for="member in members" :key="member.no" :member="member"></card>
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
      members: this.$store.state.members,
      searchName: "",
      searchState: false,
    };
  },
  watch: {
    searchName() {
      if (this.searchName === "") {
        this.members = this.$store.state.members;
      }
    },
  },
  methods: {
    openSlider() {
      this.slider = !this.slider;
      localStorage.setItem("slider", this.slider);
    },
    searchMember() {
      this.members = this.members.filter((member) => {
        return member.name
          .toLowerCase()
          .includes(this.searchName.toLowerCase());
      });
      this.searchState = false;
    },
    clearSearch() {
      this.members = this.$store.state.members;
      this.searchName = "";
    },
  },
  created() {
    const sliderState = localStorage.getItem("slider");
    sliderState ? (this.slider = true) : (this.slider = false);
  },
};
</script>

<style scoped lang="scss">
$break-desktop: 750px;

.home {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  &__button {
    padding: 1.25rem;
    border-radius: 0.5rem;
    box-shadow: 3px 3px 0 rgba($color: #000000, $alpha: 0.7);
    border: 1px solid blue;
    cursor: pointer;

    &:active {
      box-shadow: none;
    }
  }

  &__button--search {
    position: fixed;
    right: 1.5%;
    top: 50%;
    transform: translateY(-50%);
    background-image: url(../assets/icon/search-outline.svg);

    &.close {
      background-image: url(../assets/icon/close-square-outline.svg);
    }
  }

  &__button--submit {
    background-image: url(../assets/icon/done-all-outline.svg);
    margin-right: 0.75rem;
  }

  &__button--clear {
    background-image: url(../assets/icon/trash-2-outline.svg);
  }

  &__input--box {
    position: fixed;
    top: 30%;
    z-index: 999;
    padding: 1.5rem;
    background-color: #ccc;
    border-radius: 0.5rem;
    box-shadow: 3px 3px 0 rgba($color: #000000, $alpha: 0.7);
    display: flex;
  }

  &__input--search {
    margin-right: 0.75rem;
    padding: 0.75rem;
    border-radius: 0.5rem;
    border: 1px solid blue;
    box-shadow: 3px 3px 0 rgba($color: #000000, $alpha: 0.7);
    font-size: 12pt;
  }
}
.cards {
  margin: 3rem;
  @media (min-width: $break-desktop) {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;
  }
}
</style>
