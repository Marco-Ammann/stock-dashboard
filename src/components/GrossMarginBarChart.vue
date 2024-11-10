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
  name: 'GrossMarginBarChart',
  components: {
    BarChart: Bar,
  },
  data() {
    return {
      chartData: {
        labels: ['Nvidia', 'Meta', 'Amazon', 'Microsoft', 'Alphabet', 'Apple', 'Tesla'],
        datasets: [
          {
            label: 'Gross Margin (%)',
            data: [24.8, 24.3, 12.7, 12.5, 12.2, 6.2, 5.7],
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
            text: 'Gross Margin in % LQ',
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
            max: 30,
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
              callback: function(value) {
                return value + '%';
              }
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
