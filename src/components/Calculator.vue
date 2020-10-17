<template>
  <div>
    <h4>{{ valueTemp }}</h4>
  </div>
  <div></div>
</template>

<script>
export default {
  name: "Calculator",
  data: () => ({
    valueTemp: 0,
  }),

  methods: {
    add: function (a, b) {
      let result = a + b;
      return result;
    },
  },

  //MOUNTED Example & Console.log Example
  mounted: function () {
    console.log(this.add(1, 2)),
    this.valueTemp = this.add(4, 5);  
  },
};
</script>

<style lang="scss" scoped>
</style>