<template>
  <div id="app-root">
    <nav class="navbar">
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
              <a v-if="project.link" :href="project.link" target="_blank" rel="noopener" class="project-link">Repo ↗</a>
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
        <div class="contact-cards reveal">
          <a href="mailto:eotenfrere@gmail.com" class="contact-card">
            <div class="contact-icon">✉️</div>
            <div class="contact-info">
              <div class="contact-label">Email</div>
              <div class="contact-value">eotenfrere@gmail.com</div>
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
import { ref, onMounted, onUnmounted } from 'vue'


const isMobile = ref(window.innerWidth <= 1024)
const sectionIds = ['hero', 'about', 'experience', 'skills', 'projects', 'contact']
const TAB_WIDTH = 70; // px

const menuOpen = ref(false)
const activeSection = ref('hero')

const navLinks = [
  { id: 'hero', label: 'Accueil' },
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
    items: ['CakePHP', 'PHP', 'HTML', 'CSS', 'JavaScript', 'Bootstrap'],
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
  // Initial reveal for hero section
  setTimeout(revealElements, 100)
})

onUnmounted(() => {
  window.removeEventListener('resize', handleResize)
})
</script>


<style>
html, body {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
  overflow: hidden; /* Prevent global scroll */
  background: #0a0e14; /* Fill entire window */
}
</style>

<style scoped>
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
#app-root { font-family: 'Inter', sans-serif; background: #0a0e14; height: 100vh; overflow: hidden; color: #c9d1d9; }

/* ── HEADER GLASSMORPHISM ── */
.navbar {
  position: fixed;
  top: 1.5rem;
  left: 50%;
  transform: translateX(-50%);
  width: calc(100% - 3rem);
  max-width: 1200px;
  height: 70px;
  background: rgba(13, 17, 23, 0.45);
  backdrop-filter: blur(28px);
  -webkit-backdrop-filter: blur(28px);
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 100px;
  display: flex;
  align-items: center;
  padding: 0 2rem;
  z-index: 999;
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.5);
  transition: all 0.3s;
}

