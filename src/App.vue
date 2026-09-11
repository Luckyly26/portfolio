<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const name = 'Luca Claus'
const course = 'B.Sc. Informatik — Master ab Sep 2026'
const university = 'Hochschule Karlsruhe (HKA)'
const mail = 'kontakt@lucaclaus.de'
const linkedin = 'https://www.linkedin.com/in/dein-profil/'
const github = 'https://github.com/dein-benutzername'

const highlights = [
  { title: 'Schnelle Entwicklung', text: 'Moderne Toolchain: Vue 3 + Vite für produktive Iteration.' },
  { title: 'Einfache Veröffentlichung', text: 'Deploy über GitHub Pages mit einem Build-Script.' },
  { title: 'Retro-Look', text: 'Pixeliger Stil für ein auffälliges Portfolio.' },
]

const steps = [
  'Repository auf GitHub anlegen oder verbinden.',
  'npm install und lokal testen (npm run dev).',
  'Build und deployen (npm run build && npm run deploy).',
]

const education = [
  { year: 'B.Sc.', title: 'Bachelor of Science (Informatik)', org: university },
  { year: 'ab Sep 2026', title: 'Masterstudium Informatik', org: university },
]

const skills = ['Java', 'Python', 'C++', 'JavaScript', 'Vue.js', 'Datenbanken', 'Git']

const projects = ref([
  {
    title: 'Bachelorarbeit: Sicherheitskonzeption für Cloud-ERP-Customizing',
    desc: 'Sicherheitskonzeption und Risikoanalyse (STRIDE/OWASP) für Cloud-basiertes ERP-Customizing bei Forterro/abas.',
    link: 'https://www.abas-erp.com',
    github: '#',
    tech: ['STRIDE','OWASP','Cloud Security']
  },
  {
    title: 'Seminararbeit: DORA-Metriken',
    desc: 'Erhebung, Analyse und Visualisierung von DORA-Metriken; Implementierung von Auswertungs-Skripten und Reporting.',
    link: '#',
    github: '#',
    tech: ['DORA','Data Analysis','Reporting']
  },
  {
    title: 'Algorithmus-Visualisierung',
    desc: 'Interaktive Visualisierung von Such- und Sortieralgorithmen (Web).',
    link: '#',
    github: '#',
    tech: ['JavaScript','Canvas']
  }
])

const projectsBand = ref(null)

function onWheel(e) {
  const el = projectsBand.value
  if (!el) return
  if (Math.abs(e.deltaY) > Math.abs(e.deltaX)) {
    e.preventDefault()
    el.scrollLeft += e.deltaY
  }
}

onMounted(() => {
  if (projectsBand.value) projectsBand.value.addEventListener('wheel', onWheel, { passive: false })
})

onUnmounted(() => {
  if (projectsBand.value) projectsBand.value.removeEventListener('wheel', onWheel)
})

const workExperience = [
  { period: 'März 2024 – August 2024', role: 'Praktikant (Praxissemester)', company: 'abas GmbH', site: 'https://www.abas-erp.com' },
  { period: 'Oktober 2024 – Februar 2026', role: 'Werkstudent', company: 'abas GmbH', site: 'https://www.abas-erp.com' },
  { period: 'März 2026 – Juli 2026', role: 'Thesis', company: 'abas GmbH', site: 'https://www.abas-erp.com' },
]
</script>

