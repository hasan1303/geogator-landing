<template>
  <!-- Agencies section - linked from navbar -->
  <section id="agencies" class="agencies">
    <div class="container">
      <div class="agencies__grid">
        
        <!-- Left column: text content -->
        <div class="agencies__content">
          <span class="section-tag">Für Agenturen</span>
          <h2 class="agencies__title">
            Verschaffen Sie Ihren Kunden klare 
            <span>Wettbewerbsvorteile</span>
          </h2>
          <p>GEOGATOR liefert die strukturierte Grundlage, um Sichtbarkeit in KI-Systemen zu analysieren, einzuordnen und in konkrete Beratung zu überführen.</p>

          <!-- Loop through benefits array -->
          <div class="agencies__benefits">
            <div class="agencies__benefit" v-for="b in benefits" :key="b">
              <span class="agencies__benefit-dot"></span>
              {{ b }}
            </div>
          </div>

          <!-- Business model card -->
          <div class="agencies__model">
            <h3>Ihr Geschäftsmodell</h3>
            <div class="agencies__model-items">
              <!-- Loop through models array (icon, label, desc) -->
              <div class="agencies__model-item" v-for="m in models" :key="m.label">
                <span class="agencies__model-icon">{{ m.icon }}</span>
                <div>
                  <strong>{{ m.label }}</strong>
                  <p>{{ m.desc }}</p>
                </div>
              </div>
            </div>
          </div>

          <a href="#" class="btn btn--green btn--lg">Partnerprogramm anfragen</a>
        </div>

        <!-- Right column: stats + credit card -->
        <div class="agencies__visual">
          <!-- Loop through stats array (icon, value, label) -->
          <div class="agencies__stat-card" v-for="stat in stats" :key="stat.label">
            <span class="agencies__stat-icon">{{ stat.icon }}</span>
            <div>
              <strong>{{ stat.value }}</strong>
              <p>{{ stat.label }}</p>
            </div>
          </div>

          <!-- Credit system info card -->
          <div class="agencies__credit-card">
            <div class="agencies__credit-header">
              <span>Das Credit-System</span>
              <span class="agencies__credit-badge">Flexibel</span>
            </div>
            <p>1 Credit = 1 zusätzlicher Scan</p>
            <ul>
              <li>Zusätzliche Analysen für bestehende Kunden</li>
              <li>Kurzfristige Deep Dives</li>
              <li>Flexible Nutzung ohne Paketwechsel</li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
// Benefits list shown as bullet points
const benefits = [
  'Fundierte Analysen mit klaren Zahlen',
  'Klare Handlungsempfehlungen',
  'Nachvollziehbare Ergebnisse',
  'Starke Argumentationsbasis gegenüber Kunden',
  'White-Label Reports im eigenen Branding',
]

// Business model options (icon, title, description)
const models = [
  { icon: '💼', label: 'GEO Analyse als eigenständige Leistung', desc: 'z. B. 500–1.000 € pro Kunde' },
  { icon: '🔗', label: 'Integration in Strategie-Projekte', desc: 'Als Grundlage für Content & Kommunikation' },
  { icon: '🔄', label: 'Kontinuierliche Betreuung', desc: 'Über Monitoring und regelmäßige Re-Scans' },
]

// Stats displayed in right column cards
const stats = [
  { icon: '🏢', value: '5–40', label: 'aktive Projekte je nach Paket' },
  { icon: '📊', value: 'White-Label', label: 'Reports im eigenen Branding' },
  { icon: '⚡', value: 'Sofort', label: 'nach Freischaltung startbereit' },
]
</script>

<style lang="scss" scoped>
/* Styles apply only to this component (scoped) */
@use '../assets/styles/variables' as *;

.agencies {
  padding: $space-3xl 0;
  background: $color-white;

  /* Two-column layout, stacks on tablet/mobile */
  &__grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: $space-2xl;
    align-items: start;

    @media (max-width: $bp-lg) {
      grid-template-columns: 1fr;
    }
  }

  &__content {
    h2 { margin-bottom: $space-sm; }
    > p {
      color: $color-gray;
      line-height: 1.7;
      margin-bottom: $space-lg;
    }
  }

  /* Responsive font size using clamp() */
  &__title {
    font-size: clamp(1.8rem, 3.5vw, 2.6rem);
    color: $color-dark;
    margin-bottom: $space-sm;

    span { color: $color-brand-green; }
  }

  &__benefits {
    display: flex;
    flex-direction: column;
    gap: 0.6rem;
    margin-bottom: $space-lg;
  }

  /* Each benefit row: green dot + text */
  &__benefit {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    font-size: 0.95rem;
    color: $color-gray;

    &-dot {
      width: 8px;
      height: 8px;
      border-radius: 50%;
      background: $color-bright-green;
      flex-shrink: 0;
    }
  }

  &__model {
    background: $color-sage-light;
    border: 1px solid $color-border;
    border-radius: 20px;
    padding: $space-md;
    margin-bottom: $space-lg;

    h3 { font-size: 1rem; color: $color-dark; margin-bottom: $space-sm; }
  }

  &__model-items {
    display: flex;
    flex-direction: column;
    gap: $space-sm;
  }

  &__model-item {
    display: flex;
    gap: 0.75rem;
    align-items: flex-start;

    &-icon { font-size: 1.2rem; flex-shrink: 0; }
    strong { font-size: 0.9rem; color: $color-dark; display: block; margin-bottom: 0.2rem; }
    p { font-size: 0.82rem; color: $color-gray; }
  }

  /* Right column stays sticky while scrolling */
  &__visual {
    display: flex;
    flex-direction: column;
    gap: $space-sm;
    position: sticky;
    top: 100px;
  }

  /* Slides right on hover */
  &__stat-card {
    display: flex;
    align-items: center;
    gap: $space-sm;
    padding: $space-md;
    background: $color-sage-light;
    border: 1px solid $color-border;
    border-radius: 16px;
    transition: transform $transition-base;

    &:hover { transform: translateX(6px); }
    &-icon { font-size: 1.5rem; }
    strong { font-family: $font-display; font-size: 1.3rem; color: $color-brand-green; display: block; }
    p { font-size: 0.82rem; color: $color-gray; }
  }

  /* Dark card for credit system info */
  &__credit-card {
    padding: $space-md;
    background: $color-dark-green;
    border-radius: 16px;
    color: $color-white;
    margin-top: 0.5rem;
  }

  &__credit-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 0.5rem;
    font-weight: 600;
    font-size: 0.9rem;
  }

  &__credit-badge {
    background: rgba($color-bright-green, 0.2);
    color: $color-bright-green;
    padding: 0.2rem 0.7rem;
    border-radius: 50px;
    font-size: 0.7rem;
    font-weight: 600;
  }

  p { font-size: 0.85rem; color: rgba($color-white, 0.6); margin-bottom: 0.75rem; }

  /* Arrow prefix on list items */
  ul {
    display: flex;
    flex-direction: column;
    gap: 0.4rem;

    li {
      font-size: 0.82rem;
      color: rgba($color-white, 0.7);
      &::before { content: '→ '; color: $color-bright-green; }
    }
  }
}
</style>