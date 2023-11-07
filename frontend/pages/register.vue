<template>
  <ModalFail v-model="isShowFailModal" title="สมัครสมาชิกไม่สำเร็จ" :description="registerErrorMessage">
  </ModalFail>
  <ModalSuccess v-model="isShowSuccessModal" title="สมัครสมาชิกสำเร็จ" description="คุณสามารถเข้าสู่ระบบได้เลย" @close="router.push('/login')">
  </ModalSuccess>
  <div class="h-screen flex items-center justify-center lg:bg-blue-400">
    <Head>
      <Title>ลงทะเบียน - Mhalong</Title>
      <Meta name="description" content="My app description"/>
    </Head>
    <form @submit="onSubmit" class="bg-white w-full h-5/6 rounded-md p-6 lg:w-2/5">
      <div class="text-center">
        <p class="text-3xl font-bold">Register</p>
        <p class="text-gray-500">Sign up for using Mhalong</p>
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
                class="border p-1 rounded-md w-full px-2"
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
              class="border p-1 w-full rounded-md px-2"
              placeholder="รหัสผ่าน"
              required
          />
          <span
              class="absolute right-3 top-1/2 transform -translate-y-1/2 cursor-pointer"
              @click="togglePassword('Password')"
          >
            <Icon :name="eyeIconPassword" color="black"/>
          </span>
        </div>
        <p class="text-xs text-red-500">{{ errors.password }}</p>
      </div>
      <div class="mb-2">
        <label for="confirmPassword" class="text-gray-500"
        >Confirm Password<span class="text-red-500">*</span></label
        >
        <div class="relative">
          <input
              v-model="confirmPassword"
              :type="showPasswordConfirm ? 'text' : 'password'"
              id="confirmPassword"
              class="border p-1 w-full rounded-md px-2"
              placeholder="ยืนยันรหัสผ่าน"
              required
          />
          <span
              class="absolute right-3 top-1/2 transform -translate-y-1/2 cursor-pointer"
              @click="togglePassword('Confirm')"
          >
            <Icon :name="eyeIconConfirm" color="black"/>
          </span>
        </div>
        <p class="text-xs text-red-500">{{ errors.confirmPassword }}</p>
      </div>
      <div class="py-2">
        <button
            class="bg-blue-500 hover-bg-blue-700 text-white font-bold py-2 px-4 rounded w-full"
        >
          Sign Up
        </button>
      </div>
      <div class="py-2">
        <p class="text-gray-500">
          Already have an account?
          <NuxtLink to="/login">
            <span class="text-blue-800 underline">Login</span>
          </NuxtLink>
        </p>
      </div>
    </form>
  </div>
</template>

<script lang="ts" setup>
import { useField, useForm } from 'vee-validate'
import { toTypedSchema } from '@vee-validate/zod'
import * as zod from 'zod'
import { ref, computed } from 'vue'
import axios from 'axios'
import ModalFail from '~/components/ModalFail.vue'
import ModalSuccess from '~/components/ModalSuccess.vue'

const router = useRouter()
const isShowSuccessModal = ref<boolean>(false)
const isShowFailModal = ref<boolean>(false)
const showPasswordPassword = ref(false)
const showPasswordConfirm = ref(false)
const registerErrorMessage = ref<string>('')

const togglePassword = (field) => {
  if (field === 'Password') {
    showPasswordPassword.value = !showPasswordPassword.value
  } else if (field === 'Confirm') {
    showPasswordConfirm.value = !showPasswordConfirm.value
  }
}

const eyeIconPassword = computed(() =>
    showPasswordPassword.value ? 'uil:eye' : 'uil:eye-slash',
)

const eyeIconConfirm = computed(() =>
    showPasswordConfirm.value ? 'uil:eye' : 'uil:eye-slash',
)

const validationSchema = toTypedSchema(
    zod.object({
      username: zod.string().min(5, { message: 'กรุณากรอกข้อมูล' }),
      password: zod.string().min(8, { message: 'กรุณากรอกข้อมูล' }),
      confirmPassword: zod.string().min(8, { message: 'กรุณากรอกข้อมูล' }),
    }).refine((data) => data.password === data.confirmPassword, {
      message: 'กรุณากรอกยืนยันรหัสผ่านให้ตรงกัน',
      path: ['confirmPassword'],
    }),
)

const { handleSubmit, errors } = useForm({
  validationSchema,
})

const { value: username } = useField('username')
const { value: password } = useField('password')
const { value: confirmPassword } = useField('confirmPassword')
const onSubmit = handleSubmit((values) => {
  registerErrorMessage.value = ''
  if (values.password != values.confirmPassword) {
    isLoginFail.value = true
  } else {
    axios.post('https://vote-api.mhalong.com/auth/register', {
      username: values.username,
      password: values.password,
      confirmPassword: values.confirmPassword,
    }).then((res) => {
      isShowSuccessModal.value = true
    }).catch((e) => {
      console.error('Error:', e)
      const res = e.response.data
      isShowFailModal.value = true
      for (const [key, value] of Object.entries(res.fields)) {
        registerErrorMessage.value += `${key}: ${value.message}\n`
      }
    })
  }
})
</script>
