<script setup>
import UniqueID from '../features/UniqueID'

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

const uuid = UniqueID().getID()
</script>

<template>
  <input
    type="radio"
    @change="$emit('update:modelValue', value)"
    :checked="modelValue === value"
    :value="value"
    v-bind="$attrs"
    :id="uuid"
  />
  <label :for="uuid" v-if="label">{{ label }}</label>
</template>
