<script setup lang="ts">
import { ref, type Ref } from 'vue';
import TemTem from './TemTem.vue';
import type {
  TemTemApiTem,
  TemTemApiType,
  TemTemApiWeaknesses,
} from '@maael/temtem-types';

type TemApiResponse = (TemTemApiTem & { weaknesses: TemTemApiWeaknesses })[]

function hackInTypes(temTemData: TemApiResponse) {
  return temTemData.map((tem) => ({
    ...tem,
    types: tem.types.map(t => types?.find(ot => ot.name === t)),
  }))
}

const searchText = ref('')
var tems: Ref<TemTemApiTem[]> = ref([])
var types: TemTemApiType[] = []

fetch('https://temtem-api.mael.tech/api/types')
  .then(response => response.json())
  .then(data => {
    types = data
    fetch('https://temtem-api.mael.tech/api/temtems?weaknesses=true')
      .then(response => response.json())
      .then(data => tems = (hackInTypes(data) as any));
  })


function normalise(input: string): string {
  return input.toLowerCase()
}

function search(term: string | undefined, tems: any[]) {
  if (term === "" || term === undefined) {
    return tems
  } else {
    return tems.filter(tem => {
      const termNormalised = normalise(term)
      console.log(termNormalised)
      return normalise(tem.name).includes(termNormalised) ||
        tem.number.toString().includes(termNormalised) ||
        tem.types.some((type: { name: string, icon: string }) => normalise(type.name).includes(termNormalised))
    })
  }
}
</script>

<template>
  <input v-model="searchText" type="text" placeholder="Temtem Name">
  <TemTem v-for="tem in search(searchText, tems)" :key="tem.number" :data="tem" />
</template>
