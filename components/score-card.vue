<template>
  <div class="score-card">
    <img :src="getImagePng(score.img)" alt="Score Image" />
    <div class="score-context">
      <span class="score-title">{{ score.title }}</span>
      <div>
        <span>
          {{ score.contextTop }}
          <span class="text-red">{{ score.textRed }}</span>
        </span>
        <span>
          {{ score.contextBottom }}
          <span class="text-green">{{ score.textGreen }}</span>
        </span>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'nuxt-property-decorator'

@Component({
  components: {},
})
export default class ScoreCard extends Vue {
  @Prop({
    type: Object,
    default: () => ({
      img: '',
      title: 'Default Title',
      contextTop: '',
      textRed: '',
      contextBottom: '',
      textGreen: '',
    }),
  })
  readonly score!: {
    img: string
    title: string
    contextTop: string
    textRed: string
    contextBottom: string
    textGreen: string
  }

  getImagePng(img: string) {
    return require(`@/assets/png/${img}.png`)
  }
}
</script>

<style scoped lang="scss">
.score-card {
      width: 100%;
      height: 100px;
      padding: 12px;
      display: flex;
      gap: 16px;
      align-items: center;
      background: #1d1d2966;
      border-radius: 12px;
      img {
        width: 76px;
        height: auto;
      }
      .score-context {
        display: flex;
        flex-direction: column;
        gap: 8px;
        .score-title {
          font-weight: 700;
          font-family: 'Hanson';
          font-size: 15px;
        }
        div {
          display: flex;
          flex-direction: column;
          span {
            font-family: 'Reza Zulmi Alfaizi Sans';
            font-size: 14px;
            line-height: 160%;
          }
        }
      }
    }
    .text-red {
  color: #ff5b5b;
}
.text-green {
  color: #7eff61;
}

</style>
