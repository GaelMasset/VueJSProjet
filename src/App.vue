<script setup>
import { ref } from "vue";

const texte = ref("chalutmeau croisés");
const postes = ref([]);

function addPoste() {
  postes.value.push(texte.value);
  texte.value = "";
}
</script>

<template>
  <h1>NOUS ALLONS DETRUIRE LE MONDE</h1>
  <h2>Je ne veux pas mourir ...💧</h2>
  <h3>C'est une blague</h3>
  <h6>Tout le monde est mort.🚗🚐🚌🚌🚛🚛🚛🚛🚛🚛</h6>

  <hr />

  <main>
    <div class="container">
      <form class="card" @submit.prevent="addPoste">
        <h1>Chalut le formulaire</h1>
        <textarea name="post" id="post" placeholder="Tu veux quoi wsh ?" v-model="texte"></textarea>
        <button>Envoie.</button>
      </form>
      <p v-for="(poste, index) in postes" :key="index">{{ poste }}</p>
    </div>
  </main>
</template>

<style scoped>
.container {
  height: 100vh;
  margin: 0 auto;
  max-width: 640px;
}
.card {
  background-color: var(--color-bg-secondary);
  border-radius: 10px;
  border: 1px solid var(--color-border);
  margin-bottom: 1rem;
}

form {
  display: flex;
  flex-direction: column;
  margin-top: 1rem;
  padding: 1rem 1.5rem;
  width: 100%;
}
textarea {
  background: none;
  border: none;
  color: var(--color-text-primary);
  flex: 1;
  margin-bottom: 1rem;
  outline: none;
  padding: 0.5rem 0;
  resize: none;
  field-sizing: content;
}
button {
  align-self: flex-end;
  background: none;
  border-radius: 10px;
  border: 1px solid var(--color-border);
  color: var(--color-text-primary);
  cursor: pointer;
  font-size: 1rem;
  height: 40px;
  padding: 0 1rem;
}
</style>
