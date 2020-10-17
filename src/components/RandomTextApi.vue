<template>
    <div>
        <input v-model="inputText" type="text">
        <p>{{inputText}}</p>
        <button @click="updatedText = inputText + ' Hello'">Update</button>
        <p>{{updatedText}}</p>
        <p>{{displayText}}</p>
        <p v-for="text in state.data" :key="text"> {{text.join()}} <!-- .join() removes square brackets from array -->
        </p>
        <p>{{state.data[0]}}</p>
    </div>
</template>

<script>
    import { ref, watchEffect, reactive} from "vue";
export default {

    name:"RandomTextApi",
    setup () {
        const inputText = ref(null)
        const updatedText = ref(null)   //normal Variable
        const state = reactive({ data: []})  //This is reactive Variable or lets say a "state"-Variable
 

        watchEffect(() => {             //like useEffect I guess
            if(inputText.value) {
            fetch(`https://baconipsum.com/api/?type=all-meat&paras=2&start-with-lorem=1`)
            .then((response) => response.json())
            .then((data) => {
               state.data.push(data)
            })
            }
        })
        return {
            inputText,
            updatedText,
            state,
      
        }
    },

}
</script>

<style lang="scss" scoped>

</style>