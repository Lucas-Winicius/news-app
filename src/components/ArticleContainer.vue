<template>
  <article>
    <div class="visualização" v-if="!estaAberto" @click="changeView">
      <h1>{{ titulo }}</h1>
      <img :src="imagem" :alt="titulo" />
      <p>{{ descricao }}</p>
      <small>- {{ autor }}</small>
    </div>
    <div class="materiaCompleta" v-if="estaAberto">
      <span id="close"
        ><img
          src="../assets/close.svg"
          alt="Close"
          @click="changeView"
          title="Fechar"
      /></span>
      <h1>
        <a :href="artigoOriginal">{{ titulo }}</a>
      </h1>
      <img :src="imagem" :alt="titulo" />
      <p>{{ artigoCompleto }}</p>
      <p>
        <small id="author">{{ autor }}</small
        ><small id="dataDePublicacao">{{
          new Date(dataDePublicacao).toLocaleString(linguagem)
        }}</small>
      </p>
    </div>
  </article>
</template>

<script>
export default {
  name: "ArticleContainer",
  props: {
    autor: String,
    titulo: String,
    descricao: String,
    artigoOriginal: String,
    imagem: String,
    dataDePublicacao: String,
    artigoCompleto: String,
    linguagem: String,
  },
  data() {
    return { estaAberto: false };
  },
  methods: {
    changeView() {
      this.estaAberto = !this.estaAberto;
    },
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap");

* {
  font-family: "Montserrat", sans-serif;
}

article {
  display: flex;
  flex-wrap: wrap;
  margin-bottom: 45px;
  /* width: max-content; */
}

.visualização {
  width: 25vw;
  min-width: 300px;
  display: flex;
  flex-wrap: wrap;
  border: 1px solid rgb(176, 176, 176);
  padding: 20px;
  border-radius: 15px;
  box-shadow: 2px 4px 8px 1px #00000099;
  transition: 300ms;
}

.visualização:hover {
  transform: scale(1.05);
}

.visualização img {
  width: 100%;
  margin: 15px 0px;
  pointer-events: none;
  user-select: none;
}

.visualização h1 {
  font-size: 1.5em;
}

.visualização p {
  text-align: justify;
}

.visualização small {
  display: inline-block;
  width: 100%;
  text-align: end;
  margin-top: 10px;
}

/* ESTILO DA MATERIA COMPLETA */

.materiaCompleta {
  background-color: rgb(231, 231, 231);
  position: fixed;
  z-index: 2;
  top: 0px;
  left: 0px;
  width: 100vw;
  height: 100vh;
  overflow-y: scroll;
  transition: 1s;
}
.materiaCompleta img {
  width: 70%;
  /* display: none; */
}

.materiaCompleta #close img {
  position: fixed;
  top: 0px;
  right: 20px;
  width: 30px;
  margin: 10px;
  background-color: rgba(0, 0, 0, 0.1);
  border-radius: 100%;
  color: white;
  padding: 5px;
  cursor: pointer;
}

.materiaCompleta > img {
  display: block;
  width: 50%;
  margin: auto;
  /* padding: 10px; */
}

.materiaCompleta a {
  color: black;
  text-decoration: none;
}

.materiaCompleta a:hover {
  text-decoration: underline;
}
.materiaCompleta h1 {
  text-align: center;
  padding: 20px;
  font-size: 2em;
  color: black;
}

.materiaCompleta > p {
  text-align: justify;
  padding: 20px;
}

.materiaCompleta #author {
  float: left;
}

.materiaCompleta #dataDePublicacao {
  float: right;
}

@media screen and (max-width: 1025px) {
  .visualização {
    width: 40vw;
    min-width: 0px;
  }
}

@media screen and (max-width: 705px) {
  
}

@media screen and (max-width: 495px) {
  .visualização {
    width: 80vw;
  }
}

</style>