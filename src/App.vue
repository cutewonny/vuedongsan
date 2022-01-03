<template>
  <div class="menu">
    <a v-for="menu in menus" :key="menu">{{ menu }}</a>
  </div>
  {{ logo }}

  <Discount />
  <Modal
    @closeModal="모달창열렸니 = false"
    :원룸들="원룸들"
    :누른거="누른거"
    :모달창열렸니="모달창열렸니"
    :신고수="신고수"
  />
  <Product
    @openModal="
      모달창열렸니 = true;
      누른거 = $event;
    "
    :원룸="원룸들[i]"
    v-for="(작명, i) in 원룸들"
    :key="작명"
  />

  <!-- <div v-for="(product, i) in 원룸들" :key="product">
    <img :src="product.image" class="room-img" />
    {{ product.image }}
    <h4
      class="red"
      :style="스타일"
      @click="
        모달창열렸니 = true;
        누른거 = i;
      "
    >
      {{ product.title }}
    </h4>
    <p>{{ product.price }} 만원</p>
    <button @click="increase(i)">허위 매물 신고</button>
    <span>신고 수: {{ 신고수[i] }}</span>
  </div> -->
</template>

<script>
//데이터 바인딩.. js데이터를 Html에 꽂아넣음
import { apple, data } from "./assets/oneroom.js";
import Discount from "./Discount.vue";
import Modal from "./Modal.vue";
import Product from "./Product.vue";
console.log("apple>>>> ", apple);

export default {
  name: "App",
  data() {
    return {
      누른거: 0,
      원룸들: data,
      모달창열렸니: false,
      신고수: [0, 0, 0],
      menus: ["Home", "Shop", "About"],
      products: ["역삼동 원룸", "천호동 원룸", "마포구 원룸"],
      prices: [70, 60, 50],
      logo: "로고샵",
      스타일: "color : red",
      profileUrl: [
        require("./assets/room0.jpg"),
        require("./assets/room1.jpg"),
        require("./assets/room2.jpg"),
      ],
    };
  },
  methods: {
    increase(i) {
      this.신고수[i] += 1;
    },
  },
  components: {
    Discount: Discount,
    Modal: Modal,
    Product: Product,
  },
};
</script>

<style>
.room-img {
  width: 100%;
  margin-top: 40px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: beige;
  border-radius: 8px;
  padding: 20px;
}
</style>
