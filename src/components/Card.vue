<template>
  <div class="card">
    <div class="card__dots"></div>
    <div class="card__header">
      <div class="card__info">
        <span class="card__number">{{ member.no }}</span>
        <span class="card__gender">{{ member.gender }}</span>
      </div>
      <div class="card__picture" :style="photoMember"></div>
      <!-- <img :src="member.photo" alt="member_photo" class="card__img" /> -->
    </div>
    <div class="card__content">
      <p class="card__name">{{ capitalizeName }}</p>
      <p class="card__city">{{ member.city }}</p>
    </div>
    <div class="card__footer">
      <ul class="card__social">
        <li>
          <a :href="member.instagram" class="card__link">
            <img src="../assets/icon/instagram.svg" alt class="card__social--icon" />
          </a>
        </li>
        <li>
          <a :href="member.facebook" class="card__link">
            <img src="../assets/icon/facebook.svg" alt class="card__social--icon" />
          </a>
        </li>
        <li>
          <a :href="member.twitter" class="card__link">
            <img src="../assets/icon/twitter.svg" alt class="card__social--icon" />
          </a>
        </li>
        <li>
          <a :href="member.youtube" class="card__link">
            <img src="../assets/icon/youtube.svg" alt class="card__social--icon" />
          </a>
        </li>
        <li>
          <a :href="member.github" class="card__link">
            <img src="../assets/icon/github.svg" alt class="card__social--icon" />
          </a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "card",
  props: {
    member: {
      type: Object,
      required: true,
    },
  },
  computed: {
    capitalizeName() {
      const name = this.member.name.split(" ");
      let rest = "";
      for (let i = 0; i < name.length; i++) {
        rest +=
          name[i].charAt(0).toUpperCase() +
          name[i].slice(1).toLowerCase() +
          " ";
      }
      return rest;
    },
    photoMember() {
      return {
        backgroundImage: `url(${this.member.photo})`,
      };
    },
  },
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
  margin-bottom: 2.75rem;

  &__header {
    text-align: center;
    margin-bottom: 1rem;
  }

  &__info {
    display: flex;
    justify-content: space-between;
    margin-bottom: 1rem;
  }

  &__picture {
    width: 14rem;
    height: 10rem;
    margin: auto;
    background-repeat: no-repeat;
    background-size: cover;
  }

  &__content {
    margin-bottom: 1rem;
  }

  &__social {
    display: flex;
    justify-content: space-around;
    li {
      list-style: none;
    }

    &--icon {
      width: 1.5rem;
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
