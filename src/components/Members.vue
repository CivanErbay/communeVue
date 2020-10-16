<template>
    <div class="member-container">
        {{message}}
        <ul class="member-container__ul">
            <li v-for="member in members" :key="member">{{member}}</li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: "Members",
        data: () => ({
            message: "Unsere aktuellen WG-Mitglieder",
            members: [
                "Anthea",
                "Paul",
                "Eyleen",
                "Paco",
                "Civan"
            ]
        })
    }
</script>

<style lang="scss" scoped>
    .member-container {
        &__ul{
                list-style-type: none;
                padding: 0;
        }
    }
</style>