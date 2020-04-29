<template>
  <div id="app">
    <CodeSnippets/>
  </div>
</template>

<script>
import CodeSnippets from './components/CodeSnippets.vue';
export default {
  name: 'App',
  components: {
    CodeSnippets
  }
}
</script>

<style>
*{
  margin: 0px;
    background-color: #303030;
    color: #f7f7f7;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
