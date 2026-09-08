<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const menuOpen = ref(false)
const scrolled = ref(false)

const navItems = ['About', 'Skills', 'Experience', 'Projects', 'Education', 'Contact']

const skills = [
  { group: 'Backend', items: ['PHP', 'Laravel', 'Python', 'Django', 'REST APIs', 'GraphQL'] },
  { group: 'Frontend', items: ['JavaScript', 'React.js', 'Vue.js', 'Tailwind CSS'] },
  { group: 'Data & Security', items: ['MySQL', 'MongoDB', 'Keycloak SSO', 'RBAC'] },
  { group: 'Tools & Practices', items: ['Git', 'Postman', 'Agile / SDLC', 'Code Review', 'CI/CD Support'] }
]

const experience = [
  {
    role: 'Senior Software Developer',
    company: 'Paybrook Payments Tech Private Limited',
    period: 'Jun 2024 — Present',
    points: [
      'Led development and enhancement of Laravel-based Domestic Money Transfer and Payout Management Systems.',
      'Developed API-driven automated payout solutions processing 20,000+ daily transactions with 99.9% uptime.',
      'Built cross-border currency exchange, payroll management, recharge management and multi-company reporting platforms.',
      'Implemented secure authentication and authorization mechanisms across enterprise applications.',
      'Contributed to sprint planning, code reviews, testing, deployment, production support and technical documentation.'
    ]
  },
  {
    role: 'Software Developer',
    company: 'Paysmart Payment Technologies Private Limited',
    period: 'Apr 2023 — Jun 2024',
    points: [
      'Developed and maintained payout transaction management systems using Laravel.',
      'Built reusable backend services and RESTful APIs following PSR coding standards.',
      'Collaborated with QA and UI/UX teams to deliver stable product releases.',
      'Supported database design, optimization and production troubleshooting.',
      'Prepared technical documentation and implementation guides for future enhancements.'
    ]
  }
]

const projects = [
  {
    title: 'Payout Automation Platform',
    kicker: 'FINTECH · HIGH VOLUME',
    description: 'Bulk-transfer processing, real-time status tracking, provider integrations, role-based access and multi-level approval workflows for high-volume financial operations.',
    tags: ['Laravel', 'REST APIs', 'RBAC', 'MySQL'],
    metric: '20K+ daily transactions'
  },
  {
    title: 'Currency Exchange & Cross-Border Platform',
    kicker: 'FINTECH · MULTI-CURRENCY',
    description: 'Multi-currency transaction workflows spanning deposits, withdrawals, verification, approvals, user accounts and currency-specific configurations.',
    tags: ['Laravel', 'APIs', 'MySQL', 'Security'],
    metric: 'End-to-end transaction lifecycle'
  },
  {
    title: 'Payroll Management System',
    kicker: 'ENTERPRISE · HRMS',
    description: 'Salary processing, tax calculations, attendance-driven payroll workflows and compliance reporting for enterprise HR operations.',
    tags: ['Laravel', 'Vue.js', 'Payroll', 'Reporting'],
    metric: 'Payroll + compliance workflows'
  },
  {
    title: 'Multi-Company Report Hub',
    kicker: 'ENTERPRISE · ANALYTICS',
    description: 'Centralized reporting platform with role-based access controls for multi-company operational visibility and secure data access.',
    tags: ['Laravel', 'Reporting', 'RBAC', 'MySQL'],
    metric: 'Centralized multi-company reporting'
  }
]

const stats = [
  ['3+', 'Years Experience'],
  ['20K+', 'Daily Transactions'],
  ['99.9%', 'Platform Uptime'],
  ['2', 'Fintech Companies']
]

const onScroll = () => { scrolled.value = window.scrollY > 24 }
onMounted(() => window.addEventListener('scroll', onScroll))
onUnmounted(() => window.removeEventListener('scroll', onScroll))

const goTo = (id) => {
  document.getElementById(id.toLowerCase())?.scrollIntoView({ behavior: 'smooth' })
  menuOpen.value = false
}
</script>

