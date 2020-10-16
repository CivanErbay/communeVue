<template>
  <div class="member-container">
    {{ message }}
    <ul class="member-container__ul">
      <li v-for="(member, index) in members" :key="member">
        {{ ++index }} {{ member }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Members",
  data: () => ({
    message: "Unsere aktuellen WG-Mitglieder",
    members: ["Anthea", "Paul", "Eyleen", "Paco", "Civan"],
  }),
};
</script>

<style lang="scss" scoped>
.member-container {
    max-width: 20%;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    align-items: center;
  &__ul {
    
    list-style-type: none;
    padding: 0;
    
    text-align: left;
  }
}
</style>