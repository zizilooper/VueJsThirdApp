<template>
  <div id="wrapper">
    <div class="card">
      <h1>you</h1>
      <v-col cols="4">
        <v-progress-linear :value="you.length * 10"></v-progress-linear>
      </v-col>
    </div>
    <div class="card">
      <h1>mon</h1>
      <v-col cols="4">
        <v-progress-linear :value="mons.length * 10"></v-progress-linear>
      </v-col>
    </div>
    <button class="btn" @click="startGame">start</button>
    <div class="card" v-show="!show" v-if="show ? show : !show">
      <span @click="selectedComponent = 'Attack'"></span>
      <span @click="selectedComponent = 'SpetialAtt'"></span>
      <span @click="selectedComponent = 'Heal'"></span>
      {{ selectedComponent }}
      <component :is="selectedComponent"></component>
      <Results :monArr="mons" :youArr="you"></Results>
      <button class="btn" @click="startGame">Give up</button>
      <Attack
        :monArr="mons"
        :youArr="you"
        class="btn"
        @AttYou="youArr = $event"
      ></Attack>
      <Spetial-att
        :monArr="mons"
        :youArr="you"
        @AttYou="youArr = $event"
        class="btn"
      ></Spetial-att>
      <Heal
        :monArr="mons"
        :youArr="you"
        class="btn"
        @AttYou="youArr = $event"
      ></Heal>
    </div>
  </div>
</template>

<script>
import Attack from "../components/Attack.vue";
import SpetialAtt from "../components/specialAtt.vue";
import Heal from "../components/Heal.vue";
import Results from "../components/Results.vue";

export default {
  name: "Home",
  components: {
    Attack: Attack,
    "Spetial-att": SpetialAtt,
    Heal: Heal,
    Results: Results,
  },
  data() {
    return {
      you: [1, 1, 1, 1, 1, 1, 1, 1, 1, 1],
      mons: [1, 1, 1, 1, 1, 1, 1, 1, 1, 1],
      selectedComponent: "",
      show: true,
    };
  },
  methods: {
    startGame() {
      this.show = !this.show;
      console.log(this.show);
    },
  },
};
</script>

<style>
#wrapper {
  width: 800px;
  height: 400px;
  margin: auto;
  padding: 0;
  background-color: rgb(236, 233, 241);
}
.card {
  width: 100%;
  display: inline-flex;
}
.btn {
  color: blueviolet;
  background: rgb(34, 18, 6);
  width: 90px;
  border-radius: 5px;
  margin: auto;
}

h1 {
  margin-left: 10px;
}
</style>
