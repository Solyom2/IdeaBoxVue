<template>
  <div id="app">
    <h1>Idea Box powered by Vue</h1>

    <!--
    <HelloWorld v-bind:msg="message"/>
    <input v-model="message" type="text">
    <button v-on:click="alertMesage">Alert!</button>
    -->
    <Idea/>

  </div>
</template>

<script>
import Idea from "@/components/Idea";

export default {
  name: "App",
  components: {
    Idea
  },

}
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
</style>
