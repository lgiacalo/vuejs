<template>
  <div id="app">
    <main class="ui main container">
      <h1>{{ restaurantName }}</h1>

      <p class="description">
        Bienvenue dans notre café {{ restaurantName }} ! Nous sommes réputés
        pour notre pain et nos merveilleuses pâtisseries. Faites vous plaisir
        dès le matin ou avec un goûter réconfortant. Mais attention, vous verrez
        qu'il est difficile de s'arrêter.
      </p>

      <section class="menu">
        <h2>Menu</h2>

        <div class="ui centered three column grid">
          <menu-item
            class="column"
            v-for="item in simpleMenu"
            v-bind:item="item"
            v-bind:addToShoppingCart="addToShoppingCart"
            v-bind:key="item.name"
          />
        </div>
      </section>

      <aside class="shopping-cart">
        <h2>Panier d'achat: {{ shoppingCart }} articles</h2>
      </aside>

      <div>
        <h2>Contactez nous</h2>
        <p>Adresse : {{ addresse }}</p>
        <p>Téléphone : {{ phone }}</p>
        <p>Email : {{ email }}</p>
        <p>Horaires :</p>
        <ul>
          <li>L-V: 06:00 à 16:00</li>
          <li>Samedi: 07:00 à 14:00</li>
          <li>Dimanche: 07:00 à 12:00</li>
        </ul>
      </div>
    </main>
    <footer class="ui inverted vertical footer segment form-page">
      <p class="ui container">{{ copyright }}</p>
    </footer>
  </div>
</template>

<script>
import MenuItem from "./components/MenuItem.vue";

export default {
  components: { MenuItem },
  name: "App",
  data: function() {
    return {
      restaurantName: "La belle vue",
      addresse: "18 avenue du Beurre, Paris, France",
      phone: "01 88 88 88 88",
      email: "hello@cafewithavue.bakery",
      shoppingCart: 0,
      simpleMenu: [
        {
          name: "Croissant",
          image: {
            source: "/images/croissant.jpg",
            alt: "Un croissant",
          },
          inStock: true,
          quantity: 1,
        },
        {
          name: "Baguette de pain",
          image: {
            source: "/images/french-baguette.jpeg",
            alt: "Quatre baguettes de pain",
          },
          inStock: true,
          quantity: 1,
        },
        {
          name: "Éclair",
          image: {
            source: "/images/eclair.jpg",
            alt: "Éclair au chocolat",
          },
          inStock: false,
          quantity: 1,
        },
      ],
    };
  },
  computed: {
    copyright: function() {
      const currentYear = new Date().getFullYear();
      return `Copyright ${this.restaurantName} ${currentYear}`;
    },
  },
  methods: {
    addToShoppingCart(nb) {
      this.shoppingCart += nb;
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
