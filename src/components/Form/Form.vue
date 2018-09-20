<template>
    <div class='bot-form'>
        <h3>Creating Table</h3>
        <h5>Name: <input v-model="buildBot.name" type="text"></h5>
        <h5>Attack Value: <input v-model="buildBot.attack" type="text"></h5>
        <h5>Health Value: <input v-model="buildBot.health" type="text"></h5>
        <button @click='addBot()' >Build</button>
    </div>
</template>

<script>
export default {
  data() {
    return {
      buildingBot: {
        name: '',
        attack: '',
        health: ''
      }
    };
  },
  methods:{
  },
  props: ['buildBot','addBot']
};
</script>

<style>
.bot-form {
  height: 45vh;
  width: 300px;
  background: lightslategray;
  display: flex;
  flex-direction: column;
  align-content: center;
  justify-content: space-around;
  margin: 50px;
}
</style>
