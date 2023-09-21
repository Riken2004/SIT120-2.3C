<template>
  <div>
    <h2>Racing Game Details</h2>
    <p>Racer 1: {{ racer1 }}</p>
    <p>Racer 2: {{ racer2 }}</p>
    <p>Racer 3: {{ racer3 }}</p>
    <p v-html="raceDescription"></p>
    <p :id="trackId"></p>
    <p>Race Date: {{ raceDate }}</p>
    <button @click="startRace">Start Race</button>

    <h2>Race Results</h2>
    <p>Winner: {{ winner }}</p>
    <p>Finish Time: {{ raceTime }}</p>

    <h2>Racer List</h2>
    <ul>
      <li v-for="racer in racers" :key="racer.id">{{ racer.name }}</li>
    </ul>

    <button @click="recordVictory">Record Victory</button>
    <button @click="recordDisqualification">Record Disqualification</button>

    <h2>Enter Race Details</h2>
    <label for="finishTime">Finish Time:</label>
    <input type="text" v-model="raceTime" />
    <br />
    <label for="disqualified">Disqualified:</label>
    <input type="checkbox" v-model="disqualified" />
    <label for="raceSummary">Race Summary:</label>
    <textarea v-model="raceSummary"></textarea>

    <h2>Racing Game Components</h2>
    <race-summary :summary="raceSummary"></race-summary>
    <player-stats @victory="handleVictoryEvent"></player-stats>
    <slot-example></slot-example>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const racer1 = ref('Riken');
const racer2 = ref('Ansh');
const racer3 = ref('Jainam')
const raceDescription = '<p>Grand Prix 2024!</p>';
const trackId = 'race-track';
const raceDate = '19/01/2024';

const startRace = () => {
  alert('Race has started!');
};

const winner = ref('');
const raceTime = ref('');
const disqualified = ref(false);

const racers = ref([
  { id: 1, name: 'Riken' },
  { id: 2, name: 'Ansh' },
  { id: 3, name: 'Jainam' },
]);

const recordVictory = () => {
  winner.value = 'Riken';
};

const recordDisqualification = () => {
  disqualified.value = true;
};

const raceSummary = ref('');

const handleVictoryEvent = (data) => {
  // Handle victory event
};
</script>

<style>

.racing-game-details {
  font-family: sans-serif;
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  background-color: #f7f7f7;
  border: 1px solid #ccc;
  border-radius: 10px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

h2 {
  font-size: 2rem;
  margin-top: 0;
}

p {
  margin: 0;
}

button {
  background-color: green;
  color: white;
  padding: 10px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.2s ease;
}

button:hover {
  background-color: #00FF00;
}

.racer-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.racer-list li {
  display: inline-block;
  padding: 10px;
  margin: 0 10px;
  border: 1px solid black;
  border-radius: 5px;
}

.enter-race-details {
  margin-top: 20px;
}

.enter-race-details label {
  display: block;
  margin-bottom: 10px;
}

.enter-race-details input,
.enter-race-details textarea {
  width: 100%;
  padding: 10px;
  border: 1px solid black;
  border-radius: 5px;
}

.enter-race-details textarea {
  height: 100px;
}

/* Race Game Components */

.race-summary {
  width: 50%;
  max-width: 200px;
  margin: 10px auto;
  border: 10px solid #00FF00;
}

.player-stats {
  width: 100%;
  max-width: 600px;
  margin: 0 auto;
  background-color: green;
  color: white;
}

/* Custom Button Styles */
button.start-race {
  background-color: green;
}

button.record-disqualification {
  background-color: red;
}

</style>
