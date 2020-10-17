<template>
  <div>
      <h4>Child Input</h4>
    <input v-model="inputText" type="text" />
    <h5>
      Im am Passed from Home to RandomRextApi-Component + {{ inputFromParent }}
    </h5>

    <button @click="updatedText = inputText + ' Hello'">Update</button>
    <p>{{ updatedText }}</p>

    <p v-for="text in state.data" :key="text">
      {{ text.join() }}
      <!-- .join() removes square brackets from array -->
    </p>
  </div>
</template>

<script>
import { ref, watchEffect, reactive } from "vue";
export default {
  name: "RandomTextApi",
  props: {
    userInput: String,
  },
  setup(props) {
    const inputText = ref(null);
    const updatedText = ref(null); //normal Variable
    const state = reactive({ data: [] }); //This is reactive Variable or lets say a "state"-Variable
    const userID = ref(0);
    let inputFromParent = ref(null);

    watchEffect(() => {
      //like useEffect I guess --> watchEffect will run a method whenever any of its dependencies are changed,
      
      
      if (updatedText.value) {
        //One thing to note is that watchEffect will also run immediately whenever the component is initialized
        fetch(
          `https://baconipsum.com/api/?type=all-meat&paras=2&start-with-lorem=1`
        )
          .then((response) => response.json())
          .then((data) => {
            state.data.push(data);
          });
      }


      console.log(userID.value); //gets logged 2 times - right after Init = 0, after 1Second = 43
      console.log(props.randomInput);


     
      console.log(inputFromParent)
    });

    setTimeout(() => {
      userID.value = 43;
       inputFromParent = props.randomInput;
    }, 1000);

    return {
      inputText,
      updatedText,
      state,
      inputFromParent
    };
  },
};
</script>

<style lang="scss" scoped>
</style>