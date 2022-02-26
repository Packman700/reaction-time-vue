<template>
  <h2 v-if="reaction < 0"> Did you know yo should click ONLY when button is green 🤣 </h2>
  <h2 v-else-if="reaction < 1"> You is like sonic </h2>
  <h2 v-else-if="reaction < 20"> Lucky shot? 😮😮😮</h2>
  <h2 v-else-if="reaction < 50"> Faster then light ⚡</h2>
  <h2 v-else-if="reaction < 100"> Okey this was nice 🙀</h2>
  <h2 v-else-if="reaction < 300"> Not bad for an old 👵</h2>
  <h2 v-else-if="reaction < 500"> Just click green button, pretty simple right 😌 </h2>
  <h2 v-else-if="reaction < 700"> I hope you will be better next time 😔</h2>
  <h2 v-else-if="reaction < 1000"> 🐌 </h2>
  <h2 v-else-if="reaction < 2000"> Maybe drink some energy drink??? ☕</h2>
  <h2 v-else> Don't sleep 😴 </h2>
  <h3> Your reaction time is {{ reaction/1000 }}s </h3>

</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Result",
  props: [ 'reaction' ]
}
</script>

<style scoped>
</style>