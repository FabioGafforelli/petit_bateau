<script>
import header1 from "../components/Header.vue"
import footer1 from "../components/Footer.vue"
import Doughnut from "../components/Graphique_Doughnut.vue"
import Radar from "../components/Radar.vue"
import Bar from "../components/Bar.vue"
import Line from "../components/Line.vue"




export default {
    name:"App",
    components: { header1, footer1, Doughnut, Radar, Bar, Line },
}
</script>

<template>
<main class="">
        <header1/>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
        <br>
<div>
<div>
    
    <h1 class="font-bold text-2xl">Petit bateau</h1>

   

                </div>
<Radar class="graphique1 pl-8" />
<br>

</div>

<h2 class="font-bold text-xl">Voici des graph</h2>
<div class="flex items-stretch">
<div class="py-4"><Doughnut /></div>
<Line class="graphique1" />
</div>
<!-- <div>
    <Bar class="graphique2" />
</div> -->
<footer1 />
</main>
</template>

<style scoped>
    .graphique1 {
        width: 40%;
    }
    .graphique2 {
        width: 30%;
    }
</style>