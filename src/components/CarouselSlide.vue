<template>
  <img
    v-show="visibleIndex === index"
    class="carousel-slide"
    :src="getImgUrl(image)"
    alt="Product image"
  />
</template>

<script>
export default {
  props: {
    image: {
      type: String,
      default() {
        return "";
      },
    },
    index: {
      type: Number,
      default() {
        return 0;
      },
    },
    visibleIndex: {
      type: Number,
      default() {
        return 0;
      },
    },
  },
  methods: {
    getImgUrl(pic) {
      return require(`../assets/images/${pic}`);
    },
  },
};
</script>

<style scoped>
@media (min-width: 1024px) {
  .carousel-slide {
    border-radius: 25px;
  }
}
</style>
