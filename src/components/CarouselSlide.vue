<template>
  <img v-show="visibleIndex === index" :src="getImgUrl(image)" alt="" />
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

<style></style>
