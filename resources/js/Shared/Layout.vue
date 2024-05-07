<script setup>
import Nav from "./Nav.vue";
import {computed} from "vue";
import {usePage} from "@inertiajs/vue3";

const page = usePage();
const username = computed(() => {
    return page.props.auth.user.username
})
</script>

<template>
    <header class="flex justify-between bg-slate-100 p-6">
        <div class="flex items-center">
            <h1>My App</h1>
            <span class="text-sm ml-6">Hello! {{ username }}</span>
        </div>
        <Nav/>
    </header>
    <section class="m-6">
        <div class="max-w-3xl mx-auto">
            <slot/>
        </div>
    </section>
</template>

