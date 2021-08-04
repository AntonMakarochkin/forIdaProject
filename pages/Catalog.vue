<template>
<div id="container">

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
        <br>
      <p>{{ this.arrList.length -1 }}</p>


</div>
    
 
</template>

<script>

export default {
 data() {
     return {
         pisa: 1, 
         arrList: [
             {id :0, title:'Наименование товара', img:"href", text:'Lorem ipsum dolor sit amet consectetur adipisicing elit. Obcaecati,', price:'2000'},
             {id :1, title:'Наименование товара', img:"href", text:'Lorem ipsum dolor sit amet consectetur adipisicing elit. Obcaecati,', price:'3000'},
             {id :2, title:'Наименование товара', img:"href", text:'Lorem ipsum dolor sit amet consectetur adipisicing elit. Obcaecati,', price:'4000'},
             {id :3, title:'Наименование товара', img:"href", text:'Lorem ipsum dolor sit amet consectetur adipisicing elit. Obcaecati,', price:'5000'},
             {id :3, title:'Наименование товара', img:"href", text:'Lorem ipsum dolor sit amet consectetur adipisicing elit. Obcaecati,', price:'5000'},
         ]
     }
 }
}
</script>


<style lang="scss">
#container{
    display: flex;
    flex-direction: row;
    
}
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
</style>