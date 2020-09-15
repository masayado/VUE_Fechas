<template>
<center>
  <div id="app">
    <div class="message">{{ message }}</div>
    <span class="time">{{ time }}</span>
    <div class="buttons">
    <b-button variant="dark" @click="run(3)">3s</b-button>
    <b-button variant="dark" @click="run(60)">1m</b-button>
    <b-button variant="dark" @click="run(300)">5m</b-button>
    <b-button variant="dark" @click="run(600)">10m</b-button>
    <b-button variant="dark" @click="run(1800)">30m</b-button>
    </div>
    
  </div>
</center>
</template>

<script>
var interval;
  export default {
    data() {
      return {
        message: 'Cuenta regresiva',
        time: "00:00",
      };
    },
    methods: {
        run:function(seg){
        const now = Date.now();
        const end = now+(seg+1)*1000;
        this.discount(end);
        },
        countdown3s:function(){
            console.log("3s");
        },
        countdown1m:function(){
            console.log("1m");
        },
        countdown5m:function(){
            console.log("5m");
        },
        countdown10m:function(){
            console.log("10m");
        },
        countdown30m:function(){
            console.log("30m");
        },
        discount:function(end){
            interval = setInterval(()=>{
                const rest = Math.round((end-Date.now())/1000);
                if (rest < 0){
                    clearInterval(interval);
                    return;
                }
                const minutes = Math.floor((rest % 3600)/60);
                const seconds = rest % 60;
                console.log(minutes, seconds);
                //this.time = `${minutes}:${seconds}`;
                if ((String(seconds).length)===1 && (String(minutes).length)===1 ){
                    this.time=`0${minutes}:0${seconds}`
                }else if((String(seconds).length)===1 && (String(minutes).length)!=1 ){
                    this.time=`${minutes}:0${seconds}`
                }else if((String(seconds).length)!=1 && (String(minutes).length)===1 ){
                    this.time=`0${minutes}:${seconds}`
                }else{
                this.time=`${minutes}:${seconds}`
                }
            },1000);
        }

    }
}
</script>

<style scoped>
  #app {
    width:30%;
    margin: 0 auto;
    margin-top:3.75rem;
    padding:1.25rem;
    font-size: 1.5625rem;
    font-family: $font-family-base;
    color: #000;
    background-color:#fff;
    border: 1px solid #000;
  }

  .message{
    font-weight: normal;
  }

  .buttons{
    padding:10px;
  }

  .time{
    font-family: 'Helvetica', sans-serif;
    padding:10px;
    font-weight:bold;
  }

</style>