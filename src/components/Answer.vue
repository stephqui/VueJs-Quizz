<template>
    <label :for="id" :class="classes">
        <input :disabled="propsDisabled" :id="id" type="radio" name="answer" :value="propsValue" @change="onChange" v-model="model">
        {{ propsValue }}
    </label>
</template>

<script setup>
import { computed } from 'vue';


const props = defineProps({
    id: String,
    propsDisabled: Boolean,
    propsValue: String,
    correctAnswer: String
})

const emits = defineEmits(['change'])
const onChange = (event) => {
    emits('change', event)
}
const model = defineModel()

const classes = computed(() => ({
    disabled: props.propsDisabled,
    right: props.propsDisabled && props.propsValue === props.correctAnswer,
    wrong: props.propsDisabled && props.propsValue !== props.correctAnswer && model.value === props.propsValue
}))
</script>

<style>
.disabled {
    opacity: .5;
}

.right {
    color: green;
    opacity: 1;
}

.wrong {
    color: red;
    opacity: 1;
}
</style>