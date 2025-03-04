<template>
  <VueUiSparkbar :dataset="dataset" style="width: 300px" />
  <VueUiSparkHistogram :dataset="dataset2" style="width: 900px" />
  {{ JSON.stringify(repoData) }}
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue";
import octokit from "@/services"

import {
  VueUiSparkbar,
  type VueUiSparkbarDatasetItem,
  type VueUiSparkbarConfig
} from "vue-data-ui";

import {
  VueUiSparkHistogram,
  type VueUiSparkHistogramDatasetItem,
  type VueUiSparkHistogramConfig
} from "vue-data-ui";

const dataset: VueUiSparkbarDatasetItem[] = [
  {
    name: "quality",
    value: 61.953,
    rounding: 2,
    suffix: "%",
  },
  {
    name: "popularity",
    value: 20.0412,
    rounding: 2,
    suffix: "%",
  },
  {
    name: "maintenance",
    value: 33.3291,
    rounding: 2,
    suffix: "%",
  },
]

const dataset2: VueUiSparkHistogramDatasetItem[] = [
  { "value": 1.2, "valueLabel": "20%", "timeLabel": "09:00", "intensity": 0.2 },
  { "value": 1.3, "valueLabel": "50%", "timeLabel": "10:00", "intensity": 0.5 },
  { "value": 1.1, "valueLabel": "60%", "timeLabel": "11:00", "intensity": 0.6 },
  { "value": 0.8, "valueLabel": "70%", "timeLabel": "12:00", "intensity": 0.7 },
  { "value": 2, "valueLabel": "100%", "timeLabel": "13:00", "intensity": 1 },
  { "value": 2.1, "valueLabel": "100%", "timeLabel": "14:00", "intensity": 1 },
  { "value": 2.3, "valueLabel": "80%", "timeLabel": "15:00", "intensity": 0.8 },
  { "value": 2.1, "valueLabel": "70%", "timeLabel": "16:00", "intensity": 0.7 },
  { "value": 0.9, "valueLabel": "60%", "timeLabel": "17:00", "intensity": 0.6 },
  { "value": 0.7, "valueLabel": "50%", "timeLabel": "18:00", "intensity": 0.5 },
  { "value": 0.3, "valueLabel": "30%", "timeLabel": "19:00", "intensity": 0.3 },
  { "value": 0.2, "valueLabel": "20%", "timeLabel": "20:00", "intensity": 0.2 }
]

const repoData = ref()

onMounted(async () => {
  repoData.value = await octokit.request('GET /repos/{owner}/{repo}', {
    owner: 'SHFeMIX',
    repo: 'github-fashion-show',
    headers: {
      'X-GitHub-Api-Version': '2022-11-28'
    }
  })
})

</script>
