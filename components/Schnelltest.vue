<template>
  <v-card
    class="mb-4 rounded-xl"
    :color="test['omicron-sensitive'] ? 'error' : 'success'"
  >
    <div style="display: flex; align-items: center">
      <div>
        <v-img
          class="ml-8"
          :src="test['omicron-sensitive'] ? './microbe.png' : './ok-hand.png'"
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