.nav-inner { width: 100%; display: flex; justify-content: space-between; align-items: center; }
.nav-logo { font-size: 1.5rem; font-weight: 800; color: #58a6ff; text-decoration: none; }
.nav-links { display: flex; gap: 2.5rem; list-style: none; }
.nav-links a { color: #8b949e; text-decoration: none; font-size: 0.95rem; font-weight: 600; transition: color 0.3s; }
.nav-links a:hover, .nav-links a.active { color: #fff; }

/* ── MOBILE MENU & BURGER ── */
.burger { display: none; background: none; border: none; cursor: pointer; flex-direction: column; gap: 5px; }
.burger span { width: 25px; height: 3px; background: #c9d1d9; border-radius: 2px; transition: 0.3s; }
.mobile-menu { display: none; position: fixed; top: 0; left: 0; width: 100vw; height: 100vh; background: rgba(10, 14, 20, 0.95); backdrop-filter: blur(20px); -webkit-backdrop-filter: blur(20px); flex-direction: column; justify-content: center; align-items: center; gap: 2rem; z-index: 1000; opacity: 0; transition: 0.3s; pointer-events: none; }
.mobile-menu.open { display: flex; opacity: 1; pointer-events: auto; }
.mobile-menu a { color: #fff; text-decoration: none; font-size: 1.5rem; font-weight: 700; transition: 0.2s; }
.mobile-menu a:hover { color: #58a6ff; }

/* ── MAIN STACK ── */
.cards-container {
  position: relative;
  width: 100vw;
  height: 100vh;
  padding-top: calc(70px + 3rem); /* pour le header */
  background: radial-gradient(circle at 20% 30%, #1f6feb22 0%, transparent 40%),
              radial-gradient(circle at 80% 80%, #58a6ff1a 0%, transparent 40%);
}

.section-card {
  position: absolute;
  top: calc(70px + 3rem);
  bottom: 2rem;
  left: 2rem;
  width: calc(100vw - 4rem - 350px); /* 5 inactives * 70px = 350px */
  background: rgba(18, 22, 29, 0.75);
  backdrop-filter: blur(40px);
  -webkit-backdrop-filter: blur(40px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 24px;
  box-shadow: -15px 0 50px rgba(0, 0, 0, 0.5), inset 0 1px 1px rgba(255, 255, 255, 0.1);
  transition: transform 0.6s cubic-bezier(0.2, 0.8, 0.2, 1), opacity 0.6s, top 0.6s cubic-bezier(0.2, 0.8, 0.2, 1), bottom 0.6s cubic-bezier(0.2, 0.8, 0.2, 1);
  overflow: hidden;
  display: flex;
}

.section-card.inactive {
  top: calc(70px + 4.5rem);
  bottom: 3.5rem;
  opacity: 0.85;
}

.section-card.inactive:hover {
  background: rgba(18, 22, 29, 0.85);
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
  border-left: 1px solid rgba(255, 255, 255, 0.05);
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(0, 0, 0, 0.2);
  writing-mode: vertical-rl;
  text-orientation: mixed;
  color: #8b949e;
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
  color: #58a6ff;
  background: rgba(88, 166, 255, 0.1);
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
.section-label { color: #58a6ff; font-weight: 600; font-size: 0.9rem; letter-spacing: 0.1em; text-transform: uppercase; margin-bottom: 1rem; }
.section-title { font-size: 2.5rem; font-weight: 800; color: #fff; margin-bottom: 3rem; }

/* Styles du hero */
.hero-content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  min-height: 100%;
}
.hero-name { font-size: clamp(3rem, 6vw, 4.5rem); font-weight: 800; line-height: 1.1; margin-bottom: 1rem; color: #fff; }
.accent { color: #58a6ff; }
.hero-title { font-size: clamp(1.1rem, 2vw, 1.4rem); color: #8b949e; font-weight: 500; margin-bottom: 1.5rem; }
.hero-tagline { font-size: 1.1rem; color: #c9d1d9; line-height: 1.6; max-width: 600px; margin-bottom: 2.5rem; }
.hero-cta { display: flex; gap: 1rem; }
.btn-primary { background: #58a6ff; color: #0d1117; padding: 0.8rem 1.8rem; border-radius: 12px; font-weight: 600; text-decoration: none; transition: 0.2s; }
.btn-primary:hover { background: #1f6feb; color: #fff; transform: translateY(-2px); }
.btn-outline { background: transparent; color: #58a6ff; border: 1px solid #58a6ff; padding: 0.8rem 1.8rem; border-radius: 12px; font-weight: 600; text-decoration: none; transition: 0.2s; }
.btn-outline:hover { background: rgba(88, 166, 255, 0.1); transform: translateY(-2px); }

/* About */
.about-grid { display: grid; gap: 3rem; grid-template-columns: 1fr 350px; }
.about-text p { color: #c9d1d9; font-size: 1.05rem; line-height: 1.7; margin-bottom: 1.5rem; }
.about-text strong { color: #fff; }
.about-tags { display: flex; flex-wrap: wrap; gap: 0.6rem; margin-top: 2rem; }
.tag { background: rgba(88, 166, 255, 0.1); color: #58a6ff; padding: 0.4rem 1rem; border-radius: 20px; font-size: 0.85rem; font-weight: 600; }
.about-card { background: #161b22; border: 1px solid #21262d; border-radius: 16px; padding: 2rem; display: flex; flex-direction: column; gap: 1.5rem; }
.card-item { display: flex; gap: 1rem; }
.card-icon { width: 40px; height: 40px; background: #0d1117; border: 1px solid #30363d; border-radius: 10px; display: flex; align-items: center; justify-content: center; font-size: 1.2rem; }
.card-label { font-size: 0.72rem; color: #8b949e; text-transform: uppercase; letter-spacing: 0.08em; margin-bottom: 2px; }
.card-value { font-size: 0.9rem; font-weight: 600; color: #e6edf3; }

/* Experience */
.exp-grid { background: #161b22; border: 1px solid #21262d; border-radius: 16px; padding: 2.5rem; display: flex; flex-direction: column; gap: 2rem; }
.exp-header { display: flex; justify-content: space-between; align-items: flex-start; flex-wrap: wrap; gap: 1rem; padding-bottom: 1.5rem; border-bottom: 1px solid #21262d; }
.exp-company { display: flex; align-items: center; gap: 1rem; }
.exp-logo { width: 50px; height: 50px; background: linear-gradient(135deg, #1f6feb, #58a6ff); border-radius: 12px; display: flex; align-items: center; justify-content: center; font-weight: 800; font-size: 1.2rem; color: #fff; flex-shrink: 0; }
.exp-name { font-size: 1.25rem; font-weight: 700; color: #e6edf3; margin-bottom: 0.25rem; }
.exp-role { color: #8b949e; font-size: 0.9rem; font-weight: 500; }
.exp-repo-btn { display: inline-flex; align-items: center; gap: 0.25rem; font-size: 0.85rem; font-weight: 600; color: #58a6ff; text-decoration: none; padding: 0.5rem 1rem; border: 1px solid rgba(88, 166, 255, 0.3); border-radius: 8px; transition: background 0.2s, border-color 0.2s; }
.exp-repo-btn:hover { background: rgba(88, 166, 255, 0.1); border-color: rgba(88, 166, 255, 0.6); }
.exp-context p { color: #c9d1d9; font-size: 1rem; line-height: 1.7; }
.exp-missions { display: grid; grid-template-columns: 1fr 1fr; gap: 2rem; }
.exp-mission-col h4 { font-size: 1rem; font-weight: 600; color: #e6edf3; margin-bottom: 1rem; }
.exp-mission-col ul { list-style: none; }
.exp-mission-col li { color: #8b949e; font-size: 0.9rem; line-height: 1.6; margin-bottom: 0.75rem; padding-left: 1.25rem; position: relative; }
.exp-mission-col li::before { content: '→'; position: absolute; left: 0; color: #58a6ff; font-weight: bold; }
.exp-tags { display: flex; flex-wrap: wrap; gap: 0.5rem; padding-top: 1.5rem; border-top: 1px solid #21262d; }

/* Skills */
.skills-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 1.5rem; }
.skill-category { background: #161b22; border: 1px solid #21262d; border-radius: 16px; padding: 1.75rem; }
.skill-cat-header { display: flex; align-items: center; gap: 0.75rem; margin-bottom: 1.25rem; }
.skill-cat-icon { font-size: 1.5rem; }
.skill-cat-header h3 { font-size: 1.1rem; font-weight: 600; color: #e6edf3; }
.skill-badges { display: flex; flex-wrap: wrap; gap: 0.5rem; }
.badge { background: #0d1117; border: 1px solid #30363d; color: #c9d1d9; padding: 0.4rem 0.8rem; border-radius: 8px; font-size: 0.85rem; font-weight: 500; }

/* Projects */
.projects-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(320px, 1fr)); gap: 1.5rem; }
.project-card { background: #161b22; border: 1px solid #21262d; border-radius: 16px; padding: 2rem; display: flex; flex-direction: column; position: relative; overflow: hidden; }
.project-accent { position: absolute; top: 0; left: 0; width: 100%; height: 4px; }
.project-meta { display: flex; justify-content: space-between; align-items: center; margin-bottom: 1rem; }
.project-type { font-size: 0.75rem; font-weight: 700; color: #8b949e; text-transform: uppercase; letter-spacing: 0.1em; }
.project-title { font-size: 1.25rem; font-weight: 700; color: #fff; margin-bottom: 0.75rem; }
.project-desc { color: #8b949e; font-size: 0.9rem; line-height: 1.7; margin-bottom: 1.25rem; flex: 1; }
.project-desc a { color: #58a6ff; text-decoration: none; border-bottom: 1px solid rgba(88, 166, 255, 0.3); transition: border-color 0.2s; }
.project-desc a:hover { border-color: #58a6ff; }
.project-footer { display: flex; align-items: flex-end; justify-content: space-between; gap: 0.75rem; flex-wrap: wrap; }
.project-tags { display: flex; flex-wrap: wrap; gap: 0.4rem; flex: 1; }
.project-tag { background: #0d1117; border: 1px solid #30363d; color: #8b949e; padding: 0.2rem 0.6rem; border-radius: 4px; font-size: 0.75rem; font-weight: 500; }
.project-link { display: inline-flex; align-items: center; gap: 0.25rem; font-size: 0.78rem; font-weight: 600; color: #58a6ff; text-decoration: none; white-space: nowrap; padding: 0.25rem 0.65rem; border: 1px solid rgba(88, 166, 255, 0.3); border-radius: 6px; transition: background 0.2s, border-color 0.2s; flex-shrink: 0; }
.project-link:hover { background: rgba(88, 166, 255, 0.1); border-color: rgba(88, 166, 255, 0.6); }

/* Contact & Footer */
.contact-intro { font-size: 1.1rem; color: #c9d1d9; max-width: 500px; margin-bottom: 2rem; line-height: 1.6; }
.contact-cards { display: flex; gap: 1.5rem; }
.contact-card { display: flex; align-items: center; gap: 1rem; background: #161b22; border: 1px solid #21262d; border-radius: 16px; padding: 1.25rem 1.5rem; text-decoration: none; transition: 0.3s; width: 100%; max-width: 320px; }
.contact-card:hover { border-color: #58a6ff; transform: translateY(-3px); }
.contact-icon { font-size: 1.5rem; }
.contact-label { font-size: 0.75rem; color: #8b949e; text-transform: uppercase; letter-spacing: 0.05em; margin-bottom: 3px; }
.contact-value { font-size: 1rem; font-weight: 600; color: #e6edf3; }
footer { margin-top: 3rem; border-top: 1px solid #21262d; padding-top: 2rem; }
.footer-inner { display: flex; justify-content: space-between; align-items: center; }
.footer-logo { font-size: 1.25rem; font-weight: 800; color: #58a6ff; }
.footer-copy { color: #8b949e; font-size: 0.85rem; margin-bottom: 2rem; } /* added bot margin so it clears bottom */

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
