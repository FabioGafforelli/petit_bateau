<script setup>
    import { reactive, ref, onMounted } from 'vue';
// import d'un graphique type doughnut
    import { Doughnut } from 'vue-chartjs'
    import { aleatoire, densite } from '@/composables/commonChart.js'

    import { Chart as ChartJS, Title, Tooltip, Legend, ArcElement, CategoryScale} from 'chart.js'

    //elements utilisés potentiellement pour notre graphique
    ChartJS.register(Title, Tooltip, Legend, ArcElement, CategoryScale)

    const propChart = defineProps ({
        chartID: { type: String, default: 'doughnut-chart'},
        datasetIdKey: { type: String, default: 'label'},
        width: { type: Number, default: 50},
        height: { type: Number, default: 50},
        cssClasses: { type: String, default: ""},
        styles: { type: Object, default: () => {}},
        plugins: { type: Object, default: () => {}},
    })

    const chartData = reactive({
        //labels vide
        labels:['0 - Indemne', '1 - Blessé léger', '2 - Blessé hospitalisé', '3 - Tué'],
        datasets: [
            {
                data: [24, 215, 194, 15],
                backgroundColor: ['pink', 'yellow','red','blue'],
                borderColor: [],
                borderWidth:1
            }
        ]
    })
    // Selection mode aleatoire/ dégradé
   // Pour la liste déroulante
   let modeSelected = ref()
   // Par défaut : false, mode dégradé
   modeSelected.value = false

   let baseColor = ref()
   // Fonction appelé lorsque le type de coloration à changé
   const selectMode = () =>{
    let bgColor = null
    let bdColor = null
   
    if(modeSelected.value){
      [bgColor, bdColor] = aleatoire(chartData.labels)
    }else{
      [bgColor, bdColor] = densite(baseColor.value,chartData.datasets[0].data)
    }
   // Mise a jour des couleurs du graphe
   chartData.datasets[0].backgroundColor   = bgColor
   chartData.datasets[0].borderColor       = bdColor
   chartData.datasets[0].borderWidth       = 1
  }
</script>

<template>
		<main id="heading1" class="grid grid-flow-row-dense grid-cols-[repeat(auto-fit,minmax(350px,1fr))]">
    <div class="container">
        <Doughnut
        :chart-options="chartOptions"
        :chart-data="chartData"
        :chart-id="chartID"
        :dataset-id-key="datasetIdKey"
        :plugins="plugins"
        :css-classes="cssClasses"
        :styles="styles"
        :width="width"
        :height="height"
        />
    </div>
    <div class="custom-control custom-switch">
      <input type="checkbox" class="custom-control-input"
      id="customSwitch1" v-model="modeSelected" @change="selectMode">
      <label class="custom-control-label" for="customSwitch1">
        couleur aléatoire
      </label>
    </div>
		</main>
</template>