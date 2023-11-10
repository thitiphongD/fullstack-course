<template>
  <div>
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
    <slot />
  </div>
</template>
<script setup lang="ts">
import { Menu, MenuButton, MenuItem, MenuItems } from '@headlessui/vue'
</script>
