<script setup lang="ts">
    // const props = defineProps<{
    //     label: string
    // }>();

    const emit = defineEmits<{
        (e: 'fun', ev: Event): void
    }>();

    const foo = (e: Event) => {
        emit('fun', e);
    }

    onMounted(() => {
        console.log("Mounted")
    });
</script>

<template>
    <div>
        <button class="my-button" @click="foo">
            <slot></slot>
        </button>
    </div>
</template>

<style scoped>
    button {
        padding: 40px;
        margin: 10px;
        user-select: none;
        background-color: aqua;
        color: blue;
    }
</style>