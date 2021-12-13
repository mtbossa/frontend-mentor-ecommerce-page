<template>
  <article class="product-info container">
    <h3 class="product-info__producer-name">Sneaker Company</h3>
    <h1 class="product-info__name">Fall Limited Edition Sneakers</h1>
    <p class="product-info__description">
      These low-profile sneakers are your perfect casual wear companion.
      Featuring a durable rubber outer sole, they’ll withstand everything the
      weather can offer.
    </p>
    <div class="product-info__price-container">
      <div class="product-info__current-price-container">
        <h2 class="product-info__current-price">$125.00</h2>
        <div class="product-info__discount">50%</div>
      </div>

      <h4 class="product-info__old-price">$250.00</h4>
    </div>

    <QuantityInput />
    <AppButton />
  </article>
</template>

<script>
import QuantityInput from "@/components/QuantityInput";
import AppButton from "@/components/AppButton";
export default {
  components: { QuantityInput, AppButton },
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
</style>
