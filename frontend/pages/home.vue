<template>
  <TransitionRoot appear :show="isOpen" as="template">
    <Dialog as="div" @close="closeModal" class="relative z-10">
      <TransitionChild
        as="template"
        enter="duration-300 ease-out"
        enter-from="opacity-0"
        enter-to="opacity-100"
        leave="duration-200 ease-in"
        leave-from="opacity-100"
        leave-to="opacity-0"
      >
        <div class="fixed inset-0 bg-black bg-opacity-75" />
      </TransitionChild>

      <div class="fixed inset-0 overflow-y-auto">
        <div
          class="flex min-h-full items-center justify-center p-4 text-center"
        >
          <TransitionChild
            as="template"
            enter="duration-300 ease-out"
            enter-from="opacity-0 scale-95"
            enter-to="opacity-100 scale-100"
            leave="duration-200 ease-in"
            leave-from="opacity-100 scale-100"
            leave-to="opacity-0 scale-95"
          >
            <DialogPanel
              class="w-1/3 transform overflow-hidden rounded-2xl bg-white p-6 text-left align-middle shadow-xl transition-all"
            >
              <button
                type="button"
                class="text-2xl absolute top-0 right-0 h-16 w-16"
                @click="closeModal"
              >
                <Icon name="material-symbols:cancel-rounded" color="black" />
              </button>
              <DialogTitle
                as="h3"
                class="text-2xl text-center font-medium leading-6 text-gray-900"
              >
                New Post
              </DialogTitle>

              <div class="mt-2">
                <form @submit="onSubmit">
                  <div class="mb-6">
                    <label
                      for="name"
                      class="block mb-2 text-lg font-medium text-gray-500"
                      >Name<span class="text-red-700">*</span></label
                    >
                    <input
                      type="text"
                      v-model="namePost"
                      class="border text-gray-900 text-sm rounded-lg w-full p-2.5"
                      placeholder="Name"
                    />
                  </div>
                  <div class="mb-6">
                    <label
                      for="description"
                      class="block mb-2 text-lg font-medium text-gray-500"
                      >Description</label
                    >
                    <textarea
                      name="description"
                      v-model="descriptionPost"
                      rows="3"
                      class="w-full h-48 rounded-md p-2.5 border text-gray-700"
                    ></textarea>
                  </div>
                  <button
                    type="submit"
                    class="text-white bg-blue-500 hover:bg-blue-300 w-full p-2 rounded-md"
                  >
                    Submit
                  </button>
                </form>
              </div>
            </DialogPanel>
          </TransitionChild>
        </div>
      </div>
    </Dialog>
  </TransitionRoot>
  <TransitionRoot appear :show="isOpenVote" as="template">
    <Dialog as="div" @close="closeVoteModal" class="relative z-10">
      <TransitionChild
        as="template"
        enter="duration-300 ease-out"
        enter-from="opacity-0"
        enter-to="opacity-100"
        leave="duration-200 ease-in"
        leave-from="opacity-100"
        leave-to="opacity-0"
      >
        <div class="fixed inset-0 bg-black/25" />
      </TransitionChild>

      <div class="fixed inset-0 overflow-y-auto">
        <div
          class="flex min-h-full items-center justify-center p-4 text-center"
        >
          <TransitionChild
            as="template"
            enter="duration-300 ease-out"
            enter-from="opacity-0 scale-95"
            enter-to="opacity-100 scale-100"
            leave="duration-200 ease-in"
            leave-from="opacity-100 scale-100"
            leave-to="opacity-0 scale-95"
          >
            <DialogPanel
              class="w-full max-w-md transform overflow-hidden rounded-2xl bg-white p-6 text-left align-middle shadow-xl transition-all"
            >
              <DialogTitle
                as="h3"
                class="text-lg font-medium leading-6 text-gray-900"
              >
                <DialogTitle
                  as="h3"
                  class="text-lg font-medium leading-6 text-gray-900"
                >
                  {{ voteTitle }}
                </DialogTitle>
              </DialogTitle>
              <div class="mt-2">
                <p class="text-sm text-gray-500">{{ voteDescription }}</p>
              </div>

              <div class="mt-4">
                <button
                  type="button"
                  class="inline-flex justify-center rounded-md border border-transparent bg-blue-100 px-4 py-2 text-sm font-medium text-blue-900 hover:bg-blue-200 focus:outline-none focus-visible:ring-2 focus-visible:ring-blue-500 focus-visible:ring-offset-2"
                  @click="closeVoteModal"
                >
                  Got it, thanks!
                </button>
              </div>
            </DialogPanel>
          </TransitionChild>
        </div>
      </div>
    </Dialog>
  </TransitionRoot>

  <Head>
    <Title>Vote System - Mhalong</Title>
    <Meta name="description" content="My app description" />
  </Head>
  <div class="h-screen lg:bg-blue-400">
    <nav
      class="relative flex flex-wrap items-center justify-between px-3 py-3 bg-gray-800 mb-3"
    >
      <div
        class="container px-4 mx-auto flex flex-wrap items-center justify-between"
      >
        <div
          class="w-full relative flex justify-between lg:w-auto px-4 lg:static lg:block lg:justify-start"
        >
          <NuxtLink
            class="text-sm font-bold leading-relaxed inline-block mr-4 py-2 whitespace-nowrap text-white"
            to="/home"
          >
            Mhalong
          </NuxtLink>
          <button
            type="button"
            @click="openVoteModal"
            class="rounded-md bg-black/20 px-4 py-2 text-sm font-medium text-white hover:bg-black/30 focus:outline-none focus-visible:ring-2 focus-visible:ring-white/75"
          >
            Open dialog
          </button>
        </div>
        <div class="lg:flex lg:flex-grow items-center">
          <ul class="flex flex-col lg:flex-row list-none ml-auto">
            <li class="nav-item">
              <Menu as="div" class="relative inline-block text-left">
                <div>
                  <MenuButton
                    class="inline-flex w-full justify-center rounded-md text-xl text-white font-bold"
                  >
                    {{ username }}
                  </MenuButton>
                </div>
                <transition
                  enter-active-class="transition duration-100 ease-out"
                  enter-from-class="transform scale-95 opacity-0"
                  enter-to-class="transform scale-100 opacity-100"
                  leave-active-class="transition duration-75 ease-in"
                  leave-from-class="transform scale-100 opacity-100"
                  leave-to-class="transform scale-95 opacity-0"
                >
                  <MenuItems
                    class="absolute right-0 mt-2 w-56 origin-top-right divide-y divide-gray-100 rounded-md bg-white shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none"
                  >
                    <div class="px-1 py-1">
                      <MenuItem v-slot="{ active }">
                        <button
                          type="button"
                          @click="openModal"
                          :class="[
                            active ? 'bg-blue-500 text-white' : 'text-gray-900',
                            'group flex w-full items-center rounded-md px-2 py-2 text-sm',
                          ]"
                        >
                          New Post
                        </button>
                      </MenuItem>
                    </div>

                    <div class="px-1 py-1">
                      <MenuItem v-slot="{ active }">
                        <button
                          :class="[
                            active ? 'bg-blue-500 text-white' : 'text-gray-900',
                            'group flex w-full items-center rounded-md px-2 py-2 text-sm',
                          ]"
                        >
                          Your Posts
                        </button>
                      </MenuItem>
                      <MenuItem v-slot="{ active }">
                        <NuxtLink to="/login">
                          <button
                            :class="[
                              active
                                ? 'bg-blue-500 text-white'
                                : 'text-gray-900',
                              'group flex w-full items-center rounded-md px-2 py-2 text-sm',
                            ]"
                          >
                            Logout
                          </button>
                        </NuxtLink>
                      </MenuItem>
                    </div>
                  </MenuItems>
                </transition>
              </Menu>
            </li>
          </ul>
        </div>
      </div>
    </nav>

    <div class="px-32 py-10">
      <p class="text-3xl font-bold">
        All Posts <span>({{ countVote }})</span>
      </p>
      <div class="py-5">
        <div class="flex items-center justify-between">
          <div class="flex items-center space-x-2">
            <Menu as="div" class="relative inline-block text-left">
              <div>
                <MenuButton
                  class="inline-flex w-full justify-center rounded-md items-center px-4 py-2"
                >
                  Sort
                  <Icon name="material-symbols:keyboard-arrow-down" />
                </MenuButton>
              </div>

              <transition
                enter-active-class="transition duration-100 ease-out"
                enter-from-class="transform scale-95 opacity-0"
                enter-to-class="transform scale-100 opacity-100"
                leave-active-class="transition duration-75 ease-in"
                leave-from-class="transform scale-100 opacity-100"
                leave-to-class="transform scale-95 opacity-0"
              >
                <MenuItems
                  class="absolute left-0 mt-2 w-56 origin-top-right divide-y divide-gray-100 rounded-md bg-white shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none"
                >
                  <div class="px-1 py-1">
                    <MenuItem v-slot="{ active }">
                      <button
                        :class="[
                          active ? 'bg-blue-500 text-white' : 'text-gray-900',
                          'group flex w-full items-center rounded-md px-2 py-2 text-sm',
                        ]"
                      >
                        Newest
                      </button>
                    </MenuItem>
                    <MenuItem v-slot="{ active }">
                      <button
                        :class="[
                          active ? 'bg-blue-500 text-white' : 'text-gray-900',
                          'group flex w-full items-center rounded-md px-2 py-2 text-sm',
                        ]"
                      >
                        Most votes
                      </button>
                    </MenuItem>
                  </div>
                </MenuItems>
              </transition>
            </Menu>
          </div>
          <div class="mb-3">
            <div class="relative mb-4 flex w-full flex-wrap items-stretch">
              <input
                type="search"
                class="relative w-56 flex-auto rounded-md border p-2 shadow-md"
                placeholder="Search"
                aria-label="Search"
                aria-describedby="button-addon1"
              />
              <button
                class="relative flex items-center text-lg bg-blue-500 px-2 text-white shadow-md"
                type="button"
                id="button-addon1"
                data-te-ripple-init
                data-te-ripple-color="light"
              >
                <Icon name="material-symbols:search" />
              </button>
            </div>
          </div>
        </div>

        <div
          class="grid grid-cols-2 md:grid-cols-3 grid-rows-3 md:grid-rows-2 gap-4 py-10"
        >
          <div
            class="bg-white row-span-1 col-span-1 rounded-md h-40 p-3 cursor-pointer"
            v-for="(item, i) in items"
            :key="i"
            @click="openVoteModal(item)"
          >
            <div class="flex items-center justify-between">
              <p class="text-blue-400 font-bold text-xl w-4/5 truncate">
                {{ item.name }}
              </p>
              <button
                class="group border border-blue-400 rounded-md py-1 w-24 cursor-pointer text-blue-400 font-bold transition-all duration-300 hover:bg-blue-400 hover:text-white active:bg-blue-200 active:text-white focus:outline-none"
              >
                1 votes
              </button>
            </div>
            <div class="py-2 h-2/4">
              <p class="text-sm text-gray-400 line-clamp-2">
                {{ item.description }}
              </p>
            </div>
            <hr class="h-px bg-gray-400 border-0" />
            <div class="flex items-center justify-between">
              <div class="flex items-center py-2 space-x-1">
                <span class="text-sm text-gray-400">By</span>
                <span class="text-sm text-gray-400">{{
                  item.user.username
                }}</span>
              </div>
              <p class="text-sm text-gray-400">{{ dayjs(item.created_at) }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
import {
  Menu,
  MenuButton,
  MenuItems,
  MenuItem,
  TransitionRoot,
  TransitionChild,
  Dialog,
  DialogPanel,
  DialogTitle,
} from "@headlessui/vue";
import { ref, computed } from "vue";
import axios from "axios";
import dayjs from "dayjs";
import { number } from "zod";
const router = useRouter();
const token =
  typeof window !== "undefined" ? localStorage.getItem("access_token") : null;
const username =
  typeof window !== "undefined" ? localStorage.getItem("username") : null;
if (token == null || token == "") {
  router.push("/login");
}
// const voteItems = ref([])
const items = ref([]);
const countVote = ref<number>(0);
onMounted(() => {
  axios
    .get(
      "https://vote-api.mhalong.com/posts?limit=30&page=1&q=&order_by=posts.created_at+DESC",
      {
        headers: {
          Authorization: localStorage.getItem("access_token"),
        },
      }
    )
    .then((res) => {
      countVote.value = res.data.count;
      items.value = res.data.items;
    })
    .catch((e) => {
      console.error("Error:", e);
    });
});

const isOpen = ref<boolean>(false);
const closeModal = (): void => {
  isOpen.value = false;
};
const openModal = (): void => {
  isOpen.value = true;
};

const isOpenVote = ref<boolean>(false);
const voteTitle = ref<string>("");
const voteDescription = ref<string>("");
const openVoteModal = (item: any): void => {
  isOpenVote.value = true;
  voteTitle.value = item.name;
  voteDescription.value = item.description;
};

const closeVoteModal = (): void => {
  isOpenVote.value = false;
};

const namePost = ref<string>("");
const descriptionPost = ref<string>("");
const onSubmit = (values: any) => {
  values.preventDefault();
  const name = namePost.value;
  const description = descriptionPost.value;
};
// https://vote-api.mhalong.com/posts/26736f2b-816e-4b74-b1b2-8bc51f8876ee/votes
</script>

<style scoped></style>
