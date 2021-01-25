<template>
  <div id="app">
    <div class="container">
      <h3>Example1: A type of value is string</h3>
      <input type="date" v-model="date1" />
      <p>Time: {{ date1 }}</p>
      <p>A type of the value is: {{ function () { return typeof date1; }() }}</p>
    </div>
    <div class="container">
      <h3>Example2: Treat a value as a Date Object</h3>
      <input type="date"
        v-bind:value="date2"
        v-on:input="date2 = strToDate($event.target.value)"
      />
      <p>{{ date2 }}</p>
      <p>A type of the value is: {{ function () { return typeof date2;}() }}</p>
    </div>
    <div class="container">
      <h3>MyDate: A component of treating a value as a Date Object.</h3>
      <my-date :date="date3" />
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import MyDate from './components/MyDate.vue';

@Component({
  components: {
    MyDate,
  },
})
export default class App extends Vue {
  private date1: Date = new Date();
  private date2: Date = new Date();
  private date3: Date = new Date();

  strToDate(date: string): Date {
    return new Date(date);
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

.container {
  min-width: 200px;
  min-height: 300px;
  border: solid;
  border-color: black;
  background-color: cadetblue;
  margin-bottom: 10px;
}
</style>
