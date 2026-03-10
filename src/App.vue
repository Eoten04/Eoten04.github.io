<template>
  <div id="app-root">
    <nav class="navbar" :class="theme">
      <div class="nav-inner">
        <a href="#hero" class="nav-logo" @click.prevent="scrollTo('hero')">EF</a>
        <ul class="nav-links">
          <li v-for="link in navLinks" :key="link.id">
            <a :href="`#${link.id}`" @click.prevent="scrollTo(link.id)" :class="{ active: activeSection === link.id }">
              {{ link.label }}
            </a>
          </li>
        </ul>
        <div class="nav-actions">
          <button class="theme-toggle" @click="toggleTheme" :aria-label="theme === 'dark' ? 'Passer au thème clair' : 'Passer au thème sombre'" :title="theme === 'dark' ? 'Thème clair' : 'Thème sombre'">
            {{ theme === 'dark' ? '☀️' : '🌙' }}
          </button>
          <button class="burger" @click="menuOpen = !menuOpen" :aria-expanded="menuOpen">
            <span></span><span></span><span></span>
          </button>
        </div>
      </div>
      <div class="mobile-menu" :class="{ open: menuOpen }">
        <a v-for="link in navLinks" :key="link.id" :href="`#${link.id}`"
           @click.prevent="scrollTo(link.id); menuOpen = false">{{ link.label }}</a>
      </div>
    </nav>

    
      <main class="cards-container">

    <section 
      id="hero" 
      class="section-card" 
      :class="{ active: activeSection === 'hero', inactive: activeSection !== 'hero' }" 
      :style="getCardStyle('hero')"
      @click="activeSection !== 'hero' && scrollTo('hero')"
    >
      <div class="card-inner-scroll custom-scrollbar">

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
      </div>
    
      </div>
      <div class="side-tab">
        <span class="side-tab-text">{{ getTabLabel('hero') }}</span>
      </div>
    </section>

      
    <section 
      id="about" 
      class="section-card" 
      :class="{ active: activeSection === 'about', inactive: activeSection !== 'about' }" 
      :style="getCardStyle('about')"
      @click="activeSection !== 'about' && scrollTo('about')"
    >
      <div class="card-inner-scroll custom-scrollbar">

      <div class="container">
        <div class="section-label reveal">01 — À propos</div>
        <h2 class="section-title reveal">Qui suis-je&nbsp;?</h2>
        <div class="about-grid">
          <div class="about-text reveal">
            <p>Étudiant en <strong>3ème année de BUT Informatique</strong>, je me passionne pour le développement web sous toutes ses formes — de la conception d'interfaces propres à l'architecture de systèmes back-end robustes.</p>
            <p>J'aime particulièrement les projets qui demandent de <strong>repartir de zéro</strong> ou de <strong>moderniser l'existant</strong> : revoir une architecture, migrer une base de données, conteneuriser un environnement ou refondre une UI. Ce qui me motive, c'est de livrer quelque chose qui tient dans le temps.</p>
            <p>En dehors du code, je suis quelqu'un de <strong>curieux et méthodique</strong>, toujours à chercher la meilleure façon de faire les choses plutôt que la plus rapide.</p>
            <div class="about-cta reveal" style="margin-top: 2rem;">
              <a href="#skills" class="btn-primary" style="display: inline-flex; align-items: center; gap: 0.5rem;" @click.stop.prevent="scrollTo('skills')">
                <span style="font-size: 1.2rem;">⚡</span> Découvrir ma stack technique
              </a>
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
    
      </div>
      <div class="side-tab">
        <span class="side-tab-text">{{ getTabLabel('about') }}</span>
      </div>
    </section>


      
    <section 
      id="experience" 
      class="section-card" 
      :class="{ active: activeSection === 'experience', inactive: activeSection !== 'experience' }" 
      :style="getCardStyle('experience')"
      @click="activeSection !== 'experience' && scrollTo('experience')"
    >
      <div class="card-inner-scroll custom-scrollbar">

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
            <div style="display: flex; gap: 0.5rem;">
              <a href="https://agrilearn.fr" target="_blank" rel="noopener" class="exp-repo-btn site-btn">Site ↗</a>
              <a href="https://git.widee.dev/Agrilearn" target="_blank" rel="noopener" class="exp-repo-btn">Repo ↗</a>
            </div>
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
    
      </div>
      <div class="side-tab">
        <span class="side-tab-text">{{ getTabLabel('experience') }}</span>
      </div>
    </section>

      
    <section 
      id="skills" 
      class="section-card" 
      :class="{ active: activeSection === 'skills', inactive: activeSection !== 'skills' }" 
      :style="getCardStyle('skills')"
      @click="activeSection !== 'skills' && scrollTo('skills')"
    >
      <div class="card-inner-scroll custom-scrollbar">

      <div class="container">
        <div class="section-label reveal">03 — Compétences</div>
        <h2 class="section-title reveal">Stack technique</h2>
        <div class="skills-grid">
          <div class="skill-category reveal" v-for="(group, groupName) in groupedTech" :key="groupName">
            <div class="skill-cat-header">
              <h3>{{ groupName }}</h3>
            </div>
            <div class="skill-badges">
              <span class="badge" v-for="skill in group" :key="skill.name">
                <img :src="getIconPath(skill.icon)" :alt="`${skill.name} icon`" class="badge-icon-svg" />
                {{ skill.name }}
              </span>
            </div>
          </div>
        </div>
      </div>
    
      </div>
      <div class="side-tab">
        <span class="side-tab-text">{{ getTabLabel('skills') }}</span>
      </div>
    </section>

      
    <section 
      id="projects" 
      class="section-card" 
      :class="{ active: activeSection === 'projects', inactive: activeSection !== 'projects' }" 
      :style="getCardStyle('projects')"
      @click="activeSection !== 'projects' && scrollTo('projects')"
    >
      <div class="card-inner-scroll custom-scrollbar">

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
              <div style="display: flex; gap: 0.5rem; flex-shrink: 0; align-items: center;">
                <a v-if="project.demoLink" :href="project.demoLink" target="_blank" rel="noopener" class="project-link site-btn">Site ↗</a>
                <a v-if="project.link" :href="project.link" target="_blank" rel="noopener" class="project-link">Repo ↗</a>
              </div>
            </div>
          </div>
        </div>
      </div>
    
      </div>
      <div class="side-tab">
        <span class="side-tab-text">{{ getTabLabel('projects') }}</span>
      </div>
    </section>

      
    <section 
      id="contact" 
      class="section-card" 
      :class="{ active: activeSection === 'contact', inactive: activeSection !== 'contact' }" 
      :style="getCardStyle('contact')"
      @click="activeSection !== 'contact' && scrollTo('contact')"
    >
      <div class="card-inner-scroll custom-scrollbar">

      <div class="container">
        <div class="section-label reveal">05 — Contact</div>
        <h2 class="section-title reveal">Travaillons ensemble</h2>
        <p class="contact-intro reveal">Une opportunité, un projet, ou simplement envie d'échanger ? N'hésitez pas à me contacter.</p>
        <div class="contact-cards reveal" style="flex-wrap: wrap;">
          <a href="mailto:eotenfrere@gmail.com" class="contact-card">
            <div class="contact-icon">✉️</div>
            <div class="contact-info">
              <div class="contact-label">Email</div>
              <div class="contact-value">eotenfrere@gmail.com</div>
            </div>
          </a>
          <a href="https://www.linkedin.com/in/eoten-fr%C3%A8re-114a72295/" target="_blank" rel="noopener" class="contact-card">
            <div class="contact-icon">🔗</div>
            <div class="contact-info">
              <div class="contact-label">LinkedIn</div>
              <div class="contact-value">Eoten FRÈRE</div>
            </div>
          </a>
        </div>
        
        <footer style="margin-top: 4rem; border-top: 1px solid #21262d; padding-top: 2rem;">
          <div class="footer-inner" style="display: flex; justify-content: space-between; align-items: center;">
            <span class="footer-logo" style="font-size: 1.25rem; font-weight: 800; color: #58a6ff;">EF</span>
            <span class="footer-copy" style="color: #8b949e; font-size: 0.85rem;">© 2026 Eoten FRERE — Développeur Web</span>
          </div>
        </footer>
      </div>
      
      </div>
      <div class="side-tab">
        <span class="side-tab-text">{{ getTabLabel('contact') }}</span>
      </div>
    </section>
    

    </main>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted, watch } from 'vue'


