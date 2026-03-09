<template>
  <div id="app-root">
    <nav class="navbar" :class="{ scrolled: isScrolled }">
      <div class="nav-inner">
        <a href="#hero" class="nav-logo" @click.prevent="scrollTo('hero')">EF</a>
        <ul class="nav-links">
          <li v-for="link in navLinks" :key="link.id">
            <a :href="`#${link.id}`" @click.prevent="scrollTo(link.id)" :class="{ active: activeSection === link.id }">
              {{ link.label }}
            </a>
          </li>
        </ul>
        <button class="burger" @click="menuOpen = !menuOpen" :aria-expanded="menuOpen">
          <span></span><span></span><span></span>
        </button>
      </div>
      <div class="mobile-menu" :class="{ open: menuOpen }">
        <a v-for="link in navLinks" :key="link.id" :href="`#${link.id}`"
           @click.prevent="scrollTo(link.id); menuOpen = false">{{ link.label }}</a>
      </div>
    </nav>

    <section id="hero">
      <div class="hero-bg">
        <div class="hero-orb orb1"></div>
        <div class="hero-orb orb2"></div>
        <div class="grid-overlay"></div>
      </div>
      <div class="hero-content">
        <h1 class="hero-name reveal">Eoten <span class="accent">FRERE</span></h1>
        <h2 class="hero-title reveal">Développeur Web <span class="sep">|</span> Étudiant BUT Informatique 3ème année</h2>
        <p class="hero-tagline reveal">Passionné par le développement web, la conception d'applications robustes et la modernisation d'architectures existantes.</p>
        <div class="hero-cta reveal">
          <a href="#projects" class="btn-primary" @click.prevent="scrollTo('projects')">Voir mes projets</a>
          <a href="#contact" class="btn-outline" @click.prevent="scrollTo('contact')">Me contacter</a>
        </div>
        <div class="hero-scroll-hint reveal" @click="scrollTo('about')">
          <span>Scroll</span>
          <div class="scroll-line"></div>
        </div>
      </div>
    </section>

    <section id="about">
      <div class="container">
        <div class="section-label reveal">01 — À propos</div>
        <h2 class="section-title reveal">Qui suis-je&nbsp;?</h2>
        <div class="about-grid">
          <div class="about-text reveal">
            <p>Étudiant en <strong>3ème année de BUT Informatique</strong>, je me passionne pour le développement web sous toutes ses formes — de la conception d'interfaces propres à l'architecture de systèmes back-end robustes.</p>
            <p>J'aime particulièrement les projets qui demandent de <strong>repartir de zéro</strong> ou de <strong>moderniser l'existant</strong> : revoir une architecture, migrer une base de données, conteneuriser un environnement ou refondre une UI. Ce qui me motive, c'est de livrer quelque chose qui tient dans le temps.</p>
            <p>En dehors du code, je suis quelqu'un de <strong>curieux et méthodique</strong>, toujours à chercher la meilleure façon de faire les choses plutôt que la plus rapide.</p>
            <div class="about-tags">
              <span class="tag" v-for="t in dailyTech" :key="t">{{ t }}</span>
            </div>
          </div>
          <div class="about-card reveal">
            <div class="card-item">
              <div class="card-icon">📍</div>
              <div>
                <div class="card-label">Localisation</div>
                <div class="card-value">France</div>
              </div>
            </div>
            <div class="card-item">
              <div class="card-icon">🎓</div>
              <div>
                <div class="card-label">Formation</div>
                <div class="card-value">BUT Informatique — 3ème année</div>
              </div>
            </div>
            <div class="card-item">
              <div class="card-icon">🚀</div>
              <div>
                <div class="card-label">Projet en cours</div>
                <div class="card-value">Stage Développeur Web — Agrilearn</div>
              </div>
            </div>
            <div class="card-item">
              <div class="card-icon">💡</div>
              <div>
                <div class="card-label">Centres d'intérêt</div>
                <div class="card-value">Architecture logicielle, DevOps, UI/UX</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>


    <section id="experience">
      <div class="container">
        <div class="section-label reveal">02 — Expérience</div>
        <h2 class="section-title reveal">Projet en cours</h2>
        <div class="exp-grid">
          <div class="exp-header reveal">
            <div class="exp-company">
              <div class="exp-logo">AG</div>
              <div>
                <div class="exp-name">Agrilearn</div>
                <div class="exp-role">Développeur Web — Stage</div>
              </div>
            </div>
            <a href="https://git.widee.dev/Agrilearn" target="_blank" rel="noopener" class="exp-repo-btn">Voir le repo ↗</a>
          </div>
          <div class="exp-context reveal">
            <p>L'entreprise disposait d'une architecture <strong>fragmentée en 5 briques distinctes</strong> : authentification, e-learning, boutique, API et CDN reposant sur une base de données <strong>Neo4j</strong>. Ma mission : rationaliser et moderniser l'ensemble.</p>
          </div>
          <div class="exp-missions reveal">
            <div class="exp-mission-col">
              <h4>🔧 Back-End &amp; Architecture</h4>
              <ul>
                <li>Développement <strong>from scratch</strong> d'une application monolithique <strong>CakePHP</strong> fusionnant les briques d'authentification et de boutique</li>
                <li>Abandon de Neo4j, modélisation et création intégrale d'une nouvelle base de données <strong>MySQL</strong></li>
                <li>Délégation du e-learning vers un LMS externe (<strong>School Maker</strong>)</li>
                <li>Refactoring de méthodes existantes pour de meilleures performances</li>
              </ul>
            </div>
            <div class="exp-mission-col">
              <h4>🐳 DevOps &amp; Optimisation</h4>
              <ul>
                <li>Refonte complète de l'<strong>architecture Docker</strong> pour optimiser la gestion des conteneurs</li>
                <li>Mise en place des fondations d'une <strong>pipeline CI/CD</strong></li>
                <li>Reprise et optimisation de l'<strong>UI/UX</strong> sur diverses fonctionnalités</li>
              </ul>
            </div>
          </div>
          <div class="exp-tags reveal">
            <span class="tag" v-for="t in expTags" :key="t">{{ t }}</span>
          </div>
        </div>
      </div>
    </section>

    <section id="skills">
      <div class="container">
        <div class="section-label reveal">03 — Compétences</div>
        <h2 class="section-title reveal">Stack technique</h2>
        <div class="skills-grid">
          <div class="skill-category reveal" v-for="cat in skills" :key="cat.name">
            <div class="skill-cat-header">
              <span class="skill-cat-icon">{{ cat.icon }}</span>
              <h3>{{ cat.name }}</h3>
            </div>
            <div class="skill-badges">
              <span class="badge" v-for="skill in cat.items" :key="skill">{{ skill }}</span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="projects">
      <div class="container">
        <div class="section-label reveal">04 — Projets</div>
        <h2 class="section-title reveal">Portfolio</h2>
        <div class="projects-grid">
          <div class="project-card reveal" v-for="project in projects" :key="project.title">
            <div class="project-accent" :style="{ background: project.color }"></div>
            <div class="project-meta">
              <span class="project-type">{{ project.type }}</span>
            </div>
            <h3 class="project-title">{{ project.title }}</h3>
            <p class="project-desc" v-html="project.desc"></p>
            <div class="project-footer">
              <div class="project-tags">
                <span class="project-tag" v-for="tag in project.tags" :key="tag">{{ tag }}</span>
              </div>
              <a v-if="project.link" :href="project.link" target="_blank" rel="noopener" class="project-link">Repo ↗</a>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="contact">
      <div class="container">
        <div class="section-label reveal">05 — Contact</div>
        <h2 class="section-title reveal">Travaillons ensemble</h2>
        <p class="contact-intro reveal">Une opportunité, un projet, ou simplement envie d'échanger ? N'hésitez pas à me contacter.</p>
        <div class="contact-cards reveal">
          <a href="mailto:eotenfrere@gmail.com" class="contact-card">
            <div class="contact-icon">✉️</div>
            <div class="contact-info">
              <div class="contact-label">Email</div>
              <div class="contact-value">eotenfrere@gmail.com</div>
            </div>
          </a>
        </div>
      </div>
    </section>

    <footer>
      <div class="footer-inner">
        <span class="footer-logo">EF</span>
        <span class="footer-copy">© 2026 Eoten FRERE — Développeur Web</span>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const menuOpen = ref(false)
