<template>
  <NSpace>
    <div>{{ $t('filters.species') }}</div>
    <NRadioGroup v-model:value="value" name="species">
      <NGrid cols="2" responsive="screen">
        <NGridItem>
          <NRadio id="allspecies" value="all" :label="$t('all')" @change="toggle($event)" />
        </NGridItem>
        <NGridItem v-for="i in data" :key="i">
          <NRadio :id="i" :value="i" :label="$t(`species.${i}`)" @change="toggle($event)" />
        </NGridItem>
      </NGrid>
    </NRadioGroup>
  </NSpace>
</template>

<script setup lang="ts">
import { NGrid, NGridItem, NRadio, NRadioGroup, NSpace } from 'naive-ui'
import { ref } from 'vue'
import { useGlobalStore } from '~/store/global'

defineProps<{
  data: string[]
}>()

const value = ref('all')

const global = useGlobalStore()

const toggle = (event: Event) => global.selectedSpecies = ((event.target as HTMLInputElement).value)
</script>
