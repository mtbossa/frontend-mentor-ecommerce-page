<template>
  <article clas="product-showcase">
    <img
      class="product-showcase__main-image"
      src="@/assets/images/image-product-1.jpg"
      alt=""
    />

    <div
      class="product-showcase__button product-showcase__button--previous"
      @click="previousImage"
    >
      <button class="button-icon">
        <img src="@/assets/images/icon-previous.svg" alt="Previous" />
      </button>
    </div>

    <div
      class="product-showcase__button product-showcase__button--next"
      @click="nextImage"
    >
      <button class="button-icon">
        <img src="@/assets/images/icon-next.svg" alt="Next" />
      </button>
    </div>

    <!-- ou div com background image -->
    <div></div>
  </article>
</template>

<script>
export default {
  methods: {
    previousImage() {
      console.log("previous");
    },
    nextImage() {
      console.log("next");
    },
  },
};
</script>

<style scoped>
.product-showcase {
  position: relative;
}

.product-showcase__button {
  position: absolute;
  top: 200px;
  z-index: 1;
  width: 40px;
  height: 40px;
  background-color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 25px;
  cursor: pointer;
}

.product-showcase__button--previous {
  left: 1rem;
}

.product-showcase__button--next {
  right: 1rem;
}

.button-icon > img {
  width: 8px;
}
</style>
