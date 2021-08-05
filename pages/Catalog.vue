<template>
<div id="app">
             <transition name="slide-fade">
                 <p v-show='trigger' class="complete"></p>
                 <p v-show='trigger' class="uncomplete"></p>
             </transition>
                 <div id="v-model-select" class="demo">
                    <select v-model="selected" @change='sort' >
                        <option disabled value="">По умолчанию</option>
                        <option value="a">PriceMin </option>
                        <option value="b"> PriceMax </option>
                        <option value="c"> Названию </option>
                    </select>
                 </div>
                 
  <div id='container'>
       <div class="wrapper" 
               v-for="(item, index) in list" :key="index">           
                <div class="img" ><img v-bind:src="href" > </div>
                <div class="title"> <strong>{{ item.title }}</strong> </div>
                <div class="text">{{item.text}} </div>
                <div class="price"> <strong>{{item.price}} руб. </strong></div>
                <br>
                <button class="bucket" @click="deleteFromList(index)">  </button>
    
          </div>
  </div>
        <div id="validation-container">

            <form @submit.prevent="submitForm" >

            <p class="validation-text">Наименование товара</p>
           <input class="input-title" style="white-space: pre-line" v-model.trim="title" placeholder="Введите Наименование">
            <p v-if="errorsTitle.length">
                <b>Это поле обязательное</b>
            </p>

             <p class="validation-text">Описание товара</p>
           <input class="input-text" v-model.trim="text" placeholder="Введите описание товара">
            <p v-if="errorsText.length">
                <b>Это поле обязательное</b>
           </p>
            <p class="validation-text">Ссылка на изображение товара</p>
           <input class="input-price" v-model.trim="href" placeholder="Введите ссылку">
          
             <p class="validation-text">Цена товара</p>
           <input class="input-href" v-model.trim='price' placeholder="Введите Цену">  
             <p v-if="errorsPrice.length">
                <b>Это поле обязательное</b>
            </p> 
                <button @click='getName'
                        :class="[this.text && this.title && this.price ? 'nov' : 'koe']"> Добавить товар
                </button>
            </form>
        </div>
                <h3>Добавление товара</h3>

