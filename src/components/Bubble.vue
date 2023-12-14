<script setup>
import { reactive } from 'vue'

import { Bubble } from 'vue-chartjs'

import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  PointElement,
  LinearScale,
} from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, PointElement, LinearScale)

const propChart = defineProps({
        chartId:            { type: String,         default: 'bubble-chart'      }, // Id du graphique
        datasetIdKey:       { type: String,         default: 'label'          }, // Id du dataSet
        width:              { type: Number,         default: 300              }, // Hauteur du graphe
        height:             { type: Number,         default: 300              }, // Largeur du graphe
        cssClasses:         { type: String,         default: ''               }, // Classes css utilisées
        styles:             { type: Object,         default: () => {}         }, // Styles utilisés
        plugins:            { type: Object,         default: () => {}         }  // plugins utilisés
    })
    const chartData = {
      datasets: [
        {
          label: 'Bubulle 1',
          backgroundColor: '#f87979',
          data: [
            {
              x: 20,
              y: 25,
              r: 5
            },
            {
              x: 40,
              y: 10,
              r: 10
            },
            {
              x: 30,
              y: 22,
              r: 30
            }
          ]
        },
        {
          label: 'Bourgogne',
          backgroundColor: '#7C8CF8',
          data: [
            {
              x: 30,
              y: 27,
              r: 15
            },
            {
              x: 20,
              y: 20,
              r: 10
            },
            {
              x: 25,
              y: 15,
              r: 30
            }
          ]
        }
      ]
    }

    const chartOptions = {
      responsive: true,
      maintainAspectRatio: false
    }
</script>

<template>
    
    <Bubble
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
