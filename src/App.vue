<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const name = 'Luca Claus'
const course = 'B.Sc. Informatik — Master ab Sep 2026'
const university = 'Hochschule Karlsruhe (HKA)'
const mail = 'kontakt@lucaclaus.de'
const linkedin = 'https://www.linkedin.com/in/luca-claus-0a2b23297/'
const github = 'https://github.com/Luckyly26'

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

const timeline = [
  {
    period: 'Sep 2022 – Aug 2026',
    title: 'BA-Studium Informatik',
    type: 'Studium',
    startMonth: 0,
    endMonth: 48,
    organization: university,
    description: 'Bachelorstudium der Informatik an der Hochschule Karlsruhe.',
  },
  {
    period: 'März – Aug 2024',
    title: 'Praxissemester',
    type: 'Berufserfahrung',
    startMonth: 18,
    endMonth: 24,
    organization: 'abas GmbH',
    description: 'Praktische Erfahrungen und Mitarbeit an Projekten bei abas.',
  },
  {
    period: 'Okt 2024 – Feb 2026',
    title: 'Werkstudent',
    type: 'Berufserfahrung',
    startMonth: 25,
    endMonth: 42,
    organization: 'abas GmbH',
    description: 'Werkstudentische Tätigkeit neben dem Informatikstudium.',
  },
  {
    period: 'März – Juli 2026',
    title: 'BA-Thesis',
    type: 'Abschlussarbeit',
    startMonth: 42,
    endMonth: 47,
    organization: 'abas GmbH',
    description: 'Bachelorarbeit zur Sicherheitskonzeption für Cloud-ERP-Customizing.',
  },
  {
    period: 'Seit Sep 2026',
    title: 'MA-Studium Informatik',
    type: 'Studium',
    startMonth: 48,
    endMonth: 49,
    organization: university,
    description: 'Masterstudium der Informatik an der Hochschule Karlsruhe.',
  },
]

const selectedTimelineItem = ref(timeline[0])
const timelineDuration = 49

function selectedTimelineStyle() {
  return {
    '--timeline-start': `${(selectedTimelineItem.value.startMonth / timelineDuration) * 100}%`,
    '--timeline-width': `${((selectedTimelineItem.value.endMonth - selectedTimelineItem.value.startMonth) / timelineDuration) * 100}%`,
  }
}

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
    title: 'Portfolio-Website',
    desc: 'Persönliche Portfolio-Website mit Informationen zu meinem Werdegang, meinen Projekten und meinen Fähigkeiten.',
    link: '#',
    github: '#',
    tech: ['Vue.js', 'Vite', 'GitHub Pages']
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

const volunteering = [
  {
    period: 'Seit Oktober 2025',
    role: '1. Kassenwart',
    organization: 'Förderverein der Fachschaft IWI e.V.',
  },
  {
    period: 'Seit Oktober 2025',
    role: 'Teamlead Sponsoring',
    organization: 'Förderverein der Fachschaft IWI e.V.',
  },
  {
    period: 'Oktober 2024 – September 2025',
    role: 'Fachbereich Sponsoring',
    organization: 'Fachschaft IWI | Hochschule Karlsruhe',
    description: 'Verantwortlich für die Kommunikation mit unseren Sponsoringpartnern.',
  },
  {
    period: 'Seit Januar 2018',
    role: 'Betreuer Kinderfreizeit',
    organization: 'Prot. Kirchengemeinde Waldsee-Otterstadt',
    description: 'Betreuung der Kinder während der jährlichen Kinderfreizeit sowie Einarbeitung neuer Betreuerinnen und Betreuer.',
  },
]
</script>

<template>
  <div>
    <nav class="nav">
      <div class="nav__links">
        <a href="#about">Über</a>
        <a href="#timeline">Werdegang</a>
        <a href="#ehrenamt">Ehrenamt</a>
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
        </div>
      </section>

      <section id="about" class="section-grid">
        <article class="info-card" style="grid-column: span 3">
          <h2>Über mich</h2>
          <p>Ich studiere Informatik und arbeite an Projekten in den Bereichen Webentwicklung, Algorithmen und Datensysteme. Ich suche praktische Erfahrungen, Praktika und spannende Projektzusammenarbeiten.</p>
        </article>
      </section>

      <section id="timeline" class="timeline-section">
        <div class="timeline-heading">
          <p class="eyebrow">Werdegang</p>
          <h2>Mein Weg durch Studium und Beruf</h2>
        </div>

        <div class="timeline-overview" :style="selectedTimelineStyle()" aria-label="Position des ausgewählten Zeitraums auf der Gesamtzeitleiste">
          <span class="timeline-overview__active" aria-hidden="true"></span>
        </div>

        <div class="timeline" aria-label="Zeitstrahl des Werdegangs">
          <button
            v-for="item in timeline"
            :key="item.title"
            class="timeline-item"
            :class="{ 'timeline-item--active': selectedTimelineItem.title === item.title }"
            type="button"
            :aria-pressed="selectedTimelineItem.title === item.title"
            @click="selectedTimelineItem = item"
          >
            <span class="timeline-dot" aria-hidden="true"></span>
            <span class="timeline-period">{{ item.period }}</span>
            <strong>{{ item.title }}</strong>
            <span class="timeline-type">{{ item.type }}</span>
          </button>
        </div>

        <article class="timeline-detail" aria-live="polite">
          <div>
            <p class="eyebrow">Ausgewählt</p>
            <h3>{{ selectedTimelineItem.title }}</h3>
          </div>
          <div>
            <p class="timeline-detail__period">{{ selectedTimelineItem.period }}</p>
            <p>{{ selectedTimelineItem.description }}</p>
            <a v-if="selectedTimelineItem.organization === 'abas GmbH'" href="https://www.abas-erp.com" target="_blank" rel="noopener">{{ selectedTimelineItem.organization }}</a>
            <p v-else class="timeline-detail__organization">{{ selectedTimelineItem.organization }}</p>
          </div>
          <a v-if="['Berufserfahrung', 'Abschlussarbeit'].includes(selectedTimelineItem.type)" class="timeline-detail__more" href="#wirtschaft">
            <svg viewBox="0 0 24 24" aria-hidden="true"><path d="m6 9 6 6 6-6" /></svg>
            <span>Siehe mehr</span>
          </a>
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

      <section id="ehrenamt" class="section-grid" style="margin-top:18px">
        <article style="grid-column: span 3">
          <h2>Ehrenamt</h2>
        </article>

        <div class="ehrenamt-track" aria-label="Ehrenamtliche Tätigkeiten">
          <article v-for="item in volunteering" :key="`${item.role}-${item.period}`" class="info-card ehrenamt-card">
            <h3>{{ item.role }}</h3>
            <p>{{ item.organization }}</p>
            <p>{{ item.period }}</p>
            <p v-if="item.description">{{ item.description }}</p>
          </article>
        </div>
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
