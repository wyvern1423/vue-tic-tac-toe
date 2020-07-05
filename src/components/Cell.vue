<template>
  <div class="cell" @click="xClick">
    <template v-if="xDisplay">{{text}}</template>
    <template v-else></template>
  </div>
</template>

<script>

  export default {
    name: 'Cell',
    props:['value'],
    data() {
      return {
        xDisplay: false,
        text:null
      }
    },
    methods: {
      xClick() {
        if (this.text !== null){
          return
        }
        if ((this.value+1)%2 ===1){
          this.text='o'
        }else {
          this.text='x'
        }
        this.xDisplay = true
        this.$emit('click-num-change',[this.value+1,this.text])
      }
    }
  }

</script>

<style>
  .cell {
    font-size: 24px;
    border: 1px solid black;
    width: 50px;
    height: 50px;
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>
