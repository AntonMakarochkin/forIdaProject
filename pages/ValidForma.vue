<template>

  <div id="app">
</div>
       
</template>

<script>

export default {
    components: {
     mounted() {
      this.myMethod()
    },
  },

  data() {
      return {


    }
  },
  methods:{
     getUnits: function() {
         setInterval(() => {
             console.log('k')
         }, 1000);
     },


      beforeMount(){
    this.getUnits()
 },
 },
 }

</script>

<style lang="scss">

  
</style>