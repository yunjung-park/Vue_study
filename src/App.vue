<template>
  <nav class="menu">
    <!-- v-for 반복문 -->
    <a v-for="(nav, idx) in menus" :key="idx">{{ nav }}</a>
  </nav>

  <div v-for="(name, idx) in products" :key="name">
    <h4 :style="fontColor">{{ name }}</h4>
    <p>{{ price[idx] }}만원</p>
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
    };
  },
  components: {},
};
</script>

<style>
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
