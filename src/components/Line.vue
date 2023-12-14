<script setup>
    import { reactive, ref, onMounted } from 'vue';
// import d'un graphique type ligne
import { Line } from 'vue-chartjs'

import { Chart as ChartJS, Title, Tooltip, Legend, PointElement, LineElement, LineController, CategoryScale, LinearScale, Filler} from 'chart.js'

//elements utilisés potentiellement pour notre graphique
ChartJS.register(Title, Tooltip, Legend, PointElement, LineElement, LineController, CategoryScale, LinearScale, Filler)

const propChart = defineProps ({
    chartID: { type: String, default: 'line-chart'},
    datasetIdKey: { type: String, default: 'label'},
    width: { type: Number, default: 200},
    height: { type: Number, default: 100},
    cssClasses: { type: String, default: ""},
    styles: { type: Object, default: () => {}},
    plugins: { type: Object, default: () => {}},
})

  //Montage du composant Chargement des données
//Liste contiendra le résultat de la requête

let chartData = reactive({
// Etiquettes l'axe
labels: ['1', '2', '4', '5', '6', '7', '8'],
//Valeurs des données du graphique
datasets: [
    {
        //Etiquette du jeu de données
        label : 'CA',
        // Valeurs des données (statiques pour l'exemple)
        data: [863901, 540138, 1689296, 1977722, 1646325, 1610982, 1824320],
        borderColor: 'green',
        tension: 0.5,
        fill:true
    },
    {
        //Etiquette du jeu de données
        label : 'Charge de personnel',
        // Valeurs des données (statiques pour l'exemple)
        data: [110880, 110880, 299376, 310464, 433608, 433608, 321552],
        borderColor: 'yellow',
        tension: 0.5,
        fill:true,
    },
    {
        //Etiquette du jeu de données
        label : 'Entretien et confort',
        // Valeurs des données (statiques pour l'exemple)
        data: [151800, 152083, 207456, 210994, 345600, 351648, 238560],
        borderColor: 'orange',
        tension: 0.5,
        fill:true,
    },
    {
        //Etiquette du jeu de données
        label : 'Service exterieur comm publicité',
        // Valeurs des données (statiques pour l'exemple)
        data: [56400, 49200, 120000, 132000, 168000, 171600, 147600],
        borderColor: 'red',
        tension: 0.5,
        fill:true,
    },
    {
        //Etiquette du jeu de données
        label : 'Achat denrée boissons',
        // Valeurs des données (statiques pour l'exemple)
        data: [551621, 282102, 870499, 1019634, 812860, 865549, 1004916],
        borderColor: 'blue',
        tension: 0.5,
        fill:true,
    },

]
});
//Options du graphique
let chartOptions = reactive({
//Aspect responsive du graphique
responsive: true,
//les plugins
plugins:{
    //titre du graphique
    title:{
        //affichage
        display:true,
        //Libellé du graphique
        text: 'Dépense et rentrée argent petit bateau par an :',
        // police du texte
        font:{
            size:16
        }
    }
}
});
</script>

<template>
<Line
    :chart-options="chartOptions"
    :chart-data="chartData"
    :chart-id="chartId"
    :dataset-id-key="datasetIdKey"
    :plugins="plugins"
    :css-classes="cssClasses"
    :styles="styles"
    :width="width"
    :height="height"
    />
</template>