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
            >Зарегестрироваться</NuxtLink
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
const host = "https://68d3-178-46-180-106.ngrok.io/api/"
export default {
  layout: "empty",
  data: () => ({

    select: null,
    token: '',

    user: '',
    loginForm :{
        email : '',
        password : '',
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
      await fetch(host + `login`, {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json'
            },
            body: JSON.stringify(this.loginForm)
          })
          .then(res => res.json())
          .then(body => {
            
            console.log(body);
            this.user = body
          })
          console.log(this.user);
          this.token = this.user.api_token
          localStorage.setItem('api-token', this.token)
          
          

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