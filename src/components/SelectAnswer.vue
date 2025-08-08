<template>
    <div >
        <input type="radio">
        <label>
            {{ listAnswerProps }}
        </label>
    </div>

</template>

<script setup>

defineProps({
    listAnswerProps: Object
})
</script>