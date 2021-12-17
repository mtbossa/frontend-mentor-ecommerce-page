<template>
  <div class="carousel-preview">
    <img
      v-for="(slide, index) in slides"
      :key="index"
      :src="getImgUrl(slide.thumbnail)"
      alt="Product image"
    />
  </div>
</template>

<script>
export default {
  props: {
    slides: {
      type: Array,
      default() {
        return [];
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
.carousel-preview {
  display: none;
}

@media (min-width: 1024px) {
  .carousel-preview {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 3rem;
    margin-top: 3rem;
  }

  .carousel-preview > img {
    width: 30%;
    border-radius: 25px;
    cursor: pointer;
  }
}
</style>
