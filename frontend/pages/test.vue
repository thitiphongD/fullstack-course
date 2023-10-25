<template>
  <div class="h-screen bg-blue-500 flex items-center justify-center">
    <Head>
      <Title>เข้าสู่ระบบ - Mhalong</Title>
      <Meta name="description" content="My app description" />
    </Head>
    <form @submit="onSubmit" class="bg-white w-2/5 h-4/5 rounded-md p-6">
      <div class="text-center">
        <p class="text-3xl font-bold">Welcome back!</p>
        <p class="text-gray-500">Sign in to continue using Mhalong</p>
      </div>
      <div class="mt-4 flex flex-col">
        <div class="mb-2">
          <label for="username" class="text-gray-500"
            >Username<span class="text-red-500">*</span></label
          >
          <div class="flex items-center">
            <input
              name="username"
              v-model="username"
              type="text"
              class="border p-2 rounded-md w-full"
              placeholder="Username"
            />
          </div>
          <p class="text-red-500">{{ errors.username }}</p>
        </div>
      </div>

      <div class="mb-2">
        <label for="password" class="text-gray-500"
          >Password<span class="text-red-500">*</span></label
        >
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
            @click="togglePassword('Password')"
          >
            <Icon :name="eyeIconPassword" color="black" />
          </span>
        </div>
        <p class="text-red-500">{{ errors.password }}</p>
      </div>
      <div class="py-6">
        <button
          class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded w-full"
        >
          Sign In
        </button>
      </div>
      <div class="py-2">
        <p class="text-gray-500">
          Don’t have an account?
          <a href="/register" class="text-blue-800 underline">Register</a>
        </p>
      </div>
    </form>
  </div>
</template>
<script setup>
import { useField, useForm } from "vee-validate";
import { toTypedSchema } from "@vee-validate/zod";
import * as zod from "zod";
import { ref, computed } from "vue";

const inputPassword = ref("");
const showPasswordPassword = ref(false);
const togglePassword = (field) => {
  if (field === "Password") {
    showPasswordPassword.value = !showPasswordPassword.value;
  }
};

const eyeIconPassword = computed(() =>
  showPasswordPassword.value ? "uil:eye" : "uil:eye-slash"
);

const validationSchema = toTypedSchema(
  zod.object({
    username: zod
      .string()
      .nonempty("กรุณากรอกข้อมูล")
      .min(8, { message: "กรุณากรอกข้อมูล" }),
    password: zod
      .string()
      .nonempty("กรุณากรอกข้อมูล")
      .min(8, { message: "กรุณากรอกข้อมูล" }),
  })
);
const { handleSubmit, errors } = useForm({
  validationSchema,
});
const { value: username } = useField("username");
const { value: password } = useField("password");
const onSubmit = handleSubmit((values) => {
  alert(JSON.stringify(values, null, 2));
});
</script>
