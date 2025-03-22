<template>
  <div class="dashboard-wrap">
    <div class="wrap-banner">
      <banner-cards />
    </div>
    <div class="dashboard-wrap-coins tr-scrollbar">
      <btc-card v-for="i in 3" :key="i" />
    </div>
    <div class="dashboard-wrap-icons">
      <div v-for="(icon, i) of icons" :key="i" class="card-icon">
        <div>
          <img :src="getImagePath(icon.icon)" />
        </div>
        <span>{{ icon.title }}</span>
      </div>
    </div>
    <button class="btn scan-btn">
      <img src="@/assets/svg/qr.svg" />
      SCAN QR
    </button>
    <div class="dashboard-wrap-scores">
      <score-card v-for="(score, i) of scores" :key="i" :score="score" />

    </div>
    <div class="">
      <h3 class="main-title">Your ACCOUNTS</h3>
      <div class="dashboard-wrap-accounts">
        <div v-for="(account, i) of accounts" :key="i" class="account-card">
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
    <img src="@/assets/png/features.png" class="sub-banner" />
    <div>
      <h3 class="main-title">Prepaid cards</h3>
      <div class="dashboard-wrap-cards">
        <div v-for="i in 4" :key="i" class="card-num">
          <div>
            <img :src="getImagePath('cards')" />
          </div>
          <span>****2235</span>
        </div>
      </div>
    </div>
    <div>
      <h3 class="main-title">Oracle's Service</h3>
      <div class="dashboard-wrap-services">
        <div v-for="(service, i) of services" :key="i" class="service-card">
          <img
            :src="getImagePath(service.img)"
            :class="i == 1 && 'rotate-45'"
          />
          <div class="service-content">
            <div class="context">
              <span class="service-title">{{ service.title }}</span>
              <span>{{ service.content }}</span>
            </div>
            <button class="btn service-btn">
              {{ service.btn }}
              <img :src="getImagePath('chevron')" />
            </button>
          </div>
        </div>
        <div class="third-card">
          <div class="wrap-card">
            <img :src="getImagePath('p2p')" />
            <div class="context">
              <span class="service-title">P2P MARKET</span>
              <div>
                <span>Ongoing Exchanges as a Buyer - 1</span>
                <span>Your Exchange Active Listings: 15</span>
                <span class="text-red">Ongoing Disputes: 0</span>
              </div>
            </div>
          </div>
          <button class="btn service-btn">
            EXCHANGE #9012: ACTION REQUIRED!
            <img :src="getImagePath('chevron')" />
          </button>
        </div>
      </div>
    </div>
    <div class="wrap-btcs">
      <h3 class="main-title">Swap</h3>
      <div class="dashboard-wrap-coins tr-scrollbar">
        <btc-card v-for="i in 3" :key="i" />
      </div>
    </div>
    <div class="wrap-btn">
      <button class="btn crypto-btn">
        <img :src="getImagePath('crypto')" />
        Create a new Crypto Account
      </button>
    </div>
    <navigation-bottom />
  </div>
</template>
<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'
// @ts-ignore
import ArrowBackIcon from '@/assets/svg/arrow-back.svg?inline'
import BlockTitleOracle from '~/components/block-title-oracle.vue'

@Component({
  components: {
    ArrowBackIcon,
    BlockTitleOracle,
  },
})
export default class DashboardPage extends Vue {
  icons = [
    { icon: 'send', title: 'Transfer' },
    { icon: 'p2p', title: 'P2P' },
    { icon: 'swap', title: 'SWAP' },
    { icon: 'escrow2', title: 'Escrow' },
    { icon: 'mixer', title: 'Mixer' },
    { icon: 'deposit', title: 'Deposit' },
  ]

  scores = [
    {
      img: 'baraban',
      title: 'Your transactions',
      contextTop: 'Your Expenses MTD: ',
      textRed: '$70,923',
      contextBottom: 'Your Deposits MTD: ',
      textGreen: '$105,921',
    },
    {
      img: 'monkey',
      title: 'Current score: 151',
      contextTop: 'Points Lost: ',
      textRed: '- 15',
      contextBottom: 'Points Gained: ',
      textGreen: '+ 15',
    },
  ]

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

  services = [
    {
      img: 'mixer',
      title: 'Oracle Crypto Mixing',
      content: 'Current Mixes: 7',
      btn: 'Action required',
    },
    {
      img: 'cards',
      title: 'Oracle pay',
      content: 'Your way to collect payments',
      btn: ' Open',
    },
  ]

  getImagePath(icon: string) {
    return require(`@/assets/svg/${icon}.svg`)
  }

  getImagePng(img: string) {
    return require(`@/assets/png/${img}.png`)
  }

