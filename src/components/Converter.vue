<script setup>
import { onMounted, provide, ref } from 'vue'

import axios from 'axios'
import ConverterForm from './ConverterForm.vue'

const currency = ref([])
const result = ref(0)

async function fetchCurrencyRates() {
  try {
    const { data } = await axios.get('https://open.exchangerate-api.com/v6/latest')
    currency.value = data.rates
  } catch (error) {
    console.error('Ошибка при получении данных о курсах валют:', error)
  }
}

function resultFunc(num, currencyChange) {
  result.value = (
    (currency.value[currencyChange['В']] / currency.value[currencyChange['Из']]) *
    num
  ).toFixed(2)
}

onMounted(async () => {
  await fetchCurrencyRates()
})
provide('converter', { currency })
</script>

<template>
  <div class="justify-center n border p-5 w-96 min-h-60 flex flex-col gap-5 bg-white rounded-xl">
    <h1 class="text-3xl font-medium">Конвертер валют</h1>
    <ConverterForm @resultFunc="resultFunc" />
    <div>
      <h2 class="text-2xl font-medium">Результат: {{ result }}</h2>
    </div>
  </div>
</template>
