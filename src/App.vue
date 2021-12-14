<template>
  <AppHeader @cart-clicked="toggleCart" />

  <ProductShowcase />

  <ProductInfo :product="product" />

  <AppCart v-if="cartOpen" />

  <div class="attribution">
    Challenge by
    <a href="https://www.frontendmentor.io?ref=challenge" target="_blank"
      >Frontend Mentor</a
    >. Coded by
    <a href="https://www.github.com/mtbossa">Mateus Ribeiro Bossa</a>.
  </div>
</template>

<script>
import AppHeader from "@/components/AppHeader";
import ProductShowcase from "@/components/ProductShowcase";
import ProductInfo from "@/components/ProductInfo";
import AppCart from "@/components/AppCart";

export default {
  name: "App",
  components: { AppHeader, ProductShowcase, ProductInfo, AppCart },
  data() {
    return {
      cartOpen: true,
      product: {
        name: "Fall Limited Edition Sneakers",
        description:
          "These low-profile sneakers are your perfect casual wear companion. Featuring a durable rubber outer sole, they’ll withstand everything the weather can offer.",
        price: 250.0,
        discount: 50,
        manufacturer: "Sneaker Company",
      },
      cart: {},
    };
  },
  methods: {
    toggleCart() {
      this.cartOpen = !this.cartOpen;
    },
  },
};
</script>

<style>
html {
  font-family: "Kumbh Sans", sans-serif;
}

body {
  background-color: var(--color-white);
  font-size: var(--font-size);
  color: var(--color-black);
}
.container {
  margin: 0rem 2rem;
}

.attribution {
  margin-top: 5rem;
  font-size: 11px;
  text-align: center;
}
.attribution a {
  color: hsl(228, 45%, 44%);
}
</style>
