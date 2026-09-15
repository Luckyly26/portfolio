<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const name = 'Luca Claus'
const course = 'B.Sc. Informatik — Master ab Sep 2026'
const university = 'Hochschule Karlsruhe (HKA)'
const employer = {
  name: 'abas',
  legalName: 'Forterro Deutschland abas GmbH',
  website: 'https://www.abas-erp.com',
}
const mail = 'kontakt@lucaclaus.de'
const linkedin = 'https://www.linkedin.com/in/luca-claus-0a2b23297/'
const github = 'https://github.com/Luckyly26'
const fachschaft = 'https://iwi-hka.de/about/'

const steps = [
  'Repository auf GitHub anlegen oder verbinden.',
  'npm install und lokal testen (npm run dev).',
  'Build und deployen (npm run build && npm run deploy).',
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
    organization: employer.name,
    description: 'Praktische Erfahrungen und Mitarbeit an Projekten bei abas.',
  },
  {
    period: 'Okt 2024 – Feb 2026',
    title: 'Werkstudent',
    type: 'Berufserfahrung',
    startMonth: 25,
    endMonth: 42,
    organization: employer.name,
    description: 'Werkstudentische Tätigkeit neben dem Informatikstudium.',
  },
  {
    period: 'März – Juli 2026',
    title: 'BA-Thesis',
    type: 'Abschlussarbeit',
    startMonth: 42,
    endMonth: 47,
    organization: employer.name,
    description: 'Bachelorarbeit zur Sicherheitskonzeption für Cloud-ERP-Customizing.',
  },
  {
    period: 'Seit Sep 2026',
    title: 'MA-Studium Informatik',
    type: 'Studium',
    startMonth: 48,
    endMonth: 48,
    organization: university,
    description: 'Masterstudium der Informatik an der Hochschule Karlsruhe.',
  },
]

const selectedTimelineItem = ref(timeline[0])
const timelineDuration = 48
const timelineMarkers = [
  { label: '2023', month: 4 },
  { label: '2024', month: 16 },
  { label: '2025', month: 28 },
  { label: '2026', month: 40 },
]

function timelineMarkerStyle(month) {
  return { left: `${(month / timelineDuration) * 100}%` }
}

function selectedTimelineStyle() {
  return {
    '--timeline-start': `${(selectedTimelineItem.value.startMonth / timelineDuration) * 100}%`,
    '--timeline-width': `${((selectedTimelineItem.value.endMonth - selectedTimelineItem.value.startMonth) / timelineDuration) * 100}%`,
  }
}

const skillGroups = [
  {
    title: 'Tech-Skills',
    label: 'Werkzeuge & Sprachen',
    description: 'Technologien, mit denen ich entwickle und arbeite.',
    items: ['Java', 'Python', 'C++', 'JavaScript', 'Vue.js', 'Git', 'SQL', 'Linux', 'Docker', 'Cucumber', 'Unix'],
  },
  {
    title: 'Know-how',
    label: 'Methoden & Systeme',
    description: 'Fachliche Schwerpunkte aus Studium und Berufserfahrung.',
    items: ['Datenbanken', 'Webentwicklung', 'Systemprogrammierung', 'Cloud Security', 'ERP-Customizing', 'Softwarearchitektur', 'Agile Methoden', 'DevOps', 'Penetration Testing', 'DORA-Metriken', 'STRIDE', 'OWASP Top 10'],
  },
  {
    title: 'Softskills',
    label: 'Zusammenarbeit',
    description: 'Stärken, die meine Arbeit im Team und an Projekten prägen.',
    items: ['Teamarbeit', 'Kommunikation', 'Analytisches Denken', 'Projektkoordination', 'Ehrenamtliches Engagement', 'Selbstorganisation', 'Problemlösungskompetenz'],
  },
]

const selectedSkillGroup = ref(skillGroups[0])

