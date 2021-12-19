<template>
  <div class="preview-image__container">
    <img v-bind="$attrs" alt="Product image" class="preview-image__image" />
    <div
      :class="{ 'preview-image__image-overlay--selected': isSelected }"
      class="preview-image__image-overlay"
    ></div>
  </div>
</template>

<script>
export default {
  props: {
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
  computed: {
    isSelected() {
      return this.visibleIndex === this.index ? true : false;
    },
  },
};
</script>

<style scoped>
.preview-image__image {
  border-radius: 10px;
}

.preview-image__container {
  position: relative;
  display: flex;
  cursor: pointer;
}

.preview-image__image-overlay--selected {
  box-shadow: 0 0 0 3px var(--color-primary-orange);
  background-color: rgba(255, 255, 255, 0.5);
}

.preview-image__image-overlay {
  cursor: pointer;
  width: 100%;
  height: 100%;
  z-index: 999;
  position: absolute;
  top: 0;
  left: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 1;
  border-radius: 10px;
}
.preview-image__image-overlay:hover {
  background-color: rgba(255, 255, 255, 0.5);
}
</style>
