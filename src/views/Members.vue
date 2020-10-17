<template>
  <div class="member-container">
    <h1>{{ message }}</h1>
    <ul class="member-container__ul">
      <!--  :class="{'member-container__ul--finished':member.finished}" - class member.container__ul--finished is active as soon as member.finished is truthy -->
      <li
        v-for="(member, index) in members"
        :key="member.id"
        :class="{ 'member-container__ul--finished': member.finished }"
      >
        <input @click="toggleFinish(member)" type="checkbox" :checked="member.finished" />
        {{ ++index }} {{ member.name }}
      </li>
    </ul>
    <h3>{{counter}}</h3>
    <button @click="addMethod">Add</button>
    <Calculator/>
  </div>
</template>

<script>
import Calculator from "../components/Calculator";

export default {
  name: "Members",
  data: () => ({
    message: "WG-Mitglieder",
    members: [
      { id: 1, name: "Anthea", finished: false },
      { id: 2, name: "Paul", finished: false },
      { id: 3, name: "Eyleen", finished: false },
      { id: 4, name: "Paco", finished: false },
      { id: 5, name: "Civan", finished: false },
    ],
    counter: 0
  }),
  methods: {
      addMethod() {
          this.counter++
      },
      toggleFinish(member){
          member.finished = !member.finished;
      }
  },
  components: {
    Calculator
  }
    
};
</script>

<style lang="scss" scoped>
.member-container {
  max-width: 40%;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  &__ul {
    list-style-type: none;
    padding: 0;
    text-align: left;

    &--finished {
      text-decoration: line-through;
    }

    li {
      font-size: 20px;
      font-weight: 500;
    }
  }
}
</style>