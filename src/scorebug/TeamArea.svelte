<script lang="ts">
    export let teamColor: string
    export let teamName: string
</script>

<div class="teamArea anim2" style="--bgcolor: {teamColor}">
    <span class="teamName">
        { teamName }
    </span>
</div>

<style>
.teamArea {
    background-color: var(--bgcolor);
    height: 40px;
    width: 210px;
}

.teamName {
  color: white;
  font-size: 18px;
  font-family: "Open Sans";
  font-weight: bolder;
  position: relative;
  left: -30px;
  top: 20%;
}

</style>