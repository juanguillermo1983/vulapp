<script setup lang="ts">
import AppLayout from '@/layouts/AppLayout.vue'
import { Head, Link } from '@inertiajs/vue3'
import { computed } from 'vue'
import { usePage } from '@inertiajs/vue3'

const page = usePage()
const proyectoId = computed(() => page.props.id)

const breadcrumbs = [
  { title: 'Dashboard', href: '/dashboard' },
  { title: 'Proyectos', href: '/proyectos' },
  { title: `Proyecto #${proyectoId.value}`, href: `/proyectos/${proyectoId.value}/ver` },
]

// Datos de ejemplo (reemplazar por props más adelante)
const versiones = [
  {
    id: 1,
    nombre_version: 'v1.0.0',
    estado: 'aprobado',
    motivo_cambio: 'lanzamiento inicial',
    fecha_creacion: '2024-01-10',
  },
  {
    id: 2,
    nombre_version: 'v1.1.0',
    estado: 'en prueba',
    motivo_cambio: 'mejoras UI',
    fecha_creacion: '2024-02-20',
  },
]
</script>

<template>
  <Head title="Detalle del Proyecto" />

  <AppLayout :breadcrumbs="breadcrumbs">
    <div class="p-6 space-y-6">
      <h1 class="text-2xl font-bold">Versiones del Proyecto #{{ proyectoId }}</h1>

      <div class="grid gap-4">
        <div
          v-for="v in versiones"
          :key="v.id"
          class="bg-white rounded-xl shadow p-4 hover:shadow-lg transition"
        >
          <h2 class="text-lg font-semibold">{{ v.nombre_version }}</h2>
          <p class="text-sm text-gray-600">Motivo: {{ v.motivo_cambio }}</p>
          <p class="text-sm">Estado: <strong>{{ v.estado }}</strong></p>
          <p class="text-sm">Fecha creación: {{ v.fecha_creacion }}</p>

          <div class="mt-2">
            <Link
              :href="`/versiones/${v.id}/ver`"
              class="text-blue-600 hover:underline text-sm"
            >
              Ver compromisos →
            </Link>
          </div>
        </div>
      </div>
    </div>
  </AppLayout>
</template>
