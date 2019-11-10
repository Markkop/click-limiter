<template>
  <div id="app">
    <h3>Changed {{ count }} times</h3>
    <div class="examples">
      <div class="container">
        <h2>Throttle</h2>
        <button @click="throttle(countUp, 1000)">Click me</button>
        <input @keyup="throttle(countUp, 1000)" />
      </div>
      <div class="container">
        <h2>Normal</h2>
        <button @click="countUp">Click me</button>
        <input @keyup="countUp" />
      </div>
      <div class="container">
        <h2>Debounce</h2>
        <button @click="debounce(countUp, 1000)">Click me</button>
        <input @keyup="debounce(countUp, 1000)" />
      </div>
    </div>
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
  display: flex;
  flex-direction: column;
}

.examples {
  justify-content: center;
  display: flex;
  flex-direction: row;
}

.container {
  margin: 60px;
  display: flex;
  flex-direction: column;
}
</style>
