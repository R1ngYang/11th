<template>
    <div class="xi-icon-main">
        <Component :is="icon" />
    </div>
</template>

<script setup lang="ts">
import { computed, defineProps } from '@vue/runtime-core';
import Icon from './export-icon'
const props = defineProps({
    icon: {
        type: [String],
        default: "xi-icon-default"
    },
    size: {
        type: [String, Number],
        default: 16
    }
})

const icon = (Icon as Record<string, unknown>)[props.icon]

const size = computed(() => {
    const buttonSize = `${parseInt(props.size + "")}px`
    return {
        fontSize: buttonSize,
        height: buttonSize,
        lineHeight: buttonSize,
    }
})
</script>

<style scoped>
.xi-icon-main {
    display: inline-block;
    font-size: v-bind("size.fontSize");
    height: v-bind("size.height");
    line-height: v-bind("size.lineHeight");
    vertical-align: -0.125em;
}
</style>