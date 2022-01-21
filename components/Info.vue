<template>
  <div class="text-center">
    <div style="width: 100%" class="ma-auto py-4 text-md-body-1 text-body-2 my-3" v-bind:class="{ desktopContainer: $vuetify.breakpoint.mdAndUp }">
      Welcher Schnelltest erkennt noch Omikron Sars-CoV-2? Da die <a
      href="https://www.pei.de/DE/newsroom/hp-meldungen/2021/211230-antigentests-omikron-variante.html"
    >
      Tabellen</a
    > des PEI sehr
      unübersichtlich und schlecht zu lesen sind haben wir eine schöne Suche gebaut.
      Jetzt kannst du selbst einfach nachschauen ob dein
      Schnelltest auch Omikron noch erkennt.

    </div>
    <div class="text-md-h4 text-h6 font-weight-bold">
      Suche jetzt!
    </div>
  </div>
</template>

<style scoped>
.desktopContainer {
  max-width: 700px !important;
}
</style>
