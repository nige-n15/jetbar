<template>
  <span
    class="px-2 inline-flex text-xs leading-5 font-semibold rounded-full"
    :class="badgeColors"
    >{{ text }}</span
  >
</template>

<script setup>
import { computed } from 'vue'

defineProps({
  text: {
    type: String,
    required: true
  },
  type: {
    type: String,
    default: 'info',
    validator: (value) => {
      return ['info', 'success', 'warning', 'danger'].includes(value)
    }
  }
})
const badgeColors = computed(() => {
  const colors = {
    info: 'bg-blue-100 text-blue-800',
    success: 'bg-green-100 text-green-800',
    warning: 'bg-yellow-100 text-yellow-800',
    danger: 'bg-red-100 text-red-800'
  }
  return colors[this.type]
})
</script>
