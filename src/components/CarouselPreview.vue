<template>
  <div class="carousel-preview">
    <PreviewImage
      v-for="(slide, index) in slides"
      :key="index"
      :src="getImgUrl(slide.thumbnail)"
      :index="index"
      :visible-index="visibleIndex"
      @click="$emit('previewClicked', index)"
    />
  </div>
</template>

<script>
import PreviewImage from "./PreviewImage.vue";

export default {
  components: { PreviewImage },
  props: {
    slides: {
      type: Array,
      default() {
        return [];
      },
    },
    visibleIndex: {
      type: Number,
      default() {
        return 0;
      },
    },
  },
  emits: ["previewClicked"],
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
}
</style>
