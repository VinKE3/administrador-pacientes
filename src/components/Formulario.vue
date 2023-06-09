<script setup>
import { reactive } from "vue";
import Alerta from "./Alerta.vue";

const alerta = reactive({
  mensaje: "",
  tipo: "",
});

const emit = defineEmits([
  "update:nombre",
  "update:documento",
  "update:email",
  "update:fecha",
  "update:sintomas",
  "guardar-paciente",
]);

const props = defineProps({
  nombre: {
    type: String,
    required: true,
  },
  documento: {
    type: String,
    required: true,
  },
  email: {
    type: String,
    required: true,
  },
  fecha: {
    type: String,
    required: true,
  },
  sintomas: {
    type: String,
    required: true,
  },
});

const validarRegistro = () => {
  if (Object.values(props).includes("")) {
    alerta.mensaje = "Todos los campos son obligatorios";
    alerta.tipo = "error";
    return;
  }
  emit("guardar-paciente");
};
</script>

<template>
  <div class="md:w-1/2 text-white">
    <h2 class="font-black text-3xl text-center">Seguimiento Pacientes</h2>
    <p class="text-lg mt-5 text-center mb-10">
      Añade Pacientes y
      <span class="text-primary font-bold">Adminístralos</span>
    </p>
    <Alerta v-if="alerta.mensaje" :alerta="alerta" />
    <form
      @submit.prevent="validarRegistro"
      class="bg-secondary-100 shadow-xl rounded-lg py-10 px-5 mb-10"
    >
      <div class="mb-5">
        <label for="paciente" class="block text-white uppercase font-bold">
          Nombre Paciente
        </label>
        <input
          id="paciente"
          type="text"
          placeholder="Nombre Paciente"
          @input="$emit('update:nombre', $event.target.value)"
          class="border-2 w-full mt-2 py-3 px-3 rounded-lg bg-secondary-200 focus:outline-none focus:border-primary"
        />
      </div>
      <div class="mb-5">
        <label for="documento" class="block text-white uppercase font-bold">
          D.N.I
        </label>
        <input
          id="documento"
          type="text"
          maxlength="8"
          placeholder="N° D.N.I"
          @input="$emit('update:documento', $event.target.value)"
          class="border-2 w-full mt-2 py-3 px-3 rounded-lg bg-secondary-200 focus:outline-none focus:border-primary"
        />
      </div>
      <div class="mb-5">
        <label for="email" class="block text-white uppercase font-bold">
          Correo Electrónico
        </label>
        <input
          id="email"
          type="email"
          placeholder="Correo Electrónico"
          @input="$emit('update:email', $event.target.value)"
          class="border-2 w-full mt-2 py-3 px-3 rounded-lg bg-secondary-200 focus:outline-none focus:border-primary"
        />
      </div>
      <div class="mb-5">
        <label for="fecha" class="block text-white uppercase font-bold">
          Fecha de Entrada
        </label>
        <input
          id="fecha"
          type="date"
          @input="$emit('update:fecha', $event.target.value)"
          class="border-2 w-full mt-2 py-3 px-3 rounded-lg bg-secondary-100 focus:outline-none focus:border-primary"
        />
      </div>
      <div class="mb-5">
        <label for="sintomas" class="block text-white uppercase font-bold">
          Sintomas
        </label>
        <textarea
          class="border-2 w-full mt-2 py-3 px-3 rounded-lg bg-secondary-200 focus:outline-none focus:border-primary"
          name="sintomas"
          @input="$emit('update:sintomas', $event.target.value)"
          placeholder="Describir Sintomas"
          id="sintomas"
          cols="30"
          rows="10"
        />
      </div>
      <input
        type="submit"
        value="Añadir Paciente"
        class="bg-secondary-200 rounded-lg w-full p-3 uppercase font-bold hover:text-primary cursor-pointer"
      />
    </form>
  </div>
</template>
