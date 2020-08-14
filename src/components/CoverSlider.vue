.<template>
  <div
    :class="['cover', slider ? 'open' : '']"
    class="w-full min-h-screen bg-purple-500 absolute top-0 z-10 opacity-100"
  >
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 320" class="absolute top-0">
      <path
        fill="#fff"
        fill-opacity="1"
        d="M0,256L0,128L110.8,128L110.8,224L221.5,224L221.5,192L332.3,192L332.3,288L443.1,288L443.1,160L553.8,160L553.8,288L664.6,288L664.6,160L775.4,160L775.4,128L886.2,128L886.2,128L996.9,128L996.9,160L1107.7,160L1107.7,64L1218.5,64L1218.5,128L1329.2,128L1329.2,160L1440,160L1440,0L1329.2,0L1329.2,0L1218.5,0L1218.5,0L1107.7,0L1107.7,0L996.9,0L996.9,0L886.2,0L886.2,0L775.4,0L775.4,0L664.6,0L664.6,0L553.8,0L553.8,0L443.1,0L443.1,0L332.3,0L332.3,0L221.5,0L221.5,0L110.8,0L110.8,0L0,0L0,0Z"
      />
    </svg>

    <h1 class="cover__title text-center font-bold">IMAGINE SUQUAD 2016</h1>
    <h2 class="text-center font-bold text-white mt-2 mb-8">Family Book</h2>
    <div class="desc mx-auto w-64">
      <p
        class="text-justify"
      >Semoga dengan adanya buku digital ini seluruh keluarga Imagine Squad 2016 bisa selalu teringat dan tak terlupakan bahwa pernah memiliki keluarga saat kuliah di jurusan Informatika fakultas Teknik UTM.</p>
    </div>
    <button
      class="cover__button absolute bg-white rounded-full p-3 shadow-lg focus:outline-none"
      @click="$emit('openSlider')"
    >
      <span class="cover__icon cover__icon--open block no-repeat w-10 h-10"></span>
    </button>

    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 320" class="absolute bottom-0">
      <path
        fill="#fff"
        fill-opacity="1"
        d="M0,64L0,224L84.7,224L84.7,0L169.4,0L169.4,192L254.1,192L254.1,32L338.8,32L338.8,128L423.5,128L423.5,160L508.2,160L508.2,96L592.9,96L592.9,32L677.6,32L677.6,192L762.4,192L762.4,64L847.1,64L847.1,160L931.8,160L931.8,96L1016.5,96L1016.5,160L1101.2,160L1101.2,96L1185.9,96L1185.9,224L1270.6,224L1270.6,64L1355.3,64L1355.3,224L1440,224L1440,320L1355.3,320L1355.3,320L1270.6,320L1270.6,320L1185.9,320L1185.9,320L1101.2,320L1101.2,320L1016.5,320L1016.5,320L931.8,320L931.8,320L847.1,320L847.1,320L762.4,320L762.4,320L677.6,320L677.6,320L592.9,320L592.9,320L508.2,320L508.2,320L423.5,320L423.5,320L338.8,320L338.8,320L254.1,320L254.1,320L169.4,320L169.4,320L84.7,320L84.7,320L0,320L0,320Z"
      />
    </svg>
  </div>
</template>

<script>
export default {
  name: "cover-slider",
  props: {
    slider: {
      type: Boolean,
      required: true,
    },
  },
};
</script>

<style scoped lang="scss">
.cover {
  transition: min-height 0.75s ease, opacity 1s ease;

  &__title {
    margin-top: 7rem;
  }

  &__button {
    bottom: 25%;
    left: 50%;
    transform: translate(-50%, -50%);
  }

  &__icon--open {
    background: url(../assets/icon/book-open.svg);
  }

  &.open {
    min-height: 0;
    opacity: 0;
    pointer-events: none;
  }
}
</style>
