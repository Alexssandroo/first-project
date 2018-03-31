<template>
  <div>
    <v-navigation-drawer
      fixed
      :clipped="$vuetify.breakpoint.lgAndUp"
      app
      v-model="drawer"
    >
      <v-list dense>
        <template v-for="item in items">
          <v-layout
            row
            v-if="item.heading"
            align-center
            :key="item.heading"
          >
            <v-flex xs6>
              <v-subheader v-if="item.heading">
                {{ item.heading }}
              </v-subheader>
            </v-flex>
            <v-flex xs6 class="text-xs-center">
              <a href="#!" class="body-2 black--text">EDIT</a>
            </v-flex>
          </v-layout>
          <v-list-group
            v-else-if="item.children"
            v-model="item.model"
            :key="item.text"
            :prepend-icon="item.model ? item.icon : item['icon-alt']"
            append-icon=""
            :to="item.endereco"
          >
            <v-list-tile slot="activator">
              <v-list-tile-content :to="{name: 'dashboard'}">
                <v-list-tile-title>
                  {{ item.text }}
                </v-list-tile-title>
              </v-list-tile-content>
            </v-list-tile>
            <v-list-tile
              v-for="(child, i) in item.children"
              :key="i"
              @click=""
              :to="child.endereco"
            >
              <v-list-tile-action v-if="child.icon">
                <v-icon>{{ child.icon }}</v-icon>
              </v-list-tile-action>
              <v-list-tile-content>
                <v-list-tile-title >
                  {{ child.text }}
                </v-list-tile-title>
              </v-list-tile-content>
            </v-list-tile>

          </v-list-group>
          <v-list-tile v-else @click="" :key="item.text" :to="item.endereco">
            <v-list-tile-action>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title>
                {{ item.text }}
              </v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
        </template>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar
      color="blue light-2"
      dark
      app
      :clipped-left="$vuetify.breakpoint.lgAndUp"
      fixed
    >
      <v-toolbar-title style="width: 300px" class="ml-0 pl-3">
        <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>
        <span class="hidden-sm-and-down">Quokka Intelligence</span>
      </v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon >
        <v-icon>apps</v-icon>
      </v-btn>
      <v-btn icon >
        <v-icon>exit_to_app</v-icon>
      </v-btn>
      <v-btn icon large>
        <v-avatar size="32px">
          <img
            src="https://d3ieicw58ybon5.cloudfront.net/ex/350.350/shop/product/89cb32bc8b1e448fa455f1e3e9c807f2.jpg"
            alt="Quokka"
          >
        </v-avatar>
      </v-btn>
    </v-toolbar>
  </div>
</template>
<script>
export default {
  data: () => ({
    dialog: false,
    drawer: null,
    items: [
      { icon: 'folder', text: 'Arquivos', endereco: '/file' },
      { icon: 'star', text: 'Favoritos', endereco: '/favorite' },
      { icon: 'trending_up', text: 'Consultas Dinamicas', endereco: '/query' },
      { icon: 'donut_small', text: 'Dashboards', endereco: '/dashboard' },
      {
        icon: 'keyboard_arrow_up',
        'icon-alt': 'keyboard_arrow_down',
        text: 'Analises Salvas',
        endereco: '/',
        model: true,
        children: [
          { icon: 'add', text: 'Criar Analise', endereco: '/dashboard' },
          { icon: 'poll', text: 'Analise 1', endereco: '/dash1' }
        ]
      },
      {
        icon: 'keyboard_arrow_up',
        'icon-alt': 'keyboard_arrow_down',
        text: 'Mais',
        endereco: '/',
        model: false,
        children: [
          { text: 'Import', endereco: '/rota1' },
          { text: 'Export', endereco: '/rota2' },
          { text: 'Print', endereco: '/rota3' },
          { text: 'Undo changes', endereco: '/rota4' },
          { text: 'Other contacts', endereco: '/rota5' }
        ]
      },
      { icon: 'settings', text: 'Configuracoes', endereco: '/settings' },
      { icon: 'help', text: 'Ajuda', endereco: '/help' },
      { icon: 'keyboard', text: 'Ir para versao padrao', endereco: '/default' }
    ]
  }),
  props: {
    source: String
  }
}
</script>
