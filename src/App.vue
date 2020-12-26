<template>
  <div id="app">
    <DBButtons
      v-on:onclickPersonalData="setStr('PersonalData')"
      v-on:onclickEmployees="setStr('Employees')"
      v-on:onclickPositions="setStr('Positions')"
      v-on:onclickBusinessTrips="setStr('BusinessTrips')"
    />
    <Table
      v-bind:dbData="dbData"
      v-bind:dbName="database"
    />
    <Pagination
      v-on:onClickLeft="minusOffset(5)"
      v-on:onClickRight="plusOffset(5)"
    />
  </div>
</template>

<script>
import DBButtons from '@/components/DBButtons'
import Table from '@/components/Table'
import Pagination from '@/components/Pagination'
export default {
  name: 'App',
  data() {
    return {
      dbData: [],
      resquestStr: "",
      database: "",
      offset: 0
    }
  },
  components: {
    DBButtons,
    Table,
    Pagination
  },
  methods: {
    setStr(title) {
      this.database = title;
      this.reloadStr();
      this.request();
    },
    plusOffset(offset) {
      if (this.dbData.length >= offset) {
        this.offset += offset;
        this.reloadStr();
        this.request();
      }
    },
    minusOffset(offset) {
      if (this.offset >= offset) {
        this.offset -= offset;
        this.reloadStr();
        this.request();
      }
    },
    reloadStr() {
      this.resquestStr = `http://localhost:5000/api/${this.database}?count=5&offset=${this.offset}`;
    },
    async request() {
      const response = await fetch(this.resquestStr);
      const json = await response.json()
      this.dbData = json;
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
</style>
