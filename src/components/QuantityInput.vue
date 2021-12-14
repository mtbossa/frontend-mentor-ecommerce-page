<template>
  <div class="quantity-input">
    <button
      class="button-icon padding-x--small padding-y--small"
      @click="$emit('removeQuantity')"
    >
      <img src="@/assets/images/icon-minus.svg" alt="Minus" />
    </button>

    <p>{{ quantity }}</p>
    <button
      class="button-icon padding-x--small padding-y--small"
      @click="$emit('addQuantity')"
    >
      <img src="@/assets/images/icon-plus.svg" alt="Plus" />
    </button>
  </div>
</template>

<script>
export default {
  props: {
    quantity: {
      type: Number,
      default() {
        return 0;
      },
    },
  },
  emits: ["addQuantity", "removeQuantity"],
};
</script>

<style scoped>
.quantity-input {
  display: flex;
  align-items: center;
  justify-content: space-between;
  min-height: 3.5rem;
  background-color: var(--color-light-grayish-blue);
  border-radius: var(--border-radius-size);
}
</style>
