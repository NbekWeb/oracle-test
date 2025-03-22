<template>
  <div class="profile-block">
    <div class="go-back">
      <button class="btn back-btn">
        <img :src="getImagePath('arrow-back')" />
      </button>
      <h3 class="main-title">about user</h3>
      <span class="blur"></span>
    </div>
    <div class="wrap-info">
      <img src="@/assets/png/mouse.png" />
      <h4>Username</h4>
      <span>ID: 90124812</span>
    </div>
    <a href="https://t.me/tgname" target="_blank" class="btn-tg">
      <img :src="getImagePath('telegram')" />
      @tgname</a
    >
    <div class="block-img">
      <img src="@/assets/png/block.png" />
    </div>
    <h4 class="block-title">
      This user has been blocked due to fraud on the platform.
    </h4>
    <p>Beware of any contact with him</p>
  </div>
</template>
<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'

@Component({
  components: {},
})
export default class ProfileBlock extends Vue {
  getImagePath(icon: string) {
    return require(`@/assets/svg/${icon}.svg`)
  }

  layout() {
    return 'mobile'
  }
}
</script>
<style scoped lang="scss">
.profile-block {
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
  .btn-tg {
    width: 100%;
    height: 44px;
    border-radius: 8px;
    background: #121119;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    font-family: 'Hanson';
    font-weight: 700;
    font-size: 12px;
    margin-bottom: 25px;

    img {
      height: 16px;
      width: auto;
    }
  }
  .block-img {
    display: flex;
    justify-content: center;
    img {
      height: 240px;
      width: auto;
    }
    margin-bottom: 32px;
  }
  .block-title {
    font-family: 'Kenyan Coffee';
    font-size: 28px;
    line-height: 140%;
    text-align: center;
    margin: 0 12px 12px;
  }
  p {
    font-family: 'Reza Zulmi Alfaizi Sans';
    line-height: 140%;
    margin-bottom: 50px;
    text-align: center;
  }
}
</style>
