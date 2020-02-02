<template>
  <div>
    <d-header></d-header>
    <router-view></router-view>
    <d-footer></d-footer>
  </div>
</template>

<script>

    import DHeader from "../common/Header";
    import DFooter from "../common/Footer";
    export default {
        name: "index",
      components: {DHeader,DFooter}
    }
</script>

<style scoped>

</style>
