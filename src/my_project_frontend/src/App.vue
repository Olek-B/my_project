<script setup>
import { ref } from 'vue';
import { my_project_backend } from 'declarations/my_project_backend/index';
let msg = ref('');

async function handleSubmit(e) {
  e.preventDefault();
  const target = e.target;
  const msgFromId = target.querySelector('#msg').value;
  await my_project_backend.save_msg(msgFromId);
  msg.value = await my_project_backend.get_msg();
}
</script>

<template>
  <main>
    <img src="/logo2.svg" alt="DFINITY logo" />
    <br />
    <br />
    <form action="#" @submit="handleSubmit">
      <label for="msg">Enter your msg: &nbsp;</label>
      <input id="msg" alt="msg" type="text" />
      <button type="submit">Click Me!</button>
    </form>
    <section id="msg">{{ msg }}</section>
  </main>
</template>