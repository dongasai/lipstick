<template>
  <div class="home">

  {{ brands }}

   <br>
   {{now}}
    <ul>
    <li v-for="(ip,index) in list_line" :key="index">
        {{ip}}
    </li>
  </ul>
  </div>

</template>

<script>
// @ is an alias to /src
import brands from '../data/brand'
import ysl from '../data/ysl'
import Givenchy from '../data/givenchy'
import chanel from '../data/chanel'
import dior from '../data/dior'
import Maybelline from '../data/maybelline'

export default {
  name: 'home',
  data () {
    return {
      brands: brands,
      lists: {
        ysl: ysl,
        givenchy: Givenchy,
        chanel: chanel,
        dior: dior,
        maybelline: Maybelline
      },
      list_line: []
    }
  },
  props: {
    now: String
  },
  methods: {
    init () {
      // 初始化,读取数据
      for (let brandName in this.lists) {
        let brand = this.lists[brandName]
        for (let seriesIndex in brand) {
          let series = brand[seriesIndex]
          for (let lipsticksIndex in series.lipsticks) {
            let lipsticks = series.lipsticks[lipsticksIndex]
            console.log(lipsticks)
            this.add_lipsticks(lipsticks)
          }
        }
      }
    },
    add_lipsticks (lipsticks) {
      // 增加口红
      this.list_line.push(lipsticks)
    }
  },
  components: {
  },
  mounted () {
    this.init()
  }

}
</script>