const projects = ref([
  {
    id: 'bachelorarbeit',
    title: 'Bachelorarbeit: Sicherheitskonzeption für Cloud-ERP-Customizing',
    desc: 'Sicherheitskonzeption und Risikoanalyse (STRIDE/OWASP top 10) für Cloud-basiertes ERP-Customizing bei abas erp.',
    tech: ['STRIDE','OWASP top 10','Cloud Security', 'ERP-Customizing', 'Risk Analysis', 'Software Architecture']
  },
  {
    title: 'Aufbau von DORA-Metriken bei abas',
    desc: 'Im Rahmen meiner Tätigkeit bei abas habe ich DORA-Metriken für den betrachteten Entwicklungsbereich erstmals aufgesetzt und definiert. Die daraus entstandenen Erkenntnisse bildeten die Grundlage für meine Seminararbeit.',
    tech: ['DORA-Metriken', 'DevOps', 'Data Analysis', 'Definition von KPIs']
  },
  {
    title: 'Seminararbeit: DORA-Metriken',
    desc: 'Wissenschaftliche Ausarbeitung der DORA-Metriken (DevOps Research and Assessment) als Grundlage für die Analyse und Verbesserung von DevOps-Praktiken.',
    tech: ['DORA','Data Analysis','Reporting']
  },
  {
    id: 'ethical-hacking-pentest',
    title: 'Pentest: Ethical Hacking',
    desc: 'Durchführung eines umfassenden Pentests im Rahmen der Vorlesung Ethical Hacking an der Hochschule Karlsruhe. Analyse von Sicherheitslücken und Erstellung eines Abschlussberichts.', 
    tech: ['Penetration Testing', 'Ethical Hacking', 'Web Security', 'Security Analysis'],
    certificates: [
      { label: 'Zertifikat (DE)', href: './assets/Zertifikate/20260222_HKA_IWI_Zertifikat_Ethical_Hacking_Luca%20Claus_de.pdf' },
      { label: 'Certificate (EN)', href: './assets/Zertifikate/20260222_HKA_IWI_Zertifikat_Ethical_Hacking_Loca_Claus_en.pdf' },
    ]
  },
  {
    title: 'Portfolio-Website',
    desc: 'Persönliche Portfolio-Website mit Informationen zu meinem Werdegang, meinen Projekten und meinen Fähigkeiten.',
    github: 'https://github.com/Luckyly26/portfolio',
    tech: ['Vue.js', 'Vite', 'GitHub Pages']
  }
])

const projectsBand = ref(null)
const ehrenamtBand = ref(null)

function onWheel(e) {
  const el = e.currentTarget
  if (Math.abs(e.deltaY) > Math.abs(e.deltaX)) {
    e.preventDefault()
    el.scrollLeft += e.deltaY
  }
}

onMounted(() => {
  if (projectsBand.value) projectsBand.value.addEventListener('wheel', onWheel, { passive: false })
  if (ehrenamtBand.value) ehrenamtBand.value.addEventListener('wheel', onWheel, { passive: false })
})

onUnmounted(() => {
  if (projectsBand.value) projectsBand.value.removeEventListener('wheel', onWheel)
  if (ehrenamtBand.value) ehrenamtBand.value.removeEventListener('wheel', onWheel)
})

const workExperience = [
  { 
    period: 'März 2024 – August 2024', 
    role: 'Praktikant (Praxissemester)', 
    desc: 'Praktikum in der Anwendungsentwicklung eines ERP-Systems. Erstellung eines Testauswertungs-Tools und Mitarbeit in der Anwendungsentwicklung.', 
    company: employer.name, site: employer.website 
  },
  { 
    period: 'Oktober 2024 – Februar 2026', 
    role: 'Werkstudent', 
    desc: 'Arbeit in der Anwendungsentwicklung und Wartung den ERP-Systems. Testmigration und Übersetzung in Cucumber.', 
    company: employer.name, 
    site: employer.website 
  },
  { 
    period: 'März 2026 – Juli 2026', 
    role: 'Bachelorthesis', 
    desc: 'Sicherheitskonzeption für Cloud-basiertes ERP-Customizing. Risikoanalyse (STRIDE/OWASP top 10) und Erstellung eines Sicherheitskonzepts.', 
    company: employer.name, 
    site: employer.website 
  },
]

