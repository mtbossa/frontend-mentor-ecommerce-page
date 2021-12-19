<template>
  <button class="app-button app-button--orange">
    <img
      v-if="icon"
      class="app-button__icon"
      :src="getImgUrl(icon)"
      :alt="alt"
    />
    <slot></slot>
  </button>
</template>

<script>
export default {
  props: {
    icon: {
      type: String,
      default() {
        return "";
      },
    },
    alt: {
      type: String,
      default() {
        return "";
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
.app-button {
  align-items: center;
  display: flex;
  flex-direction: row;
  justify-content: center;
  gap: 1rem;
  width: 100%;
  border: none;
  cursor: pointer;
  font-weight: 700;
  font-size: 1rem;
  border-radius: var(--border-radius-size);
}

.app-button--orange {
  background-color: var(--color-primary-orange);
  color: var(--color-white);
}

.app-button--orange-box-shadow {
  box-shadow: 0 5px 20px 0 hsla(26, 100%, 55%, 0.418);
}

.app-button--orange:hover {
  background-color: rgb(255, 172, 108);
}
</style>
