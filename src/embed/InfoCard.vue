<template>
  <b-container class="mt-3">
    <b-row>
      <div class="d-flex flex-wrap w-100 justify-content-center">
        <Info-card :title="title" :field="field" :good-direction="goodDirection" />
      </div>
    </b-row>
  </b-container>
</template>

<script>
import InfoCard from "components/cards/InfoCard";

export default {
  name: "StatsPage",
  components: {
    InfoCard
  },
  data() {
    return {
      title: null,
      field: null,
      goodDirection: null,
    }
  },
  created() {
    const cards = {
      'confirmedCases': {
        title: 'Potrjeno okuženi',
        field: 'tests.positive.todate',
        goodDirection: 'down',
      },
      'hospitalized': {
        title: 'Hospitalizirani',
        field: 'state.in_hospital',
        goodDirection: 'down',
      },
      'icu': {
        title: 'Intenzivna enota',
        field: 'state.icu',
        goodDirection: 'down',
      },
      'deceased': {
        title: 'Umrli',
        field: 'state.deceased.todate',
        goodDirection: 'down',
      },
      'recovered': {
        title: 'Ozdraveli',
        field: 'state.recovered.todate',
        goodDirection: 'up',
      },
    }

    let data = cards[this.$route.params.type]

    this.title = data.title
    this.field = data.field
    this.goodDirection = data.goodDirection
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="sass">
</style>
