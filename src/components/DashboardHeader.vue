<!-- DashboardHeader.vue -->
<template>
  <header class="header">
    <div class="title-marker"></div>
    <h1>The Magnificent Seven Companies</h1>
  </header>
</template>

<script>
export default {
  name: 'DashboardHeader'
}
</script>

<style scoped>
.title-marker {
  width: 6rem;
  height: 2rem;
  border-radius: 0rem 6.25rem 6.25rem 0rem;
  background: #39DAFF;
}

.header {
  align-self: start;
  display: inline-flex;
  align-items: center;
  gap: 1.5rem;
}

h1 {
  color: #F9F9F9;
  font-family: Rubik;
  font-size: 2.25rem;
  font-style: normal;
  font-weight: 500;
  line-height: normal;
}
</style>
