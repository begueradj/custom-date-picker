<template>
  <div>
    <custom-date-picker v-model="date" />
    <custom-date-picker2 v-model="date2" />
    <v-btn @click="getDate">
      Ok
    </v-btn>
  </div>
</template>

<script>
import CustomDatePicker from '@/components/CustomDatePicker.vue'
import CustomDatePicker2 from '@/components/CustomDatePicker2.vue'

export default {
  components: { CustomDatePicker, CustomDatePicker2 },
  data () {
    return {
      date: '',
      date2: null
    }
  },
  methods: {
    getDate () {
      console.log(this.date + 'Date 2: ' + this.date2)
    }
  }
}
</script>
