<script setup>
import {Link, router} from '@inertiajs/vue3'
import Pagination from "../../Shared/Pagination.vue";
import {ref, watch} from "vue";
import {debounce} from "lodash";
const props = defineProps({
    users: Object,
    filters: Object,
    can: Object,

})

let search = ref(props.filters.search)

watch(search, debounce(value => {
    router.get('/users', {search: value}, {
        preserveState: true,
        replace: true
    })
}, 300))
</script>

<template>
    <div class="flex justify-between mb-6">
        <div class="flex items-center">
            <h1 class="text-4xl font-bold">Users</h1>
            <Link v-if="can.createUser" href="/users/create" class="ml-6">New User</Link>
        </div>
        <input v-model="search" class="border px-2 rounded-lg" type="text" placeholder="Search..."/>
    </div>
    <div>
        <ul role="list" class="divide-y divide-gray-100">
            <li v-for="user in users.data" :key="user.id" class="flex justify-between gap-x-6 py-5">
                <div class="min-w-0 flex-auto">
                    <p class="text-sm font-semibold leading-6 text-gray-900">{{ user.name }}</p>
                </div>
                <div class="hidden shrink-0 sm:flex sm:flex-col sm:items-end">
                    <Link :href="`/users/${user.id}/edit`" class="mt-1 truncate text-xs leading-5 text-gray-500">Edit
                    </Link>
                </div>
            </li>
        </ul>
    </div>

    <Pagination class="mt-10" :links="users.links"/>
</template>

