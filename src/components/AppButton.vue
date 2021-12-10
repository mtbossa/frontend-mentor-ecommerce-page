<template>
  <button class="app-button app-button--orange padding-y--small">
    <img
      class="app-button__icon"
      src="@/assets/images/icon-cart.svg"
      alt="Cart"
    />
    Add to cart
  </button>
</template>

<script>
export default {};
</script>

<style scoped>
.app-button {
  align-items: center;
  display: flex;
  flex-direction: row;
  justify-content: center;
  gap: 1rem;
  min-width: 300px;
  width: 100%;
  max-width: 400px;
  border: none;
  cursor: pointer;
  font-weight: 700;
  font-size: 1rem;
  font-family: "Kumbh Sans", sans-serif;
  border-radius: 10px;
}

.app-button--orange {
  background-color: var(--color-primary-orange);
  color: var(--color-white);
}
</style>
