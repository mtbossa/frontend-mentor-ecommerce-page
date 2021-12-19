<template>
  <article class="carousel-modal product-carousel">
    <div class="product-carousel__container">
      <CarouselSlide
        v-for="(slide, index) in slides"
        :key="index"
        :image="slide.main"
        :index="index"
        :visible-index="visibleIndex"
      />

      <!-- Mobile button -->
      <button
        class="button-icon product-carousel__button product-carousel__button--previous"
        @click="previousSlide"
      >
        <img src="@/assets/images/icon-previous.svg" alt="Previous" />
      </button>

      <!-- Mobile button -->
      <button
        class="button-icon product-carousel__button product-carousel__button--next"
        @click="nextSlide"
      >
        <img src="@/assets/images/icon-next.svg" alt="Next" />
      </button>
    </div>

    <CarouselPreview
      :slides="slides"
      :visible-index="visibleIndex"
      @preview-clicked="changeProductImage"
    />
  </article>
  <!-- <ProductCarousel class="carousel-modal" :slides="slides" /> -->
</template>

<script>
import CarouselSlide from "@/components/CarouselSlide.vue";
import CarouselPreview from "@/components/CarouselPreview.vue";

export default {
  components: { CarouselSlide, CarouselPreview },
  props: {
    slides: {
      type: Array,
      default() {
        return [];
      },
    },
  },
  data() {
    return { visibleIndex: 0 };
  },
  computed: {
    slidesLength() {
      return this.slides.length;
    },
  },
  methods: {
    previousSlide() {
      this.visibleIndex === 0
        ? (this.visibleIndex = this.slidesLength - 1)
        : this.visibleIndex--;
    },
    nextSlide() {
      this.visibleIndex === this.slidesLength - 1
        ? (this.visibleIndex = 0)
        : this.visibleIndex++;
    },
    changeProductImage(previewIndex) {
      this.visibleIndex = previewIndex;
    },
  },
};
</script>

<style scoped>
.carousel-modal {
  position: absolute;
  width: 28%;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.product-carousel__container {
  position: relative;
}

.product-carousel__button {
  position: absolute;
  z-index: 1;
  width: 40px;
  height: 40px;
  top: 50%;
  transform: translate(-50%, -50%);
  background-color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 25px;
  cursor: pointer;
}

.product-carousel__button--next {
  left: 100%;
}

.button-icon > img {
  width: 10px;
}
</style>