const isMobile = ref(window.innerWidth <= 1024)
const sectionIds = ['hero', 'about', 'experience', 'skills', 'projects', 'contact']
const TAB_WIDTH = 70; // px

const menuOpen = ref(false)
const activeSection = ref('hero')

const getInitialTheme = () => {
  const savedTheme = localStorage.getItem('ef-theme')
  if (savedTheme) return savedTheme
  return window.matchMedia('(prefers-color-scheme: light)').matches ? 'light-theme' : 'dark'
}

const theme = ref(getInitialTheme())

const toggleTheme = () => {
  theme.value = theme.value === 'dark' ? 'light-theme' : 'dark'
}

watch(theme, (newTheme) => {
  localStorage.setItem('ef-theme', newTheme)
  if (newTheme === 'light-theme') {
    document.documentElement.classList.add('light-theme')
    document.body.classList.add('light-theme')
  } else {
    document.documentElement.classList.remove('light-theme')
    document.body.classList.remove('light-theme')
  }
})

const navLinks = [
  { id: 'hero', label: 'Accueil' },
  { id: 'about', label: 'À propos' },
  { id: 'experience', label: 'Expérience' },
  { id: 'skills', label: 'Compétences' },
  { id: 'projects', label: 'Projets' },
  { id: 'contact', label: 'Contact' },
]

