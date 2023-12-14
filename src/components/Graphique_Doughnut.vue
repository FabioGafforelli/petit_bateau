<script setup>
    import { reactive, ref, onMounted } from 'vue';
// import d'un graphique type doughnut
    import { Doughnut } from 'vue-chartjs'

    import { Chart as ChartJS, Title, Tooltip, Legend, ArcElement, CategoryScale} from 'chart.js'

    //elements utilisés potentiellement pour notre graphique
    ChartJS.register(Title, Tooltip, Legend, ArcElement, CategoryScale)

    const propChart = defineProps ({
        chartID: { type: String, default: 'doughnut-chart'},
        datasetIdKey: { type: String, default: 'label'},
        width: { type: Number, default: 500},
        height: { type: Number, default: 500},
        cssClasses: { type: String, default: ""},
        styles: { type: Object, default: () => {}},
        plugins: { type: Object, default: () => {}},
    })

    const chartData = reactive({
        //labels vide
        labels:[' année 1', 'année 2', 'année 4', 'année 5', 'année 6', 'année 7', 'année 8'],
        datasets: [
            {
                data: [28070, 24141, 43509, 50294, 40817, 42294, 51209],
                backgroundColor: ['lightblue', 'blue','purple', 'pink', 'green', 'lime', 'red' ],
                borderColor: [],
                borderWidth:1
            }
        ]
    })
</script>

<template>
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
</template>