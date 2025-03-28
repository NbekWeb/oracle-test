<template>
  <div class="prepaid-page">
    <button class="back-btn btn">
      <img src="@/assets/svg/arrow-back.svg" />
    </button>
    <banner-cards />
    <div class="credit-cards tr-scrollbar">
      <credit-card />
      <credit-card type="black" />
    </div>
    <div class="border-gradient">
      <div class="rules-card">
        <span class="blur"></span>
        <template v-for="(rule, i) of rules">
          <div :key="i" @click="toggleOpen(rule.id)">
            <img :src="getImagePath(rule.icon)" />
            <span>
              {{ rule.title }}
              {{ open }}
            </span>
          </div>
        </template>
      </div>
    </div>
    <div class="border-gradient">
      <div class="history-card">
        <span class="blur"></span>
        <h3>replenishment history</h3>
        <div class="wrap-content">
          <span>December</span>
          <span class="price">$3,129</span>
        </div>
        <div class="bar-chart">
          <span class="violet"></span>
          <span class="yellow"></span>
          <span class="green"></span>
          <span class="orange"></span>
        </div>
      </div>
    </div>
    <div class="border-gradient requisites-wrap">
      <div class="requisites-card">
        <div class="title">
          <h3>requisites</h3>
          <span>Show</span>
        </div>
        <div class="card-bg">•••• •••• •••• 1234</div>
        <div class="cards-info">
          <div class="card-bg">•• / ••</div>
          <div class="card-bg">•••</div>
        </div>
      </div>
    </div>
    <div class="border-gradient">
      <div class="deposit-card">
        <h3>DEPOSIT MONEY</h3>
        <nuxt-link class="account-card" to="/">
          <img :src="getImagePath(account.img)" />
          <div class="main-context">
            <div>
              <span class="context-title">{{ account.title }}</span>
              <span class="sub-title">{{ account.subtitle }}</span>
            </div>
            <span class="account-num">{{ account.cardNum }}</span>
          </div>
        </nuxt-link>
        <div class="wrap-usd">
          <button>
            <img :src="getImagePath('left-arrow')" />
          </button>
          <div class="wrap-forms">
            <form class="usdt-form">
              <input v-model="amountValue" type="text" placeholder="100" />
              <img :src="getImagePath('usdt')" />
            </form>
            <div class="equal">≈</div>
            <div class="equal-form">
              <form>
                <span>$</span>
                <input v-model="amountValue" type="text" placeholder="100" />
              </form>
              <span>Commission 1,06 $</span>
            </div>
          </div>
          <button>
            <img :src="getImagePath('left-arrow')" class="right" />
          </button>
        </div>
        <button class="btn-deposit btn">DEPOSIT</button>
        <div class="wrap-details">
          <h2>Details</h2>
          <div class="wrap-details-card">
            <div>
              <span>CHANGE PIN CODE</span>
              <img :src="getImagePath('chevron')" />
            </div>
            <div>
              <span>Fees </span>
              <img :src="getImagePath('chevron')" />
            </div>
          </div>
          <button class="btn-issue btn">ISSUE A NEW CARD</button>
        </div>
      </div>
    </div>
    <template v-for="i in 2">
      <div
        :key="i"
        class="modal"
        :class="
          ((i == 1 && open == 'block') || (i == 2 && open == 'issue')) && 'open'
        "
        @click="close"
      >
        <div class="modal-content" @click.stop>
          <p>
            {{
              i == 1
                ? 'ARE YOU SURE TO BLOCK YOUR CARD?'
                : 'ARE YOU SURE TO REISSUE YOUR CARD?'
            }}
          </p>
          <div class="wrap-btns">
            <button class="btn" @click="close">YES</button>
            <button class="cancel btn" @click="close">CanCel</button>
          </div>
        </div>
      </div>
    </template>

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
export default class PrepaidPage extends Vue {
  getImagePath(icon: string) {
    return require(`@/assets/svg/${icon}.svg`)
  }

  open = ''

  toggleOpen(id: string) {
    this.open = id
  }

  close() {
    this.open = ''
  }

