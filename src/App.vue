<template>
  <div class="black-bg" v-if="OpenModal == true" @click="OpenModal = false">
    <div class="white-bg" v-if="OpenModal == true">
      <h4>상세 페이지</h4>
      <p>상세 페이지 내용</p>
    </div>
  </div>

  <nav class="menu">
    <!-- v-for 반복문 -->
    <a v-for="(nav, idx) in menus" :key="idx">{{ nav }}</a>
  </nav>

  <div v-for="(name, idx) in products" :key="name">
    <h4 :style="fontColor">{{ name }}</h4>
    <p>{{ price[idx] }}만원</p>
  </div>

  <div>
    <!-- 
      //? 클릭 이벤트리스너 : v-on:click == @click 
      -->
    <button @click="increase">Plus</button>
    <button @click="count < 1 ? 0 : count--">Minus</button>
    <span>clickCount: {{ count }}</span>
  </div>

  <div>
    <img src="./assets/image_1.png" alt="image_1" class="img" />
    <h4 @click="OpenModal = true">{{ products[0] }}</h4>
    <p>{{ price[0] }}</p>
    <button @click="신고수[0]++">버튼 1</button>
    <span> 신고수: {{ 신고수[0] }}</span>
  </div>
  <div>
    <img src="./assets/image_2.png" alt="image_2" class="img" />
    <h4 @click="OpenModal = true">{{ products[1] }}</h4>
    <p>{{ price[1] }}</p>
    <button @click="신고수[1]++">버튼 2</button>
    <span> 신고수: {{ 신고수[1] }}</span>
  </div>
  <div>
    <img src="./assets/image_3.png" alt="image_3" class="img" />
    <h4 @click="OpenModal = true">{{ products[2] }}</h4>
    <p>{{ price[2] }}</p>
    <button @click="신고수[2]++">버튼 3</button>
    <span> 신고수: {{ 신고수[2] }}</span>
  </div>
</template>

<script>
export default {
  name: "App",
  // todo: 데이터 바인딩이란?
  // ? 1. 데이터 변경을 쉽게 관리하기 위해서 사용(가변적)
  // ? 2. "실시간 자동 렌더링" 기능을 사용하기 위해 => 데이터가 변경되면 데이터와 관련된 HTML에도 실시간으로 변경
  // ? 3. HTML 속성도 데이터바인딩 가능하다 => 속성 왼쪽에 콜론(:)
  data() {
    return {
      // 데이터 보관함 (가변적인 변수)
      price: [50, 60, 100],
      fontColor: "color: darkslateblue",
      products: ["가", "나", "다"],
      menus: ["Home", "Products", "About"],
      count: 0,
      // todo 데이터를 어떻게 만들지 먼저 생각하고나서 뷰를 만들자.
      신고수: [0, 0, 0],
      // todo 모달창의 상태 데이터로 저장해두기
      OpenModal: false,
    };
  },
  methods: {
    increase() {
      this.count++;
    },

    increase2() {
      this.신고수++;
    },
  },
  components: {},
};
</script>

<style>
.img {
  width: 500px;
  margin-top: 40px;
}

body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

/* //! 동적 UI 만드는 법 
    1. UI의 현재 상태를 데이터로 저장해두기
    2. 데이터에 따라 UI가 어떻게 보일지 작성하기 */

.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}

.white-bg {
  width: 100%;
  background: #fff;
  border-radius: 8px;
  padding: 20px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: #fff;
  padding: 10px;
}
</style>
