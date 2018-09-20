<template>
    <div>
        <h3>Available Bots</h3>
        <div id='bot-grid'>
        <bot 
        v-for='(bot, i) in botList'
        :key='i'
        :bot='bot'
        :addFighters='addFighters'
        :list='true'
        :index='i'
        :receycle='receycle'
        :edit='editHealthAttack'
        />
        </div>
    </div>
</template>

<script>
import Bot from './Bot';

export default {
  props: ['botList','addFighters','receycle','editHealthAttack'],
  components: {
      Bot
  }
};
</script>

<style>
#bot-grid {
  width: 80%;
  height: 80%;
  background: darkgreen;
  display: flex;
  align-items: center;
}
</style>