<template>
  <div class="site-shell">
    <div class="ambient ambient-one"></div>
    <div class="ambient ambient-two"></div>

    <header :class="['navbar', { scrolled }]">
      <a class="brand" href="#home" @click.prevent="goTo('home')">
        <img class="profile-img" src="/profile.jpeg" alt="Keerthana R" />
        <span class="brand-copy">Keerthana R</span>
      </a>

      <nav class="desktop-nav">
        <button v-for="item in navItems" :key="item" @click="goTo(item)">{{ item }}</button>
      </nav>

      <div class="nav-actions">
        <a class="resume-link" href="/Keerthana_R.pdf" target="_blank">Resume ↗</a>
        <button class="menu-btn" @click="menuOpen = !menuOpen" aria-label="Toggle menu">☰</button>
      </div>

      <div v-if="menuOpen" class="mobile-nav">
        <button v-for="item in navItems" :key="item" @click="goTo(item)">{{ item }}</button>
      </div>
    </header>

    <main>
      <section id="home" class="hero section-wrap">
        <div class="hero-copy">
          <p class="eyebrow"><span class="pulse"></span> Available for impactful software opportunities</p>
          <h1>
            I build reliable<br />
            <span>fintech & enterprise</span><br />
            software products.
          </h1>
          <p class="hero-text">
            Senior Software Developer with 3+ years of experience building scalable payout,
            money-transfer, currency-exchange, payroll and reporting platforms using Laravel,
            React.js and Vue.js.
          </p>
          <div class="hero-actions">
            <button class="primary-btn" @click="goTo('Projects')">Explore my work <span>↘</span></button>
            <a class="secondary-btn" href="mailto:keerthanaravindran301@gmail.com">Let’s connect</a>
          </div>
          <div class="social-row">
            <a href="https://github.com/Keerthana301" target="_blank">GitHub ↗</a>
            <a href="https://linkedin.com/in/keerthana-r-3003871bb" target="_blank">LinkedIn ↗</a>
            <span>Chennai, India</span>
          </div>
        </div>

        <div class="hero-card-wrap">
          <div class="code-card">
            <div class="code-top"><span></span><span></span><span></span><small>developer.profile</small></div>
            <pre><code><span class="muted">const</span> developer = {
  name: <span class="accent">"Keerthana R"</span>,
  role: <span class="accent">"Senior Software Developer"</span>,
  stack: [
    <span class="accent">"Laravel"</span>, <span class="accent">"Vue.js"</span>,
    <span class="accent">"React.js"</span>, <span class="accent">"MySQL"</span>
  ],
  focus: <span class="accent">"Fintech + Enterprise"</span>,
  quality: <span class="accent">"Scalable & Secure"</span>
}</code></pre>
            <div class="code-status"><span class="pulse"></span> shipping dependable products</div>
          </div>
        </div>
      </section>

      <section class="stats section-wrap">
        <div v-for="([value, label], i) in stats" :key="label" class="stat-card">
          <span class="stat-index">0{{ i + 1 }}</span>
          <strong>{{ value }}</strong>
          <small>{{ label }}</small>
        </div>
      </section>

      <section id="about" class="content-section section-wrap split-section">
        <div class="section-label"><span>01</span> ABOUT</div>
        <div class="section-body about-grid">
          <div>
            <h2>Engineering software that works at real-world scale.</h2>
          </div>
          <div class="about-copy">
            <p>
              My work sits at the intersection of backend engineering, API integrations,
              secure transaction workflows and modern web interfaces. I enjoy converting complex
              operational requirements into maintainable systems that teams can confidently run in production.
            </p>
            <p>
              My experience includes payment automation, money transfer, currency exchange,
              payroll, reporting, secure authentication, database optimization and complete SDLC delivery.
            </p>
            <div class="mini-tags">
              <span>API Integrations</span><span>Secure Authentication</span><span>Database Optimization</span><span>Production Support</span>
            </div>
          </div>
        </div>
      </section>

      <section id="skills" class="content-section section-wrap split-section">
        <div class="section-label"><span>02</span> SKILLS</div>
        <div class="section-body">
          <div class="section-heading-row">
            <h2>Technical toolkit</h2>
            <p>Tools and technologies I use to take products from requirement to production.</p>
          </div>
          <div class="skill-grid">
            <article v-for="(skill, index) in skills" :key="skill.group" class="skill-card">
              <div class="skill-no">0{{ index + 1 }}</div>
              <h3>{{ skill.group }}</h3>
              <div class="tag-cloud"><span v-for="item in skill.items" :key="item">{{ item }}</span></div>
            </article>
          </div>
        </div>
      </section>

      <section id="experience" class="content-section section-wrap split-section">
        <div class="section-label"><span>03</span> EXPERIENCE</div>
        <div class="section-body">
          <h2>Building production systems across fintech and enterprise software.</h2>
          <div class="timeline">
            <article v-for="item in experience" :key="item.company" class="timeline-item">
              <div class="timeline-meta"><span>{{ item.period }}</span></div>
              <div class="timeline-content">
                <h3>{{ item.role }}</h3>
                <p class="company">{{ item.company }}</p>
                <ul>
                  <li v-for="point in item.points" :key="point">{{ point }}</li>
                </ul>
              </div>
            </article>
          </div>
        </div>
      </section>

      <section id="projects" class="content-section section-wrap split-section">
        <div class="section-label"><span>04</span> PROJECTS</div>
        <div class="section-body">
          <div class="section-heading-row">
            <h2>Selected work</h2>
            <p>Projects that reflect my experience with transaction-heavy, secure and operationally critical systems.</p>
          </div>
          <div class="project-grid">
            <article v-for="(project, index) in projects" :key="project.title" class="project-card">
              <div class="project-top">
                <span>{{ project.kicker }}</span>
                <strong>0{{ index + 1 }}</strong>
              </div>
              <h3>{{ project.title }}</h3>
              <p>{{ project.description }}</p>
              <div class="project-metric">{{ project.metric }}</div>
              <div class="project-tags"><span v-for="tag in project.tags" :key="tag">{{ tag }}</span></div>
            </article>
          </div>
        </div>
      </section>

      <section id="education" class="content-section section-wrap split-section">
        <div class="section-label"><span>05</span> EDUCATION</div>
        <div class="section-body education-layout">
          <div class="education-column">
            <h2>Education</h2>
            <article class="education-card">
              <span>IN PROGRESS</span>
              <h3>M.Tech, Computer Science and Information Security</h3>
            </article>
            <article class="education-card">
              <span>2019 — 2023</span>
              <h3>B.E., Computer Science and Engineering</h3>
              <p>Grade: 8.93 / 10</p>
            </article>
          </div>
          <div class="education-column">
            <h2>Certifications & recognition</h2>
            <ul class="cert-list">
              <li>Google Data Analytics Professional Certificate — Coursera</li>
              <li>Data Analytics and ChatGPT in Analysis — Simplilearn</li>
              <li>Virtual Internship in Data Analytics & Visualization — Accenture (Forage)</li>
              <li>NPTEL Enthusiast Star Award recipient</li>
              <li>Presented research work at the NCVCS International Conference</li>
            </ul>
          </div>
        </div>
      </section>

      <section id="contact" class="contact section-wrap">
        <div class="contact-inner">
          <p class="eyebrow">LET’S BUILD SOMETHING USEFUL</p>
          <h2>Have a role, project or collaboration in mind?</h2>
          <p>I’m open to opportunities where I can build scalable, secure and meaningful software products.</p>
          <div class="contact-actions">
            <a class="primary-btn" href="mailto:keerthanaravindran301@gmail.com">keerthanaravindran301@gmail.com <span>↗</span></a>
            <a class="secondary-btn" href="/Keerthana_R.pdf" target="_blank">View resume</a>
          </div>
        </div>
      </section>
    </main>

    <footer class="section-wrap footer">
      <span>© 2026 Keerthana R</span>
      <span>Senior Software Developer · Chennai, India</span>
    </footer>
  </div>
</template>

<style scoped>
.brand { display: flex; align-items: center; gap: 0.6rem; }
.brand a, .brand { text-decoration: none; }
.brand .profile-img { width: 44px; height: 44px; border-radius: 50%; object-fit: cover; display: inline-block; border: 2px solid rgba(255,255,255,.06); box-shadow: 0 6px 18px rgba(2,6,10,.55); transition: transform .18s ease, box-shadow .18s ease; }
.brand:hover .profile-img, .brand:focus .profile-img { transform: translateY(-2px); box-shadow: 0 10px 30px rgba(2,6,10,.6); }
.brand .brand-copy { margin-left: 0.25rem; display: inline-block; font-weight: 700; letter-spacing: -0.01em; }
.brand { cursor: pointer; }
.brand:focus { outline: none; }
</style>
