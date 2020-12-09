<template>
  <div>
    <main>
      <h1>{{ restaurantName }}</h1>

      <p class="description">
        Bienvenue dans notre café {{ restaurantName }} ! Nous sommes réputés
        pour notre pain et nos merveilleuses pâtisseries. Faites vous plaisir
        dès le matin ou avec un goûter réconfortant. Mais attention, vous verrez
        qu'il est difficile de s'arrêter.
      </p>

      <section class="menu">
        <h2>Menu</h2>

        <menu-item
          v-for="item in simpleMenu"
          v-bind:item="item"
          v-bind:addToShoppingCart="addToShoppingCart"
          v-bind:key="item.name"
        />
      </section>

      <aside class="shopping-cart">
        <h2>Panier d'achat: {{ shoppingCart }} articles</h2>
      </aside>
    </main>
    <footer>
      <p>{{ copyright }}</p>
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

<style lang="scss" scoped>
.description {
  max-width: 960px;
  font-size: 1.2rem;
  margin: 0 auto;
}

.footer {
  text-align: center;
  font-style: italic;
}

.menu {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.menu-item {
  display: flex;
  width: 500px;
  justify-content: space-between;
  margin-bottom: 30px;
}

.shopping-cart {
  position: absolute;
  right: 30px;
  top: 0;
}
</style>
