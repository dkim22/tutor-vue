<template>
  <form class="login-form">
    <input class="login-form__id" />
    <div class="login-form__password-wrapper">
      <input
        :type="isShowPassword ? 'text' : 'password'"
        class="login-form__password"
      />
      <button class="login-form__toggle-button" @click.prevent="togglePassword">
        보기
      </button>
    </div>
    <input
      type="button"
      value="로그인"
      class="login-form__submit"
      @click.prevent="handleClick"
    />
  </form>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import { useRouter } from "vue-router";

export default defineComponent({
  name: "HelloWorld",
  setup() {
    const router = useRouter();
    const isShowPassword = ref(false);
    const togglePassword = () => {
      isShowPassword.value = !isShowPassword.value;
    };
    const handleClick = () => {
      router.push({
        name: "About",
      });
    };

    return { isShowPassword, togglePassword, handleClick };
  },
});
</script>

<style lang="scss">
.login-form {
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto;
  gap: 8px;

  @media (max-width: 992px) {
    flex-direction: column;
  }

  &__id,
  &__password,
  &__submit {
    height: 24px;
    border-radius: 3px;
    border: 1px solid black;

    @media (max-width: 992px) {
      height: 40px;
    }
  }

  &__password {
    &-wrapper {
      position: relative;
    }
  }

  &__toggle-button {
    position: absolute;
    top: 50%;
    right: 4px;
    transform: translateY(-50%);
    border: 1px solid black;
    border-radius: 50%;
  }

  &__submit {
    background-color: var(--main-color);
  }
}
</style>
