<template>
  <div class="review">
    <div class="tab-wrap">
      <div
        v-for="(tab, index) in tabs"
        :key="index"
        @click="activeTab = index"
        :class="['tab-item', { 'active-tab': activeTab === index }]"
      >
        {{ tab.label }}
      </div>
    </div>

    <div class="tab-content">
      <div class="like-wrap">
        <div>
          <img src="@/assets/svg/like.svg" />
        </div>

        <div>
          <img src="@/assets/svg/like.svg" class="dislike" />
        </div>
        <div class="all">All</div>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'

@Component({
  components: {},
})
export default class reviewTab extends Vue {
  tabs = [{ label: 'Excange' }, { label: 'P2P' }, { label: 'SHOPS' }]

  activeTab = 0
}
</script>
<style scoped lang="scss">
.review {
  font-family: 'Hanson';
  font-size: 14px;
  .tab-wrap {
    display: flex;
    justify-content: space-between;
    margin-bottom: 20px;
    border-bottom: 2px solid #121119;
    .tab-item {
      flex: 1;
      text-align: center;
      padding: 10px 0;

      text-transform: uppercase;

      font-weight: 700;
      cursor: pointer;
      position: relative;
      transition: all 0.3s ease;
    }

    .active-tab::after {
      content: '';
      position: absolute;
      bottom: -2px;
      left: 0;
      width: 100%;
      height: 2px;
      background-color: #f64e2a;
    }
  }

  .tab-content {
    .like-wrap {
      width: 100%;
      height: 48px;
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      border-radius: 12px;
      background: #121119;
      padding: 4px;
      div {
        display: flex;
        align-items: center;
        justify-content: center;
        &:hover {
          cursor: pointer;
        }
        &.all {
          border-radius: 8px;
          background: #f64e2a;
          height: 100%;
          width: 100%;

          font-size: 12px;
          font-weight: 700;
          text-transform: uppercase;
        }
        img {
          width: 20px;
          height: auto;
        }
        .dislike {
          transform: rotate(-180deg);
        }
      }
    }
  }
}
</style>
