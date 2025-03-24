<template>
  <div class="card-account">
    <div class="go-back">
      <button class="btn back-btn">
        <img src="@/assets/svg/arrow-back.svg" />
      </button>
      <h3 class="main-title">BTC Account</h3>
    </div>
    <div class="qr-code">
      <img src="@/assets/png/qr.png" />
    </div>
    <div class="info-wrap">
      <span> btc9104391491309490134013094913094 </span>
      <img src="@/assets/svg/Refresh.svg" />
      <img src="@/assets/svg/Copy.svg" @click="copyAddress" />
      <img src="@/assets/svg/forward.svg" @click="shareAddress" />
    </div>
    <p class="title-send">Send only BTC coins on BTC network to this address</p>
    <div class="wrap-withdraw">
      <button class="btn">
        <img src="@/assets/svg/arrow-round.svg" />
        External Withdrawal
      </button>
      <button class="btn">
        <img src="@/assets/svg/arrow-round.svg" class="rotate-180" />
        Internal Transfer
      </button>
    </div>
    <score-card :score="score" />
    <div class="wrap-crypto">
      <button v-for="(crypto, i) of cryptos" :key="i" class="crypto-card">
        <div class="main-card">
          <span class="blur"></span>
          <img :src="getImagePath(crypto.img)" />
          <h4>{{ crypto.title }}</h4>
        </div>
        <span>{{ crypto.subtitle }}</span>
      </button>
    </div>
    <button class="crypto-banner">
      <img src="@/assets/png/crypto-banner.png" />
    </button>

    <div class="wrap-detail">
      <h3>Details</h3>
      <div class="detail-cards">
        <button v-for="(detail, i) of details" :key="i">
          <span> {{ detail }} </span>
          <img :src="getImagePath('chevron')" />
        </button>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'

@Component({
  components: {},
})
export default class CardAccount extends Vue {
  btcAddress = 'btc9104391491309490134013094913094'

  cryptos = [
    {
      img: 'two-arrow',
      title: 'Exchange Crypto to Fiat',
      subtitle: 'Get the best P2P offers right now!',
    },
    {
      img: 'swap',
      title: 'SWAP Crypto to Crypto',
      subtitle: 'Exchange Crypto2Crypto with Oracle Swap',
    },
  ]

  score = {
    img: 'baraban',
    title: 'Your transactions',
    contextTop: 'Your Expenses MTD: ',
    textRed: '$70,923',
    contextBottom: 'Your Deposits MTD: ',
    textGreen: '$105,921',
    to: '/card-account',
  }

  details = ['Limits', 'Fees', 'history']

  getImagePath(icon: string) {
    return require(`@/assets/svg/${icon}.svg`)
  }

  copyAddress() {
    navigator.clipboard.writeText(this.btcAddress)
  }

  shareAddress() {
    if (navigator.share) {
      navigator.share({
        title: 'BTC Address',
        text: `Send BTC to this address: ${this.btcAddress}`,
      })
    }
  }

  layout() {
    return 'mobile'
  }
}
</script>
<style scoped lang="scss">
.card-account {
  color: #fff;
  font-size: 14px;
  .main-title {
    font-size: 16px;
    font-family: 'Hanson';
    text-transform: uppercase;
    font-weight: 700;
  }

  .go-back {
    display: flex;
    align-items: center;
    margin: 12px 0;
    position: relative;
    height: 40px;

    .back-btn {
      position: absolute;
      left: 0;
      top: 0;
      width: 40px;
      height: 100%;
      border-radius: 50%;
      background: transparent;
      img {
        width: 8px;
      }
    }
    h3 {
      flex-grow: 1;
      display: flex;
      justify-content: center;
    }
  }
  .qr-code {
    display: flex;
    justify-content: center;
    width: 100%;
    padding-bottom: 30px;
    img {
      height: 260px;
      width: auto;
    }
  }
  .info-wrap {
    width: 100%;
    height: 40px;
    border-radius: 8px;
    background: #121119;
    padding: 10px 12px;
    display: flex;
    gap: 10px;
    span {
      overflow: hidden;
      text-overflow: ellipsis;
      white-space: nowrap;
      display: block;
      max-width: 100%;
      text-transform: uppercase;
      font-size: 16px;
      font-family: 'Evolventa';
    }
    img {
      height: 24px;
      width: auto;
    }
  }
  .title-send {
    line-height: 160%;
    font-family: 'Reza Zulmi Alfaizi Sans';
    margin: 12px 0 20px 0;
    opacity: 0.5;
  }
  .wrap-withdraw {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 8px;
    margin-bottom: 32px;

    .btn {
      height: 40px;
      padding: 10px;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 6px;
      background: #1d1d29;
      color: #fff;
      font-family: 'Reza Zulmi Alfaizi Sans';
      font-size: 12px;
      img {
        height: 20px;
        width: auto;
      }
      .rotate-180 {
        transform: rotate(180deg);
      }
    }
  }
  .wrap-crypto {
    margin: 32px 0;
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 12px;
    .crypto-card {
      width: 100%;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 8px;
      span {
        font-family: 'Kenyan Coffee';
        font-size: 12px;
        font-weight: 400;
        text-transform: none;
      }
      border: none;
      box-shadow: none;
      background: none;
      color: #fff;
      height: auto;
      .main-card {
        width: 100%;
        height: 120px;
        border-radius: 12px;
        position: relative;
        background: rgba(29, 29, 41, 0.4);
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        gap: 8px;
        img {
          width: auto;
          height: 60px;
        }
        h4 {
          font-family: 'Kenyan Coffee';
          font-size: 20px;
        }

        .blur {
          width: 54px;
          height: 40px;
          position: absolute;
          top: 0;
          left: 50%;
          transform: translateX(-50%);
          filter: blur(60px);
          background: #f17d2f;
        }
      }
    }
  }
  .crypto-banner {
    width: 100%;
    height: auto;
    margin-bottom: 32px;
    border: none;
    box-shadow: none;
    background: none;
    border-radius: none;
    img {
      width: 100%;
    }
  }
  .wrap-detail {
    font-family: 'Hanson';
    font-weight: 700;
    text-transform: uppercase;
    h3 {
      font-size: 20px;
      margin-bottom: 16px;
    }
    .detail-cards {
      display: flex;
      flex-direction: column;
      gap: 10px;
      button {
        background: #1d1d2966;
        border-radius: 10px;
        color: #fff;
        height: 48px;
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 0 12px;
        font-size: 16px;
        border: none;
        box-shadow: none;
        img {
          width: 24px;
          height: auto;
        }
      }
    }
  }
}
</style>
