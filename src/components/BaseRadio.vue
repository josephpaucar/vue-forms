<script setup>
import UniqueID from '../features/UniqueID'
import BaseErrorMessage from './BaseErrorMessage.vue'

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
  },
  error: {
    type: String,
    default: ''
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
  <BaseErrorMessage v-if="error" :id="`${uuid}-error`">
    {{ error }}
  </BaseErrorMessage>
</template>
