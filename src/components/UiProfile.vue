<template>
  <div
    class="ui-profile flex items-center gap-2"
    :class="{
      focused
    }"
  >
    <div class="bg-gray-300 rounded-full w-14 h-14"></div>
    <div class="flex flex-col gap-3">
      <label
        for="hours-old"
        class="font-koulen text-base leading-[15px] tracking-[0.02em]"
        :class="[
          focused ? 'text-[color:var(--ui-primary)]' : 'text-[color:var(--ui-dark)]'
        ]"
      >
        {{ student.name }} is
      </label>

      <div class="flex gap-3 items-center">
        <input
          ref="input"
          name="hours-old"
          id="hours-old"
          class="border-b-gray-300 border-b w-[50px]"
          :class="{
            focused
          }"
          type="number"
        />
        <div class="text font-inter not-italic font-normal text-[18px] leading-[22px] text-[color:var(--ui-dark)]">hours old</div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { useTemplateRef } from 'vue'
import { useFocus, onStartTyping } from '@vueuse/core'
import type { Student } from '@/types/student.ts'

defineProps<{
  student: Student
}>()

const input = useTemplateRef<HTMLInputElement>('input')
const { focused } = useFocus(input, { initialValue: false })
onStartTyping(() => input.value?.focus())
</script>