<ValidForma/>
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
            {text:'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк', title:'Наименование товара', price: 1500, href:'./img/Rectangle 31.jpg'},
            {text:'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк', title:'a', price: 12000, href:'./img/Rectangle 31.jpg'}, 
            {text:'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк', title:'Наименование товара', price: 1300, href:'./img/Rectangle 31.jpg'},
            {text:'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк', title:'b', price: 13000, href:'./img/Rectangle 31.jpg'},
            {text:'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк', title:'Наименование товара', price: 7300, href:'href'},
            {text:'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк', title:'b', price: 100, href:'href'},
            {text:'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк', title:'Наименование товара', price: 300, href:'href'},
            {text:'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк', title:'b', price: 20000, href:'href'},
          
          ],
            errorsTitle: [],
            errorsText: [],
            errorsPrice: [],
            text : '',
            title : '',
            price : '',
            href : '',
            selected: '',
            trigger: '',
            
     
        
    };
  },
  
  methods: {
    deleteFromList(index) {
      this.list.splice(index, 1);
    }, 

    sort() {
          if(this.selected === 'a') {
               this.list = this.list.sort(function(a, b) {return a.price - b.price})
          }
          else if ( this.selected === 'b') {
               this.list = this.list.sort((a, b) =>b.price - a.price )
          } 
          else if (this.selected === 'c') {
                    this.list = this.list.sort(function(a, b){
                    if(a.title < b.title) { return -1; }
                    if(a.title > b.title) { return 1; }
                    return 0;})
          }
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
        }
         else if(!this.price) {
            this.errorsPrice.push('0');
        }
        else if(!this.title) {
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
             this.trigger = true
            setTimeout(() => {
                 this.trigger = false
            }, 1000)
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

<style  lang="scss" >
@import url('https://fonts.googleapis.com/css2?family=Source+Sans+Pro:wght@300;400&display=swap');
    *{
  padding: 0;
  margin: 0;
  border: 0;
  font-family: 'Source Sans Pro', sans-serif;
}
:focus, :active{outline: none;}
a:focus, a:active{outline: none;}
nav, footer, header, aside{display: block;}
    #app{
         display: flex;
 flex-direction: row-reverse;
 float: left;
        margin: 100px 40px 0px 40px;

            #v-model-select{
                position: absolute;
                top: 30px;
                left: 1285px;
                width: 121px;
                height: 36px;
                display: flex;
                flex-direction: column;
                align-items: center;
                justify-content: center;
                background: #FFFEFB;
                box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
                border-radius: 4px;
                transition: 1s;
                   @media only screen and (max-width: 767px) {
                       top: 10px;
                       left: 100px;
                    }
                    @media only screen and (max-width: 576px) {
                    }

                
            }
        .complete{
            position: absolute;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            background: rgba(165, 255, 157, 0.363);
        }
        
        #container{
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        width: 1048px;
        background: rgb(255, 255, 255);
        transition: 1s;
        
        @media only screen and (max-width: 967px) {
        width: 700px;

            }
            @media only screen and (max-width: 776px) {
                width: 308px;
                    }



        .wrapper{
            background: #FFFEFB;
            box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
            border-radius: 4px;
            width: 332px;
            height: 423px;
            margin: 8px;
            position: relative;
            top: -25px;
            left: 250px;
            transition: 1s;
            @media only screen and (max-width: 767px) {
            top:580px;
            left: 0;

            }
            @media only screen and (max-width: 576px) {
            width: 305px;
            left: -50px;
            top: 490px;
            margin: 0;
            
            }
            .img{
                width: 332px;
                height: 200px;
                background: gray;
                border-radius: 4px;
            }
            .title{
                font-size: 20px;
                margin: 16px 0 16px 16px;
            }
            .text{
                width: 300px;
                height: 80px;
                background: rgba(0, 128, 0, 0);
                font-size: 16px;
                margin: 0 0 0 16px;
            }    
            .price{
                font-size: 24px;
                margin-top: 32px;
                margin-left: 16px;
            }
            .bucket{
                background: orangered;
                width: 45px;
                height: 45px;
                position: relative;
                top: -430px;
                left: 295px;
                border-radius: 10px;
                 background: url('./img/bucket.svg') 0px center/auto 120% no-repeat;


            }
        }
    }
            #validation-container{
                background: #ffffff;
                box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
                border-radius: 4px;
                width: 332px;
                height: 440px;
                left: 32px;
                top: 83px;
                margin: 0 8px 0 0;
                position: fixed;
                transition: 1s;
                ::-webkit-input-placeholder {color:#5a5a5a;padding: 0 0 0 10px;}
                   @media only screen and (max-width: 767px) {
                       top:100px;
                       left: 50px;
                       position: absolute;
                    }
                    @media only screen and (max-width: 576px) {
                    }
         
                .nov{
                    width: 284px;
                    height: 36px;
                    margin: 24px 0 0 24px;
                    transition: 0.5s;
                    background: #68ff68ad;
                    border-radius: 10px;
                    cursor: pointer;
                    font-size: 12px;
                    }
                .koe{
                  
                    width: 284px;
                    height: 36px;
                    margin: 24px 0 0 24px;
                    transition: 0.5s;
                    background: #EEEEEE;
                    border-radius: 10px;
                    font-size: 12px;
                    color: rgba(2, 2, 2, 0.548);
                    
                    }
                .validation-text{
                    font-size:10px;
                    margin: 16px 0 4px 24px;
                    padding: 0;
                    
                  
                }
                 .validation-text:first-child{
                    font-size:10px;
                    margin: 24px 0 4px 24px;
                    padding: 0;
                    
                }
                input{
                   height: 36px;
                    width: 284px;
                    left: 56px;
                    top: 124px;
                    font-size: 12px;
                    margin: 0 0 0 24px;
                    background: #FFFEFB;
                    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
                    border-radius: 4px;
                   
                   

                }
                .input-text{
                    height: 108px;
                    width: 284px;
                    left: 56px;
                    top: 193px;
                    border-radius: 4px;

                }
                b{
                    color: orangered;
                    position: absolute;
                    font-size: 8px;
                    margin: 5px 0 0 24px;

                    
                }
            }   
                    h3{
                        font-size: 28px;
                        margin: 0 0 20px 0;
                        position: absolute;
                        top: 30px;
                        left: 80px;
                        @media only screen and (max-width: 767px) {
                        top: 50px;
                        left: 20px;
                        white-space:nowrap;
                        }
                        @media only screen and (max-width: 576px) {
                        }
                    }
    }


</style>