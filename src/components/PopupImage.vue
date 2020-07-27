<template>
  <div class="popup popup__image">
    <div class="popup__image-content">
      <img @click="hide" src="@/assets/images/close.svg" alt="Закрыть" class="popup__close">
      <img alt="Фотография выбранного места" class="popup__big-image" :src="`${image}`"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "PopupImage",

  props: {
    image: {
      type: String
    }
  },

  methods: {
    hide() {
      this.$emit("hide-popup");
    }
  }
};
</script>
