<template>
  <div class="achievments-cards">
    <div ref="swiper" class="swiper-container">
      <div class="swiper-wrapper">
        <button v-for="n in 5" :key="n" class="swiper-slide">
          <div class="slide-content">
            <img src="@/assets/svg/hex.svg" />
            <span>?</span>
          </div>
        </button>
      </div>
    </div>
    <div class="swiper-pagination"></div>
  </div>
</template>

<script lang="ts">
import { Vue, Component } from 'nuxt-property-decorator'
import Swiper, { Pagination, Autoplay } from 'swiper'
import 'swiper/swiper-bundle.min.css'

Swiper.use([Pagination, Autoplay])

@Component
export default class Slider extends Vue {
  mounted() {
    new Swiper(this.$refs.swiper as HTMLElement, {
      slidesPerView: 4,
      spaceBetween: 9,
      loop: true,
      autoplay: {
        delay: 30000,
        disableOnInteraction: false,
      },
      pagination: {
        el: '.swiper-pagination',
        clickable: true,
      },
    })
  }
}
</script>

<style scoped lang="scss">
.achievments-cards {
  position: relative;
  padding-bottom: 20px;
  font-family: 'Hanson';
  color: #ffffff1a;
  font-size: 20px;
  font-weight: 700;

  .swiper-container {
    padding: 10px 12px;
    background: #1d1d2966;
    border-radius: 12px;
    .swiper-wrapper {
      .swiper-slide {
        background: transparent;
        box-shadow: none;
        border: none;
        .slide-content {
          position: relative;
          span {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            padding-right: 5px;
            padding-bottom: 5px;
          }
        }
      }
    }
  }
  .swiper-pagination {
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    gap: 5px;
    align-items: center;
    bottom: 0px;
  }
}
</style>
