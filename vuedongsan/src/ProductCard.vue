<template>
  <div>
    <div>
      <img :src="product.image" alt="방사진" class="room-img" />
      <h4 @click="modalOpenEmit">
        {{ product.title }}
      </h4>
      <p>{{ product.price }} 만원</p>
      <!-- <button v-on:click="clickHandler(idx)">신고하기</button>
    <span>신고수 : {{ report[idx] }}</span> -->
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductCard",
  props: {
    product: Object,
    idx: Number,
  },
  methods: {
    modalOpenEmit() {
      this.$emit("modalOpenHandler", this.idx);
    },
  },
};
</script>

<style></style>
