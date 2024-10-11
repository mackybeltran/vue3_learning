<template>
  <div id='app'>
    {{fullName}}
    <TwootItem  class='twoot' v-for='(twoot, index) in state.user.twoots' :key='index' :twoot='twoot.text'/>
    <div class='admin-badge' v-if='state.user.isAdmin'>ADMIN</div>
    <div>{{ state.followers }}</div>
    <button @click=followUser>Follow</button>
  </div>

</template>

<script>

import TwootItem from './components/TwootItem.vue';
import { reactive, computed } from 'vue';

export default {
// vue3 composition. vue 2 code commented out. 

  name: 'App',
  components: { TwootItem },
  setup(){
    const state = reactive({
      followers: 0,
      user: {
        id: 1, 
        firstName: 'John',
        lastName: 'Smith',
        email: 'johnsmith@yahoo.com',
        isAdmin: true,
        twoots: [
          {
            id: 1,
            text: 'this is text A'
          },
          {
            id: 2,
            text: 'this is text B'
          }
        ]
      }
    })

    const fullName= computed(() => state.user.firstName + state.user.lastName)

    const followUser = () => {
      state.followers++
    }

    return {
      state,
      fullName,
      followUser
    }
  }
  // name: 'App',
  // components: { TwootItem },
  // data(){
  //   return {
  //     followers: 0,
  //     user: {
  //       id: 1,
  //       firstName: 'John',
  //       lastName: 'Smith',
  //       email: 'johnsmith@yahoo.com',
  //       isAdmin: true,
  //       twoots: [
  //         {
  //           id: 1,
  //           text: 'this is text A'
  //         },
  //         {
  //           id: 2,
  //           text: 'this is text B'
  //         }
  //       ]
  //     }
  //   }
  // },
  // watch: {
  //   followers(newFollowerCount, oldFollowerCount){
  //     if (newFollowerCount > oldFollowerCount){
  //       console.log('gained a follower')
  //     }
  //   }
  // },
  // computed:{
  //   fullName(){
  //     return `${this.user.firstName} ${this.user.lastName}`; 
  //   }
  // },
  // methods: {
  //   followUser(){
  //     this.followers++
  //   }
  // },
  // mounted(){
  //   this.followUser()
  // }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  flex-direction: column;
}

.admin-badge {
  color: red;
  font-weight: bold;
}
</style>
