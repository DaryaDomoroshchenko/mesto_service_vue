<template>
  <div class="popup popup__addPlace">
    <div class="popup__content">
      <img @click="hide" src="@/assets/images/close.svg" alt="Закрыть" class="popup__close"/>
      <h4 class="popup__title">Новое место</h4>
      <form @submit.prevent="addCard" class="popup__form" name="add">
        <input
          v-model="name"
          type="text"
          name="name"
          class="popup__input popup__input_type_name"
          placeholder="Название"
          required
        />
        <input
          v-model="link"
          type="text"
          name="link"
          class="popup__input popup__input_type_link-url"
          placeholder="Ссылка на картинку"
          required
        />
        <button type="submit" class="button popup__button popup__button_add">+</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "PopupAddPlace",

  data() {
    return {
      name: "",
      link: ""
    };
  },

  methods: {
    hide() {
      this.$emit("hide-popup");
    },

    addCard() {
      this.hide();
      const cardData = {
        name: this.name,
        link: this.link
      };

      this.$emit("add-card", cardData);
    }
  }
};
</script>
