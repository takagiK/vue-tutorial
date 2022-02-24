<template>
  <div class="testChart">
    <br /><br /><br />
    <h2>{{ mess }}</h2>

    <div class="graph">
      <line-chart :chartData="line" :options="line_opitions" />
      <button @click="updateLineData()">line Update</button>
    </div>
    <div class="graph">
      <line-chart :chartData="surface_line" />
      <button @click="updateSurfaceLineData()">pie Update</button>
    </div>

    <div class="graph">
      <bar-chart :chartData="bar" />
      <button @click="updateBarData()">bar Update</button>
    </div>
    <div class="graph">
      <bar-chart :chartData="bar_line" />
      <button @click="updateBarlineData()">bar_line Update</button>
    </div>

    <div class="graph">
      <pie-chart :chartData="pie" />
      <button @click="updatePieData()">pie Update</button>
    </div>

    <div class="graph">
      <doughnut-chart :chartData="doughnut" :options="doughnut_options" />
      <button @click="updateDoughnutData()">doughnut Update</button>
    </div>

    <div class="graph">
      <bubble-chart :chartData="bubble" />
      <button @click="updateBubbleData()">bubble Update</button>
    </div>

    <div class="graph">
      <b-input-group prepend="Label" class="mt-3">
        <b-form-input v-model="original_prop_data.label"></b-form-input>
      </b-input-group>
      <b-input-group prepend="Color" class="mt-3">
        <b-form-input
          v-model="original_prop_data.backgroundColor01.red"
        ></b-form-input>
        <b-form-input
          v-model="original_prop_data.backgroundColor01.green"
        ></b-form-input>
        <b-form-input
          v-model="original_prop_data.backgroundColor01.blue"
        ></b-form-input>
        <input
          type="color"
          v-model="original_prop_data.backgroundColor"
          class="mt-3"
        />
      </b-input-group>
      <b-input-group prepend="0" append="255" class="mt-3">
        <b-form-input
          type="range"
          min="0"
          max="255"
          v-model="original_prop_data.backgroundColor01.red"
        ></b-form-input>
        <b-form-input
          type="range"
          min="0"
          max="255"
          v-model="original_prop_data.backgroundColor01.green"
        ></b-form-input>
        <b-form-input
          type="range"
          min="0"
          max="255"
          v-model="original_prop_data.backgroundColor01.blue"
        ></b-form-input>
      </b-input-group>
      <br />
      <button @click="updateOriginalLineData()">bar_line Update</button>
      <div class="graph">
        <bar-chart :chartData="original_datasets" />
      </div>
    </div>
  </div>
</template>

<style>
.testChart {
  display: flex;
  flex-wrap: wrap;
}
.graph {
  max-width: 400px;
  margin: 10%;
  padding: auto;
}
</style>
 
 
<script>
import BarChart from "@/components/ChartBar.vue";
import LineChart from "@/components/ChartLine.vue";
import PieChart from "@/components/ChartPie.vue";
import DoughnutChart from "@/components/ChartDoughnut.vue";
import BubbleChart from "@/components/ChartBubble.vue";

