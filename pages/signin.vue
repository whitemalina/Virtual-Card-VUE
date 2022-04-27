<template>
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
    <div class="nav">
      <div class="logo">
        <a href="/"><img src="/assets/img/Logo (1).svg" alt="VirtualCard" /></a>
      </div>

      <div class="buttons">
        <a class="navButton" href="#">Главная</a>
        <a class="navButton" href="#">Поиск</a>
        <a class="navButton" href="#">Маркет</a>
      </div>
    </div>

    <div class="main">
      <div class="container">
        <div class="navButtons">
          <div class="navLink">
            <a :class="classauth" @click="switchto('auth')">Вход</a>
            <a :class="classregister" @click="switchto('reg')" class=""
            >Регистрация</a
            >
          </div>
          <img src="/assets/img/logreg.svg" alt="" />
        </div>
        <transition name="fade" mode="out-in">
          <div key="reg" v-if="form == 'register'" class="inputForm">
            <div style="padding: 10px 44px;" class="inputs">
              <input v-model="registForm.name" type="email" placeholder="Имя" />
            </div>

            <div style="padding: 10px 44px;" class="inputs">
              <input v-model="registForm.email" type="email" placeholder="Email" />
            </div>
            <div  style="padding: 10px 44px;" class="inputs">
              <input v-model="registForm.password" type="password" placeholder="Пароль" />
            </div>
            <div style="padding: 10px 44px;" class="inputs">
              <input v-model="registForm.conpassword" type="password" placeholder="Подтверждение пароля" />
            </div>
          </div>

          <div key='123' v-if="form == 'auth'" class="inputForm">
            <div class="inputs">
              <input v-model="loginForm.email" type="email" placeholder="Email" />
            </div>
            <div class="inputs">
              <input v-model="loginForm.password" type="password" placeholder="Пароль" />
            </div>

          </div>


        </transition>
        <transition name="fade" mode="out-in">
          <div key='auth' @click="login()" class="buttonSend" v-if="form == 'auth'"><p>Войти</p></div>
          <div key='register' @click="register()" class="buttonSend reg" v-if="form == 'register'"><p>Зарегистрироваться</p></div>
        </transition>
      </div>
    </div>
  </div>
</template>

