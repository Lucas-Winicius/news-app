<template>
  <article>
    <div class="visualização" v-if="!estaAberto">
      <h1>{{ titulo }}</h1>
      <img :src="imagem" :alt="titulo">
      <p>{{ descricao }}</p>
      <small>{{ autor }}</small>
    </div>
    <div class="materiaCompleta" v-if="estaAberto">
      <h1>{{ titulo }}</h1>
      <img :src="imagem" :alt="titulo">
      <p>{{ artigoCompleto }}</p>
      <small>{{ autor }}</small>
    </div>
  </article>
</template>

<script>
export default {
    name: 'ArticleContainer',
    props: {
        autor: String,
        titulo: String,
        descricao: String,
        artigoOriginal: String,
        imagem: String,
        dataDePublicacao: String,
        artigoCompleto: String,
    },
    data() { return { estaAberto: false } }
}
</script>

<style>

article {
  display: flex;
  flex-wrap: wrap;
}

.visualização {
  width: 25vw;
  
}

</style>