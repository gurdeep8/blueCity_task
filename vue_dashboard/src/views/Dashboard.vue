<template>
  <div class="team">
    <v-container fluid>
      <v-layout class="d-flex justify-center" style="height: 100vh;">
        <v-progress-circular color="primary" class="align-self-center" v-if="!loaded" :height="5" :indeterminate="true"></v-progress-circular>
        <LineChart class="col-md-8" v-if="loaded" :chartData="chartData" :plot="plotting"></LineChart>
      </v-layout>
    </v-container>
  </div>
</template>

<script>
import LineChart from "@/components/LineChart";
const URL = "ws://35.183.23.210:8000/b";
export default {
  data() {
    return {
      chartData: "",
      plotting: "",
      loaded: false,
      connection: null,
      socketData: '',
    };
  },
  components: {
    LineChart,
  },
  watch: {
    socketData (newVal, oldVal) {
      if (newVal !== oldVal) {
        this.getSocketData()
      }
    }
  },
  methods: {
    /* eslint-disable */
    getSocketData () {
      this.connection = new WebSocket(URL);
      console.log("Starting connection to the web socket");

      this.connection.onopen = function (event) {
        console.log("connected");
      }
      this.connection.onmessage = function (event) {
        var sensors = JSON.parse(event.data);
        this.socketData = sensors.sensor
        // this.json = JSON.parse(json)
        console.log(this.socketData);
      };
     
      
    },
  },
  mounted() {
    this.$http
      .get("https://api.bluecitytechnology.com/s/smp/")
      .then((response) => {
        const info = response.data;
        this.chartData = response.data;
        this.plottting = response.data;
        this.loaded = true;
      });

    // webSocket
    this.getSocketData()
  },
};
</script>
