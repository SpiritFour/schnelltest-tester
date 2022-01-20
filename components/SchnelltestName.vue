<template>
  <div class="pa-2">
    <v-card-text class="text-h4">{{ name }}</v-card-text>
    <v-card-text class="text-h5 pt-0">{{ manufacturer }}</v-card-text>
  </div>
</template>

<script>
export default {
  props: {
    name: { type: String, default: 'Name' },
    manufacturer: { type: String, default: 'Manufacturer' },
  },
}
</script>
