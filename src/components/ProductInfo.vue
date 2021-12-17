<template>
  <article class="product-info container">
    <h3 class="product-info__producer-name">{{ product.manufacturer }}</h3>
    <h1 class="product-info__name">{{ product.name }}</h1>
    <p class="product-info__description">
      {{ product.description }}
    </p>
    <div class="product-info__price-container">
      <div class="product-info__current-price-container">
        <h2 class="product-info__current-price">${{ productRealPrice }}</h2>
        <div class="product-info__discount">{{ product.discount }}%</div>
      </div>

      <h4 class="product-info__old-price">${{ product.price }}</h4>
    </div>

    <div class="product-info__buttons-container">
      <QuantityInput
        :quantity="quantity"
        @add-quantity="addQuantity"
        @remove-quantity="removeQuantity"
      />
      <AppButton icon="icon-cart.svg" alt="Cart" @click="addToCart"
        >Add to Cart</AppButton
      >
    </div>
  </article>
</template>

<script>
import QuantityInput from "@/components/QuantityInput";
import AppButton from "@/components/AppButton";

export default {
  components: { QuantityInput, AppButton },
  props: {
    product: {
      type: Object,
      default() {
        return {};
      },
    },
  },
  emits: ["addToCart"],
  data() {
    return {
      quantity: 0,
    };
  },
  computed: {
    productRealPrice() {
      return this.product.price * (this.product.discount / 100);
    },
  },
  methods: {
    addQuantity() {
      this.quantity++;
    },
    removeQuantity() {
      if (this.quantity >= 1) this.quantity--;
    },
    addToCart() {
      this.$emit("addToCart", this.product, this.quantity);

      this.quantity = 0;
    },
  },
};
</script>

<style scoped>
.product-info {
  display: grid;
  gap: 1.5rem;
  margin-top: 2rem;
}

.product-info__producer-name {
  text-transform: uppercase;
  font-size: 0.8rem;
  font-weight: 700;
  color: var(--color-primary-orange);
}

.product-info__name {
  font-size: 2rem;
  font-weight: 700;
}

.product-info__description {
  color: var(--color-dark-grayish-blue);
  line-height: 1.5rem;
}

.product-info__price-container {
  display: flex;
  max-width: 100%;
  justify-content: space-between;
  align-items: center;
}

.product-info__current-price-container {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.product-info__current-price {
  font-size: 1.5rem;
  font-weight: 700;
}

.product-info__discount {
  color: var(--color-primary-orange);
  padding: 0.3rem 0.6rem;
  border-radius: var(--border-radius-size);
  font-weight: 700;
  background-color: var(--color-primary-pale-orange);
}

.product-info__old-price {
  color: var(--color-grayish-blue);
  font-weight: 700;
  text-decoration: line-through;
}

@media (min-width: 1024px) {
  .product-info {
    max-width: 50%;
  }

  .product-info__price-container {
    flex-direction: column;
    align-items: flex-start;
  }

  .product-info__buttons-container {
    display: flex;
  }
}
</style>
