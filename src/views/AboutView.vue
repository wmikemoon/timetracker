<template>
  <div class="about">
    <form>
    <v-text-field
      v-model="amount"
      label="Main input"
      type="number"
      hide-details="auto"
    />
    <div
      v-for="(percent, index) in percents"
      :key="index"
    >
      <v-btn
        @click="currentPercent = Number(percent)"
        >
        {{ percent }}
      </v-btn>
    </div>
    <div>
    {{ owed }}
    </div>
    </form>
  </div>
</template>
<script>
export default {
  name: 'AboutView',
  props: {}, // Values Passed into the component ($emit value back up)
  data: function () {
    return {
      amount: 0,
      percents: [0, 5, 10, 20],
      currentPercent: 0
    }
  },
  methods: {}, // general functions
  mounted () {}, // get called when the COMPONENT is mounted
  computed: { // functions, that are treated like DATA
    owed () {
      const formatter = new Intl.NumberFormat('en-US', {
        style: 'currency',
        currency: 'USD'
      })

      // return (Number(this.amount) * (this.percent / 100)) + Number(this.amount)
      const amt = Number(this.amount)
      const percent = Number(this.currentPercent)
      // if (percent === 0) return 0
      // const total = amt + amt * percent / 100
      const total = percent === 0 ? 0 : amt + amt * percent / 100
      return formatter.format(total)
    }
  }
}
</script>
