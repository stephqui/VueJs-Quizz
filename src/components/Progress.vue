<template>
    <div>
        Etape {{ valueProps + 1 }}/{{ maxProps + 1 }}
        <progress :value="valueProps + 1" :max="maxProps"/>
    </div>
</template>

<script setup>

defineProps({
    valueProps: Number,
    maxProps: Number
})

</script>