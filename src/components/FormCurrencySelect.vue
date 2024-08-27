<script setup>
import { inject } from 'vue'

const currencyChange = defineModel()

const { currency } = inject('converter')
</script>

<template>
  <div class="flex gap-2">
    <label for="fromCurrency" class="text-xl font-medium"><slot></slot></label>
    <select class="outline-none border-2 rounded" v-model="currencyChange" id="fromCurrency">
      <option v-for="option in Object.keys(currency)" :key="option">{{ option }}</option>
    </select>
  </div>
</template>
