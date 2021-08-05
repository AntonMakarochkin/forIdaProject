<template>
<!-- Я долго возился с тем, чтобы все элементы интерфейса были отдельными компонентами, но к сожалению
не смог справиться с контекстом некоторых функций и пришлось сделать так -->

<!-- Уверен, что многие моменты можно было выполнить более лаконично, но я не успел разобраться со всей документацией vue -->
  <div id="aapp" >
        <TodoItem/>
        <ValidForma/>
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

<style lang="scss" scoped>

</style>