const volunteering = [
    {
    period: 'Seit September 2026',
    role: 'Mitglied im Fakultätsrat der Fakultät IWI',
    organization: 'Hochschule Karlsruhe',
    description: 'Gewähltes Mitglied im Fakultätsrat der Fakultät IWI. Verantwortlich für die Vertretung und Repräsentation der Studierenden in Fakultätsausschüssen.',
    site: 'https://asta-hka.de/hs-politik/',
  },
  {
    period: 'Seit Oktober 2025',
    role: '1. Kassenwart',
    organization: 'Förderverein der Fachschaft IWI e.V.',
    site: fachschaft,
  },
  {
    period: 'Seit Oktober 2025',
    role: 'Teamlead Sponsoring',
    organization: 'Fachschaft IWI | Hochschule Karlsruhe',
    description: 'Verantwortung und Koordination des Sponsoringteams, sowie der Kooperationsevents mit den Sponsoringpartnern.',
    site: fachschaft,
  },
  {
    period: 'Oktober 2024 – September 2025',
    role: 'Fachbereich Sponsoring',
    organization: 'Fachschaft IWI | Hochschule Karlsruhe',
    description: 'Verantwortlich für die Kommunikation und Kooperation mit den Sponsoringpartnern.',
      site: fachschaft,
  },
  {
    period: 'Seit Januar 2018',
    role: 'Betreuer Kinderfreizeit',
    organization: 'Prot. Kirchengemeinde Waldsee-Otterstadt',
    description: 'Programmplanung und Betreuung der Kinder während der jährlichen Kinderfreizeit sowie Einarbeitung neuer Betreuerinnen und Betreuer.',
  },
]
</script>

