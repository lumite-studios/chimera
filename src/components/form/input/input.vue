<template>
    <FormKit
        type="text"
        :disabled="props.disabled"
        :placeholder="props.placeholder ?? props.name"
        :value="setProps.modelValue"
        @input="updateValue($event)"
    />
</template>

<script setup lang="ts">
import { computed } from 'vue'
import formInputProps, { FormInputProps } from './input.typings'
import { inputClasses, inputStyles } from '../form.typings'
import useGenerateProps from '../../../composables/useGenerateProps'

const setProps = defineProps(formInputProps)
const props = useGenerateProps(setProps, 'formInput', 'form') as FormInputProps
const emits = defineEmits(['update:modelValue'])

const hasError = computed((): boolean => props.error !== null && props.error !== '')
const updateValue = (event: Event): void => {
    emits('update:modelValue', event)
}
</script>
