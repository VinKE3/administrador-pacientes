<script setup>
import { ref, reactive } from "vue";
import Header from "./components/Header.vue";
import Formulario from "./components/Formulario.vue";

const pacientes = ref([]);

const paciente = reactive({
  nombre: "",
  documento: "",
  email: "",
  fecha: "",
  sintomas: "",
});
</script>

<template>
  <div class="container mx-auto mt-20">
    <Header />
    <div class="mt-12 md:flex">
      <Formulario
        v-model:nombre="paciente.nombre"
        v-model:documento="paciente.documento"
        v-model:email="paciente.email"
        v-model:fecha="paciente.fecha"
        v-model:sintomas="paciente.sintomas"
      />
      <div class="md:w-1/2 md:h-screen overflow-y-scroll">
        <h3 class="font-black text-3xl text-center text-primary">
          Administra tus Pacientes
        </h3>
        <div v-if="pacientes.length > 0"></div>
        <p
          v-else
          class="mt-20 text-2xl text-center text-primary uppercase font-bold"
        >
          No hay Pacientes
        </p>
      </div>
    </div>
  </div>
</template>
