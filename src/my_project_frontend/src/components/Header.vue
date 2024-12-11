<script setup>
import { ref } from 'vue';
import { my_project_backend } from 'declarations/my_project_backend/index';
let greeting = ref('');

async function handleSubmit(e) {
  e.preventDefault();
  const target = e.target;
  const name = target.querySelector('#name').value;
  await my_project_backend.greet(name).then((response) => {
    greeting.value = response;
  });
}
</script>

<template>
  <main >
    <img src="/logo2.svg" alt="DFINITY logo" />
    <br />
    <br />
    <form action="#" @submit="handleSubmit" class=" container w-full h-full font-mono subpixel-antialiased flex flex-col justify-center items-center gap-4">
      <label for="name" class="bg-gradient-to-b from-slate-400 to-slate-900 bg-clip-text text-transparent text-3xl">Jak się nazywasz? &nbsp;</label>
      <input id="name" alt="Name" type="text" class="text-2xl bg-gradient-to-l from-sky-300 to-fuchsia-500 shadow-lg shadow-cyan-500/50 rounded-md border-2 border-slate-700 border-solid" />
      <button type="submit" class="text-2xl bg-cyan-600  hadow-lg shadow-cyan-500/60 rounded-md border-2 border-slate-700 border-solid shadow-xl transition ease-in-out delay-150 bg-blue-500 hover:-translate-y-1 hover:scale-110 hover:bg-indigo-500 duration-300">Kliknij mnie!</button>
    </form>
    <section id="greeting">{{ greeting }}</section>
  </main>
</template>

<script>
export default{
    name: "Header"
}
</script>