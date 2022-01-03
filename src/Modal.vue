<template>
  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      {{ month }}
      <h4>{{ 원룸들[누른거].title }}</h4>
      <img :src="원룸들[누른거].image" class="room-img" />

      <p>{{ month }}개월 선택 함: {{ 원룸들[누른거].price * month }} 만원</p>
      <!-- <input v-model="month" /> -->
      <input v-model.number="month" />
      <p>{{ 원룸들[누른거].content }}</p>
      <select v-model="month">
        <option>1</option>
        <option>2</option>
        <option>3</option>
        <option>4</option>
        <option>5</option>
      </select>
      <input type="range" min="1" max="12" />
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Modal",
  data() {
    return {
      month: 1,
    };
  },
  watch: {
    month(a) {
      if (a >= 13) {
        alert("13이상 입력하지 마세요");
        this.month = 1;
      }
    },
  },
  props: {
    원룸들: Object,
    누른거: Number,
    모달창열렸니: Boolean,
  },
  methods: {
    multiple() {},
  },
};

// console.log("month>>>>>> ", this.month);
</script>

<style></style>
