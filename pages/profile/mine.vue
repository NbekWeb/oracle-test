<template>
  <div class="profile-mine">
    <div class="go-back">
      <button class="btn back-btn">
        <img :src="getImagePath('arrow-back')" />
      </button>
      <h3 class="main-title">Your profile</h3>
      <span class="blur"></span>
    </div>
    <div class="wrap-info">
      <img src="@/assets/png/man.png" />
      <h4>Username</h4>
      <span>ID: 90124812</span>
    </div>
    <div class="wrap-banner">
      <banner-cards type="add" />
    </div>
    <button class="btn link-btn" @click="toggleOpen">
      <img src="@/assets/svg/telegram.svg" />
      link your telegram account
      <img src="@/assets/svg/arrow-right.svg" />
    </button>
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
    <div class="networks-wrap">
      <div
        v-for="(network, i) of networks"
        :key="i"
        class="network-card"
        :class="i == networks.length - 1 && 'last'"
      >
        <div>
          <span class="">
            <img :src="getImagePath(network.icon)" />
          </span>
          {{ network.name }}
        </div>
        <img :src="getImagePath('chevron')" />
      </div>
    </div>
    <div class="score-wrap">
      <h5 class="main-title">Sparkle monkey</h5>
      <score-card :score="score" />
    </div>
    <div class="achievments-wrap">
      <h5 class="main-title">Achievments</h5>
      <achievments />
    </div>
    <div class="reviews-wrap">
      <div class="review-title">
        <div class="review-title-left">
          <h5 class="main-title">Reviews</h5>
          <span class="dot"></span>
          <span class="total"> Total 105 </span>
        </div>
        <div class="review-title-right">
          General score:

          <span> 4.8/5 </span>
        </div>
      </div>
      <div class="review-cards">
        <div v-for="(review, i) of reviews" :key="i" class="review-card">
          <div class="">
            <img :src="getImagePath(review.icon)" />
          </div>
          <span>{{ review.title }}</span>
        </div>
      </div>
    </div>
    <button class="btn btn-logout">
      <img :src="getImagePath('logout')" />

      Log out
    </button>
    <div class="modal" :class="open && 'open'" @click="closeModal">
      <div class="modal-content" @click.stop>
        <h3 class="main-title">link telegram</h3>
        <span class="close">
          <img :src="getImagePath('x')" />
        </span>
        <form>
          <span>@</span>
          <input type="text" placeholder="username" />
        </form>
        <button class="btn save-btn">Save</button>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'

@Component({
  components: {},
})
export default class ProfileMine extends Vue {
  data() {
    return {
      open: false,
    }
  }

  toggleOpen() {
    this.$data.open = !this.$data.open
    document.body.style.overflowY = this.$data.open ? 'hidden' : ''
  }

  closeModal(event: Event) {
    if ((event.target as HTMLElement).classList.contains('modal')) {
      this.$data.open = false
      document.body.style.overflowY = ''
    }
  }

  getImagePath(icon: string) {
    return require(`@/assets/svg/${icon}.svg`)
  }

  networks = [
    {
      icon: 'telegram',
      name: 'Telegram',
    },
    {
      icon: 'letter',
      name: 'E-mail',
    },
    {
      icon: 'password',
      name: 'Password',
    },
    {
      icon: 'key',
      name: 'PIN',
    },
  ]

  score = {
    img: 'monkey',
    title: 'Current score: 151',
    contextTop: 'Points Lost: ',
    textRed: '- 15',
    contextBottom: 'Points Gained: ',
    textGreen: '+ 15',
  }

  reviews = [
    {
      icon: 'swap',
      title: 'Excange',
    },
    {
      icon: 'p2p',
      title: 'P2P',
    },
    {
      icon: 'basket',
      title: 'Shops',
    },
  ]

  layout() {
    return 'mobile'
  }
}
</script>

