<script lang="ts">
  import gsap from "gsap";
  import { onMount } from "svelte";
  import InfoArea from "./InfoArea.svelte";
  import ScoreArea from "./ScoreArea.svelte";
  import TeamArea from "./TeamArea.svelte";
  import Timeouts from "./Timeouts.svelte";

  let away = {
    name: "DELAWARE",
    score: 0,
    color: "#00539F",
    secondary: "#004787" 
  };

  let home = {
    name: "DREXEL",
    score: 0,
    color: "#00539F",
    secondary: "#004787"
  };

  let info = {
    period: "1st",
    clock: "10:00",
    shotClock :"30"
  }

  let tl: gsap.core.Timeline;

  onMount(() => {
    tl = gsap.timeline({
      paused: true,
      onComplete: () => {
        tl.seek(0);
        tl.pause();
      },
    });
    tl.from(".anim1", {
      duration: 0.75,
      scaleX: 0,
      transformOrigin: "left",
      ease: "power4.inOut",
    });
    tl.from(
      ".anim2",
      { duration: 0.5, y: 20, opacity: 0, stagger: 0.1 },
      "-=.5"
    );
    tl.addPause(1.5);
    tl.to("#scorebug", { duration: 0.2, opacity: 0 });
    tl.reverse();
  });

  webcg.on("play", () => tl.play());
  webcg.on("stop", () => tl.play());
  webcg.on("data", (data) => {
    home.score = data.homeScore;
    home = home;
    away.score = data.awayScore;
    info.period = data.period;
  });
</script>

<main id="app">
  <div id="scorebug" class="container anim1">
    <TeamArea teamName={away.name} teamColor={away.color} />
    <ScoreArea score={away.score} teamSecondary={away.secondary} />
    <TeamArea teamName={home.name} teamColor={home.color} />
    <ScoreArea score={home.score} teamSecondary={home.secondary} />

    <InfoArea period={info.period} gameClock={info.clock} shotClock={info.shotClock} />

    <Timeouts />

    <div class="spacer" />

    <Timeouts />

    <div class="spacer" />
  </div>
</main>

<style>
  #app {
    height: 720px;
    width: 1280px;
    color: transparent;
    display: flex;
    justify-content: center;
  }

  .container {
    position: relative;
    top: 85%;
    height: 55px;
    width: 800px;
    background-color: rgba(0, 0, 0, 0.9);
    display: flex;
    flex-wrap: wrap;
  }

  .spacer {
    width: 115px;
  }

</style>
