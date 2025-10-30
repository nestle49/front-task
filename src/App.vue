<template>
  <div class="max-w-lg mx-auto py-20">
    <Profile :student />
  </div>
</template>

<script setup lang="ts">
import Profile from '@/components/UiProfile.vue'
import type { Student } from '@/types/student.ts'
import photo from '@/assets/photo.png'

const student: Student = reactive({
  name: 'Samuel',
  age: 25,
  image: photo
})
</script>
