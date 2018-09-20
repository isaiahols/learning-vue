<template>
    <div class='each-bot'>
        <h3>{{bot.name}}</h3>
            <h5>Attack {{bot.attack}} </h5>
            <button 
            v-if='list'
            @click='editing("editAttack")' 
            >Edit Attack</button>
            <input 
            v-if='editAttack'  
            v-model='bot.attack'
             type="text">

            <h5>Health {{bot.health}} </h5>
            <button 
            v-if='list' 
            @click='editing("editHealth")' 
            >Edit Health</button>
            <input 
            v-if='editHealth'  
            v-model='bot.health'
             type="text">
            
            <button v-if='addFighters' @click='addFighters(bot)'>Add to Fight</button>
            <button 
                @click='receycle(index)'
                v-if='receycle'
                >Recycle</button>
            <button 
                @click='removeFightBot(index)'
                v-else
                >Remove</button>
    </div>
</template>

<script>
export default {
  data() {
    return {
      editAttack: false,
      editHealth: false,
      input: ''
    };
  },
  methods: {
    editing(what) {
      this[what] = !this[what];
    }
  },
  props: [
    'bot',
    'addFighters',
    'list',
    'index',
    'receycle',
    'removeFightBot',
    'edit'
  ]
};
</script>

<style>
.each-bot {
  min-width: 100px;
  min-height: 100px;
  background: lightblue;
  margin: 15px;
}
</style>

