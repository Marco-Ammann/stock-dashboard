<!-- App.vue -->
<template>
  <div id="app">
    <DashboardView />
  </div>
</template>

<script>
import DashboardView from './views/DashboardView.vue'

export default {
  name: 'App',
  components: {
    DashboardView
  }
}
</script>

<style>
#app {
  font-family: 'Rubik', sans-serif;
  background: -webkit-radial-gradient(100% 111.8% at 50% 0%, #020204 14.6%, #011F35 100%);
  background: -moz-radial-gradient(100% 111.8% at 50% 0%, #020204 14.6%, #011F35 100%);
  background: radial-gradient(100% 111.8% at 50% 0%, #020204 14.6%, #011F35 100%);

  color: white;
  min-height: 100vh;
  width: 100vw;
  display: flex;
  justify-content: center;
  align-items: flex-start;
}
</style>
