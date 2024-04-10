<template>
  <q-page class="flex flex-center flex-col">
    <div class="q-pa-md" v-if="rows.length > 0">
      <div class="q-pa-md row items-start q-gutter-md">
        <q-card class="my-card">
          <q-card-section>
            {{rows[0].name}}
          </q-card-section>
        </q-card>
      </div>

      <div class="q-pa-md row items-start q-gutter-md">
        <q-card class="my-card">
          <q-card-section>
            {{ rows[1].name }}
          </q-card-section>
        </q-card>
      </div>

      <div class="q-pa-md row items-start q-gutter-md">
        <q-card class="my-card">
          <q-card-section>
            {{ rows[2].name }}
          </q-card-section>
        </q-card>
      </div>

      <q-table
        style="height: 60vh; width: 80vw;"
        flat bordered
        title="Pokemons"
        :rows="rows"
        row-key="index"
        virtual-scroll
        v-model:pagination="pagination"
        :rows-per-page-options="[0]"
      />
    </div>
  </q-page>
</template>

<script setup>
import { usePokemonStore } from 'src/stores/pokemon-store';

const pokemonStore = usePokemonStore();

pokemonStore.fetchPokemons();


const rows = pokemonStore.pokemons;
const pagination = {
  rowsPerPage: 20
}

defineOptions({
  name: 'IndexPage'
});
</script>
