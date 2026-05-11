<template>
  <section class="hero">
    <div class="hero__bg">
      <div class="hero__grid"></div>
      <div class="hero__orb hero__orb--1"></div>
      <div class="hero__orb hero__orb--2"></div>
    </div>

    <div class="container hero__inner">
      <div class="hero__content">
        <div class="hero__tag">
          <span class="section-tag">Ein neuer Standard für AI Visibility</span>
        </div>

        <h1 class="hero__title">
          Sichtbarkeit in<br>
          KI-Systemen ist<br>
          <span class="hero__title-accent">kein Zufall.</span>
        </h1>

        <p class="hero__subtitle">
          Sie ist messbar – und steuerbar.<br>
          GEOGATOR zeigt Ihnen, wie KI-Systeme Ihr Unternehmen<br class="hero__br"> wirklich verstehen und empfehlen.
        </p>

        <div class="hero__metrics">
          <div class="hero__metric">
            <span class="hero__metric-num">GEO</span>
            <span class="hero__metric-label">Score</span>
          </div>
          <div class="hero__metric-divider"></div>
          <div class="hero__metric">
            <span class="hero__metric-num">3</span>
            <span class="hero__metric-label">Ebenen Analyse</span>
          </div>
          <div class="hero__metric-divider"></div>
          <div class="hero__metric">
            <span class="hero__metric-num">0–100</span>
            <span class="hero__metric-label">Bewertungsskala</span>
          </div>
        </div>

        <div class="hero__actions">
          <a href="#pricing" class="btn btn--primary btn--lg">
            Kostenlosen Quick Check starten
            <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M3 8h10M9 4l4 4-4 4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>
          </a>
          <a href="#report" class="btn btn--ghost btn--lg">Analyse ansehen</a>
        </div>
      </div>

      <div class="hero__visual">
        <div class="hero__score-card">
          <div class="hero__score-header">
            <span class="hero__score-label">GEO Score</span>
            <span class="hero__score-status competitive">Competitive</span>
          </div>
          <div class="hero__score-main">
            <div class="hero__score-ring">
              <svg viewBox="0 0 120 120" class="hero__ring-svg">
                <circle cx="60" cy="60" r="52" fill="none" stroke="rgba(255,255,255,0.1)" stroke-width="8"/>
                <circle cx="60" cy="60" r="52" fill="none" stroke="#7AB648" stroke-width="8"
                  stroke-dasharray="327" stroke-dashoffset="98" stroke-linecap="round"
                  transform="rotate(-90 60 60)" class="hero__ring-progress"/>
              </svg>
              <div class="hero__score-value">
                <span class="hero__score-num">64</span>
                <span class="hero__score-max">/100</span>
              </div>
            </div>
          </div>
          <div class="hero__score-breakdown">
            <div class="hero__breakdown-item" v-for="item in breakdown" :key="item.label">
              <span class="hero__breakdown-label">{{ item.label }}</span>
              <div class="hero__breakdown-bar">
                <div class="hero__breakdown-fill" :style="{ width: item.pct + '%', background: item.color }"></div>
              </div>
              <span class="hero__breakdown-val">{{ item.val }}</span>
            </div>
          </div>
        </div>

        <div class="hero__float-badge hero__float-badge--1">
          <span>🎯</span>
          <span>Klare Handlungsempfehlungen</span>
        </div>
        <div class="hero__float-badge hero__float-badge--2">
          <span>📊</span>
          <span>Wettbewerbsvergleich</span>
        </div>
      </div>
    </div>

    <div class="hero__scroll">
      <div class="hero__scroll-line"></div>
    </div>
  </section>
</template>

<script setup>
const breakdown = [
  { label: 'Topics', val: '22/30', pct: 73, color: '#7AB648' },
  { label: 'Content', val: '28/40', pct: 70, color: '#F47B20' },
  { label: 'Trust', val: '14/30', pct: 47, color: '#A8CC78' },
]
</script>

<style lang="scss" scoped>
@use '../assets/styles/variables' as *;

