<template>
  <section id="pricing" class="pricing">
    <div class="pricing__bg"></div>
    <div class="container">
      <div class="pricing__header">
        <span class="section-tag">Ihre Einstiegsmöglichkeiten</span>
        <h2 class="pricing__title">Wählen Sie Ihren <span>Einstieg</span></h2>
        <p class="pricing__desc">Von der kostenlosen Orientierung bis zur kontinuierlichen Entwicklung.</p>
      </div>

      <div class="pricing__tabs">
        <button
          v-for="tab in tabs"
          :key="tab.id"
          :class="['pricing__tab', { 'pricing__tab--active': activeTab === tab.id }]"
          @click="activeTab = tab.id"
        >{{ tab.label }}</button>
      </div>

      <!-- Individual Plans -->
      <div v-if="activeTab === 'individual'" class="pricing__cards">
        <div v-for="plan in individualPlans" :key="plan.name"
          :class="['pricing__card', { 'pricing__card--featured': plan.featured }]">
          <div v-if="plan.featured" class="pricing__popular">Empfohlen</div>
          <div class="pricing__plan-icon">{{ plan.icon }}</div>
          <h3>{{ plan.name }}</h3>
          <div class="pricing__price">
            <span class="pricing__amount">{{ plan.price }}</span>
            <span v-if="plan.period" class="pricing__period">{{ plan.period }}</span>
          </div>
          <p class="pricing__tagline">{{ plan.tagline }}</p>
          <ul class="pricing__features">
            <li v-for="f in plan.features" :key="f">
              <span class="pricing__check">✓</span> {{ f }}
            </li>
          </ul>
          <a href="#" :class="['btn btn--lg', plan.featured ? 'btn--primary' : 'btn--outline']" style="width:100%; justify-content:center;">
            {{ plan.cta }}
          </a>
        </div>
      </div>

      <!-- Agency Plans -->
      <div v-if="activeTab === 'agency'" class="pricing__cards">
        <div v-for="plan in agencyPlans" :key="plan.name"
          :class="['pricing__card', { 'pricing__card--featured': plan.featured }]">
          <div v-if="plan.featured" class="pricing__popular">Beliebt</div>
          <div class="pricing__plan-icon">{{ plan.icon }}</div>
          <h3>{{ plan.name }}</h3>
          <div class="pricing__price">
            <span class="pricing__amount">{{ plan.price }}</span>
            <span class="pricing__period">/ Monat</span>
          </div>
          <p class="pricing__tagline">{{ plan.tagline }}</p>
          <ul class="pricing__features">
            <li v-for="f in plan.features" :key="f">
              <span class="pricing__check">✓</span> {{ f }}
            </li>
          </ul>
          <a href="#" :class="['btn btn--lg', plan.featured ? 'btn--primary' : 'btn--outline']" style="width:100%; justify-content:center;">
            Jetzt starten
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const activeTab = ref('individual')

const tabs = [
  { id: 'individual', label: 'Für Unternehmen' },
  { id: 'agency', label: 'Für Agenturen' },
]

const individualPlans = [
  {
    name: 'GEO Quick Check',
    icon: '⚡',
    price: 'Kostenlos',
    period: '',
    tagline: 'Der schnelle Einstieg in Ihre AI Visibility',
    featured: false,
    cta: 'Quick Check starten',
    features: [
      'GEO Score (0–100)',
      'Zentrale Stärken & Schwächen',
      '3 erste Handlungshinweise',
      'In wenigen Minuten',
    ],
  },
  {
    name: 'GEO Deep Scan',
    icon: '🔬',
    price: '49 €',
    period: 'pro Analyse',
    tagline: 'Die fundierte Analyse Ihrer Sichtbarkeit',
    featured: true,
    cta: 'Analyse freischalten',
    features: [
      'Vollständiger GEO Score',
      'Detaillierter Analysebericht',
      'Konkrete Handlungsempfehlungen',
      'Klare Priorisierung der nächsten Schritte',
    ],
  },
  {
    name: 'GEO Pulse',
    icon: '📡',
    price: '39 €',
    period: '/ Monat',
    tagline: 'Kontinuierliche Sichtbarkeit & Kontrolle',
    featured: false,
    cta: 'GEO Pulse freischalten',
    features: [
      '1 vollständiger GEO Deep Scan / Monat',
      'Bis zu 2 zusätzliche Re-Scans',
      'GEO Score im Dashboard',
      'GEO Alerts bei Veränderungen',
      'Wettbewerbsvergleich',
    ],
  },
]

