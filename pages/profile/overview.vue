<template>
  <div class="profile-overview">
    <div class="go-back">
      <button class="btn back-btn">
        <img src="@/assets/svg/arrow-back.svg" />
      </button>
      <h3 class="main-title">Profile Overview</h3>
      <span class="blur"></span>
    </div>
    <div class="wrap-info">
      <img src="@/assets/png/man.png" />
      <h4>Username</h4>
      <span>ID: 90124812</span>
    </div>
    <banner-cards />
    <a href="https://t.me/tgname" target="_blank" class="btn-tg">
      <img :src="getImagePath('telegram')" />
      @tgname</a
    >
    <div class="btn-oracle">
      <div class="context">
        <span class="oracle">ORACLE</span>
        <span> Verified </span>
      </div>
      <div class="arrow-back">
        <img :src="getImagePath('arrow-black')" />
      </div>
      <img src="@/assets/png/step-bg.png" class="step-bg" />
    </div>
    <div class="btn-msg">
      <img :src="getImagePath('msg')" />
      Open chat
    </div>
    <div class="offers-wrap">
      <button class="btn">Offer Escrow Deal</button>
      <button class="btn">Quick Transfer</button>
    </div>
    <div class="wrap-score">
      <h5 class="main-title">Sparkle monkey</h5>
      <score-card :score="score" />
    </div>
    <div class="achievment-wrap">
      <h5 class="main-title">Achievments</h5>
      <achievments />
    </div>
    <div class="review-wrap">
      <div class="review-top">
        <h5 class="main-title">Reviews</h5>
        <div class="wrap-like">
          <div class="text-green">
            90%
            <img :src="getImagePath('like-green')" />
          </div>
          <span></span>
          <div class="text-red">
            10% <img :src="getImagePath('like-red')" />
          </div>
        </div>
      </div>
      <div>
        <review-tab />
        <template v-for="i in 2">
          <review-card
            :key="i"
            :review="{
              status: i % 2 != 0 ? 'like' : 'dislike',
            }"
          />
        </template>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'

@Component({
  components: {},
})
export default class ProfileOverview extends Vue {
  getImagePath(icon: string) {
    return require(`@/assets/svg/${icon}.svg`)
  }

  score = {
    img: 'monkey',
    title: 'Current score: 151',
    contextTop: 'Points Lost: ',
    textRed: '- 15',
    contextBottom: 'Points Gained: ',
    textGreen: '+ 15',
    to: '/',
  }

  layout() {
    return 'mobile'
  }
}
</script>
<style scoped lang="scss">
.profile-overview {
  color: #fff;
  font-size: 16px;
  font-family: 'Hanson';
  .main-title {
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
    .blur {
      width: 100px;
      height: 50px;
      position: absolute;
      display: flex;
      top: 0;
      left: 50%;
      transform: translateX(-50%);
      filter: blur(90px);
      background: #f64e2a;
    }
  }
  .wrap-info {
    margin: 24px 0;
    display: flex;
    gap: 4px;
    flex-direction: column;
    align-items: center;
    img {
      width: 80px;
      height: auto;
    }
    h4 {
      font-size: 24px;
      font-family: 'Kenyan Coffee';
      line-height: 140%;
      margin-top: 4px;
    }
    span {
      opacity: 0.4;
      font-family: 'Reza Zulmi Alfaizi Sans';
    }
  }
  .btn-tg {
    width: 100%;
    height: 44px;
    border-radius: 8px;
    background: #121119;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;

    font-weight: 700;
    font-size: 12px;
    margin-bottom: 12px;
    margin-top: 24px;
    img {
      height: 16px;
      width: auto;
    }
  }
  .btn-oracle {
    margin-bottom: 20px;
    width: 100%;
    height: 60px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 15px;
    position: relative;
    z-index: 1;
    background: #e95548;
    border-radius: 12px;
    .context {
      display: flex;
      align-items: center;
      gap: 8px;
      text-transform: uppercase;
      font-size: 14px;
      font-family: 'Hanson';
      font-weight: 700;
      .oracle {
        border-radius: 6px;
        padding: 10px;
        background: #fff;
        color: #e95548;
      }
    }

    .arrow-back {
      width: 28px;
      height: 28px;
      border-radius: 50%;
      background: #fff;
      display: flex;
      align-items: center;
      justify-content: center;
      img {
        width: 18px;
        height: auto;
      }
    }

    .step-bg {
      position: absolute;
      z-index: -1;
      right: 0;
      top: 0;
      height: 100%;
      border-radius: 12px;
    }
  }
  .btn-msg {
    margin-bottom: 20px;
    width: 100%;
    height: 44px;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    background: #f64e2a;
    font-weight: 700;
    font-size: 14px;
    border-radius: 12px;
    img {
      width: 22px;
      height: auto;
    }
  }
  .offers-wrap {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 12px;
    .btn {
      height: 44px;
      background: transparent;
      color: #fff;
      font-family: 'Kenyan Coffee';
      font-size: 18px;
    }
  }
  .wrap-score,
  .achievment-wrap {
    margin-top: 36px;
    h5 {
      font-size: 20px;
      margin-bottom: 16px;
    }
  }
  .review-wrap {
    .review-top {
      margin-top: 36px;
      margin-bottom: 20px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      h5 {
        font-size: 20px;
      }
      .wrap-like {
        display: flex;
        gap: 10px;
        align-items: center;
        font-weight: 700;
        div {
          display: flex;
          align-items: center;
          gap: 5px;
          img {
            width: 16px;
            height: auto;
          }
        }
        span {
          display: flex;
          height: 5px;
          width: 5px;
          background: #434251;
          border-radius: 50%;
        }
      }
    }
  }
}
.text-red {
  color: #f64e2a;
}
.text-green {
  color: #1b961f;
}
</style>
