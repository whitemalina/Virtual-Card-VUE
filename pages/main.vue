
<template>

  <v-main class="welcome">


  <v-app id="inspire">
    <div class="text-center">
      <v-dialog
        v-model="dialog"
        hide-overlay
        persistent
        width="300"
      >
        <v-card
          color="primary"
          dark
        >
          <v-card-text>
            Генерируем...
            <v-progress-linear
              indeterminate
              color="white"
              class="mb-0 p-10"
            ></v-progress-linear>
          </v-card-text>
        </v-card>
      </v-dialog>
    </div>
  </v-app>


<v-app id="inspire">
    <div class="text-center">
      <v-dialog
        v-model="dialog2"
        width="500"
        color="red"
      >
        <v-card>
          <v-card-title class="text-h5 lighten-2">
            Создание открытки
          </v-card-title>
          <v-form>

          </v-form>
          <v-card-text>
            <v-select
            v-model="form.category"
            :items="categories"
            item-text="name"
            item-value="value"
            label="Категория"
            persistent-hint
            return-object
            single-line
          ></v-select>
          <v-text-field
            label="Заголовок"
            v-model="form.title"
            placeholder="Поздравляю с Днем рождения!"
            hint="Заголовок открытки"
          ></v-text-field>

          <v-textarea
            name="input-7-1"
            label="Содержимое"
            v-model="form.content"
            placeholder="С днем рождения! Пусть в твоем доме всегда царят покой, уют и гармония. Желаю быть счастливой, радоваться жизни, удивляться.."
            hint="Содержимое открытки"
          ></v-textarea>
          <v-select
            v-model="form.scene"
            :items="items"
            item-text="name"
            item-value="value"
            label="Сцена"
            hint="Сцена в открытке"
          ></v-select>
          </v-card-text>
  
          <v-divider>

          </v-divider>
  
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn
              color="primary"
              text
              @click="dialog2 = false; dialog = true; generate()"
            >
              СОЗДАТЬ
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </div>
  </v-app>

<v-app id="inspire">
    <div class="text-center">
      <v-dialog
        v-model="dialog3"
        width="500"
        color="red"
      >
      <v-card
      :loading="loading"
      class="mx-auto my-12"
      max-width="374"
    >
      <template slot="progress">
        <v-progress-linear
          color="deep-purple"
          height="10"
          indeterminate
        ></v-progress-linear>
      </template>

      <v-img
        height="400"
        src="https://e7.pngegg.com/pngimages/652/807/png-clipart-code-barres-2d-qr-code-business-information-e-commerce-business-text-rectangle-thumbnail.png"
      ></v-img>
  
      <v-card-title>{{card.title}}</v-card-title>
  
      <v-card-text>
  
        <div>{{card.content}}.</div>
      </v-card-text>
  
      <v-divider class="mx-4"></v-divider>
  
      <v-card-text>
        <v-chip-group
          active-class="deep-purple accent-4 white--text"
          column
        >
          <v-chip>{{card.category}}</v-chip>

        </v-chip-group>
      </v-card-text>
  
      <v-card-actions>
        <v-btn
          color="deep-purple lighten-2"
          text :href="'card/' + card.card_url"

        >
          Открыть
        </v-btn>
        <v-btn
          color="deep-purple lighten-2"
          text

        >
          Скопировать ссылку
        </v-btn>
      </v-card-actions>
    </v-card>
      </v-dialog>
    </div>
  </v-app>

    <div class="app">
    <div class="hamburger-menu">
        <div class="logo">
            <span>VirtualCard</span>
        </div>
        <input id="menu__toggle" type="checkbox" />
        <label class="menu__btn" for="menu__toggle">
          <span></span>
        </label>
    
        <ul class="menu__box">
          <li><a class="menu__item" href="#">Главная</a></li>
          <li><a class="menu__item" href="#">Поиск</a></li>
          <li><a class="menu__item" href="#">Маркет</a></li>
          <li><a class="menu__item" href="#">Профиль</a></li>
        </ul>
      </div>
    <div class="nav1">
        <div class="logo">
            <img src="/assets/img/logo.svg" alt="VirtualCard">
        </div>
        <div class="buttons">
            <a class="nav1Button" href="#">Главная</a>
            <a class="nav1Button" href="#">Поиск</a>
            <a class="nav1Button" href="#">Маркет</a>
            <div class="profile">
                <img src="assets/img/profile.svg" alt="Профиль">
                <span>Danil</span>
            </div>
        </div>
    </div>

    <div class="main">
        <div class="container1">
            <h1>Виртуальные <br> открытки</h1>
            <p>
                Здесь вы найдёте уникальные виртуальные открытки <br>
                для друзей и знакомых <br>
                Создавайте собственные вирутальные открытки <br>
                Делитесь ими 
            </p>
            <div class="video2">
                <video autoplay loop muted src="/assets/video/video.mp4"></video>
            </div> 
            <div class="buttons">

                <button onclick="window.location.href='/signin'" class="button">
                    <a href="/signin">
                        <img src="/assets/img/add.svg" alt="Генеировать"> Генерировать
                    </a>
                </button>

                <button class="button searchButton">
                    
                    <a href="">
                        <img src="/assets/img/search.svg" alt="Поиск"> 
                        Поиск
                    </a>
                
                </button>
                <div class="video">
                    <video autoplay loop muted src="/assets/video/video.mp4"></video>
                </div> 
            </div> 
        </div>
           
    </div>    
    </div>

  </v-main>
