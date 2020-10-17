<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
  </div>
  <div>
    <RandomTextApi/>
  </div>
</template>

<script>
// @ is an alias to /src
import RandomTextApi from "../components/RandomTextApi";
export default {
  name: 'Home',
  components: {
    RandomTextApi
  }
}
</script>
