<template>
  <div class="banner-cards tr-scrollbar">
    <img v-for="(card, i) of cards" :key="i" :src="getImagePath(card)" />
  </div>
</template>
<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'

@Component({
  components: {},
})
export default class BannerCards extends Vue {
  cards = ['card1', 'card2', 'card3', 'card4']

  getImagePath(icon: String) {
    return require(`@/assets/svg/${icon}.svg`)
  }
}
</script>

<style scoped lang="scss">
.banner-cards {
  display: flex;
  height: 158px;
  width: 100%;
  overflow-x: auto;
  gap: 10px;
  img {
    width: 133px;
  }
}
</style>
