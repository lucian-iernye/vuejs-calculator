<template>
  <div class="header">
    <h1>{{ title }}</h1>
  </div>
</template>

<script>
export default {
  name: "Header",
  props: {
    title: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.header {
  background-color: #2c3e50;
  color: #43b883;
  padding: 50px;
}
</style>
