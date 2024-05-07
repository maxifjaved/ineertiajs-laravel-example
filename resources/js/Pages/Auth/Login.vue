<script setup>
import {useForm} from "@inertiajs/vue3";

const form = useForm({
    email: '',
    password: '',
})

</script>

<template>
    <main class="grid place-items-center min-h-screen">
        <section class="bg-white p-8 rounded-xl max-w-md mx-auto border">
            <h1 class="text-3xl mb-6">Login</h1>
            <form @submit.prevent="form.post('/login')" class="max-w-md mx-auto mt-8">
                <div class="mt-6">
                    <label
                        class="block mb-2 uppercase font-bold text-xs text-gray-700"
                        for="email"
                    >
                        Email
                    </label>
                    <input
                        v-model="form.email"
                        class="border border p-2 w-full rounded"
                        type="email"
                        name="email"
                        id="email"

                    />
                    <div v-if="form.errors.email" v-text="form.errors.email"
                         class="text-red-500 text-sm mt-1"></div>

                </div>

                <div class="mt-6">
                    <label
                        class="block mb-2 uppercase font-bold text-xs text-gray-700"
                        for="password"
                    >
                        Password
                    </label>
                    <input
                        v-model="form.password"
                        class="border border p-2 w-full rounded"
                        type="password"
                        name="password"
                        id="password"
                    />
                    <div v-if="form.errors.password" v-text="form.errors.password"
                         class="text-red-500 text-sm mt-1"></div>
                </div>
                <div class="mt-6">
                    <button
                        type="submit"
                        class="bg-blue-400 text-white rounded py-2 px-4 hover:bg-blue-500"
                        :disabled="form.processing"
                    >
                        Login
                    </button>
                </div>
            </form>
        </section>
    </main>
</template>
