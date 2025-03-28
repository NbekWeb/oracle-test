<template>
  <div class="transfer-accounts">
    <h3>Select a transfer account</h3>
    <div ref="swiper" class="swiper-container">
      <div class="swiper-wrapper">
        <div v-for="(account, i) of accounts" :key="i" class="swiper-slide">
          <div class="slide-content account-card">
            <img :src="getImagePath(account.img)" />
            <div class="main-context">
              <div>
                <span class="context-title">{{ account.title }}</span>
                <span class="sub-title">{{ account.subtitle }}</span>
              </div>
              <span class="account-num">{{ account.cardNum }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="swiper-pagination-accounts"></div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'
// @ts-ignore

import Swiper, { Pagination } from 'swiper'
import 'swiper/swiper-bundle.min.css'

Swiper.use([Pagination])

@Component({
  components: {},
})
export default class transferAccounts extends Vue {
  accounts = [
    {
      img: 'coin1',
      title: '0,015424 BTC',
      subtitle: '(≈ $1.456)',
      cardNum: 'BTC Account: ***2235',
    },
    {
      img: 'coin2',
      title: '1 LTC',
      subtitle: '(≈ $1.456)',
      cardNum: 'LTC Account: ***2235',
    },
    {
      img: 'coin3',
      title: '15 ETH',
      subtitle: '(≈ $1.456)',
      cardNum: 'ETH Account: ***2235',
    },
    {
      img: 'coin4',
      title: '15 UDT',
      subtitle: '(≈ $15)',
      cardNum: 'USDT Account: ***2235',
    },
  ]

  getImagePath(icon: string) {
    return require(`@/assets/svg/${icon}.svg`)
  }

  mounted() {
    new Swiper(this.$refs.swiper as HTMLElement, {
      slidesPerView: 1,
      spaceBetween: 9,
      loop: true,

      pagination: {
        el: '.swiper-pagination-accounts',
        clickable: true,
      },
    })
  }
}
</script>
<style lang="scss">
.transfer-accounts {
  margin: 20px 0;
  position: relative;
  h3 {
    margin-bottom: 15px;
    font-family: 'Hanson';
    font-size: 14px;
    text-transform: uppercase;
  }
  .account-card {
    display: flex;
    gap: 16px;
    padding: 12px;
    border-radius: 12px;
    background: #1e1d26;
    color: #fff;
    img {
      height: 68px;
      width: auto;
    }
    .main-context {
      height: 100%;
      width: 100%;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      gap: 8px;
      font-size: 14px;
      margin-bottom: 20px;
      div {
        display: flex;
        align-items: center;
        gap: 6px;
        .context-title {
          font-family: 'Hanson';
          font-weight: 700;
          text-transform: uppercase;
        }
        .sub-title {
          font-family: 'Evolventa';
        }
      }
      .account-num {
        display: flex;
        padding: 6px 10px;
        max-width: max-content;
        border-radius: 8px;
        background: #191823;
        font-family: 'Reza Zulmi Alfaizi Sans';
      }
    }
  }
  .swiper-pagination-accounts {
    left: -50%;
    transform: translateX(50%);
    display: flex;
    gap: 5px;
    align-items: center;
    padding-top: 20px;
  }
}
</style>
