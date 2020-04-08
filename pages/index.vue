<template>
  <div v-infinite-scroll="loadMore"
       infinite-scroll-disabled="busy"
       infinite-scroll-distance="10">
    <p v-for="item in data" :key="item.name">
      {{item.name}}
    </p>
    <p v-if="busy">Loading...</p>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        count: 0,
        data: [],
        busy: false
      }
    },
    methods: {
      loadMore() {
        this.busy = true;

        setTimeout(() => {
          for (let i = 0, j = 10; i < j; i++) {
            this.data.push({name: ++this.count});
          }
          this.busy = false;
        }, 1000);
      }
    }
  }
</script>

<style>
</style>
