<script setup>
import UniqueID from '../features/UniqueID'

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
    type="checkbox"
    :checked="modelValue"
    @change="$emit('update:modelValue', $event.target.checked)"
    class="field"
    :id="uuid"
  />
  <label :for="uuid" v-if="label">{{ label }}</label>
</template>
