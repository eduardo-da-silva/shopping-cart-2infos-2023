<script setup>
import { livros } from '@/_data/livros.js'
import { adicionarAoCarrinho } from '@/_data/carrinho.js'

import CardLivro from '@/components/CardLivro.vue'
</script>

<template>
  <div class="listagem-livros">
    <card-livro
      v-for="livro in livros"
      v-bind:key="livro.id"
      v-bind:livro="livro"
      @adicionarAoCarrinho="adicionarAoCarrinho"
    />
  </div>
</template>

<style scoped>
.listagem-livros {
  display: flex;
  flex-wrap: wrap;
}
</style>
