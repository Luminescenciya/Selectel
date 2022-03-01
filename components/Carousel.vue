<template>
  <div class="carousel">
    <a-carousel v-if="isCarouselMounted">
      <div
        v-for="(page, i) in pages"
        :key="i"
        class="carousel-page"
        :style="{ 'background-image': 'url(' + page.image + ')' }"
      >
        <div class="carousel-page__wrapper">
          <span class="carousel-page__title">{{ page.title }}</span>
          <span class="carousel-page__description">{{ page.description }}</span>
        </div>
      </div>
    </a-carousel>
    <a-spin v-else class="carousel__spin-bg">
      <a-icon slot="indicator" type="loading" size="large" spin />
    </a-spin>
  </div>
</template>

<script>
export default {
  props: {
    pages: { type: Array, default: null },
  },
  data() {
    return {
      isCarouselMounted: false,
    }
  },
  mounted() {
    this.$nextTick(() => {
      this.isCarouselMounted = true
    })
  },
}
</script>

<style lang="scss" scoped>
%carousel-height {
  height: 546px;
  @media (max-width: 768px) {
    height: 280px;
  }
}
.carousel {
  @extend %carousel-height;
  &__spin-bg {
    display: flex;
    justify-content: center;
    align-items: center;

    width: 100%;
    height: 100%;
  }
  &-page {
    background-size: cover;
    background-repeat: no-repeat;
    background-position: 50%;
    @extend %carousel-height;

    color: #ffffff;

    position: relative;

    &__title {
      font-weight: 500;
      font-size: 32px;
      line-height: 44px;
      @media (max-width: 768px) {
        font-size: 20px;
        line-height: 27px;
      }
    }
    &__description {
      width: 453px;
      margin-top: 24px;

      font-weight: normal;
      font-size: 16px;
      line-height: 22px;
      @media (max-width: 768px) {
        width: auto;

        font-size: 14px;
        line-height: 19px;
      }
    }
    &__wrapper {
      display: flex;
      flex-direction: column;
      align-items: flex-start;
      text-align: left;

      width: 925px;
      box-sizing: border-box;

      position: absolute;
      left: 0;
      right: 0;
      bottom: 100px;
      margin-left: auto;
      margin-right: auto;
      @media (max-width: 990px) {
        width: 700px;
      }
      @media (max-width: 768px) {
        width: 100%;
        padding: 0 15px;
        bottom: 35px;
      }
    }
  }
}
</style>
