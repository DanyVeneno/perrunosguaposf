<script setup>
import { onMounted } from "vue";
import { useRoute, useRouter } from "vue-router";
import AppointmentAPI from "../../api/AppointmentAPI";
import { useAppointmentsStore } from "../../stores/appointments";

const appointments = useAppointmentsStore();
const route = useRoute();
const router = useRouter();

const { id } = route.params;

onMounted(async () => {
  try {
    const { data } = await AppointmentAPI.getById(id);
    appointments.setSelectedAppointment(data);
  } catch (error) {
    router.push({ name: "my-appointments" });
  }
});
</script>

<template>
  <nav class="my-5 flex gap-3">
    <RouterLink
      :to="{ name: 'edit-appointment' }"
      class="flex-1 text-center p-3 uppercase font-extrabold hover:bg-purple-600 hover:text-purple-100"
      :class="
        route.name === 'edit-appointment'
          ? 'bg-purple-500 text-purple-100'
          : 'bg-purple-100 text-purple-500'
      "
    >
      Servicios
    </RouterLink>

    <RouterLink
      :to="{ name: 'edit-appointment-details' }"
      class="flex-1 text-center p-3 uppercase font-extrabold hover:bg-purple-600 hover:text-purple-100"
      :class="
        route.name === 'edit-appointment-details'
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
