<template>
  <div class="pa-2">
    <v-card-text class="text-h4" v-html="getName"></v-card-text>
    <v-card-text class="text-h5 pt-0" v-html="getManufacturere"></v-card-text>
  </div>
</template>

<script>
export default {
  props: {
    name: {type: String, default: 'Name'},
    manufacturer: {type: String, default: 'Manufacturer'},
    matches: {
      type: Object, default: () => {
      }
    }
  },
  computed: {
    getName() {
      if (this.matches?.nameMatches?.length) {
        let name = this.name
        this.matches.nameMatches.forEach((match , _)=>{
          name = name.slice(0, match.indices[0][0]) + "<span class='highlight'>" + name.slice(match.indices[0][0], match.indices[0][1]+1) + "</span>" + name.slice(match.indices[0][1], name.length)
        })
        return name
      } else {
        return this.name
      }
    },
    getManufacturere() {
      if (this.matches?.manufacturerMatches?.length) {
        let name = this.manufacturer
        this.matches.manufacturerMatches.forEach((match , _)=>{
          name = name.slice(0, match.indices[0][0]) + "<span class='highlight'>" + name.slice(match.indices[0][0], match.indices[0][1]+1) + "</span>" + name.slice(match.indices[0][1], name.length)
        })
        return name
      } else {
        return this.manufacturer
      }
    },
  },
}
</script>
<style>
.highlight{
  font-weight: bold;
  text-decoration: underline
}
</style>
