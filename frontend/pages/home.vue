<template>
  <Head>
    <Title>Vote System - Mhalong</Title>
    <Meta name="description" content="My app description"/>
  </Head>
  <div class="h-screen lg:bg-blue-400">

    <nav class="relative flex flex-wrap items-center justify-between px-3 py-3 bg-gray-800 mb-3">
      <div class="container px-4 mx-auto flex flex-wrap items-center justify-between">
        <div class="w-full relative flex justify-between lg:w-auto  px-4 lg:static lg:block lg:justify-start">
          <NuxtLink
              class="text-sm font-bold leading-relaxed inline-block mr-4 py-2 text-xl whitespace-nowrap text-white"
              to="/home">
            Mhalong
          </NuxtLink>
        </div>
        <div class="lg:flex lg:flex-grow items-center">
          <ul class="flex flex-col lg:flex-row list-none ml-auto">
            <li class="nav-item">
              <p class="px-3 py-2 flex items-center text-xl font-bold leading-snug text-white hover:opacity-75 cursor-pointer">
                username</p>
            </li>
          </ul>
        </div>
      </div>
    </nav>

    <div class="px-32 py-10">
      <p class="text-3xl font-bold">All Posts <span>(0)</span></p>
      <div class="py-5">
        <div class="flex items-center justify-between">
          <div class="flex items-center space-x-2">
            <p>Sort</p>
            <Icon name="material-symbols:keyboard-arrow-down" color="black" />
          </div>
          <input class="border rounded-md p-2" placeholder="ค้าหา...">
        </div>

        <div class="grid grid-cols-2 md:grid-cols-3 grid-rows-3 md:grid-rows-2 gap-4 py-10">
          <div class="bg-white row-span-1 col-span-1 rounded-md h-40 p-3">
            <div class="flex items-center justify-between">
              <p class="text-blue-400 font-bold text-2xl">Title</p>
              <button class="group border border-blue-400 rounded-md py-1 px-3 cursor-pointer text-blue-400 font-bold active:text-white active:bg-blue-400 transition-all duration-300">
                1 votes
              </button>


            </div>
            <div class="py-2 h-2/4">
              <p class="text-sm text-gray-400">Like so many organizations these days, Autodesk is a company in
                transition. It was until recently a traditional boxed software company
                selling licenses. Yet its own business model disruption is only part of
                the story
              </p>
            </div>
            <hr class="h-px bg-gray-400 border-0">
            <div class="flex items-center justify-between">
              <div class="flex items-center py-2 space-x-1">
                <span class="text-sm text-gray-400">By</span>
                <span class="text-sm text-gray-400">username</span>
              </div>
              <p class="text-sm text-gray-400">19 ก.ย. 2566 8:58:15 PM</p>
            </div>
          </div>

          <div class="bg-white rounded-md">
            <span>02</span>
          </div>
          <div class="bg-white rounded-md">
            <span>03</span>
          </div>
          <div class="bg-white rounded-md">
            <span>04</span>
          </div>
          <div class="bg-white rounded-md">
            <span>05</span>
          </div>
          <div class="bg-white rounded-md">
            <span>06</span>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<script setup lang="ts">

</script>

<style scoped>

</style>
