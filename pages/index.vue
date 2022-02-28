
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


   <div class="container">
      <div class="welcome-wrapper">
            <div class="welcome-content animate__animated animate__backInLeft">
              <h1 class="welcome-title ">
                Виртуальные <br />
                Открытки
              </h1>
              <p class="welcome-text">
                Здесь вы найдёте уникальные виртуальные открытки<br />
                для друзей и знакомых<br />
                Создавайте собственные вирутальные открытки<br />
                Делитесь ими <br />
              </p>
              <NuxtLink to="/signin">
                <button v-if="this.token == '' " class="btn welcome-btn">Генерировать</button>
              </NuxtLink>
              <button v-if="this.token !== '' "  @click="dialog2 = !dialog2" class="btn welcome-btn">Генерировать</button>
              <!-- <a href="/signin"></a> -->
            </div>
            <div class="welcome-Aframe animate__animated animate__backInRight" style="overflow: hidden;">
              <iframe height="100%" src="http://localhost:3000/card/Q9VkEVl" style="width: calc(100% + 20px)"  class="overflow-hidden" frameborder="0"></iframe>  
            </div>   
        </div>
   </div>

  </v-main>
</template>


<style lang="scss" >
@media (min-width: 1904px){
  .container {
      max-width: none;
  }
}
@media (min-width: 1264px){
  .container {
      max-width: none;
  }
}
@media (max-width: 1342px){
  .container {
      max-width: none;
  }
  .welcome {
    &-content{
      max-width: 50%;
    }
    &-Aframe{
      width: 400px !important;
    }
    &-title{
      font-size: 60px !important;
    }
    &-text{
      font-size: 20px !important;
    }
  }

}
@media (max-width: 873px){
  // .v-main__wrap{
  //   height: 200vh;
  // }
}
.welcome {
  .v-main__wrap{
    display: flex;
    align-items: center;
  }
  background: url("./assets/image/welcome-back.png") no-repeat;
  background-size: cover;
  height: 100vh;
  &-wrapper {
    color: white;
    width: 100%;
    justify-content: space-around;
    display: flex;
    flex-wrap: wrap;
    align-items: center;
  }
  
  &-content{
    border-radius: 25px !important;
    min-height: 458px !important;
    padding: 20px 40px 20px 40px;
  }

  &-btn {
    padding: 27px 65px;
    font-size: 1.5em;
    line-height: 28px;
    transition: all ease-in-out .2s;
    &:hover{
        transform: translateY(-10%);
    }
  }
  &-title {
    font-size: 72px;
    line-height: 84px;
    font-weight: bold;
    margin-bottom: 63px;
    color: #fbfbfb;
  }
  &-text {
    // font-weight: 500;
    margin-bottom: 87px;
    font-size: 24px;
    line-height: 28px;
  }
  &-Aframe{
    width: 624px;
    min-width: 400px;
    min-height: 458px;
    height: 715px;
    background-color: white;
    border-radius: 50px;
  }
}
</style>


<script>
const host = "https://68d3-178-46-180-106.ngrok.io/api/"
import 'animate.css';

export default {
  layout: "empty",
  mounted() {
    
  },
  data() {
    return {
      dialog: false,
      dialog2: false,
      dialog3: false,
      token: '',
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
    console.log(this.token);
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
