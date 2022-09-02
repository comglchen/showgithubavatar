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
      this.$bus.$emit("mydata", {
        isFirst: false,
        isLoading: true,
        errorMsg: "",
        List: [],
      });
      axios.get(`https://api.github.com/search/users?q=${this.keyWord}`).then(
        (rep) => {
          this.$bus.$emit("mydata", {
            isLoading: false,
            errorMsg: "",
            users: rep.data.items,
          });
        },
        (error) => {
          this.$bus.$emit("mydata", {
            isLoading: false,
            errorMsg: error.message,
            users: [],
          });
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