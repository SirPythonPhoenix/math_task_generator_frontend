<template>
  <div class="page">

    <div class="task">
     <div class="task-head">
      AUFGABE 1
     </div>
     <div class="task-body">
      f(x)= 2x-2
     </div>
    </div>  

    <div class="task">
     <div class="task-head">
      AUFGABE 2
     </div>
     <div class="task-body">
      f(x)= 2x-2
     </div>
    </div>  

    <div class="task">
     <div class="task-head">
      AUFGABE 3
     </div>
     <div class="task-body">
      f(x)= 2x-2
     </div>
    </div>  

    <div class="task">
     <div class="task-head">
      AUFGABE 3
     </div>
     <div class="task-body">
      f(x)= 2x-2
     </div>
    </div>  

    <div class="task">
     <div class="task-head">
      AUFGABE 3
     </div>
     <div class="task-body">
      f(x)= 2x-2
     </div>
    </div>  

    <div class="footer">
      <label class="x">&#10005;</label>
      <div class="settings-head">
        <button class="button2">Einstellungen &#9660;</button>
        <button class="button1">Aufgaben generieren</button>
      </div>
      <br>
      <div class="settings-body">
        <p>Anzahl generierter Aufgaben:
          <input class="small-input" type="number" max="99" min="1" value="5">
        </p>
        <hr>
        <p>Schwierigkeit:
          <input>
        </p>
        <hr>
        <p>Grad der Funktion:
          <input class="small-input" type="number" max="9" min="1" value="1">
          bis
          <input class="small-input" type="number" max="9" min="1" value="3">
        </p>
        <hr>
        <p>Parameter-Wertebereich:
          <input class="medium-input" type="number" max="999" min="0" value="0">
          bis
          <input class="medium-input" type="number" max="999" min="0" value="20">
        </p>
      </div>
    </div>

  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {}
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

.task {
  margin: auto;
  background-color: white;
  max-width: 50%;
  box-shadow: 0px 0px 14px rgba(0, 0, 0, 0.2);
  margin-bottom: 100px;
}

.task-head {
  background-color: #8EA7E9;
  color: white;
  padding: 15px 0;
  font-weight: bold;
  letter-spacing: 1px;
}

.task-body {
  padding: 40px 20px;
}

.x {
  float:right;
  margin: 28px 40px;
  font-size: xx-large;
  cursor: pointer;
}

</style>
