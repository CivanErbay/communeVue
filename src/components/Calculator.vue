<template>
    <div>

    </div>
</template>

<script>
    export default {
        name: "Calculator",
        methods: {
            add: function(a,b) {
                let result = a+b
                return result;
            }
        },
        mounted: function() {
            console.log(this.add(1,2))
        }
    }
</script>

<style lang="scss" scoped>

</style>