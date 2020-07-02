<template>
  <div class="root">

    <header class="header root__section">
      <img src="@/assets/images/logo.svg" alt="mesto logo" class="logo"/>
    </header>

    <div class="profile root__section">
      <div class="user-info">
        <div class="user-info__photo"></div>
        <div class="user-info__data">
          <h1 class="user-info__name">Даша Путешественница</h1>
          <p class="user-info__job">Программист-неофит</p>
          <button class="button user-info__edit-button">Edit</button>
        </div>
        <button @click="popupIsShown=true" class="button user-info__plus-button">+</button>
      </div>
    </div>

    <div class="places-list root__section">
      <Card
        v-for="card in cards"
        :key="card.id"
        :name="card.name"
        :url="card.link"
        @remove="deleteCard(card.id)"
      />
    </div>

    <PopupAddPlace
      v-if="popupIsShown"
      @hide-popup="popupIsShown=false"
      @add-card="addCard"
    />

  </div>
</template>

<script>
import Card from "./components/Card.vue";
import PopupAddPlace from "./components/PopupAddPlace.vue";

export default {
  name: 'App',

  components: {
    Card,
    PopupAddPlace
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

      popupIsShown: false,
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
    }
  }
};
</script>

<style>
  @import url(./assets/pages/index.css);
</style>
