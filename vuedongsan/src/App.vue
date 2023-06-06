<template>
<div>

  <div class="menu">
    <a v-for="(menuName, idx) in menu" :key="idx">{{menuName}}</a>
    
  </div>

  <div style="font-size:2rem; font-weight:800">
    원룸샵
  </div>

    <div v-for="(product, idx) in products" :key="idx">
      <h4>{{product}}</h4>
      <p>{{price1}} 만원</p>
    </div>
</div>
</template>

<script>


export default {
  name: 'App',
  data() {
    return {
      price1 : 60,
      price2 : 50,
      products : ["역삼동 원룸", "천호동 원룸", "삼전동 원룸"],
      menu : ["Home", "Shop", "About"],
    }
  },
  components: {
    
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin : 0 auto; */
}

.menu {
  background:  darkslateblue;
  padding : 15px;
  border-radius: 5px;
}
.menu a {
  color : white;
  padding : 10px
}
</style>
