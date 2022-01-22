<template>
  <div class="container">
    <div class="w-50 mx-auto my-4">
      <h1 class="text-danger">{{ tituloTest }}</h1>
      <article v-for="listaArtigo in listaArtigos">
        <h2>{{ listaArtigo.title }} id {{ listaArtigo.id }}</h2>
        <p>resumo</p>
        <p class="text-warning">ler mais</p>
      </article>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // vars
      listaArtigos: [],
      tituloTest: "Blog Latim",
    };
  },

  created() {
    this.carregarListaArtigos(); //executa metodo onload da pagina
  },
  
  methods: {
    // metodos em JS
    carregarListaArtigos() {
      this.$axios
        .get("https://jsonplaceholder.typicode.com/posts")
        .then((resAPI) => {
          this.listaArtigos = resAPI.data;
          console.log(resAPI.data);
        });
    },
  },
};
</script>


<style>
</style>