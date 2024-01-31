<template>
    <h1>Lorem ipsum</h1>
    <base-button :component="{ type: 'router-link', address: '/' }">Wróc</base-button>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import BaseButton from "../components/BaseButton.vue";

export default defineComponent({
    components: { BaseButton },
    setup() {}
});
</script>
