<template>
  <div v-if="isModalOpen" class="black-bg">
    <div class="white-bg">
      <div class="button-wrapper" @click="modalHandlerEmit">
        <div>X</div>
      </div>
      <h4>{{ products[detailNumber].title }}</h4>
      <p>
        {{ month }}개월 선택함 {{ products[detailNumber].price / month }} 만원
      </p>
      <img :src="products[detailNumber].image" alt="방사진" class="room-img" />
      <p>{{ products[detailNumber].content }}</p>
      할부 개월 수<input v-model.number="month" />
      <DiscountComp />
    </div>
  </div>
</template>

<script>
import DiscountComp from "./DiscountComp.vue";

export default {
  name: "DetailModal",
  data() {
    return {
      month: 1,
    };
  },
  watch: {
    month(a) {
      if (a !== "" && typeof a === "string") {
        alert("숫자만 입력 가능합니다.");
        this.month = 1;
      }
      // if (a < 1) {
      //   alert("최소 1개월 이상 입력해야합니다.");
      //   this.month = 1;
      // }
      if (a > 12) {
        alert("할부 개월 수는 최대 12개월입니다.");
        this.month = 1;
      }
    },
  },
  props: {
    isModalOpen: Boolean,
    detailNumber: Number,
    products: Array,
  },
  components: {
    DiscountComp,
  },
  methods: {
    modalHandlerEmit() {
      this.$emit("modalHandler");
    },
  },
  mounted() {
    console.log(this.month);
  },
};
</script>

<style>
.black-bg {
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
  /* height: 60%; */
  /* max-height: 50%; */
  background: white;
  border-radius: 8px;
  padding: 20px;
  /* overflow: scroll; */
}
.button-wrapper {
  widows: 100%;
  display: flex;
  justify-content: end;
  font-weight: 900;
  cursor: pointer;
}
.room-img {
  width: 100%;
  margin-top: 40px;
}
</style>
