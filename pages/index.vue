<template>
  
  <div class="w-1/2 mx-auto my-20">
<!--     <button class="bg-red-500 p-3 text-white" v-on:click="carregaListaArtigos()">
      Carregar Artigos
    </button> -->
     <p>{{listaArtigos}}</p>
    <h1 class="text-3xl font-semibold text-red-600">
      {{tituloBlog}}
    </h1>

    <article class="my-20 text-gray-600" v-for="artigo in listaArtigos" >
      <h2 class="text-5xl font-semibold mb-5">{{artigo.titulo}}</h2>

      <p class="mb-5">{{artigo.resumo}}</p>
      <p class="text-red-500">Ler Mais...</p>
    </article>
  </div>
</template>

<script>
export default {
  data() {
    return {
      listaArtigos: [],
      tituloBlog: "Blog Nuxt"
    }
  },
  created() {
    this.carregaListaArtigos();
  },
  methods: {

    carregaListaArtigos() {
       this.$axios.get("http://127.0.0.1:8090/api/collections/artigo/records?page=1&perPage=30", { cache: 'no-store' })
      .then((respostaApi) => {
        this.listaArtigos = respostaApi.data;
        console.log(respostaApi.data);
      });
    },
  }
}
</script>
