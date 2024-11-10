<!-- DashboardView.vue -->
<template>
  <div class="dashboard">
    <DashboardHeader />

    <!-- Übersicht der Unternehmen als Karussell -->
    <div class="overview-cards" ref="carousel">
      <CompanyCard v-for="(company, index) in duplicatedCompanies" :key="index" :company="company" />
    </div>

    <!-- Diagramme und andere Metriken -->
    <div class="charts">
      <!-- LineChart hinzufügen -->
      <StockLineChart :chart-data="chartData" :chart-options="chartOptions" />
      <DonutChart />
    </div>
    <div class="chartsBottom">
      <!-- LineChart hinzufügen -->
      <div class="fakechart1"><NetIncomeBarChart /></div>
      <div class="fakechart2"><GrossMarginBarChart /></div>
      <div class="fakechart3"><RevenueGrowthBarChart /></div>

    </div>
  </div>
</template>

<script>
import CompanyCard from '../components/CompanyCard.vue';
import DashboardHeader from '../components/DashboardHeader.vue';
import LineChart from '../components/LineChart.vue';
import DonutChart from '../components/DonutChart.vue';
import NetIncomeBarChart from '../components/NetIncomeBarChart.vue';
import GrossMarginBarChart from '../components/GrossMarginBarChart.vue';
import RevenueGrowthBarChart from '../components/RevenueGrowthBarChart.vue';

export default {
  name: "DashboardView",
  components: {
    DashboardHeader,
    CompanyCard,
    StockLineChart: LineChart,
    DonutChart,
    NetIncomeBarChart,
    GrossMarginBarChart,
    RevenueGrowthBarChart
  },

  data() {
    return {
      companies: [
        { name: 'Apple', revenue: 38.52, changeFixed: 1.06, changePercent: 2.83, logo: 'apple.svg' },
        { name: 'Meta', revenue: 435.57, changeFixed: -5.81, changePercent: -1.32, logo: 'meta.svg' },
        { name: 'Microsoft', revenue: 409.05, changeFixed: 1.70, changePercent: 2.51, logo: 'microsoft.svg' },
        { name: 'Google', revenue: 29.87, changeFixed: 1.70, changePercent: 6.04, logo: 'google.svg' },
        { name: 'Amazon', revenue: 117.89, changeFixed: 4.22, changePercent: 2.43, logo: 'amazon.svg' },
        { name: 'Tesla', revenue: 177.89, changeFixed: 4.22, changePercent: 2.43, logo: 'tesla.svg' }
      ],
      scrollAmount: 1,

      chartLabels: [
        'Q1 2021', 'Q2 2021', 'Q3 2021', 'Q4 2021',
        'Q1 2022', 'Q2 2022', 'Q3 2022', 'Q4 2022',
        'Q1 2023', 'Q2 2023', 'Q3 2023', 'Q4 2023',
        'Q1 2024'
      ]
    };
  },

  computed: {
    duplicatedCompanies() {
      return [...this.companies, ...this.companies];
    },

    chartData() {
      return {
        labels: this.chartLabels,
        datasets: [
          {
            label: 'Apple',
            data: [89.58, 84.43, 87.36, 120.95, 95.28, 84.96, 92.15, 115.15, 93.84, 85.80, 87.50, 115.15, 90.84],
            borderColor: '#39DAFF',
            borderWidth: 1,
          },
          {
            label: 'Amazon',
            data: [108.52, 115.08, 113.81, 140.41, 119.44, 118.23, 125.10, 145.20, 129.36, 130.38, 138.10, 146.20, 129.36],
            borderColor: '#31BFE2',
            borderWidth: 1,
          },
          {
            label: 'Microsoft',
            data: [41.71, 46.15, 47.32, 51.73, 50.36, 55.87, 49.12, 53.75, 52.86, 57.19, 55.52, 60.40, 63.60],
            borderColor: '#29A5C5',
            borderWidth: 1,
          },
          {
            label: 'Google',
            data: [55.31, 60.88, 63.12, 74.33, 65.01, 72.69, 69.09, 75.05, 70.79, 73.60, 77.69, 80.50, 79.54],
            borderColor: '#218AA8',
            borderWidth: 1,
          },
          {
            label: 'Meta',
            data: [26.17, 31.08, 28.01, 36.67, 25.91, 32.82, 27.71, 35.17, 30.65, 36.00, 34.15, 40.64, 38.00],
            borderColor: '#196F8C',
            borderWidth: 1,
          },
          {
            label: 'Tesla',
            data: [10.39, 12.96, 15.76, 18.72, 15.76, 19.93, 21.45, 22.32, 24.33, 23.93, 27.71, 28.57, 25.20],
            borderColor: '#11546F',
            borderWidth: 1,
          },
          {
            label: 'Nvidia',
            data: [5.66, 8.51, 6.10, 9.64, 7.29, 8.70, 6.93, 9.05, 8.19, 13.51, 15.68, 14.12, 18.00],
            borderColor: '#093A52',
            borderWidth: 1,
          },
        ],
      };
    }
  },

  methods: {
    scrollCarousel() {
      const carousel = this.$refs.carousel;
      carousel.scrollLeft += this.scrollAmount;
      if (carousel.scrollLeft >= carousel.scrollWidth / 2) {
        carousel.scrollLeft = 0;
      }
    }
  },

  mounted() {
    this.scrollInterval = setInterval(this.scrollCarousel, 50);
  },

  beforeUnmount() {
    clearInterval(this.scrollInterval);
  }
};
</script>

<style scoped>
.dashboard {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 1440px;
  max-height: 1122px;
  padding-top: 4rem;
}

.overview-cards {
  display: flex;
  padding: 1.5rem;
  align-items: flex-start;
  gap: 1.5rem;
  margin-top: 2rem;
  width: 1200px;
  overflow-x: hidden;
  white-space: nowrap;
  background: rgba(2, 58, 98, 0.20);
  border-radius: 1.25rem;
}

.charts {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 2rem;
  margin-top: 2rem;
  width: 1200px;
  height: 352px;
}

.chartsBottom {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 2rem;
  margin-top: 2rem;
  width: 1200px;
  height: 352px;
}

.fakechart1 {
  flex: auto;
  height: 352px;
  background-color: #011F35;
  border-radius: 1.25rem;
}

.fakechart2 {
  width: 293px;
  height: 352px;
  background-color: #011F35;
  border-radius: 1.25rem;
}

.fakechart3 {
  width: 454px;
  height: 352px;
  background-color: #011F35;
  border-radius: 1.25rem;
}
</style>
