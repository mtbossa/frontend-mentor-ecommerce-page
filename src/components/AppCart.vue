<template>
  <div class="cart">
    <div class="container">
      <p class="cart__title">Cart</p>
    </div>
    <div class="cart__divider"></div>

    <div
      v-if="Object.keys(cart).length"
      class="cart__item-container padding-x--small padding-y--small"
    >
      <CartItem
        v-for="(product, index) in cart"
        :key="index"
        :product="product"
        @cart-item-deleted="$emit('cartItemDeleted', id)"
      />
      <AppButton class="padding-y--small">Checkout</AppButton>
    </div>

    <div
      v-if="!Object.keys(cart).length"
      class="cart__item-container-empty padding-x--small padding-y--small"
    >
      <p class="cart__empty">Your cart is empty</p>
    </div>
  </div>
</template>

<script>
import CartItem from "@/components/CartItem";
import AppButton from "@/components/AppButton";

export default {
  components: { CartItem, AppButton },
  props: {
    cart: {
      type: Array,
      default() {
        return [];
      },
    },
  },
  emits: ["cartItemDeleted"],
};
</script>

<style scoped>
.cart {
  background-color: var(--color-white);
  margin: 1rem;
  border-radius: var(--border-radius-size);
  position: fixed;
  top: var(--header-height);
  left: 0;
  right: 0;
  z-index: 130;
  box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.1);
}

.cart__title {
  padding: 1.5rem 0;
  font-weight: 700;
}

.cart__divider {
  height: 0.5px;
  background-color: var(--color-grayish-blue);
  width: 100%;
}

.cart__item-container {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.cart__item-container-empty {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 250px;
}

.cart__empty {
  font-weight: 700;
  color: var(--color-dark-grayish-blue);
  width: 100%;
  text-align: center;
}

@media (min-width: 1024px) {
  .cart {
    top: 90px;
    left: 70vw;
    max-width: 450px;
  }
}
</style>
