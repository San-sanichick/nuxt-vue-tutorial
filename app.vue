<script setup lang="ts">
    import CustomButton from './components/CustomButton.vue';

    const val = ref(0);
    
    const increment = () => {
        val.value++;
    }

    const inputTypes = ['button', 'checkbox', 'color', 'date',  'email',  'number', 'password', 'radio', 'range', 'search', 'select', 'submit', 'tel', 'text', 'textarea', 'time', 'url', 'week']
    const inputOptions = {
        checkbox: ['I like Tailwind', 'I also like FormKit', 'I like other things too'],
        radio: ['I like Tailwind', 'I like FormKit', 'I like everything'],
        select: ['I like Tailwind', 'I like FormKit', 'I like everything'],
    }

</script>

<template>
    <div>
        <input type="text" v-bind:value="val">
        <!-- ! Works -->
        <div class="flex items-center">
            <button v-on:click="increment" class=" p-4 bg-orange-700 max-w-xs rounded">
                click
            </button>
        </div>

        <!-- ! Doesn't work -->
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

        <!-- ! Works if theme is removed from formkit.config.js -->
        <!-- ! and the block above is commented out -->
        <div>
            <FormKit
                type="text"
                label="Section-key class props"
                help="Look, Ma! Tailwind styles"
                outer-class="mb-5"
                label-class="block mb-1 font-bold text-sm"
                inner-class="max-w-md border border-gray-400 rounded-lg mb-1 overflow-hidden focus-within:border-blue-500"
                input-class="w-full h-10 px-3 border-none text-base text-gray-700 placeholder-gray-400"
                help-class="text-xs text-gray-500"
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
