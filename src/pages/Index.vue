<template>
  <q-page class="flex flex-top q-ma-md">
    <div>
      <div class="dateTime q-ma-xl">
        <div class="row">
          <p>{{dateNow}}</p>
        </div>
        <div class="row">
          <p>{{timeNow}}</p>
        </div>
      </div>

      <div class="justify-center">
        <q-video
        src="https://www.youtube.com/embed/ooeyFipBxXU"
        class="videoPlayer"
        />
      </div>
    </div>
  </q-page>
</template>

<script>
import { date } from 'quasar'
export default {
  name: 'PageIndex',
  data () {
    return {
      dateNow: '',
      timeNow: ''
    }
  },
  methods: {
    getTime () {
      let timeStamp = Date.now()
      let frenchDate = {
        days: ['Dimanche', 'Lundi', 'Mardi', 'Mercredi', 'Jeudi', 'Vendredi', 'Samedi'],
        months: ['janvier', 'février', 'mars', 'avril', 'mai', 'juin', 'juillet', 'aout', 'septembre', 'octobre', 'novembre', 'décembre']
      }
      this.dateNow = date.formatDate(timeStamp, 'dddd D MMMM', frenchDate)
      this.timeNow = date.formatDate(timeStamp, 'HH:mm')
      console.log(this.dateNow)
    }
  },
  created () {
    this.getTime()
    setInterval(() => {
      this.getTime()
    }, 60000)
  }
}
</script>

<style>
  .dateTime {
    color: aquamarine;
  }

  .videoPlaye {
    width: 200%;
    height: auto;
  }
</style>
