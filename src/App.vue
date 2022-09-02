<template>
  <div>
    <SearchBox />
    <DisplayBox />
  </div>
</template>

<script>
import SearchBox from "./components/SearchBox";
import DisplayBox from "./components/DisplayBox";

export default {
  components: {
    DisplayBox,
    SearchBox,
  },
};
</script>

<style>
</style>