const activeSection = ref('hero')

const navLinks = [
  { id: 'about', label: 'À propos' },
  { id: 'experience', label: 'Expérience' },
  { id: 'skills', label: 'Compétences' },
  { id: 'projects', label: 'Projets' },
  { id: 'contact', label: 'Contact' },
]

const dailyTech = ['CakePHP', 'PHP', 'JavaScript', 'HTML', 'CSS', 'MySQL', 'Docker']

const expTags = ['CakePHP', 'PHP', 'MySQL', 'Docker', 'Git', 'School Maker', 'CI/CD', 'HTML', 'CSS', 'JavaScript']

const skills = [
  {
    icon: '🌐',
    name: 'Développement Web',
    items: ['CakePHP 3→5', 'PHP', 'HTML', 'CSS', 'JavaScript', 'Bootstrap'],
  },
  {
    icon: '🛠',
    name: 'Outils & Environnement',
    items: ['Docker', 'Git', 'Microsoft 365'],
  },
  {
    icon: '🗃',
    name: 'Bases de données',
    items: ['MySQL', 'SQLite', 'MariaDB', 'Neo4j'],
  },
  {
    icon: '💻',
    name: 'Autres langages',
    items: ['Python', 'Java'],
  },
]

const projects = [
  {
    title: 'Site Web — Mairie de Beaupont',
    type: 'SAE universitaire',
    color: 'linear-gradient(135deg, #667eea, #764ba2)',
    desc: "Refonte complète du site web communal. Migration de CakePHP 3 à CakePHP 5, remplacement d'Elasticsearch par Typesense, migration de Bootstarp 3 à Bootstrap 5, conteneurisation Docker de l'application. Focus sur la préservation du SEO, accessibilité RGAA et responsive design.",
    tags: ['CakePHP 5', 'Typesense', 'Bootstrap 5', 'Docker', 'RGAA'],
    link: 'https://git.widee.dev/Romain/beaupont5',
  },
  {
    title: 'Développeur Full Stack — Agrilearn',
    type: 'Stage',
    color: 'linear-gradient(135deg, #58a6ff, #1f6feb)',
    desc: `<strong>1. Outil centralisé de gestion des logs (Back-end)</strong><br>
    Développement d'un plugin CakePHP avec parsing via base Redis et affichage dynamique JS (DataTables) pour centraliser et déboguer les erreurs des multiples applications.<br><br>
    <strong>2. Refonte de l'authentification & 2FA (Full Stack)</strong><br>
    Implémentation d'une double authentification (2FA) invisible basée sur un "fingerprint" de navigateur (localStorage), avec envoi conditionnel de SMS via l'API Brevo.<br><br>
    <strong>3. Génération dynamique et mise en cache de PDF (Back-end)</strong><br>
    Développement d'un composant PHP (TCPDF) pour générer à la volée les programmes de formation avec un système de cache intelligent pour maximiser les performances.<br><br>
    <strong>4. Refonte UI/UX et optimisation Front-end (Design cognitif)</strong><br>
    Application de principes de neuro-design (hiérarchie visuelle, appels à l'action) guidés par un spécialiste pour maximiser la lisibilité et l'engagement des interfaces.`,
    tags: ['CakePHP', 'PHP', 'JavaScript', 'HTML', 'CSS', 'Bootstrap', 'Redis', 'MySQL', 'Neo4j', 'Docker', 'API Brevo', 'TCPDF'],
    link: 'https://git.widee.dev/Agrilearn',
  },
  {
    title: 'Fromagerie de Saint Julien',
    type: 'Freelance',
    color: 'linear-gradient(135deg, #f093fb, #f5576c)',
    desc: "Mise à jour et modernisation du site web. Migration de CakePHP 3 vers CakePHP 5 et conteneurisation complète de l'environnement de développement avec Docker.",
    tags: ['CakePHP 5', 'Docker', 'Migration'],
  },
  {
    title: 'Application Météo / Solaire',
    type: 'SAE universitaire',
    color: 'linear-gradient(135deg, #4facfe, #00f2fe)',
    desc: "Application web CakePHP pour récupérer, stocker et visualiser en temps réel les données de panneaux solaires et d'une station météorologique.",
    tags: ['CakePHP', 'Python', 'Bash', 'MariaDB', 'HTML', 'CSS', 'JavaScript', 'PHP'],
    link: 'https://iutbg-gitlab.iutbourg.univ-lyon1.fr/sae-but2/2024-25/pilotage-donnees-station-meteo',
  },
  {
    title: 'Gestion de Recettes',
    type: 'Projet web',
    color: 'linear-gradient(135deg, #43e97b, #38f9d7)',
    desc: "Application web CakePHP pour la gestion de recettes culinaires et de listes de courses. Interface intuitive pour la création, la modification et l'organisation des recettes.",
    tags: ['CakePHP', 'CRUD', 'SQLite'],
    link: 'https://iutbg-gitlab.iutbourg.univ-lyon1.fr/p2312392/listecourses_eoten_romain',
  },
  {
    title: 'Refonte Front-End — widee.dev & Transports Perrier',
    type: 'Freelance',
    color: 'linear-gradient(135deg, #fa8231, #f7b731)',
    desc: "Refonte complète de l'interface utilisateur de deux sites web : <a href='https://widee.dev' target='_blank' rel='noopener'>widee.dev</a> et la page dédiée de Transports Perrier. Modernisation graphique, optimisation de l'expérience utilisateur et amélioration de la performance front-end.",
    tags: ['HTML', 'CSS', 'JavaScript', 'UI/UX', 'Responsive'],
  },
]

