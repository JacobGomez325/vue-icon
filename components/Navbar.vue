<template>
    <div class="sticky top-0 md:z-20 z-40 ">
      
      <div class="w-full h-16 px-6 bg-gray-50  flex items-center justify-between">
        <!-- left navbar -->
        <div :class="sideBarOpen ? 'md:pl-64 lg:pl-0 ' : 'pl-0'">
          <div class="flex  items-center">
            <button  @click="toggleSidebar()">
              <svg class="h-5 w-5" v-bind:style="{ fill: 'black' }" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><title>Menu</title><path d="M0 3h20v2H0V3zm0 6h20v2H0V9zm0 6h20v2H0v-2z"/></svg>
            </button>
            <!-- <div v-if="userRule =='Personnel Soignant'" class="mx-6 flex space-x-3 items-center">
              <span class="font-semibold text-sm ">Mon centre de sante :</span>
              <span v-if="haveCentre.nom !=null " class="font-semibold text-sm shadow bg-white px-2 py-1 rounded"> {{haveCentre.nom}} </span>
              <span v-if="haveCentre.nom ==null " class="animation font-semibold text-sm shadow bg-white px-2 text-red-500 py-1 rounded"> Vous n'avez pas encore de centre santé  contactez l'administrateur </span>
            </div> -->
          </div>
        </div>
        <!-- right navbar -->
        <div class="flex space-x-2 items-center">
         
          <div class="flex items-center space-x-6">
            <ul class="flex border-b border-transparent list-reset ">
              <li @click.prevent="check_french"  :class="{'-mb-px mr-1':fr}" >
                <nuxt-link :class="{'font-bold text-primary':fr}"  class="inline-block p-2 px-0 uppercase hover:text-blue-500 focus:outline-none" :to="switchLocalePath('fr')" >fr</nuxt-link>
              </li>
              <li class="p-2 font-semibold">|</li>
              <li @click.prevent="check_english" :class="{'-mb-px mr-1':en}">
                <nuxt-link :class="{'font-bold text-primary':en}" class="inline-block p-2 px-0 uppercase hover:text-blue-darker hover:text-blue-500 focus:outline-none" :to="switchLocalePath('en')">en</nuxt-link>
              </li> 
            </ul>
          </div>
      
        <!--  <notifications></notifications> -->
         <nuxt-link to="/dashboard/profil" class="text-sm drop-button  text-gray-700 focus:outline-none" @click.prevent="toggleDD('userDropDown')">
          <div class="flex items-center  mx-2 justify-center w-8 h-8  bg-blue-400 rounded-full shadow-lg cursor-pointer"  >
            <span class="text-sm font-bold text-white uppercase"> {{initial}} </span>
          </div>
        </nuxt-link>
        </div>
      </div>
    </div>
</template>

<script>

import { mapState } from 'vuex'

export default {
  name: 'Navbar',
  computed: {
    ...mapState(['sideBarOpen'])
  },
  data() {
    return {
      dropDownOpen: false,
      currentUsers:{},
      initial:'',
      userRule:'',
      haveCentre:{},
      fr: true,
      en: false,
    }
  },
  methods: {
    toggleSidebar() {
      this.$store.dispatch('toggleSidebar')
    },
     check_french() {
      this.fr = true
      this.en = false
    },
    check_english() {
      this.fr = false
      this.en = true
    },
  },
  mounted() {
    const usersInfo = JSON.parse(localStorage.getItem("usersInfo_carte_score"));
    if (usersInfo) {
      this.currentUsers = usersInfo.users;
      this.initial = usersInfo.users.nom[0] + ''+ usersInfo.users.prenom[0]
      this.userRule = usersInfo.users.role.nom;
      this.haveCentre = usersInfo.haveCentre
    }
  },
  
}
</script>
<style scoped>
.animation {
  animation: vibration infinite .3s;
}
@keyframes vibration {
  to {
    transform: rotate(0deg);
    transition: all 0.3s ease-in-out;
  }
  from {
    transform: rotate(3deg);
    transition: all 0.3s ease-in-out;
  }
}
</style>