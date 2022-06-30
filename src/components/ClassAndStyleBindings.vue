<template>
    <div class="wrapper">
        <h2>Class and Style Bindings</h2>

        <div :class="{ green: isGreen, red: isRed }" class="square"></div>
        <button @click="changeBg">Change background</button>
    </div>
</template>

<script setup>
import { ref } from "@vue/reactivity";

const isGreen = ref(false);
const isRed = ref(true);

const changeBg = () => {
    isGreen.value = !isGreen.value;
    isRed.value = !isRed.value;
};
</script>

<style scoped>
.wrapper {
    gap: 2rem;
}

h2 {
    margin-bottom: 2rem;
}
.square {
    width: 200px;
    height: 200px;
    transition: 0.4s;
}

.red {
    background-color: crimson;
}

.green {
    background-color: hsla(160, 100%, 37%, 1);
}
</style>