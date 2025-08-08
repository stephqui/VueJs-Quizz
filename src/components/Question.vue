<template>
    <div class="question">
        <h3> {{ questionProps.question }}</h3>
    </div>
</template>

<script setup>

const props = defineProps({
    questionProps: Object
})

</script>