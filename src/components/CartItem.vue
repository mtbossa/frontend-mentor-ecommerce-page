<template>
  <article class="cart-item">
    <div class="cart-item__info-container">
      <img
        class="cart-item__image"
        src="../assets/images/image-product-1-thumbnail.jpg"
        alt="Product"
      />
      <div class="cart-item__info">
        <p class="cart-item__name">Autum Limited Edition...</p>
        <p class="cart-item__price">
          $125.00 x 3 <span class="cart-item__total">$375.00</span>
        </p>
      </div>
    </div>

    <button class="button-icon">
      <img src="../assets/images/icon-delete.svg" alt="Trash" />
    </button>
  </article>
</template>

<script>
export default {};
</script>

<style scoped>
.cart-item {
  display: flex;
  gap: 1rem;
  align-items: center;
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