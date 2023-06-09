<script setup>
defineProps({
  paciente: {
    type: Object,
    required: true,
  },
});
</script>

<template>
  <div class="mx-5 my-10 bg-secondary-200 shadow-md px-5 py-10 rounded-xl">
    <p class="font-bold mb-3 uppercase text-white">
      ID :
      <span class="font-normal normal-case text-primary"> </span>
    </p>

    <p class="font-bold mb-3 uppercase text-white">
      Nombre :
      <span class="font-normal normal-case text-primary"
        >{{ paciente.nombre }}
      </span>
    </p>

    <p class="font-bold mb-3 uppercase text-white">
      D.N.I :
      <span class="font-normal normal-case text-primary">
        {{ paciente.documento }}
      </span>
    </p>

    <p class="font-bold mb-3 uppercase text-white">
      Email :
      <span class="font-normal normal-case text-primary">
        {{ paciente.email }}</span
      >
    </p>

    <p class="font-bold mb-3 uppercase text-white">
      Fecha Ingreso :
      <span class="font-normal normal-case text-primary"
        >{{ paciente.fecha }}
      </span>
    </p>

    <p class="font-bold mb-3 uppercase text-white">
      Sintomas :
      <span class="font-normal normal-case text-primary">
        {{ paciente.sintomas }}
      </span>
    </p>

    <div class="grid md:grid-cols-2 gap-5 mt-10">
      <button
        type="button"
        class="block w-full py-2 px-10 bg-secondary-100 text-white hover:text-primary font-bold uppercase rounded-lg"
      >
        Editar
      </button>

      <button
        type="button"
        class="block w-full py-2 px-10 bg-red-600 hover:bg-red-700 text-white font-bold uppercase rounded-lg"
      >
        Eliminar
      </button>
    </div>
  </div>
</template>
