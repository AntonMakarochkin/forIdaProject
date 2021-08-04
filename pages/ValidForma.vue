<template>

  <div id='container'>
    
          
         
   
  </div>
       
</template>

<script>
import Catalog from './Catalog.vue'

export default {
    components: {
    Catalog
  },
  data() {
    return {
         
     
    }
  },
methods: {
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
        }
}
 }

</script>

<style lang="scss">

  
</style>