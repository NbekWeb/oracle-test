<template>
  <div class="banner-cards tr-scrollbar">
    <div v-if="type" class="adding">
      <span></span>
      <img src="@/assets/svg/add.svg" />
    </div>
    <button v-for="(card, i) of cards" :key="i" class="card-img">
      <img :src="getImagePath(card)" />
    </button>
  </div>
</template>
<script lang="ts">
import { Component, Vue, Prop } from 'nuxt-property-decorator'

@Component({
  components: {},
})
export default class BannerCards extends Vue {
  cards = ['card1', 'card2', 'card3', 'card4']

  getImagePath(icon: String) {
    return require(`@/assets/svg/${icon}.svg`)
  }

  @Prop({ default: '' }) readonly type!: string
}
</script>

<style scoped lang="scss">
.banner-cards {
  display: flex;
  height: auto;
  min-height: 150px;
  width: 100%;
  overflow-x: auto;
  overflow-y: hidden;
  gap: 10px;
  .card-img {
    width: 125px;
    min-width: 125px;
    height: 100%;
    border: none;
    background: transparent;
    padding: 0;
    box-shadow: none;
    img {
      width: 100%;
    }
  }
  .adding {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 125px;
    min-width: 125px;
    height: 150px;
    min-height: 150px;
    border: 1px solid transparent;
    background: linear-gradient(#121119, #121119) padding-box,
      linear-gradient(144.97deg, #f64e2a 0%, #232130 42.16%) border-box;
    height: 100%;
    border-radius: 10px;
    position: relative;

    span {
      width: 30px;
      height: 30px;
      border-radius: 50%;
      background: #eb4b2a;
      filter: blur(30px);
      display: flex;
      position: absolute;
      top: 10px;
      left: 30px;
    }
    img {
      width: 36px;
      height: 36px;
    }
  }
}
</style>
