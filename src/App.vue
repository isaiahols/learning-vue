<template>
  <div id="app">
    <div>
    <h1>Welcome to Bot Wars</h1>
    <!-- Nav BAR -->
    <div id="nav-bar">
      <button @click='changeView(false)' >Build Bot</button>
      <h3>Select Build or Figh</h3>
      <button @click='changeView(true)' >Fight Bots</button>
    </div>
    <!-- THis is the bot list Page -->
    <section v-if='showBotsFight'>
      <h2>Lets Fight!</h2>
      <div>
        <bot-fight 
        :fightBots='fightBots'
        :letsFight='letsFight'
        :removeFightBot='removeFightBot'
        />
      </div>
      <div>
        <all-bots
          :botList='botList'
          :addFighters='addFightBot'
          :receycle='receycle'
          :editHealthAttack='editHealthAttack'
         />
      </div>
    </section>
    <!-- This is the bot form Page -->
    <section v-else id='create-bot'>
      <h2>Lets Build a Bot</h2>

      <bot-form 
      :buildBot='buildingBot'
      :addBot='createBot'
      />
    </section>
    </div>


  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue';
import Form from './components/Form/Form.vue';
import BotList from './components/Bots/BotList';
import BotFight from './components/Bots/BotFight';

export default {
  name: 'app',
  data() {
    return {
      showBotsFight: false,
      buildingBot: {
        name: '',
        attack: '',
        health: ''
      },
      botList: [
        {
          name: '1',
          attack: '2',
          health: '3'
        },
        {
          name: '3',
          attack: '2',
          health: '1'
        },
        {
          name: '2',
          attack: '2',
          health: '2'
        }
      ],
      fightBots: []
    };
  },
  methods: {
    changeView(val) {
      this.showBotsFight = val;
    },
    createBot() {
      this.botList.push(this.buildingBot);
      this.buildingBot = {
        name: '',
        attack: '',
        health: ''
      };
    },
    receycle(index) {
      this.botList.splice(index, 1);
    },
    editHealthAttack(index, what, val) {
      this.botList[index][what] = val;
    },
    addFightBot(bot) {
      if (this.fightBots.length < 2) {
        this.fightBots.push(bot);
      } else {
        alert('Fight List is already full');
      }
    },
    removeFightBot(index) {
      this.fightBots.splice(index, 1);
    },
    letsFight() {
      if (this.fightBots.length === 2) {
        let win = Math.random() * 10;
        let winner;
        const { fightBots } = this;
        let f1 =fightBots[0],
            f2 =fightBots[1];

        if (f1.attack - f2.health>0) {
          // if (win < 5) {
          winner = f2;
        } else {
          winner = f1;
        }
        alert(`The winner is ${winner.name}`);
        this.fightBots = [];
      } else {
        alert('Add Another Bot');
      }
    }
  },
  components: {
    // HelloWorld
    BotForm: Form,
    AllBots: BotList,
    BotFight
  }
};
</script>



<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background: darkslategrey;
  color: #2c3e50;
  /* margin-top: 60px; */
  margin: 0px;
  padding: 0px;
  height: 100vh;
}

#nav-bar {
  display: flex;
  align-content: center;
  justify-content: space-around;
  height: 65px;
  background: lightseagreen;
  padding: 10px;
}

#create-bot {
  width: 100vw;
  display: flex;
  flex-direction: column;
  align-content: center;
  justify-content: center;
  padding: 0 50px;
}
</style>
