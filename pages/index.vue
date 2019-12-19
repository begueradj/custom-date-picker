<template>
  <div>
    <custom-date-picker v-model="date" />
    <v-btn @click="getDate">
      Ok
    </v-btn>
  </div>
</template>

<script>
import CustomDatePicker from '@/components/CustomDatePicker.vue'

export default {
  components: { CustomDatePicker },
  data () {
    return {
      date: ''
    }
  },
  methods: {
    getDate () {
      console.log(this.date)
    }
  }
}
</script>