function scrollTo(id) {
  const el = document.getElementById(id)
  if (el) el.scrollIntoView({ behavior: 'smooth' })
}

function handleScroll() {
  isScrolled.value = window.scrollY > 30

  const sections = ['hero', 'about', 'experience', 'skills', 'projects', 'contact']
  for (let i = sections.length - 1; i >= 0; i--) {
    const el = document.getElementById(sections[i])
    if (el && window.scrollY >= el.offsetTop - 120) {
      activeSection.value = sections[i]
      break
    }
  }
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll, { passive: true })

  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add('visible')
          observer.unobserve(entry.target)
        }
      })
    },
    { threshold: 0.12 }
  )

  document.querySelectorAll('.reveal').forEach((el) => observer.observe(el))
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#app-root {
  font-family: 'Inter', sans-serif;
  background: #0d1117;
  color: #e6edf3;
  scroll-behavior: smooth;
  overflow-x: hidden;
}

/* ── NAVBAR ── */
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 1000;
  transition: background 0.3s, backdrop-filter 0.3s, box-shadow 0.3s;
}

.navbar.scrolled {
  background: rgba(13, 17, 23, 0.85);
  backdrop-filter: blur(20px);
  box-shadow: 0 1px 0 rgba(255, 255, 255, 0.06);
}

