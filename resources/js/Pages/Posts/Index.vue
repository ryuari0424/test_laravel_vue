<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head } from '@inertiajs/inertia-vue3';
import { Inertia } from "@inertiajs/inertia";


defineProps({
    posts: Object,
    user: Object,
});

function destroy(id) {
    if (confirm("ほんまに削除するで?"))
    {
        Inertia.delete(route("posts.destroy", id));
    }
}
</script>

<template>
    <Head title="unchi" />

    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                {{ user.name }}
            </h2>
        </template>

        <div class="py-12" v-for="post in posts">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-sm sm:rounded-lg">
                    <div class="p-6 bg-white border-b border-gray-200">
                        <ul>
                            <li >{{ post.id }}</li>
                            <li >{{ post.title }}</li>
                            <li >{{ post.body }}</li>
                            <li >{{ post.created_at }}</li>
                        </ul>
                        <button class="bg-red-500" @click="destroy(post.id)">削除</button>
                    </div>
                </div>
            </div>
        </div>


    </AuthenticatedLayout>
</template>
