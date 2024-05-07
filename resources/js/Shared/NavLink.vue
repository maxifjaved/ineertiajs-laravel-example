<script setup>
import {Link} from "@inertiajs/vue3";

const {active} = defineProps({
    active: Boolean
})

</script>

<template>
    <Link class="text-blue-500 hover:underline" :class="{'font-bold underline': active}">
        <slot />
    </Link>
</template>
