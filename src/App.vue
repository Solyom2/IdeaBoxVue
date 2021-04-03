<template>
  <div id="app">
    <div class="navbar-text">
      <h1>Idea Box powered by Vue</h1>
    </div>

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

</style>