const groupedTech = {
  'Back-End & Base de données': [
    { name: 'CakePHP', icon: 'cakephp.svg' },
    { name: 'Symfony', icon: 'symfony.svg' },
    { name: 'PHP', icon: 'php.svg' },
    { name: 'MySQL', icon: 'mysql.svg' },
    { name: 'Neo4j', icon: 'neo4j.svg' }
  ],
  'Front-End': [
    { name: 'Vue.js', icon: 'vue.svg' },
    { name: 'JavaScript', icon: 'js.svg' },
    { name: 'HTML', icon: 'html-5.svg' },
    { name: 'CSS', icon: 'css-3.svg' },
    { name: 'Bootstrap', icon: 'bootstrap.svg' }
  ],
  'Infrastructure & Outils': [
    { name: 'Docker', icon: 'docker.svg' },
    { name: 'Git', icon: 'git.svg' },
    { name: 'Bash', icon: 'bash.svg' }
  ],
  'Autres langages': [
    { name: 'Python', icon: 'python.svg' },
    { name: 'Java', icon: 'java.svg' }
  ]
}

const expTags = ['CakePHP', 'PHP', 'MySQL', 'Docker', 'Git', 'School Maker', 'CI/CD', 'HTML', 'CSS', 'JavaScript']

const getIconPath = (iconFileName) => {
  return `${import.meta.env.BASE_URL}icons/${iconFileName}`
}

// Skills data removed, currently using the same groupedTech array as 'À propos'

const projects = [
  {
    title: 'Site Web — Mairie de Beaupont',
    type: 'SAE universitaire',
    color: 'linear-gradient(135deg, #667eea, #764ba2)',
    desc: "Refonte complète du site web communal. Migration de CakePHP 3 à CakePHP 5, remplacement d'Elasticsearch par Typesense, migration de Bootstarp 3 à Bootstrap 5, conteneurisation Docker de l'application. Focus sur la préservation du SEO, accessibilité RGAA et responsive design.",
    tags: ['CakePHP 5', 'Typesense', 'Bootstrap 5', 'Docker', 'RGAA'],
    link: 'https://git.widee.dev/Romain/beaupont5',
    demoLink: 'https://beaupont.fr',
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
    demoLink: 'https://agrilearn.fr',
  },
  {
    title: 'Fromagerie de Saint Julien',
    type: 'Freelance',
    color: 'linear-gradient(135deg, #f093fb, #f5576c)',
    desc: "Mise à jour et modernisation du site web. Migration de CakePHP 3 vers CakePHP 5 et conteneurisation complète de l'environnement de développement avec Docker.",
    tags: ['CakePHP 5', 'Docker', 'Migration'],
    demoLink: 'https://boutiqueducomte.com/',
  },
  {
    title: 'Application Météo / Solaire',
    type: 'SAE universitaire',
    color: 'linear-gradient(135deg, #4facfe, #00f2fe)',
    desc: "Application web CakePHP pour récupérer, stocker et visualiser en temps réel les données de panneaux solaires et d'une station météorologique.",
    tags: ['CakePHP', 'Python', 'Bash', 'MariaDB', 'HTML', 'CSS', 'JavaScript', 'PHP'],
    link: 'https://iutbg-gitlab.iutbourg.univ-lyon1.fr/sae-but2/2024-25/pilotage-donnees-station-meteo',
    demoLink: 'https://iutbgdgt-meteo.iutbourg.univ-lyon1.fr',
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
    demoLink: 'https://widee.dev',
  },
]

