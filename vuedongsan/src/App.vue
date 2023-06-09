<template>

<div>

  <div v-if="isModalOpen" class="black-bg">
    <div class="white-bg">
      <div class="button-wrapper" v-on:click="isModalOpen=false">
        <div>
          X
        </div>
      </div>
      <h4>상세페이지</h4>
      <p>상세페이지 내용</p>
    </div>
  </div>

  <div class="menu">
    <a v-for="(menuName, idx) in menu" :key="idx">{{menuName}}</a>
    
  </div>

  <div style="font-size:2rem; font-weight:800">
    VUEDONGSAN
  </div>



  <div v-for="(product, idx) in products" :key="idx">
    <img :src="product.image" alt="방사진" class="room-img"/>
    <h4 v-on:click="isModalOpen = true">{{product.title}}</h4>
    <p>{{product.price}} 만원</p>
    <button v-on:click="clickHandler(idx)">신고하기</button> <span>신고수 : {{report[idx]}}</span>
  </div>

</div>
</template>

<script>

import dataList from "./data"
console.log(dataList)

export default {
  name: 'App',
  data() {
    return {
      isModalOpen : false,
      price1 : 60,
      price2 : 50,
      products : dataList,
      menu : ["Home", "Shop", "About"],
      report : [0,1,2]
    }
  },
  methods : {
    clickHandler(idx) {
      this.report[idx]++
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

body {
  margin : 0
}
div {
  box-sizing: border-box;
} 
.menu {
  background:  darkslateblue;
  padding : 15px;
  /* border-radius: 5p */
}
.menu a {
  color : white;
  padding : 10px
}
.room-img {
  width : 100%;
  margin-top : 40px;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed;
  padding : 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding : 20px;
}
.button-wrapper {
  widows: 100%;
  display: flex;
  justify-content: end;
  font-weight: 900;
  cursor: pointer;
}
</style>
