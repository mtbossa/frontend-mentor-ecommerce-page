<template>
  <AppHeader
    :cart-product-amount="cart.length"
    @cart-clicked="toggleCart"
    @open-menu="cartOpen = false"
  />
  <AppCart
    v-if="cartOpen"
    v-click-outside="onClickOutsideCart"
    :cart="cart"
    @cart-item-deleted="removeFromCart(id)"
  />

  <div class="main-container">
    <ProductCarousel
      :slides="product.images"
      @product-carousel-click="openCarouselModal"
    />
    <ProductInfo :product="product" @add-to-cart="addProductToCart" />
  </div>

  <teleport to="#modals">
    <CarouselModal
      v-if="carouselModalOpen"
      :slides="product.images"
      :opened-image-index="imageClickedIndex"
      @close-product-carousel-modal="carouselModalOpen = !carouselModalOpen"
    />
  </teleport>

  <div class="attribution">
    Challenge by
    <a href="https://www.frontendmentor.io?ref=challenge" target="_blank"
      >Frontend Mentor</a
    >. Coded by
    <a href="https://www.github.com/mtbossa">Mateus Ribeiro Bossa</a>
  </div>
</template>

<script>
import AppHeader from "@/components/AppHeader";
import ProductCarousel from "@/components/ProductCarousel";
import ProductInfo from "@/components/ProductInfo";
import AppCart from "@/components/AppCart";
import CarouselModal from "@/components/Modals/CarouselModal";
import vClickOutside from "click-outside-vue3";

export default {
  name: "App",
  components: {
    AppHeader,
    ProductCarousel,
    ProductInfo,
    AppCart,
    CarouselModal,
  },
  directives: {
    clickOutside: vClickOutside.directive,
  },
  data() {
    return {
      cartOpen: false,
      carouselModalOpen: false,
      imageClickedIndex: 0,
      product: {
        id: 1,
        name: "Fall Limited Edition Sneakers",
        description:
          "These low-profile sneakers are your perfect casual wear companion. Featuring a durable rubber outer sole, they’ll withstand everything the weather can offer.",
        price: 250.0,
        discount: 50,
        manufacturer: "Sneaker Company",
        mainThumbnail: "image-product-1-thumbnail.jpg",
        images: [
          {
            main: "image-product-1.jpg",
            thumbnail: "image-product-1-thumbnail.jpg",
          },
          {
            main: "image-product-2.jpg",
            thumbnail: "image-product-2-thumbnail.jpg",
          },
          {
            main: "image-product-3.jpg",
            thumbnail: "image-product-3-thumbnail.jpg",
          },
          {
            main: "image-product-4.jpg",
            thumbnail: "image-product-4-thumbnail.jpg",
          },
        ],
      },
      cart: [],
    };
  },
  methods: {
    toggleCart() {
      this.cartOpen = !this.cartOpen;
    },

    onClickOutsideCart() {
      this.cartOpen = false;
    },

    addProductToCart(product, quantity) {
      if (quantity < 1) return;

      const item = this.cart.findIndex((x) => x.productId === product.id);

      // Means this product is already in the cart
      if (item !== -1) {
        this.cart[item].quantity += quantity;
      } else {
        const cartItem = {
          productId: product.id,
          name: product.name,
          mainThumbnail: product.mainThumbnail,
          price: this.getRealPrice(product.price, product.discount),
          quantity: quantity,
        };

        this.cart = [...this.cart, cartItem];
      }
    },

    getRealPrice(price, discount) {
      return price * (discount / 100);
    },

    removeFromCart(id) {
      this.cart = this.cart.filter((item) => item.id !== id);
    },

    openCarouselModal(visibleIndex) {
      if (window.window.screen.width < 1024) return;

      this.imageClickedIndex = visibleIndex;
      this.carouselModalOpen = true;
    },
  },
};
</script>

<style>
html {
  font-family: "Kumbh Sans", sans-serif;
  font-size: var(--fs-400);
}

body {
  background-color: var(--color-white);
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

@media (min-width: 1024px) {
  .main-container {
    display: flex;
    margin-top: calc(var(--header-height) + 3.5rem);
    padding: 7rem 18rem;
    align-items: center;
    justify-content: center;
    gap: 6rem;
  }
}
</style>
