<template>
  <div
    @click="handleClick"
    class="speedTestBlock"
    :class="{
      active: !this.isClicked && this.blockIsActive,
      error: this.isClicked && this.isClickedToEarly,
      success: this.isClicked && !this.isClickedToEarly,
    }"
  >
    <p v-if="!this.isClicked && this.blockIsActive"> Click me </p>
    <p v-else-if="this.isClickedToEarly"> Hold on boy </p>
    <p v-else-if="this.isClicked"> Nice but time try be faster ;P </p>
    <p v-else> Wait for me </p>
  </div>

</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Block",
  data() {
    return {
      blockIsActive: false,
      isClickedToEarly: false,
      isClicked: false,
      reactionTime: null,
      componentRenderTime: null
    }
  },
  props: {
    delay: { type: Number }
  },
  methods: {
    setup(){
      this.blockIsActive = false
      this.isClickedToEarly = false
      this.isClicked = false
      this.reactionTime = null
      this.componentRenderTime = Date.now()
    },
    changeBlockToActive(){
      this.blockIsActive = true
    },
    handleClick(){
      if (!this.blockIsActive)
        this.isClickedToEarly = true
      this.isClicked = true
      this.reactionTime = Date.now() - this.componentRenderTime - this.delay
      console.log(this.reactionTime)
      this.$emit("buttonClicked", this.reactionTime)
    },
  },
  watch: {
    delay:{
      immediate: true,
      handler(newDelay) {
        this.setup()
        setTimeout(this.changeBlockToActive, newDelay)
      }
    }
  },
}
</script>

<style scoped lang="scss">
  .speedTestBlock{
    display: flex;
    align-items: center;
    justify-content: center;

    background-color: rgba(0,0,0,0.2);
    border: solid 1px rgba(0,0,0,0.6);
    width: 300px;
    height: 250px;
    margin: 2rem auto;
  }
    .active{
      background-color: #8cff90;
    }
    .error{
      background-color: #ff8c8c;
    }
    .success{
      background-color: #fff08c;
    }
</style>