<template>
  <div>

    <main class="page-shell">
      <section class="hero">
        <div class="hero__copy">
          <p class="eyebrow">Portfolio</p>
          <h1>{{ name }}</h1>
          <p class="lead">{{ course }} — {{ university }}</p>
          <p class="lead">Ich bin Informatikstudent mit Interesse an Security-Architektur, Webentwicklung und Systemprogrammierung. Auf dieser Seite sind meine Projekte, Fähigkeiten und bereits gesammelte Erfahrungen zusammengefasst.</p>
          <div class="hero__actions">
            <a class="button button--ghost" href="#about">Über</a>
            <a class="button button--ghost" href="#timeline">Werdegang</a>
            <a class="button button--project" href="#projects">Projekte</a>
            <a class="button button--ghost" href="#skills">Fähigkeiten</a>
            <a class="button button--wirtschaft" href="#wirtschaft">Berufserfahrung</a>
            <a class="button button--ehrenamt" href="#ehrenamt">Ehrenamt</a>
            <a class="button button--primary" href="#contact">Kontakt</a>
          </div>
        </div>

        <div class="hero__panel">
          <div class="panel-card panel-card--accent">
            <span>Hauptinteressen</span>
            <strong>Security · DevOps · Webentwicklung</strong>
          </div>
          <div class="panel-card">
            <span>Berufserfahrung</span>
            <strong>Softwareentwicklung bei {{ employer.name }}</strong>
          </div>
          <div class="panel-card">
            <span>Sprachen</span>
            <strong class="language-list">
              <span class="language-item">
                <svg class="language-flag" viewBox="0 0 24 16" role="img" aria-label="Deutschlandflagge">
                  <rect width="24" height="16" fill="#ffce00" />
                  <rect width="24" height="10.67" fill="#dd0000" />
                  <rect width="24" height="5.33" fill="#111" />
                </svg>
                <span aria-hidden="true">-</span>
                <span>Muttersprache</span>
              </span>
              <span class="language-item">
                <svg class="language-flag" viewBox="0 0 24 16" role="img" aria-label="Flagge des Vereinigten Königreichs">
                  <rect width="24" height="16" fill="#012169" />
                  <path d="M0 0 24 16M24 0 0 16" stroke="#fff" stroke-width="4" />
                  <path d="M0 0 24 16M24 0 0 16" stroke="#c8102e" stroke-width="1.7" />
                  <path d="M12 0v16M0 8h24" stroke="#fff" stroke-width="5" />
                  <path d="M12 0v16M0 8h24" stroke="#c8102e" stroke-width="2.8" />
                </svg>
                <span aria-hidden="true">-</span>
                <span>Geschäftssicher</span>
              </span>
            </strong>
          </div>
        </div>
      </section>

      <section id="about" class="section-grid">
        <article class="info-card" style="grid-column: span 3">
          <h2>Über mich</h2>
          <p>Ich bin Luca, Informatikstudent an der Hochschule Karlsruhe. Nach meinem Bachelorstudium studiere ich seit September 2026 im Master weiter und vertiefe dabei meine Interessen an Webentwicklung, Softwarearchitektur und sicheren Softwaresystemen.</p>
          <p>Ergänzend zu meinem Studium vertiefe ich stetig meine Fähigkeiten im wirtschaftlichen Umfeld. Durch mein Praxissemester mit darauf folgenden Werkstudententätigkeit und Bachelorarbeit bei {{ employer.name }} konnte ich bereits viele zeitaktuelle Erfahrungen und Fähigkeiten erwerben.</p>
          <p>Davon abgesehen engagiere ich mich ehrenamtlich in verschiedenen Positionen und arbeite gerne mit Menschen an gemeinsamen Projekten.</p>

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
        <div class="timeline-years" aria-hidden="true">
          <span
            v-for="marker in timelineMarkers"
            :key="marker.label"
            class="timeline-year"
            :style="timelineMarkerStyle(marker.month)"
          >
            {{ marker.label }}
          </span>
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
            <a v-if="selectedTimelineItem.organization === employer.name" :href="employer.website" target="_blank" rel="noopener">{{ selectedTimelineItem.organization }}</a>
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

        <div ref="projectsBand" class="projects-track" aria-label="Projekte">
          <article v-for="p in projects" :key="p.title" :id="p.id" class="project-card">
            <h3>{{ p.title }}</h3>
            <p>{{ p.desc }}</p>
            <p v-if="p.github || p.link">
              >
              <a v-if="p.github" :href="p.github" target="_blank" rel="noopener noreferrer">GitHub</a>
              <span v-if="p.github && p.link"> · </span>
              <a v-if="p.link" :href="p.link" target="_blank" rel="noopener noreferrer">Live</a>
            </p>
            <p v-if="p.certificates">
              <a
                v-for="(certificate, index) in p.certificates"
                :key="certificate.href"
                :href="certificate.href"
                target="_blank"
                rel="noopener noreferrer"
              >
                <span v-if="index"> · </span>{{ certificate.label }}
              </a>
            </p>
          </article>
        </div>
      </section>

      <section id="skills" class="section-grid" style="margin-top:18px">
        <article class="skills-content" style="grid-column: 1 / -1">
          <h2>Fähigkeiten</h2>
          <div class="skills-selector" aria-label="Skill-Kategorien">
            <button
              v-for="group in skillGroups"
              :key="group.title"
              class="skills-selector__item"
              :class="{ 'skills-selector__item--active': selectedSkillGroup.title === group.title }"
              type="button"
              :aria-pressed="selectedSkillGroup.title === group.title"
              @click="selectedSkillGroup = group"
            >
              <span class="skills-selector__marker" aria-hidden="true"></span>
              <span>
                <strong>{{ group.title }}</strong>
                <small>{{ group.label }}</small>
              </span>
            </button>
          </div>

          <div class="skills-detail" aria-live="polite">
            <div>
              <p class="eyebrow">Ausgewählt</p>
              <h3>{{ selectedSkillGroup.title }}</h3>
              <p>{{ selectedSkillGroup.description }}</p>
            </div>
            <ul class="skills-detail__list">
              <li v-for="skill in selectedSkillGroup.items" :key="skill">{{ skill }}</li>
            </ul>
          </div>
        </article>
      </section>

      <section id="wirtschaft" class="section-grid" style="margin-top:18px">
        <article style="grid-column: span 3">
          <h2>Berufserfahrung</h2>
        </article>

        <article v-for="w in workExperience" :key="w.period" class="info-card">
          <h3 class="work-role">{{ w.role }}</h3>
          <p class="work-company"> > {{ w.company }}</p>
          <p>{{ w.period }}</p>
          <p>{{ w.desc }}</p>
          <p v-if="w.role === 'Thesis'"><a href="#bachelorarbeit">Zur Bachelorarbeit</a></p>
          <p v-else><a :href="w.site" target="_blank" rel="noopener">{{ w.site }}</a></p>
        </article>
      </section>

      <section id="ehrenamt" class="section-grid" style="margin-top:18px">
        <article style="grid-column: span 3">
          <h2>Ehrenamt</h2>
        </article>

        <div ref="ehrenamtBand" class="ehrenamt-track" aria-label="Ehrenamtliche Tätigkeiten">
          <article v-for="item in volunteering" :key="`${item.role}-${item.period}`" class="info-card ehrenamt-card">
            <h3 class="work-role">{{ item.role }}</h3>
            <p class="work-company"> > {{ item.organization }}</p>
            <p>{{ item.period }}</p>
            <p v-if="item.description">{{ item.description }}</p>
            <p v-if="item.site"><a :href="item.site" target="_blank" rel="noopener">{{ item.site }}</a></p>
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
