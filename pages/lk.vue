<template>
<v-main class="welcome2">
  <v-app id="inspire2">
    <div class="text-center">
        <v-dialog dark v-model="dialog2" width="500" color="red">
          <v-card>
            <v-card-title class="text-h5 lighten-2">
              Создание открытки
            </v-card-title>
            <v-form> </v-form>
            <v-card-text>
              <v-text-field
                label="Название"
                v-model="form.name"
                placeholder="Открытка максиму"
                hint="Название открытки"
              ></v-text-field>
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

            <v-divider> </v-divider>

            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn color="primary" text @click.prevent="generate"> СОЗДАТЬ </v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
    </div>
  </v-app>
  <v-app id="inspire">
    <v-row justify="center">
      <v-dialog
        v-model="dialog4"
        fullscreen
        dark
        hide-overlay
        transition="dialog-bottom-transition"
      >
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            color="dark"
            dark
            v-bind="attrs"
            v-on="on"
          >
            Open Dialog
          </v-btn>
        </template>
        <v-card>
          <v-toolbar
            dark
            color="dark"
          >
            <v-btn
              icon
              dark
              @click="dialog4 = false"
            >
              <v-icon>mdi-close</v-icon>
            </v-btn>
            <v-toolbar-title>Профиль</v-toolbar-title>
            <v-spacer></v-spacer>
            <v-toolbar-items>
              <v-btn
                error
                text
                @click="dialog4 = false; changeProfile()"
              >
                Сохранить
              </v-btn>
            </v-toolbar-items>
          </v-toolbar>
          <v-list
            three-line
            subheader
          >
            <v-subheader>Редактирование профиля</v-subheader>
            <v-list-item>
              <v-list-item-content>
                <v-list-item-title>Имя пользователя</v-list-item-title>
                <v-text-field
                    label="Имя"
                    v-model="user.name"
                    :placeholder="user.name"
                    hint="Отображается в профиле"
                  ></v-text-field>

              </v-list-item-content>
            </v-list-item>
            <v-list-item>
              <v-list-item-content>
                <v-list-item-title>Описание</v-list-item-title>
                <v-textarea
                  label="Описание"
                  v-model="bio"
                  :placeholder="user.description"
                  hint="Отображается в профиле"
                  
                >
                </v-textarea>
              </v-list-item-content>
            </v-list-item>
          </v-list>
          <v-divider></v-divider>
          <v-list
            three-line
            subheader
          >
            <v-subheader>Внешний вид</v-subheader>
            <v-list-item>
              <v-list-item-content>
                <v-list-item-title>Аватарка</v-list-item-title>
                <v-file-input
                accept="image/png, image/jpeg, image/bmp"
                placeholder="Выберите аватар"
                prepend-icon="mdi-camera"
                label=""
                ></v-file-input>
              </v-list-item-content>
            </v-list-item>
            <v-list-item>
              <v-list-item-content>
                <v-list-item-title
                
                >Баннер профиля</v-list-item-title>
                <v-file-input @change="fileSelected"
                accept="image/png, image/jpeg, image/bmp"
                placeholder="Выберите баннер"
                prepend-icon="mdi-camera"
                label=""
                ></v-file-input>
              </v-list-item-content>
            </v-list-item>
            </v-list-item>
          </v-list>
        </v-card>
      </v-dialog>
    </v-row>
  </v-app>
  <!-- generate loading -->
  <v-app id="inspire2">
  <div class="text-center">
        <v-dialog v-model="dialog" hide-overlay persistent width="200" height="100">
          <v-card color="primary" dark>
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
  <!-- generated card -->
  <v-app id="inspire2">
    <div class="text-center">
        <v-dialog v-model="dialog3" dark width="500" color="red">
          <v-card :loading="loading" class="mx-auto my-12" max-width="374">
            <template slot="progress">
              <v-progress-linear
                color="deep-purple"
                height="10"
                indeterminate
              ></v-progress-linear>
            </template>

            <vue-qr style="margin-left: 50%; transform: translateX(-50%); margin-top: 2rem; border-radius: 17px"  logoSrc='../assets/img/Group 13 (1).png' logoScale='0' logoBackgroundColor='transparent'  :text="card.qrurl" :size="250"></vue-qr>

            <v-card-title>{{ card.title }}</v-card-title>

            

            <v-card-text>
                <p>Текст: {{card.text}}</p>
                <p>Ссылка: <b>{{card.qrurl}}</b> </p>
                
                <v-divider style="" class="mx-4"></v-divider>
                <div style="display: flex; justify-content: space-between; align-item: center" class="">
                  <span style=" text-align: center;margin-top:10px; margin-right: 15px">Категория</span>
                  <v-chip style="margin-top: 10px" >{{ cardInfo.category.title }}</v-chip>
                </div>
                

            </v-card-text>

            <v-card-actions>
              <v-btn
                color="deep-purple lighten-2"
                text
                :href="card.qrurl"
              >
                Открыть
              </v-btn>
              <v-btn @click="copy()" color="deep-purple lighten-2" text>
                Скопировать ссылку
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
    </div>
  </v-app>
