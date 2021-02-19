<script lang="ts">
  export let period: string;
  export let gameClock: string;
  export let shotClock: string;
</script>

<div class="infoArea anim2">
  <span id="period">{period}</span>
  <span id="clock">{gameClock}</span>
</div>
<div class="shotClockArea anim2">
  <span id="shotClock">{shotClock}</span>
</div>

<style>
  .infoArea {
    width: 185px;
    height: 40px;
    background-color: #131313;
    display: flex;
    justify-content: space-around;
    align-items: center;
    color: white;
    font-size: 20px;
    font-family: "Open Sans";
    font-weight: 600;
  }

  #clock {
    color: yellow;
  }

  .shotClockArea {
    height: 40px;
    width: 55px;
    background-color: black;
    display: flex;
    justify-content: space-around;
    align-items: center;
    font-size: 20px;
    font-family: "Open Sans";
    font-weight: bold;
  }

  #shotClock {
    color: white;
  }
</style>
