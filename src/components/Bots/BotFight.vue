<template>
    <div class='fight-container'>
        <h2>Fighting Bots</h2>
        <div>
            <bot
            v-for="(eachBot,i) in fightBots"
            :key='i'
            :bot='eachBot'
            :removeFightBot='removeFightBot'
             />
        </div>
        <button @click='letsFight' >Fight</button>
    </div>
</template>

<script>
import Bot from './Bot';
export default {
  props: ['fightBots','letsFight','removeFightBot'],
  components: {
    Bot
  }
};
</script>

<style>
.fight-containter {
  height: 200px;
  width: 600px;
  background: darkorchid;
}
</style>