.nav-inner {
  max-width: 1100px;
  margin: 0 auto;
  padding: 0 2rem;
  height: 68px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.nav-logo {
  font-size: 1.25rem;
  font-weight: 800;
  color: #58a6ff;
  text-decoration: none;
  letter-spacing: 0.05em;
}

.nav-links {
  list-style: none;
  display: flex;
  gap: 2rem;
}

.nav-links a {
  color: #8b949e;
  text-decoration: none;
  font-size: 0.875rem;
  font-weight: 500;
  transition: color 0.2s;
  position: relative;
  padding-bottom: 2px;
}

.nav-links a::after {
  content: '';
  position: absolute;
  bottom: -2px;
  left: 0;
  width: 0;
  height: 2px;
  background: #58a6ff;
  transition: width 0.25s ease;
}

.nav-links a:hover,
.nav-links a.active {
  color: #e6edf3;
}

.nav-links a:hover::after,
.nav-links a.active::after {
  width: 100%;
}

.burger {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 4px;
}

.burger span {
  display: block;
  width: 22px;
  height: 2px;
  background: #e6edf3;
  border-radius: 2px;
  transition: transform 0.3s, opacity 0.3s;
}

.mobile-menu {
  display: none;
  flex-direction: column;
  background: rgba(13, 17, 23, 0.97);
  padding: 0;
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.4s ease, padding 0.3s;
}

.mobile-menu.open {
  max-height: 300px;
  padding: 1rem 0;
}

.mobile-menu a {
  color: #e6edf3;
  text-decoration: none;
  padding: 0.75rem 2rem;
  font-size: 1rem;
  font-weight: 500;
  display: block;
  transition: color 0.2s, background 0.2s;
}

.mobile-menu a:hover {
  color: #58a6ff;
  background: rgba(88, 166, 255, 0.06);
}

/* ── REVEAL ANIMATIONS ── */
.reveal {
  opacity: 0;
  transform: translateY(28px);
  transition: opacity 0.65s ease, transform 0.65s ease;
}

.reveal.visible {
  opacity: 1;
  transform: translateY(0);
}

/* ── HERO ── */
#hero {
  position: relative;
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.hero-bg {
  position: absolute;
  inset: 0;
  z-index: 0;
}

.hero-orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(100px);
  opacity: 0.18;
}

