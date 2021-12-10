<template>
  <article clas="product-showcase">
    <img
      class="product-showcase__main-image"
      src="@/assets/images/image-product-1.jpg"
      alt=""
    />

    <button
      class="product-showcase__icon-previous button-icon button-icon--rounded-bg"
    >
      <img src="@/assets/images/icon-previous.svg" alt="" />
    </button>

    <button
      class="product-showcase__icon-next button-icon button-icon--rounded-bg"
    >
      <img src="@/assets/images/icon-next.svg" alt="" />
    </button>

    <!-- ou div com background image -->
    <div></div>
  </article>
</template>

<script>
export default {};
</script>

<style scoped>
.product-showcase {
  position: relative;
}

.product-showcase__icon-previous {
  position: absolute;
  top: 200px;
  left: 2.4rem;
  z-index: 1;
}

.product-showcase__icon-next {
  position: absolute;
  top: 200px;
  right: 2.4rem;
  z-index: 1;
}
</style>
