<template>
  <div class="chart-container">
    <DoughnutChart v-if="chartData" :data="chartData" :options="chartOptions" />
    <p class="chart-note">In Billion USD TTM</p>

  </div>
</template>

<script>
import { defineComponent } from 'vue';
import { Doughnut } from 'vue-chartjs';
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  ArcElement,
} from 'chart.js';

ChartJS.register(
  Title,
  Tooltip,
  Legend,
  ArcElement
);

export default defineComponent({
  name: 'DonutChart',
  components: {
    DoughnutChart: Doughnut,
  },
  data() {
    return {
      chartData: {
        labels: ['Meta 8.7', 'Tesla 5.4', 'Nvidia 14.7', 'Microsoft 17', 'Apple 17.7', 'Google 11.5', 'Amazon 9.1'],
        datasets: [
          {
            data: [8.7, 5.4, 14.7, 17, 17.7, 11.5, 9.1],
            backgroundColor: [
              '#39DAFF', '#31BFE2', '#29A5C5', '#218AA8', '#196F8C', '#11546F', '#093A52'
            ],
            borderColor: '#FFF',
            borderWidth: 1,
          },
        ],
      },
      chartOptions: {
        responsive: true,
        maintainAspectRatio: false,
        cutout: '70%',
        plugins: {
          legend: {
            position: 'right',
            labels: {
              color: '#FFF',
              font: {
                size: 10,
                family: 'Rubik',
              },
              boxWidth: 32,
              boxHeight: 12,
              padding: 10,
              usePointStyle: false,
            },
          },
          title: {
            display: true,
            text: 'Revenue Breakdown Magnificent Seven',
            color: '#FFFFFF',
            position: 'top',
            align: 'start',
            font: {
              size: 20,
              family: 'Rubik',
              weight: 'bold'
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
            borderWidth: 1,
            bodyFont: {
              size: 10,
              family: 'Rubik'
            },
            titleFont: {
              size: 10,
              family: 'Rubik'
            }
          },

          elements: {
            arc: {
              borderWidth: 1,
              borderColor: '#011F35',
            }
          },

        },
      },
    };
  },
});
</script>

<style scoped>
.chart-container {
  flex: 1;
  height: 100%;
  background-color: #011F35;
  padding: 20px 49px 32px 32px;
  border-radius: 12px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  position: relative;
}
.chart-note {
  position: absolute;
  bottom: 32px;
  right: 49px;
  color: #FFF;
  font-size: 10px;
  font-family: Rubik, sans-serif;
}
</style>
