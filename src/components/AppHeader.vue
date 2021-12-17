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
          class="nav__menu-mobile-container nav__menu-mobile-container--full-width"
        >
          <div
            v-click-outside="onClickOutside"
            class="nav__menu-mobile-container"
          >
            <ul class="nav__menu-mobile" role="list">
              <li class="nav__link-mobile">Collections</li>
              <li class="nav__link-mobile">Men</li>
              <li class="nav__link-mobile">Women</li>
              <li class="nav__link-mobile">About</li>
              <li class="nav__link-mobile">Contact</li>
            </ul>
          </div>
        </div>

        <div class="nav__menu-container">
          <ul class="nav__menu" role="list">
            <li class="nav__link noselect">Collections</li>
            <li class="nav__link noselect">Men</li>
            <li class="nav__link noselect">Women</li>
            <li class="nav__link noselect">About</li>
            <li class="nav__link noselect">Contact</li>
          </ul>
        </div>
      </div>
      <div class="nav__user-container">
        <div class="nav__cart">
          <div
            v-if="cartProductAmount > 0"
            class="nav__product-amount noselect"
          >
            {{ cartProductAmount }}
          </div>
          <button class="nav__icon-cart button-icon">
            <img
              src="@/assets/images/icon-cart.svg"
              alt="Cart"
              @click="$emit('cartClicked')"
            />
          </button>
        </div>

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
import vClickOutside from "click-outside-vue3";

export default {
  directives: {
    clickOutside: vClickOutside.directive,
  },
  props: {
    cartProductAmount: {
      type: Number,
      default: 0,
    },
  },
  emits: ["cartClicked", "openMenu"],
  data() {
    return {
      visibleMenu: false,
    };
  },
  methods: {
    showMenu() {
      this.visibleMenu = !this.visibleMenu;
      this.$emit("openMenu");
    },
    onClickOutside() {
      this.visibleMenu = false;
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
  z-index: 120;
}

.nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
}

.nav__container {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.nav__icon-open {
  margin-top: 0.3rem;
}

.nav__icon-close {
  position: absolute;
  z-index: 100;
}

/* MENU */
.nav__menu {
  display: none;
}

/* MOBILE MENU */
.nav__menu-mobile-container {
  position: fixed;
  top: 0;
  left: 0;
  min-height: 100vh;
  min-width: 70%;
  background-color: var(--color-white);
  padding: 0 2rem;
  z-index: 90;
}

.nav__menu-mobile-container--full-width {
  min-width: 100vw;
  background-color: rgba(0, 0, 0, 0.8);
}

.nav__menu-mobile {
  margin: calc(var(--header-height) + 2rem) 0;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  padding: 0;
}

.nav__link-mobile {
  font-weight: 700;
  cursor: pointer;
}

.nav__user-container {
  display: flex;
  align-items: center;
  gap: 1.55rem;
}

.nav__cart {
  position: relative;
}

.nav__product-amount {
  background-color: var(--color-primary-orange);
  display: inline-block;
  padding: 0 10px;
  font-size: 0.7rem;
  border-radius: 10px;
  color: var(--color-white);
  position: absolute;
  left: 10px;
  bottom: 20px;
  font-weight: 700;
}

.nav__user-photo {
  cursor: pointer;
  width: 1.5rem;
}

.nav__user-photo:hover {
  box-shadow: 0 0 0 2px var(--color-primary-orange);
  border-radius: 50%;
}

@media (min-width: 1024px) {
  .header {
    min-height: calc(var(--header-height) + 2rem);
    border-bottom: 1px solid var(--color-light-grayish-blue);
    padding: 2rem 10rem;
  }

  .nav__menu-container {
    margin-left: 2rem;
  }

  .nav__menu {
    display: flex;
    gap: 2rem;
  }

  .nav__link {
    color: var(--color-dark-grayish-blue);
    font-size: var(--fs-300);
    cursor: pointer;
    position: relative;
  }

  .nav__link:hover::after {
    content: "";
    background-color: var(--color-primary-orange);
    width: 100%;
    height: 4px;
    display: block;
    position: absolute;
    border-radius: 5px;
    top: calc(var(--header-height) + 6px);
  }

  .nav__icon-open {
    display: none;
  }

  .nav__user-container {
    display: flex;
    align-items: center;
    gap: 3rem;
  }

  .nav__user-photo {
    width: 3rem;
  }
}
</style>