// getTechIcon is no longer used for About section, maintained for legacy if needed or removable

function handleResize() {
  isMobile.value = window.innerWidth <= 1024;
}

function getTabLabel(id) {
  const lbls = { hero: 'Accueil', about: 'À propos', experience: 'Expérience', skills: 'Compétences', projects: 'Projets', contact: 'Contact' }
  return lbls[id] || id;
}

function getCardStyle(id) {
  if (isMobile.value) {
    if (activeSection.value === id) {
      return { transform: 'translateY(0)', opacity: 1, zIndex: 10, pointerEvents: 'auto' }
    } else {
      return { transform: 'translateY(50px)', opacity: 0, zIndex: 0, pointerEvents: 'none' }
    }
  }

  const N = sectionIds.length;
  const index = sectionIds.indexOf(id);
  const activeIndex = sectionIds.indexOf(activeSection.value);

  if (index === activeIndex) {
    return {
      zIndex: 50,
      transform: 'translateX(0)',
      cursor: 'default'
    }
  } else {
    // Les inactives s'entassent vers la DROITE.
    const visualIndex = index < activeIndex ? index : index - 1; // de 0 à N-2
    // La distance depuis la droite.
    const translateX = (visualIndex + 1) * TAB_WIDTH;
    return {
      zIndex: 20 - visualIndex, // La plus à droite a z=20.
      transform: 'translateX(' + translateX + 'px)',
      cursor: 'pointer'
    }
  }
}

function scrollTo(id) {
  activeSection.value = id
}

function revealElements() {
  document.querySelectorAll('.reveal').forEach((el) => {
    el.classList.add('visible')
  })
}

onMounted(() => {
  window.addEventListener('resize', handleResize, { passive: true })
  
  if (theme.value === 'light-theme') {
    document.documentElement.classList.add('light-theme')
    document.body.classList.add('light-theme')
  }

  // Initial reveal for hero section
  setTimeout(revealElements, 100)
})

onUnmounted(() => {
  window.removeEventListener('resize', handleResize)
})
</script>


<style>
:root {
  --bg-color: #0a0e14;
  --text-main: #c9d1d9;
  --text-heading: #ffffff;
  --text-muted: #8b949e;
  --accent-color: #58a6ff;
  --accent-hover: #1f6feb;
  --card-bg: rgba(18, 22, 29, 0.75);
  --card-bg-hover: rgba(18, 22, 29, 0.85);
  --card-bg-solid: #161b22;
  --border-color: rgba(255, 255, 255, 0.1);
  --border-solid: #21262d;
  --nav-bg: rgba(13, 17, 23, 0.45);
  --nav-bg-mobile: rgba(10, 14, 20, 0.95);
  --badge-bg: #0d1117;
  --badge-border: #30363d;
  --hero-gradient-1: #1f6feb22;
  --hero-gradient-2: #58a6ff1a;
  --tab-bg: rgba(0, 0, 0, 0.2);
  --tag-bg: rgba(88, 166, 255, 0.1);
}

.light-theme {
  --bg-color: #f6f8fa;
  --text-main: #24292f;
  --text-heading: #0f1419;
  --text-muted: #57606a;
  --accent-color: #0969da;
  --accent-hover: #0550ae;
  --card-bg: rgba(255, 255, 255, 0.85);
  --card-bg-hover: rgba(255, 255, 255, 0.95);
  --card-bg-solid: #ffffff;
  --border-color: rgba(0, 0, 0, 0.1);
  --border-solid: #d0d7de;
  --nav-bg: rgba(255, 255, 255, 0.85);
  --nav-bg-mobile: rgba(255, 255, 255, 0.98);
  --badge-bg: #f6f8fa;
  --badge-border: #d0d7de;
  --hero-gradient-1: #0969da15;
  --hero-gradient-2: #58a6ff1a;
  --tab-bg: rgba(0, 0, 0, 0.05);
  --tag-bg: rgba(9, 105, 218, 0.1);
}

