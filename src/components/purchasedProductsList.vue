<script setup>
import {useApiStore} from 'src/stores'
const store = useApiStore()
</script>

<template>
  <div v-for="s in store.prod" :key="s">
    {{s.nomi}}
  </div>
    <div class="q-pa-md q-gutter-md">
        <q-list bordered class="rounded-borders" style="max-width: 90%">
      <q-item-label header>Friends</q-item-label>

      <q-item clickable v-ripple v-for="products in store.purchasedProducts" :key="products">
        <q-item-section avatar>
          <q-avatar>
            <img src="https://cdn.quasar.dev/img/avatar2.jpg">
          </q-avatar>
        </q-item-section>

        <q-item-section>
          <q-item-label lines="1">Brunch this weekend?</q-item-label>
          <q-item-label caption lines="2">
            <span class="text-weight-bold">Janet</span>
            -- I'll be in your neighborhood doing errands this
            weekend. Do you want to grab brunch?
          </q-item-label>
        </q-item-section>

        <q-item-section side top>
          1 min ago
        </q-item-section>
      </q-item>

      <q-separator inset="item" />
      </q-list>
    </div>
</template>