<template>
  <article class="cart-item">
    <div class="cart-item__info-container">
      <img
        class="cart-item__image"
        :src="getImgUrl(product.mainThumbnail)"
        alt="Product"
      />
      <div class="cart-item__info">
        <p class="cart-item__name">{{ product.name }}</p>
        <p class="cart-item__price">
          ${{ product.price }} x {{ product.quantity }}
          <span class="cart-item__total">${{ totalValue }}</span>
        </p>
      </div>
    </div>

    <button class="button-icon" @click="$emit('cartItemDeleted', product.id)">
      <img src="../assets/images/icon-delete.svg" alt="Trash" />
    </button>
  </article>
</template>

<script>
export default {
  props: {
    product: {
      type: Object,
      default() {
        return {};
      },
    },
  },
  emits: ["cartItemDeleted"],
  computed: {
    totalValue() {
      return this.product.price * this.product.quantity;
    },
  },
  methods: {
    getImgUrl(pic) {
      return require(`../assets/images/${pic}`);
    },
  },
};
</script>

<style scoped>
.cart-item {
  display: flex;
  gap: 1rem;
  align-items: center;
  justify-content: space-between;
}

.cart-item__info-container {
  display: flex;
  gap: 1rem;
}

.cart-item__image {
  max-width: 15%;
  border-radius: var(--border-radius-size);
}

.cart-item__name {
  color: var(--color-dark-grayish-blue);
}

.cart-item__price {
  color: var(--color-dark-grayish-blue);
}

.cart-item__total {
  font-weight: 700;
  color: var(--color-black);
}
</style>
