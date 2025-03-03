<template>
  <VueUiSparkbar :dataset="dataset" :config="config" style="width: 300px"/>
</template>

<script setup lang="ts">
import {
  VueUiSparkbar,
  type VueUiSparkbarDatasetItem,
  type VueUiSparkbarConfig
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
const config: VueUiSparkbarConfig = {}
</script>
