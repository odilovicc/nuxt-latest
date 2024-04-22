<template>
    <button :class="{ 'button-success': success, 'button-danger': danger }" v-bind="$props">{{ label }}</button>
</template>

<script setup>
import { defineProps, toRefs } from 'vue'

const props = defineProps({
    success: {
        type: Boolean,
        default: false
    },
    danger: {
        type: Boolean,
        default: false
    },
    label: {
        type: String,
        required: true
    }
})

const { success, danger } = toRefs(props)
</script>
