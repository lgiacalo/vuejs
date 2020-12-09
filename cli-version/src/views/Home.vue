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
    </main>
    <footer class="ui inverted vertical footer segment form-page">
      <p class="ui container">{{ copyright }}</p>
    </footer>
  </div>
</template>

<script>
import MenuItem from "../components/MenuItem.vue";

export default {
  components: { MenuItem },
  name: "App",
  data: function() {
    return {
      restaurantName: "La belle vue",
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
          price: 2.99,
        },
        {
          name: "Baguette de pain",
          image: {
            source: "/images/french-baguette.jpeg",
            alt: "Quatre baguettes de pain",
          },
          inStock: true,
          quantity: 1,
          price: 3.99,
        },
        {
          name: "Éclair",
          image: {
            source: "/images/eclair.jpg",
            alt: "Éclair au chocolat",
          },
          inStock: false,
          quantity: 1,
          price: 4.99,
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
