<script setup>
import BaseErrorMessage from './BaseErrorMessage.vue'
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
  error: {
    type: String,
    default: ''
  }
})

const uuid = UniqueID().getID()
</script>
<template>
  <label :for="uuid" v-if="label">{{ label }}</label>
  <input
    v-bind="$attrs"
    @input="$emit('update:modelValue', $event.target.value)"
    :value="modelValue"
    :placeholder="label"
    class="field"
    :id="uuid"
    :aria-describedby="error ? `${uuid}-error` : null"
    :aria-invalid="error ? true : null"
    :class="{ error }"
  />
  <BaseErrorMessage v-if="error" :id="`${uuid}-error`">
    {{ error }}
  </BaseErrorMessage>
</template>