<div class="app">
    

    <div class="hamburger-menu " v-if="dialog4 == false">
        <div class="logo">
            <span>VirtualCard</span>
        </div>
        <input id="menu__toggle" type="checkbox" />
        <label class="menu__btn" for="menu__toggle">
            <span></span>
        </label>
    
        <ul class="menu__box">
            <li><a class="menu__item" onclick="window.location.href='/'"  href="#">Главная</a></li>
            <li><a class="menu__item" href="#">Поиск</a></li>
            <li><a class="menu__item" href="#">Маркет</a></li>
            <li><a class="menu__item" href="#">Профиль</a></li>
            <li><a class="menu__item" @click="logout()" href="#">Выйти</a></li>
        </ul>
    </div>
    <div class="nav" v-if="dialog4 == false">
    <div class="logo">
        <a href="/"><img src="/assets/img/Logo (1).svg" alt="VirtualCard" /></a>
    </div>

    <div class="buttons">
        <a class="navButton" href="#">Главная</a>
        <a class="navButton" href="#">Поиск</a>
        <a class="navButton" href="#">Маркет</a>
        <a class="navButton" @click="logout()" href="#">

        </a>
    </div>
    </div>

    
        <section class="userCard" >
            <div class="container mx-auto">
                <div class="card mt-20">
                    
                    <div class="card__info">
                        <div class="logo">
                            <svg width="117" height="115" viewBox="0 0 117 115" fill="none" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
                                <g filter="url(#filter0_b_149_20)">
                                <path d="M45.2334 6.14104C51.5555 2.35945 59.4445 2.35945 65.7666 6.14104L93.831 22.9279C99.8684 26.5392 103.564 33.0568 103.564 40.0917V74.9083C103.564 81.9432 99.8683 88.4608 93.831 92.0721L65.7666 108.859C59.4445 112.641 51.5555 112.641 45.2334 108.859L17.169 92.0721C11.1316 88.4608 7.43559 81.9432 7.43559 74.9083V40.0917C7.43559 33.0568 11.1316 26.5392 17.169 22.9279L45.2334 6.14104Z" fill="url(#paint0_linear_149_20)"/>
                                <path d="M45.2334 6.14104C51.5555 2.35945 59.4445 2.35945 65.7666 6.14104L93.831 22.9279C99.8684 26.5392 103.564 33.0568 103.564 40.0917V74.9083C103.564 81.9432 99.8683 88.4608 93.831 92.0721L65.7666 108.859C59.4445 112.641 51.5555 112.641 45.2334 108.859L17.169 92.0721C11.1316 88.4608 7.43559 81.9432 7.43559 74.9083V40.0917C7.43559 33.0568 11.1316 26.5392 17.169 22.9279L45.2334 6.14104Z" fill="url(#paint1_radial_149_20)" fill-opacity="0.2"/>
                                <path d="M65.51 6.57014L93.5744 23.357C99.4608 26.878 103.064 33.2327 103.064 40.0917V74.9083C103.064 81.7673 99.4607 88.122 93.5744 91.643L65.51 108.43C59.3459 112.117 51.6541 112.117 45.49 108.43L17.4256 91.643C11.5392 88.122 7.93559 81.7673 7.93559 74.9083V40.0917C7.93559 33.2327 11.5392 26.878 17.4256 23.357L45.49 6.57014C51.6541 2.88309 59.3459 2.88309 65.51 6.57014Z" stroke="#68CBDC"/>
                                </g>
                                <path d="M45.2074 11.1778C51.5424 7.37544 59.4576 7.37544 65.7926 11.1778L89.5269 25.4235C95.5495 29.0383 99.2343 35.5476 99.2343 42.5717V72.4283C99.2343 79.4524 95.5495 85.9617 89.5269 89.5765L65.7926 103.822C59.4576 107.625 51.5424 107.625 45.2074 103.822L21.4731 89.5765C15.4505 85.9617 11.7657 79.4524 11.7657 72.4283V42.5717C11.7657 35.5476 15.4505 29.0383 21.4731 25.4235L45.2074 11.1778Z" fill="url(#pattern0)"/>
                                <path d="M101.44 71.9452C102.24 70.947 103.76 70.947 104.56 71.9452L105.745 73.4226C106.212 74.0048 106.964 74.2785 107.696 74.1327L109.554 73.7626C110.808 73.5126 111.972 74.4891 111.944 75.7683L111.902 77.6618C111.885 78.4079 112.286 79.1011 112.94 79.4598L114.601 80.3702C115.723 80.9854 115.987 82.4814 115.143 83.4432L113.893 84.8667C113.401 85.4276 113.262 86.2159 113.533 86.9113L114.22 88.6763C114.684 89.8687 113.924 91.1843 112.66 91.3785L110.788 91.6661C110.05 91.7793 109.437 92.2939 109.197 93.0006L108.589 94.7942C108.178 96.006 106.751 96.5256 105.657 95.8614L104.038 94.8784C103.4 94.491 102.6 94.491 101.962 94.8784L100.343 95.8614C99.2494 96.5256 97.8219 96.006 97.4109 94.7942L96.8027 93.0006C96.5631 92.2939 95.9499 91.7793 95.2123 91.6661L93.3403 91.3785C92.0755 91.1843 91.316 89.8687 91.7802 88.6763L92.4671 86.9113C92.7378 86.2159 92.5988 85.4276 92.1066 84.8667L90.8574 83.4432C90.0134 82.4814 90.2772 80.9854 91.3993 80.3702L93.06 79.4598C93.7144 79.1011 94.1146 78.4079 94.0981 77.6618L94.0562 75.7683C94.0278 74.4891 95.1915 73.5126 96.4465 73.7626L98.3039 74.1327C99.0358 74.2785 99.7879 74.0048 100.255 73.4226L101.44 71.9452Z" fill="black"/>
                                <g clip-path="url(#clip0_149_20)">
                                <path d="M108.192 80.3355C107.855 79.9981 107.308 79.9983 106.97 80.3355L101.473 85.8325L99.0302 83.3894C98.6929 83.0521 98.146 83.0521 97.8087 83.3894C97.4713 83.7268 97.4713 84.2736 97.8087 84.611L100.862 87.6647C101.031 87.8333 101.252 87.9178 101.473 87.9178C101.694 87.9178 101.915 87.8335 102.084 87.6647L108.192 81.557C108.529 81.2199 108.529 80.6728 108.192 80.3355Z" fill="#00D1FF"/>
                                </g>
                                <defs>
                                <filter id="filter0_b_149_20" x="-80.3948" y="-84.5254" width="271.79" height="284.051" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
                                <feFlood flood-opacity="0" result="BackgroundImageFix"/>
                                <feGaussianBlur in="BackgroundImage" stdDeviation="43.9152"/>
                                <feComposite in2="SourceAlpha" operator="in" result="effect1_backgroundBlur_149_20"/>
                                <feBlend mode="normal" in="SourceGraphic" in2="effect1_backgroundBlur_149_20" result="shape"/>
                                </filter>
                                <pattern id="pattern0" patternContentUnits="objectBoundingBox" width="1" height="1">
                                <use xlink:href="#image0_149_20" transform="translate(-0.539604) scale(0.00192519)"/>
                                </pattern>
                                <linearGradient id="paint0_linear_149_20" x1="-101.715" y1="-127.808" x2="55.9453" y2="218.241" gradientUnits="userSpaceOnUse">
                                <stop offset="0.397419" stop-color="white" stop-opacity="0.2"/>
                                <stop offset="1" stop-color="white" stop-opacity="0"/>
                                </linearGradient>
                                <radialGradient id="paint1_radial_149_20" cx="0" cy="0" r="1" gradientUnits="userSpaceOnUse" gradientTransform="translate(56.3102 115.284) rotate(-90) scale(68.0627 65.6953)">
                                <stop stop-color="white"/>
                                <stop offset="1" stop-color="white" stop-opacity="0"/>
                                </radialGradient>
                                <clipPath id="clip0_149_20">
                                <rect width="10.8889" height="10.8889" fill="white" transform="translate(97.5557 78.5557)"/>
                                </clipPath>
                                <image id="image0_149_20" width="1080" height="540" xlink:href="/assets/img/5-1.jpg"></image>

                                </defs>
                            </svg>
                        </div>
                        <div class="bio">
                            <div class="bio__username">
                                <p class="user">{{user.name}}</p>
                                <a @click.prevent="dialog4 = !dialog4">
                                    <img src="/assets/img/pensil.svg" alt="">
                                </a>
                            </div>
                            <div class="bio__info">
                                <p>
                                    {{bio}}
                                </p>
                            </div>
                            <div class="bio__stats">
                                <span class="number">{{cardCount}}</span>
                                <span>{{decWord}}</span>
                                <button @click="dialog2 = !dialog2" v-if="loadedNum">
                                    <img src="/assets/img/addCard.svg" alt="">
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section class="cards" v-if="cardCount > 0">
            <div class="container mx-auto">
                <p class="presCard">Открытки</p>
                <div class="line"></div>    

                <div class="createdCards grid grid-cols-1 sm:grid-cols-2 md:grid-cols-2 lg:grid-cols-4 sm:px-8 sm:py-12 sm:gap-x-8 md:py-16">
                    <div v-for="(card, index) in cards" class="cardContainer" :key="card.id"  style="background-image: url('/assets/img/image 4.png')">
                        <div class="card">
                            <div class="card__background">
                                <img src="/assets/img/image 4.png" alt="">
                            </div>
                            <div class="card__info">
                                <div class="card__bio">
                                    <p>New Year</p>
                                    <span>
                                        Lorem ipsum dolor sit amet, consectetur adipiscing elit. 
                                    </span>    
                                </div>
                                <svg width="111" height="115" viewBox="0 0 111 115" fill="none" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
                                    <g filter="url(#filter0_b_149_21)">
                                    <path d="M45.2334 6.14104C51.5555 2.35945 59.4445 2.35945 65.7666 6.14104L93.831 22.9279C99.8684 26.5392 103.564 33.0568 103.564 40.0917V74.9083C103.564 81.9432 99.8683 88.4608 93.831 92.0721L65.7666 108.859C59.4445 112.641 51.5555 112.641 45.2334 108.859L17.169 92.0721C11.1316 88.4608 7.43559 81.9432 7.43559 74.9083V40.0917C7.43559 33.0568 11.1316 26.5392 17.169 22.9279L45.2334 6.14104Z" fill="url(#paint0_linear_149_21)"/>
                                    <path d="M45.2334 6.14104C51.5555 2.35945 59.4445 2.35945 65.7666 6.14104L93.831 22.9279C99.8684 26.5392 103.564 33.0568 103.564 40.0917V74.9083C103.564 81.9432 99.8683 88.4608 93.831 92.0721L65.7666 108.859C59.4445 112.641 51.5555 112.641 45.2334 108.859L17.169 92.0721C11.1316 88.4608 7.43559 81.9432 7.43559 74.9083V40.0917C7.43559 33.0568 11.1316 26.5392 17.169 22.9279L45.2334 6.14104Z" fill="url(#paint1_radial_149_21)" fill-opacity="0.2"/>
                                    <path d="M45.49 6.57014C51.6541 2.88309 59.3459 2.88309 65.51 6.57014L93.5744 23.357C99.4608 26.878 103.064 33.2327 103.064 40.0917V74.9083C103.064 81.7673 99.4607 88.122 93.5744 91.643L65.51 108.43C59.3459 112.117 51.6541 112.117 45.49 108.43L17.4256 91.643C11.5392 88.122 7.93559 81.7673 7.93559 74.9083V40.0917C7.93559 33.2327 11.5392 26.878 17.4256 23.357L45.49 6.57014Z" stroke="#68CBDC"/>
                                    </g>
                                    <path d="M45.2074 11.1778C51.5424 7.37544 59.4576 7.37544 65.7926 11.1778L89.5269 25.4235C95.5495 29.0383 99.2343 35.5476 99.2343 42.5717V72.4283C99.2343 79.4524 95.5495 85.9617 89.5269 89.5765L65.7926 103.822C59.4576 107.625 51.5424 107.625 45.2074 103.822L21.4731 89.5765C15.4505 85.9617 11.7657 79.4524 11.7657 72.4283V42.5717C11.7657 35.5476 15.4505 29.0383 21.4731 25.4235L45.2074 11.1778Z" fill="url(#pattern0)"/>
                                    <defs>
                                    <filter id="filter0_b_149_21" x="-80.3948" y="-84.5255" width="271.79" height="284.051" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
                                    <feFlood flood-opacity="0" result="BackgroundImageFix"/>
                                    <feGaussianBlur in="BackgroundImage" stdDeviation="43.9152"/>
                                    <feComposite in2="SourceAlpha" operator="in" result="effect1_backgroundBlur_149_21"/>
                                    <feBlend mode="normal" in="SourceGraphic" in2="effect1_backgroundBlur_149_21" result="shape"/>
                                    </filter>
                                    <pattern id="pattern0" patternContentUnits="objectBoundingBox" width="1" height="1">
                                    <use xlink:href="#image0_149_21" transform="translate(-0.539604) scale(0.00192519)"/>
                                    </pattern>
                                    <linearGradient id="paint0_linear_149_21" x1="-101.715" y1="-127.808" x2="55.9453" y2="218.241" gradientUnits="userSpaceOnUse">
                                    <stop offset="0.397419" stop-color="white" stop-opacity="0.2"/>
                                    <stop offset="1" stop-color="white" stop-opacity="0"/>
                                    </linearGradient>
                                    <radialGradient id="paint1_radial_149_21" cx="0" cy="0" r="1" gradientUnits="userSpaceOnUse" gradientTransform="translate(56.3102 115.284) rotate(-90) scale(68.0627 65.6953)">
                                    <stop stop-color="white"/>
                                    <stop offset="1" stop-color="white" stop-opacity="0"/>
                                    </radialGradient>
                                    <image id="image0_149_21" width="1080" height="540" xlink:href="/assets/img/5-1.jpg"></image>"
                                    </defs>
                                </svg>
                            </div>
                        </div>
                    </div>

                </div>
            </div>
            
        </section>