html, body {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
  overflow: hidden; /* Prevent global scroll */
  background: var(--bg-color); /* Fill entire window */
  color: var(--text-main);
  transition: background-color 0.3s, color 0.3s;
}
</style>

<style scoped>
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
#app-root { font-family: 'Inter', sans-serif; height: 100vh; overflow: hidden; }

/* ── HEADER GLASSMORPHISM ── */
.navbar {
  position: fixed;
  top: 1.5rem;
  left: 50%;
  transform: translateX(-50%);
  width: calc(100% - 3rem);
  max-width: 1200px;
  height: 70px;
  background: var(--nav-bg);
  backdrop-filter: blur(28px);
  -webkit-backdrop-filter: blur(28px);
  border: 1px solid var(--border-color);
  border-radius: 100px;
  display: flex;
  align-items: center;
  padding: 0 2rem;
  z-index: 999;
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.15);
  transition: all 0.3s;
}
.light-theme .navbar {
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.08);
}

.nav-inner { width: 100%; display: flex; justify-content: space-between; align-items: center; }
.nav-logo { font-size: 1.5rem; font-weight: 800; color: var(--accent-color); text-decoration: none; }
.nav-links { display: flex; gap: 2.5rem; list-style: none; }
.nav-links a { color: var(--text-muted); text-decoration: none; font-size: 0.95rem; font-weight: 600; transition: color 0.3s; }
.nav-links a:hover, .nav-links a.active { color: var(--text-heading); }

.nav-actions { display: flex; align-items: center; gap: 1rem; }
.theme-toggle { background: transparent; border: 1px solid var(--border-color); border-radius: 50%; width: 40px; height: 40px; display: flex; align-items: center; justify-content: center; font-size: 1.2rem; cursor: pointer; color: var(--text-main); transition: 0.2s; }
.theme-toggle:hover { background: var(--tag-bg); border-color: var(--accent-color); transform: scale(1.05); }

/* ── MOBILE MENU & BURGER ── */
.burger { display: none; background: none; border: none; cursor: pointer; flex-direction: column; gap: 5px; }
.burger span { width: 25px; height: 3px; background: var(--text-main); border-radius: 2px; transition: 0.3s; }
.mobile-menu { display: none; position: fixed; top: 0; left: 0; width: 100vw; height: 100vh; background: var(--nav-bg-mobile); backdrop-filter: blur(20px); -webkit-backdrop-filter: blur(20px); flex-direction: column; justify-content: center; align-items: center; gap: 2rem; z-index: 1000; opacity: 0; transition: 0.3s; pointer-events: none; }
.mobile-menu.open { display: flex; opacity: 1; pointer-events: auto; }
.mobile-menu a { color: var(--text-heading); text-decoration: none; font-size: 1.5rem; font-weight: 700; transition: 0.2s; }
.mobile-menu a:hover { color: var(--accent-color); }

/* ── MAIN STACK ── */
.cards-container {
  position: relative;
  width: 100vw;
  height: 100vh;
  padding-top: calc(70px + 3rem); /* pour le header */
  background: radial-gradient(circle at 20% 30%, var(--hero-gradient-1) 0%, transparent 40%),
              radial-gradient(circle at 80% 80%, var(--hero-gradient-2) 0%, transparent 40%);
}

.section-card {
  position: absolute;
  top: calc(70px + 3rem);
  bottom: 2rem;
  left: 2rem;
  width: calc(100vw - 4rem - 350px); /* 5 inactives * 70px = 350px */
  background: var(--card-bg);
  backdrop-filter: blur(40px);
  -webkit-backdrop-filter: blur(40px);
  border: 1px solid var(--border-color);
  border-radius: 24px;
  box-shadow: -15px 0 50px rgba(0, 0, 0, 0.3), inset 0 1px 1px rgba(255, 255, 255, 0.05);
  transition: transform 0.6s cubic-bezier(0.2, 0.8, 0.2, 1), opacity 0.6s, top 0.6s cubic-bezier(0.2, 0.8, 0.2, 1), bottom 0.6s cubic-bezier(0.2, 0.8, 0.2, 1), background-color 0.3s, border-color 0.3s;
  overflow: hidden;
  display: flex;
}
.light-theme .section-card {
  box-shadow: -15px 0 50px rgba(0, 0, 0, 0.08), inset 0 1px 1px rgba(255, 255, 255, 0.5);
}

