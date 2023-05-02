<script setup>
defineProps({
  label: {
    type: String,
    default: ''
  },
  modelValue: {
    type: [String, Number],
    default: ''
  },
  value: {
    type: [String, Number],
    required: true
  }
})
</script>

<template>
  <input
    type="radio"
    @change="$emit('update:modelValue', value)"
    :checked="modelValue === value"
    :value="value"
    v-bind="$attrs"
  />
  <label v-if="label">{{ label }}</label>
</template>
