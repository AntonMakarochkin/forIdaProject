<template>

  <div id='container'>
       <div class="wrapper" 
               
    >
                <div class="title"> {{ user.name }} </div>
                <div class="price"> {{user.position}} </div>
                <br>
                <button @click='sort'></button>
                <button @click='sortPlus'></button>
                <button @click='sortName'></button>
          </div>
   
  </div>
       
</template>

<script>
export default {
   props: {
    user: {
      name: String,
      position: Number
    }
  },
  data() {
    return {
      
            
     
    }
  },
methods: {
        sort() {
        this.users = this.users.sort(function(a, b) {return a.position - b.position})
        },
        sortPlus() {
        this.urers = this.users.sort((a, b) =>b.position - a.position )
        },
        sortName() {
        this.users = this.users.sort(function(a, b){
    if(a.name < b.name) { return -1; }
    if(a.name > b.name) { return 1; }
    return 0;
})
        }
}
 }

</script>

<style lang="scss">

  
</style>