.section-card.inactive {
  top: calc(70px + 4.5rem);
  bottom: 3.5rem;
  opacity: 0.85;
}

.section-card.inactive:hover {
  background: var(--card-bg-hover);
  opacity: 1;
}

.card-inner-scroll {
  flex: 1;
  height: 100%;
  overflow-y: auto;
  overflow-x: hidden;
  padding: 3rem 4rem;
}

/* ── SIDE TAB (ONGLET) ── */
.side-tab {
  position: absolute;
  top: 0;
  right: 0;
  width: 70px;
  height: 100%;
  border-left: 1px solid var(--border-color);
  display: flex;
  align-items: center;
  justify-content: center;
  background: var(--tab-bg);
  writing-mode: vertical-rl;
  text-orientation: mixed;
  color: var(--text-muted);
  font-weight: 600;
  font-size: 0.95rem;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  transition: all 0.3s;
  opacity: 1;
}

.section-card.active .side-tab {
  opacity: 0;       /* L'onglet disparait quand la carte est au premier plan */
  pointer-events: none;
}

.section-card.inactive:hover .side-tab {
  color: var(--accent-color);
  background: var(--tag-bg);
}

.side-tab-text {
  transform: rotate(180deg); /* Tourner vers la gauche pour être lisible facilement */
}

/* ── SCROLLBAR ── */
.custom-scrollbar {
  scrollbar-width: none; /* Firefox */
  -ms-overflow-style: none; /* IE et Edge */
}
.custom-scrollbar::-webkit-scrollbar { 
  display: none; /* Chrome, Safari, Opera */
}

/* Gardons le style de base pour tout le contenu interne (hero, about, skills, etc) */
.container { max-width: 900px; margin: 0 auto; }
.section-label { color: var(--accent-color); font-weight: 600; font-size: 0.9rem; letter-spacing: 0.1em; text-transform: uppercase; margin-bottom: 1rem; }
.section-title { font-size: 2.5rem; font-weight: 800; color: var(--text-heading); margin-bottom: 3rem; }

