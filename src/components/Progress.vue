<template>
    <div>
        Etape {{ value + 1 }}/{{ max + 1 }}
        <progress :value="value + 1" :max="max"/>
    </div>
</template>

<script setup>

defineProps({
    value: Number,
    max: Number
})

</script>