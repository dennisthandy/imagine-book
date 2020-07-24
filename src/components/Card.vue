<template>
  <div class="card">
    <div class="card__dots"></div>
    <div class="card__header">
      <div class="card__info">
        <span class="card__number">00079</span>
        <span class="card__gender">Laki - Laki</span>
      </div>
      <img src="../assets/img/logo.png" alt class="card__img" />
    </div>
    <div class="card__content">
      <p class="card__name">Dennis Thandy Nur Cahyono</p>
      <p class="card__city">Bojonegoro</p>
      <p class="card__class">C</p>
    </div>
    <div class="card__footer">
      <ul class="card__social">
        <li>
          <a href class="card__link">
            <img src="../assets/icon/instagram.svg" alt class="card__social--icon" />
          </a>
        </li>
        <li>
          <a href class="card__link">
            <img src="../assets/icon/instagram.svg" alt class="card__social--icon" />
          </a>
        </li>
        <li>
          <a href class="card__link">
            <img src="../assets/icon/instagram.svg" alt class="card__social--icon" />
          </a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "card",
};
</script>

<style scoped lang="scss">
.card {
  width: 16rem;
  height: 21.5rem;
  border: 1px solid purple;
  border-radius: 0.75rem;
  padding: 2.25rem 1rem;
  box-shadow: 3px 3px 0 rgba($color: #000000, $alpha: 0.7);
  position: relative;

  &__header {
    text-align: center;
    margin-bottom: 0.5rem;
  }

  &__info {
    display: flex;
    justify-content: space-between;
    margin-bottom: 0.5rem;
  }

  &__img {
    width: 10rem;
  }

  &__content {
    margin-bottom: 0.5rem;
  }

  &__social {
    display: flex;
    justify-content: space-around;
    li {
      list-style: none;
    }

    &--icon {
      width: 1.75rem;
    }
  }

  // extends for dots
  %dots {
    position: absolute;
    width: 12px;
    height: 12px;
    border-radius: 50%;
  }

  &__dots {
    @extend %dots;
    top: 1.5%;
    left: 3%;
    background-color: red;

    &::before {
      @extend %dots;
      content: "";
      left: 150%;
      background-color: yellow;
    }

    &::after {
      @extend %dots;
      content: "";
      left: 300%;
      background-color: green;
    }
  }

  &::before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 1.5rem;
    border-bottom: 1px solid purple;
    background-color: rgba($color: #c4c4c4, $alpha: 1);
    border-radius: 0.75rem 0.75rem 0 0;
  }
}
</style>