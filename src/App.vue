<script setup>
import { ref } from "vue";

const texte = ref("chalutmeau croisés");
const trimedText = texte.value.trim();
const postes = ref([]);

function addPoste() {
  const nouveauPoste = {
    id: Math.random().toString(36).substring(2),
    content : texte.value,
    createdAt: new Date(),
    author:{
      username: "phasme",
      avatarUtl: "phasme.jpeg"
    }
  }

  postes.value.push(nouveauPoste);
  texte.value = "";
}
</script>

<template>
  <h1>NOUS ALLONS DETRUIRE LE MONDE</h1>
  <h2>Je ne veux pas mourir ...😥</h2>
  <h3>C'est une blague</h3>
  <h6>Tout le monde est mort.🚗🚐🚌🚌🚛🚛🚛🚛🚛🚛</h6>

  <hr />

  <main>
    <div class="container">
      <form class="card" @submit.prevent="addPoste">
        <h1>Chalut le formulaire</h1>
        <textarea name="post" id="post" placeholder="Tu veux quoi wsh ?" v-model="texte"></textarea>
        <button :disabled="!texte.length">Envoie.</button>
      </form>

      <p v-if="!postes.length">Il n'y a aucun post... mets en un ***</p>

      <article  v-for="(poste, index) in postes" :key="index">
        <img :src="poste.author.avatarUtl" alt="avatar" width="36" height="36" class="image">
        <a> {{ poste.author.username }}</a>
        <p>{{ poste.content }}</p>
      </article>
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
button:disabled{
  cursor: not-allowed;
  opacity: 0.4;
}
article{
  padding: 0.75rem 1.5rem; 
  overflow: hidden;
  background-color: rgba(216, 226, 172, 0.5);
  border-radius: 10px;
  border: 1px solid var(--color-border);
}
article p{
  background-color: rgb(129, 66, 23);
  padding: 2px;
  padding-left: 10px;
  padding-right: 10px;
  border-radius: 10px;
  color: rgb(194, 165, 165);
}

.image{
  border-radius: 50%;
  object-fit: cover;

}

</style>
