<template>
  <div class="popup popup__edit">
    <div class="popup__content">
      <img @click="hide" src="@/assets/images/close.svg" alt="Закрыть" class="popup__close">
      <h4 class="popup__title">Редактировать профиль</h4>
      <form @submit.prevent="editProfile" class="popup__form" name="edit">
          <input
           v-model="profileName"
            type="text"
            name="profileName"
            class="popup__input popup__input_type_profileName"
            placeholder="Имя"
            required
          />
          <input
            v-model="about"
            type="text"
            name="about"
            class="popup__input popup__input_type_about"
            placeholder="О себе"
            required
          />
          <button type="submit" class="button popup__button popup__button_edit">Сохранить</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "PopupEditProfile",

  data() {
    return {
      profileName: "",
      about: ""
    };
  },

  methods: {
    hide() {
      this.$emit("hide-popup");
    },

    editProfile() {
      this.hide();
      const userInfo = {
        profileName: this.profileName,
        about: this.about
      };

      this.$emit("edit-profile", userInfo);
    }
  }
};
</script>
