<template>
  <div class="menu-item">
    <img
      class="menu-item__image"
      :src="item.image.source"
      :alt="item.image.alt"
    />
    <div>
      <h3>
        <router-link :to="{ name: 'Item', params: { name: item.name } }">{{
          item.name
        }}</router-link>
      </h3>
      <p>Prix : {{ generatedPrice }}</p>
      <p v-if="item.inStock">En stock</p>
      <p v-else>En rupture de stock</p>
      <div>
        <div>
          <label for="add-item-quantity">Quantité:</label>
          <input
            id="add-ite-quantity"
            type="number"
            :disabled="!item.inStock"
            v-model.number="item.quantity"
          />

          <button
            @click="addToShoppingCart(item.quantity)"
            :disabled="!item.inStock"
          >
            Ajouter au panier d'achat
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MenuItem",
  props: {
    item: Object,
    addToShoppingCart: Function,
  },
  data: function() {
    return {
      onSale: false,
    };
  },
  beforeMount() {
    const today = new Date().getDate();
    if (!today % 2) this.onSale = true;
  },
  computed: {
    generatedPrice() {
      if (this.onSale) return (this.item.price * 0.9).toFixed(2);
      return this.item.price;
    },
  },
};
</script>

<style lang="scss" scoped>
.menu-item__image {
  max-width: 300px;
}
</style>
