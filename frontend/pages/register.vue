<template>
  <body class="bg-blue-200 flex justify-center items-center h-screen">

    <div class="w-[40vw] h-4/5 bg-white rounded-md">

      <form class="px-12 pt-6 pb-8 mb-4">
        <div class="text-center py-6">
          <p class="text-3xl font-bold">Register</p>
          <br>
          <p class="font-bold text-gray-500">Sign up for using Mhalong</p>
        </div>
        <div class="mb-6">
          <label class="block text-gray-400 text-sm font-bold mb-2" for="username">
            Username
            <span class="text-red-500">*</span>
          </label>
          <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline" id="username" type="text" placeholder="Username">
          <p class="text-red-500 text-xs">กรุณากรอกข้อมูล</p>
        </div>


        <div class="mb-6">
          <label class="block text-gray-400 text-sm font-bold mb-2" for="password">
            Password
            <span class="text-red-500">*</span>
          </label>
          <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline" id="password" type="password" placeholder="รหัสผ่าน">
          <p class="text-red-500 text-xs">กรุณากรอกข้อมูล</p>
        </div>
        <div class="mb-6">
          <label class="block text-gray-400 text-sm font-bold mb-2" for="password">
            Confirm Password
            <span class="text-red-500">*</span>
          </label>
          <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline" id="confirmPassword" type="password" placeholder="ยืนยันรหัสผ่าน">
          <p class="text-red-500 text-xs">กรุณากรอกข้อมูล</p>
        </div>
        <div class="py-6">
          <button class="bg-blue-500 hover:bg-blue-700 w-full text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" type="button">
            Sign Up
          </button>
        </div>

          <div>
            <span>
              Already have an account?
              <a class="inline-block align-baseline text-md underline text-blue-500 hover:text-blue-800" href="/login">
                Login
              </a>
            </span>
          </div>
      </form>
    </div>
  </body>
</template>

<script setup>

</script>

<style scoped>

</style>
