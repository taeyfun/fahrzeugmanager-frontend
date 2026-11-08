<script setup lang="ts">
import { ref } from 'vue'

interface Fahrzeug {
  id: number
  marke: string
  modell: string
  baujahr: number
  kilometerstand: number
  einkaufspreis: number
  verkaufspreis: number
  favorit: boolean
  reserviert: boolean
}

const fahrzeuge = ref<Fahrzeug[]>([
  {
    id: 1,
    marke: 'VW',
    modell: 'Golf',
    baujahr: 2019,
    kilometerstand: 62000,
    einkaufspreis: 13500,
    verkaufspreis: 15900,
    favorit: true,
    reserviert: false,
  },
  {
    id: 2,
    marke: 'Audi',
    modell: 'A4',
    baujahr: 2018,
    kilometerstand: 89000,
    einkaufspreis: 16000,
    verkaufspreis: 18500,
    favorit: false,
    reserviert: true,
  },
  {
    id: 3,
    marke: 'BMW',
    modell: '320d',
    baujahr: 2020,
    kilometerstand: 41000,
    einkaufspreis: 22000,
    verkaufspreis: 24900,
    favorit: false,
    reserviert: false,
  },
])
</script>

<template>
  <table>
    <thead>
      <tr>
        <th>ID</th>
        <th>Marke</th>
        <th>Modell</th>
        <th>Baujahr</th>
        <th>Kilometerstand</th>
        <th>Einkaufspreis</th>
        <th>Verkaufspreis</th>
        <th>Favorit</th>
        <th>Reserviert</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="f in fahrzeuge" :key="f.id">
        <td>{{ f.id }}</td>
        <td>{{ f.marke }}</td>
        <td>{{ f.modell }}</td>
        <td>{{ f.baujahr }}</td>
        <td>{{ f.kilometerstand }}</td>
        <td>{{ f.einkaufspreis }}</td>
        <td>{{ f.verkaufspreis }}</td>
        <td>{{ f.favorit }}</td>
        <td>{{ f.reserviert }}</td>
      </tr>
    </tbody>
  </table>
</template>

<style scoped>
th, td {
  padding: 0 1.5rem;
  text-align: left;
}
</style>
