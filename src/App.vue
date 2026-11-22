<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <div class="app-shell">
    <aside class="sidebar">
      <RouterLink class="brand" to="/" aria-label="Fahrzeugmanager Startseite">
        <span class="brand-mark">F</span>
        <span>fahrwerk<span class="brand-dot">.</span><small>FAHRZEUGMANAGEMENT</small></span>
      </RouterLink>

      <div class="nav-label">MENÜ</div>
      <nav class="main-nav" aria-label="Hauptnavigation">
        <RouterLink class="nav-link" to="/"><span class="nav-icon">▦</span>Übersicht</RouterLink>
        <RouterLink class="nav-link" to="/"><span class="nav-icon">▣</span>Fahrzeuge<span class="nav-count">3</span></RouterLink>
        <RouterLink class="nav-link" to="/"><span class="nav-icon">↗</span>Verkäufe</RouterLink>
        <RouterLink class="nav-link" to="/"><span class="nav-icon">◷</span>Aktivitäten</RouterLink>
      </nav>

      <div class="sidebar-bottom">
        <div class="help-card"><span class="help-icon">?</span><strong>Fragen?</strong><p>Wir helfen dir gerne weiter.</p><a href="mailto:hallo@fahrwerk.de">Support kontaktieren <span>→</span></a></div>
        <div class="profile"><div class="avatar">TM</div><div><strong>Tom Müller</strong><small>Administrator</small></div><span class="profile-more">···</span></div>
      </div>
    </aside>

    <div class="main-column">
      <header class="topbar">
        <div class="breadcrumb">Workspace <span>/</span> <strong>Fahrzeugbestand</strong></div>
        <div class="topbar-actions"><button class="icon-button" aria-label="Benachrichtigungen">♧<i></i></button><div class="top-avatar">TM</div></div>
      </header>
      <RouterView />
    </div>
  </div>
</template>
