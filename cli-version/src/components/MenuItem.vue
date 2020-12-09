<template>
  <div class="ui fluid card">
    <img :src="item.image.source" :alt="item.image.alt" />
    <div class="ui content">
      <h3>{{ item.name }}</h3>
      <p v-if="item.inStock">En stock</p>
      <p v-else>En rupture de stock</p>
      <div class="ui medium form">
        <div class="field">
          <label for="add-item-quantity">Quantité:</label>
          <input
            id="add-ite-quantity"
            type="number"
            :disabled="!item.inStock"
            v-model.number="item.quantity"
          />

          <button
            class="fluid ui button"
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
};
</script>
