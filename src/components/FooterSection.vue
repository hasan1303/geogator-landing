<template>
  <footer class="footer">
    <div class="container">
      <div class="footer__top">
        <div class="footer__brand">
          <div class="footer__logo">
            <img src="/Logo_GEO_GATOR_web.png" alt="GEO GATOR" class="footer__logo-img" />
          </div>
          <p>Ein Angebot des MIM Marken Institut München.<br>Ein neuer Standard für AI Visibility.</p>
          <div class="footer__contact">
            <a href="mailto:kirn@marke41.de">kirn@marke41.de</a>
            <a href="tel:+4989729 59915">+49 89 729 59 915</a>
          </div>
        </div>

        <div class="footer__links-col" v-for="col in linkCols" :key="col.title">
          <h4>{{ col.title }}</h4>
          <ul>
            <li v-for="link in col.links" :key="link.label">
              <a :href="link.href">{{ link.label }}</a>
            </li>
          </ul>
        </div>
      </div>

      <div class="footer__bottom">
        <p>© 2025 MIM Marken Institut München GmbH · Ridlerstraße 35a, 80339 München</p>
        <div class="footer__legal">
          <a href="#">Impressum</a>
          <a href="#">Datenschutz</a>
          <a href="#">AGB</a>
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup>
const linkCols = [
  {
    title: 'Produkt',
    links: [
      { label: 'GEO Quick Check', href: '#pricing' },
      { label: 'GEO Deep Scan', href: '#pricing' },
      { label: 'GEO Pulse', href: '#pricing' },
      { label: 'Für Agenturen', href: '#agencies' },
    ],
  },
  {
    title: 'Informationen',
    links: [
      { label: 'Warum GEOGATOR', href: '#why' },
      { label: "So funktioniert's", href: '#how-it-works' },
      { label: 'Beispiel-Analyse', href: '#report' },
      { label: 'FAQ', href: '#faq' },
    ],
  },
  {
    title: 'Unternehmen',
    links: [
      { label: 'MIM Marken Institut', href: 'https://www.marken-institut-muenchen.de' },
      { label: 'Partnerprogramm', href: '#agencies' },
      { label: 'Kontakt', href: 'mailto:kirn@marke41.de' },
    ],
  },
]
</script>

<style lang="scss" scoped>
@use '../assets/styles/variables' as *;

.footer {
  background: $color-dark-green;
  color: rgba($color-white, 0.8);

  &__top {
    display: grid;
    grid-template-columns: 2fr 1fr 1fr 1fr;
    gap: $space-xl;
    padding: $space-2xl 0;
    border-bottom: 1px solid rgba($color-white, 0.12);

    @media (max-width: $bp-lg) { grid-template-columns: 1fr 1fr; }
    @media (max-width: $bp-sm) { grid-template-columns: 1fr; gap: $space-lg; padding: $space-xl 0; }
  }

  &__brand {
    p {
      font-size: 0.875rem;
      line-height: 1.7;
      margin-bottom: $space-sm;
      max-width: 280px;
      color: rgba($color-white, 0.65);
    }
  }

  &__logo {
    margin-bottom: $space-sm;
  }

  &__logo-img {
    height: 70px;
    width: auto;
    object-fit: contain;
    filter: drop-shadow(0 2px 8px rgba(0,0,0,0.3));
    @media (max-width: $bp-sm) { height: 55px; }
  }

  &__contact {
    display: flex;
    flex-direction: column;
    gap: 0.4rem;

    a {
      font-size: 0.85rem;
      color: rgba($color-white, 0.5);
      transition: color $transition-fast;
      &:hover { color: $color-white; }
    }
  }

  &__links-col {
    h4 {
      font-family: $font-display;
      font-size: 0.8rem;
      font-weight: 700;
      color: rgba($color-white, 0.4);
      text-transform: uppercase;
      letter-spacing: 0.1em;
      margin-bottom: $space-sm;
    }

    ul { display: flex; flex-direction: column; gap: 0.7rem; }

    a {
      font-size: 0.875rem;
      color: rgba($color-white, 0.65);
      transition: color $transition-fast;
      &:hover { color: $color-white; }
    }
  }

  &__bottom {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: $space-md 0;
    gap: $space-md;
    flex-wrap: wrap;

    @media (max-width: $bp-sm) { flex-direction: column; text-align: center; }

    p { font-size: 0.78rem; color: rgba($color-white, 0.4); }
  }

  &__legal {
    display: flex;
    gap: $space-md;

    a {
      font-size: 0.78rem;
      color: rgba($color-white, 0.4);
      transition: color $transition-fast;
      &:hover { color: $color-white; }
    }
  }
}
</style>