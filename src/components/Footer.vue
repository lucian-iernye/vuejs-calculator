<template>
  <footer class="footer">
    <p>{{ copyright }}</p>
    <a href="#">GitHub</a>
    <a href="#">LinkedIn</a>
  </footer>
</template>

<script>
export default {
  name: "Footer",
  props: {
    copyright: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.footer {
  margin: 0 auto;
  background-color: #2c3e50;
  color: #43b883;
  padding: 30px;
}

p {
  font-size: 1.5rem;
}

a {
  color: white;
  margin: 5px;
  text-decoration: none;
}

a:hover {
  color: #43b883;
  margin: 5px;
  text-decoration: underline;
}
</style>
