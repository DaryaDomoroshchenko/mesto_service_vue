<template>
    <div class="popup popup__changeAvatar">
      <div class="popup__content">
        <img @click="hide" src="@/assets/images/close.svg" alt="Закрыть" class="popup__close"/>
        <h4 class="popup__title">Обновить аватар</h4>
        <form @submit.prevent="changeAvatar" class="popup__form" name="changeAvatar">
          <input
            v-model="imageUrl"
            type="url"
            name="avatarLink"
            class="popup__input popup__input_type_avatar-link"
            placeholder="Ссылка на аватар"
          />
          <button type="submit" class="button popup__button popup__button_edit">Сохранить</button>
        </form>
      </div>
    </div>
</template>

<script>
export default {
  name: "PopupChangeAvatar",

  data() {
    return {
      imageUrl: ""
    };
  },

  methods: {
    hide() {
      this.$emit("hide-popup");
    },

    changeAvatar() {
      this.hide();
      const avatarLink = this.imageUrl;

      this.$emit("change-avatar", avatarLink);
    }
  }
};
</script>
