<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated class="tophead">
      <q-toolbar>
        <q-toolbar-title>
          <div id="maintitle">
             <img class="logo" :src="img.logo" alt="" >
          Calculadora de Rendimentos</div>
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>

export default {
  name: 'MainLayout',
  data () {
    return {
      img: {
        logo: require('../assets/invest-icon.png')
      }
    }
  }
}
</script>
