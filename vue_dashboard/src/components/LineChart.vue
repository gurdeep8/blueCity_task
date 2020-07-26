<script>
import { Line } from "vue-chartjs";

export default {
  extends: Line,
  data() {
    return {
      serialData: [],
    };
  },
  props: {
    chartData: {
      type: Object,
    },
    plot: {
      type: String,
    },
  },
  mounted() {
    /* eslint-disable */

    // console.log("yy", this.chartData);
    for (let yPlot of this.chartData.plot.y) {
      let obj = {
        name: yPlot,
        data: this.chart_data(this.chartData.data, yPlot, this.chartData.plot),
      };
      this.serialData.push(obj);
    }
    // console.log("axis", this.serialData);
    this.createChart();
  },
  methods: {
    chart_data(data, yAxis, plot) {
      let arr = [];

      for (let val of plot.x) {
        let timeObj = data[val];
        let flag = false;
        for (let axis in timeObj) {
          if (axis === yAxis) {
            arr.push(timeObj[axis]);
            flag = true;
          }
        }
        if (!flag) arr.push(0);
      }
      return arr;
    },
    createChart() {
      this.renderChart(
        {
          labels: this.chartData.plot.x,
          datasets: [
            {
              label: this.serialData[0].name,
              data: this.serialData[0].data,
              fill: false,
              borderColor: "#2196F3",
              backgroundColor: "#2196F3",
              borderWidth: 1,
            },
            {
              label: this.serialData[1].name,
              data: this.serialData[1].data,
              fill: false,
              borderColor: "#009688",
              backgroundColor: "#009688",
              borderWidth: 1,
            },
            {
              label: this.serialData[2].name,
              data: this.serialData[2].data,
              fill: false,
              borderColor: "#B0BEC5",
              backgroundColor: "#B0BEC5",
              borderWidth: 1,
            },
            {
              label: this.serialData[3].name,
              data: this.serialData[3].data,
              fill: false,
              borderColor: "#81D4FA",
              backgroundColor: "#81D4FA",
              borderWidth: 1,
            },
            {
              label: this.serialData[4].name,
              data: this.serialData[4].data,
              fill: false,
              borderColor: "#3F51B5",
              backgroundColor: "#3F51B5",
              borderWidth: 1,
            },
          ],
        },
        
      );
    },
  },
};
</script>