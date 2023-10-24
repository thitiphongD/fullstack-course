<template>
  <div class="pb-6">
    <div class="flex items-center space-x-1 px-1 cursor-pointer">
      <img class="rounded-full w-6 h-6" :src="item.icon">
      <div class="px-1">
        <p class="text-xs">{{ item.name }}</p>
        <p class="text-xs">{{ item.link }}</p>
      </div>
    </div>
    <div class="py-1">
      <p class="text-xl cursor-pointer hover:underline text-blue-800">{{ item.title }}</p>
      <p class="text-xs">{{ item.detail }}</p>
    </div>
  </div>
</template>
<script lang="ts" setup>
defineProps<{
  item : {
    icon : string,
    name : string,
    link : string,
    title : string,
    detail : string
  }
}>()
</script>
