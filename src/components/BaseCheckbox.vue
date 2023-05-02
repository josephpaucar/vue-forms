<script setup>
import UniqueID from '../features/UniqueID'
import BaseErrorMessage from './BaseErrorMessage.vue'

defineProps({
  label: {
    type: String,
    default: ''
  },
  modelValue: {
    type: Boolean,
    default: false
  }
})

const uuid = UniqueID().getID()
</script>
<template>
  <input
    v-bind="$attrs"
    type="checkbox"
    :checked="modelValue"
    @change="$emit('update:modelValue', $event.target.checked)"
    class="field"
    :id="uuid"
  />
  <label :for="uuid" v-if="label">{{ label }}</label>
  <BaseErrorMessage v-if="error" :id="`${uuid}-error`">
    {{ error }}
  </BaseErrorMessage>
</template>