<style >
.fade-enter-active, .fade-leave-active {
  transition: opacity .3s ease;
}
.fade-enter, .fade-leave-to
  /* .component-fade-leave-active до версии 2.1.8 */ {
  opacity: 0;
}
/* cyrillic-ext */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 100;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq6R8WXV0poK5.woff2)
  format("woff2");
  unicode-range: U+0460-052F, U+1C80-1C88, U+20B4, U+2DE0-2DFF, U+A640-A69F,
  U+FE2E-FE2F;
}
/* cyrillic */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 100;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq6R8WXx0poK5.woff2)
  format("woff2");
  unicode-range: U+0400-045F, U+0490-0491, U+04B0-04B1, U+2116;
}
/* vietnamese */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 100;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq6R8WXd0poK5.woff2)
  format("woff2");
  unicode-range: U+0102-0103, U+0110-0111, U+0128-0129, U+0168-0169, U+01A0-01A1,
  U+01AF-01B0, U+1EA0-1EF9, U+20AB;
}
/* latin-ext */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 100;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq6R8WXZ0poK5.woff2)
  format("woff2");
  unicode-range: U+0100-024F, U+0259, U+1E00-1EFF, U+2020, U+20A0-20AB,
  U+20AD-20CF, U+2113, U+2C60-2C7F, U+A720-A7FF;
}
/* latin */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 100;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq6R8WXh0pg.woff2)
  format("woff2");
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA,
  U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215,
  U+FEFF, U+FFFD;
}
/* cyrillic-ext */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 200;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jqyR9WXV0poK5.woff2)
  format("woff2");
  unicode-range: U+0460-052F, U+1C80-1C88, U+20B4, U+2DE0-2DFF, U+A640-A69F,
  U+FE2E-FE2F;
}
/* cyrillic */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 200;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jqyR9WXx0poK5.woff2)
  format("woff2");
  unicode-range: U+0400-045F, U+0490-0491, U+04B0-04B1, U+2116;
}
/* vietnamese */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 200;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jqyR9WXd0poK5.woff2)
  format("woff2");
  unicode-range: U+0102-0103, U+0110-0111, U+0128-0129, U+0168-0169, U+01A0-01A1,
  U+01AF-01B0, U+1EA0-1EF9, U+20AB;
}
/* latin-ext */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 200;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jqyR9WXZ0poK5.woff2)
  format("woff2");
  unicode-range: U+0100-024F, U+0259, U+1E00-1EFF, U+2020, U+20A0-20AB,
  U+20AD-20CF, U+2113, U+2C60-2C7F, U+A720-A7FF;
}
/* latin */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 200;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jqyR9WXh0pg.woff2)
  format("woff2");
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA,
  U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215,
  U+FEFF, U+FFFD;
}
/* cyrillic-ext */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 300;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq_p9WXV0poK5.woff2)
  format("woff2");
  unicode-range: U+0460-052F, U+1C80-1C88, U+20B4, U+2DE0-2DFF, U+A640-A69F,
  U+FE2E-FE2F;
}
/* cyrillic */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 300;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq_p9WXx0poK5.woff2)
  format("woff2");
  unicode-range: U+0400-045F, U+0490-0491, U+04B0-04B1, U+2116;
}
/* vietnamese */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 300;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq_p9WXd0poK5.woff2)
  format("woff2");
  unicode-range: U+0102-0103, U+0110-0111, U+0128-0129, U+0168-0169, U+01A0-01A1,
  U+01AF-01B0, U+1EA0-1EF9, U+20AB;
}
/* latin-ext */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 300;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq_p9WXZ0poK5.woff2)
  format("woff2");
  unicode-range: U+0100-024F, U+0259, U+1E00-1EFF, U+2020, U+20A0-20AB,
  U+20AD-20CF, U+2113, U+2C60-2C7F, U+A720-A7FF;
}
/* latin */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 300;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq_p9WXh0pg.woff2)
  format("woff2");
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA,
  U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215,
  U+FEFF, U+FFFD;
}
/* cyrillic-ext */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 400;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq6R9WXV0poK5.woff2)
  format("woff2");
  unicode-range: U+0460-052F, U+1C80-1C88, U+20B4, U+2DE0-2DFF, U+A640-A69F,
  U+FE2E-FE2F;
}
/* cyrillic */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 400;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq6R9WXx0poK5.woff2)
  format("woff2");
  unicode-range: U+0400-045F, U+0490-0491, U+04B0-04B1, U+2116;
}
/* vietnamese */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 400;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq6R9WXd0poK5.woff2)
  format("woff2");
  unicode-range: U+0102-0103, U+0110-0111, U+0128-0129, U+0168-0169, U+01A0-01A1,
  U+01AF-01B0, U+1EA0-1EF9, U+20AB;
}
/* latin-ext */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 400;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq6R9WXZ0poK5.woff2)
  format("woff2");
  unicode-range: U+0100-024F, U+0259, U+1E00-1EFF, U+2020, U+20A0-20AB,
  U+20AD-20CF, U+2113, U+2C60-2C7F, U+A720-A7FF;
}
/* latin */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 400;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq6R9WXh0pg.woff2)
  format("woff2");
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA,
  U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215,
  U+FEFF, U+FFFD;
}
/* cyrillic-ext */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 500;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq5Z9WXV0poK5.woff2)
  format("woff2");
  unicode-range: U+0460-052F, U+1C80-1C88, U+20B4, U+2DE0-2DFF, U+A640-A69F,
  U+FE2E-FE2F;
}
/* cyrillic */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 500;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq5Z9WXx0poK5.woff2)
  format("woff2");
  unicode-range: U+0400-045F, U+0490-0491, U+04B0-04B1, U+2116;
}
/* vietnamese */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 500;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq5Z9WXd0poK5.woff2)
  format("woff2");
  unicode-range: U+0102-0103, U+0110-0111, U+0128-0129, U+0168-0169, U+01A0-01A1,
  U+01AF-01B0, U+1EA0-1EF9, U+20AB;
}
/* latin-ext */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 500;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq5Z9WXZ0poK5.woff2)
  format("woff2");
  unicode-range: U+0100-024F, U+0259, U+1E00-1EFF, U+2020, U+20A0-20AB,
  U+20AD-20CF, U+2113, U+2C60-2C7F, U+A720-A7FF;
}
/* latin */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 500;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq5Z9WXh0pg.woff2)
  format("woff2");
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA,
  U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215,
  U+FEFF, U+FFFD;
}
/* cyrillic-ext */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 600;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq3p6WXV0poK5.woff2)
  format("woff2");
  unicode-range: U+0460-052F, U+1C80-1C88, U+20B4, U+2DE0-2DFF, U+A640-A69F,
  U+FE2E-FE2F;
}
/* cyrillic */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 600;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq3p6WXx0poK5.woff2)
  format("woff2");
  unicode-range: U+0400-045F, U+0490-0491, U+04B0-04B1, U+2116;
}
/* vietnamese */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 600;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq3p6WXd0poK5.woff2)
  format("woff2");
  unicode-range: U+0102-0103, U+0110-0111, U+0128-0129, U+0168-0169, U+01A0-01A1,
  U+01AF-01B0, U+1EA0-1EF9, U+20AB;
}
/* latin-ext */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 600;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq3p6WXZ0poK5.woff2)
  format("woff2");
  unicode-range: U+0100-024F, U+0259, U+1E00-1EFF, U+2020, U+20A0-20AB,
  U+20AD-20CF, U+2113, U+2C60-2C7F, U+A720-A7FF;
}
/* latin */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 600;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq3p6WXh0pg.woff2)
  format("woff2");
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA,
  U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215,
  U+FEFF, U+FFFD;
}
/* cyrillic-ext */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 700;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq0N6WXV0poK5.woff2)
  format("woff2");
  unicode-range: U+0460-052F, U+1C80-1C88, U+20B4, U+2DE0-2DFF, U+A640-A69F,
  U+FE2E-FE2F;
}
/* cyrillic */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 700;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq0N6WXx0poK5.woff2)
  format("woff2");
  unicode-range: U+0400-045F, U+0490-0491, U+04B0-04B1, U+2116;
}
/* vietnamese */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 700;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq0N6WXd0poK5.woff2)
  format("woff2");
  unicode-range: U+0102-0103, U+0110-0111, U+0128-0129, U+0168-0169, U+01A0-01A1,
  U+01AF-01B0, U+1EA0-1EF9, U+20AB;
}
/* latin-ext */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 700;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq0N6WXZ0poK5.woff2)
  format("woff2");
  unicode-range: U+0100-024F, U+0259, U+1E00-1EFF, U+2020, U+20A0-20AB,
  U+20AD-20CF, U+2113, U+2C60-2C7F, U+A720-A7FF;
}
/* latin */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 700;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jq0N6WXh0pg.woff2)
  format("woff2");
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA,
  U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215,
  U+FEFF, U+FFFD;
}
/* cyrillic-ext */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 800;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jqyR6WXV0poK5.woff2)
  format("woff2");
  unicode-range: U+0460-052F, U+1C80-1C88, U+20B4, U+2DE0-2DFF, U+A640-A69F,
  U+FE2E-FE2F;
}
/* cyrillic */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 800;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jqyR6WXx0poK5.woff2)
  format("woff2");
  unicode-range: U+0400-045F, U+0490-0491, U+04B0-04B1, U+2116;
}
/* vietnamese */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 800;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jqyR6WXd0poK5.woff2)
  format("woff2");
  unicode-range: U+0102-0103, U+0110-0111, U+0128-0129, U+0168-0169, U+01A0-01A1,
  U+01AF-01B0, U+1EA0-1EF9, U+20AB;
}
/* latin-ext */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 800;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jqyR6WXZ0poK5.woff2)
  format("woff2");
  unicode-range: U+0100-024F, U+0259, U+1E00-1EFF, U+2020, U+20A0-20AB,
  U+20AD-20CF, U+2113, U+2C60-2C7F, U+A720-A7FF;
}
/* latin */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 800;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jqyR6WXh0pg.woff2)
  format("woff2");
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA,
  U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215,
  U+FEFF, U+FFFD;
}
/* cyrillic-ext */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 900;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jqw16WXV0poK5.woff2)
  format("woff2");
  unicode-range: U+0460-052F, U+1C80-1C88, U+20B4, U+2DE0-2DFF, U+A640-A69F,
  U+FE2E-FE2F;
}
/* cyrillic */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 900;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jqw16WXx0poK5.woff2)
  format("woff2");
  unicode-range: U+0400-045F, U+0490-0491, U+04B0-04B1, U+2116;
}
/* vietnamese */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 900;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jqw16WXd0poK5.woff2)
  format("woff2");
  unicode-range: U+0102-0103, U+0110-0111, U+0128-0129, U+0168-0169, U+01A0-01A1,
  U+01AF-01B0, U+1EA0-1EF9, U+20AB;
}
/* latin-ext */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 900;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jqw16WXZ0poK5.woff2)
  format("woff2");
  unicode-range: U+0100-024F, U+0259, U+1E00-1EFF, U+2020, U+20A0-20AB,
  U+20AD-20CF, U+2113, U+2C60-2C7F, U+A720-A7FF;
}
/* latin */
@font-face {
  font-family: "Montserrat";
  font-style: italic;
  font-weight: 900;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUFjIg1_i6t8kCHKm459Wx7xQYXK0vOoz6jqw16WXh0pg.woff2)
  format("woff2");
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA,
  U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215,
  U+FEFF, U+FFFD;
}
/* cyrillic-ext */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 100;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCtr6Xw0aXpsog.woff2)
  format("woff2");
  unicode-range: U+0460-052F, U+1C80-1C88, U+20B4, U+2DE0-2DFF, U+A640-A69F,
  U+FE2E-FE2F;
}
/* cyrillic */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 100;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCtr6Xw9aXpsog.woff2)
  format("woff2");
  unicode-range: U+0400-045F, U+0490-0491, U+04B0-04B1, U+2116;
}
/* vietnamese */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 100;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCtr6Xw2aXpsog.woff2)
  format("woff2");
  unicode-range: U+0102-0103, U+0110-0111, U+0128-0129, U+0168-0169, U+01A0-01A1,
  U+01AF-01B0, U+1EA0-1EF9, U+20AB;
}
/* latin-ext */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 100;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCtr6Xw3aXpsog.woff2)
  format("woff2");
  unicode-range: U+0100-024F, U+0259, U+1E00-1EFF, U+2020, U+20A0-20AB,
  U+20AD-20CF, U+2113, U+2C60-2C7F, U+A720-A7FF;
}
/* latin */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 100;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCtr6Xw5aXo.woff2)
  format("woff2");
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA,
  U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215,
  U+FEFF, U+FFFD;
}
/* cyrillic-ext */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 200;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCvr6Hw0aXpsog.woff2)
  format("woff2");
  unicode-range: U+0460-052F, U+1C80-1C88, U+20B4, U+2DE0-2DFF, U+A640-A69F,
  U+FE2E-FE2F;
}
/* cyrillic */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 200;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCvr6Hw9aXpsog.woff2)
  format("woff2");
  unicode-range: U+0400-045F, U+0490-0491, U+04B0-04B1, U+2116;
}
/* vietnamese */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 200;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCvr6Hw2aXpsog.woff2)
  format("woff2");
  unicode-range: U+0102-0103, U+0110-0111, U+0128-0129, U+0168-0169, U+01A0-01A1,
  U+01AF-01B0, U+1EA0-1EF9, U+20AB;
}
/* latin-ext */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 200;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCvr6Hw3aXpsog.woff2)
  format("woff2");
  unicode-range: U+0100-024F, U+0259, U+1E00-1EFF, U+2020, U+20A0-20AB,
  U+20AD-20CF, U+2113, U+2C60-2C7F, U+A720-A7FF;
}
/* latin */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 200;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCvr6Hw5aXo.woff2)
  format("woff2");
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA,
  U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215,
  U+FEFF, U+FFFD;
}
/* cyrillic-ext */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 300;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCs16Hw0aXpsog.woff2)
  format("woff2");
  unicode-range: U+0460-052F, U+1C80-1C88, U+20B4, U+2DE0-2DFF, U+A640-A69F,
  U+FE2E-FE2F;
}
/* cyrillic */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 300;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCs16Hw9aXpsog.woff2)
  format("woff2");
  unicode-range: U+0400-045F, U+0490-0491, U+04B0-04B1, U+2116;
}
/* vietnamese */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 300;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCs16Hw2aXpsog.woff2)
  format("woff2");
  unicode-range: U+0102-0103, U+0110-0111, U+0128-0129, U+0168-0169, U+01A0-01A1,
  U+01AF-01B0, U+1EA0-1EF9, U+20AB;
}
/* latin-ext */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 300;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCs16Hw3aXpsog.woff2)
  format("woff2");
  unicode-range: U+0100-024F, U+0259, U+1E00-1EFF, U+2020, U+20A0-20AB,
  U+20AD-20CF, U+2113, U+2C60-2C7F, U+A720-A7FF;
}
/* latin */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 300;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCs16Hw5aXo.woff2)
  format("woff2");
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA,
  U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215,
  U+FEFF, U+FFFD;
}
/* cyrillic-ext */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 400;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCtr6Hw0aXpsog.woff2)
  format("woff2");
  unicode-range: U+0460-052F, U+1C80-1C88, U+20B4, U+2DE0-2DFF, U+A640-A69F,
  U+FE2E-FE2F;
}
/* cyrillic */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 400;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCtr6Hw9aXpsog.woff2)
  format("woff2");
  unicode-range: U+0400-045F, U+0490-0491, U+04B0-04B1, U+2116;
}
/* vietnamese */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 400;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCtr6Hw2aXpsog.woff2)
  format("woff2");
  unicode-range: U+0102-0103, U+0110-0111, U+0128-0129, U+0168-0169, U+01A0-01A1,
  U+01AF-01B0, U+1EA0-1EF9, U+20AB;
}
/* latin-ext */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 400;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCtr6Hw3aXpsog.woff2)
  format("woff2");
  unicode-range: U+0100-024F, U+0259, U+1E00-1EFF, U+2020, U+20A0-20AB,
  U+20AD-20CF, U+2113, U+2C60-2C7F, U+A720-A7FF;
}
/* latin */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 400;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCtr6Hw5aXo.woff2)
  format("woff2");
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA,
  U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215,
  U+FEFF, U+FFFD;
}
/* cyrillic-ext */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 500;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCtZ6Hw0aXpsog.woff2)
  format("woff2");
  unicode-range: U+0460-052F, U+1C80-1C88, U+20B4, U+2DE0-2DFF, U+A640-A69F,
  U+FE2E-FE2F;
}
/* cyrillic */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 500;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCtZ6Hw9aXpsog.woff2)
  format("woff2");
  unicode-range: U+0400-045F, U+0490-0491, U+04B0-04B1, U+2116;
}
/* vietnamese */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 500;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCtZ6Hw2aXpsog.woff2)
  format("woff2");
  unicode-range: U+0102-0103, U+0110-0111, U+0128-0129, U+0168-0169, U+01A0-01A1,
  U+01AF-01B0, U+1EA0-1EF9, U+20AB;
}
/* latin-ext */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 500;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCtZ6Hw3aXpsog.woff2)
  format("woff2");
  unicode-range: U+0100-024F, U+0259, U+1E00-1EFF, U+2020, U+20A0-20AB,
  U+20AD-20CF, U+2113, U+2C60-2C7F, U+A720-A7FF;
}
/* latin */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 500;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCtZ6Hw5aXo.woff2)
  format("woff2");
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA,
  U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215,
  U+FEFF, U+FFFD;
}
/* cyrillic-ext */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 600;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCu173w0aXpsog.woff2)
  format("woff2");
  unicode-range: U+0460-052F, U+1C80-1C88, U+20B4, U+2DE0-2DFF, U+A640-A69F,
  U+FE2E-FE2F;
}
/* cyrillic */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 600;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCu173w9aXpsog.woff2)
  format("woff2");
  unicode-range: U+0400-045F, U+0490-0491, U+04B0-04B1, U+2116;
}
/* vietnamese */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 600;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCu173w2aXpsog.woff2)
  format("woff2");
  unicode-range: U+0102-0103, U+0110-0111, U+0128-0129, U+0168-0169, U+01A0-01A1,
  U+01AF-01B0, U+1EA0-1EF9, U+20AB;
}
/* latin-ext */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 600;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCu173w3aXpsog.woff2)
  format("woff2");
  unicode-range: U+0100-024F, U+0259, U+1E00-1EFF, U+2020, U+20A0-20AB,
  U+20AD-20CF, U+2113, U+2C60-2C7F, U+A720-A7FF;
}
/* latin */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 600;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCu173w5aXo.woff2)
  format("woff2");
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA,
  U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215,
  U+FEFF, U+FFFD;
}
/* cyrillic-ext */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 700;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCuM73w0aXpsog.woff2)
  format("woff2");
  unicode-range: U+0460-052F, U+1C80-1C88, U+20B4, U+2DE0-2DFF, U+A640-A69F,
  U+FE2E-FE2F;
}
/* cyrillic */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 700;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCuM73w9aXpsog.woff2)
  format("woff2");
  unicode-range: U+0400-045F, U+0490-0491, U+04B0-04B1, U+2116;
}
/* vietnamese */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 700;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCuM73w2aXpsog.woff2)
  format("woff2");
  unicode-range: U+0102-0103, U+0110-0111, U+0128-0129, U+0168-0169, U+01A0-01A1,
  U+01AF-01B0, U+1EA0-1EF9, U+20AB;
}
/* latin-ext */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 700;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCuM73w3aXpsog.woff2)
  format("woff2");
  unicode-range: U+0100-024F, U+0259, U+1E00-1EFF, U+2020, U+20A0-20AB,
  U+20AD-20CF, U+2113, U+2C60-2C7F, U+A720-A7FF;
}
/* latin */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 700;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCuM73w5aXo.woff2)
  format("woff2");
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA,
  U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215,
  U+FEFF, U+FFFD;
}
/* cyrillic-ext */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 800;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCvr73w0aXpsog.woff2)
  format("woff2");
  unicode-range: U+0460-052F, U+1C80-1C88, U+20B4, U+2DE0-2DFF, U+A640-A69F,
  U+FE2E-FE2F;
}
/* cyrillic */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 800;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCvr73w9aXpsog.woff2)
  format("woff2");
  unicode-range: U+0400-045F, U+0490-0491, U+04B0-04B1, U+2116;
}
/* vietnamese */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 800;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCvr73w2aXpsog.woff2)
  format("woff2");
  unicode-range: U+0102-0103, U+0110-0111, U+0128-0129, U+0168-0169, U+01A0-01A1,
  U+01AF-01B0, U+1EA0-1EF9, U+20AB;
}
/* latin-ext */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 800;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCvr73w3aXpsog.woff2)
  format("woff2");
  unicode-range: U+0100-024F, U+0259, U+1E00-1EFF, U+2020, U+20A0-20AB,
  U+20AD-20CF, U+2113, U+2C60-2C7F, U+A720-A7FF;
}
/* latin */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 800;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCvr73w5aXo.woff2)
  format("woff2");
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA,
  U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215,
  U+FEFF, U+FFFD;
}
/* cyrillic-ext */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 900;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCvC73w0aXpsog.woff2)
  format("woff2");
  unicode-range: U+0460-052F, U+1C80-1C88, U+20B4, U+2DE0-2DFF, U+A640-A69F,
  U+FE2E-FE2F;
}
/* cyrillic */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 900;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCvC73w9aXpsog.woff2)
  format("woff2");
  unicode-range: U+0400-045F, U+0490-0491, U+04B0-04B1, U+2116;
}
/* vietnamese */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 900;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCvC73w2aXpsog.woff2)
  format("woff2");
  unicode-range: U+0102-0103, U+0110-0111, U+0128-0129, U+0168-0169, U+01A0-01A1,
  U+01AF-01B0, U+1EA0-1EF9, U+20AB;
}
/* latin-ext */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 900;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCvC73w3aXpsog.woff2)
  format("woff2");
  unicode-range: U+0100-024F, U+0259, U+1E00-1EFF, U+2020, U+20A0-20AB,
  U+20AD-20CF, U+2113, U+2C60-2C7F, U+A720-A7FF;
}
/* latin */
@font-face {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 900;
  font-display: swap;
  src: url(https://fonts.gstatic.com/s/montserrat/v23/JTUHjIg1_i6t8kCHKm4532VJOt5-QNFgpCvC73w5aXo.woff2)
  format("woff2");
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA,
  U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215,
  U+FEFF, U+FFFD;
}
* {
  margin: 0;
  padding: 0;
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
  content: "";
  top: -8px;
}

.menu__btn > span::after {
  content: "";
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
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 500;
  font-size: 19px;
  line-height: 115%;
  /* identical to box height, or 22px */
  letter-spacing: -0.045em;
  color: #ffffff;
}

.menu__btn > span,
.menu__btn > span::before,
.menu__btn > span::after {
  display: block;
  position: absolute;
  width: 100%;
  height: 2px;
  background-color: #616161;
  transition-duration: 0.25s;
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
  transition-duration: 0.25s;
}

.menu__item {
  display: block;
  padding: 12px 24px;
  color: #ffffff;
  font-family: "Roboto", sans-serif;
  font-size: 20px;
  font-weight: 600;
  text-decoration: none;
  transition-duration: 0.25s;
  transition-duration-font-family: "Montserrat";
  transition-duration-font-style: normal;
  transition-duration-font-weight: 500;
  transition-duration-font-size: 19px;
  transition-duration-line-height: 115%;
  /* identical to box height, or 22px */
  transition-duration-letter-spacing: -0.045em;
  transition-duration-color: #ffffff;
}

.menu__item:hover {
  background-color: #1e1e30;
}

.hamburger-menu {
  display: none;
}

body {
  overflow-x: hidden;
  background-color: #33334b;
  background-size: cover;
  background-repeat: no-repeat;
  height: 100%;
}

*::-webkit-scrollbar {
  width: 5px;
}

*::-webkit-scrollbar-track {
  background: #383838;
}

*::-webkit-scrollbar-thumb {
  background: #757575;
}

.app {
  background-color: transparent;
  background-size: cover;
  background-repeat: no-repeat;
  width: 100vw;
  height: 100%;
}

.main {
  width: 100vw;
  position: absolute;
}

.main .container {
  position: relative;
  vertical-align: middle;
  margin: 0 auto;
  padding: 0;
  width: 457px;
  height: 459px;
  margin-top: 200px;
  background: #292941;
  box-shadow: 0px 10px 30px -10px rgba(0, 0, 0, 0.42);
  border-radius: 9px;
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
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 700;
  font-size: 21px;
  line-height: 115%;
  /* or 24px */
  letter-spacing: -0.045em;
  color: #ffffff;
}

.main .buttons button {
  border: none;
  width: 250px;
  height: 64.91px;
  cursor: pointer;
  background: linear-gradient(90deg, #ff005b 0%, #662d8c 100%);
  box-shadow: 0px 10px 30px 4px rgba(208, 0, 255, 0.082),
  inset 0px 0px 0px 1px rgba(255, 255, 255, 0.24);
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
  box-shadow: 0px 10px 30px 4px rgba(207, 0, 255, 0.5),
  inset 0px 0px 0px 1px rgba(255, 255, 255, 0.24);
}

.main .buttons .searchButton {
  width: 188.03px;
  height: 64.91px;
  margin-left: 40px;
  background: linear-gradient(90deg, #2b0950 0%, #411273 100%);
  box-shadow: 0px 10px 30px 4px rgba(208, 0, 255, 0.192),
  inset 0px 2px 6px #ff005b;
  border-radius: 88px;
}

.main .buttons .searchButton:hover {
  box-shadow: 0px 10px 30px 4px rgba(207, 0, 255, 0.5),
  inset 0px 2px 6px #ff005b;
}

.nav {
  padding: 37px 100px 0px 100px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.nav .buttons {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.nav .buttons a {
  padding: 0px 60px;
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 700;
  font-size: 19px;
  line-height: 115%;
  /* identical to box height, or 22px */
  text-decoration: none;
  letter-spacing: -0.045em;
  color: #ffffff;
}

.nav .buttons .profile {
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

.nav .buttons .profile img {
  padding-left: 14px;
}

.nav .buttons .profile span {
  font-family: "Montserrat";
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

.navButtons {
  width: 100%;
  padding: 35px 44px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.navButtons a {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 600;
  font-size: 24px;
  line-height: 115%;
  /* identical to box height, or 28px */
  letter-spacing: -0.045em;
  cursor: pointer;
  color: #71708c;
}

.navButtons a:nth-last-child(1) {
  margin-left: 24px;
}

.navButtons .active {
  color: #fbfcff;
}

.inputs {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px 44px;
}

.inputs input {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 400;
  font-size: 19px;
  line-height: 115%;
  /* identical to box height, or 22px */
  letter-spacing: -0.045em;
  color: #7a7993;
  border: none;
  background: #33314a;
  border-radius: 9px;
  width: 80%;
  height: 38px;
  color: white;
  padding: 0 29px;
}

.inputs input:focus {
  border: none;
  text-decoration: none;
  outline: none;
}

.inputs input::placeholder {
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 400;
  font-size: 19px;
  line-height: 115%;
  /* identical to box height, or 22px */
  letter-spacing: -0.045em;
  color: #7a7993;
}

.buttonSend {
  margin: 35px 44px;
  width: 141px;
  height: 45px;
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(90deg, #fb5915 0%, #d93c98 100%);
  cursor: pointer;
  border-radius: 88px;
  font-family: "Montserrat";
  font-style: normal;
  font-weight: 700;
  font-size: 21px;
  line-height: 115%;
  /* or 24px */
  text-align: center;
  letter-spacing: -0.045em;
  align-self: flex-end;
  color: #ffffff;
}
.reg{
  width: 300px;
}
.buttonSend:hover {
  box-shadow: 0px 10px 30px -10px #e94a5b;
}

.main .container {
  display: flex;
  justify-content: space-between;
  flex-direction: column;
}

@media screen and (max-width: 1079px) {
  .container {
    padding: 0px 10px 0px 10px !important;
  }
  .hamburger-menu {
    top: 0;
    display: block;
  }
  .nav {
    display: none;
  }
}

@media screen and (max-width: 952px) {
  .container {
    margin-top: 20px;
  }
  .container h1 {
    font-size: 66px;
  }
}

@media screen and (max-width: 740px) {
  body {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .container {
    margin-top: 20px;
  }
  .container h1 {
    font-size: 56px;
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
  .main .container p {
    font-size: 15px !important;
    word-break: break-word;
  }
}

@media screen and (max-width: 950px) {
  /* body {
    height: 1000px;
  } */
}

@media screen and (max-width: 687px) {
  .video2 {
    height: 90vw !important;
  }
}

@media screen and (max-width: 687px) {
  .container {
    width: 80vw !important;
  }
  .buttonSend {
    align-self: center !important;
  }
  .inputs {
    padding: 15px 1% !important;
  }
  .inputs input {
    width: 90% !important;
  }
}
.nav {
  box-shadow: none !important;
}
@media screen and (max-width: 448px) {
  .container {
    width: 80vw !important;
  }
  .navButtons,
  .inputs {
    padding: 20px 10px;
  }
  .buttonSend {
    margin: 25px 10px;
    align-self: center;
    margin: 0 auto;
    width: 90%;
  }
}

@media screen and (max-width: 448px) {
  .container {
    width: 80vw !important;
  }
  .navButtons a {
    font-size: 18px !important;
  }
  .navButtons,
  .inputs {
    padding: 20px 10px;
  }
  .buttonSend {
    margin: 20px 10px;
  }
}
/*# sourceMappingURL=main.css.map */
</style>

<script>
const HOST = process.env.HOST;
import { Notyf } from "notyf";
import "notyf/notyf.min.css";
const notyf = new Notyf({
  position: { x: "center", y: "top" },
  duration: 4000,
  dismissible: true,
});

import "animate.css";
import { log } from "aframe";
const host = "//127.0.0.1:8000/api/";
export default {
  layout: "empty",
  head() {
    return {
      script: [
        {
          src: "assets/js/site.js",
        },
      ],
    };
  },
  data: () => ({
    form: "auth",
    select: null,
    token: "",
    classauth: "active",
    classregister: "",
    user: "",
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
  }),

  methods: {
    switchto(data) {
      if (data != "auth") {
        this.loginForm.email == "";
        this.loginForm.password == "";
        this.classauth = "";
        this.classregister = "active";
        this.form = "register";
      } else {
        // this.loginForm.email == ''
        // this.loginForm.password == ''
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
                    path: "/lk",
                  });
                  window.location.href='/lk'
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
                    path: "/lk",
                  });
                  window.location.href='/lk'
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
    // Вывод ошибок Notyf
    errorNotyf(data) {
      for (let i = 0; i < Object.keys(data.message).length; i++) {
        let value = Object.values(data.message)[i];
        notyf.error(value[0]);
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
  &-buttons {
    margin-top: 50px;
  }
}
</style>
