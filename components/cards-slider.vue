<template>
  <div class="dashboard-wrap-cards">
    <div ref="swiper" class="swiper">
      <div class="swiper-wrapper">
        <div v-for="i in 5" :key="i" class="swiper-slide card-num">
          <div>
            <img :src="getImagePath('cards')" />
          </div>
          <span>****2235</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Vue, Component } from 'nuxt-property-decorator'
import Swiper, { Autoplay } from 'swiper'
import 'swiper/swiper-bundle.min.css'

Swiper.use([Autoplay])

@Component
export default class CardsSlider extends Vue {
  getImagePath(icon: string) {
    return require(`@/assets/svg/${icon}.svg`)
  }

  mounted() {
    new Swiper(this.$refs.swiper as HTMLElement, {
      slidesPerView: 4,
      spaceBetween: 10,
      loop: true,
      autoplay: {
        delay: 2500,
        disableOnInteraction: false,
      },
    })
  }
}
</script>

<style scoped lang="scss">
.dashboard-wrap-cards {
  font-size: 14px;
  font-family: 'Reza Zulmi Alfaizi Sans';
  color: #fff;
  overflow-x: hidden;
  margin-top: 16px;
  margin-bottom: 32px;
  width: 100%;
  position: relative;
  z-index: -1;
  .card-num {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 6px;
    div {
      height: 60px;
      width: 80px;
      border-radius: 8px;
      background: #1d1d2966;
      display: flex;
      align-items: center;
      justify-content: center;
      img {
        height: 40px;
        width: auto;
      }
    }
  }
}

.swiper {
  width: 100%;
}

.swiper-wrapper {
  display: flex;
}
</style>