const agencyPlans = [
  {
    name: 'GEO Agency Starter',
    icon: '🚀',
    price: '99 €',
    tagline: 'Für den Einstieg in die AI Visibility Beratung',
    featured: false,
    features: [
      'Bis zu 5 aktive Projekte',
      '1 Scan pro Projekt / Monat',
      '2 zusätzliche Credits / Monat',
      'White-Label Reports',
      'Dashboard-Zugang',
    ],
  },
  {
    name: 'GEO Agency Growth',
    icon: '📈',
    price: '249 €',
    tagline: 'Für wachsende Agenturen',
    featured: true,
    features: [
      'Bis zu 15 aktive Projekte',
      '1 Scan pro Projekt / Monat',
      '10 zusätzliche Credits / Monat',
      'White-Label Reports',
      'Wettbewerbsvergleich inklusive',
    ],
  },
  {
    name: 'GEO Agency Scale',
    icon: '🏢',
    price: '499 €',
    tagline: 'Für größere Kundenportfolios',
    featured: false,
    features: [
      'Bis zu 40 aktive Projekte',
      '1 Scan pro Projekt / Monat',
      '20 zusätzliche Credits / Monat',
      'White-Label Reports',
      'Wettbewerbsvergleich inklusive',
    ],
  },
]
</script>

<style lang="scss" scoped>
@use '../assets/styles/variables' as *;

.pricing {
  padding: $space-3xl 0;
  background: $color-dark-green;
  position: relative;
  overflow: hidden;

  &__bg {
    position: absolute;
    inset: 0;
    background:
      radial-gradient(ellipse at 20% 50%, rgba($color-bright-green, 0.08) 0%, transparent 50%),
      radial-gradient(ellipse at 80% 20%, rgba($color-orange, 0.06) 0%, transparent 40%);
  }

  &__header {
    text-align: center;
    margin-bottom: $space-xl;
    position: relative;
  }

  &__title {
    font-size: clamp(2rem, 4vw, 3rem);
    color: $color-white;
    margin-bottom: $space-sm;

    span { color: $color-bright-green; }
  }

  &__desc {
    color: rgba($color-white, 0.6);
    font-size: 1.05rem;
  }

  &__tabs {
    display: flex;
    justify-content: center;
    gap: 0;
    background: rgba($color-white, 0.07);
    border: 1px solid rgba($color-white, 0.1);
    border-radius: 50px;
    padding: 4px;
    width: fit-content;
    margin: 0 auto $space-xl;
    position: relative;
  }

  &__tab {
    padding: 0.6rem 1.8rem;
    border-radius: 50px;
    border: none;
    background: transparent;
    color: rgba($color-white, 0.6);
    font-family: $font-body;
    font-size: 0.9rem;
    font-weight: 500;
    cursor: pointer;
    transition: all $transition-base;

    &--active {
      background: $color-bright-green;
      color: $color-white;
    }
  }

  &__cards {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: $space-md;
    position: relative;

    @media (max-width: $bp-lg) {
      grid-template-columns: 1fr;
      max-width: 420px;
      margin: 0 auto;
    }
  }

  &__card {
    background: rgba($color-white, 0.06);
    border: 1px solid rgba($color-white, 0.1);
    border-radius: 24px;
    padding: $space-lg;
    display: flex;
    flex-direction: column;
    gap: $space-sm;
    position: relative;
    transition: transform $transition-base, border-color $transition-base;

    &:hover {
      transform: translateY(-6px);
      border-color: rgba($color-bright-green, 0.4);
    }

    &--featured {
      background: rgba($color-white, 0.12);
      border-color: $color-bright-green;
      transform: scale(1.02);

      &:hover { transform: scale(1.02) translateY(-6px); }
    }
  }

  &__popular {
    position: absolute;
    top: -12px;
    left: 50%;
    transform: translateX(-50%);
    background: $color-orange;
    color: $color-white;
    font-size: 0.72rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    padding: 0.25rem 1rem;
    border-radius: 50px;
    white-space: nowrap;
  }

  &__plan-icon {
    font-size: 1.8rem;
  }

  h3 {
    font-size: 1.1rem;
    font-weight: 700;
    color: $color-white;
  }

  &__price {
    display: flex;
    align-items: baseline;
    gap: 0.3rem;
  }

  &__amount {
    font-family: $font-display;
    font-weight: 800;
    font-size: 2rem;
    color: $color-bright-green;
  }

  &__period {
    font-size: 0.85rem;
    color: rgba($color-white, 0.5);
  }

  &__tagline {
    font-size: 0.85rem;
    color: rgba($color-white, 0.6);
    line-height: 1.5;
    padding-bottom: $space-sm;
    border-bottom: 1px solid rgba($color-white, 0.08);
  }

  &__features {
    flex: 1;
    display: flex;
    flex-direction: column;
    gap: 0.6rem;
    margin-bottom: $space-sm;

    li {
      display: flex;
      gap: 0.5rem;
      font-size: 0.875rem;
      color: rgba($color-white, 0.75);
    }
  }

  &__check {
    color: $color-bright-green;
    flex-shrink: 0;
    font-weight: 600;
  }
}
</style>
