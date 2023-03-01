<template>
  <div class="md:w-1/3 lg:w-64 fixed md:top-0  md:left-0  h-screen overflow-auto shadow lg:block bg-gray-50  z-30" >
    <div>
      <div class="w-full h-20 mt-14 md:mt-0 flex px-4 items-center mb-4">
        <p  class="font-semibold text-3xl  text-gray-700"> <span class="text-green-500">GOJO</span>  icon </p>
      </div>

      <div  class="mx-3">
        <input type="text" placeholder="Search icon" class="px-4 py-2 border border-gray-300 bg-gray-200 shadow w-full text-lg rounded outline-none">
      </div>
     
        <nuxt-link  style="width:95%"  class="flex items-center my-3 px-2 py-2 z-10 relative text-gray-700 mx-3"  to="/">
          <span>Home</span>
        </nuxt-link>

        <nuxt-link v-for="link in links" :key="link.id" style="width:95%"  class="flex items-center my-3 px-2 py-2 z-10 relative text-gray-700 mx-3"  :to=" {name:'module-name',params:{name:link.name}} ">
          <span>{{link.name}}</span>
        </nuxt-link>

      
    </div>
  </div>
</template>

<script>

export default {
  name: 'sidebar',
  data() {
    return {
      links:[
        {name:"Ant Design Icons"},
        {name:"Bootstrap Icons"},
        {name:"BoxIcons"},
        {name:"Devicons"},
        {name:"Feather"},
        {name:"Flat Color Icons"},
        {name: "Font Awesome"},
        {name:"Game Icons"},
        {name:"Grommet-Icons"},
        {name:"Heroicons"},
        {name:"IcoMoon Free"},
        {name:"IcoMoon Free"},
        {name:"Ionicons 4"},
        {name:"Ionicons 5"},
        {name:"Material Design icons"},
        {name:"Remix Icon"},
        {name:"Simple Icons"},
        {name:"Tabler Icons"},
        {name:"VS Code Icons"},
        {name:"Weather Icons"},
        {name:"css.gg"}
      ]
    };
  },
  computed: {
   
  },
  methods: {
    
   
  },

  
};
</script>

<style scoped>

.nuxt-link-exact-active
{
  color: #fff;
  font-weight: bold;
  padding: 10px 18px;
  background-color: #4498E5;
}




</style>