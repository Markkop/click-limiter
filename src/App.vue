<template>
  <div id="app">
    <button @click="throttle(countUp, 1000)">Click me</button>
    <h3>Changed {{ count }} times</h3>
    <input @keyup="throttle(countUp, 1000)" />
  </div>
</template>

<script>
export default {
  name: "app",
  data: () => ({
    count: 0
  }),

  methods: {
    countUp() {
      this.count++;
    },

    debounce: function(callback, wait) {
      if (this.timeout) clearTimeout(this.timeout);
      this.timeout = setTimeout(() => callback(), wait);
    },

    throttle: function(callback, wait) {
      if (!this.isWaiting) {
        this.isWaiting = true;
        callback();
        setTimeout(() => (this.isWaiting = false), wait);
      }
    }
  }
};
</script>

<style>
#app {
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
