<template>
    <v-card>
      <v-toolbar
        color="transparent"
        dark
      >
        <v-app-bar-nav-icon></v-app-bar-nav-icon>
  
        <v-toolbar-title>MAR Advisory</v-toolbar-title>
  
        <v-spacer></v-spacer>
  
        <v-btn icon>
          <v-icon>mdi-magnify</v-icon>
        </v-btn>
  
        <v-btn icon>
          <v-icon>mdi-dots-vertical</v-icon>
        </v-btn>
  
        <template v-slot:extension>
          <v-tabs
            v-model="currentItem"
            fixed-tabs
            center
            dense
          >
            <v-tab
              v-for="item in items"
              :key="item"
              :value="'tab-' + item"
            >
              {{ item }}
           
            </v-tab>
  
            <v-menu
              v-if="more.length"
            >
              <template v-slot:activator="{ props }">
                <v-btn
                  variant="plain"
                  rounded="0"
                  class="align-self-center me-4"
                  height="100%"
                  v-bind="props"
                >
                  mais
                  <v-icon end>
                    mdi-menu-down
                  </v-icon>
                </v-btn>
              </template>
  
              <v-list class="bg-grey-lighten-3">
                <v-list-item
                  v-for="item in more"
                  :key="item"
                  @click="addItem(item)"
                >
                  {{ item }}
                </v-list-item>
              </v-list>
            </v-menu>
          </v-tabs>
        </template>
      </v-toolbar>
  
      <v-window v-model="currentItem">
        <v-window-item
          v-for="item in items.concat(more)"
          :key="item"
          :value="'tab-' + item"
        >
          <v-card flat>
            <v-card-text>
              <h2>{{ item }}</h2>
              {{ text }}
            </v-card-text>
          </v-card>
        </v-window-item>
      </v-window>
    </v-card>
  </template>
  <script>
    export default {
      data: () => ({
        currentItem: 'tab-Web',
        items: [
          'Produtos Financeiros','Assessoria de investimentos', 'Gestão de Fundos', 'Investimentos Alternativos', 'Assessoria Imobiliária','Conteúdo', 'Sobre',
        ],
        more: [
          'Mercado Livre Energia', 'Investimentos Imobiliários', 'Venture Capital', 'Operações Estruturadas', 'Research',
        ],
        text: ''
      }),
  
      methods: {
        addItem (item) {
          const removed = this.items.splice(0, 1)
          this.items.push(
            ...this.more.splice(this.more.indexOf(item), 1),
          )
          this.more.push(...removed)
          this.$nextTick(() => { this.currentItem = 'tab-' + item })
        },
      },
    }
  </script>