<script setup lang="ts">
    import CustomButton from './components/CustomButton.vue';

    const val = ref(0);
    
    const increment = () => {
        val.value++;
    }

    const bar = (e: Event) => {
        console.log(e);
    }

    const arr = [
        {
            id: 0,
            text: "Pidor"
        },
        {
            id: 1,
            text: "Rukav"
        },
        {
            id: 2,
            text: "Timosh"
        }
    ]
</script>

<template>
    <div>
        <input type="text" v-bind:value="val">
        <button v-on:click="increment">
            click
        </button>
        <!-- <CustomButton v-if="val === 2">kek</CustomButton>
        <div v-else-if="val === 3">Rukav pidor</div>
        <div v-else>Timosh dai labu</div> -->

        <div>
            <div v-for="el in arr" :key="el.id">
                <CustomButton>
                    <h4>{{ el.id }}</h4>
                    <p>{{ el.text }}</p>
                </CustomButton>
            </div>
        </div>

        <NuxtPage />
    </div>
</template>

<style>
    div {
        display: grid;
    }
</style>