</template>

<style>
.welcome {
}
.welcome .v-main__wrap {
  display: flex;
  align-items: center;
}
.app{
    display: block;
}


* {
  margin: 0;
  padding: 0;
}

#menu__toggle {
  opacity: 0;
}

#menu__toggle:checked + .menu__btn > span {
  transform: rotate(45deg);
}

#menu__toggle:checked + .menu__btn > span::before {
  top: 0;
  transform: rotate(0deg);
}

#menu__toggle:checked + .menu__btn > span::after {
  top: 0;
  transform: rotate(90deg);
}

#menu__toggle:checked ~ .menu__box {
  left: 0 !important;
}

.menu__btn {
  position: fixed;
  top: 20px;
  left: 20px;
  width: 26px;
  height: 26px;
  cursor: pointer;
  z-index: 1;
}

.menu__btn > span::before {
  content: '';
  top: -8px;
}

.menu__btn > span::after {
  content: '';
  top: 8px;
}

.logo img {
  cursor: pointer;
}

.hamburger-menu {
  backdrop-filter: blur(10px);
  height: 50px;
  position: fixed;
  z-index: 999;
  width: 100%;
}

.hamburger-menu .logo {
  position: absolute;
  right: 20px;
  top: 10px;
  font-family: 'Montserrat';
  font-style: normal;
  font-weight: 500;
  font-size: 19px;
  line-height: 115%;
  /* identical to box height, or 22px */
  letter-spacing: -0.045em;
  color: #FFFFFF;
}

.menu__btn > span,
.menu__btn > span::before,
.menu__btn > span::after {
  display: block;
  position: absolute;
  width: 100%;
  height: 2px;
  background-color: #616161;
  transition-duration: .25s;
}

.menu__box {
  display: block;
  position: fixed;
  top: 0;
  left: -100%;
  width: 300px;
  height: 100vh;
  height-z-index: 99922222;
  margin: 0;
  padding: 80px 0;
  list-style: none;
  list-style-backdrop-filter: blur(5px);
  background-color: #292941;
  box-shadow: 2px 2px 6px #00000066;
  transition-duration: .25s;
}

.menu__item {
  display: block;
  padding: 12px 24px;
  color: #ffffff;
  font-family: 'Roboto', sans-serif;
  font-size: 20px;
  font-weight: 600;
  text-decoration: none;
  transition-duration: 0.25s;
  transition-duration-font-family: 'Montserrat';
  transition-duration-font-style: normal;
  transition-duration-font-weight: 500;
  transition-duration-font-size: 19px;
  transition-duration-line-height: 115%;
  /* identical to box height, or 22px */
  transition-duration-letter-spacing: -0.045em;
  transition-duration-color: #FFFFFF;
}

.menu__item:hover {
  background-color: #1e1e30;
}

.hamburger-menu {
  display: none;
}

@font-face {
  font-family: 'Druk';
  src: url("/assets/fonts/Druc.ttf") format("truetype");
}

h1 {
  overflow: hidden;
  font-family: 'Druk';
  font-style: normal;
  font-weight: 800;
  text-transform: uppercase;
  font-size: 85px;
  line-height: 115%;
  /* or 100px */
  overflow-x: hidden;
  letter-spacing: -0.045em;
  color: #FFFFFF;
}

body {
  overflow-x: hidden;
  background-image: url(/assets/img/main.png);
  background-size: cover;
  background-repeat: no-repeat;
  height: 100%;
}

*::-webkit-scrollbar {
  width: 5px;
}

*::-webkit-scrollbar-track {
  background: #2e1e8a;
}

*::-webkit-scrollbar-thumb {
  background: #af1cdb;
}

