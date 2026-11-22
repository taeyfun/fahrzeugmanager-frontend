<script setup lang="ts">
import Fahrzeugliste from '@/components/Fahrzeugliste.vue'
</script>

<template>
  <main class="page-content">
    <div class="page-heading">
      <div><div class="eyebrow">MONTAG, 24. JUNI 2024</div><h1>Fahrzeugbestand</h1><p>Behalte deinen Bestand und alle wichtigen Kennzahlen im Blick.</p></div>
      <button class="primary-button"><span>＋</span> Fahrzeug hinzufügen</button>
    </div>

    <section class="stats-grid" aria-label="Bestandskennzahlen">
      <article class="stat-card"><div class="stat-top"><span>Fahrzeuge im Bestand</span><span class="stat-icon blue">▣</span></div><strong>03</strong><div class="stat-foot"><span class="trend">↗</span> Alle Fahrzeuge im Überblick</div></article>
      <article class="stat-card"><div class="stat-top"><span>Bestandswert</span><span class="stat-icon violet">€</span></div><strong>51.500 <small>€</small></strong><div class="stat-foot"><span class="muted-dot"></span> Gesamter Einkaufspreis</div></article>
      <article class="stat-card"><div class="stat-top"><span>Verkaufswert</span><span class="stat-icon green">↗</span></div><strong>59.300 <small>€</small></strong><div class="stat-foot"><span class="trend">↗</span> Potenzieller Erlös</div></article>
      <article class="stat-card"><div class="stat-top"><span>Reserviert</span><span class="stat-icon amber">◷</span></div><strong>01</strong><div class="stat-foot"><span class="amber-text">●</span> In Verhandlung</div></article>
    </section>

    <section class="inventory-panel">
      <div class="panel-heading"><div><h2>Deine Fahrzeuge</h2><p>Verwalte und sortiere alle Fahrzeuge in deinem Bestand.</p></div><button class="filter-button">☷ <span>Filter</span></button></div>
      <Fahrzeugliste />
      <div class="table-footer"><span>1–3 von 3 Fahrzeugen</span><div class="pagination"><button disabled aria-label="Vorherige Seite">‹</button><button class="current-page">1</button><button disabled aria-label="Nächste Seite">›</button></div></div>
    </section>
    <footer class="page-footer"><span>© 2024 Fahrwerk</span><span>Mit Sorgfalt für deinen Fuhrpark gemacht <b>✳</b></span></footer>
  </main>
</template>
