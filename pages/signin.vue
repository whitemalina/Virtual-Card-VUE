<template>
  <div>
    <div class="signin ">
      <div class="signin-content animate__animated animate__fadeIn">
        <h2 class="sign-title">Вход</h2>

        <div class="sign-inputs">
          <form action="#">
          <div class="sign-input">
            <img src="../assets/image/mail.svg" alt="" />
            <input type="email" required v-model="loginForm.email" placeholder="E-mail" />
          </div>
          <div class="sign-input">
            <img src="../assets/image/lock.svg" alt="" />
            <input
              type="password" required v-model="loginForm.password"
              placeholder="Пароль"
            />
          </div>
          
          <div class="sign-buttons">
          <button 
        color="success"
        @click.prevent="validate"  class="sign-button btn">Войти</button>
          <NuxtLink to="/signup" class="sign-button_signup"
            >Зарегистрироваться</NuxtLink
          >
        </div>
          </form>
          
          
        </div>
        
        
      </div>
    </div>
  </div>
</template>

<script>
import 'animate.css';

import { Notyf } from 'notyf';
import 'notyf/notyf.min.css';
const notyf = new Notyf({
  position: {
    x: 'center',
    y: 'top',
  },
});

const HOST = "http://127.0.0.1:8000/api/"

export default {
  layout: "empty",
  data: () => ({

    select: null,
    token: '',

    user: '',
    loginForm :{
        email : 'test23@gmail.com',
        password : 'test',
    }
    

  }),

  methods: {
    validate () {
      // this.$refs.form.validate()
      // if (this.valid) {
         
         
           this.auth() 

      // }
    },
    async auth (){
      let email = this.loginForm.email;
      let password = this.loginForm.password;

      let data = {
        email: email,
        password: password,
      };
      let user = null;
      let result;
      // Валидация?
      function validate(email, password) {
        let re = /^[\w-\.]+@[\w-]+\.[a-z]{2,4}$/i;
        if (email.length >= 1 && password.length >= 1) {
          if (!re.test(email)) {
            notyf.error("Неправильная почта");
            return false;
          } else {
            return true;
          }
        } else {
          notyf.error("Заполните все поля");
          console.log(email, password);
          return false;
        }
      }

      // если валидация успешна, продолжаем
      if (validate(email, password)) {
        // авторизация
        try{
          await fetch(HOST + "login", {
            method: "POST",
            body: JSON.stringify(data),
            headers: {
              "Content-Type": "application/json",
            },
          })
            .then((res) => {
              if (res.status == 200) {
                result = 1;
              } else {
                result = 2;
              }
              return res.json();
            })
            .then((data) => {
              console.log(data);
              if (result == 1) {
                this.user = data;
                // this.saveLocalData();

              } else {

              }
              if (result == 1) {
                notyf.success("Вы успешно вошли");
                // this.login.email = this.regist.email;
                // this.login.password = this.regist.password;
                // this.setPage("succes");
                localStorage.setItem("user", JSON.stringify(this.user.data));
                console.log(JSON.parse(localStorage.getItem("user")));
                this.$router.push({
                    path: '/'
                })
              } else {
                notyf.error("Ошибка: " + data.message);
              }
            });
        } catch (e) {
          notyf.error(String(e));
        }
        

      }

      //clear
      // this.login.email = '';
      // this.login.password ='';

    },
    reset () {
      this.$refs.form.reset()
    },
    resetValidation () {
      this.$refs.form.resetValidation()
    },
  },
};
</script>

<style lang="scss">
.signin {
  background: url("./assets/image/signin-back.png") no-repeat;
  background-size: cover;
  height: 100vh;
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  &-content {
    padding: 40px 100px;
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
    input{
        padding-left: 12px;
        &:focus{
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
    font-size: 35px !important;
    text-align: center;
    line-height: 53px;
    margin-bottom: 20px !important;
  }
  &-inputs {
    margin-bottom: 50px !important;
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
  &-buttons{
    margin-top: 50px;
  }
}
</style>