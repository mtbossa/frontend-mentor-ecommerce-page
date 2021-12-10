<template>
  <header class="header">
    <nav class="container nav">
      <div class="nav__container">
        <button
          v-if="visibleMenu"
          class="nav__icon-close button-icon"
          @click="showMenu"
        >
          <img src="@/assets/images/icon-close.svg" alt="X" />
        </button>
        <button
          v-if="!visibleMenu"
          class="nav__icon-open button-icon"
          @click="showMenu"
        >
          <img src="@/assets/images/icon-menu.svg" alt="" />
        </button>
        <img src="@/assets/images/logo.svg" alt="Sneakers logo" />

        <div
          v-if="visibleMenu"
          class="nav__menu-container nav__menu-container--full-width"
        >
          <div class="nav__menu-container">
            <ul class="nav__menu">
              <li class="nav__link">Collections</li>
              <li class="nav__link">Men</li>
              <li class="nav__link">Women</li>
              <li class="nav__link">About</li>
              <li class="nav__link">Contact</li>
            </ul>
          </div>
        </div>
      </div>
      <div class="nav__user-container">
        <button class="nav__icon-cart button-icon">
          <img src="@/assets/images/icon-cart.svg" alt="Cart" />
        </button>
        <img
          src="@/assets/images/image-avatar.png"
          alt="User profile photo"
          class="nav__user-photo"
        />
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  data() {
    return {
      visibleMenu: false,
    };
  },
  methods: {
    showMenu() {
      this.visibleMenu = !this.visibleMenu;
    },
  },
};
</script>

<style scoped>
.header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  min-height: var(--header-height);
  display: flex;
  background-color: var(--color-white);
  z-index: 100;
}

.nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
}

.nav__icon-open {
  margin-right: 10px;
}

.nav__icon-close {
  position: absolute;
  z-index: 100;
}

.nav__menu-container {
  position: fixed;
  top: 0;
  left: 0;
  min-height: 100vh;
  min-width: 70%;
  background-color: var(--color-white);
  padding: 0 2rem;
}

.nav__menu-container--full-width {
  min-width: 100vw;
  background-color: rgba(0, 0, 0, 0.8);
}

.nav__menu {
  margin: calc(var(--header-height) + 2rem) 0;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.nav__link {
  font-weight: 700;
  cursor: pointer;
}

.nav__user-container {
  display: flex;
  align-items: center;
  gap: 1.55rem;
}

.nav__user-photo {
  width: 1.5rem;
}
</style>
