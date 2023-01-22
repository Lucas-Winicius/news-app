<template>
  <HeaderComponent @submit="pesquisar($event)" />
  <div v-if="artigos.length < 1" id="semArtigos">
    <p>Esta tudo tão vazio...</p>
  </div>

  <div id="newsContainer"></div>
</template>

<script>
import HeaderComponent from "./components/HeaderComponent.vue";
// import ArticleContainer from "./components/ArticleContainer.vue";

export default {
  name: "App",
  components: { HeaderComponent },
  data() {
    return {
      artigos: [],
    };
  },
  methods: {
    pesquisar(e) {
      e.preventDefault();
      console.log("Opa");
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
}
</style>