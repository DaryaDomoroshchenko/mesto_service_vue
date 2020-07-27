<template>
  <div class="root">

    <header class="header root__section">
      <img src="@/assets/images/logo.svg" alt="mesto logo" class="logo"/>
    </header>

    <div class="profile root__section">
      <div class="user-info">
        <div @click="changePopupIsShown=true" class="user-info__photo"
          :style="`background-image: url(${avatarUrl})`"
        />
        <div class="user-info__data">
          <h1 class="user-info__name">{{ profileName }}</h1>
          <p class="user-info__job">{{ about }}</p>
          <button @click="editPopupIsShown=true" class="button user-info__edit-button">Edit</button>
        </div>
        <button @click="addPopupIsShown=true" class="button user-info__plus-button">+</button>
      </div>
    </div>

    <div class="places-list root__section">
      <Card
        v-for="card in cards"
        :key="card.id"
        :name="card.name"
        :url="card.link"
        @remove="deleteCard(card.id)"
        @show-image="showImage(card.link)"
      />
    </div>

    <PopupAddPlace
      v-if="addPopupIsShown"
      @hide-popup="addPopupIsShown=false"
      @add-card="addCard"
    />

    <PopupEditProfile
      v-if="editPopupIsShown"
      @hide-popup="editPopupIsShown=false"
      @edit-profile="editProfile"
    />

    <PopupChangeAvatar
      v-if="changePopupIsShown"
      @hide-popup="changePopupIsShown=false"
      @change-avatar="changeAvatar"
    />

    <PopupImage
      v-if="imagePopupIsShown"
      @hide-popup="imagePopupIsShown=false"
      :image="imageUrl"
    />

  </div>
</template>

<script>
import Card from "@/components/Card.vue";
import PopupAddPlace from "@/components/PopupAddPlace.vue";
import PopupEditProfile from "@/components/PopupEditProfile.vue";
import PopupChangeAvatar from "@/components/PopupChangeAvatar.vue";
import PopupImage from "@/components/PopupImage.vue";

export default {
  name: 'App',

  components: {
    Card,
    PopupAddPlace,
    PopupEditProfile,
    PopupChangeAvatar,
    PopupImage
  },

  data() {
    return {
      cards: [
        {
          id: 1,
          name: "Токио",
          link:
            "https://images.unsplash.com/flagged/photo-1556709917-1b02a2d54472?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=400&q=80"
        },
        {
          id: 2,
          name: "Найроби",
          link:
            "https://images.unsplash.com/photo-1585523658894-cc78fc2c8f67?ixlib=rb-1.2.1&auto=format&fit=crop&w=334&q=80"
        },
        {
          id: 3,
          name: "Денвер",
          link:
            "https://images.unsplash.com/photo-1585180636723-dc006ba51fe5?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=358&q=80"
        },
        {
          id: 4,
          name: "Рио-де-Жанейро",
          link:
            "https://images.unsplash.com/photo-1510333337682-fdd0eba357a4?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=375&q=80"
        },
        {
          id: 5,
          name: "Берлин",
          link:
            "https://images.unsplash.com/photo-1591553746977-30af7be0288b?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=359&q=80"
        },
        {
          id: 6,
          name: "Москва",
          link:
            "https://images.unsplash.com/photo-1520106212299-d99c443e4568?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=334&q=80"
        },
        {
          id: 7,
          name: "Лиссабон",
          link:
            "https://images.unsplash.com/photo-1562250883-a18ef907fcab?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=334&q=80"
        },
        {
          id: 8,
          name: "Стокгольм",
          link:
            "https://images.unsplash.com/photo-1552516529-2360b188b56e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=334&q=80"
        },
        {
          id: 9,
          name: "Хельсинки",
          link:
            "https://images.unsplash.com/photo-1593157327221-213b1df00998?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=376&q=80"
        }
      ],

      profileName: "Даша Путешественница",
      about: "Программист-неофит",

      avatarUrl: "https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcTPtZfyeQViRSxXaMp7V0ZZcq9Omtn8PJWmcQ&usqp=CAU",

      addPopupIsShown: false,
      editPopupIsShown: false,
      changePopupIsShown: false,
      imagePopupIsShown: false,

      imageUrl: ""
    };
  },

  methods: {
    deleteCard(id) {
      this.cards = this.cards.filter(card => card.id !== id);
    },

    addCard(data) {
      const { name, link } = data;
      const id = Date.now();
      this.cards.push({ name, link, id });
    },

    editProfile(userInfo) {
      this.profileName = userInfo.profileName;
      this.about = userInfo.about;
    },

    changeAvatar(url) {
      this.avatarUrl = url;
    },

    showImage(link) {
      console.log(link);
      this.imageUrl = link;
      this.imagePopupIsShown = true
    }
  }
};
</script>

<style>
  @import url(./assets/pages/index.css);
</style>
