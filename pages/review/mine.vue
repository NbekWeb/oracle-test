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
      <review-card :review="{ status: 'like', type: 'mine' }" />
      <review-card
        v-for="i in 5"
        :key="i"
        :review="{
          status: i % 2 != 0 ? 'like' : 'dislike',
          type: 'mine',
          answerEmpty: true,
        }"
      />
    </div>
  </div>
</template>
<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'

@Component({
  components: {},
})
export default class mineREviewPage extends Vue {
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