.orb1 {
  width: 600px;
  height: 600px;
  background: #58a6ff;
  top: -150px;
  left: -150px;
}

.orb2 {
  width: 500px;
  height: 500px;
  background: #a371f7;
  bottom: -100px;
  right: -100px;
}

.grid-overlay {
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(rgba(88, 166, 255, 0.04) 1px, transparent 1px),
    linear-gradient(90deg, rgba(88, 166, 255, 0.04) 1px, transparent 1px);
  background-size: 60px 60px;
}

.hero-content {
  position: relative;
  z-index: 1;
  text-align: center;
  padding: 8rem 2rem 4rem;
  max-width: 800px;
}

.hero-badge {
  display: inline-block;
  background: rgba(88, 166, 255, 0.12);
  border: 1px solid rgba(88, 166, 255, 0.3);
  color: #58a6ff;
  font-size: 0.8rem;
  font-weight: 600;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  padding: 0.35rem 1rem;
  border-radius: 50px;
  margin-bottom: 1.5rem;
}

.hero-name {
  font-size: clamp(3rem, 8vw, 5.5rem);
  font-weight: 800;
  line-height: 1.08;
  letter-spacing: -0.03em;
  margin-bottom: 0.75rem;
}

.accent {
  color: #58a6ff;
}

.hero-title {
  font-size: clamp(1rem, 2.5vw, 1.25rem);
  font-weight: 400;
  color: #8b949e;
  margin-bottom: 1.5rem;
}

.sep {
  color: #30363d;
  margin: 0 0.5rem;
}

.hero-tagline {
  font-size: 1.05rem;
  color: #8b949e;
  line-height: 1.7;
  max-width: 560px;
  margin: 0 auto 2.5rem;
}

