<template>
  <div class="sitesList mt-3">
    <v-card
      elevation="15"
      v-for="site of listaSites"
      :key="site.id"
      class="mx-auto mb-3"
      max-width="344"
    >
      <div>
        <a :href="site.site">
          <v-img :src="site.imagem" alt="site.nome" class="rounded-lg"></v-img>
        </a>
      </div>
      <v-card-title>
        <h3>{{ site.nome }}</h3>
      </v-card-title>

      <v-card-subtitle>
        <span v-for="ferramenta of site.ferramentas" :key="ferramenta.id">
          {{ ferramenta }};
        </span>
      </v-card-subtitle>

      <v-divider></v-divider>

      <v-card-text>
        <p>
          {{ site.descricao }}
        </p>
        <v-btn
          :href="site.site"
          target="_blank"
          class="botao-saibaMais"
          color="white"
          text
        >
          Saiba Mais
        </v-btn>
      </v-card-text>
    </v-card>
  </div>
</template>

<script>
export default {
  name: "MeuInicio",
  data() {
    return {
      listaSites: [],
      show: false,
    };
  },
  created() {
    fetch("https://it3-hbn-default-rtdb.firebaseio.com/fakeNews.json")
      .then((resposta) => resposta.json())
      .then((json) => {
        this.listaSites = json;
      });
  },
};
</script>

<style scoped>
.v-main {
  background-color: black;
}

.botao-saibaMais {
  background-color: black;
}

p {
  text-align: justify;
}
</style>