<template>
  <div>
    <nav class="nav">
      <div class="nav__links">
        <a href="#about">Über</a>
        <a href="#highlights">Features</a>
        <a href="#deploy">Deployment</a>
        <a href="#contact">Kontakt</a>
      </div>
    </nav>

    <main class="page-shell">
      <section class="hero">
        <div class="hero__copy">
          <p class="eyebrow">Portfolio</p>
          <h1>{{ name }}</h1>
          <p class="lead">{{ course }} — {{ university }}</p>
          <p class="lead">Ich bin Informatikstudent mit Interesse an Algorithmen, Webentwicklung und Systemprogrammierung. Auf dieser Seite findest du Projekte, Fähigkeiten und Kontaktmöglichkeiten.</p>
          <div class="hero__actions">
            <a class="button button--primary" href="#projects">Projekte</a>
            <a class="button button--ghost" href="#contact">Kontakt</a>
          </div>
        </div>

        <div class="hero__panel">
          <div class="panel-card panel-card--accent">
            <span>Rolle</span>
            <strong>{{ course }}</strong>
          </div>
          <div class="panel-card">
            <span>Uni</span>
            <strong>{{ university }}</strong>
          </div>
          <div class="panel-card">
            <span>Resume</span>
            <strong><a href="#">CV herunterladen</a></strong>
          </div>
        </div>
      </section>

      <section id="about" class="section-grid">
        <article class="info-card" style="grid-column: span 3">
          <h2>Über mich</h2>
          <p>Ich studiere Informatik und arbeite an Projekten in den Bereichen Webentwicklung, Algorithmen und Datensysteme. Ich suche praktische Erfahrungen, Praktika und spannende Projektzusammenarbeiten.</p>
        </article>
      </section>

      <section id="projects" class="section-grid">
        <article style="grid-column: span 3">
          <h2>Projekte</h2>
        </article>

        <article v-for="p in projects" :key="p.title" class="info-card">
          <h3>{{ p.title }}</h3>
          <p>{{ p.desc }}</p>
          <p>
            <a :href="p.github">GitHub</a> · <a :href="p.link">Live</a>
          </p>
        </article>
      </section>

      <section id="skills" class="section-grid" style="margin-top:18px">
        <article class="info-card" style="grid-column: span 2">
          <h2>Fähigkeiten</h2>
          <ul>
            <li v-for="s in skills" :key="s">{{ s }}</li>
          </ul>
        </article>

        <aside class="panel-card" style="align-self:start">
          <h3>Ausbildung</h3>
          <ul>
            <li v-for="e in education" :key="e.title">{{ e.year }} — {{ e.title }} ({{ e.org }})</li>
          </ul>
        </aside>
      </section>

      <section id="wirtschaft" class="section-grid" style="margin-top:18px">
        <article style="grid-column: span 3">
          <h2>Berufserfahrung</h2>
        </article>

        <article v-for="w in workExperience" :key="w.period" class="info-card">
          <h3>{{ w.role }} — {{ w.company }}</h3>
          <p>{{ w.period }}</p>
          <p><a :href="w.site" target="_blank" rel="noopener">{{ w.site }}</a></p>
        </article>
      </section>

      <footer id="contact" class="site-footer">
        <div class="footer-links">
          <a class="footer-link" :href="`mailto:${mail}`" :aria-label="`E-Mail an ${mail}`" title="E-Mail">
            <svg viewBox="0 0 24 24" aria-hidden="true"><path d="M3 5h18v14H3z" /><path d="m3 6 9 7 9-7" /></svg>
          </a>
          <a class="footer-link" :href="linkedin" target="_blank" rel="noopener noreferrer" aria-label="LinkedIn-Profil" title="LinkedIn">
            <svg viewBox="0 0 24 24" aria-hidden="true"><path d="M6 8v11" /><path d="M6 5.5v.01" /><path d="M11 19v-6a3 3 0 0 1 6 0v6" /><path d="M11 11v8" /><path d="M17 19v-6" /></svg>
          </a>
          <a class="footer-link" :href="github" target="_blank" rel="noopener noreferrer" aria-label="GitHub-Profil" title="GitHub">
            <svg viewBox="0 0 24 24" aria-hidden="true"><path d="M9 19c-4 1.5-4-2-5.5-2.5M15 19v-3.5c0-1 .1-1.4-.5-2 2.5-.3 5-1.2 5-5.5a4.3 4.3 0 0 0-1.2-3c.1-.3.5-1.5-.1-3 0 0-1-.3-3.2 1.2a11 11 0 0 0-5.8 0C7 2.7 6 3 6 3c-.6 1.5-.2 2.7-.1 3A4.3 4.3 0 0 0 4.7 8.5c0 4.3 2.5 5.2 5 5.5-.6.5-.6 1.2-.5 2V19" /></svg>
          </a>
        </div>
        <p>© {{ new Date().getFullYear() }} — Portfolio</p>
      </footer>
    </main>
  </div>
</template>
