<script setup>
import { ref } from 'vue'
import { livros } from '@/_data/livros.js'

const carrinho = ref({
  itens: [],
  total: 0
})

function adicionarAoCarrinho(livro) {
  carrinho.value.itens.push({
    ...livro,
    quantidade: 1,
    total: livro.price
  })
  carrinho.value.total += livro.price
}

function formatarPreco(preco) {
  return 'R$ ' + preco.toFixed(2).replace('.', ',')
}
</script>

<template>
  <h1>Minha livraria</h1>
  <div class="container-geral">
    <div class="listagem-livros">
      <div class="card-livro" v-for="livro in livros" :key="livro.id">
        <div class="wrap-livro">
          <img :src="livro.img" alt="Capa do livro" class="capa-livro" />
        </div>
        <p class="titulo-livro">{{ livro.title }}</p>
        <p class="autor-livro">{{ livro.author }}</p>
        <p class="preco-livro">{{ formatarPreco(livro.price) }}</p>
        <button @click="adicionarAoCarrinho(livro)">Adicionar ao carrinho</button>
      </div>
    </div>
    <div class="carrinho">
      <h2>Meu carrinho</h2>
      <p v-if="carrinho.itens.length === 0">Seu carrinho está vazio</p>
      <div v-else>
        <div class="item-carrinho" v-for="(item, index) in carrinho.itens" :key="index">
          <div class="info-livro">
            <div class="imagem-livro">
              <img :src="item.img" class="icon-capa-livro" />
            </div>
            <div class="detalhes-livro">
              <div>
                <p>{{ item.title }}</p>
                <p class="info-livro-preco">{{ formatarPreco(item.price) }}/un</p>
              </div>
              <div>
                <p>Qtde: {{ item.quantidade }}</p>
                <p>Total: {{ formatarPreco(item.total) }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
      <p>Total: {{ formatarPreco(carrinho.total) }}</p>
    </div>
  </div>
</template>

<style scoped>
.info-livro {
  display: flex;
  margin-bottom: 10px;
}
.detalhes-livro {
  display: flex;
  flex-direction: column;
  width: 100%;
}

.detalhes-livro p {
  margin: 0;
}

.detalhes-livro div {
  display: flex;
  justify-content: space-between;
  width: 100%;
}
.info-livro-preco {
  margin-left: auto;
}
.icon-capa-livro {
  width: 30px;
  margin-right: 10px;
}
.container-geral {
  /* display: flex;
  justify-content: space-between; */
  display: grid;
  grid-template-columns: 3fr 1fr;
}

.carrinho {
  /* min-width: 20%; */
}
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
