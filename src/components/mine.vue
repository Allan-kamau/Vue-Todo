<template>
  <div class="text">
    <ul>
      <p class="flex">{{msg}}</p>
      <!-- <Mine msg="stop working" /> -->
    </ul>
  </div>
</template>

<script>
// import Mine from "src/App.vue";
export default {
  name: "Mine",
  props: {
    msg: String
  }
  // Mine
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