  ruleClick = (id: string) => {
    if (id === 'block') {
      this.toggleOpen(id)
    }
  }

  amount = '100'

  get amountValue() {
    return this.amount.replace(/\B(?=(\d{3})+(?!\d))/g, ' ')
  }

  set amountValue(value) {
    this.amount = value.replace(/\s/g, '').replace(/[^0-9]/g, '')
  }

  rules = [
    {
      icon: 'lock',
      title: 'Block',
      id: 'block',
    },
    {
      icon: 'bitcoin-card',
      title: 'Reissue',
      id: 'issue',
    },
    {
      icon: 'card-coin',
      title: ' Withdraw everything',
      id: 'withdraw',
    },
  ]

  account = {
    img: 'coin1',
    title: '0,015424 BTC',
    subtitle: '(≈ $1.456)',
    cardNum: 'BTC Account: ***2235',
  }

  layout() {
    return 'mobile'
  }
}
</script>
<style scoped lang="scss">
.prepaid-page {
  button {
    height: 48px;
  }
  padding-bottom: 70px;
  font-family: 'Reza Zulmi Alfaizi Sans';
  .back-btn {
    width: 10px;
    height: 10px;
    background: transparent;

    border: none;
    box-shadow: none;
    margin: 25px 0;
    img {
      width: 100%;
    }
  }
  .credit-cards {
    margin: 24px 0;
    display: flex;
    gap: 20px;
    overflow-x: auto;
    overflow-y: hidden;
  }
  .border-gradient {
    margin-bottom: 10px;
    background: #121119;
  }
  .border-gradient,
  .border-gradient::before {
    border-radius: 8px;
    position: relative;
  }

  .border-gradient::before {
    content: '';
    position: absolute;
    inset: 0;
    padding: 1px;
    background: linear-gradient(108.71deg, #f64e2a 0%, #232130 30.45%);
    -webkit-mask: linear-gradient(#fff 0 0) content-box,
      linear-gradient(#fff 0 0);
    mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
    -webkit-mask-composite: xor;
    mask-composite: exclude;
    pointer-events: none;
  }

  .rules-card {
    display: flex;
    align-items: start;
    justify-content: space-between;
    padding: 20px 42px;
    position: relative;
    &:hover {
      cursor: pointer;
    }

    div {
      max-width: 80px;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 8px;
      text-align: center;
      font-size: 14px;

      img {
        width: 38px;
        height: 38px;
      }
    }
  }
  .history-card {
    padding: 22px 16px;
    h3 {
      text-transform: uppercase;
      font-weight: 700;
      font-family: 'Hanson';
      font-size: 14px;
      margin-bottom: 10px;
    }
    .wrap-content {
      display: flex;
      flex-direction: column;
      gap: 6px;
      font-size: 14px;
      margin-bottom: 15px;
      .price {
        font-size: 16px;
        font-family: 'Evolventa';
      }
    }
    .bar-chart {
      display: flex;
      width: 100%;
      height: 10px;
      .violet,
      .green {
        min-width: 33%;
        width: 33%;
        height: 100%;
      }
      .violet {
        background: #902af6;
        border-radius: 5px 0 0 5px;
      }
      .green {
        background: #2af653;
      }
      .yellow,
      .orange {
        min-width: 17%;
        width: 17%;
        height: 100%;
      }
      .yellow {
        background: #f6c32a;
      }
      .orange {
        background: #f64e2a;
        border-radius: 0 5px 5px 0;
      }
    }
  }
  .requisites-wrap {
    margin: 14px 0 24px 0;
    .requisites-card {
      padding: 22px 16px;
      .title {
        display: flex;
        align-items: center;
        justify-content: space-between;
        margin-bottom: 24px;
        h3 {
          text-transform: uppercase;
          font-weight: 700;
          font-family: 'Hanson';
        }
        span {
          color: #f64e2a;
          font-size: 14px;
        }
      }
      .card-bg {
        height: 42px;
        border-radius: 6px;
        background: #1e1d26;
        display: flex;
        align-items: center;
        padding: 0 12px;
        font-size: 14px;
        width: 100%;
        color: #ffffff66;
      }
      .cards-info {
        display: grid;
        grid-template-columns: repeat(2, minmax(0, 1fr));
        gap: 12px;
        margin-top: 12px;
      }
    }
  }
  .blur {
    width: 80px;
    height: 40px;
    position: absolute;
    border-radius: 50%;
    top: 20px;
    left: 20px;
    filter: blur(50px);
    background: #eb4b2a;
  }
  .deposit-card {
    padding: 22px 16px;

    h3 {
      font-family: 'Hanson';
      font-weight: 700;
      font-size: 14px;
      margin-bottom: 20px;
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
    .wrap-usd {
      display: flex;
      align-items: start;
      justify-content: space-between;
      gap: 10px;
      max-width: 100%;
      margin-top: 18px;
      button {
        margin-top: 5px;
        box-shadow: none;
        background: transparent;
        height: 30px;
        width: 30px;
        border: none;
        .right {
          transform: rotate(180deg);
        }
      }
      .wrap-forms {
        flex-grow: 1;

        .usdt-form {
          height: 42px;
          width: 100%;
          position: relative;
          input {
            font-size: 16px;
            font-family: 'Evolventa';
            height: 100%;
            width: 100%;
            background: #1d1c24;
            border: none;
            outline: none;
            color: #fff;
            padding-left: 14px;
            padding-right: 50px;
            border-radius: 8px;
          }
          img {
            position: absolute;
            height: 20px;
            top: 50%;
            transform: translateY(-50%);
            right: 14px;
          }
        }
        .equal {
          width: 100%;
          font-family: 'Evolventa';
          font-size: 22px;
          display: flex;
          justify-content: center;
          padding: 10px;
          opacity: 0.6;
        }
        .equal-form {
          width: 100%;
          margin-bottom: 20px;
          span {
            opacity: 0.5;
            font-size: 10px;
          }
          form {
            width: 100%;
            height: 42px;
            padding: 12px;
            display: flex;
            align-items: center;
            background: #1e1d26;
            border-radius: 8px;
            gap: 2px;
            input {
              flex-grow: 1;
              background: transparent;
              border: none;
              outline: none;
              &::placeholder {
                color: rgba(27, 150, 31, 0.3);
              }
            }
            span,
            input {
              color: #1b961f;
              font-size: 16px;
              opacity: 1;
            }
          }
        }
      }
    }
    .btn-deposit {
      background: transparent;
      width: 100%;
      font-size: 16px;
      font-family: 'Hanson';
      text-align: center;
    }
    .wrap-details {
      margin-top: 30px;
      font-weight: 700;
      font-family: 'Hanson';
      h2 {
        font-size: 20px;
      }
      &-card {
        display: flex;
        flex-direction: column;
        gap: 10px;
        font-size: 16px;
        margin-top: 16px;
        margin-bottom: 30px;
        div {
          width: 100%;
          border-radius: 10px;
          background: #1d1d2966;
          display: flex;
          align-items: center;
          justify-content: space-between;
          padding: 0 20px;
          img {
            width: 24px;
          }
        }
      }
      .btn-issue {
        background: #f64e2a;
        text-align: center;

        font-family: 'Hanson';
        font-weight: 700;
      }
    }
  }
  .modal {
    display: none;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    background: #00000099;
    z-index: 100;
    overflow-y: hidden;
    align-items: center;
    justify-content: center;
    padding: 12px;

    &.open {
      display: flex;
    }
    .modal-content {
      padding: 30px 16px;
      background: #1e1d26;

      border-radius: 8px;
      p {
        margin-bottom: 32px;
        font-family: 'Hanson';
        font-size: 14px;
        font-weight: 700;
      }
      .wrap-btns {
        display: flex;
        flex-direction: column;
        gap: 12px;
        button {
          background: #f64e2a;
          color: #fff;
          font-family: 'Hanson';
          font-size: 16px;
          font-weight: 700;
        }
        .cancel {
          background: transparent;
        }
      }
    }
  }
}
</style>
