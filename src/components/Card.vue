<template>
  <div class="card w-64 h-auto p-2 m-4 rounded-lg shadow-lg bg-white">
    <div class="card__dots"></div>
    <div class="card__header">
      <div class="card__info flex w-full justify-between mb-3">
        <span class="card__number w-8 text-center bg-gray-300 rounded-full">{{ member.no }}</span>
        <span
          class="card__gender px-2 rounded-lg text-white"
          :class="genderStyle"
        >{{ member.gender }}</span>
      </div>
      <!-- <div class="card__picture w-full h-32 bg-no-repeat object-center" :style="photoMember"></div> -->
      <img
        :src="member.photo"
        alt="member_photo"
        class="card__img w-full h-48 object-cover object-top rounded-sm mb-3"
      />
    </div>
    <div class="card__content mb-3">
      <p class="card__name">{{ capitalizeName }}</p>
      <p class="card__city">{{ member.city }}</p>
    </div>
    <div class="card__footer mb-1">
      <ul class="card__social flex justify-around">
        <li v-if="member.instagram">
          <a :href="member.instagram" class="card__link">
            <img src="../assets/icon/instagram.svg" alt class="card__social--icon w-8 h-8" />
          </a>
        </li>
        <li v-if="member.facebook">
          <a :href="member.facebook" class="card__link">
            <img src="../assets/icon/facebook.svg" alt class="card__social--icon w-8 h-8" />
          </a>
        </li>
        <li v-if="member.youtube">
          <a :href="member.youtube" class="card__link">
            <img src="../assets/icon/youtube.svg" alt class="card__social--icon w-8 h-8" />
          </a>
        </li>
        <li v-if="member.github">
          <a :href="member.github" class="card__link">
            <img src="../assets/icon/github.svg" alt class="card__social--icon w-8 h-8" />
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
    genderStyle() {
      return this.member.gender === "Perempuan" ? "bg-pink-500" : "bg-blue-500";
    },
  },
};
</script>