</div>
</v-main>
</template>

<style lang="sass" >
@font-face
    font-family: 'Druk'
    src: url('/assets/fonts/Druc.ttf') format('truetype')
@import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap')
*
    margin: 0
    padding: 0
html
    background: linear-gradient(0deg, rgba(0, 0, 0, 0.2), rgba(0, 0, 0, 0.2)), linear-gradient(90deg, #260B3B 1.27%, #13063E 41.27%, #310E41 83.95%, #3A1141 100%)
    //box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    overflow-x: hidden
*
    margin: 0
    padding: 0
.v-application--wrap
  display: none !important
#menu__toggle
    opacity: 0
    &:checked
        & + .menu__btn
            & > span
                transform: rotate(45deg)
                &::before
                    top: 0
                    transform: rotate(0deg)
                &::after
                    top: 0
                    transform: rotate(90deg)
        & ~ .menu__box
            left: 0 !important
.menu__btn
    position: fixed
    top: 20px
    left: 20px
    width: 26px
    height: 26px
    cursor: pointer
    z-index: 1
    & > span
        &::before
            content: ''
            top: -8px
        &::after
            content: ''
            top: 8px
.logo
    img
        cursor: pointer
.hamburger-menu
    backdrop-filter: blur(10px)
    height: 50px
    position: fixed
    z-index: 999
    width: 100%
    .logo
        position: absolute
        right: 20px
        top: 10px
        font-family: 'Montserrat'
        font-style: normal
        font-weight: 500
        font-size: 19px
        line-height: 115%
        /* identical to box height, or 22px */

        letter-spacing: -0.045em

        color: #FFFFFF
.menu__btn > span,
.menu__btn > span::before,
.menu__btn > span::after
    display: block
    position: absolute
    width: 100%
    height: 2px
    background-color: #616161
    transition-duration: .25s
.menu__box
    display: block
    position: fixed
    top: 0
    left: -100%
    width: 300px
    height: 100vh

    z-index: 99922222
    margin: 0
    padding: 80px 0
    list-style: none
    backdrop-filter: blur(5px)
    background-color: #292941
    box-shadow: 2px 2px 6px #00000066
    transition-duration: .25s
.menu__item
    display: block
    padding: 12px 24px
    color: #A5A4AF

    font-family: 'Roboto', sans-serif
    font-size: 20px
    font-weight: 600
    text-decoration: none
    transition-duration: .25s
    font-family: 'Montserrat'
    font-style: normal
    font-weight: 500
    font-size: 19px
    line-height: 115%
    /* identical to box height, or 22px */

    letter-spacing: -0.045em

    &:hover
        background-color: #1e1e30
.hamburger-menu
    display: none
*
    &::-webkit-scrollbar
        width: 5px

    &::-webkit-scrollbar-track
        background: #2e1e8a

    &::-webkit-scrollbar-thumb
        background: #af1cdb
.app
    background-color: transparent
    background-size: cover
    background-repeat: no-repeat
    width: 100vw
    height: 100%
.main
    width: 100vw
    position: absolute
    .container
        position: relative
        vertical-align: middle
        // left: 50%
        margin: 0 auto
        width: 457px
        height: 459px
        margin-top: 200px
        background: #292941
        box-shadow: 0px 10px 30px -10px rgba(0, 0, 0, 0.42)
        border-radius: 9px
    .buttons
        margin-top: 73px
        display: flex
        a
            display: flex
            justify-content: center
            align-items: center
            text-decoration: none
            text-align: center
            font-family: 'Montserrat'
            font-style: normal
            font-weight: 700
            font-size: 21px
            line-height: 115%
            /* or 24px */

            letter-spacing: -0.045em

            color: #FFFFFF
        button

            border: none
            width: 250px
            height: 64.91px
            cursor: pointer
            background: linear-gradient(90deg, #FF005B 0%, #662D8C 100%)
            box-shadow: 0px 10px 30px 4px rgba(208, 0, 255, 0.082), inset 0px 0px 0px 1px rgba(255, 255, 255, 0.24)
            border-radius: 88px

            transform-style: preserve-3d
            a
                transform: translateZ(20px)
                img
                    padding-right: 17px
            &:hover
                box-shadow: 0px 10px 30px 4px rgba(207, 0, 255, 0.5), inset 0px 0px 0px 1px rgba(255, 255, 255, 0.24)
        .searchButton
            width: 188.03px
            height: 64.91px
            margin-left: 40px
            background: linear-gradient(90deg, #2B0950 0%, #411273 100%)
            box-shadow: 0px 10px 30px 4px rgba(208, 0, 255, 0.192), inset 0px 2px 6px #FF005B
            border-radius: 88px
            &:hover
                box-shadow: 0px 10px 30px 4px rgba(207, 0, 255, 0.5), inset 0px 2px 6px #FF005B
.nav
    padding: 37px 100px 0px 100px
    display: flex
    justify-content: space-between
    align-items: center

    .buttons
        display: flex
        justify-content: space-between
        align-items: center
        a
            padding: 0px 60px
            font-family: 'Montserrat'
            font-style: normal
            font-weight: 700
            font-size: 19px
            line-height: 115%
            /* identical to box height, or 22px */
            text-decoration: none
            letter-spacing: -0.045em
            color: #A5A4AF
        .profile
            cursor: pointer
            display: flex
            justify-content: space-between
            align-items: center
            height: 43px
            left: 1732px
            top: 41px

            background: rgba(255, 255, 255, 0.28)
            backdrop-filter: blur(4px)
            /* Note: backdrop-filter has minimal browser support */

            border-radius: 13px
            img
                padding-left: 14px
            span
                font-family: 'Montserrat'
                font-style: normal
                font-weight: 700
                font-size: 19px
                line-height: 115%
                /* or 16px */

                letter-spacing: -0.045em

                color: rgba(255, 255, 255, 0.37)
                padding-left: 17px
                padding-right: 14px
.navButtons
    padding: 35px 44px
    display: flex
    justify-content: space-between
    align-items: center
    a
        font-family: 'Montserrat'
        font-style: normal
        font-weight: 600
        font-size: 24px
        line-height: 115%
        /* identical to box height, or 28px */

        letter-spacing: -0.045em
        cursor: pointer
        color: #71708C
        &:nth-last-child(1)
            margin-left: 24px

    .active
        color: #FBFCFF
.inputs
    display: flex
    justify-content: center
    align-items: center
    padding: 20px 44px
    input
        font-family: 'Montserrat'
        font-style: normal
        font-weight: 400
        font-size: 19px
        line-height: 115%
        /* identical to box height, or 22px */
        letter-spacing: -0.045em

        color: #7A7993
        border: none
        background: #33314A
        border-radius: 9px
        width: 80%
        height: 38px
        color: white
        padding: 0 29px
        &:focus
            border: none
            text-decoration: none
            outline: none
        &::placeholder
            font-family: 'Montserrat'
            font-style: normal
            font-weight: 400
            font-size: 19px
            line-height: 115%
            /* identical to box height, or 22px */
            letter-spacing: -0.045em

            color: #7A7993
.buttonSend
    margin: 35px 44px
    width: 141px
    height: 45px
    display: flex
    justify-content: center
    align-items: center

    background: linear-gradient(90deg, #FB5915 0%, #D93C98 100%)
    cursor: pointer
    border-radius: 88px
    font-family: 'Montserrat'
    font-style: normal
    font-weight: 700
    font-size: 21px
    line-height: 115%
    /* or 24px */
    text-align: center
    letter-spacing: -0.045em
    align-self: flex-end
    color: #FFFFFF
    &:hover
        box-shadow: 0px 10px 30px -10px #E94A5B

.userCard
    .card
        width: 100%
        // test
        //height: 491px !important

        background-image: url("/assets/img/Frame 2184.jpg")
        background-size: cover
        background-repeat: no-repeat
        border-radius: 17px
        //background-position-y: center

        display: flex
        flex-direction: column
        justify-content: flex-end
        &__info
            height: 60%
            margin-top: 10rem
            width: 100%
            border-radius: 0 0 17px 17px
            align-self: flex-end

            background: radial-gradient(59.18% 59.18% at 50.73% 100.25%, rgba(255, 255, 255, 0.2) 0%, rgba(255, 255, 255, 0) 100%), linear-gradient(156.26deg, rgba(255, 255, 255, 0.2) -4.88%, rgba(255, 255, 255, 0) 147.21%)

            backdrop-filter: blur(87.8303px)

            display: flex
            flex-direction: column
            justify-content: flex-start
            align-items: center
            .logo
                transform: translateY(-50%)
            .bio
                margin-bottom: 1rem
                display: flex
                justify-content: center
                align-items: center
                flex-direction: column
                &__username
                    margin-top: -3rem
                    display: flex !important
                    justify-content: center
                    align-items: center
                    p
                        font-family: 'Montserrat'
                        font-style: normal
                        font-weight: 700
                        font-size: 26px
                        line-height: 115%
                        /* identical to box height, or 30px */

                        //letter-spacing: -0.045em;

                        color: #FFFFFF
                    a
                        margin-left: 15px
                        img
                            height: 30px
                &__info
                    width: 366px
                    margin-top: 1rem
                    p
                        font-family: 'Montserrat'
                        font-style: normal
                        font-weight: 300
                        font-size: 18px
                        line-height: 115%
                        /* or 21px */

                        text-align: center
                        letter-spacing: -0.045em

                        color: rgba(255, 255, 255, 0.76)
                &__stats
                    margin-top: 2rem
                    width: 90%
                    display: flex
                    justify-content: space-between
                    align-items: center
                    span
                        font-family: 'Montserrat'
                        font-style: normal
                        font-weight: 700
                        font-size: 22px
                        line-height: 100%
                        /* identical to box height, or 22px */

                        text-align: center

                        color: #FFFFFF

                        /* Inside auto layout */

                        flex: none
                        order: 0
                        flex-grow: 0
                        margin: 0px 10px
                    .number
                        font-size: 57px
                        line-height: 115%
                        text-align: center
                        letter-spacing: -0.045em
                        color: #FFFFFF

.cards
    padding-bottom: 2rem
    .line
        height: 1px
        background-color: #E0DFDF
        margin-top: 32px
    .presCard
        margin-top: 4rem
        font-family: 'Druk'
        font-style: normal
        font-weight: 800
        font-size: 44px
        line-height: 115%
        /* identical to box height, or 51px */

        letter-spacing: -0.045em

        color: #FFFFFF
    .createdCards
        margin-top: 3rem

        // padding-bottom: 3rem
        .cardContainer
            display: flex
            justify-content: center
            align-items: center
            flex-direction: column
            max-width: 363px
            margin-top: 3rem
            border-radius: 17px
            background-image: url("/assets/img/image 2.png")
            background-size: cover
            background-repeat: no-repeat

            .card
                display: flex
                justify-content: center
                align-items: center
                flex-direction: column
                border-radius: 17px
                padding: 19px
                width: 100%
                height: 100%
                background: radial-gradient(59.18% 59.18% at 50.73% 100.25%, rgba(255, 255, 255, 0.2) 0%, rgba(255, 255, 255, 0) 100%), linear-gradient(156.26deg, rgba(255, 255, 255, 0.2) -4.88%, rgba(255, 255, 255, 0) 147.21%)
                backdrop-filter: blur(87.8303px)
                &__info
                    display: flex
                    justify-content: space-between
                    align-items: center
                &__background

                    border-radius: 17px
                &__bio
                    max-width: 70%
                    p
                        margin-top: 19px
                        font-family: 'Montserrat'
                        font-style: normal
                        font-weight: 700
                        font-size: 26px
                        line-height: 115%
                        /* identical to box height, or 30px */

                        letter-spacing: -0.045em

                        color: #FFFFFF
                    span
                        margin-top: 30px
                        font-family: 'Montserrat'
                        font-style: normal
                        font-weight: 400
                        font-size: 18px
                        line-height: 115%
                        /* or 21px */

                        letter-spacing: -0.045em

                        color: rgba(255, 255, 255, 0.76)

                        mix-blend-mode: overlay

@media screen and (max-width: 1079px)
    .container
        padding: 0px 10px 0px 10px !important
    .hamburger-menu
        top: 0
        display: block
    .nav
        display: none
@media screen and (max-width: 952px)
    .container
        margin-top: 20px
        h1
            font-size: 66px
@media screen and (max-width: 740px)

    .container
        margin-top: 20px
        h1
            font-size: 56px
@media screen and (max-width: 350px)
    h1
        position: absolute
        top: 10%
        text-align: center
        left: 50%
        z-index: 1
        transform: translateX(-50%)
        font-size: 20px !important
    .buttons
        flex-direction: column
        button
            margin-top: 10%
            width: 80vw
        .searchButton
            box-shadow: none !important
            border: 1px solid #ffffff42 !important
    .main .container p
        font-size: 15px !important
        word-break: break-word
@media screen and (max-width: 950px)
    body
        height: 1000px
@media screen and (max-width: 687px)
    .video2
        height: 90vw !important
    .bio__info
        width: 80% !important
    .presCard
        // display: flex
        // justify-content: center
        // align-items: center
        font-size: 26px !important
@media screen and (max-width: 687px)
    .container
        width: 80vw !important
@media screen and (max-width: 448px)
    .container
        width: 80vw !important
    .navButtons, .inputs
        padding: 20px 10px
    .buttonSend
        margin: 25px 10px
        align-self: center
        margin: 0 auto
        width: 90%

@media screen and (max-width: 448px)
    .container
        width: 80vw !important
    .navButtons a
        font-size: 18px !important

    .navButtons, .inputs
        padding: 20px 10px
    .buttonSend
        margin: 20px 10px
@media screen and (max-width: 338px)
    .userCard .card__info .bio__stats .number
        font-size: 40px !important
    .userCard .card__info .bio__stats span
        font-size: 18px !important

</style>

<script>
const HOST = process.env.HOST;
import { Notyf } from "notyf";
import "notyf/notyf.min.css";
import VueQr from 'vue-qr'

const notyf = new Notyf({
  position: { x: "center", y: "top" },
  duration: 4000,
  dismissible: true,
});

function declOfNum(number, words) {  
    return words[(number % 100 > 4 && number % 100 < 20) ? 2 : [2, 0, 1, 1, 1, 2][(number % 10 < 5) ? Math.abs(number) % 10 : 5]];
}

import "animate.css";
import { log } from "aframe";
const host = "//127.0.0.1:8000/api/";
export default {
  layout: "empty",
  // head() {
  //   return {
  //     script: [
  //       {
  //         //src: "https://cdn.tailwindcss.com",
  //       },
  //     ],
  //   };
  // },
  components: {VueQr},
  beforeMount() {
    try {
      if (localStorage.getItem("user") !== "") {
        this.token = JSON.parse(localStorage.getItem("user")).token;
      } else {
        
      }
      if (localStorage.getItem("user")) {
        try {
          this.user = JSON.parse(localStorage.getItem("user"));
        } catch (e) {
          console.log(e);
          localStorage.removeItem("user");
        }
      }
      console.log(this.token);
    }
    catch(e){
      localStorage.removeItem("user");
      this.token = null
      window.location.href = '/signin';
      // window.location.reload();
    }
    this.fetchUserInfo()
    this.fetchGetCards();
    try {
      this.cardCount = this.cards.length;
    } catch (e) {
      console.log(e);
    }
  },
//   mounted() {

//   },
  data: () => ({
    form: "auth",
    select: null,
    form: {
        title: "",
        content: "123",
        scene: 2,
        category: 2,
        name: '',
        image: null,
    },
    token: "",
    cardCount: null,
    classauth: "active",
    classregister: "",
    loadedNum: false,
    cards: null,
    user: "",
    bio: "Всем привет! Я начал использовать замечательный проект – VirtualCard. Тут я делюсь своими открытками",
    profileForm: {
      name: "",
      description: "",
      image: null,
      banner: null,
    },
    
    loginForm: {
      email: "",
      password: "",
    },
    registForm: {
      name: "123",
      email: "test23@gmail.com",
      password: "123",
      conpassword: '',
    },
    cardInfo: {
        category: {
          title: null,
        },
    },
    dialog: false,
    dialog2: false,
    dialog3: false,
    dialog4: false,
    card: {
        title: "1qw",
        content: "123",
        scene: 2,
        category: 2,
        qrurl: ' ',
      },
      items: [
        { name: "Зима", value: "1" },
        { name: "Дом", value: "2" },
        { name: "Улица", value: "3" },
        { name: "Закат", value: "4" },
      ],
      categories: [
        { name: "Поздравление", value: "1" },
        { name: "День рождения", value: "2" },
        { name: "Доброе утро", value: "3" },
        { name: "Зима", value: "4" },
      ],
    decWord: null,
  }),

  methods: {

    logout() {
      localStorage.clear();
      notyf.success("Вы вышли");
      setTimeout(() => {
        window.location.href = "/";
      }, 1000);
      
    },

    async fetchUserInfo() {
      let url = HOST + "user";
      let result = await fetch(url, {
        method: "GET",
        headers: {
          "Content-Type": "application/json",
          Authorization: "Bearer " + this.token,
        },
      });
      let data = await result.json();
      if (data.success === true) {
        this.user = data.data;
        console.log(this.user);
      } else {
        notyf.error(data.message);
      }
    },
    fileSelected() {
      if(event.target.files.length)
        this.postForm.image = event.target.files[0];
    },
    AvatarSelected() {
      if(event.target.files.length)
        this.profileForm.image = event.target.files[0];
    },
    BannerSelected() {
      if(event.target.files.length)
        this.profileForm.image = event.target.files[0];
    },
    async fetchGetCards() {
      let url = HOST + "show/cards";
      let result = await fetch(url, {
        method: "GET",
        headers: {
          "Content-Type": "application/json",
          Authorization: "Bearer " + this.token,
        },
      });
      let data = await result.json();
      if (data.success === true) {
        this.cards = data.data;
        console.log(this.cards);
        this.cardCount = this.cards.length
        this.decWord = declOfNum(this.cardCount, ['открытка', 'открытки', 'открыток'])
        this.loadedNum = true;
      } else {
        notyf.error(data.message);
      }
    },

    switchto(data) {
      if (data != "auth") {
        this.loginForm.email == "";
        this.loginForm.password == "";
        this.classauth = "";
        this.classregister = "active";
        this.form = "register";
      } else {

        this.classauth = "active";
        this.classregister = "";
        this.form = "auth";
      }

      setTimeout(() => {$('.buttonSend').tilt({scale: 1.1, speed: 1000})}, 500);

    },
    validate(datatext) {
      let re = /^[\w-\.]+@[\w-]+\.[a-z]{2,4}$/i;

      if (datatext == 'auth') {
        console.log('ne vnytri')
        try {
          if (
            this.loginForm.email.length >= 1 &&
            this.loginForm.password.length >= 1
          ) {
            console.log('vnytri')
            if (!re.test(this.loginForm.email)) {
              notyf.error("Неправильная почта");
              return false;
            } else {
              return true;
            }
          } else {
            notyf.error("Заполните все поля");
            console.log(this.loginForm.email, this.loginForm.password);
            return false;
          }
        } catch (e) {
          console.log(e);
          notyf.error("Произошла ошибка");
        }

        this.auth();
      } else {

      }
    },
    async login() {
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
        try {
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
                setTimeout(() => {
                  this.$router.push({
                    path: "/",
                  });
                  window.location.href='/'
                }, 1000);
              } else {
                notyf.error("Ошибка: " + data.message);
              }
            });
        } catch (e) {
          notyf.error(String(e));
        }
      }

    },
    opencard(data) {
        console.log('opencard');
        window.location.href  = '/card/' + data
    },
    async auth() {
      let status = "";
      try {
        await fetch(host + `login`, {
          method: "POST",
          headers: {
            // 'Access-Control-Allow-Origin' : '*',
            "Content-Type": "application/json",
          },
          body: JSON.stringify(this.loginForm),
        })
          .then((res) => {
            status = res.status;
            res.json();
          })
          .then((res) => {
            notyf.error(body);
            console.log(res);
            notyf.error(String(body.message[0]));
            notyf.error(String(body.message[0]));
            notyf.error(String(body.message[0]));
            this.user = body;
          });
      } catch (e) {
        notyf.error('error')
      }

      console.log(this.user);
      this.token = this.user.api_token;
      localStorage.setItem("api-token", this.token);
    },
    async register() {
      let email = this.registForm.email;
      let name = this.registForm.name;
      let password = this.registForm.password;
      let conpassword = this.registForm.conpassword;
      let data = {
        email: email,
        name: name,
        password: password,
        confirm_password: conpassword,
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
        try {
          await fetch(HOST + "register", {
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
                notyf.success("Вы успешно зарегистрировались");
                localStorage.setItem("user", JSON.stringify(this.user.data));
                console.log(JSON.parse(localStorage.getItem("user")));
                setTimeout(() => {
                  this.$router.push({
                    path: "/",
                  });
                  window.location.href='/'
                }, 1000);

              } else {
                this.errorNotyf(data)
              }
            });
        }
        catch(e) {
          notyf.error(String(e))
        }

      }
    },

    async generate() {
      try {
        let result;
        let form = {
            name: this.form.name,
            category_id: this.form.category.value,
            scene_id: this.form.scene,
            title: this.form.title,
            text: this.form.content,
        }
        await fetch(HOST + `cards`, {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
            Accept: "application/json",
            Authorization: "Bearer " + this.token,
          },
          body: JSON.stringify(form),
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
            let url = data.data.url
            // if (result == 1) {
            //   // this.user = data;
            //   // this.saveLocalData();
            // } else {
            // }
            if (result == 1) {
              //setTimeout(() => (notyf.success("Открытка создана")), 4000);

              setTimeout(() => {
                notyf.success("Открытка создана");
                this.dialog = false
                this.dialog3 = true
              }, 5000)
              ;
              this.cardInfo = data.data
              console.log('card info');
              console.log(this.cardInfo);
              this.card = form
              this.dialog2 = false; this.dialog = true;
              
              console.log(location.href.slice(0, -1) + 'card/url?url=' + url);
              this.card.qrurl = String(location.href.slice(0, -1).slice(0, -1).slice(0, -1) + 'card/url?url=' + url)

            } else {
              this.errorNotyf(data)
            }
          });
          console.log(this.card);
          // .then((body) => {
          //   console.log(body);
          //   //this.card = body["Created card"];
          // });
        //dialog2 = false; dialog = true;
      } catch (e) {
        console.log(e);
        setTimeout(() => (notyf.error(String(e))), 4000);
        
      }
    },

    // Вывод ошибок Notyf
    errorNotyf(data) {
      for (let i = 0; i < Object.keys(data.message).length; i++) {
        let value = Object.values(data.message)[i];
        notyf.error(value[0]);
      }
    },
    changeProfile() {
      
    },
    copy() {
      try {
        navigator.clipboard.writeText(this.card.qrurl)
      } catch(e){
        console.log(e);
      }
      
    },
    reset() {
      this.$refs.form.reset();
    },
    resetValidation() {
      this.$refs.form.resetValidation();
    },
  },
};
</script>