.hero-cta {
  display: flex;
  gap: 1rem;
  justify-content: center;
  flex-wrap: wrap;
  margin-bottom: 4rem;
}

.btn-primary {
  display: inline-block;
  background: #58a6ff;
  color: #0d1117;
  font-weight: 700;
  font-size: 0.9rem;
  padding: 0.8rem 2rem;
  border-radius: 8px;
  text-decoration: none;
  transition: background 0.2s, transform 0.2s, box-shadow 0.2s;
}

.btn-primary:hover {
  background: #79b8ff;
  transform: translateY(-2px);
  box-shadow: 0 8px 24px rgba(88, 166, 255, 0.35);
}

.btn-outline {
  display: inline-block;
  background: transparent;
  color: #e6edf3;
  font-weight: 600;
  font-size: 0.9rem;
  padding: 0.8rem 2rem;
  border-radius: 8px;
  border: 1px solid #30363d;
  text-decoration: none;
  transition: border-color 0.2s, color 0.2s, transform 0.2s;
}

.btn-outline:hover {
  border-color: #58a6ff;
  color: #58a6ff;
  transform: translateY(-2px);
}

.hero-scroll-hint {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
  cursor: pointer;
  opacity: 0.4;
  transition: opacity 0.2s;
}

.hero-scroll-hint:hover {
  opacity: 0.8;
}

.hero-scroll-hint span {
  font-size: 0.7rem;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: #8b949e;
}

.scroll-line {
  width: 1px;
  height: 40px;
  background: linear-gradient(to bottom, #58a6ff, transparent);
  animation: scrollPulse 2s ease-in-out infinite;
}

@keyframes scrollPulse {
  0%, 100% { opacity: 0.3; }
  50% { opacity: 1; }
}

/* ── SHARED LAYOUT ── */
.container {
  max-width: 1100px;
  margin: 0 auto;
  padding: 0 2rem;
}

section {
  padding: 6rem 0;
}

section:not(#hero) {
  border-top: 1px solid #21262d;
}

.section-label {
  font-size: 0.75rem;
  font-weight: 600;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: #58a6ff;
  margin-bottom: 0.75rem;
}

.section-title {
  font-size: clamp(1.8rem, 4vw, 2.8rem);
  font-weight: 800;
  letter-spacing: -0.02em;
  margin-bottom: 3rem;
  color: #e6edf3;
}

/* ── ABOUT ── */
.about-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 3rem;
  align-items: start;
}

.about-text p {
  color: #8b949e;
  line-height: 1.8;
  margin-bottom: 1.25rem;
  font-size: 1rem;
}

.about-text strong {
  color: #e6edf3;
  font-weight: 600;
}

.about-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-top: 1.5rem;
}

.tag {
  background: rgba(88, 166, 255, 0.1);
  border: 1px solid rgba(88, 166, 255, 0.25);
  color: #58a6ff;
  padding: 0.3rem 0.8rem;
  border-radius: 6px;
  font-size: 0.8rem;
  font-weight: 500;
}

.about-card {
  background: #161b22;
  border: 1px solid #21262d;
  border-radius: 16px;
  padding: 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}

