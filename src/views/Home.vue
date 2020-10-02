<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <Kachel/>
    <KachelGrid/>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

import Kachel from "@/components/Kachel.vue";
import KachelGrid from "@/components/KachelGrid.vue"

@Component({
  components: {
    Kachel,
    KachelGrid
  }
})
export default class Home extends Vue {}
</script>
