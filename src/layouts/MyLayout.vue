<template>
  <q-layout view="lHh Lpr lFf" class="backgroundApp">
    <q-header class="toolbar">
      <q-toolbar>
        <q-space />
          <q-btn
            flat
            dense
            round
            @click="leftDrawerOpen = !leftDrawerOpen"
            icon="menu"
            aria-label="Menu"
        />
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      elevated
    >
      <q-list>
        <q-item-label header class="menu" @click="leftDrawerOpen = !leftDrawerOpen">Menu</q-item-label>
        <q-item clickable  href="https://quasar.dev">
          <q-item-section avatar>
            <q-icon name="apps" />
          </q-item-section>
          <q-item-section>
            <q-item-label>App</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable  href="https://github.quasar.dev">
          <q-item-section avatar>
            <q-icon name="toggle_on" />
          </q-item-section>
          <q-item-section>
            <q-item-label>Réglage</q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  name: 'MyLayout',
  data () {
    return {
      leftDrawerOpen: false,
      textSizing: 2,
      dateNow: '',
      timeNow: ''
    }
  },
  methods: {
    getTime () {
      let timeStamp = Date.now()
      this.dateNow = timeStamp.formatDate(timeStamp, 'YYYY-MM-DDTHH:mm:ss.SSSZ')
      this.timeNow = timeStamp.formatDate(timeStamp, 'HH:mm')
      console.log(this.dateNow)
    }
  },
  mounted () {
    this.getTime()
  }
}
</script>

<style>
  .backgroundApp {
    background-color: black;
  }

  .fit, .menu{
    background-color: black;
    color: aquamarine;
  }

  .toolbar {
    background-color: rgba(0, 0, 0, 0);
    color: aquamarine;
  }
</style>
