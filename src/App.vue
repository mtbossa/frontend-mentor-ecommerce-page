<template>
  <header>
    <img src="../images/logo.svg" alt="Sneakers logo" />
    <nav>
      <ul>
        <li>Collections</li>
        <li>Men</li>
        <li>Women</li>
        <li>About</li>
        <li>Contact</li>
      </ul>
    </nav>
    <button>cesto</button>
    <div>
      <p>cesto</p>
      <div>
        <img src="" alt="" />
        <p>Fall Limited Edition Sneakers</p>
        <p>$125.00 x3 <strong>$375.00</strong></p>
      </div>
    </div>
    <img src="../images/image-avatar.png" alt="" />
  </header>

  <article>
    <img src="" alt="" />
    <!-- ou div com background image -->
    <div></div>
  </article>

  <article>
    <h3>Sneaker Company</h3>
    <h1>Fall Limited Edition Sneakers</h1>
    <p>
      These low-profile sneakers are your perfect casual wear companion.
      Featuring a durable rubber outer sole, they’ll withstand everything the
      weather can offer.
    </p>
    <div>
      <h2>$125.00</h2>
      <div>50%</div>
      <h4>$250.00</h4>
    </div>

    <div>
      <div>0</div>
      <button>Add to cart</button>
    </div>
  </article>

  <div class="attribution">
    Challenge by
    <a href="https://www.frontendmentor.io?ref=challenge" target="_blank"
      >Frontend Mentor</a
    >. Coded by
    <a href="https://www.github.com/mtbossa">Mateus Ribeiro Bossa</a>.
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
};
</script>

<style>
:root {
  --color-primary-orange: hsl(26, 100%, 55%);
  --color-primary-pale-orange: hsl(25, 100%, 94%);
  --color-very-dark-blue: hsl(220, 13%, 13%);
  --color-dark-grayish-blue: hsl(219, 9%, 45%);
  --color-grayish-blue: hsl(220, 14%, 75%);
  --color-light-grayish-blue: hsl(223, 64%, 98%);
  --color-white: hsl(0, 0%, 100%);
  --color-black: hsl(0, 0%, 0%);

  --font-size: 16px;
}

html {
  font-family: "Kumbh Sans", sans-serif;
}

body {
  background-color: var(--color-white);
}

.attribution {
  font-size: 11px;
  text-align: center;
}
.attribution a {
  color: hsl(228, 45%, 44%);
}
</style>
