<template>
  <div class="cart">
    <div class="container">
      <p class="cart__title">Cart</p>
    </div>
    <div class="cart__divider"></div>
    <div
      v-if="!cartEmpty"
      class="cart__item-container padding-x--small padding-y--small"
    >
      <CartItem />
      <CartItem />
    </div>
    <div
      v-if="cartEmpty"
      class="cart__item-container-empty padding-x--small padding-y--small"
    >
      <p class="cart__empty">Your cart is empty</p>
    </div>
  </div>
</template>

<script>
import CartItem from "@/components/CartItem";

export default {
  components: { CartItem },
  data() {
    return {
      cartEmpty: true,
    };
  },
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
  z-index: 100;
  box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.3);
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
</style>