<template>
  <button class="btc-card">
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
  </button>
</template>

<style scoped lang="scss">
.btc-card {
  color: #fff;
  display: flex;
  align-items: center;
  text-align: start;
  height: 74px;
  min-width: 190px;
  gap: 12px;
  font-size: 12px;
  padding: 8px;
  padding: 0;
  box-shadow: none;
  background: transparent;
  outline: none;
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

    .context-title {
      font-weight: 700;
      font-size: 12px;
      font-family: 'Hanson';
    }
    .context-price {
      font-size: 14px;
    }
    .context-date {
      font-size: 12px;
      opacity: 0.6;
    }
  }
}
</style>
