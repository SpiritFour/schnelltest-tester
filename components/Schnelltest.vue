<template>
  <v-card outlined class="mb-md-4 mb-2 rounded-xl">
    <div style="display: flex; align-items: baseline">
      <div>
        <v-icon
          large
          :color="test['omicron-sensitive'] ? 'green' : 'red'"
          class="ml-md-8 ml-4 mt-1 mt-md-2"
          >{{
            test['omicron-sensitive'] ? 'mdi-check-circle' : 'mdi-alert-circle'
          }}
        </v-icon>
      </div>
      <SchnelltestName
        style="flex-grow: 1"
        :name="test.name"
        :sensitive="test['omicron-sensitive']"
        :manufacturer="test.manufacturer"
        :matches="test.matches"
      />
    </div>
  </v-card>
</template>
<script>
import SchnelltestName from './SchnelltestName.vue'
export default {
  components: { SchnelltestName },
  props: { test: { type: Object, default: () => {} } },
}
</script>

<style></style>
