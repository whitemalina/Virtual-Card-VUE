<template>
    <div >
        <div class="open-card-wrap">
            <div class="container">
                <div class="open-card-content">
                    <div class="open-card-content-item">
                        <h3 class="open-card-title">На гаваях </h3>
                        <span class="open-card-author">Николай</span>
                    </div>
                    <div class="open-card-content-item">
                        <div class="open-card"><img src="../assets/image/share.svg" alt=""><span>Поделиться</span></div>
                    </div>
                    
                </div>
            </div>
          <div class="scene-block">
            <div class="scene">
                <div class="scene-qr">
                    <img src="../assets/image/qr.svg" alt="">
                </div>
                <button class="scene-button">Посмотреть</button>
            </div>
          </div>
            
        </div>
        <div class="container">
            <div class="simler">
                <h3 class="simler-title">Похожие</h3>
                <hr>
                <div class="cards">
                    <div class="card-wrapper">
                        <v-card :loading="loading" class="mx-auto my-12 list_card" max-width="298">
                            <template slot="progress">
                                <v-progress-linear color="deep-purple" height="10" indeterminate></v-progress-linear>
                            </template>
            
                            <v-img height="250" src="https://cdn.vuetifyjs.com/images/cards/cooking.png"></v-img>
                            <div class="card-content">
                                <v-card-title>Cafe Badilico</v-card-title>
                                <div class="like">
                                    <img src="../assets/image/like_none.svg" alt="">
                                    <span>245</span>
                                </div>
                                
                            </div>
                            <v-card-text>
                                <p class="card-author">Алексей</p>
                                <p class="card-category-text">#ДоброеУтро</p>
                            </v-card-text>
            
            
                        </v-card>
                     
            
            
            
                    </div>
                    <div class="card-wrapper">
                        <v-card :loading="loading" class="mx-auto my-12 list_card" max-width="298">
                            <template slot="progress">
                                <v-progress-linear color="deep-purple" height="10" indeterminate></v-progress-linear>
                            </template>
            
                            <v-img height="250" src="https://cdn.vuetifyjs.com/images/cards/cooking.png"></v-img>
                            <div class="card-content">
                                <v-card-title>Cafe Badilico</v-card-title>
                                <div class="like">
                                    <img src="../assets/image/like_none.svg" alt="">
                                    <span>245</span>
                                </div>
                                
                            </div>
                            <v-card-text>
                                <p class="card-author">Алексей</p>
                                <p class="card-category-text">#ДоброеУтро</p>
                            </v-card-text>
            
            
                        </v-card>
                     
            
            
            
                    </div>
                    <div class="card-wrapper">
                        <v-card :loading="loading" class="mx-auto my-12 list_card" max-width="298">
                            <template slot="progress">
                                <v-progress-linear color="deep-purple" height="10" indeterminate></v-progress-linear>
                            </template>
            
                            <v-img height="250" src="https://cdn.vuetifyjs.com/images/cards/cooking.png"></v-img>
                            <div class="card-content">
                                <v-card-title>Cafe Badilico</v-card-title>
                                <div class="like">
                                    <img src="../assets/image/like_none.svg" alt="">
                                    <span>245</span>
                                </div>
                                
                            </div>
                            <v-card-text>
                                <p class="card-author">Алексей</p>
                                <p class="card-category-text">#ДоброеУтро</p>
                            </v-card-text>
            
            
                        </v-card>
                     
            
            
            
                    </div>
                    <div class="card-wrapper">
                        <v-card :loading="loading" class="mx-auto my-12 list_card" max-width="298">
                            <template slot="progress">
                                <v-progress-linear color="deep-purple" height="10" indeterminate></v-progress-linear>
                            </template>
            
                            <v-img height="250" src="https://cdn.vuetifyjs.com/images/cards/cooking.png"></v-img>
                            <div class="card-content">
                                <v-card-title>Cafe Badilico</v-card-title>
                                <div class="like">
                                    <img src="../assets/image/like_none.svg" alt="">
                                    <span>245</span>
                                </div>
                                
                            </div>
                            <v-card-text>
                                <p class="card-author">Алексей</p>
                                <p class="card-category-text">#ДоброеУтро</p>
                            </v-card-text>
            
            
                        </v-card>
                     
            
            
            
                    </div>
                    <div class="card-wrapper">
                        <v-card :loading="loading" class="mx-auto my-12 list_card" max-width="298">
                            <template slot="progress">
                                <v-progress-linear color="deep-purple" height="10" indeterminate></v-progress-linear>
                            </template>
            
                            <v-img height="250" src="https://cdn.vuetifyjs.com/images/cards/cooking.png"></v-img>
                            <div class="card-content">
                                <v-card-title>Cafe Badilico</v-card-title>
                                <div class="like">
                                    <img src="../assets/image/like_none.svg" alt="">
                                    <span>245</span>
                                </div>
                                
                            </div>
                            <v-card-text>
                                <p class="card-author">Алексей</p>
                                <p class="card-category-text">#ДоброеУтро</p>
                            </v-card-text>
            
            
                        </v-card>
                     
            
            
            
                    </div>
                    <div class="card-wrapper">
                        <v-card :loading="loading" class="mx-auto my-12 list_card" max-width="298">
                            <template slot="progress">
                                <v-progress-linear color="deep-purple" height="10" indeterminate></v-progress-linear>
                            </template>
            
                            <v-img height="250" src="https://cdn.vuetifyjs.com/images/cards/cooking.png"></v-img>
                            <div class="card-content">
                                <v-card-title>Cafe Badilico</v-card-title>
                                <div class="like">
                                    <img src="../assets/image/like_none.svg" alt="">
                                    <span>245</span>
                                </div>
                                
                            </div>
                            <v-card-text>
                                <p class="card-author">Алексей</p>
                                <p class="card-category-text">#ДоброеУтро</p>
                            </v-card-text>
            
            
                        </v-card>
                     
            
            
            
                    </div>
                    <div class="card-wrapper">
                        <v-card :loading="loading" class="mx-auto my-12 list_card" max-width="298">
                            <template slot="progress">
                                <v-progress-linear color="deep-purple" height="10" indeterminate></v-progress-linear>
                            </template>
            
                            <v-img height="250" src="https://cdn.vuetifyjs.com/images/cards/cooking.png"></v-img>
                            <div class="card-content">
                                <v-card-title>Cafe Badilico</v-card-title>
                                <div class="like">
                                    <img src="../assets/image/like_none.svg" alt="">
                                    <span>245</span>
                                </div>
                                
                            </div>
                            <v-card-text>
                                <p class="card-author">Алексей</p>
                                <p class="card-category-text">#ДоброеУтро</p>
                            </v-card-text>
            
            
                        </v-card>
                     
            
            
            
                    </div>
                    <div class="card-wrapper">
                        <v-card :loading="loading" class="mx-auto my-12 list_card" max-width="298">
                            <template slot="progress">
                                <v-progress-linear color="deep-purple" height="10" indeterminate></v-progress-linear>
                            </template>
            
                            <v-img height="250" src="https://cdn.vuetifyjs.com/images/cards/cooking.png"></v-img>
                            <div class="card-content">
                                <v-card-title>Cafe Badilico</v-card-title>
                                <div class="like">
                                    <img src="../assets/image/like_none.svg" alt="">
                                    <span>245</span>
                                </div>
                                
                            </div>
                            <v-card-text>
                                <p class="card-author">Алексей</p>
                                <p class="card-category-text">#ДоброеУтро</p>
                            </v-card-text>
            
            
                        </v-card>
                     
            
            
            
                    </div>
                    <div class="card-wrapper">
                        <v-card :loading="loading" class="mx-auto my-12 list_card" max-width="298">
                            <template slot="progress">
                                <v-progress-linear color="deep-purple" height="10" indeterminate></v-progress-linear>
                            </template>
            
                            <v-img height="250" src="https://cdn.vuetifyjs.com/images/cards/cooking.png"></v-img>
                            <div class="card-content">
                                <v-card-title>Cafe Badilico</v-card-title>
                                <div class="like">
                                    <img src="../assets/image/like_none.svg" alt="">
                                    <span>245</span>
                                </div>
                                
                            </div>
                            <v-card-text>
                                <p class="card-author">Алексей</p>
                                <p class="card-category-text">#ДоброеУтро</p>
                            </v-card-text>
            
            
                        </v-card>
                     
            
            
            
                    </div>
        
                </div>
            </div>
        </div>
    </div>
    
