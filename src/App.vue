<script setup>
import { ref, reactive } from "vue";
import { uid } from "uid";
import Header from "./components/Header.vue";
import Formulario from "./components/Formulario.vue";
import Paciente from "./components/Paciente.vue";

const pacientes = ref([]);

const paciente = reactive({
  id: null,
  nombre: "",
  documento: "",
  email: "",
  fecha: "",
  sintomas: "",
});

const guardarPaciente = () => {
  pacientes.value.push({
    ...paciente,
    id: uid(),
  });
  Object.assign(paciente, {
    nombre: "",
    documento: "",
    email: "",
    fecha: "",
    sintomas: "",
  });
};

const actualizarPaciente = (id) => {
  const pacienteEditar = pacientes.value.filter(
    (paciente) => paciente.id === id
  )[0];
  Object.assign(paciente, pacienteEditar);
  
};
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
        @guardar-paciente="guardarPaciente"
      />
      <div class="md:w-1/2 md:h-screen overflow-y-scroll">
        <h3 class="font-black text-3xl text-center text-primary">
          Administra tus Pacientes
        </h3>
        <div v-if="pacientes.length > 0">
          <p class="text-lg mt-5 text-center mb-10 text-white">
            Información de tus
            <span class="text-primary font-bold">Pacientes</span>
          </p>
          <Paciente
            v-for="paciente in pacientes"
            :paciente="paciente"
            :key="paciente.id"
            @actualizar-paciente="actualizarPaciente"
          />
        </div>
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
