<template>
  <div class="home relative flex flex-col justify-center items-center min-h-screen z-0">
    <div
      class="home__toolbar fixed flex flex-col h-48 justify-around bg-gray-500 bg-opacity-75 px-1 rounded-md"
    >
      <button
        class="home__button home__button--search bg-white rounded-full p-1 shadow-lg focus:outline-none"
        :class="{ close: searchState, active: searchState }"
        @click="searchState = !searchState"
      >
        <span class="home__icon home__icon--search block no-repeat w-8 h-8"></span>
      </button>
      <button
        class="home__button home__button--male bg-white rounded-full p-1 shadow-lg focus:outline-none"
        @click="filterMember('Laki - Laki')"
        :class="{ active: male }"
      >
        <span class="home__icon home__icon--male block no-repeat w-8 h-8"></span>
      </button>
      <button
        class="home__button home__button--female bg-white rounded-full p-1 shadow-lg focus:outline-none"
        @click="filterMember('Perempuan')"
        :class="{ active: female }"
      >
        <span class="home__icon home__icon--female block no-repeat w-8 h-8"></span>
      </button>
    </div>

    <div
      class="home__input home__input--box flex fixed p-5 bg-gray-500 bg-opacity-75 rounded-md"
      v-show="searchState"
    >
      <input
        type="text"
        placeholder="Cari Nama . . ."
        class="home__input home__input--search rounded-md px-1"
        v-model="searchName"
        @keypress.enter="searchMember"
      />
      <button
        class="home__button home__button--submit mx-2 bg-white rounded-full p-1 shadow-lg focus:outline-none"
        @click="searchMember"
      >
        <span class="home__icon home__icon--submit block no-repeat w-6 h-6"></span>
      </button>
      <button
        class="home__button home__button--clear bg-white rounded-full p-1 shadow-lg focus:outline-none"
        @click="clearSearch"
      >
        <span class="home__icon home__icon--clear block no-repeat w-6 h-6"></span>
      </button>
    </div>

    <cover-slider :slider="slider" @openSlider="openSlider"></cover-slider>
    <div class="cards flex flex-wrap justify-around" v-show="slider">
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
  props: {
    sliderState: {
      required: true,
      type: Boolean,
    },
    setSliderState: {
      required: true,
      type: Function,
    },
  },
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
      male: false,
      female: false,
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
      this.$emit("setSliderState");
    },
    searchMember() {
      this.members = this.members.filter((member) => {
        return member.name
          .toLowerCase()
          .includes(this.searchName.toLowerCase());
      });
    },
    clearSearch() {
      this.members = this.$store.state.members;
      this.searchName = "";
    },
    filterMember(gender) {
      if (gender === "Laki - Laki" && !this.male) {
        if (this.female) {
          this.members = this.$store.state.members;
          this.female = false;
        }
        this.members = this.members.filter((member) => {
          return member.gender === gender;
        });
        this.male = true;
      } else if (gender === "Perempuan" && !this.female) {
        if (this.male) {
          this.members = this.$store.state.members;
          this.male = false;
        }
        this.members = this.members.filter((member) => {
          return member.gender === gender;
        });
        this.female = true;
      } else {
        this.members = this.$store.state.members;
        this.male = false;
        this.female = false;
      }
    },
  },
  created() {
    const sliderState = localStorage.getItem("slider");
    sliderState ? (this.slider = true) : (this.slider = false);
  },
};
</script>

<style lang="scss">
.home {
  &__toolbar {
    top: 50%;
    right: 0.5%;
    transform: translateY(-50%);
  }

  &__button--search {
    &.active {
      @apply bg-orange-500;
    }
  }

  &__icon--search {
    background-image: url(../assets/icon/search-outline.svg);
  }

  &__button--male {
    &.active {
      @apply bg-blue-500;
    }
  }

  &__icon--male {
    background-image: url(../assets/icon/male.svg);
  }

  &__button--female {
    &.active {
      @apply bg-pink-500;
    }
  }

  &__icon--female {
    background-image: url(../assets/icon/female.svg);
  }

  &__input--box {
    top: 20%;
  }

  &__icon--submit {
    background-image: url(../assets/icon/done-all-outline.svg);
  }

  &__icon--clear {
    background-image: url(../assets/icon/trash-2-outline.svg);
  }
}
</style>
