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
    <!-- <ArticleContainer
      titulo="OG Bitcoin Core Developer Claims Hack Drained Nearly All His BTC"
      imagem="https://i.kinja-img.com/gawker-media/image/upload/c_fill,f_auto,fl_progressive,g_center,h_675,pg_1,q_80,w_1200/c8e3b3fe0595dfbab3656a5ba0e06e2c.jpg"
      descricao="Even cryptocurrency’s most accomplished tech wizards apparently aren’t immune from the occasional wallet-draining hack. Luke Dashjr, one of the original core developers for Bitcoin, claims that someone swiped hundreds of BTC from his accounts late last year—l…"
      autor="Lucas Ropek"
      artigoOriginal="https://gizmodo.com/bitcoin-price-hack-217-btc-og-developer-luke-dashjr-1849944799"
      data-de-publicacao="2023-01-03T20:48:00Z"
      artigo-completo="Even cryptocurrencys most accomplished tech wizards apparently arent immune from the occasional wallet-draining hack. Luke Dashjr, one of the original core developers for Bitcoin, claims that someone… [+2723 chars]"
    /> -->
  </div>
</template>

<script>
import HeaderComponent from "./components/HeaderComponent.vue";
import ArticleContainer from "./components/ArticleContainer.vue";
import axios from "axios";

export default {
  name: "App",
  components: { HeaderComponent, ArticleContainer },
  data() {
    return {
      artigos: [],
      linguagem: "pt",
    };
  },
  methods: {
    pesquisar(e) {
      e.preventDefault();
      const pesquisa = document.querySelector("#search").value;
      this.linguagem = document.querySelector("#lang").value;

      axios
        .get(
          `https://newsapi.org/v2/everything?q=${pesquisa}&apiKey=ccdb7acfb1404b468b5ed475ad5eb28c&language=${this.linguagem}`
        )
        .then((response) => {
          this.artigos = response.data.articles;
        });
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