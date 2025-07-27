<script setup lang="ts">
import AppLayout from '@/layouts/AppLayout.vue'
import { Head, Link } from '@inertiajs/vue3'

const breadcrumbs = [
  { title: 'Dashboard', href: '/dashboard' },
  { title: 'Proyectos', href: '/proyectos' },
]

// Datos de ejemplo
const proyectos = [
  {
    id: 1,
    nombre: 'Sistema de Inventario',
    descripcion: 'Control y gestión de stock',
    criticidad: 'Alta',
    fecha_creacion: '2024-05-01',
    ultima_version: 'v1.2.0',
  },
  {
    id: 2,
    nombre: 'Portal Web',
    descripcion: 'Sitio institucional del cliente',
    criticidad: 'Media',
    fecha_creacion: '2024-06-12',
    ultima_version: 'v2.0.0',
  },
]
</script>

<template>
  <Head title="Proyectos" />

  <AppLayout :breadcrumbs="breadcrumbs">
    <div class="p-6 space-y-6">
      <h1 class="text-2xl font-bold">Lista de Proyectos</h1>

      <div class="grid gap-4">
        <div
          v-for="p in proyectos"
          :key="p.id"
          class="bg-white rounded-xl shadow p-4 hover:shadow-lg transition"
        >
          <h2 class="text-lg font-semibold text-gray-800">{{ p.nombre }}</h2>
          <p class="text-sm text-gray-600">{{ p.descripcion }}</p>
          <p class="text-sm mt-1">Criticidad: <strong>{{ p.criticidad }}</strong></p>
          <p class="text-sm">Creado: {{ p.fecha_creacion }}</p>
          <p class="text-sm">Última versión: {{ p.ultima_version }}</p>

          <div class="mt-2">
            <Link
              :href="`/proyectos/${p.id}/ver`"
              class="text-blue-600 hover:underline text-sm"
            >
              Ver detalle →
            </Link>
          </div>
        </div>
      </div>
    </div>
  </AppLayout>
</template>
