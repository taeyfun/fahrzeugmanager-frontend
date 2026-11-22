<script setup lang="ts">
import { ref, onMounted } from 'vue'

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

const API_URL = import.meta.env.VITE_API_URL ?? 'http://localhost:8080'

const fahrzeuge = ref<Fahrzeug[]>([])
const fehler = ref<string | null>(null)

onMounted(async () => {
  try {
    const response = await fetch(`${API_URL}/fahrzeuge`)
    if (!response.ok) {
      throw new Error(`Server antwortete mit Status ${response.status}`)
    }
    fahrzeuge.value = await response.json()
  } catch (e) {
    fehler.value = 'Fahrzeuge konnten nicht geladen werden.'
    console.error(e)
  }
})

const numberFormat = new Intl.NumberFormat('de-DE')
const currencyFormat = new Intl.NumberFormat('de-DE', {
  style: 'currency',
  currency: 'EUR',
  maximumFractionDigits: 0,
})
</script>

<template>
  <p v-if="fehler">{{ fehler }}</p>
  <div class="table-scroll">
    <table class="vehicle-table">
      <thead>
        <tr>
          <th>FAHRZEUG</th>
          <th>BAUJAHR</th>
          <th>KILOMETERSTAND</th>
          <th>EINKAUFSPREIS</th>
          <th>VERKAUFSPREIS</th>
          <th>STATUS</th>
          <th><span class="sr-only">Aktionen</span></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="f in fahrzeuge" :key="f.id">
          <td>
            <div class="vehicle-cell">
              <div class="vehicle-logo" :class="`brand-${f.marke.toLowerCase()}`">
                {{ f.marke.slice(0, 1) }}
              </div>
              <div>
                <strong>{{ f.marke }} {{ f.modell }}</strong
                ><small
                  >FZG-{{ String(f.id).padStart(4, '0') }}
                  <span v-if="f.favorit" class="favorite">★ Favorit</span></small
                >
              </div>
            </div>
          </td>
          <td>{{ f.baujahr }}</td>
          <td>{{ numberFormat.format(f.kilometerstand) }} <span class="unit">km</span></td>
          <td>{{ currencyFormat.format(f.einkaufspreis) }}</td>
          <td class="selling-price">{{ currencyFormat.format(f.verkaufspreis) }}</td>
          <td>
            <span class="status-pill" :class="f.reserviert ? 'reserved' : 'available'"
              ><i></i>{{ f.reserviert ? 'Reserviert' : 'Verfügbar' }}</span
            >
          </td>
          <td>
            <button class="row-menu" :aria-label="`Aktionen für ${f.marke} ${f.modell}`">
              ···
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
