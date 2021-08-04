<template>
  <div id="aapp" >
        <TodoItem/>
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
     
        
    }
    
  },
  methods: {
    funPush() {

    
    },

  
  }

 
}
</script>

<style lang="scss">
#aapp{
 display: flex;
 flex-direction: row-reverse;
 float: left;
  button{
    width: 100px;
    height: 20px;
    background: green;
  }
  #container{
    display: flex;
    flex-direction: row;
    width: 1150px;
    background: greenyellow;
      flex-wrap: wrap;

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
  .container-form{
    
    width: 300px;
    height: 500px;
    background: lightcoral;
  }
}

</style>
