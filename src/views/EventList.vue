<template>
  <div class="event">
    <h1>Events for Good</h1>
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
// @ is an alias to /src
import EventCard from "@/components/EventCard.vue";

export default {
  name: "EventList",
  components: {
    EventCard
  },
  data() {
    return {
      events: null
    }
  },
  created() {
    fetch('https://my-json-server.typicode.com/Code-Pop/Real-World_Vue-3/events')
      .then(res => res.json())
      .then(results => {
        this.events = results;
      })
      .catch(console.error)
  }
};
</script>

<style scoped>
.event {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>