<script lang="ts">
    export let score: Number;
    export let teamSecondary: string;
</script>

<div class="scoreArea anim2" id="awayScoreArea" style="--bgcolor: {teamSecondary}">
    <span class="score" id="awayScore">{ score }</span>
</div>

<style>
.scoreArea {
    background-color: var(--bgcolor); 
    height: 40px;
    width: 70px;
    display: flex;
    justify-content: center;
    align-items: center;
}

.score {
    color: white;
    font-size: 30px;
    font-family: "Open Sans";
    font-weight: bold;
}
</style>