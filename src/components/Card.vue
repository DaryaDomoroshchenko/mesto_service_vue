<template>
  <div class="place-card">
    <div class="place-card__image" :style="`background-image: url(${url})`">
      <button
        @click="removeCard"
        class="place-card__delete-icon"
      ></button>
    </div>
    <div class="place-card__description">
      <h3 class="place-card__name">{{ name }}</h3>
      <button
        @click="toggleLike"
        class="place-card__like-icon"
        :class="{ 'place-card__like-icon_liked': like }"
      ></button>
    </div>
  </div>
</template>

<script>
export default {

  props: ["name", "url"],

  data() {
    return {
      like: false
    };
  },

  methods: {

    toggleLike() {
      this.like = !this.like;
    },

    removeCard() {
      this.$emit("remove");
    }
  }
};
</script>
