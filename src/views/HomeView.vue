<script setup>
import Computed from "../components/Computed.vue";
import ClassAndStyleBindings from "../components/ClassAndStyleBindings.vue";
import { ref } from "@vue/reactivity";

// Picking component

let currentTab = ref("Computed");
const tabs = { Computed, ClassAndStyleBindings };

// Changing active tab text color

const pickTab = (e) => {
    currentTab.value = e.target.textContent;
    const buttons = document.querySelectorAll("button");
    e.target.style.color = "hsla(160, 100%, 37%, 1)";
    buttons.forEach((button) => {
        if (button.textContent !== e.target.textContent) {
            button.style.color = "var(--text-color)";
        }
    });
};
</script>

<template>
    <div class="wrapper">
        <h1>Choose component:</h1>
        <div class="component-container">
            <button v-for="(_, tab) in tabs" :key="tab" @click="pickTab">
                {{ tab }}
            </button>
            <component :is="tabs[currentTab]"></component>
        </div>
    </div>
</template>

<style scoped>
.wrapper {
    margin-top: 2rem;
    border-top: 1px solid var(--color-border);
    max-width: 100vw;
    /* min-height: 100vh; */

    display: flex;
    flex-direction: column;
    align-items: center;
}

.wrapper > h1 {
    margin: 2rem 0;
}

button {
    border-right: 1px solid var(--color-border);
}
</style>