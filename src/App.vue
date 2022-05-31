<template>
  <SignUpForm />
</template>

<script>
import SignUpForm from "./components/SignUpForm.vue";
export default {
  name: "App",
  components: { SignUpForm },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 20px;
}
body {
  background-color: #3282b8;
}
h1 {
  color: #bbe1fa;
  padding-top: 10px;
  font-family:'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif
}
</style>