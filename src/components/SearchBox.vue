<template>
  <div>
    <input
      type="text"
      placeholder="请输入要搜索内容的关键字"
      v-model="keyWord"
    />
    <button @click="search">搜索</button>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      keyWord: "",
    };
  },
  methods: {
    search() {
      axios.get(`https://api.github.com/search/users?q=${this.keyWord}`).then(
        (data) => {
          console.log("请求成功！", data.data.items);
          this.$bus.$emit("mydata", data.data.items);
        },
        (error) => {
          console.log("请求失败！", error);
        }
      );
    },
  },
};
</script>

<style>
.searchBox {
  height: 600px;
  background-color: aqua;
}
</style>