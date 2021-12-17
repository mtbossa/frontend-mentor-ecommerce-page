<template>
  <img
    alt="Product image"
    class="preview-image"
    :class="{ 'preview-image--selected': isSelected }"
  />
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
.preview-image {
  width: 30%;
  border-radius: 10px;
  cursor: pointer;
}

.preview-image:hover {
  opacity: 0.3;
}

.preview-image--selected {
  border: 3px solid var(--color-primary-orange);
}
</style>
