<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
  </div>
  <div>
    <h2>Parent Input </h2>
    <input v-model="userInput" type="text" name="" id="" />
  </div>
  <div>
    <RandomTextApi v-bind:userInput="userInput" /> 
    <!-- V-BIND really important, otherwise you Only pass a String instead of dynamic props!!! -->
  </div>
</template>

<script>
// @ is an alias to /src
import RandomTextApi from "../components/RandomTextApi";
export default {
  name: "Home",
  components: {
    RandomTextApi,
  },
  data: function () {
    return {
      userInput: "",
    };
  },
};
</script>
