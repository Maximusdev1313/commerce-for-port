

<script setup>
import {useRoute} from 'vue-router'
import {ref, onMounted,watch} from 'vue'
import {useApiStore} from 'src/stores'
import card from 'src/components/card.vue'
import axios from 'axios'
let store = useApiStore()
let route = useRoute()
let list = ref([])
onMounted(()=>{
    store.getProducts(route.params.id)
})

    watch(
  () => route.params.id,
  (route) => (route = route <= store.categories  ? store.getProducts(route): route),
);
</script>

<template>
    <q-page>
        <div>
        detail 
        {{ route.params.id }}
<Suspense >
    <card :products="store.products" v-if="store.products.length"/>

</Suspense>
    </div>
    </q-page>
   
</template>