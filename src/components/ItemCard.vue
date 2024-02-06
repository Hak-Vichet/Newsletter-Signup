<template>
  <!-- Popup card  -->
  <PopupCard
    v-if="isShowCard"
    :getUserEmail="userInput"
    class="absolute"
    @closeCard="setToCloseCard"
  />

  <div class="h-screen bg-slate-600 flex items-center justify-center">
    <div class="w-[700px] h-full md:h-auto bg-white rounded-2xl">
      <div class="grid md:grid-cols-2 md:gap-x-5">
        <!-- mobile head show  -->
        <div class="md:hidden">
          <img
            src="@/assets/illustration-sign-up-mobile.svg"
            alt="image"
            class="w-full"
          />
        </div>

        <!-- left side  -->
        <div
          class="space-y-5 justify-center flex flex-col md:ml-5 px-6 pb-10 p-5"
        >
          <h1 class="text-4xl font-bold">Stay updated!</h1>
          <p class="text-md">
            Join 60,00+ product managers receiving monthly updates on:
          </p>

          <div class="space-y-2">
            <div class="flex gap-x-3 items-center">
              <img src="/checkmark.png" alt="icon" class="w-4 h-4" />
              <p class="text-xs text">
                Product discovery and building what matters
              </p>
            </div>
            <div class="flex gap-x-3 items-center">
              <img src="/checkmark.png" alt="icon" class="w-4 h-4" />
              <p class="text-xs text">
                Measuring to ensure updates are a success
              </p>
            </div>
            <div class="flex gap-x-3 items-center">
              <img src="/checkmark.png" alt="icon" class="w-4 h-4" />
              <p class="text-xs text">And much more!</p>
            </div>
          </div>

          <!-- email input  -->
          <div class="space-y-1">
            <p class="text-xs font-bold text-gray-600">Email address</p>
            <input
              v-model="userInput"
              type="email"
              class="w-full border border-gray-800 rounded-md p-4 text-xs"
              placeholder="Enter your email"
            />
            <p class="text-xs text-red-500">{{ msg }}</p>
          </div>

          <button
            @click="userSubscript"
            class="text-xs bg-red-500 rounded-md w-full p-5 text-white"
          >
            Subscribe to monthly newsletter
          </button>
        </div>

        <!-- right side  -->
        <div class="items-center justify-center hidden md:flex p-4">
          <img src="@/assets/illustration-sign-up-desktop.svg" alt="image" />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

import PopupCard from "@/components/PopupCard.vue";

const msg = ref("");

const isShowCard = ref(false);
const userInput = ref('');

const userSubscript = () => {
  if (userInput.value.length !== 0) {
    isShowCard.value = true;
    msg.value = "";
    console.log("The usermain: ", userInput.value);
  } else {
    msg.value = "Please enter your email!";
  }
};

const setToCloseCard = () => {
  isShowCard.value = false;
  userInput.value = "";
};
</script>
