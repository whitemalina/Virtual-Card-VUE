<template>
  <div>
    <div class="signup">
      <div class="signup-content">
        <h2 class="sign-title">Регистрация</h2>
        <div class="sign-inputs">
          <div class="sign-input">
            <img src="../assets/image/acount.svg" alt="" />
            <input type="text" placeholder="Имя пользователя" />
          </div>
          <div class="sign-input">
            <img src="../assets/image/mail.svg" alt="" />
            <input type="text" placeholder="E-mail" />
          </div>
          <div class="sign-input">
            <img src="../assets/image/lock.svg" alt="" /><input
              type="password"
              placeholder="Пароль"
            />
          </div>
        </div>
        <div class="sign-buttons">
          <button class="sign-button btn">Войти</button>
          <NuxtLink to="/signup" class="sign-button_signup"
            >Зарегестрироваться</NuxtLink
          >
        </div>
      </div>
    </div>
  </div>
</template>


<style lang="scss">
.signup {
  background: url("./assets/image/signup-back.png") no-repeat;
  background-size: cover;
  height: 100vh;
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  .sign-input {
    &s {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
    }
    width: 80%;
    &:not(.sign-input:last-child) {
      margin-bottom: 40px;
    }
  }
  &-content {
    padding: 64px 120px;
    width: max-content;
    background-color: white;
    border-radius: 50px;
    margin: 0 auto;
    position: absolute;
    top: 50%;
    left: 0;
    right: 0;
    transform: translateY(-50%);
  }
  .sign-input {
    border-bottom: 1px solid #f6851b;
    display: flex;
    align-items: center;
    padding: 10px 0;
    input {
      padding-left: 12px;
      &:focus {
        border: none;
        outline: none;
      }
    }

    &:nth-child(1) {
      margin-bottom: 42px;
    }
  }
}
.sign {
  &-title {
    font-size: 64px;
    text-align: center;
    line-height: 75px;
    margin-bottom: 91px;
  }
  &-inputs {
    margin-bottom: 88px;
  }
  &-button {
    margin-bottom: 17px;
    &_signup {
      color: #333333;
    }
    &s {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
    }
    padding: 16px 80px;
  }
}
</style>


<script>
export default {
  layout: "empty",
  data() {
    return {};
  },
};
</script>