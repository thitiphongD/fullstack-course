<template>
  <ModalFail
    v-model="isShowFailModal"
    title="ไม่สามารถเข้าสู่ระบบได้"
    description="email or password is an invalid"
  >
  </ModalFail>
  <div class="h-screen flex items-center justify-center lg:bg-blue-400">
    <Head>
      <Title>เข้าสู่ระบบ - Mhalong</Title>
      <Meta name="description" content="My app description" />
    </Head>
    <form
      @submit="onSubmit"
      class="bg-white w-full h-5/6 rounded-md p-6 lg:w-2/5"
    >
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
          <p class="text-xs text-red-500">{{ errors.username }}</p>
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
        <p class="text-xs text-red-500">{{ errors.password }}</p>
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
          <NuxtLink to="/register">
            <span class="text-blue-800 underline">Register</span>
          </NuxtLink>
        </p>
      </div>
    </form>
  </div>
</template>
<script setup lang="ts">
import { useField, useForm } from "vee-validate";
import { toTypedSchema } from "@vee-validate/zod";
import * as zod from "zod";
import { ref, computed } from "vue";
import axios from "axios";
import ModalFail from "~/components/ModalFail.vue";
const router = useRouter();

const isShowFailModal = ref<boolean>(false);
const showPasswordPassword = ref(false);
const loginErrorMessage = ref<string>("");

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
    username: zod.string().min(5, { message: "กรุณากรอกข้อมูล" }),
    password: zod.string().min(8, { message: "กรุณากรอกข้อมูล" }),
  })
);
const { handleSubmit, errors } = useForm({
  validationSchema,
});
const { value: username } = useField("username");
const { value: password } = useField("password");

const onSubmit = handleSubmit((values) => {
  axios
    .post("https://vote-api.mhalong.com/auth/login", {
      username: values.username,
      password: values.password,
    })
    .then((res) => {
    const data = res.data;
    for (const [key, value] of Object.entries(data)) {
      localStorage.setItem(key, value);
    }
      sessionStorage.setItem("sessionTimeout", String(Date.now() + 1800000));
      router.push("/home");
    })
    .catch((e) => {
      console.error("Error:", e);
      const res = e.response.data;
      isShowFailModal.value = true;
      for (const [key, value] of Object.entries(res.fields)) {
        loginErrorMessage.value += `${key}: ${value.message}\n`;
      }
    });
});
</script>

<!--
https://vote-api.mhalong.com/auth/login
--->
