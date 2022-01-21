<template>
  <v-card
    class="mb-4 rounded-xl"
    :color="test['omicron-sensitive'] ? 'success' : 'error'"
  >
    <div style="display: flex; align-items: center">
      <div>
        <v-img
          class="ml-8"
          :src="test['omicron-sensitive'] ?  './ok-hand.png':'./microbe.png' "
          height="70px"
          width="70px"
        />
      </div>
      <SchnelltestName
        style="flex-grow: 1"
        :name="test.name"
        :manufacturer="test.manufacturer"
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
