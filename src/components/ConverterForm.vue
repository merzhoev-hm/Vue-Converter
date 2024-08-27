<script setup>
import {  ref, watch } from 'vue'
import FormCurrencySelect from './FormCurrencySelect.vue'
import FormInput from './FormInput.vue'

const emit = defineEmits(['resultFunc'])

const num = ref()
const currencyChange = ref({
  Из: 'USD',
  В: 'RUB'
})

watch(
  [num, currencyChange],
  () => {
    emit('resultFunc', num.value, currencyChange.value)
  },
  { deep: true }
)
</script>

<template>
  <form class="flex flex-col gap-4">
    <FormInput v-model="num" />
    <div class="flex gap-4">
      <FormCurrencySelect v-model="currencyChange['Из']">Из</FormCurrencySelect>
      <FormCurrencySelect v-model="currencyChange['В']">В</FormCurrencySelect>
    </div>
  </form>
</template>