.app {
  background-image: url(/assets/img/main.png);
  background-size: cover;
  background-repeat: no-repeat;
  width: 100vw;
  height: 100%;
}

.main .container1 {
  margin-top: 10%;
  padding: 0px 100px 0px 100px;
}

.main .container1 p {
  margin-top: 30px;
  font-family: 'Montserrat';
  font-style: normal;
  font-weight: 700;
  font-size: 21px;
  line-height: 180%;
  /* or 22px */
  color: #FFFFFF;
}

.main .buttons {
  margin-top: 73px;
  display: flex;
}

.main .buttons a {
  display: flex;
  justify-content: center;
  align-items: center;
  text-decoration: none;
  text-align: center;
  font-family: 'Montserrat';
  font-style: normal;
  font-weight: 700;
  font-size: 21px;
  line-height: 115%;
  /* or 24px */
  letter-spacing: -0.045em;
  color: #FFFFFF;
}

.main .buttons button {
  border: none;
  width: 250px;
  height: 64.91px;
  cursor: pointer;
  background: linear-gradient(90deg, #FF005B 0%, #662D8C 100%);
  box-shadow: 0px 10px 30px 4px rgba(208, 0, 255, 0.082), inset 0px 0px 0px 1px rgba(255, 255, 255, 0.24);
  border-radius: 88px;
  transform-style: preserve-3d;
}

.main .buttons button a {
  transform: translateZ(20px);
}

.main .buttons button a img {
  padding-right: 17px;
}

.main .buttons button:hover {
  box-shadow: 0px 10px 30px 4px rgba(207, 0, 255, 0.5), inset 0px 0px 0px 1px rgba(255, 255, 255, 0.24);
}

.main .buttons .searchButton {
  width: 188.03px;
  height: 64.91px;
  margin-left: 40px;
  background: linear-gradient(90deg, #2B0950 0%, #411273 100%);
  box-shadow: 0px 10px 30px 4px rgba(208, 0, 255, 0.192), inset 0px 2px 6px #FF005B;
  border-radius: 88px;
}

.main .buttons .searchButton:hover {
  box-shadow: 0px 10px 30px 4px rgba(207, 0, 255, 0.5), inset 0px 2px 6px #FF005B;
}

.nav1 {
  padding: 37px 100px 0px 100px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.nav1 .buttons {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.nav1 .buttons a {
  padding: 0px 60px;
  font-family: 'Montserrat';
  font-style: normal;
  font-weight: 700;
  font-size: 19px;
  line-height: 115%;
  /* identical to box height, or 22px */
  text-decoration: none;
  letter-spacing: -0.045em;
  color: #FFFFFF;
}

.nav1 .buttons .profile {
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 43px;
  left: 1732px;
  top: 41px;
  background: rgba(255, 255, 255, 0.28);
  backdrop-filter: blur(4px);
  /* Note: backdrop-filter has minimal browser support */
  border-radius: 13px;
}

.nav1 .buttons .profile img {
  padding-left: 14px;
}

.nav1 .buttons .profile span {
  font-family: 'Montserrat';
  font-style: normal;
  font-weight: 700;
  font-size: 19px;
  line-height: 115%;
  /* or 16px */
  letter-spacing: -0.045em;
  color: rgba(255, 255, 255, 0.37);
  padding-left: 17px;
  padding-right: 14px;
}

.video {
  width: 217px;
  height: 345.85px;
  position: relative;
  left: 200px;
  bottom: 150px;
  border: 3px solid #662D8C;
  box-sizing: border-box;
  box-shadow: 0px 10px 30px 4px rgba(207, 0, 255, 0.25);
  border-radius: 28px;
  overflow: hidden;
}

.video video {
  width: 100%;
}

@media screen and (max-width: 1079px) {
  .container1 {
    padding: 0px 10px 0px 10px !important;
  }
  .hamburger-menu {
    top: 0;
    display: block;
  }
  .nav1 {
    display: none;
  }
}

@media screen and (max-width: 952px) {
  .container1 {
    margin-top: 20px;
  }
  .container1 h1 {
    font-size: 66px;
  }
}

@media screen and (max-width: 740px) {
  body {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .container1 {
    margin-top: 20px;
  }
  .container1 h1 {
    font-size: 56px;
  }
}

@media screen and (max-width: 598px) {
  h1 {
    font-size: 30px !important;
  }
  .buttons {
    position: relative;
    flex-direction: column;
  }
  .buttons button {
    margin-top: 10%;
    width: 80vw !important;
  }
  .buttons .searchButton {
    box-shadow: none !important;
    border: 1px solid #ffffff42 !important;
  }
  h1 {
    position: absolute;
    top: 9%;
    text-align: center;
    left: 50%;
    transform: translateX(-50%);
  }
  .main .container1 p {
    font-size: 14px !important;
  }
  .main .container1 p {
    margin-top: 100px !important;
  }
  .buttons {
    display: flex;
    justify-content: space-around;
    align-items: center;
  }
  .searchButton {
    margin-right: 0;
    margin-left: 0 !important;
  }
  .button {
    margin-right: 0 !important;
    width: 150px !important;
  }
  .button a {
    font-size: 14px !important;
  }
  .button a img {
    padding-right: 5px !important;
  }
}

@media screen and (max-width: 350px) {
  h1 {
    position: absolute;
    top: 10%;
    text-align: center;
    left: 50%;
    z-index: 1;
    transform: translateX(-50%);
    font-size: 20px !important;
  }
  .buttons {
    flex-direction: column;
  }
  .buttons button {
    margin-top: 10%;
    width: 80vw;
  }
  .buttons .searchButton {
    box-shadow: none !important;
    border: 1px solid #ffffff42 !important;
  }
  .main .container1 p {
    font-size: 15px !important;
    word-break: break-word;
  }
}

@media screen and (max-width: 950px) {
  body {
    height: 1000px;
  }
  .container1 {
    margin-top: 25% !important;
  }
}

@media screen and (max-width: 917px) {
  .video {
    left: 100px;
  }
}

.video2 {
  display: none;
}

@media screen and (max-width: 917px) {
  body {
    height: 100%;
  }
  .container1 {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }
  .container1 h1 {
    align-self: flex-start;
  }
  .buttons {
    margin-bottom: 100px;
  }
  .video {
    display: none;
  }
  .video2 {
    position: relative;
    display: block;
    margin-top: 100px;
    margin-bottom: 10px;
    bottom: 0px;
    height: 800px !important;
    width: 60vw;
    border: 3px solid #662D8C;
    box-sizing: border-box;
    box-shadow: 0px 10px 30px 4px rgba(207, 0, 255, 0.25);
    border-radius: 28px;
    overflow: hidden;
    height: 60vw;
  }
  .video2 video {
    width: 100%;
  }
}

@media screen and (max-width: 687px) {
  .video2 {
    height: 90vw !important;
  }
}
/*# sourceMappingURL=main.css.map */

</style>


<script src="https://code.jquery.com/jquery-3.6.0.slim.min.js"> </script>
<script>

import { Notyf } from 'notyf';
import 'notyf/notyf.min.css';
const notyf = new Notyf();

const host = "https://68d3-178-46-180-106.ngrok.io/api/"
import 'animate.css';


export default {
  layout: "empty",

  mounted() {
// $('.button').tilt({scale: 1.1, speed: 1000})
// $('.video').tilt({scale: 1.1, speed: 1000, glare: true, maxGlare: 1})
// $('.navButton').tilt({scale: 1.1, speed: 1000})
// $('.profile').tilt({scale: 1.1, speed: 1000})
  },
  head() {
    return {
    script: [

        {
            src: "assets/js/site.js",
        },
    ]
    }
    

  },
  
  data() {
    return {
      dialog: false,
      dialog2: false,
      dialog3: false,
      token: '123',
      form: {
        title: '',
        content: '123',
        scene: 2,
        category: 2,
      },
      card: '',
      items: [
        { name: 'Зима', value: '1'},
        { name: 'Дом', value: '2'},
        { name: 'Улица', value: '3'},
        { name: 'Закат', value: '4'},
      ],
      categories: [
        { name: 'Поздравление', value: '1'},
        { name: 'День рождения', value: '2'},
        { name: 'Доброе утро', value: '3'},
        { name: 'Зима', value: '4'},
      ]
    };
  },
  watch: {
    dialog (val) {
      if (!val) return

      setTimeout(() => (this.dialog = false, this.dialog3 = true), 4000)
      
    },
    
  },
  mounted(){
    if (localStorage.getItem('api-token') !== '') {
      this.token = localStorage.getItem('api-token') 
    }
    this.token = '123'
    //console.log(this.token);
    //notyf.success('123')
  },
  methods : {
    async generate (){
      await fetch(host + `store`, {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json',
                'Authorization': 'Bearer ' + this.token
            },
            body: JSON.stringify({
              'category' : this.form.category.value,
              'scene' : this.form.scene,
              'title' : this.form.title,
              'content' : this.form.content
            })
          })
          .then(res => res.json())
          .then(body => {
            
            console.log(body);
            this.card = body['Created card']
          })
          
          

    },
  }
};

</script>
