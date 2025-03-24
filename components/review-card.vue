<template>
  <div class="review-card">
    <div class="main-review">
      <img src="@/assets/png/man.png" class="user-img" />
      <div class="main-review-content">
        <div class="main-review-content-top">
          <div class="wrap-users">
            <span>@username</span>
            <template v-if="review.type">
              <div class="stars-wrap">
                <img
                  v-for="j in 4"
                  :key="j"
                  src="@/assets/svg/start-full.svg"
                />
                <img src="@/assets/svg/star.svg" />
              </div>
            </template>
          </div>
          <div class="like-wraper">
            <span> 20.12.24 </span>
            <img
              v-if="review.status == 'like'"
              src="@/assets/svg/like-green.svg"
            />
            <img v-else src="@/assets/svg/like-red.svg" />
          </div>
        </div>
        <p class="">Lorem ipsum dolor sit amet consectetur ad</p>
      </div>
    </div>
    <div
      v-if="review.type == 'mine' && review.answerEmpty"
      class="write-answer"
      @click="toggleOpen"
    >
      Write an answer
    </div>
    <div v-if="!review.answerEmpty" class="answer-review">
      <div class="">
        <img src="@/assets/png/man.png" class="user-img" />
        <span> @username </span>
        <img
          src="@/assets/svg/forward-white.svg"
          class="forward"
          @click="toggleOpen"
        />
        <div v-if="review.type == 'mine'" class="pen">
          <img src="@/assets/svg/pen.svg" @click="toggleOpen" />
        </div>
      </div>
      <p :class="['limit2', { 'show-full': isExpanded }]">
        Lorem ipsum dolor sit amet consectetur adipiscing elit Ut et massa mi.
        Aliquam in hendrerit urna. Aliquam in hendrerit urna. Aliquam in
        hendrerit urna.
      </p>
      <template v-if="review.type == 'unknown'">
        <span class="view-more" @click="toggleExpand">
          {{ isExpanded ? 'Hide' : 'View more' }}
          <img
            src="@/assets/svg/arrow-right.svg"
            alt=""
            :class="{ rotated: isExpanded }"
          />
        </span>
      </template>
    </div>
    <div class="comment-open" :class="open && 'open'" @click="closeOpen">
      <div class="comment-wrap" @click.stop>
        <div class="comment-content">
          <div class="comment-content-top">
            <div>
              <img src="@/assets/png/man.png" />
              your answer
            </div>
            <img src="@/assets/svg/like-green.svg" />
          </div>
          <p>
            Lorem ipsum dolor sit amet consectetur adipiscing elit Ut et massa
            mi. Aliquam in hendrerit urna.
          </p>
        </div>
        <form>
          <input type="text" placeholder="Type your answer..." />
        </form>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import { Component, Vue, Prop } from 'nuxt-property-decorator'

@Component
export default class ReviewCard extends Vue {
  @Prop({
    type: Object,
    default: () => ({
      status: '',
      type: '',
      answerEmpty: false,
    }),
  })
  readonly review!: { status: string; type: string; answerEmpty: boolean }

  isExpanded = false
  open = false

  toggleOpen() {
    this.open = !this.open
    document.body.style.overflowY = 'hidden'
  }

  closeOpen() {
    this.open = false
    document.body.style.overflowY = ''
  }

  toggleExpand() {
    this.isExpanded = !this.isExpanded
  }
}
</script>
<style scoped lang="scss">
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
        .like-wraper {
          display: flex;
          align-items: center;
          gap: 6px;

          span {
            font-family: 'Reza Zulmi Alfaizi Sans';
            color: #ffffff66;
          }
        }
        .wrap-users {
          display: flex;
          align-items: center;
          gap: 6px;
          .stars-wrap {
            display: flex;
            gap: 0;
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
      .pen {
        display: flex;
        flex-grow: 1;
        justify-content: end;
        img {
          width: 16px;
        }
      }
    }
  }
  .view-more {
    font-size: 10px;
    font-family: 'Hanson';
    text-transform: uppercase;
    display: flex;
    align-items: center;
    gap: 6px;
    color: #f64e2a;
    &:hover {
      cursor: pointer;
    }
    img {
      width: 16px;
      transform: rotate(90deg);
      transition: 0.3s ease;
      &.rotated {
        transform: rotate(270deg);
      }
    }
  }
  .limit2 {
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
    overflow: hidden;
  }

  .show-full {
    -webkit-line-clamp: unset;
  }
  .comment-open {
    position: fixed;
    top: 0;
    left: 0;
    height: 100vh;
    width: 100%;
    background: #0a090fcc;
    z-index: 100;
    display: none;
    &.open {
      display: flex;
    }
    align-items: end;
    .comment-wrap {
      padding: 12px;
      border-radius: 12px 12px 0 0;
      background: #1e1d26;
      display: flex;
      flex-direction: column;
      gap: 20px;
      .comment-content {
        &-top {
          display: flex;
          align-items: center;
          justify-content: space-between;
          img {
            width: 16px;
            height: 16px;
          }
          div {
            font-size: 12px;
            font-family: 'Hanson';
            font-weight: 700;
            text-transform: uppercase;
            display: flex;
            align-items: center;
            gap: 10px;
            img {
              width: 24px;
              height: 24px;
            }
          }
        }
        p {
          margin-top: 6px;
          font-size: 14px;
          font-family: 'Reza Zulmi Alfaizi Sans';
        }
      }
      form {
        width: 100%;
        height: 40px;
        border-radius: 8px;
        background: #272531;
        padding: 0 12px;
        display: flex;
        align-items: center;
        input {
          font-size: 14px;
          color: #fff;
          font-family: 'Reza Zulmi Alfaizi Sans';
          background: transparent;
          width: 100%;
          border: none;
          outline: none;
        }
      }
    }
  }
  .write-answer {
    text-align: end;
    margin-top: -5px;
    font-size: 12px;
    font-family: 'Evolventa';
    font-weight: 700;
    color: #f64e2a;
  }
}
</style>
