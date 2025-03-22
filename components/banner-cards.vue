<template>
  <div class="banner-cards tr-scrollbar">
    <img v-for="(card, i) of cards" :key="i" :src="card" />
  </div>
</template>
<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'

import card1 from '@/assets/svg/card1.svg'
import card2 from '@/assets/svg/card2.svg'
import card3 from '@/assets/svg/card3.svg'
import card4 from '@/assets/svg/card4.svg'

@Component({
  components: {},
})
export default class BannerCards extends Vue {
  cards = [card1, card2, card3, card4]
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
