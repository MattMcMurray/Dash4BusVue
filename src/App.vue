<template>
  <div id="app">
    <nav-bar></nav-bar>

    <section class="monitor-lockup">
      <div class="container">
        <div class="column">
          <bus-monitor v-for="monitor in getSortedMonitors" 
                       :key="monitor.arrival" 
                       :username="monitor.user" 
                       :route="monitor.route" 
                       :arrival="monitor.arrival"></bus-monitor>
        </div>
      </div>
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
        },

        {
          user: 'Casey',
          route: '11',
          arrival: 10
        }
      ]
    }
  },

  computed: {
    getSortedMonitors: function() {
      var compare = function(a, b) {
        if (a.arrival < b.arrival)
          return -1;
        if (a.arrival > b.arrival)
          return 1
        return 0;
      } 

      return this.monitors.sort(compare);
    }
  }
}
</script>

<style lang="scss">

body {
  background-color: #2c3e50;
}

.monitor-lockup {
  padding-top: 1em;
}

.column {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
