<template>
  <div v-if="event">
    <h1>{{ event.title }}</h1>
    <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
    <p>{{ event.description }}</p>
  </div>
</template>

<script>
export default {
  props: ['id'],
  data() {
    return {
      event: null
    }
  },
  created() {
    fetch('https://my-json-server.typicode.com/Code-Pop/Real-World_Vue-3/events/' + this.id)
      .then(res => res.json())
      .then(results => {
        this.event = results;
      })
      .catch(console.error)
  }
};
</script>