<template>
  <br>
  <h1>Parameteraufgaben</h1>
  <br><br>
  <button id="task-button" v-on:click="get_task">Aufgabe generieren</button>
  <br><br><br>
  <div class="task-container" v-for="task in tasks" v-bind:key="task">
      <p>{{ task.math_task }}</p>
      <label id="show-solved"><u>Lösung anzeigen</u></label>
      <p v-if="task.show_solution">{{ task.math_solution }}</p>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data() {
    return {
      tasks: [
        {
          "math_task": "",
          "math_solution": "",
          "show_solution": false
        }
      ]
    }
  },
  methods: {
    async get_task() {
        let task = document.getElementById("task")
        let solution = document.getElementById("solution")
        let response = await fetch("http://localhost:8000/generate/function/")
        let json_string = await response.json()
        task.innerText = json_string["task"]
        solution.innerText = json_string["function_solved"]
    },
    async show_solution() {
        let solution = document.getElementById("solution")
        solution.classList.remove("hidden")
    },
  },
  async mounted() {
    await this.get_task()
        let task_button = document.getElementById("task-button")
        task_button.addEventListener("click", this.get_task)
        let show_solved = document.getElementById("show-solved")
        show_solved.addEventListener("click", this.show_solution)
  }
}



</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

body {
    margin: 0;
    padding: 0;
    background: #121212;
    color: #FFFFFF;
    text-align: center;
    font-family: Arial, sans-serif;
    line-height: 30px
}

h1 {
    margin: 0;
    padding: 0;
}

button {
    background-color: #3700B3;
    border-style: solid;
    color: #FFFFFF;
    padding: 15px 32px;
    text-align: center;
    display: inline-block;
    font-size: 16px;
    cursor: pointer;
    border-radius: 8px;
    border-width: 1px;
    border-color: #FFFFFF;
}

.task-container {
    border-style: solid;
    border-width: 2px;
    border-color: #FFFFFF;
    margin-left: 26%;
    margin-right: 26%;
    padding: 8px;
}

#show-solved {
    color: darkgray;
    cursor: pointer;
}

.hidden {
    display: none;
}

#solution {
    font-size: 20px
}

</style>
