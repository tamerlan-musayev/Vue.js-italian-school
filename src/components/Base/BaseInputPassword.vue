<template>
  <div class="c-input-wrapper">
    <div class="c-input-password" :class="{ error: error }">
      <BaseIcon name="pass" class="c-input-password__field-icon" />
      <input
        class="c-input-password__field"
        :type="type"
        :placeholder="placeholder"
        v-model="val"
        @input="changeValue"
      />
      <div
        class="c-input-password__field-show-icon"
        @click.stop="toggleShow"
      >
        <img src="@/assets/img/icons/hide-pass.svg" alt="hide" v-if="isShow" />
        <img src="@/assets/img/icons/eye-pass.svg" alt="show" v-else />
      </div>
      <template v-if="showProgress">
        <div class="c-input-password__progress">
          <span :style="{ width: security_password }"></span>
        </div>
      </template>
    </div>
    <template v-if="error_message" class="error-message-wrapper">
      <div class="c-input-password__notifer">
        {{ error_message }}
      </div>
    </template>
  </div>
</template>

<script>
export default {
  name: "BaseInputPassword",
  props: {
    placeholder: {
      type: String
    },
    showProgress: {
      type: Boolean
    },
    error: {
      type: Boolean
    },
    error_message: {
      type: String
    }
  },
  computed: {
    type() {
      return this.isShow ? "text" : "password";
    },
    security_password() {
      return this.val.length <= 10 ? `${this.val.length * 10}%` : `100%`;
    }
  },
  data() {
    return {
      isShow: false,
      val: ""
    };
  },
  methods: {
    toggleShow() {
      this.isShow = !this.isShow;
    },
    changeValue() {
      this.$emit("input", this.val);
    }
  }
};
</script>

<style lang="scss">
.c-input-password {
  position: relative;
  @extend %df;
  @extend %aic;
  border: 1px solid $soft_gray;
  width: 100%;
  height: rem(50);
  padding: 0 0 0 20px;
  transition: all 0.5s ease;
  margin-bottom: 0px !important;
  position: relative;
  .c-input-password__field-show-icon--show {
    height: 20px;
    width: 20px;
  }
  svg {
    width: 20px;
    margin-left: 2px;
  }
  .c-input__field {
    padding-left: 0px;
  }
  .error-message-wrapper {
    display: block;
  }
  &__notifer {
    @extend %text-very-small;
    color: $red;
    margin-top: 10px;
    // text-align: center;
  }
  &__progress {
    position: absolute;
    left: 0;
    bottom: -8px;
    width: 100%;
    height: 4px;
    span {
      @extend %df;
      border-radius: 2px;
      height: 100%;
      background-color: $green;
      transition: all 0.3s ease;
    }
  }
  &.error {
    border-color: $red;
    .c-input-password__field {
      color: $red;
      &-icon {
        color: $red;
      }
    }
  }
  &__field {
    width: 100%;
    @extend %text-middle;
    @extend %input-reset;
    color: $black;
    height: 100%;
    max-width: rem(220);
    padding-left: 10px;
    &::placeholder {
      color: rgba(75, 75, 75, 1);
    }
    &-icon {
      &.icon {
        fill: transparent;
        stroke: currentColor;
      }
      width: rem(34);
      height: rem(20);
    }
  }
}
</style>
