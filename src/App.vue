<template>
  <HtmlClock theme="rainbow"></HtmlClock>
  <HtmlClock theme="red"></HtmlClock>
  <HtmlClock></HtmlClock>
</template>

<script>
import HtmlClock from './components/HtmlClock.vue';
export default {
  components: {
    HtmlClock,
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=IBM+Plex+Serif:wght@700&family=Orbitron&display=swap');

body {
  font-family: 'Orbitron', sans-serif;
}
</style>
