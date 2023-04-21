<script setup>
const temps = [1,2,3]
const props = defineProps({
    shoppingList: Array
});
</script>

<template>
    <main>
        <h2 style="padding:10px">Shopping List</h2>
        <q-list bordered>
            <q-item v-for="temp in temps" clickable v-ripple>
                <q-item-section avatar>
                <q-avatar color="teal" text-color="white" icon="bluetooth" />
                </q-item-section>

                <q-item-section>Avatar-type icon</q-item-section>
            </q-item>
        </q-list>
        <q-btn color="secondary" text-color="black" label="입력" />
    </main>
</template>

<style scoped>
</style>