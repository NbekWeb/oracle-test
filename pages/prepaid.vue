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

    <div class="withdraw" :class="open == 'withdraw' && 'open'" @click="close">
      <div class="withdraw-content" @click.stop>
        <span class="close-line" @click="close"></span>
        <div class="cancel-btn" @click="close">Cancel</div>
        <div class="withdraw-content-forms">
          <form class="withdraw-content-forms-usdt">
            <div>
              <span>$</span>
              <input v-model="amountUsd" />
            </div>

            <img :src="getImagePath('usdt-round')" />
          </form>
          <img :src="getImagePath('equal')" class="equal-img" />
          <form class="withdraw-content-forms-usdt">
            <div>
              <input v-model="amountBtc" readonly />
            </div>

            <img :src="getImagePath('bit')" />
          </form>
        </div>
        <transfer-accounts />
        <button class="withdraw-btn" @click="toggleOpen('success')">
          WITHDRAW ALL
        </button>
      </div>
    </div>
    <div
      class="withdraw-success"
      :class="open == 'success' && 'open'"
      @click="close"
    >
      <div class="withdraw-success-content" @click.stop>
        <div class="withdraw-success-content-usdt">
          <span> 52.12 $ </span>
          <img :src="getImagePath('line-arrow')" />
          <span>0 $</span>
        </div>
        <div class="withdraw-success-content-btc">0.5 BTC</div>
        <div class="withdraw-success-content-card">
          <span class="btn-number">***2235</span>
          <img :src="getImagePath('withdrow-round')" class="withdraw-round" />
          <div class="">
            <span> 52.12 $ </span>
            <img :src="getImagePath('line-arrow')" />
            <span>0 $</span>
          </div>
        </div>
      </div>
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
  amountUsd = '52.12'
  amountBtc = '0.5 Btc'

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
@import '@/assets/styles/prepaid.scss';
</style>
