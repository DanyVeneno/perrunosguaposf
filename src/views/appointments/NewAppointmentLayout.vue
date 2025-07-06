<script setup>
import { onMounted } from "vue";
import { useRoute } from "vue-router";
import { useAppointmentsStore } from "../../stores/appointments";

const route = useRoute();
const appointments = useAppointmentsStore();

onMounted(() => {
  appointments.clearAppointmentData();
});
</script>

<template>
  <nav class="my-5 flex gap-3">
    <RouterLink
      :to="{ name: 'new-appointment' }"
      class="flex-1 text-center p-3 uppercase font-extrabold hover:bg-purple-600 hover:text-purple-100 rounded-lg"
      :class="
        route.name === 'new-appointment'
          ? 'bg-purple-500 text-purple-100'
          : 'bg-purple-100 text-purple-500'
      "
    >
      Servicios
    </RouterLink>

    <RouterLink
      :to="{ name: 'appointment-details' }"
      class="flex-1 text-center p-3 uppercase font-extrabold hover:bg-purple-600 hover:text-purple-100 rounded-lg"
      :class="
        route.name === 'appointment-details'
          ? 'bg-purple-500 text-purple-100'
          : 'bg-purple-100 text-purple-500'
      "
    >
      Cita y Resumen
    </RouterLink>
  </nav>
  <div class="space-y-5">
    <RouterView />
  </div>
</template>
