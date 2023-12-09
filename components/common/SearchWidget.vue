<script setup lang="ts">
const route = useRoute();
const router = useRouter();
const runtimeConfig = useRuntimeConfig();

const q = ref(route.query.q);

function submitClick() {
    router.push({query: {...route.query, q: q.value}});
}
const searchTermQuery = computed(() => {
    return 'q' in route.query && route.query.q !== '' ? route.fullPath : null;
});
</script>
<template>
    <v-card
    class="mx-auto"
    max-width="800"
    flat
    >
    <v-card-text>
        <h2 class="mb-5">Search collection</h2>
        
        <form class="d-flex justify-end mt-5" method="get" @submit.stop.prevent="submitClick">
            <v-text-field
                density="compact"
                variant="solo"
                label="Enter text to lookup"
                append-inner-icon="mdi-magnify"
                single-line
                hide-details
                :autofocus="true"
                name="q"
                v-model="q"
            ></v-text-field>
        </form>
    </v-card-text>
    </v-card>
</template>