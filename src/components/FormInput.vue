<script setup>
const num = defineModel()
</script>

<template>
  <div class="flex gap-2">
    <label class="text-xl font-medium" for="amount">Сумма:</label>
    <input
      class="outline-none w-36 border-2 pl-2"
      type="number"
      id="amount"
      placeholder="Введите сумму"
      v-model="num"
    />
  </div>
</template>
