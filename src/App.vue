<template>
  <div id="app">
    <source-code></source-code>
    <div class="wrapper">
      <div class="tip">
        when you click on the time0 input box, <br/>you will find that you
        <span class="work">can</span> select the time bettween
        <span class="bold">02:00:00 - 02:30:00.</span>
      </div>
      <div class="label">time0</div>
      <date-picker
        type="time"
        :disabled-time="disabledTime0"
        v-model="time0"
      ></date-picker>
      <div class="tip">
        when you click on the time1 input box, <br/>you will find that you
        <span class="do-not-work">can not</span> select the time bettween
        <span class="bold">02:01:00 - 02:30:00.</span>
      </div>
      <div class="label">time1</div>
      <date-picker
        type="time"
        :disabled-time="disabledTime1"
        v-model="time1"
      ></date-picker>
    </div>
  </div>
</template>

<script>
import DatePicker from "vue2-datepicker";
import "vue2-datepicker/index.css";
import SourceCode from "./source-code.md";

export default {
  name: "App",
  components: {
    DatePicker,
    SourceCode,
  },
  data() {
    return {
      time0: "",
      time1: "",
    };
  },
  methods: {
    disabledTime0(date) {
      const a = new Date();
      const b = new Date();
      // 02:00:00 00
      a.setHours(2, 0, 0, "000");
      b.setHours(2, 30, 0, "000");

      date = new Date(date);
      if (a <= date && date <= b) {
        return false;
      }
      return true;
    },
    disabledTime1(date) {
      const a = new Date();
      const b = new Date();
      // 02:01:00 000
      a.setHours(2, 1, 0, "000");
      b.setHours(2, 30, 0, "000");

      date = new Date(date);
      if (a <= date && date <= b) {
        return false;
      }
      return true;
    },
  },
};
</script>

<style lang="less" scoped>
#app {
  display: flex;
  .wrapper {
    margin-left: 100px;
    margin-top: 100px;
    .tip {
      margin-top: 100px;
    }
    .label {
      margin: 10px 0 6px;
      font-weight: bold;
    }
    .work {
      font-weight: bold;
      color: green;
    }

    .do-not-work {
      font-weight: bold;
      color: red;
    }

    .bold {
      font-weight: bold;
    }
  }
}
</style>

