<template>
  <div>
    <input type="date"
      v-bind:value="dateToStr(date)"
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

  private dateToStr(date: Date): string {
    const year = date.getFullYear();
    const month = date.getMonth() + 1 < 9 ? `0${date.getMonth() + 1}` : `${date.getMonth() + 1}`;
    const day = date.getDate() < 9 ? `0${date.getDate()}` : `${date.getDate()}`;
    const strDate = `${year}-${month}-${day}`;
    return strDate;
  }
}

export default MyDate;
</script>
