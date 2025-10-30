<template>
  <div class="max-w-lg mx-auto py-20">
    <Profile :student v-model:age="student.age" /><br><br>

    {{ student }}<br><br>

    <Profile :student="student2" v-model:age="student2.age" /><br><br>

    {{ student }}
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

const student2: Student = reactive({
  name: 'John Doe',
  age: 30,
  image: photo
})
</script>
