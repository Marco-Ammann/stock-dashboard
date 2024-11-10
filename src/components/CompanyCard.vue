<template>
  <div class="company-card">

    <h3> <img class="logo" :src="getImagePath(company.logo)" alt="Company Logo"> {{ company.name }}</h3>
    <p class="label-revenue">Revenue Q1 2024:</p>
    <div class="revenue-container">
      <p class="company-revenue_amount">{{ company.revenue }}</p>
      <div class="revenue-changes">
        <p class="revenue-change" :class="{ positive: company.changeFixed > 0, negative: company.changeFixed < 0 }">
          <span v-if="company.changeFixed > 0">+</span>
          <span>{{ company.changeFixed }}</span>
          <img class="arrow-icon" v-if="company.changeFixed > 0" src="../assets/img/arrow_up.svg" alt="">
          <img class="arrow-icon" v-if="company.changeFixed < 0" src="../assets/img/arrow_down.svg" alt="">
        </p>
        <p class="revenue-change" :class="{ positive: company.changePercent > 0, negative: company.changePercent < 0 }">
          <span class="transparent" v-if="company.changeFixed > 0">+</span>
          <span>{{ company.changePercent }} %</span>
        </p>
      </div>
    </div>
    <p class="currency-info">In Bill USD</p>
  </div>
</template>

<script>
export default {
  name: "CompanyCard",
  props: {
    company: {
      type: Object,
      required: true
    }
  },

  methods: {
    getImagePath(fileName) {
      return new URL(`../assets/img/${fileName}`, import.meta.url).href;
    },
  },
}
</script>


<style scoped>
.company-card {
  display: flex;
  padding: 1.25rem 1.5rem;
  flex-direction: column;
  align-items: flex-start;
  gap: 0.5rem;

  border-radius: 1rem;
  background: #011F35;
}

h3 {
  font-size: 1.25rem;
  font-style: normal;
  font-weight: 500;
  line-height: normal;
}

.transparent {
  color: transparent;
}

.label-revenue {
  font-size: 0.75rem;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
}

.revenue-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.company-revenue_amount {
  font-size: 1.5rem;
  font-style: normal;
  font-weight: 500;
  line-height: normal;
}

.revenue-changes {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: center;
  margin-left: 0.25rem;
}

.revenue-change {
  display: flex;
  align-items: center;
  justify-content: flex-start;
}

.arrow-icon {
  width: 20px;
  height: 20px;
}

.positive {
  color: #3BA752;
}

.negative {
  color: #C41C1C;
}

span .revenue-change {
  font-size: 0.8125rem;
  font-style: normal;
  font-weight: 500;
  line-height: normal;
}

.currency-info {
  font-size: 0.5rem;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
}

.logo {
  height: 1.25rem;
  aspect-ratio: 1 / 1;
  margin-right: 0.5rem;
}
</style>
