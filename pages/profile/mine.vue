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
      <h4>U1sername</h4>
      <span>ID: 90124812</span>
    </div>

    <!-- <banner-cards /> -->
  </div>
</template>
<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'

@Component({
  components: {},
})
export default class ProfileMine extends Vue {
  getImagePath(icon: string) {
    return require(`@/assets/svg/${icon}.svg`)
  }

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

}
</style>