</template>


<style lang="SCSS">
    .open-card{
        
        &-content{
            margin-bottom: 10px;
            display: flex;
            margin-top: 40px;
            justify-content: space-between;
            &-item{
                display: flex;
                flex-direction: column;
               
                &:last-child{
                    justify-content: end;
                }
            }
        }
        &-title{
            font-weight: 500;
            font-size: 36px;
            line-height: 42px;
            margin-bottom: 6px;
            display: flex;
            align-items: center;
            text-align: center;
    }
    }
    .scene{
        position: relative;
        background: url('../assets/image/scene.png') no-repeat;
        background-size: cover;
        border-radius: 50px;
        margin-bottom: 157px;
        
        height: 576px;
        &-block{
            padding: 0 120px;
        }
        &-button{
            position: absolute;
            left:0;
            right: 0;
            bottom: 0;
            margin: 0 auto;
           
            transform: translateY(50%);
            padding: 16px 24px;
            border-radius: 50px ;
            color: white;
            background-color:#037DD6;
        }
        &-qr{
            position: absolute;
            top: 50%;
            left: 10%;
            transform: translateY(-50%);
            padding: 36px 32px;
            background: rgba(255, 255, 255, 0.7);
            mix-blend-mode: normal;
            backdrop-filter: blur(7px);
            width: min-content;
            border-radius: 32px;
        }
    }
    .card-wrapper {
       
       border-radius: 10px;
       width: 300px;
       min-height: 350px;
   }
   .simler{
    &-title{
        font-weight: 500;
        font-size: 36px;
        line-height: 42px;
        margin-bottom: 20px;
    }
    hr{
        border: 1px solid #E9EBEE;
        margin-bottom: 64px;
    }
   }
   select{
       appearance: auto;
   }