  layout() {
    return 'mobile'
  }
}
</script>

<style lang="scss">
.dashboard-wrap {
  color: #fff;
  padding-bottom: 70px;
  .wrap-banner {
    padding: 12px 0 20px 0;
  }
  &-coins {
    display: flex;
    gap: 10px;
    width: 100%;
    overflow-x: auto;
    padding-bottom: 24px;
  }
  &-icons {
    display: flex;
    justify-content: space-between;
    gap: 8px;
    .card-icon {
      display: flex;
      flex-direction: column;
      gap: 6px;
      align-items: center;
      font-size: 14px;
      font-family: 'Kenyan Coffee';
      width: 52px;
      div {
        width: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        padding: 6px;
        border-radius: 10px;
        background: #1d1d29;
        height: 52px;
        img {
          height: 100%;
        }
      }
    }
  }
  .scan-btn {
    height: 44px;
    width: 100%;
    background: transparent;
    margin-top: 24px;
    margin-bottom: 12px;
    color: #fff;
    font-family: 'Hanson';
    font-weight: 700;
    display: flex;
    gap: 8px;
    align-items: center;
    justify-content: center;
    img {
      width: 20px;
      height: auto;
    }
  }
  &-scores {
    display: flex;
    flex-direction: column;
    gap: 12px;
    margin-bottom: 32px;

  }
  &-accounts {
    margin-top: 16px;
    margin-bottom: 32px;
    display: flex;
    flex-direction: column;
    gap: 10px;
    .account-card {
      display: flex;
      gap: 16px;
      padding: 12px;
      border-radius: 12px;
      background: #1d1d2966;
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
  }
  .sub-banner {
    width: 100%;
    height: auto;
    margin-bottom: 32px;
  }
  &-cards {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-top: 16px;
    margin-bottom: 32px;
    width: 100%;
    font-size: 14px;
    font-family: 'Reza Zulmi Alfaizi Sans';
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
  &-services {
    margin-top: 16px;
    margin-bottom: 32px;
    display: flex;
    gap: 10px;
    flex-direction: column;
    font-size: 14px;
    font-family: 'Reza Zulmi Alfaizi Sans';
    .service-card {
      padding: 16px;
      border-radius: 12px;
      background: #1d1d2966;
      display: flex;
      gap: 16px;
      align-items: center;

      img {
        height: auto;
        width: 72px;
      }
      .service-content {
        display: flex;
        flex-direction: column;
        gap: 15px;
        .context {
          display: flex;
          flex-direction: column;
          gap: 5px;
          .service-title {
            font-weight: 700;
            font-family: 'Hanson';
            text-transform: uppercase;
          }
        }
        .service-btn {
          display: flex;
          align-items: center;
          gap: 4px;
          height: 36px;
          max-width: max-content;
          background: transparent;
          color: #fff;
          padding: 0 8px;
          font-family: 'Reza Zulmi Alfaizi Sans';
          font-size: 13px;
          img {
            width: 16px;
          }
        }
      }
    }
    .third-card {
      padding: 16px;
      border-radius: 12px;
      background: #1d1d2966;
      display: flex;
      flex-direction: column;
      gap: 16px;
      align-items: center;
      .wrap-card {
        display: flex;
        gap: 16px;
        align-items: center;
        img {
          height: auto;
          width: 72px;
        }
        .context {
          display: flex;
          flex-direction: column;
          gap: 8px;
          .service-title {
            font-family: 'Hanson';
            text-transform: uppercase;
            font-weight: 700;
          }
          div {
            display: flex;
            flex-direction: column;
            gap: 4px;
          }
        }
      }
      .service-btn {
        display: flex;
        align-items: center;
        gap: 4px;
        height: 36px;
        width: 100%;
        background: transparent;
        color: #fff;
        padding: 0 8px;
        font-family: 'Reza Zulmi Alfaizi Sans';
        font-size: 13px;
        img {
          width: 16px;
        }
      }
    }
  }
  .wrap-btcs {
    display: flex;
    flex-direction: column;
    gap: 16px;
  }
  .wrap-btn {
    padding: 0 12px 12px 12px;

    .crypto-btn {
      width: 100%;
      height: 48px;
      background: #f64e2a;
      color: #fff;
      font-family: 'Kenyan Coffee';
      font-size: 16px;

      img {
        height: 22px;
        width: auto;
      }
    }
  }
  .text-red {
    color: #ff5b5b;
  }
  .text-green {
    color: #7eff61;
  }
  .rotate-45 {
    transform: rotate(-45deg);
  }
  .main-title {
    font-size: 16px;
    font-family: 'Hanson';
    text-transform: uppercase;
    font-weight: 700;
  }
}
</style>
