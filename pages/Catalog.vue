<template>
<div id="app">
      <button @click='sort'></button>
                <button @click='sortPlus'></button>
                <button @click='sortName'></button>
  <div id='container'>
       <div class="wrapper" 
               v-for="(item, index) in list" :key="index"
    >           
                <div class="img" > {{item.href}} </div>
                <div class="title"> {{ item.title }} </div>
                <div class="text">{{item.text}} </div>
                <div class="price"> {{item.price}} руб. </div>
                <br>
                <button @click="deleteFromList(index)">Delete</button>
          </div>
   
  </div>
        <div id="validation-container">
            <form @submit.prevent="submitForm" >

           <input class="input-title" v-model.trim="title" placeholder="Наименование"> <br> <br> <br>
            <p v-if="errorsTitle.length">
            <b>Пожалуйста исправьте указанные ошибки:</b>
           </p>
           <input class="input-text" v-model.trim="text" placeholder="Текст"> <br> <br> <br>
           <p v-if="errorsText.length">
            <b>Пожалуйста исправьте указанные ошибки:</b>
           </p>
           <input class="input-price" v-model.trim="price" placeholder="Цена"> <br> <br> <br>
           <p v-if="errorsPrice.length">
            <b>Пожалуйста исправьте указанные ошибки:</b>
           </p>
           <input class="input-href" v-model.trim='href' placeholder="href">    <br> <br> <br>
           <button @click='getName'
                    :class="[this.text && this.title && this.price ? 'nov' : 'koe']"
           ></button>
            </form>
        </div>
</div>
</template>

<script>
import ValidForma from './ValidForma.vue'

export default {

components: {
    ValidForma
  },
  data() {
    return {
      list: [
           {text:'Текст', title:'a', price: 1000, href:'href'},
           {text:'Текст', title:'c', price: 1200, href:'href'}, 
           {text:'Текст', title:'b', price: 1300, href:'href'}
          
          ],
            errorsTitle: [],
            errorsText: [],
            errorsPrice: [],
            text : '',
            title : '',
            price : '',
            href : '',
            
     
    };
  },
  
  methods: {
    deleteFromList(index) {
      this.list.splice(index, 1);
    }, 
          sort() {
        this.list = this.list.sort(function(a, b) {return a.price - b.price})
        },
        sortPlus() {
        this.list = this.list.sort((a, b) =>b.price - a.price )
        },
        sortName() {
        this.list = this.list.sort(function(a, b){
    if(a.title < b.title) { return -1; }
    if(a.title > b.title) { return 1; }
    return 0;
})
        },
   
    
    getName() {
        
        },
   submitForm () {
       
       this.errorsTitle = []
             this.errorsText = []
             this.errorsPrice = []
      

        if (!this.text && !this.title && !this.price) {
            this.errorsText.push('0');
            this.errorsTitle.push('0');
            this.errorsPrice.push('0');
        }
        else if(!this.text && !this.title ) {
            this.errorsTitle.push('0');
            this.errorsText.push('0');
        }
        else if (!this.text && !this.price) {
            this.errorsPrice.push('0');
            this.errorsText.push('0');

        } else if (!this.price && !this.title){
            this.errorsPrice.push('0');
            this.errorsTitle.push('0');

        } else if(!this.price) {
            this.errorsPrice.push('0');
        }else if(!this.title) {
            this.errorsTitle.push('0');
        }
        else if(!this.text) {
            this.errorsText.push('0');
        }
        else {
            this.list.push({text:this.text, title:this.title, price:this.price, href:this.href})
             this.text = ''
             this.title = ''
             this.price = ''
             this.href = ''
        }
        setTimeout(() => {
             this.errorsText = []
              this.errorsTitle = []
               this.errorsPrice = []
        }, 3400)


          
   }

  }
};
</script>

<style lang="scss">

    #app{
        display: flex;
        flex-direction: row-reverse;

        #container{
        display: flex;
        flex-direction: row;
        width: 1000px;
        background: greenyellow;

        .wrapper{
            background: gold;
            width: 332px;
            height: 423px;
            margin: 20px;
            .img{
                width: 332px;
                height: 200px;
                background: gray;
            }
            .title{
                font-size: 20px;
                margin: 16px 0px;
            }
            .text{
                width: 300px;
                height: 80px;
                background: green;
                font-size: 16px;
            }    
            .price{
                font-size: 24px;
                margin-top: 32px;
            }
        }
    }
            #validation-container{
                width: 300px;
                height: 500px;
                background: lightcoral;
                .nov{
                    background: lightsalmon;
                    cursor: pointer;
                    border: none;
                    }
                .koe{
                    background: limegreen;
                    }
            }
    }
</style>