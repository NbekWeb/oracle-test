<template>
  <div class="btc-card">
    <div class="btc-card-icon">
      <div class="">
        <img src="@/assets/svg/btc.svg" />
      </div>
    </div>
    <div class="btc-card-context">
      <span class="context-title">BTC/USDT</span>
      <span class="context-price">1.000.000$</span>
      <span class="context-date">21.04, 15:21</span>
    </div>
  </div>
</template>

<style scoped lang="scss">
.btc-card {
  display: flex;
  height: 74px;
  min-width: 190px;
  gap: 12px;
  padding: 8px;
  border: 1px solid #18171c;
  border-radius: 12px;
  font-family: 'Reza Zulmi Alfaizi Sans';
  &-icon {
    min-width: 58px;
    height: 58px;
    border-radius: 8px;
    background: #3c3c4833;
    display: flex;
    align-items: center;
    justify-content: center;
    div {
      width: 34px;
      height: 34px;
      display: flex;
      align-items: center;
      justify-content: center;
      background: #fff;
      border-radius: 50%;
      img {
        width: 16px;
      }
    }
  }
  &-context {
    display: flex;
    flex-direction: column;
    gap: 4px;
    font-size: 12px;
    line-height: 14px;

    .context-title {
      font-weight: 700;
      font-family: 'Hanson';
    }
    .context-price {
      font-size: 14px;
    }
    .context-date {
      opacity: 0.6;
    }
  }
}
</style>