.card-item {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.card-icon {
  font-size: 1.5rem;
  width: 44px;
  height: 44px;
  background: #0d1117;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.card-label {
  font-size: 0.72rem;
  color: #8b949e;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  margin-bottom: 2px;
}

.card-value {
  font-size: 0.9rem;
  font-weight: 600;
  color: #e6edf3;
}

/* ── EXPERIENCE ── */
.exp-grid {
  background: #161b22;
  border: 1px solid #21262d;
  border-radius: 16px;
  padding: 2.5rem;
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.exp-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  flex-wrap: wrap;
  gap: 1rem;
  padding-bottom: 1.5rem;
  border-bottom: 1px solid #21262d;
}

.exp-company {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.exp-logo {
  width: 50px;
  height: 50px;
  background: linear-gradient(135deg, #1f6feb, #58a6ff);
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 800;
  font-size: 1.2rem;
  color: #fff;
  letter-spacing: 0.05em;
  flex-shrink: 0;
}

.exp-name {
  font-size: 1.25rem;
  font-weight: 700;
  color: #e6edf3;
  margin-bottom: 0.25rem;
}

.exp-role {
  color: #8b949e;
  font-size: 0.9rem;
  font-weight: 500;
}

.exp-repo-btn {
  display: inline-flex;
  align-items: center;
  gap: 0.25rem;
  font-size: 0.85rem;
  font-weight: 600;
  color: #58a6ff;
  text-decoration: none;
  padding: 0.5rem 1rem;
  border: 1px solid rgba(88, 166, 255, 0.3);
  border-radius: 8px;
  transition: background 0.2s, border-color 0.2s;
}

.exp-repo-btn:hover {
  background: rgba(88, 166, 255, 0.1);
  border-color: rgba(88, 166, 255, 0.6);
}

.exp-context p {
  color: #c9d1d9;
  font-size: 1rem;
  line-height: 1.7;
}

.exp-context strong {
  color: #fff;
}

.exp-missions {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 2rem;
}

.exp-mission-col h4 {
  font-size: 1rem;
  font-weight: 600;
  color: #e6edf3;
  margin-bottom: 1rem;
}

.exp-mission-col ul {
  list-style: none;
}

.exp-mission-col li {
  color: #8b949e;
  font-size: 0.9rem;
  line-height: 1.6;
  margin-bottom: 0.75rem;
  padding-left: 1.25rem;
  position: relative;
}

.exp-mission-col li::before {
  content: '→';
  position: absolute;
  left: 0;
  color: #58a6ff;
  font-weight: bold;
}

.exp-mission-col strong {
  color: #c9d1d9;
}

.exp-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  padding-top: 1.5rem;
  border-top: 1px solid #21262d;
}

/* ── SKILLS ── */
#skills {
  background: #0a0e14;
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1.5rem;
}

.skill-category {
  background: #161b22;
  border: 1px solid #21262d;
  border-radius: 16px;
  padding: 1.75rem;
  transition: border-color 0.25s, transform 0.25s;
}

.skill-category:hover {
  border-color: rgba(88, 166, 255, 0.3);
  transform: translateY(-4px);
}

.skill-cat-header {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  margin-bottom: 1.25rem;
}

.skill-cat-icon {
  font-size: 1.4rem;
}

.skill-cat-header h3 {
  font-size: 0.95rem;
  font-weight: 700;
  color: #e6edf3;
}

.skill-badges {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.badge {
  background: #0d1117;
  border: 1px solid #30363d;
  color: #8b949e;
  padding: 0.3rem 0.75rem;
  border-radius: 6px;
  font-size: 0.8rem;
  font-weight: 500;
  transition: border-color 0.2s, color 0.2s;
}

.skill-category:hover .badge {
  border-color: rgba(88, 166, 255, 0.2);
  color: #c9d1d9;
}

/* ── PROJECTS ── */
.projects-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1.5rem;
}

.project-card {
  background: #161b22;
  border: 1px solid #21262d;
  border-radius: 16px;
  padding: 1.75rem;
  position: relative;
  overflow: hidden;
  transition: border-color 0.25s, transform 0.25s, box-shadow 0.25s;
}

.project-card:hover {
  border-color: rgba(88, 166, 255, 0.25);
  transform: translateY(-5px);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.4);
}

.project-accent {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 3px;
}

.project-meta {
  margin-bottom: 0.75rem;
  margin-top: 0.5rem;
}

.project-type {
  font-size: 0.72rem;
  font-weight: 600;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: #58a6ff;
}

.project-title {
  font-size: 1.1rem;
  font-weight: 700;
  color: #e6edf3;
  margin-bottom: 0.75rem;
  line-height: 1.3;
}

