<script setup lang="ts">
    import CustomButton from './components/CustomButton.vue';

    const val = ref(0);
    
    const increment = () => {
        val.value++;
    }

    const inputTypes = ['button', 'checkbox', 'color', 'date', 'datetime-local', 'email', 'file', 'month', 'number', 'password', 'radio', 'range', 'search', 'select', 'submit', 'tel', 'text', 'textarea', 'time', 'url', 'week']
    const inputOptions = {
        checkbox: ['I like Tailwind', 'I also like FormKit', 'I like other things too'],
        radio: ['I like Tailwind', 'I like FormKit', 'I like everything'],
        select: ['I like Tailwind', 'I like FormKit', 'I like everything'],
    }

</script>

<template>
    <div>
        <input type="text" v-bind:value="val">
        <div class="flex items-center">
            <button v-on:click="increment" class=" p-4 bg-orange-700 max-w-xs rounded">
                click
            </button>
        </div>

        <div>

            <FormKit
                v-for="type in inputTypes"
                :key="type"
                :label="`This is a ${type} input`"
                :type="type"
                :placeholder="`${type} input placeholder`"
                :options="inputOptions[type] ? inputOptions[type] : null"
                :help="`Help text for the ${type} input`"
                :multiple="type === 'file'"
                :disabled="type === 'date' ? true : undefined"
                :validation="type === 'email' ? 'required|email' : 'required'"
                :validation-visibility="type === 'email' ? 'live' : 'blur'"
                :validation-label="type"
            />
        </div>

        <NuxtPage />
    </div>
</template>

<style>
    div {
        display: grid;
    }
</style>
