<template>
  <div class="flex flex-col p-4 h-[80vh]">
    <div class="flex justify-between items-center gap-2 lg:space-x-4">
      <div class="flex items-center space-x-4">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
             stroke="currentColor" class="w-6 h-6 lg:hidden">
          <path stroke-linecap="round" stroke-linejoin="round" d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5"/>
        </svg>
        <p class="text-[14px] cursor-pointer lg:text-base lg:hidden">ทั้งหมด</p>
        <p class="text-[14px] cursor-pointer lg:text-base lg:hidden">ภาพ</p>
      </div>
      <div class="flex items-center space-x-4">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
             stroke="currentColor" class="w-6 h-6 lg:hidden">
          <path stroke-linecap="round" stroke-linejoin="round"
                d="M14.857 17.082a23.848 23.848 0 005.454-1.31A8.967 8.967 0 0118 9.75v-.7V9A6 6 0 006 9v.75a8.967 8.967 0 01-2.312 6.022c1.733.64 3.56 1.085 5.455 1.31m5.714 0a24.255 24.255 0 01-5.714 0m5.714 0a3 3 0 11-5.714 0"/>
        </svg>

        <p class="hidden text-[8px] lg:text-base lg:block cursor-pointer hover:underline">Gmail</p>
        <p class="hidden text-[8px] lg:text-base lg:block cursor-pointer hover:underline">ค้นรูป</p>
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
             stroke="currentColor" class="w-6 h-6 lg:w-6 lg:h-6 cursor-pointer hover:bg-slate-100 rounded-full">
          <path stroke-linecap="round" stroke-linejoin="round"
                d="M3.75 6A2.25 2.25 0 016 3.75h2.25A2.25 2.25 0 0110.5 6v2.25a2.25 2.25 0 01-2.25 2.25H6a2.25 2.25 0 01-2.25-2.25V6zM3.75 15.75A2.25 2.25 0 016 13.5h2.25a2.25 2.25 0 012.25 2.25V18a2.25 2.25 0 01-2.25 2.25H6A2.25 2.25 0 013.75 18v-2.25zM13.5 6a2.25 2.25 0 012.25-2.25H18A2.25 2.25 0 0120.25 6v2.25A2.25 2.25 0 0118 10.5h-2.25a2.25 2.25 0 01-2.25-2.25V6zM13.5 15.75a2.25 2.25 0 012.25-2.25H18a2.25 2.25 0 012.25 2.25V18A2.25 2.25 0 0118 20.25h-2.25A2.25 2.25 0 0113.5 18v-2.25z"/>
        </svg>
        <img class="rounded-full w-6 h-6 lg:w-12 lg:h-12 cursor-pointer" src="~/assets/imgs/daew.png"
             alt="Profile"/>
      </div>

    </div>
    <form @submit.prevent="onSubmit">
      <div class="flex justify-center h-screen lg:items-center">
        <div class="flex-col">
          <p class="text-center text-4xl font-black text-gray-800 py-10 lg:text-7xl">Google</p>
          <div class="flex justify-center items-center mb-6">

            <div class="relative flex items-center">
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                   stroke="currentColor" class="w-4 h-4 absolute left-3">
                <path stroke-linecap="round" stroke-linejoin="round"
                      d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z"/>
              </svg>

              <input type="text" v-model="search" class="border rounded-full w-[90vw] p-3 px-10 lg:w-[40vw]">

              <div class="absolute right-3 flex gap-4">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                     stroke="currentColor" class="w-4 h-Ï4 cursor-pointer">
                  <path stroke-linecap="round" stroke-linejoin="round"
                        d="M2.25 8.25h19.5M2.25 9h19.5m-16.5 5.25h6m-6 2.25h3m-3.75 3h15a2.25 2.25 0 002.25-2.25V6.75A2.25 2.25 0 0019.5 4.5h-15a2.25 2.25 0 00-2.25 2.25v10.5A2.25 2.25 0 004.5 19.5z"/>
                </svg>
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                     stroke="currentColor" class="w-4 h-4 cursor-pointer">
                  <path stroke-linecap="round" stroke-linejoin="round"
                        d="M12 18.75a6 6 0 006-6v-1.5m-6 7.5a6 6 0 01-6-6v-1.5m6 7.5v3.75m-3.75 0h7.5M12 15.75a3 3 0 01-3-3V4.5a3 3 0 116 0v8.25a3 3 0 01-3 3z"/>
                </svg>
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                     stroke="currentColor" class="w-4 h-4 cursor-pointer">
                  <path stroke-linecap="round" stroke-linejoin="round"
                        d="M6.827 6.175A2.31 2.31 0 015.186 7.23c-.38.054-.757.112-1.134.175C2.999 7.58 2.25 8.507 2.25 9.574V18a2.25 2.25 0 002.25 2.25h15A2.25 2.25 0 0021.75 18V9.574c0-1.067-.75-1.994-1.802-2.169a47.865 47.865 0 00-1.134-.175 2.31 2.31 0 01-1.64-1.055l-.822-1.316a2.192 2.192 0 00-1.736-1.039 48.774 48.774 0 00-5.232 0 2.192 2.192 0 00-1.736 1.039l-.821 1.316z"/>
                  <path stroke-linecap="round" stroke-linejoin="round"
                        d="M16.5 12.75a4.5 4.5 0 11-9 0 4.5 4.5 0 019 0zM18.75 10.5h.008v.008h-.008V10.5z"/>
                </svg>
              </div>
            </div>


          </div>
          <div class="flex justify-center items-center gap-6">
            <button type="submit"
                    class="hidden lg:block lg:border lg:w-48 lg:p-2 lg:rounded-md lg:hover:bg-slate-100">ค้นหาด้วย
              Google
            </button>
            <button @click="onSubmit"
                    class="hidden lg:block lg:border lg:w-48 lg:p-2 lg:rounded-md lg:hover:bg-slate-100">ดีใจจังค้น
              แล้วเจอเลย
            </button>
          </div>
          <p class="text-center py-4">แสดง Google ใน: <a
              class="cursor-pointer text-[#1e40af] hover:underline">English</a></p>
        </div>
      </div>
    </form>
    <footer class="px-4 py-2">
      <div class="py-4">
        <p>ไทย</p>
      </div>
      <div class="flex justify-between flex-col lg:flex-row">
        <div class="hidden lg:flex lg:space-x-4">
          <a href="#" class="cursor-pointer hover:underline">เกี่ยวกับ</a>
          <a href="#" class="cursor-pointer hover:underline">โฆษณา</a>
          <a href="#" class="cursor-pointer hover:underline">ธุรกิจ</a>
          <a href="#" class="hidden lg:block cursor-pointer hover:underline">วิธีการทำงานของ Search</a>
        </div>
        <div class="hidden lg:flex lg:space-x-4">
          <a href="#" class="cursor-pointer hover:underline">ความเป็นส่วนตัว</a>
          <a href="#" class="cursor-pointer hover:underline">ข้อกำหนด</a>
          <a href="#" class="cursor-pointer hover:underline">การตั้งค่า</a>
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup>
const router = useRouter()
const search = ref('')

const onSubmit = () => {
  router.push({
    path: 'google-search',
    query: { q: search.value },
  })
}

</script>
