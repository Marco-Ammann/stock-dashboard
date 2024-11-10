<template>
  <div class="chart-container">
    <LineChart v-if="chartData" :data="chartData" :options="chartOptions" />
  </div>
</template>

<script>
import { defineComponent } from 'vue';
import { Line } from 'vue-chartjs';
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  LineElement,
  LineController,
  PointElement,
  CategoryScale,
  LinearScale,
} from 'chart.js';

ChartJS.register(
  Title,
  Tooltip,
  Legend,
  LineElement,
  LineController,
  PointElement,
  CategoryScale,
  LinearScale
);

export default defineComponent({
  name: 'StockLineChart',
  components: {
    LineChart: Line,
  },
  props: {
    chartData: {
      type: Object,
      required: true
    },
    chartOptions: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      // eslint-disable-next-line vue/no-dupe-keys
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
              boxWidth: 32,
              boxHeight: 12,
              padding: 10,
              font: {
                size: 10,
                family: 'Rubik',
              },
              generateLabels: (chart) => {
                return chart.data.datasets.map((dataset, i) => ({
                  text: dataset.label,
                  fillStyle: dataset.borderColor,
                  fontColor: '#FFF',
                  hidden: !chart.isDatasetVisible(i),
                  index: i
                }));
              }
            },
          },
          title: {
            display: true,
            text: 'Revenue last 3 years',
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
            enabled: true,
            backgroundColor: '#333',
            titleColor: '#fff',
            bodyColor: '#fff',
            borderColor: '#fff',
            borderWidth: 1,
            titleFont: {
              size: 10,
              family: 'Rubik'
            },
            bodyFont: {
              size: 10,
              family: 'Rubik'
            }
          },
        },
        interaction: {
          intersect: false,
          mode: 'index',
        },
        scales: {
          x: {
            grid: {
              color: '#86868688',
              display: true
            },
            ticks: {
              color: '#FFF',
              font: {
                size: 10,
                family: 'Rubik'
              }
            }
          },
          y: {
            beginAtZero: true,
            grid: {
              color: '#86868688',
              display: true
            },
            ticks: {
              color: '#FFF',
              font: {
                size: 10,
                family: 'Rubik'
              },
              stepSize: 30,
            }
          }
        },
        elements: {
          point: {
            radius: 0,
            hitRadius: 5,
            hoverRadius: 4,
            hoverBorderWidth: 2
          },
          line: {
            tension: 0.2,
            borderWidth: 1,
            fill: false,
          }
        },
        layout: {
          padding: {
            left: 0,
            right: 0,
            top: 0,
            bottom: 0
          }
        },
        animation: {
          duration: 1000,
          easing: 'easeInOutQuart'
        },
      }
    };
  }
});
</script>

<style scoped>
.chart-container {
  width: 714px;
  height: 100%;
  background-color: #011F35;
  padding: 20px 32px;
  border-radius: 12px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}
</style>
