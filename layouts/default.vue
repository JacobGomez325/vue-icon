<template>
  <div class="relative ">
    <div class="flex flex-wrap" >
      <div class="">
        <sidebar></sidebar>
      </div>
      
      <div class="pl-64">
        <div class="bg-blue-100 h-full p-2 ">
          <nuxt />
        </div>
      </div>
    </div>
   
  </div>
</template>

<script>


export default {
  name: 'Dashboard',
  data() {
    return {
     
    }
  },
 
   mounted() {
    
  },

}
</script>

<style scoped>
* {
  font-family: 'Inter', sans-serif;
}
</style>
