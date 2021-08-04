<template>
  <div id="aapp" >
    <div id='container'>
           <div class="wrapper" 
                v-for="item in arrList"
                v-bind:todo="item"
                v-bind:key="item.id"
    >
                <div class="img" > {{item.id}} </div>
                <div class="title"> {{item.title}} </div>
                <div class="text"> {{item.text}} </div>
                <div class="price"> {{item.price}} </div>
          </div>
    </div>
   
        <br>
      <input v-model="img"> 
      <input v-model="title"> 
      <input v-model="text"> 
      <input v-model="price"> 
      <button class="btn" @click="funPush"></button>
      
    
    
  </div>
</template>

<script>
import TodoItem from "./Catalog.vue"
import ValidForma from './ValidForma.vue'



export default {
  components: {
    TodoItem,
    ValidForma
  },

  data() {
    return {
     
         img: 'href',
         title: 'some title',
         text: 'some name',
         price: '1000',
         newObj: {},
         arrList: [
             {id :0, title:'Наименование товара', img:"href", text:'Lorem ipsum dolor sit amet consectetur adipisicing elit. Obcaecati,', price:'3000'},
            
         ],
    }
    
  },
  methods: {
    funPush() {
    
      this.newObj.img = this.img
      this.newObj.title = this.title
      this.newObj.text = this.text
      this.newObj.price = this.price

      
      this.arrList.push(this.newObj)
   
    }
  }

 
}
</script>

<style lang="scss">
  button{
    width: 100px;
    height: 20px;
    background: green;
  }
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
</style>