.like{
   display: flex;
   align-items: center;
   justify-content: center;
   flex-direction: column;
   img{
       margin-bottom: 5px;
       margin-top: 5px;
   }
}
.cards{
   display: flex;
   flex-wrap: wrap;
   margin-bottom: 120px;
}
   
.select {
 width: 100%;
 min-width: 15ch;
 max-width: 30ch;
 border: 1px solid var(--select-border);
 border-radius: 0.25em;
 padding: 0.25em 0.5em;
 font-size: 1.25rem;
 cursor: pointer;
 line-height: 1.1;
 background-color: #fff;
 background-image: linear-gradient(to top, #f9f9f9, #fff 33%);
}
   
:root {
 --select-border: #777;
 --select-focus: blue;
 --select-arrow: var(--select-border);
}
   .list_card{
       margin-right: 20px;
       margin-bottom: 20px;
   }

   .card {
       &-card {
           display: flex;
           flex-direction: column;

           img {
               width: 100%;
               border: 10px 10px 0 0;
           }
       }

       &-image {
           img {
               border-radius: 10px 10px 0 0;
           }
       }

       &-category {
           margin-top: 30px;
           margin-bottom: 25px;
           border-radius: 50px;
           padding: 13px 20px;
           font-weight: normal;
           width: 25%;
           box-shadow: 0px 0px 4px rgba(0, 0, 0, 0.25);
           &-text{
               font-size: 14px;
               line-height: 19px;
               font-style: italic;
           }
           select{
               width: 100%;
           }
           font-size: 14px;
           line-height: 19px;
       }

       &-title {
           font-style: normal;
           font-weight: 600;
           font-size: 14px;
           line-height: 19px;
       }

       &-description {
           display: flex;
           justify-content: space-between;
           align-items: flex-end;
           height: 100%;
       }

       &-info {
           display: flex;
           height: 100%;
           flex-direction: column;
           justify-content: space-between;
           align-items: center;
       }

       &-wrapper {
           display: flex;
           flex-wrap: wrap;
       }

       &-content {
           display: flex;
           justify-content: space-between;
           align-items: flex-start;
           padding: 0 10px;
           padding-top: 10px;
           
       }
   }

   .v-card__subtitle,
   .v-card__text,
   .v-card__title {
       padding: 5px;
   }

   .v-card__text{
       margin-top: 15px;
       display: flex;
       justify-content: space-between;
       padding: 0 10px;
   }

   .card-description {
       padding: 10px 20px;
   }

   .v-sheet.v-card {
       border-radius: 10px;
   }
   .v-card__title{
       padding: 0;
   }

   .card-wrapper {
       border-radius: 10px;
       width: min-content;
   }
   @media screen and (min-width: 1264px){
       .container{
           max-width: 1350px;
       }
       
   }

   @media screen and (max-width: 1260px){
       .cards{
           justify-content: center;
       }
       
   }
</style>

<script>
    export default {
        layout: "mainLayout",
        mounted() {

        },
        data() {
            return {

            };
        },
    };
</script>