<template>
    <div :class="classes" :style="styles">
        <slot
            @open-drawer="openDrawer"
        />
    </div>
</template>

<script setup lang="ts">
import { computed } from 'vue'
import { offcanvasContentProps, OffcanvasContentProps } from './offcanvas.typings'
import useApplyPadding from '../../composables/methods/styles/useApplyPadding'
import useGenerateProps from '../../composables/useGenerateProps'

const setProps = defineProps(offcanvasContentProps)
const emits = defineEmits('open-drawer')
const props = useGenerateProps(setProps, 'offcanvasContent') as OffcanvasContentProps

const classes = computed((): Array<string> => {
    return [
        'grow overflow-y-auto'
    ]
})
const styles = computed(() => {
    return {
        ...useApplyPadding(props.p, props.px, props.py),
    }
})

const openDrawer = () => {
    console.log('content openDrawer')
}
</script>

<script lang="ts">
export default {
    name: 'ChiOffcanvasContent'
}
</script>
