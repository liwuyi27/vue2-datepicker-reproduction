### Source Code
``` html
<template>
  <div id="app">
    <label>time0</label>
    <date-picker type="time" :disabled-time="disabledTime0" v-model="time0"></date-picker>
    <label>time1</label>
    <date-picker type="time" :disabled-time="disabledTime1" v-model="time1"></date-picker>
  </div>
</template>
```
``` js
<script>
import DatePicker from 'vue2-datepicker';
import 'vue2-datepicker/index.css';
export default {
  components: { DatePicker },
  data() { 
    return { time0: '', time1: '' } 
  },
  methods: {
    disabledTime0(date) {
      const a = new Date();
      const b = new Date();
      a.setHours(2, 0, 0, '000'); // 02:00:00 00
      b.setHours(2, 30, 0, '000');
      date = new Date(date);
      if (a <= date && date <= b) {
        return false;
      } 
      return true;
    },
    disabledTime1(date) {
      const a = new Date();
      const b = new Date();
      a.setHours(2, 1, 0, '000'); // 02:01:00 000
      b.setHours(2, 30, 0, '000');
      date = new Date(date);
      if (a <= date && date <= b) {
        return false;
      } 
      return true;
    }
  }
}
</script>
```
