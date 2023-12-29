<template>
 
  <v-container fluid>
    <v-footer id="footer"
      class="text-center d-flex flex-column"
      height="200px"
      img src="/assets/img/captura.jpeg" alt=""
      bg-image="assets/img/captura.jpeg"
    >
   <div>
        <v-btn
          v-for="icon in icons"
          :key="icon"
          class="mx-4"
          :icon="icon"
          variant="text"
          
        ></v-btn>
     
      </div>
      <div class="pt-0">
        <v-toolbar
         height="90"
          
          :color="color"
          :flat="flat"
          dark
          class="px-15"
          :class="{ expand: flat }"
        >
        
            <v-toolbar-title> <v-img src="@/assets/img/logocury.png" max-width="100px" /></v-toolbar-title>
  
            <v-toolbar-title>
            <v-img src="@/assets/img/origemlogo.jpeg" max-width="200px" />
          </v-toolbar-title>
          <v-toolbar-title>
            <v-img src="@/assets/img/cury.jpg" max-width="100px" />
          </v-toolbar-title>
          <v-spacer />
          <v-app-bar-nav-icon
            @click.stop="drawer = !drawer"
            class="mr-4"
            v-if="isXs"
          />
          <div v-else>
            <v-btn text @click="$vuetify.goTo('#hero')">
              <span class="mr-2 text-brown">Sobre</span>
              
            </v-btn>
            <v-btn text @click="$vuetify.goTo('#features')">
              <span class="mr-2 text-brown">Plantas</span>
            </v-btn>
            <v-btn text @click="$vuetify.goTo('#download')">
              <span class="mr-2 text-brown">Construtora</span>
            </v-btn>
            <v-btn text @click="$vuetify.goTo('#pricing')">
              <span class="mr-2 text-brown">Preços</span>
            </v-btn>
            <v-btn rounded outlined  @click="$vuetify.goTo('#contact')">
              <span class="mr-2 text-brown">Contato</span>
            </v-btn>
          </div>
        </v-toolbar>  
      </div>
  
      <v-divider></v-divider>
  
      <div>
        {{ new Date().getFullYear() }} — <strong>Maicon Roberto</strong>
      </div>
  
    </v-footer>
  </v-container>
  </template>
  <script>
    export default {
      data: () => ({
        icons: [
          'mdi-facebook',
          'mdi-twitter',
          'mdi-linkedin',
          'mdi-instagram',
        ],
      }),
    }
  </script>
  <style scoped>
  .footer {
    background-image: url('/@/assets/img/captura.jpeg');
  }
  </style>