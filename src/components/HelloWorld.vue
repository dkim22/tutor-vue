<template>
  <form class="login-form">
    <input class="login-form__id" />
    <input type="password" class="login-form__password" />
    <input type="button" value="로그인" class="login-form__submit" />
  </form>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "HelloWorld",
});
</script>

<style lang="scss">
.login-form {
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto;

  @media (max-width: 992px) {
    flex-direction: column;
  }

  &__id,
  &__password,
  &__submit {
    @media (max-width: 992px) {
      height: 30px;
    }
  }

  &__submit {
    background-color: var(--main-color);
  }
}
</style>
