<template>
  <div>
    <DetailModal
      :isModalOpen="isModalOpen"
      :detailNumber="detailNumber"
      :products="products"
      @modalHandler="modalHandler"
    />

    <!-- 헤더 -->
    <div class="menu">
      <a v-for="(menuName, idx) in menu" :key="idx">{{ menuName }}</a>
    </div>

    <DiscountComp :product="product" :idx="idx" />

    <!-- 상품 목록 -->
    <div v-for="(product, idx) in products" :key="idx">
      <ProductCard
        @modalOpenHandler="modalOpenHandler"
        :product="product"
        :idx="idx"
      />
    </div>
  </div>
</template>

<script>
import dataList from "./data";
import DiscountComp from "./DiscountComp.vue";
import DetailModal from "./DetailModal.vue";
import ProductCard from "./ProductCard.vue";

console.log(dataList);

export default {
  name: "App",
  data() {
    return {
      isModalOpen: false,
      detailNumber: null,
      price1: 60,
      price2: 50,
      products: dataList,
      menu: ["Home", "Shop", "About"],
      report: [0, 1, 2],
    };
  },
  methods: {
    clickHandler(idx) {
      this.report[idx]++;
    },
    modalHandler() {
      this.isModalOpen = !this.isModalOpen;
    },
    modalOpenHandler(idx) {
      this.isModalOpen = true;
      this.detailNumber = idx;
    },
  },
  components: {
    DiscountComp,
    DetailModal,
    ProductCard,
  },
};
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
  margin: 0;
}
div {
  box-sizing: border-box;
}
.menu {
  background: darkslateblue;
  padding: 15px;
  /* border-radius: 5p */
}
.menu a {
  color: white;
  padding: 10px;
}
.room-img {
  width: 100%;
  margin-top: 40px;
}
/* .black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
  display: flex;
  justify-content: center;
}
.white-bg {
  width: 90%;
  max-height: 50%;
  background: white;
  border-radius: 8px;
  padding: 20px;
  overflow: scroll;
}
.button-wrapper {
  widows: 100%;
  display: flex;
  justify-content: end;
  font-weight: 900;
  cursor: pointer;
} */
</style>
