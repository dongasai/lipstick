<template>
  <div id="app">
    <div id="nav">
      <div
      class="brand"
      v-for="(brand, index) in brands" :key="index">
        <span @click="change_brand(index)"  >{{brand.name}}</span> |
      </div>
      <div>
        {{ now_brand }}
        <home :now="now_brand"></home>
      </div>
    </div>
  </div>
</template>
<script>
import brands from './data/brand'
import home from './views/Home'
export default {
  data () {
    return {
      brands: brands,
      now_brand: 'all'
    }
  },
  methods: {
    change_brand (index) {
      this.now_brand = index
      console.log(index)
    }
  },
  components: {
    home: home
  }
}
</script>

<style lang="less">
.brand{
  float: right
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  min-width: 250px;
  margin: auto;
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
