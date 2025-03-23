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
      <div v-for="i in 2" :key="i" class="review-card">
        <div class="main-review">
          <img src="@/assets/png/man.png" class="user-img" />
          <div class="main-review-content">
            <div class="main-review-content-top">
              <span>@username</span>
              <div>
                <span> 20.12.24 </span>
                <img v-if="i % 2 == 1" src="@/assets/svg/like-green.svg" />
                <img v-else src="@/assets/svg/like-red.svg" />
              </div>
            </div>
            <p>Lorem ipsum dolor sit amet consectetur ad</p>
          </div>
        </div>
        <div class="answer-review">
          <div class="">
            <img src="@/assets/png/man.png" class="user-img" />
            <span> @username </span>
            <img src="@/assets/svg/forward-white.svg" class="forward" />
          </div>
          <p>
            Lorem ipsum dolor sit amet consectetur adipiscing elit Ut et massa
            mi. Aliquam in hendrerit urna.
          </p>
        </div>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent, ref } from 'vue'

export default defineComponent({
  setup() {
    const tabs = ref([
      { label: 'Excange' },
      { label: 'P2P' },
      { label: 'SHOPS' },
    ])

    const activeTab = ref(0)

    return { tabs, activeTab }
  },
})
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
    .review-card {
      display: flex;
      flex-direction: column;
      gap: 12px;
      border-bottom: 1px solid #15131f;
      padding: 12px 0;
      p {
        font-family: 'Reza Zulmi Alfaizi Sans';
        font-size: 14px;
      }
      .main-review {
        display: flex;
        gap: 10px;
        .user-img {
          width: 50px;
          height: 50px;
        }
        &-content {
          display: flex;
          flex-direction: column;
          gap: 10px;
          &-top {
            display: flex;
            align-items: center;
            justify-content: space-between;
            font-size: 12px;
            text-transform: uppercase;
            div {
              display: flex;
              align-items: center;
              gap: 6px;

              span {
                font-family: 'Reza Zulmi Alfaizi Sans';
                color: #ffffff66;
              }
            }
          }
        }
      }
      .answer-review {
        display: flex;
        flex-direction: column;
        gap: 6px;
        div {
          display: flex;
          align-items: center;
          gap: 6px;
          font-size: 12px;
          text-transform: uppercase;
          font-weight: 700;
          .user-img {
            width: 24px;
            height: 24px;
            margin-right: 10px;
          }
          .forward {
            width: 15px;
            height: auto;
          }
        }
      }
    }
  }
}
</style>
