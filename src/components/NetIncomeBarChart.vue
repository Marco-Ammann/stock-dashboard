<!--Test-->
<template>
  <div class="chart-container">
    <BarChart :data="chartData" :options="chartOptions" />
  </div>
</template>

<script>
import { defineComponent } from 'vue';
import { Bar } from 'vue-chartjs';
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale,
} from 'chart.js';

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale);

export default defineComponent({
  name: 'NetIncomeBarChart',
  components: {
    BarChart: Bar,
  },
  data() {
    return {
      chartData: {
        labels: ['Amazon', 'Meta', 'Alphabet', 'Microsoft', 'Apple', 'Nvidia', 'Tesla'],
        datasets: [
          {
            label: 'Net Income',
            data: [62.62, 40.15, 39.5, 24.51, 26.25, 6.81, 3.16],
            backgroundColor: [
              '#39DAFF',
              '#31BFE2',
              '#29A5C5',
              '#218AA8',
              '#196F8C',
              '#11546F',
              '#093A52'
            ],
            borderRadius: 0,
            borderColor: '#FFF',
            borderWidth: 1,
            barThickness: 15,
          },
        ],
      },
      chartOptions: {
        indexAxis: 'y',
        responsive: true,
        maintainAspectRatio: false,
        plugins: {
          legend: {
            display: false,
          },
          title: {
            display: true,
            text: 'Net Income TTM',
            color: '#FFFFFF',
            align: 'start',
            font: {
              size: 20,
              weight: 'bold',
              family: 'Rubik',
            },
            padding: {
              top: 0,
              bottom: 20
            }
          },
          tooltip: {
            backgroundColor: '#333',
            titleColor: '#fff',
            bodyColor: '#fff',
            borderColor: '#fff',
            borderWidth: 1
          },
        },
        scales: {
          x: {
            beginAtZero: true,
            grid: {
              color: '#86868688',
              display: true,
            },
            ticks: {
              color: '#FFF',
              font: {
                size: 9,
                family: 'Rubik',
              },
              stepSize: 20,
            },
          },
          y: {
            grid: {
              color: '#86868688',
              display: true,
            },
            ticks: {
              color: '#FFF',
              font: {
                size: 10,
                family: 'Rubik',
              },
            },
          },
        },
      },
    };
  },
});
</script>

<style scoped>
.chart-container {
  width: 100%;
  height: 100%;
  background-color: #011F35;
  padding: 20px 32px;
  border-radius: 12px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}
</style>
