<template>
  <div class="c-notifications-alert">
    <ul>
      <li class="c-notification-alert__list">
        <div class="c-notification-alert__holder">
          <img :src="require(`@/assets/toasted/${typeRequest}.svg`)" alt="" />
          <span>{{ text }}</span>
        </div>
        <div class="c-notification-alert__holder">
          <button class="c-notification-alert__close">
            <svg
              width="22"
              height="22"
              viewBox="0 0 22 22"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <circle
                cx="11"
                cy="11"
                r="10.5"
                fill="#FBFBFB"
                stroke="#D8D8D8"
              />
              <path
                d="M7.85715 7.85693L14.1429 14.1426"
                stroke="#4B4B4B"
                stroke-linecap="round"
              />
              <path
                d="M14.1429 7.85693L7.85714 14.1426"
                stroke="#4B4B4B"
                stroke-linecap="round"
              />
            </svg>
          </button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Notifications",
  data() {
    return {
      img: "alert-great"
    };
  },
  props: {
    text: {
      type: String,
      required: true
    },
    typeRequest: {
      type: String,
      required: true
    }
  }
};
</script>

<style lang="scss">
.notification-enter-active,
.notification-leave-active {
  transition: transform 0.5s ease;
  transform: translateY(0);
}
.notification-enter,
.notification-leave-to {
  transform: translateY(100%);
}
.emppty-layout-notifer {
  .c-notification-alert {
    &__list {
      width: 100vw;
    }
  }
}
.c-notification-alert {
  position: relative;
  &__list {
    position: fixed;
    bottom: 0;
    border-top: 1px solid $gray;
    background-color: $white;
    z-index: 999999;
    @extend %df;
    @extend %jcsb;
    @extend %aic;
    width: calc(100vw - 393px);
    padding: 20px 40px;
  }

  &__holder {
    @extend %df;
    @extend %jcsb;
    @extend %aic;
    @extend %text-middle;
    color: $gray;
    margin-right: 80px;
    padding: absolute;
  }

  &__holder img {
    margin-right: 21px;
  }

  &__close {
    background-color: $dark_white;
    border-radius: 50%;
    width: 22px;
    height: 22px;
  }
}
@include bp(1310px) {
  .c-notification-alert {
    &__list {
      width: 100%;
    }
  }
}
</style>
