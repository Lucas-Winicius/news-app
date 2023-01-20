<template>
  <header>
    <h1>Noticias</h1>
    <form>
      <input type="text" name="search" id="search" placeholder="Pesquisa" />
      <select name="lang" id="lang">
        <option v-for="(lang, index) in langs" :value="lang" :key="index">
          {{ lang.toLocaleUpperCase() }}
        </option>
      </select>
      <button type="submit">Pesquisar</button>
    </form>
    <!-- <div><img src="../assets/dark-mode.png" alt="Dark Mode" width="10px"></div> -->
  </header>
</template>

<script>
export default {
  name: "HeaderComponent",
  data() { return { langs: [ "pt", "en", "ar", "de", "es", "fr", "he", "it", "nl", "no", "ru", "sv", "ud", "zh", ] }; },
};
</script>

<style scoped>

* {
  margin: 0px;
  padding: 0px;
  outline: 0px;
  font-family: Arial, Helvetica, sans-serif;
}

h1 {
  padding-left: 3vw;
  color: white;
  text-shadow: 0px 0px 2.5px #000000;
}

header {
  position: sticky;
  position: -webkit-sticky;
  top: 0px;
  display: flex;
  justify-content: space-between;
  padding: 20px 0px;
  background-image: linear-gradient(90deg, #34e89e, #0f3443);
  box-shadow: -1px 3px 9px rgb(0 0 0 / 63%);;
}

input {
  width: 200px;
  height: 20px;
  padding: 5px 20px;
  border-radius: 20px 0px 0px 20px;
  border: 1px solid rgb(136, 136, 136);
  border-right: none;
  background-color: white;
}

select {
  height: 32px;
  padding: 5px 10px;
  border: 1px solid rgb(136, 136, 136);
  /* border-left: 1px solid black; */
  border-right: none;
  /* border-left: none; */
  background-color: white;
}

button {
  height: 32px;
  padding: 0px 20px;
  border: 1px solid rgb(136, 136, 136);
  /* border-left: none; */
  border-radius: 0px 20px 20px 0px;
  background-color: white;
  margin-right: 3vw;
}

</style>