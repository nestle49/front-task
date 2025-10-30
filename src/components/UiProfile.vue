<template>
  <div
    class="ui-profile flex items-center gap-4"
    :class="{
      focused
    }"
  >
    <div
      class="rounded-full
             relative
             w-20
             h-20
             bg-[color:var(--ui-gray)]
             after:content-['']
             after:absolute
             after:-left-1
             after:-top-1
             after:block
             after:w-[88px]
             after:h-[88px]
             after:rounded-full
             after:pointer-events-none
             after:ease
             after:transition-colors
             after:duration-200
             after:border
             after:box-border
             after:transition-border-color"
      :class="[
          focused ? 'after:border-[color:var(--ui-primary)]' : 'after:border-[color:transparent]'
      ]"
    >
      <img :src="student.image"
           width="80"
           height="80"
           loading="lazy"
           alt="Student photo"
      /><!-- TODO: with api add skeleton -->
    </div>

    <div class="flex flex-col gap-3">
      <label
        for="hours-old"
        class="font-koulen text-base leading-[15px] tracking-[0.02em] ease transition-colors duration-200"
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
import type { Student } from '@/types/student.ts'

defineProps<{
  student: Student
}>()

const input = useTemplateRef<HTMLInputElement>('input')
const { focused } = useFocus(input, { initialValue: false })
onStartTyping(() => input.value?.focus())
</script>
