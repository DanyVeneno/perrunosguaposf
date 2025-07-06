<script setup>
import { useUserStore } from "../../stores/user";
const user = useUserStore();
</script>

<template>
  <div class="flex justify-between">
    <div>
      <h1 class="text-2xl lg:text-6xl font-black text-purple-100">
        Perrunos Guapos
      </h1>
      <h2 class="text-xl lg:text-2xl font-black text-purple-600">
        Panel de Administración
      </h2>
    </div>

    <div class="flex flex-col space-y-5">
      <div class="flex gap-2 items-center">
        <p class="text-purple-100 text-right">Hola: {{ user.getUserName }}</p>
        <button
          type="button"
          class="bg-red-400 hover:bg-red-500 p-2 text-purple-100 uppercase text-xs font-extrabold rounded-lg"
          @click="user.logout"
        >
          Cerrar Sesión
        </button>
      </div>
    </div>
  </div>
  <main class="space-y-6">
    <RouterView />
  </main>
</template>
