<template>
  <div class="max-w-lg mx-auto py-20">
    <Profile :student />
  </div>
</template>

<script setup lang="ts">
import { reactive } from 'vue'

import Profile from '@/components/UiProfile.vue'
import type { Student } from '@/types/student.ts'

const student: Student = reactive({
  name: 'Samuel',
  age: null,
  image: null,
})
</script>
