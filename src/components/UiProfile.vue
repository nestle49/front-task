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
      /><!-- TODO: skeleton -->
    </div>

    <div class="flex flex-col gap-3 flex-1 min-w-0">
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
        <!-- зеркальный span -->
        <div class="relative overflow-hidden">
          <span
            ref="mirror"
            class="absolute invisible whitespace-pre font-inter text-[18px] leading-[22px] max-w-full"
          >
            {{ value }}
          </span>

          <input
            ref="input"
            type="text"
            name="hours-old"
            id="hours-old"
            class="duration-200 transition-border-color transition-colors transition-opacity outline-none w-[50px] py-[10px] px-[8px] font-inter font-medium text-[18px] leading-[22px] border-solid rounded-[6px] truncate max-w-[calc(100%-1px)]"
            :class="[
              focused ? 'border-[1.5px] border-[color:var(--ui-primary-light)] text-[color:var(--ui-dark)]' : 'border-[1px] border-[color:var(--ui-light-gray)] text-[color:var(--ui-dark)]/30'
            ]"
            :style="{ width: `${inputWidth}px` }"
            v-model="value"
          />
        </div>
        <div
          class="text font-inter not-italic font-normal whitespace-nowrap text-[18px] leading-[22px] text-[color:var(--ui-dark)]">
          hours old
        </div>
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

const value = ref('')
const inputWidth = computed(() => Math.min(Math.max(width.value + 22, 72), 400)) // padding + границы

const mirror = useTemplateRef<HTMLSpanElement>('mirror')
const { width } = useElementSize(mirror)
</script>