<style scoped lang="scss">
.profile-mine {
  color: #fff;
  font-size: 16px;
  .main-title {
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
  .wrap-banner {
    margin: 20px 0;
  }
  .link-btn {
    height: 44px;
    background: transparent;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    font-family: 'Hanson';
    font-size: 12px;
    font-weight: 700;
    width: 100%;
    color: #fff;
    text-transform: uppercase;
    img {
      height: 16px;
      width: auto;
    }
  }
  .btn-oracle {
    margin: 20px 0;
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
  .networks-wrap {
    padding: 0 12px;
    border-radius: 12px;
    background: #1d1d2966;
    font-size: 16px;
    font-family: 'Reza Zulmi Alfaizi Sans';
    .network-card {
      padding: 12px 0;
      border-bottom: 1px solid #ffffff0d;
      display: flex;
      align-items: center;
      justify-content: space-between;
      img {
        width: 18px;
        height: auto;
      }
      div {
        display: flex;
        gap: 12px;
        align-items: center;
        span {
          width: 32px;
          height: 32px;
          display: flex;
          align-items: center;
          justify-content: center;
          border-radius: 50%;
          border: 1px solid #f64e2a;
          box-shadow: 0px 0px 10px 2px rgba(246, 78, 42, 0.25);

          img {
            width: 16px;
            height: 16px;
          }
        }
      }
    }
    .last {
      border-bottom: none;
    }
  }
  .score-wrap,
  .achievments-wrap {
    margin: 36px 0;
    h5 {
      margin-bottom: 16px;
      font-size: 20px;
    }
  }
  .reviews-wrap {
    margin-bottom: 28px;
    .review-title {
      margin-bottom: 20px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      &-left {
        display: flex;
        align-items: center;
        gap: 8px;
        h5 {
          font-size: 16px;
        }
        .dot {
          height: 3px;
          width: 3px;
          border-radius: 50%;
          background: #fff;
        }
        .total {
          font-size: 14px;
          color: #ffffff80;
          font-family: 'Reza Zulmi Alfaizi Sans';
        }
      }
      &-right {
        font-size: 14px;
        font-family: 'Reza Zulmi Alfaizi Sans';
        color: #ffffff80;
        span {
          color: #fff;
        }
      }
    }
    .review-cards {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 12px;
      .review-card {
        display: flex;
        flex-direction: column;
        gap: 6px;
        align-items: center;
        div {
          display: flex;
          align-items: center;
          justify-content: center;
          width: 100%;
          height: 60px;
          border-radius: 10px;
          background: #1d1d29;
          img {
            height: 46px;
            width: auto;
          }
        }
        span {
          font-size: 14px;
          font-family: 'Kenyan Coffee';
        }
      }
    }
  }
  .btn-logout {
    margin-bottom: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 10px;
    font-size: 20px;
    font-family: 'Kenyan Coffee';
    height: 48px;
    background: transparent;
    color: #fff;
    img {
      width: 20px;
      height: auto;
    }
  }
}
.modal {
  position: fixed;
  z-index: 10;
  top: 0;
  left: 0;
  background: #00000099;
  width: 100%;
  height: 100%;
  padding: 0 16px;
  display: none;
  &.open {
    display: flex;
  }
  align-items: center;
  &-content {
    display: flex;
    flex-direction: column;
    gap: 20px;
    width: 100%;
    padding: 16px;
    border-radius: 12px;
    background: #19191f;
    position: relative;
    h3 {
      text-align: center;
      font-size: 16px;
    }
    .close {
      position: absolute;
      top: 10px;
      right: 10px;
      width: 30px;
      height: 30px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      background: #33333e;
      img {
        width: 20px;
        height: auto;
      }
    }
    form {
      background: #272531;
      border-radius: 8px;
      width: 100%;
      font-size: 16px;
      font-family: 'Reza Zulmi Alfaizi Sans';
      padding: 15px 12px;
      display: flex;
      align-items: center;
      gap: 4px;
      input {
        border: none;
        outline: none;
        overflow: hidden;
        flex-grow: 1;
        font-size: 16px;
        font-family: 'Reza Zulmi Alfaizi Sans';
        background: transparent;
        color: #fff;
      }
    }
    .save-btn {
      height: 44px;
      width: 100%;
      background: #f64e2a;
      color: #fff;
      text-transform: uppercase;
      font-size: 14px;
      font-family: 'Hanson';
      font-weight: 700;
    }
  }
}
</style>
