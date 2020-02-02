<template>
  <div>
    <header class="w">
      <div class="w-container">
        <div class="nav-logo">
          <h1 @click="changePage(-1)">
            <router-link to="/" title="随画">随画——绘画交流区</router-link>
          </h1>
        </div>
      </div>
    </header>
  </div>
</template>

<script>
  export default {
    name: "Header",
    data() {
      return {
        activeIndex: '1',
        choosePage: -1,
      };
    },
    methods: {
      handleSelect(key, keyPath) {
        console.log(key, keyPath);
      },
      changePage (v) {
        this.choosePage = v;
      }
    }
  }
</script>

<style lang="scss" rel="stylesheet/scss" scoped>

</style>
