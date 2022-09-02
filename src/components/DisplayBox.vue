<template>
  <div class="searchBox">
    <h1 v-show="userInfo.isFirst">欢迎光临！</h1>
    <h1 v-show="userInfo.isLoading">正加载中。。。</h1>
    <h1 v-show="userInfo.errorMsg">{{ userInfo.errorMsg }}</h1>
    <div
      v-show="userInfo.users.length"
      v-for="user in userInfo.users"
      :key="user.login"
    >
      <a :href="user.html_url">
        <img :src="user.avatar_url" style="height: 80px; width: 80px" />
      </a>
      <p>{{ user.login }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      userInfo: {
        isFirst: true,
        isLoading: false,
        errorMsg: "",
        users: [],
      },
    };
  },
  mounted() {
    this.$bus.$on("mydata", (obj) => {
      //合并userInfo与obj
      this.userInfo = { ...this.userInfo, ...obj };
    });
  },
};
</script>

<style>
</style>