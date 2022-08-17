<template>
  <div>
    <v-toolbar dense>
      <v-toolbar-title>TimeTracker</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn>
        Links
      </v-btn>

      <v-btn>
        Features
      </v-btn>

    </v-toolbar>
    <v-container>
      <v-data-table
        v-model="selected"
        :headers="headers"
        :items="events"
        :single-select="singleSelect"
        :items-per-page="5"
        show-select
        class="elevation-1"
      >
      </v-data-table>
    </v-container>
    <v-btn
      color="green"
      fab
      absolute
      right
      large
      >
        <v-icon>mdi-plus-circle-outline</v-icon>
    </v-btn>
  </div>
</template>

<script>
export default {
  name: 'TimesTable',
  data: function () {
    return {
      singleSelect: false,
      selected: [],
      items: ['hello', 'world', 'good', 'bye'],
      headers: [
        {
          text: 'Description',
          align: 'start',
          sortable: true
        },
        {
          text: 'Start Time',
          sortable: true
        },
        {
          text: 'End Time',
          sortable: true
        },
        {
          text: 'Duration',
          sortable: true
        }],
      thingIClicked: 'NOTHING'
    }
  },
  computed: {
    numberOfHeaders () {
      return this.headers.length
    }
  },
  methods: {
    youClickedIt (input) {
      this.thingIClicked = input
    }
  }
}
</script>
