<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          size="10px"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />
        
        <q-toolbar-title>
          Parcefone: Sistema de inventario
          <q-icon 
            name="fab fa-pied-piper-square"
            size="35px"
          />
        </q-toolbar-title>
        

        <div>COMODISIMOS</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      class="bg-grey-1"
    >
      <q-list>
        <q-item-label
          header
          class="text-grey-8"
        >
          Menu
        </q-item-label>

        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
  {
    title: 'Registrar equipo',
    caption: 'Monitores, PCs, portatiles, etc.',
    icon: "far fa-save",
    link: 'http://localhost:9090/#/registrar'
  },
  {
    title: 'Realizar una accion',
    caption: 'Actualizar caracteristicas, dar de baja, etc.',
    icon: "fas fa-magic",
    link: 'http://localhost:9090/#/registrar'
  },
  {
    title: 'Manual de usuario',
    caption: 'Manual con las instrucciones del software',
    icon: "fas fa-book-reader",
    link: 'http://localhost:9090/#/registrar'
  },
];

import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialLink
  },

  setup () {
    const leftDrawerOpen = ref(false)

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
})
</script>
