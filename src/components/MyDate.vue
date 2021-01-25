<template>
  <div>
    <input type="date"
      v-bind="date"
      v-on:input="date = strToDate($event.target.value)"  
    />
    <p>{{ date }}</p>
    <p>A type of the value is: {{ function () { return typeof date;}() }}</p>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
class MyDate extends Vue {
  @Prop() private date!: Date;

  private strToDate(str: string): Date {
    return new Date(str);
  }
}

export default MyDate;
</script>