/* Styles du hero */
.hero-content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  min-height: 100%;
}
.hero-name { font-size: clamp(3rem, 6vw, 4.5rem); font-weight: 800; line-height: 1.1; margin-bottom: 1rem; color: var(--text-heading); }
.accent { color: var(--accent-color); }
.hero-title { font-size: clamp(1.1rem, 2vw, 1.4rem); color: var(--text-muted); font-weight: 500; margin-bottom: 1.5rem; }
.hero-tagline { font-size: 1.1rem; color: var(--text-main); line-height: 1.6; max-width: 600px; margin-bottom: 2.5rem; }
.hero-cta { display: flex; gap: 1rem; }
.btn-primary { background: var(--accent-color); color: var(--bg-color); padding: 0.8rem 1.8rem; border-radius: 12px; font-weight: 600; text-decoration: none; transition: 0.2s; }
.btn-primary:hover { background: var(--accent-hover); color: #fff; transform: translateY(-2px); }
.btn-outline { background: transparent; color: var(--accent-color); border: 1px solid var(--accent-color); padding: 0.8rem 1.8rem; border-radius: 12px; font-weight: 600; text-decoration: none; transition: 0.2s; }
.btn-outline:hover { background: var(--tag-bg); transform: translateY(-2px); }

/* About */
.about-grid { display: grid; gap: 3rem; grid-template-columns: 1fr 350px; }
.about-text p { color: var(--text-main); font-size: 1.05rem; line-height: 1.7; margin-bottom: 1.5rem; }
.about-text strong { color: var(--text-heading); }
.about-tags-grouped { display: flex; flex-direction: column; gap: 1.5rem; margin-top: 2rem; }
.tag-group { display: flex; flex-direction: column; gap: 0.5rem; }
.tag-group-title { font-size: 0.8rem; font-weight: 700; color: var(--text-muted); text-transform: uppercase; letter-spacing: 0.05em; margin-bottom: 0.2rem; }
.about-tags { display: flex; flex-wrap: wrap; gap: 0.6rem; }
.tag { background: var(--tag-bg); color: var(--accent-color); padding: 0.4rem 1rem; border-radius: 20px; font-size: 0.85rem; font-weight: 600; display: inline-flex; align-items: center; gap: 0.5rem; }
.tag-icon-svg { width: 22px; height: 22px; object-fit: contain; }
.about-card { background: var(--card-bg-solid); border: 1px solid var(--border-solid); border-radius: 16px; padding: 2rem; display: flex; flex-direction: column; gap: 1.5rem; }
.card-item { display: flex; gap: 1rem; }
.card-icon { width: 40px; height: 40px; background: var(--badge-bg); border: 1px solid var(--badge-border); border-radius: 10px; display: flex; align-items: center; justify-content: center; font-size: 1.2rem; }
.card-label { font-size: 0.72rem; color: var(--text-muted); text-transform: uppercase; letter-spacing: 0.08em; margin-bottom: 2px; }
.card-value { font-size: 0.9rem; font-weight: 600; color: var(--text-heading); }

/* Experience */
.exp-grid { background: var(--card-bg-solid); border: 1px solid var(--border-solid); border-radius: 16px; padding: 2.5rem; display: flex; flex-direction: column; gap: 2rem; }
.exp-header { display: flex; justify-content: space-between; align-items: flex-start; flex-wrap: wrap; gap: 1rem; padding-bottom: 1.5rem; border-bottom: 1px solid var(--border-solid); }
.exp-company { display: flex; align-items: center; gap: 1rem; }
.exp-logo { width: 50px; height: 50px; background: linear-gradient(135deg, var(--accent-hover), var(--accent-color)); border-radius: 12px; display: flex; align-items: center; justify-content: center; font-weight: 800; font-size: 1.2rem; color: #fff; flex-shrink: 0; }
.exp-name { font-size: 1.25rem; font-weight: 700; color: var(--text-heading); margin-bottom: 0.25rem; }
.exp-role { color: var(--text-muted); font-size: 0.9rem; font-weight: 500; }
.exp-repo-btn { display: inline-flex; align-items: center; gap: 0.25rem; font-size: 0.85rem; font-weight: 600; color: var(--accent-color); text-decoration: none; padding: 0.5rem 1rem; border: 1px solid var(--accent-color); border-radius: 8px; transition: background 0.2s, border-color 0.2s, color 0.2s; opacity: 0.8;}
.exp-repo-btn:hover { background: var(--tag-bg); opacity: 1; border-color: var(--accent-color); }
.exp-repo-btn.site-btn { background: var(--accent-color); color: #fff; border-color: var(--accent-color); opacity: 1; }
.exp-repo-btn.site-btn:hover { background: var(--accent-hover); border-color: var(--accent-hover); color: #fff; }
.exp-context p { color: var(--text-main); font-size: 1rem; line-height: 1.7; }
.exp-missions { display: grid; grid-template-columns: 1fr 1fr; gap: 2rem; }
.exp-mission-col h4 { font-size: 1rem; font-weight: 600; color: var(--text-heading); margin-bottom: 1rem; }
.exp-mission-col ul { list-style: none; }
.exp-mission-col li { color: var(--text-muted); font-size: 0.9rem; line-height: 1.6; margin-bottom: 0.75rem; padding-left: 1.25rem; position: relative; }
.exp-mission-col li::before { content: '→'; position: absolute; left: 0; color: var(--accent-color); font-weight: bold; }
.exp-tags { display: flex; flex-wrap: wrap; gap: 0.5rem; padding-top: 1.5rem; border-top: 1px solid var(--border-solid); }

/* Skills */
.skills-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 1.5rem; }
.skill-category { background: var(--card-bg-solid); border: 1px solid var(--border-solid); border-radius: 16px; padding: 1.75rem; }
.skill-cat-header { display: flex; align-items: center; gap: 0.75rem; margin-bottom: 1.25rem; }
.skill-cat-header h3 { font-size: 1.1rem; font-weight: 600; color: var(--text-heading); }
.skill-badges { display: flex; flex-wrap: wrap; gap: 0.5rem; }
.badge { background: var(--badge-bg); border: 1px solid var(--badge-border); color: var(--text-main); padding: 0.4rem 0.8rem; border-radius: 8px; font-size: 0.85rem; font-weight: 500; display: inline-flex; align-items: center; gap: 0.5rem; }
.badge-icon-svg { width: 16px; height: 16px; object-fit: contain; }

/* Projects */
.projects-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(320px, 1fr)); gap: 1.5rem; }
.project-card { background: var(--card-bg-solid); border: 1px solid var(--border-solid); border-radius: 16px; padding: 2rem; display: flex; flex-direction: column; position: relative; overflow: hidden; }
.project-accent { position: absolute; top: 0; left: 0; width: 100%; height: 4px; }
.project-meta { display: flex; justify-content: space-between; align-items: center; margin-bottom: 1rem; }
.project-type { font-size: 0.75rem; font-weight: 700; color: var(--text-muted); text-transform: uppercase; letter-spacing: 0.1em; }
.project-title { font-size: 1.25rem; font-weight: 700; color: var(--text-heading); margin-bottom: 0.75rem; }
.project-desc { color: var(--text-muted); font-size: 0.9rem; line-height: 1.7; margin-bottom: 1.25rem; flex: 1; }
.project-desc a { color: var(--accent-color); text-decoration: none; border-bottom: 1px solid var(--border-color); transition: border-color 0.2s; }
.project-desc a:hover { border-color: var(--accent-color); }
.project-footer { display: flex; align-items: flex-end; justify-content: space-between; gap: 0.75rem; flex-wrap: wrap; }
.project-tags { display: flex; flex-wrap: wrap; gap: 0.4rem; flex: 1; }
.project-tag { background: var(--badge-bg); border: 1px solid var(--badge-border); color: var(--text-muted); padding: 0.2rem 0.6rem; border-radius: 4px; font-size: 0.75rem; font-weight: 500; }
.project-link { display: inline-flex; align-items: center; gap: 0.25rem; font-size: 0.78rem; font-weight: 600; color: var(--accent-color); text-decoration: none; white-space: nowrap; padding: 0.25rem 0.65rem; border: 1px solid var(--accent-color); opacity:0.8; border-radius: 6px; transition: background 0.2s, border-color 0.2s, color 0.2s; flex-shrink: 0; }
.project-link:hover { background: var(--tag-bg); opacity: 1; border-color: var(--accent-color); }
.project-link.site-btn { background: var(--accent-color); color: #fff; border-color: var(--accent-color); opacity: 1;}
.project-link.site-btn:hover { background: var(--accent-hover); border-color: var(--accent-hover); color: #fff; }

/* Contact & Footer */
.contact-intro { font-size: 1.1rem; color: var(--text-main); max-width: 500px; margin-bottom: 2rem; line-height: 1.6; }
.contact-cards { display: flex; gap: 1.5rem; }
.contact-card { display: flex; align-items: center; gap: 1rem; background: var(--card-bg-solid); border: 1px solid var(--border-solid); border-radius: 16px; padding: 1.25rem 1.5rem; text-decoration: none; transition: 0.3s; width: 100%; max-width: 320px; }
.contact-card:hover { border-color: var(--accent-color); transform: translateY(-3px); }
.contact-icon { font-size: 1.5rem; }
.contact-label { font-size: 0.75rem; color: var(--text-muted); text-transform: uppercase; letter-spacing: 0.05em; margin-bottom: 3px; }
.contact-value { font-size: 1rem; font-weight: 600; color: var(--text-heading); }
footer { margin-top: 3rem; border-top: 1px solid var(--border-solid); padding-top: 2rem; }
.footer-inner { display: flex; justify-content: space-between; align-items: center; }
.footer-logo { font-size: 1.25rem; font-weight: 800; color: var(--accent-color); }
.footer-copy { color: var(--text-muted); font-size: 0.85rem; margin-bottom: 2rem; } /* added bot margin so it clears bottom */

/* Responsive Mobile */
@media (max-width: 1024px) {
  .section-card {
    position: relative;
    top: 0 !important;
    left: 0 !important;
    right: 0 !important;
    bottom: 0 !important;
    width: 100% !important;
    height: 100%;
    transform: none !important;
    opacity: 1 !important;
    pointer-events: auto !important;
    z-index: 1 !important;
    border-radius: 0;
    border: none;
    box-shadow: none;
    background: transparent;
    padding-top: 0;
  }
  .cards-container {
    padding-top: calc(70px + 1rem); /* top space */
    overflow-y: auto; /* Allow full scroll on mobile */
  }
  .side-tab { display: none; }
  .card-inner-scroll { padding: 1.5rem; overflow: visible; }
  .nav-links { display: none; }
  .burger { display: flex; }
}

@media (max-width: 768px) {
  .about-grid, .exp-missions, .skills-grid, .projects-grid { grid-template-columns: 1fr; }
}
</style>