export default {
  name: "testChart",
  components: {
    // RandomLineChart,
    BarChart,
    LineChart,
    PieChart,
    DoughnutChart,
    BubbleChart,
  },
  // =====================================================
  data() {
    return {
      mess: "Chart.js Tutorial",
      // ChartBar
      bar: {},
      bar_opitions: {},

      bar_line: {},

      // ChartLine
      line: {},
      line_opitions: {},
      // ChartPie
      pie: {},
      pie_opitions: {},

      // surface_line
      surface_line: {},

      // Doughnut
      doughnut: {},
      doughnut_options: {},

      // BubbleChart
      bubble: {},

      // original graph
      original_datasets: {
        labels: [
          "January",
          "February",
          "March",
          "April",
          "May",
          "June",
          "July",
          "August",
          "September",
          "October",
          "November",
          "December",
        ],
        datasets: [
          {
            label: "",
            data: [
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
            ],
            backgroundColor: "#000000",
          },
        ],
      },
      original_prop_data: {
        label: "",
        backgroundColor: "",
        backgroundColor01: {
          red: 0,
          green: 0,
          blue: 0,
        },
      },
    };
  },
  // =====================================================
  mounted() {
    this.updateBarData();
    this.updateLineData();
    this.updateBarlineData();
    this.updatePieData();
    this.updateDoughnutData();
    this.updateSurfaceLineData();
    this.updateBubbleData();
  },
  // =====================================================
  methods: {
    // ************************************
    updateBarData() {
      this.bar = {
        labels: [
          "January",
          "February",
          "March",
          "April",
          "May",
          "June",
          "July",
          "August",
          "September",
          "October",
          "November",
          "December",
        ],
        datasets: [
          {
            label: "Count",
            data: [
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
            ],
            backgroundColor: "rgba(255, 99, 132, 0.8)",
          },
        ],
      };
    }, // ************************************
    updateBarlineData() {
      this.bar_line = {
        labels: [
          "January",
          "February",
          "March",
          "April",
          "May",
          "June",
          "July",
          "August",
          "September",
          "October",
          "November",
          "December",
        ],
        datasets: [
          {
            type: "line",
            label: "予算",
            data: [
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
            ],
            borderColor: "rgba(0, 191, 255, 0.5)",
            // tension: 0,
            fill: false,
          },
          {
            label: "売上",
            data: [
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
            ],
            backgroundColor: "rgba(255, 228, 181, 0.5)",
          },
        ],
      };
    },
    // ************************************
    updateLineData() {
      this.line = {
        labels: [
          "January",
          "February",
          "March",
          "April",
          "May",
          "June",
          "July",
          "August",
          "September",
          "October",
          "November",
          "December",
        ],
        datasets: [
          {
            label: "潮位",
            data: [
              this.getRandomInt(),
              null,
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
            ],
            borderColor: "rgba(0, 191, 255)",
            backgroundColor: "rgba(224, 255, 255, 0.5)",
            pointBackgroundColor: "rgba(0, 0, 240)",
            pointHoverBorderColor: "rgba(0, 191, 255)",
            pointHoverBackgroundColor: "rgba(224, 255, 255, 0.5)",
            spanGaps: true,
          },
          {
            label: "海苔網",
            data: [30, 30, 30, 30, 30, 30, 30, 30, 30, 30, 30, 30],
            borderColor: "rgba(50, 205, 50)",
            backgroundColor: "rgba(0,0,0,0)",
            pointBackgroundColor: "rgba(50, 205, 50)",
            pointRadius: 0,
            pointHoverBorderColor: "rgba(50, 205, 50)",
            pointHoverBackgroundColor: "rgba(0,0,0,0)",
            spanGaps: true,
          },
        ],
      };
      this.line_opitions = {
        scales: {
          xAxes: [
            {
              scaleLabel: {
                display: true,
                labelString: "Month",
              },
            },
          ],
          yAxes: [
            {
              ticks: {
                beginAtZero: true,
                stepSize: 10,
              },
            },
          ],
        },
        elements: {
          line: {
            // tension: 0, // ベジェ曲線を無効にする
          },
        },
      };
    },
    // ************************************
    updateOriginalLineData() {
      this.original_datasets = {
        labels: [
          "January",
          "February",
          "March",
          "April",
          "May",
          "June",
          "July",
          "August",
          "September",
          "October",
          "November",
          "December",
        ],
        datasets: [
          {
            label: this.original_prop_data.label,
            data: [
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
            ],
            backgroundColor: this.original_prop_data.backgroundColor,
            borderColor: `rgba(${this.original_prop_data.backgroundColor01.red}, ${this.original_prop_data.backgroundColor01.green}, ${this.original_prop_data.backgroundColor01.blue})`,
            borderWidth: 3,
          },
        ],
      };
    },
    // ************************************
    updatePieData() {
      this.pie = {
        labels: [
          "January",
          "February",
          "March",
          "April",
          "May",
          "June",
          "July",
          "August",
          "September",
          "October",
          "November",
          "December",
        ],
        datasets: [
          {
            label: "Count",
            data: [
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
            ],
            backgroundColor: "rgba(255, 99, 132, 0.8)",
          },
        ],
      };
    },
    // ************************************
    updateDoughnutData() {
      (this.doughnut = {
        labels: ["A", "B", "C", "D"],
        datasets: [
          {
            label: "Count",
            data: [
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
              this.getRandomInt(),
            ],
            backgroundColor: ["orange", "skyblue", "yellow", "hotpink"],
          },
        ],
      }),
        (this.doughnut_options = {
          animation: {},
        });
    },
    // ************************************
    updateBubbleData() {
      this.bubble = {
        labels: [
          "January",
          "February",
          "March",
          "April",
          "May",
          "June",
          "July",
          "August",
          "September",
          "October",
          "November",
          "December",
        ],
        datasets: [
          {
            label: "Count",
            data: [
              {
                x: this.getRandomInt(),
                y: this.getRandomInt(),
                r: this.getRandomInt(),
              },
              {
                x: this.getRandomInt(),
                y: this.getRandomInt(),
                r: this.getRandomInt(),
              },
              {
                x: this.getRandomInt(),
                y: this.getRandomInt(),
                r: this.getRandomInt(),
              },
              {
                x: this.getRandomInt(),
                y: this.getRandomInt(),
                r: this.getRandomInt(),
              },
              {
                x: this.getRandomInt(),
                y: this.getRandomInt(),
                r: this.getRandomInt(),
              },
              {
                x: this.getRandomInt(),
                y: this.getRandomInt(),
                r: this.getRandomInt(),
              },
              {
                x: this.getRandomInt(),
                y: this.getRandomInt(),
                r: this.getRandomInt(),
              },
              {
                x: this.getRandomInt(),
                y: this.getRandomInt(),
                r: this.getRandomInt(),
              },
              {
                x: this.getRandomInt(),
                y: this.getRandomInt(),
                r: this.getRandomInt(),
              },
              {
                x: this.getRandomInt(),
                y: this.getRandomInt(),
                r: this.getRandomInt(),
              },
              {
                x: this.getRandomInt(),
                y: this.getRandomInt(),
                r: this.getRandomInt(),
              },
              {
                x: this.getRandomInt(),
                y: this.getRandomInt(),
                r: this.getRandomInt(),
              },
            ],
            backgroundColor: "rgba(255, 99, 132, 0.8)",
          },
        ],
      };
    },
    // ************************************
    updateSurfaceLineData() {
      this.surface_line = {
        labels: [
          "January",
          "February",
          "March",
          "April",
          "May",
          "June",
          "July",
          "August",
          "September",
          "October",
          "November",
          "December",
        ],
        datasets: [
          //データセット0 設定
          {
            fill: "origin", //'origin'まで塗る
            label: "商品A",
            data: [
              this.getRandomInt02(0),
              this.getRandomInt02(0),
              this.getRandomInt02(0),
              this.getRandomInt02(0),
              this.getRandomInt02(0),
              this.getRandomInt02(0),
              this.getRandomInt02(0),
              this.getRandomInt02(0),
              this.getRandomInt02(0),
              this.getRandomInt02(0),
              this.getRandomInt02(0),
              this.getRandomInt02(0),
            ],
            lineTension: 0,
            borderColor: "rgba(199,21,133,1)", //ミディアムバイオレット
            backgroundColor: "rgba(199,21,133,0.5)",
          },
          // データセット1 設定
          {
            fill: 0, // データセット0まで塗る
            label: "商品B",
            data: [
              this.getRandomInt02(15),
              this.getRandomInt02(15),
              this.getRandomInt02(15),
              this.getRandomInt02(15),
              this.getRandomInt02(15),
              this.getRandomInt02(15),
              this.getRandomInt02(15),
              this.getRandomInt02(15),
              this.getRandomInt02(15),
              this.getRandomInt02(15),
              this.getRandomInt02(15),
              this.getRandomInt02(15),
            ],
            lineTension: 0,
            borderColor: "rgba(255,243,82,1)", //レモンイエロー
            backgroundColor: "rgba(255,243,82,0.5)",
          },
          // データセット2 設定
          {
            fill: 1, // データセット1sまで塗る
            label: "商品C",
            data: [
              this.getRandomInt02(26),
              this.getRandomInt02(26),
              this.getRandomInt02(26),
              this.getRandomInt02(26),
              this.getRandomInt02(26),
              this.getRandomInt02(26),
              this.getRandomInt02(26),
              this.getRandomInt02(26),
              this.getRandomInt02(26),
              this.getRandomInt02(26),
              this.getRandomInt02(26),
              this.getRandomInt02(26),
            ],
            lineTension: 0,
            borderColor: "rgba(0,172,154,1)", //ペパーミントグリーン
            backgroundColor: "rgba(0,172,154,0.5)",
          },
        ],
      };
    },
    // ************************************
    // 乱数生成
    getRandomInt() {
      return Math.floor(Math.random() * (50 - 5 + 1)) + 5;
    },
    // ************************************
    // 乱数生成
    getRandomInt02(b) {
      return Math.floor(Math.random() * 10) + b;
    },
  },
};
</script>