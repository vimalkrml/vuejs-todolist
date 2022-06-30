<script>
import { ref } from "vue";
export default {
  setup() {
    let show = ref();
    const isOpen = () => (show.value = !show.value);
    return { show, isOpen };
  },
};
</script>

<template>
  <div class="flex justify-between mt-5 px-5">
    <div class="">
      <h1 class="text-3xl font-bold">Users-Lists</h1>
    </div>
    <div class="flex gap-5">
      <h2
        class="
          cursor-pointer
          border-b-2 border-sky-500
          shadow-sky-100 shadow-md
        "
      >
        Signup
      </h2>
      <h2
        class="
          cursor-pointer
          border-b-2 border-sky-500
          shadow-sky-100 shadow-md
        "
      >
        Signin
      </h2>
      <div>
        <div class="relative">
          <!-- Dropdown toggle button -->
          <button
            @click="isOpen"
            class="
              flex
              items-center
              px-1
              py-1
              text-white
              bg-blue-500
              rounded-md
            "
          >
            <span class="mx-auto text-sm">Account</span>
            <svg class="w-5 h-5 text-white dark:text-white" fill="currentColor">
              <path
                fill-rule="evenodd"
                d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z"
                clip-rule="evenodd"
              />
            </svg>
          </button>

          <!-- Dropdown menu -->
          <div
            v-show="show"
            class="
              absolute
              right-0
              py-2
              mt-2
              bg-indigo-500
              rounded-md
              shadow-xl
            "
          >
            <a
              to="/"
              class="
                block
                px-4
                py-2
                text-sm text-indigo-100
                hover:bg-indigo-400 hover:text-indigo-100
              "
            >
              Profile
            </a>
            <a
              to="/"
              class="
                block
                px-4
                py-2
                text-sm text-indigo-100
                hover:bg-indigo-400 hover:text-indigo-100
              "
            >
              Settings
            </a>
            <a
              to="/"
              class="
                block
                px-4
                py-2
                text-sm text-indigo-100
                hover:bg-indigo-400 hover:text-indigo-100
              "
            >
              Signout
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
