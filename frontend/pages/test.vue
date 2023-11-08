<template>
  <div>
    <div>
      {{ dayjs('2020-10-08T07:51:58Z').format('MMM Do YYYY') }}
    </div>
    <form @submit="logToConsole">
      <p>Name</p>
      <input type="text" class="border border-blue-400" v-model="name">
      <button type="submit" class="bg-blue-500 p-2">Print</button>
    </form>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import * as dayjs from 'dayjs'

const name = ref<string>('');

const logToConsole = (event: any) => {
  event.preventDefault(); // Prevent the default form submission
  console.log('Name:', name.value); // Log the input field's value
};
</script>
