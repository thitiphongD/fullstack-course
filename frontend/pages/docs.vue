<template>
  <div
    class="h-screen py-12 flex lg:items-center justify-center w-full"
    :class="{ 'bg-slate-800': changeMode }"
  >
    <div>
      <p
        class="text-center text-3xl font-bold"
        :class="{ 'text-white': changeMode }"
      >
        Login
      </p>
      <Icon
        :name="darkModeIcon"
        @click="toggleDarkMode"
        class="cursor-pointer text-2xl"
        :class="{ 'text-white': changeMode }"
      />
      <div class="mt-4 flex flex-col">
        <div class="mb-2">
          <label for="email" :class="{ 'text-white': changeMode }">Email</label>
          <div class="flex items-center">
            <input type="email" class="border p-2 rounded-lg lg:w-96" />
          </div>
        </div>

        <div class="mb-2">
          <label for="password" :class="{ 'text-white': changeMode }"
            >Password</label
          >
          <div class="relative">
            <input
              :type="showPasswordPassword ? 'text' : 'password'"
              id="password"
              class="border p-2 rounded-lg lg:w-96"
            />
            <span
              class="absolute right-3 top-1/2 transform -translate-y-1/2 cursor-pointer"
              @click="togglePassword('Password')"
            >
              <Icon :name="eyeIconPassword" color="black" />
            </span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { ref, computed } from "vue";

const changeMode = ref(false);
const darkModeIcon = computed(() =>
  changeMode.value ? "iconamoon:mode-dark-light" : "iconamoon:mode-light-thin"
);

const toggleDarkMode = () => {
  changeMode.value = !changeMode.value;
};

const showPasswordPassword = ref(false);
const togglePassword = (field: string) => {
  if (field === "Password") {
    showPasswordPassword.value = !showPasswordPassword.value;
  }
};

const eyeIconPassword = computed(() =>
  showPasswordPassword.value ? "uil:eye" : "uil:eye-slash"
);
</script>

<style scoped></style>
