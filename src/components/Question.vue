<template>
    <div class="question">
        <h3> {{ question.questions }}</h3>
    </div>
</template>

<script setup>

const props = defineProps({
    question: Object
})

</script>