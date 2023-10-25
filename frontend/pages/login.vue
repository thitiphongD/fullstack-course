<template>
  <div class="h-screen bg-blue-500 flex items-center justify-center">
    <Head>
      <Title>เข้าสู่ระบบ - Mhalong</Title>
      <Meta name="description" content="My app description" />
    </Head>
    <form class="bg-white w-2/5 h-4/5 rounded-md p-6 novalidate">
      <div class="text-center">
        <p class="text-2xl">Welcome back!</p>
        <p>Sign in to continue using Mhalong</p>
      </div>
      <div class="mt-4 flex flex-col">
        <div class="mb-2">
          <label for="username">Username</label>
          <div class="flex items-center">
            <input
              type="text"
              id="username"
              class="border p-2 rounded-md w-full"
              placeholder="Username"
              required
            />
          </div>
        </div>

        <div class="mb-2">
          <label for="password">Password</label>
          <div class="relative">
            <input
              v-model="password"
              :type="showPasswordPassword ? 'text' : 'password'"
              id="password"
              class="border p-2 w-full rounded-md"
              placeholder="รหัสผ่าน"
              required
            />
            <span
              class="absolute right-3 top-1/2 transform -translate-y-1/2 cursor-pointer"
              @click="togglePasswordVisibility('Password')"
            >
              <Icon :name="eyeIconPassword" color="black" />
            </span>
          </div>
        </div>

        <div class="py-6">
          <button
            class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded w-full"
          >
            Sign In
          </button>
        </div>
        <div class="py-2">
          <p>
            Don’t have an account?
            <a href="/register" class="text-blue-800 underline">Register</a>
          </p>
        </div>
      </div>
    </form>
  </div>
</template>

<script setup>
import { ref, computed } from "vue";

const password = ref("");

const showPasswordPassword = ref(false);

const togglePasswordVisibility = (field) => {
  if (field === "Password") {
    showPasswordPassword.value = !showPasswordPassword.value;
  }
};

const eyeIconPassword = computed(() =>
  showPasswordPassword.value ? "uil:eye" : "uil:eye-slash"
);
</script>

<style scoped></style>
