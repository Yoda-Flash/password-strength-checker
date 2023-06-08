<template>
    <div class="container mx-auto w-64">
      <h1 class="text-xl text-center">Password strength checker</h1>
      <input
        class="
          block
          w-full
          my-1
          p-2
          border border-grey-30
          rounded
          leading-normal
          text-grey-80
        "
        type="text"
        v-model="password"
      />
  
      <PasswordScore
        :value="password"
        class="mt-2 mb-6"
        @passed="isPasswordStrong = true"
        @failed="isPasswordStrong = false"
      />
  
      <button
        class="
          mt-6
          px-6
          py-1
          leading-lg
          select-none
          bg-blue-400
          text-white
          font-semibold
          border border-blue-500
          rounded
        "
        :class="[
          {
            'cursor-not-allowed opacity-50 pointer-events-hover':
              !isPasswordStrong,
          },
        ]"
      >
        Submit
      </button>
    </div>
  </template>
  
  <script>
  import { ref } from 'vue';
  import PasswordScore from './PasswordScore.vue';
  
  export default {
    components: {
      PasswordScore,
    },
  
    setup() {
      const password = ref('');
      const isPasswordStrong = ref(false);
  
      return { password, isPasswordStrong };
    },
  };
  </script>
  