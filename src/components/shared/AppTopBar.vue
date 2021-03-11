<!--Cria-se componente iniciando com App quando ele é utilizado em todo aplicativo.-->
<template>
  <div class="app-top-bar">
    <!-- Barra de navegação-->
    <v-app-bar color="green lighten-1" app dark>
      <v-app-bar-nav-icon @click="drawer = true"></v-app-bar-nav-icon>

      <!-- Titulo da barra -->
      <v-toolbar-title>Campeonato Brasileiro ⚽</v-toolbar-title>

      <v-spacer></v-spacer>
    </v-app-bar>
    <!-- Navegação da barra-->
    <v-navigation-drawer v-model="drawer" absolute temporary>
      <v-list nav dense>
        <!-- actovi-class é onde fica a cor do menu quando o usuario clica.-->
        <v-list-item-group
          v-model="group"
          active-class="green--text text--lighten-2"
        >
          <!-- Link caminho início sem atualizar tela-->
          <router-link to="/">
            <v-list-item>
              <v-list-item-icon>
                <v-icon>mdi-home</v-icon>
              </v-list-item-icon>
              <v-list-item-title>Início</v-list-item-title>
            </v-list-item>
          </router-link>

          <!-- Link caminho classificação sem atualizar tela -->
          <router-link to="/classificacao">
            <v-list-item>
              <v-list-item-icon>
                <v-icon>mdi-soccer</v-icon>
              </v-list-item-icon>
              <v-list-item-title>Classificação</v-list-item-title>
            </v-list-item>
          </router-link>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>
  </div>
</template>

<script>
export default {
  name: "AppTopBar",
  data: () => ({
    /* Script importante para o funcionamento do NAVIGATION DRAWER*/
    drawer: false,
    group: null,
  }),
};
</script>
<style scoped>
.app-top-bar a {
  text-decoration: none;
}
</style>
