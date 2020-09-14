<template>
  <div id="app">
    <div>{{ message }}</div>
    <div>{{ countdown_msg }}</div>
    <button @click="countdown3s">3s</button>
    <button @click="countdown1m">1m</button>
    <button @click="countdown5m">5m</button>
    <button @click="countdown10m">10m</button>
    <button @click="countdown30m">30m</button>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        message: 'Cuenta regresiva',
        countdown_msg: '00:00 min/seg'
      };
    },
    methods: {
        countdown3s:function(){
            alert("3s");
        },
        countdown1m:function(){
            alert("1m");
        },
        countdown5m:function(){
            alert("5m");
        },
        countdown10m:function(){
            alert("10m");
        },
        countdown30m:function(){
            alert("30m");
        }
    }
}
</script>

<style scoped>
  #app {
    font-size: 25px;
    font-family: "Calibri", sans-serif;
    color: #000;
  }
</style>