.project-desc {
  color: #8b949e;
  font-size: 0.9rem;
  line-height: 1.7;
  margin-bottom: 1.25rem;
}

.project-desc a {
  color: #58a6ff;
  text-decoration: none;
  border-bottom: 1px solid rgba(88, 166, 255, 0.3);
  transition: border-color 0.2s;
}

.project-desc a:hover {
  border-color: #58a6ff;
}

.project-footer {
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  gap: 0.75rem;
  flex-wrap: wrap;
}

.project-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.4rem;
  flex: 1;
}

.project-tag {
  background: #0d1117;
  border: 1px solid #30363d;
  color: #8b949e;
  padding: 0.2rem 0.6rem;
  border-radius: 4px;
  font-size: 0.75rem;
  font-weight: 500;
}

.project-link {
  display: inline-flex;
  align-items: center;
  gap: 0.25rem;
  font-size: 0.78rem;
  font-weight: 600;
  color: #58a6ff;
  text-decoration: none;
  white-space: nowrap;
  padding: 0.25rem 0.65rem;
  border: 1px solid rgba(88, 166, 255, 0.3);
  border-radius: 6px;
  transition: background 0.2s, border-color 0.2s;
  flex-shrink: 0;
}

.project-link:hover {
  background: rgba(88, 166, 255, 0.1);
  border-color: rgba(88, 166, 255, 0.6);
}

/* ── CONTACT ── */
#contact {
  background: #0a0e14;
}

.contact-intro {
  color: #8b949e;
  font-size: 1.05rem;
  margin-bottom: 2.5rem;
  margin-top: -1.5rem;
}

.contact-cards {
  display: flex;
  gap: 1.25rem;
  flex-wrap: wrap;
}

.contact-card {
  display: flex;
  align-items: center;
  gap: 1rem;
  background: #161b22;
  border: 1px solid #21262d;
  border-radius: 14px;
  padding: 1.25rem 1.75rem;
  text-decoration: none;
  transition: border-color 0.25s, transform 0.25s, box-shadow 0.25s;
  min-width: 260px;
}

.contact-card:hover {
  border-color: rgba(88, 166, 255, 0.35);
  transform: translateY(-4px);
  box-shadow: 0 12px 30px rgba(0, 0, 0, 0.3);
}

.contact-icon {
  font-size: 1.75rem;
}

.contact-label {
  font-size: 0.72rem;
  color: #8b949e;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  margin-bottom: 3px;
}

.contact-value {
  font-size: 0.95rem;
  font-weight: 600;
  color: #e6edf3;
}

/* ── FOOTER ── */
footer {
  border-top: 1px solid #21262d;
  padding: 2rem;
}

.footer-inner {
  max-width: 1100px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.footer-logo {
  font-size: 1.1rem;
  font-weight: 800;
  color: #58a6ff;
  letter-spacing: 0.05em;
}

.footer-copy {
  font-size: 0.8rem;
  color: #8b949e;
}

/* ── RESPONSIVE ── */
@media (max-width: 768px) {
  .nav-links {
    display: none;
  }

  .burger {
    display: flex;
  }

  .mobile-menu {
    display: flex;
  }

  .about-grid,
  .exp-missions,
  .skills-grid,
  .projects-grid {
    grid-template-columns: 1fr;
  }

  .contact-cards {
    flex-direction: column;
  }

  .contact-card {
    min-width: 0;
    width: 100%;
  }

  .hero-content {
    padding: 7rem 1.5rem 3rem;
  }

  section {
    padding: 4rem 0;
  }

  .section-title {
    margin-bottom: 2rem;
  }
}

@media (max-width: 480px) {
  .hero-cta {
    flex-direction: column;
    align-items: center;
  }

  .btn-primary,
  .btn-outline {
    width: 100%;
    text-align: center;
  }
}
</style>
