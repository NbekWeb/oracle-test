<template>
  <div class="score-cards">
    <div class="emotions-slider">
      <div ref="swiper" class="swiper">
        <div class="swiper-wrapper">
          <div class="swiper-slide" v-for="num in 10" :key="num">
            <img src="@/assets/png/score.png" />
            <h4>Sparkle monkey</h4>
            <span> Flashing your shine, swinging to the top. </span>
          </div>
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
export default class ScoreCards extends Vue {
  mounted() {
    const swiperInstance = new Swiper(this.$refs.swiper as HTMLElement, {
      slidesPerView: 'auto',
      spaceBetween: 40,
      loop: true,
      centeredSlides: true,
      autoplay: {
        delay: 5000,
        disableOnInteraction: false,
      },
      navigation: {
        nextEl: '.swiper-button-next',
        prevEl: '.swiper-button-prev',
      },
      pagination: {
        el: '.swiper-pagination',
        clickable: true,
      },
      on: {
        slideChange: function (this: Swiper) {
          document.querySelectorAll('.swiper-slide').forEach((slide) => {
            ;(slide as HTMLElement).style.transform = 'scale(1)'
            ;(slide as HTMLElement).style.zIndex = '1'
          })
          const activeSlide = this.slides[this.activeIndex]
          if (activeSlide) {
            ;(activeSlide as HTMLElement).style.transform = 'scale(1.3)'
            ;(activeSlide as HTMLElement).style.zIndex = '10'
          }
        },
      },
    })

    swiperInstance.emit('slideChange')
  }
}
</script>

<style scoped lang="scss">
.score-cards {
  font-family: 'Kenyan Coffee';
  color: #fff;
  overflow-x: hidden;
  padding: 50px 0;
}

.emotions-slider {
  position: relative;
  margin: auto;
  max-width: 100%;
}

.swiper {
  width: 100%;
  overflow: visible;
}

.swiper-wrapper {
  display: flex;
}

.swiper-slide {
  display: flex;
  flex-direction: column;
  gap: 4px;
  align-items: center;
  color: #fff;
  font-size: 24px;
  width: 150px;
  height: auto;
  border-radius: 12px;
  transition: transform 0.3s ease-in-out;
  font-family: 'Kenyan Coffee';
  text-align: center;
  img {
    width: 100%;
    height: auto;
  }
  h4 {
    font-size: 20px;
    font-weight: 700;
    margin-top: 8px;
  }
  span {
    font-size: 12px;
  }
}
</style>
