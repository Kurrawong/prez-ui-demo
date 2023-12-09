<script setup lang="ts">
import type { HeaderLink } from '~/lib/prez.d';
const route = useRoute();
const props = defineProps<{links: HeaderLink[]|undefined}>();
</script>
<template>
    <v-card
    class="mx-auto"
    max-width="800"
    flat
    >
      <v-card-text>
        <h2>Profiles</h2>
<v-chip-group  v-if="links">
    <v-chip 
        :class="route.query._profile == link.token ? 'active': ''"
        :to="{query: {_profile: link.token}}" v-for="link in links.filter(link=>link.title).sort((a,b)=>a.title! > b.title! ? 1 : (a.title! < b.title! ? -1 : 0))">
      {{ link.title }}
    </v-chip>
    </v-chip-group>
  </v-card-text>
  </v-card>

</template>
<style scoped>
.active {
    background-color: #555;
    color: white;
}
</style>