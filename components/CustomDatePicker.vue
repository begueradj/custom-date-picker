<template>
  <v-container fill-height>
    <v-row justify="center" align="center">
      <v-col cols="12">
        <!-- Date picker -->
        <v-menu
          ref="menu1"
          v-model="menu1"
          :close-on-content-click="false"
          :return-value.sync="date"
          transition="scale-transition"
          offset-y
        >
          <template v-slot:activator="{ on }">
            <v-text-field
              v-model="dateFormatted"
              @blur="date = parseDate(dateFormatted)"
              v-on="on"
              :label="value"
              value
              color="green lighten-1"
            />
          </template>
          <v-date-picker
            v-bind:value="value"
            v-on:input="$emit('input', $event)"
            @input="menu1 = false"
            no-title
            header-color="green lighten-1"
            color="green lighten-1"
          />
        </v-menu>
        <!-- end of date picker -->
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'CustomDatePicker',
  props: {
    value: {
      type: String,
      default: ''
    }
  },
  data () {
    return {
      menu1: null,
      date: null,
      dateFormatted: null
    }
  },

  computed: {
    computedDateFormatted () {
      return this.formatDate(this.date)
    }
  },

  watch: {
    date (val) {
      this.dateFormatted = this.formatDate(this.date)
    }
  },
  methods: {
    formatDate (date) {
      if (!date) { return null }
      return date
    },
    parseDate (date) {
      if (!date) { return null }

      const [year, month, day] = date.split('-')
      return `${year}-${month.padStart(2, '0')}-${day.padStart(2, '0')}`
    }
  }
}
</script>
