<template>
  <div class="credit-card" :class="type ? 'bg-black-100' : 'bg-orange-liner'">
    <div class="wrap-balance">
      <div class="">
        <span class="">Balance</span>
        <span class="balance-amount">$5,756</span>
      </div>
      <img src="@/assets/svg/chip.svg" />
    </div>
    <div class="wrap-info">
      <div>
        <span class="wrap-info-desc">CARD HOLDER</span>
        <span>User</span>
      </div>
      <div>
        <span class="wrap-info-desc">VALID THRU</span>
        <span>12/31</span>
      </div>
    </div>
    <div class="wrap-nums">3778 **** **** 1234</div>
  </div>
</template>
<script lang="ts">
import { Component, Vue, Prop } from 'nuxt-property-decorator'

@Component({
  components: {},
})
export default class CreditCard extends Vue {
  @Prop({ default: '' }) readonly type!: string
}
</script>

<style scoped lang="scss">
.credit-card {
  display: flex;
  flex-direction: column;
  font-family: 'Evolventa';
  line-height: 100%;
  width: 260px;
  min-width: 260px;
  height: 170px;
  border-radius: 15px;
  .wrap-balance {
    padding: 16px 20px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    div {
      display: flex;
      flex-direction: column;
      gap: 0px;
      span {
        font-family: 'Reza Zulmi Alfaizi Sans';
        font-size: 11px;
      }
      .balance-amount {
        font-size: 16px;
      }
    }
    img {
      height: 29px;
      width: 29px;
    }
  }
  .wrap-info {
    display: flex;
    align-items: center;
    justify-content: space-between;

    padding: 20px 20px 20px 15px;
    div {
      display: flex;
      flex-direction: column;
      gap: 0px;
      span {
        font-size: 13px;
      }
      .wrap-info-desc {
        font-size: 10px;

        opacity: 0.7;
      }
    }
  }
  .wrap-nums {
    flex-grow: 1;
    border-radius: 0 0 15px 15px;
    background: linear-gradient(
      180deg,
      rgba(255, 255, 255, 0.15) 0%,
      rgba(255, 255, 255, 0) 100%
    );
    display: flex;
    align-items: center;
    padding: 0 20px;
  }
}

.bg-orange-liner {
  background: linear-gradient(107.38deg, #f64e2a 2.61%, #d80027 101.2%);
}
.bg-black-100 {
  background: #121119;
}
</style>
