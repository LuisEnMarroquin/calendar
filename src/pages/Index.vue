<template>
  <q-page class="flex flex-center">
    <div class="block">
      <q-date v-model="hoy" :events="eventsFn" today-btn event-color='accent' />
    </div>
  </q-page>
</template>

<script>
export default {
  name: 'PageIndex',
  data () {
    return {
      hoy: this.today(),
      start: '2019/05/06'
    }
  },
  methods: {
    pad (number, length) {
      var str = '' + number
      while (str.length < length) { str = '0' + str }
      return str
    },
    today () {
      var yyyy = new Date().getFullYear()
      var mm = new Date().getMonth() + 1
      mm = this.pad(mm, 2)
      var dd = new Date().getDate()
      dd = this.pad(dd, 2)
      var date = yyyy + '/' + mm + '/' + dd
      return date
    },
    eventsFn (date) {
      var daysDiference = this.diffDays(this.start, date)
      if (daysDiference % 3 === 0) return true
      else return false
    },
    diffDays (date1, date2) {
      var dt1 = new Date(date1)
      var dt2 = new Date(date2)
      return Math.floor(
        (
          Date.UTC(dt2.getFullYear(), dt2.getMonth(), dt2.getDate()) - Date.UTC(dt1.getFullYear(), dt1.getMonth(), dt1.getDate())
        ) / (1000 * 60 * 60 * 24)
      )
    }
  }
}
</script>
