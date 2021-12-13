<template>
  <div class="quantity-input">
    <button
      class="button-icon padding-x--small padding-y--small"
      @click="removeQuantity"
    >
      <img src="@/assets/images/icon-minus.svg" alt="Minus" />
    </button>

    <p>{{ quantity }}</p>
    <button
      class="button-icon padding-x--small padding-y--small"
      @click="addQuantity"
    >
      <img src="@/assets/images/icon-plus.svg" alt="Plus" />
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      quantity: 0,
    };
  },
  methods: {
    addQuantity() {
      this.quantity++;
    },
    removeQuantity() {
      if (this.quantity >= 1) this.quantity--;
    },
  },
};
</script>

<style scoped>
.quantity-input {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: var(--color-light-grayish-blue);
  border-radius: var(--border-radius-size);
}
</style>
