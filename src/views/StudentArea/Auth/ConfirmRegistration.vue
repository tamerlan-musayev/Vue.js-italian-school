<template>
  <div class="confirm-final-registration">
    <div class="confirm-final-registration__content">
      <figure>
        <img src="~@/assets/email.svg" />
      </figure>
      <div class="confirm-text">
        <h2 class="confirm-final-registration__content-tag">
          Проверьте вашу почту
        </h2>
        <p class="confirm-final-registration__content-text">
          Вам на почту было отправленно письмо с подтверждением регистрации.
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CheckEmailModal"
};
</script>

<style lang="scss">
.confirm-final-registration {
  margin-top: $mt;
  .confirm-text {
    margin-top: 40px;
  }
  &__content {
    @extend %df;
    @extend %jcc;
    @extend %fdc;
    height: 100%;
    max-width: 311px;
    width: 100%;
    margin: 0 auto;
    &-tag {
      @extend %h2-title-regular;
      color: $black;
    }

    &-text {
      @extend %text-small-big-line-height;
      color: $gray;
      margin-top: rem(12);
    }

    &-question {
      @extend %text-middle;
      color: $black;
      margin-top: rem(24);
    }

    &-send {
      @extend %text-middle;
      color: $green;
    }
    @media screen and (max-width: $mobile) {
      max-width: 231px;
      .confirm-text {
        margin-top: 30px;
        h2 {
          font-size: 22px;
          line-height: 100%;
          white-space: nowrap;
        }
        p {
          font-size: 12px;
        }
      }
    }
  }
}
</style>