.hero {
  min-height: 100vh;
  background: $color-dark-green;
  display: flex;
  flex-direction: column;
  position: relative;
  overflow: hidden;

  &__bg {
    position: absolute;
    inset: 0;
    pointer-events: none;
  }

  &__grid {
    position: absolute;
    inset: 0;
    background-image:
      linear-gradient(rgba($color-bright-green, 0.06) 1px, transparent 1px),
      linear-gradient(90deg, rgba($color-bright-green, 0.06) 1px, transparent 1px);
    background-size: 48px 48px;
  }

  &__orb {
    position: absolute;
    border-radius: 50%;
    filter: blur(80px);

    &--1 {
      width: 600px;
      height: 600px;
      background: rgba($color-bright-green, 0.12);
      top: -200px;
      right: -100px;
    }

    &--2 {
      width: 400px;
      height: 400px;
      background: rgba($color-orange, 0.08);
      bottom: -100px;
      left: 10%;
    }
  }

  &__inner {
    flex: 1;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: $space-lg;
    align-items: center;
    padding-top: 120px;
    padding-bottom: $space-2xl;

    @media (max-width: $bp-lg) {
      grid-template-columns: 1fr;
      gap: $space-xl;
      padding-top: 100px;
    }
  }

  &__content {
    position: relative;
    z-index: 1;
  }

  &__tag {
    margin-bottom: $space-md;
  }

  &__title {
    font-size: clamp(1.8rem, 3.5vw, 3rem);
    color: $color-white;
    font-weight: 800;
    line-height: 1.1;
    margin-bottom: $space-md;
    letter-spacing: -0.03em;

    &-accent {
      color: $color-bright-green;
      display: block;
    }
  }

  &__subtitle {
    color: rgba($color-white, 0.7);
    font-size: 1.1rem;
    line-height: 1.7;
    margin-bottom: $space-lg;
    max-width: 520px;
  }

  &__br {
    @media (max-width: $bp-md) { display: none; }
  }

  &__metrics {
    display: flex;
    align-items: center;
    gap: $space-md;
    margin-bottom: $space-lg;
    padding: $space-sm $space-md;
    background: rgba($color-white, 0.06);
    border: 1px solid rgba($color-white, 0.1);
    border-radius: 16px;
    backdrop-filter: blur(8px);
    width: fit-content;
  }

  &__metric {
    text-align: center;
    display: flex;
    flex-direction: column;

    &-num {
      font-family: $font-display;
      font-weight: 800;
      font-size: 1.4rem;
      color: $color-bright-green;
    }

    &-label {
      font-size: 0.72rem;
      color: rgba($color-white, 0.5);
      text-transform: uppercase;
      letter-spacing: 0.05em;
    }

    &-divider {
      width: 1px;
      height: 36px;
      background: rgba($color-white, 0.15);
    }
  }

  &__actions {
    display: flex;
    gap: $space-sm;
    flex-wrap: wrap;
  }

  &__visual {
    position: relative;
    display: flex;
    justify-content: center;
    padding: 30px 50px 30px 20px;
    overflow: visible;

    @media (max-width: $bp-lg) {
      display: none;
    }
  }

  &__score-card {
    background: rgba($color-white, 0.07);
    border: 1px solid rgba($color-white, 0.12);
    border-radius: 24px;
    padding: $space-md;
    backdrop-filter: blur(16px);
    width: 300px;
    position: relative;
    z-index: 1;
    box-shadow: 0 24px 64px rgba(0, 0, 0, 0.3);
  }

  &__score-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: $space-md;
  }

  &__score-label {
    font-family: $font-mono;
    font-size: 0.75rem;
    color: rgba($color-white, 0.5);
    text-transform: uppercase;
    letter-spacing: 0.1em;
  }

  &__score-status {
    padding: 0.2rem 0.75rem;
    border-radius: 50px;
    font-size: 0.72rem;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.05em;

    &.competitive {
      background: rgba($color-bright-green, 0.2);
      color: $color-bright-green;
    }
  }

  &__score-main {
    display: flex;
    justify-content: center;
    margin-bottom: $space-md;
  }

  &__score-ring {
    position: relative;
    width: 120px;
    height: 120px;
  }

  &__ring-svg {
    width: 100%;
    height: 100%;
  }

  &__ring-progress {
    animation: ringFill 1.5s ease-out 0.5s both;
  }

  @keyframes ringFill {
    from { stroke-dashoffset: 327; }
    to { stroke-dashoffset: 98; }
  }

  &__score-value {
    position: absolute;
    inset: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
  }

  &__score-num {
    font-family: $font-display;
    font-weight: 800;
    font-size: 2.2rem;
    color: $color-white;
    line-height: 1;
  }

  &__score-max {
    font-size: 0.75rem;
    color: rgba($color-white, 0.4);
  }

  &__score-breakdown {
    display: flex;
    flex-direction: column;
    gap: 0.75rem;
  }

  &__breakdown-item {
    display: grid;
    grid-template-columns: 60px 1fr 48px;
    align-items: center;
    gap: 0.5rem;
  }

  &__breakdown-label {
    font-size: 0.78rem;
    color: rgba($color-white, 0.6);
    font-family: $font-mono;
  }

  &__breakdown-bar {
    height: 6px;
    background: rgba($color-white, 0.1);
    border-radius: 3px;
    overflow: hidden;
  }

  &__breakdown-fill {
    height: 100%;
    border-radius: 3px;
    animation: barFill 1.2s ease-out 0.8s both;
  }

  @keyframes barFill {
    from { width: 0 !important; }
  }

  &__breakdown-val {
    font-family: $font-mono;
    font-size: 0.72rem;
    color: rgba($color-white, 0.5);
    text-align: right;
  }

  &__float-badge {
    position: absolute;
    display: flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.6rem 1rem;
    background: $color-white;
    border-radius: 50px;
    box-shadow: 0 8px 24px rgba(0, 0, 0, 0.2);
    font-size: 0.8rem;
    font-weight: 500;
    color: $color-dark;
    white-space: nowrap;
    z-index: 2;

    &--1 {
      top: -30px;
      right: -10px;
      animation: floatBadge1 3s ease-in-out infinite;
    }

    &--2 {
      bottom: -30px;
      left: -10px;
      animation: floatBadge1 3s ease-in-out infinite;
      animation-delay: 1.5s;
    }
  }

  @keyframes floatBadge1 {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-8px); }
  }

  &__scroll {
    display: flex;
    justify-content: center;
    padding-bottom: $space-lg;
    position: relative;
    z-index: 1;
  }

  &__scroll-line {
    width: 1px;
    height: 60px;
    background: linear-gradient(to bottom, rgba($color-white, 0.3), transparent);
    animation: scrollPulse 2s ease-in-out infinite;
  }

  @keyframes scrollPulse {
    0%, 100% { opacity: 0.3; }
    50% { opacity: 1; }
  }
}
</style>