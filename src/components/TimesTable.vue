<template>
  <div>
    {{ items }}
    {{ thingIClicked }}
    <v-list>
      <v-list-item
        v-for="(item, index) of items"
        :key="index"
      >
        <v-list-item-content
          v-if="index !== 2"
        >
            {{ index }} {{ item }}
        </v-list-item-content>
        <v-list-item-action>
          <v-btn
            text
            color="primary darken-2"
            @click="youClickedIt(item)"
          >
            btn
          </v-btn>
        </v-list-item-action>
      </v-list-item>
    </v-list>
  </div>
</template>

<script>
export default {
  name: 'TimesTable',
  data: function () {
    return {
      items: ['hello', 'world', 'good', 'bye'],
      headers: [],
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
