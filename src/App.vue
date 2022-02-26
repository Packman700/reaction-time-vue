<template>
  <h1>Speed reaction game</h1>
  <button @click="startGame"> Start game </button>
  <div v-if="isStarted" >
    <Block :delay="delay" @buttonClicked="updateReaction"/>
  </div>
  <div v-if="reaction !== null">
    <Result :reaction="reaction" />
  </div>
</template>

<script>
import Block from './components/Block.vue'
import Result from './components/Result.vue'
import getRandomInt from "@/helpers/randomInt";

export default {
  name: 'App',
  data() {
    return{
      isStarted: false,
      delay: null,
      reaction: null
    }
  },
  methods: {
    startGame(){
      this.isStarted = true
      this.delay = getRandomInt(400, 2000)
    },
    updateReaction(reaction){
      console.log(reaction)
      this.reaction = reaction
    }
  },
  components: {
    Block,
    Result
  }
}
</script>

<style scoped>
  button {
    background-color: #4CAF50; /* Green */
    border: none;
    color: white;
    padding: 15px 32px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
  }
</style>
