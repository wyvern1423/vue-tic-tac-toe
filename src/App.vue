<template>
  <div>
    <div class="row">
      <Cell :value="clickNum" @click-num-change="clickCount(0,$event)"></Cell>
      <Cell :value="clickNum" @click-num-change="clickCount(1,$event)"></Cell>
      <Cell :value="clickNum" @click-num-change="clickCount(2,$event)"></Cell>
    </div>
    <div class="row">
      <Cell :value="clickNum" @click-num-change="clickCount(3,$event)"></Cell>
      <Cell :value="clickNum" @click-num-change="clickCount(4,$event)"></Cell>
      <Cell :value="clickNum" @click-num-change="clickCount(5,$event)"></Cell>
    </div>
    <div class="row">
      <Cell :value="clickNum" @click-num-change="clickCount(6,$event)"></Cell>
      <Cell :value="clickNum" @click-num-change="clickCount(7,$event)"></Cell>
      <Cell :value="clickNum" @click-num-change="clickCount(8,$event)"></Cell>
    </div>
    {{result}}
  </div>
</template>

<script>
  import Cell from "./components/Cell";

  export default {
    name: 'App',
    components: {Cell},
    data() {
      return {
        clickNum: 0,
        map: [
          [null, null, null], [null, null, null], [null, null, null]
        ],
        result: false
      }
    },
    methods: {
      clickCount(i, val) {
        this.clickNum = val[0]
        this.map[Math.floor(i / 3)][i % 3] = val[1]
        console.log(this.map)
        console.log(`text和val分别是${val[0]}+${val[1]}`)
        this.tell()
      },
      tell() {
        const map = this.map
        for (let i = 0; i < 3; i++) {
          if (map[i][0] !== null && map[i][0] === map[i][1] && map[i][1] === map[i][2]) {
            this.result = true
          }
        }
        for (let i = 0; i < 3; i++) {
          if (map[0][i] !== null && map[0][i] === map[1][i] && map[1][i] === map[2][i]) {
            this.result = true
          }
        }
        if (map[0][0] !== null && map[1][1] === map[2][2] && map[1][1] === map[0][0]){
          this.result =true
        }
        if (map[0][2] !== null && map[0][2] === map[1][1] && map[1][1] === map[2][0]) {
          this.result = true
        }
      }
    }
  }

</script>

<style>
  .row {
    display: flex;
  }
</style>
