<template>
  <HeaderComponent @submit="pesquisar($event)" />
  <div v-if="artigos.length < 1" id="semArtigos">
    <p>Esta tudo tão vazio...</p>
  </div>
  <div id="newsContainer" v-if="artigos.length >= 1">
    <ArticleContainer
    v-for="(artigo, index) in artigos"
    :key="index"
    :autor="artigo.author"
    :titulo="artigo.title"
    :descricao="artigo.description"
    :artigo-original="artigo.url"
    :imagem="artigo.urlToImage"
    :data-de-publicacao="artigo.publishedAt"
    :artigo-completo="artigo.content"
    linguagem="pt"
    />
  </div>
</template>

<script>
import HeaderComponent from "./components/HeaderComponent.vue";
import ArticleContainer from "./components/ArticleContainer.vue";
import axios from 'axios'


export default {
  name: "App",
  components: { HeaderComponent, ArticleContainer },
  data() {
    return {
      artigos: [],
      linguagem: 'pt'
    };
  },
  methods: {
    pesquisar(e) {
      e.preventDefault();
      const pesquisa = document.querySelector('#search').value
      this.linguagem = document.querySelector('#lang').value

      axios(`https://newsapi.org/v2/everything?q=${pesquisa}&apiKey=ccdb7acfb1404b468b5ed475ad5eb28c&language=${this.linguagem}`)
        .then(response => {
          this.artigos = response.data.articles
        })
    },
  },
};
</script>

<style>
* {
  margin: 0px;
  padding: 0px;
}

body {
  overflow-x: hidden;
}

#newsContainer {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
  margin-top: 45px;
  /* margin-top: 45px; */
}

#semArtigos {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 80vh;
  font-size: 1.5em;
  color: gray;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  user-select: none;
  pointer-events: none;
}
</style>