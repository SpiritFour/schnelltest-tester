<template>
  <div class="pa-md-2">
    <v-card-text class="text-md-h5 text-h6 pb-1" v-html="getName"></v-card-text>
    <v-card-text
      class="text-md-body-1 text-body-2 py-0"
      v-html="getManufacturere"
    ></v-card-text>

    <v-card-text class="text-md-subtitle-1 text-md-subtitle-2 grey--text pt-1">
      Erkennt Omikron {{ sensitive ? 'gut' : 'schlecht' }}
    </v-card-text>
  </div>
</template>

<script>
export default {
  props: {
    sensitive: { type: Boolean, default: undefined },
    name: { type: String, default: 'Name' },
    manufacturer: { type: String, default: 'Manufacturer' },
    matches: {
      type: Object,
      default: () => {},
    },
  },
  computed: {
    getName() {
      if (this.matches?.nameMatches?.length) {
        let name = this.name
        this.matches.nameMatches[0].indices =
          this.matches.nameMatches[0].indices.sort((p, c, _) => {
            if (
              p.indices?.[1] - p.indices?.[0] >=
              c.indices?.[1] - c.indices?.[0]
            ) {
              return 1
            }
            return -1
          })[0]
        name =
          name.slice(0, this.matches.nameMatches[0].indices[0]) +
          "<span class='highlight'>" +
          name.slice(
            this.matches.nameMatches[0].indices[0],
            this.matches.nameMatches[0].indices[1] + 1
          ) +
          '</span>' +
          name.slice(this.matches.nameMatches[0].indices[1] + 1, name.length)
        return name
      } else {
        return this.name
      }
    },
    getManufacturere() {
      if (this.matches?.manufacturerMatches?.length) {
        let name = this.manufacturer
        this.matches.manufacturerMatches[0].indices =
          this.matches.manufacturerMatches[0].indices.sort((p, c, _) => {
            if (
              p.indices?.[1] - p.indices?.[0] >=
              c.indices?.[1] - c.indices?.[0]
            ) {
              return 1
            }
            return -1
          })[0]
        name =
          name.slice(0, this.matches.manufacturerMatches[0].indices[0]) +
          "<span class='highlight'>" +
          name.slice(
            this.matches.manufacturerMatches[0].indices[0],
            this.matches.manufacturerMatches[0].indices[1] + 1
          ) +
          '</span>' +
          name.slice(
            this.matches.manufacturerMatches[0].indices[1] + 1,
            name.length
          )
        return name
      } else {
        return this.manufacturer
      }
    },
  },
}
</script>
<style>
.highlight {
  font-weight: bold;
  text-decoration: underline;
}
</style>
