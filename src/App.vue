<template>
  <div class="page">

    <div class="task-root" v-for="task in tasks" v-bind:key="task">
     <div class="task-head">
      AUFGABE {{ task.number }}
     </div>
     <div class="task-body">
       {{ task["task"] }}
     </div>
    </div>

    <p v-if="tasksEmpty">Hier befinden sich noch keine Aufgaben.</p>

    <div class="footer" v-if="footer_visible">
      <label class="x" v-on:click="toggleFooter">&#10005;</label>
      <div class="settings-head">
        <button class="button2" v-on:click="toggleSettings">Einstellungen {{ settings_visible ? "&#9660;" : "&#9650;" }}</button>
        <button class="button1" v-on:click="generateTasks">Aufgaben generieren</button>
      </div>
      <br>
      <div class="settings-body" v-if="settings_visible">
        <p>Anzahl generierter Aufgaben:
          <input class="small-input" type="number" max="10" min="1" v-model="number">
        </p>
        <hr>
        <p>Grad der Funktion:
          <input class="small-input" type="number" v-bind:max="settings.grade_max" min="1" v-model="settings['grade_min']">
          bis
          <input class="small-input" type="number" max="9" v-bind:min="settings.grade_min" v-model="settings['grade_max']">
        </p>
        <hr>
        <p>Parameter-Wertebereich:
          <input class="medium-input" type="number" v-bind:max="settings.param_max" v-model="settings['param_min']">
          bis
          <input class="medium-input" type="number" v-bind:min="settings.param_min" v-model="settings['param_max']">
        </p>
      </div>
    </div>

  </div>
</template>

<script>

export default {
  name: 'App',
  components: {},
  data() {
    return {
      tasks: [],
      settings_visible: true,
      footer_visible: true,
      number: 3,
      settings: {
        grade_min: 2,
        grade_max: 3,
        param_min: -4,
        param_max: 5,
      }
    }
  },
  computed: {
    tasksEmpty() {
      return this.tasks.length === 0
    }
  },
  methods: {
    toggleSettings() {
      this.settings_visible = !this.settings_visible
    },
    toggleFooter() {
      this.footer_visible = !this.footer_visible
    },
    async generateTasks() {
      this.tasks = []
      for (let i=1; i<=this.number; i++) {
        const response = await fetch(
            "http://rdm.spdns.de:25566/generate/function",
            {
              method: 'POST',
              headers: {
                'Content-Type': 'application/json;charset=utf-8'
              },
              body: JSON.stringify(this.settings)
            },
        )
        let new_task = await response.json()
        new_task["number"] = i
        this.tasks.push(new_task)
      }
    }
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
  background-color: white;
}

hr {
  color:#7286D3;
}

.small-input {
  width: 45px;
}

.medium-input {
  width: 65px;
}

.button1 {
  background-color:#7286D3;
  border-color:#7286D3;
  border-style: solid;
  color: white;
  border-radius: 40px;
  font-weight: bold;
  padding: 15px 80px;
  font-size:larger;
  margin: 20px 50px;
  transition: color 0.2s, background-color 0.2s, border-color 0.2s;
}

.button1:hover {
  background-color: #5e6ead;
  border-color: #5e6ead;
}

.button2 {
  background-color: rgba(0, 0, 0, 0);
  border-color: #7286D3;
  border-width: 2px;
  border-style: solid;
  color:#7286D3;
  border-radius: 40px;
  font-weight: bold;
  padding: 15px 80px;
  font-size:larger;
  margin: 20px 50px;
  transition: color 0.2s, background-color 0.2s, border-color 0.2s;
}

.button1:active {
  opacity: 0.8;
}

.button2:hover {
  color: white;
  background-color:#5e6ead;
  border-color: #5e6ead;
}

.button2:active {
  opacity: 0.8;
}

.footer {
  background-color: white;
  max-width: 100%;
  height: 380px;
  float: bottom;
  box-shadow: 0 -8px 10px rgba(0, 0, 0, 0.15);
}

.settings-head {
  margin: auto;
  max-width: 50%;
  text-align: center;
}

.settings-body {
  margin: auto;
  max-width: 50%;
  text-align: left;
}

.task-root {
  margin: auto auto 100px;
  background-color: white;
  max-width: 50%;
  box-shadow: 0 0 14px rgba(0, 0, 0, 0.2);
}

.task-head {
  background-color: #8EA7E9;
  color: white;
  padding: 15px 0;
  font-weight: bold;
  letter-spacing: 1px;
}

.task-body {
  padding: 40px 120px;
}

.x {
  float:right;
  margin: 28px 40px;
  font-size: xx-large;
  cursor: pointer;
}

</style>
