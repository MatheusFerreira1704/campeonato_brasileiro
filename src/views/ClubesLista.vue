<!-- Depois de criar uma nova view, NÃO esquecer de adicionar a rota.-->
<template>
  <v-container>
    <h2 class="text-h5 text-center mb-3 mt-5">
      Classificação
    </h2>

    <v-simple-table>
      <template v-slot:default>
        <thead>
          <tr>
            <th colspan="2" class="text-left">
              Clubles
            </th>
            <th class="text-right">
              Pontos
            </th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(clube, index) of clubesListaOrdenada" :key="clube.id">
            <td>{{ index + 1 }}</td>
            <td>
              <!-- avatar transformar imagem em tamanho pequeno. -->
              <v-avatar size="24px">
                <img :src="clube.escudo" :alt="clube.nome" />
              </v-avatar>
              <!--Class pl-2 é padding-left pra afastar o nome da imagem-->
              <span class="pl-2">{{ clube.nome }}</span>
            </td>
            <td class="text-right">{{ clube.pontos }}</td>
          </tr>
        </tbody>
      </template>
    </v-simple-table>
  </v-container>
</template>

<script>
export default {
  name: "ClubeLista",
  /*Criando array pra consumir a API*/

  data() {
    return {
      clubesListas: [],
    };
  },
  computed: {
    clubesListaOrdenada() {
      const listaOrdenada = this.clubesListas
        .slice(0)
        .sort((a, b) => (a.pontos > b.pontos ? -1 : 1));
      return listaOrdenada;
    },
  },
  /*Consumindo a API*/
  created() {
    fetch("https://hackthon-decola.firebaseio.com/clubes-lista.json")
      .then((resposta) => resposta.json())
      .then((json) => {
        this.clubesListas = json;
        console.log(this.clubesListas);
      });
  },
};
</script>

<style scoped></style>
