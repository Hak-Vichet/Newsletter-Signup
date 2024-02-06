<template>
  <div
    class="absolute w-full h-screen flex items-center justify-center bg-slate-600/50 z-50"
  >
    <div
      class="flex flex-col md:w-[300px] md:h-auto h-full bg-white md:rounded-2xl p-8 md:space-y-4 space-y-6"
    >
      <img
        src="/checkmark-96.png"
        alt="image"
        class="md:w-10 w-20 md:mt-0 mt-20"
      />
      <h1 class="text-3xl font-bold">Thanks for subscribing!</h1>
      <p class="text-xs text-gray-600">
        A confirmation email has been sent to
        <span class="font-bold">{{ props.getUserEmail }}.</span> Please open
        it and click the button to confirm your subscription.
      </p>
      <div class="flex flex-1"></div>
      <button @click="$emit('closeCard')" class="bg-red-500 w-full text-xs text-white py-3 rounded-lg">
        Dismiss message
      </button>
    </div>
  </div>
</template>

<script setup>
import { ref, defineEmits, defineProps } from 'vue'

defineEmits(['closeCard'])

const props = defineProps({
    getUserEmail: String
})
console.log('The user email: ', props.getUserEmail)


</script>
