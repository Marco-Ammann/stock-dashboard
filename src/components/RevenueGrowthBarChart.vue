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
  name: 'RevenueGrowthBarChart',
  components: {
    BarChart: Bar,
  },
  data() {
    return {
      chartData: {
        labels: ['Apple', 'Microsoft', 'Amazon', 'Alphabet', 'Meta', 'Tesla', 'Nvidia'],
        datasets: [
          {
            label: 'Q1 2024',
            data: [10, 12, 70, 15, 6, 7, 3],
            backgroundColor: '#39DAFF',
            barPercentage: 0.7,
          },
          {
            label: 'Q4 2023',
            data: [8, 11, 65, 14, 5, 6, 2],
            backgroundColor: '#31BFE2',
            barPercentage: 0.7,
          },
          {
            label: 'Q3 2023',
            data: [7, 10, 60, 13, 4, 5, 2],
            backgroundColor: '#29A5C5',
            barPercentage: 0.7,
          },
          {
            label: 'Q2 2023',
            data: [6, 9, 55, 12, 3, 4, 1],
            backgroundColor: '#218AA8',
            barPercentage: 0.7,
          },
        ],
      },
      chartOptions: {
        responsive: true,
        maintainAspectRatio: false,
        plugins: {
          legend: {
            display: true,
            position: 'right',
            labels: {
              color: '#FFF',
              usePointStyle: false,
              boxWidth: 24,
              boxHeight: 8,
              padding: 15,
              font: {
                size: 10,
                family: 'Rubik',
              },
            },
          },
          title: {
            display: true,
            text: 'Revenue Growth in % YoY',
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
            grid: {
              display: false,
            },
            ticks: {
              color: '#FFF',
              font: {
                size: 10,
                family: 'Rubik',
              },
            },
          },
          y: {
            beginAtZero: true,
            max: 90,
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
              callback: function(value) {
                return value + '%';
              }
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
