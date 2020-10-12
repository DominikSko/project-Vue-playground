<template>
  <div id="app">
    <header>
      <h1>Vue Course Goals</h1>
    </header>
    <section id="user-goal">
      <h2>My Course Goal</h2>
      <!-- <p v-html="outputGoal()"></p> -->
      <p>{{ outputGoal() }}</p>
      <p>Learn more <a v-bind:href="vueLink">about Vue</a>.</p>
    </section>
    <myName />
    <events />
    <TaskTwo />
    <VueStyle />
    <VueStyle2 />
    <Tasks />
  </div>
</template>

<script>
import myName from './components/myName.vue'
import events from './components/events.vue'
import TaskTwo from './components/TaskTwo.vue'
import VueStyle from './components/VueStyle.vue'
import VueStyle2 from './components/VueStyle2.vue'
import Tasks from './components/tasks/Tasks.vue'

export default {
  name: 'App',
  components: {
    myName,
    events,
    TaskTwo,
    VueStyle,
    VueStyle2,
    Tasks
  },
  data() {
    return {
      courseGoalA: 'Finish the course and learn Vue!',
      courseGoalB: 'Master Vue and build amazing apps!',
      vueLink: 'https://vuejs.org/'
    };
  },
  methods: {
    outputGoal() {
      const randomNumber = Math.random();
      if (randomNumber < 0.5) {
        return this.courseGoalA;
      } else {
        return this.courseGoalB;
      }
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: 'Jost', sans-serif;
}

body {
  margin: 0;
}

header {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  background-color: #4fc08d;
  color: white;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#user-goal {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#user-goal h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: #4fc08d;
  margin: 0 0 1rem 0;
}

#user-goal p {
  font-size: 1.25rem;
  font-weight: bold;
  border: 1px solid #4fc08d;
  background-color: #4fc08d;
  color: white;
  padding: 0.5rem;
  border-radius: 25px;
}

#user-goal input {
  font: inherit;
  border: 1px solid #ccc;
}

#user-goal input:focus {
  outline: none;
  border-color: #1b995e;
  background-color: #d7fdeb;
}

#user-goal button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}

#user-goal button:hover,
#user-goal button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}

</style>
