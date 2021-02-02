<template>
  <q-layout>
    <q-header elevated>
      <q-toolbar>
        <q-toolbar-title class="text-bold">
          RafaCalc
        </q-toolbar-title>
        <q-btn
          flat
          round
          dense
          icon="edit"
        />
      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  data () {
    return {
    }
  }
}
</script>
