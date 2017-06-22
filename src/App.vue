<template>
  <div id="app">
    <nav-bar></nav-bar>

    <section class="monitor-lockup">
      <bus-monitor v-for="monitor in monitors" :username="monitor.user"></bus-monitor>
    </section>
  </div>
</template>

<script>
import NavBar from './DashNav.vue'
import BusMonitor from './BusMonitor.vue'

export default {
  name: 'app',
  components: {NavBar, BusMonitor},
  data () {
    return {
      monitors: [
        {
          user: 'Mathieu',
          route: '19',
          arrival: 0
        },

        {
          user: 'James',
          route: '365',
          arrival: 20
        }
      ]
    }
  }
}
</script>

<style lang="scss">
.monitor-lockup {
  padding-top: 5em;
}
</style>
