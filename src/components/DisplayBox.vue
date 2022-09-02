<template>
  <div class="searchBox">
    欢迎光临！
    <span v-for="user in List" :key="user.login">
      <a :href="user.html_url">
        <img :src="user.avatar_url" style="height: 80px; width: 80px" />
      </a>
      <p>{{ user.login }}</p>
    </span>
  </div>
</template>

<script>
export default {
  data() {
    return {
      List: [],
    };
  },
  mounted() {
    this.$bus.$on("mydata", (data) => {
      this.List = data;
      console.log(this.List);
    });
  },
};
</script>

<style>
</style>