<template>
  <div class="score-page">
    <div class="go-back">
      <img :src="getImagePath('arrow-back')" />

      <h3 class="main-title">Level</h3>
    </div>
    <banner-cards />
    <div class="score-wrap">
      <h3>score: 595</h3>
      <score-cards />
    </div>
    <div class="score-rate">
      <div class="rate-nums">
        <span>450</span>
        <span>650</span>
      </div>
      <div class="slide">
        <span></span>
      </div>
      <span class="current">595</span>
    </div>
    <div class="rewards-wrap">
      <h3>Your Status Rewards</h3>
      <div class="rewards-card">
        <div v-for="i in 3" :key="i">
          <span></span>
          Lorem ipsum dolor sit amet consectetur
        </div>
      </div>
    </div>
    <div class="overview-wrap">
      <h3>Score overview</h3>
      <div class="overview-cards">
        <div v-for="(overview, i) of overviews" :key="i">
          <span
            class="status"
            :class="overview.status == 'warn' ? 'warn' : 'success'"
          >
            {{ overview.title }}
          </span>
          <span>24.05.24, 05:20 PM </span>
        </div>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'

@Component({
  components: {},
})
export default class ScorePage extends Vue {
  getImagePath(icon: string) {
    return require(`@/assets/svg/${icon}.svg`)
  }

  overviews = [
    {
      title: '+10 Succesfull deal',
      status: 'success',
    },
    {
      title: '+5 good review',
      status: 'success',
    },
    {
      title: '-5 Dispute lost',
      status: 'warn',
    },
    {
      title: '+10 succesfull deal',
      status: 'success',
    },
    {
      title: '+5 good review',
      status: 'success',
    },
    {
      title: '-5 Dispute lost',
      status: 'warn',
    },
  ]

  layout() {
    return 'mobile'
  }
}
</script>
<style scoped lang="scss">
.score-page {
  font-family: 'Hanson';
  color: #fff;
  font-size: 14px;
  h3 {
    font-weight: 700;
    text-transform: uppercase;
  }
  .go-back {
    margin: 16px 0;
    display: flex;
    align-items: center;
    gap: 10px;
    img {
      width: auto;
      height: 20px;
    }
    h3 {
      font-size: 16px;
    }
  }
  .score-wrap {
    h3 {
      font-size: 20px;
      text-align: center;
      margin: 36px 0 20px 0;
    }
  }
  .score-rate {
    margin-bottom: 28px;
    font-family: 'Reza Zulmi Alfaizi Sans';

    .rate-nums {
      display: flex;
      justify-content: space-between;

      color: #ffffff66;
      margin-bottom: 8px;
    }
    .slide {
      width: 100%;
      height: 6px;
      display: flex;
      background: #181720;
      border-radius: 6px;
      position: relative;
      span {
        width: 70%;
        position: absolute;
        height: 100%;
        background: #f64e2a;
        border-radius: 6px;
      }
    }
    .current {
      display: flex;
      margin-left: calc(70% - 15px);
      margin-top: 6px;
    }
  }
  .rewards-wrap {
    margin-bottom: 36px;

    h3 {
      font-weight: 700;
      font-size: 20px;
      margin-bottom: 16px;
    }
    .rewards-card {
      font-family: 'Reza Zulmi Alfaizi Sans';
      display: flex;
      flex-direction: column;
      gap: 8px;
      div {
        width: 100%;
        padding: 12px;
        background: #181720;
        border-radius: 8px;
        display: flex;
        align-items: center;
        gap: 8px;
        span {
          width: 8px;
          height: 8px;
          border-radius: 50%;
          display: flex;
          background: #f64e2a;
        }
      }
    }
  }
  .overview-wrap {
    h3 {
      font-size: 20px;
      font-weight: 700;
      margin-bottom: 16px;
    }
    .overview-cards {
      display: flex;
      flex-direction: column;
      gap: 10px;
      div {
        background: #1d1d2966;
        border-radius: 12px;
        padding: 12px;
        display: flex;
        align-items: center;
        justify-content: space-between;
        font-family: 'Reza Zulmi Alfaizi Sans';
      }
      .status {
        font-family: 'Kenyan Coffee';
        font-size: 20px;
        font-weight: 700;
        text-transform: uppercase;
      }
      .success {
        color: #1b961f;
      }
      .warn {
        color: #f64e2a;
      }
    }
  }
}
</style>
