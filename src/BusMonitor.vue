<template>
<div class="box">
  <article class="media">
    <div class="media-left">
      <figure class="image is-64x64">
        <h1 class="route-num">{{ route }}</h1>
      </figure>
    </div>
    <div class="media-content">
      <div class="content">
        <p>
          <strong>{{ username }} </strong>
          <br>
          Your bus arrives at <strong> {{ formattedTime }}</strong>, <strong>{{ minutesToArrival }}</strong>.
        </p>
      </div>
    </div>
  </article>
</div>
</template>

<script>
export default {
    name: 'BusMonitor',
    props: ['username', 'route', 'arrival'],
    data() {
        return {
            image_src: 'http://via.placeholder.com/500x500',
            arrival_time: this.arrival,
        }
    },
    computed: {
      formattedTime: function() {
        return moment(this.arrival_time).format('h:mm a');
      },
      minutesToArrival: function() {
        return moment(this.arrival_time).fromNow();
      }
    }
}

</script>

<style lang="scss">

.route-num {
  font-size: 2.5em;
  text-align: center;
  vertical-align: middle;
  font-family: 'Fira Mono', monospace;
}

.box {
  width: 66vw;
}

.media-content {
  padding-left: 1em;
}


</style>