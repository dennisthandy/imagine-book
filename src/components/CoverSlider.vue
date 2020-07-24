.<template>
  <div :class="['cover', slider ? 'open' : '']">
    <button class="cover__button" @click="$emit('openSlider')"></button>
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
  background-image: linear-gradient(blue -50%, purple 90%);
  width: 100%;
  min-height: 100vh;
  position: absolute;
  z-index: 1;
  top: 0;
  opacity: 1;
  transition: min-height 0.5s ease, opacity 1s ease;

  &__button {
    background: url(../assets/icon/book-open.svg) no-repeat center;
    position: absolute;
    bottom: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    outline: none;
    cursor: pointer;
    padding: 1.25rem;
    width: 5rem;
    border: 1.5px solid #fff;
    border-radius: 10px;
    box-shadow: 5px 5px 0 rgba($color: #000000, $alpha: 0.7);
  }

  &.open {
    min-height: 0;
    opacity: 0;
    pointer-events: none;
  }
}
</style>
