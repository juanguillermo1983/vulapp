<script setup lang="ts">
import AppLayout from '@/layouts/AppLayout.vue';
import { type BreadcrumbItem } from '@/types';
import { Head } from '@inertiajs/vue3';

const breadcrumbs: BreadcrumbItem[] = [
    {
        title: 'Dashboard',
        href: '/dashboard',
    },
];
</script>

<template>
    <Head title="Dashboard" />

    <AppLayout :breadcrumbs="breadcrumbs">
        <div class="p-8">
            <h1 class="text-3xl font-bold mb-4">¡Bienvenido al Panel de Administración!</h1>

            <p class="text-lg mb-6">
                Esta es la página principal de tu aplicación.
            </p>

            <inertia-link 
                href="/proyecto" 
                class="text-blue-600 hover:underline"
            >
                Ir a la página de Proyecto →
            </inertia-link>
        </div>
    </AppLayout>
</template>
