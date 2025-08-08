<template>
    <input type="radio">
    <label>
        {{ listAnswerProps }}
    </label>
</template>

<script setup>

defineProps({
    listAnswerProps: Object
})
</script>