<template>
    <div id="tShirt">
      <van-pull-refresh v-model="isLoading" @refresh="onRefresh">
        <p>sportPant-刷新次数: {{ count }}</p>
      </van-pull-refresh>
    </div>
  </template>
  <script>
  
  export default {
    name: "vue",
    data() {
      return {
        count: 0,
        isLoading: false,
      };
    },
    computed: {},
    watch: {},
    methods: {
      onRefresh() {
        setTimeout(() => {
          this.isLoading = false;
          this.count++;
        }, 1000);
      },
    },
  };
  </script>
  <style></style>
  