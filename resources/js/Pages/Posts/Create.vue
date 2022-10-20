<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head } from '@inertiajs/inertia-vue3';
import { reactive } from 'vue'
import { Inertia } from '@inertiajs/inertia'

defineProps({
    errors: Object,
});
const form = reactive({
    title: null,
    body: null,
})

function submit() {
    Inertia.post('/posts', form)
}

// defineProps({
//     posts: Array,
//     user: Object,
// });
</script>
<template>
    <AuthenticatedLayout>
        <Head title="toukou" />
        <form @submit.prevent="submit">
            <label for="title">title:</label>
            <input id="title" v-model="form.title" />
            <div v-if="errors.title">{{ errors.title }}</div>
            <label for="body">content</label>
            <input id="body" v-model="form.body" />
            <div v-if="errors.body">{{ errors.body }}</div>
            <button type="submit">Submit</button>
        </form>
    </AuthenticatedLayout>

</template>
