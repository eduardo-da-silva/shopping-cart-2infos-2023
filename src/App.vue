<script setup>
import { livros } from '@/_data/livros.js'
</script>

<template>
  <h1>Minha livraria</h1>
  <div class="listagem-livros">
    <div class="card-livro" v-for="livro in livros" :key="livro.id">
      <div class="wrap-livro">
        <img :src="livro.img" alt="Capa do livro" class="capa-livro" />
      </div>
      <p class="titulo-livro">{{ livro.title }}</p>
      <p class="autor-livro">{{ livro.author }}</p>
      <p class="preco-livro">{{ livro.price }}</p>
    </div>
  </div>
  <!-- {{ livros }} -->
</template>

<style scoped>
.listagem-livros {
  display: flex;
  flex-wrap: wrap;
}

.card-livro {
  margin: 5px 10px;
  padding: 10px;
  background-color: beige;
  border-radius: 10px;
  width: 180px;
}

.wrap-livro {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: white;
  border-radius: 10px;
  width: 180px;
  height: 270px;
}
.capa-livro {
  width: 90%;
  max-height: 100%;
}

.card-livro p {
  margin: 0;
}

.card-livro .titulo-livro {
  font-weight: bold;
  margin-bottom: 5px;
}
</style>
