<template>
  <div class="quantity-input">
    <img src="@/assets/images/icon-minus.svg" alt="Plus" />
    <p>0</p>
    <img src="@/assets/images/icon-plus.svg" alt="Plus" />
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.quantity-input {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: var(--color-light-grayish-blue);
  padding: 1.5rem;
  border-radius: 10px;
}
</style>
