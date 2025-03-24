<template>
  <div class="card-account">
    <div class="go-back">
      <img src="@/assets/svg/arrow-back.svg" />
      <div>
        <h3 class="main-title">Reviews</h3>
        <span></span>
        <h3 class="main-title">Excange</h3>
      </div>
    </div>
    <div>
      <review-tab />
      <template v-for="i in 6">
        <review-card
          :key="i"
          :review="{ status: i % 2 != 0 ? 'like' : 'dislike', type: 'unknown' }"
        />
      </template>
    </div>
  </div>
</template>
<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'
import ReviewTab from '~/components/review-tab.vue'

@Component({
  components: { ReviewTab },
})
export default class unknownPage extends Vue {
  getImagePath(icon: string) {
    return require(`@/assets/svg/${icon}.svg`)
  }

  layout() {
    return 'mobile'
  }
}
</script>
<style scoped lang="scss">
.card-account {
  color: #fff;
  font-size: 14px;
  .main-title {
    font-size: 16px;
    font-family: 'Hanson';
    text-transform: uppercase;
    font-weight: 700;
  }

  .go-back {
    display: flex;
    align-items: center;
    gap: 10px;
    margin: 15px 0;

    img {
      width: 8px;
    }
    div {
      display: flex;
      align-items: center;
      gap: 8px;

      h3 {
        flex-grow: 1;
        display: flex;
        justify-content: center;
      }
      span {
        display: flex;
        width: 5px;
        height: 5px;
        border-radius: 50%;
        background: #fff;
      }
    }
  }
}
</style>
