<template>
  <div>
    <Transition name="fade">
      <DetailModal
        :isModalOpen="isModalOpen"
        :detailNumber="detailNumber"
        :products="products"
        @modalHandler="modalHandler"
      />
    </Transition>

    <!-- 헤더 -->
    <div class="menu">
      <a v-for="(menuName, idx) in menu" :key="idx">{{ menuName }}</a>
    </div>

    <!-- 할인배너 -->
    <DiscountComp v-if="showDiscount" :discountRate="discountRate" />

    <button @click="priceSort">가격순 정렬</button>
    <button @click="sortBack">기본 정렬</button>

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
      discountRate: 30,
      showDiscount: true,
      isModalOpen: false,
      detailNumber: null,
      price1: 60,
      price2: 50,
      products: dataList,
      newProducts: [...dataList],
      menu: ["Home", "Shop", "About"],
      report: [0, 1, 2],
    };
  },
  watch: {
    discountRate() {
      if (this.discountRate === 0) {
        this.showDiscount = false;
      }
    },
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
    priceSort() {
      this.products.sort(function (a, b) {
        return a.price - b.price;
      });
    },
    sortBack() {
      this.products = [...this.newProducts];
    },
  },
  components: {
    DiscountComp,
    DetailModal,
    ProductCard,
  },
  mounted() {
    setInterval(() => {
      this.discountRate--;
      // if (this.discountRate === 0) {
      //   this.showDiscount = false;
      // }
    }, 1000);
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

.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  opacity: 1;
}

.fade-leave-from {
  opacity: 1;
}
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to {
  opacity: 0;
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
.start {
  opacity: 0;
  transition: all 0.7s;
}
.end {
  opacity: 1;
}
</style>
