<template>
    <div class="wrapper">
        <h2>Computed Properties</h2>
        <input v-model="text" type="text" />
        <ul>
            <li v-for="(item, index) in checkList" :key="index">{{ item }}</li>
        </ul>
    </div>
</template>

<script setup>
import { reactive, ref } from "@vue/reactivity";
import { computed } from "@vue/reactivity";

const list = ref([
    "banana",
    "mango",
    "apple",
    "carrot",
    "strawberry",
    "raspberry",
    "cranberry",
]);

const filteredList = computed(() => {
    return list.value.filter((item) => {
        return item.length > 5;
    });
});

const text = ref("");

const checkList = computed(() => {
    return list.value.filter((item) => {
        return item.toLowerCase().includes(text.value);
    });
});
</script>

<style scoped>
.wrapper {
    display: flex;
    flex-direction: column;
    gap: 2rem;
}
</style>