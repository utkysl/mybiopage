<template>
  <div class="page">
    <!-- Hero -->
    <section class="hero">
      <div class="avatar">
        <img v-if="avatarUrl" :src="avatarUrl" alt="Utku" />
        <div v-else class="avatar-placeholder"></div>
      </div>
      <h1 class="name">{{ bio.name }}</h1>
      <p class="tagline">{{ bio.tagline }}</p>

      <!-- Skills -->
      <div class="skills">
        <span
          v-for="s in skills"
          :key="s.label"
          class="badge"
          :style="{ background: s.color }"
        >
          {{ s.label }}
        </span>
      </div>

      <!-- Links -->
      <div class="links">
        <a v-if="bio.email" :href="bio.email" class="btn">📧 Email</a>
        <a v-if="bio.linkedin" :href="bio.linkedin" target="_blank" class="btn"
          >🔗 LinkedIn</a
        >
        <a v-if="bio.instagram" :href="bio.instagram" target="_blank" class="btn"
          >📸 Instagram</a
        >
        <a v-if="bio.github" :href="bio.github" target="_blank" class="btn">💻 GitHub</a>
      </div>
    </section>

    <!-- About -->
    <section class="card">
      <h2>📜 About Me</h2>
      <div v-html="formatMarkdown(bio.summary)"></div>
    </section>

<!-- Projects -->
<section class="card">
  <h2>💻 Some Projects</h2>
  <div class="projects-grid">
    <a
      v-for="p in projects"
      :key="p.title"
      :href="p.href"
      target="_blank"
      rel="noreferrer"
      class="project-card"
    >
      <div class="project-title">{{ p.title }}</div>
      <div class="project-desc">{{ p.desc }}</div>
    </a>
  </div>
</section>

<section class="card">
  <h2>🌍 Languages</h2>
  <div class="language-grid">
    <div v-for="l in languages" :key="l.name" class="language-card">
      <div class="language-name">
        <img :src="l.flag" alt="flag" class="flag-icon" /> {{ l.name }}
      </div>
      <div class="language-level">{{ l.level }}</div>
    </div>
  </div>
</section>


    <!-- Footer -->
    <footer class="footer">
      © {{ new Date().getFullYear() }} {{ bio.name }}. Built with ♥, math, and coffee.
    </footer>
  </div>
</template>

<script setup>
const avatarUrl = "/utku.jpeg";

const bio = {
  name: "Utku Yeşil",
  tagline: "🚀 Physics Engineering Student • Programmer • Lifelong Learner",
  summary: `The Intersection of Physics, Code, and Curiosity
Hello! I’m Utku Yeşil, a Physics Engineering student at Ankara University with a relentless drive to understand how the world—and everything in it—works. Whether it's the fundamental laws of the universe or the architecture of a complex codebase, I am driven by a passion for solving puzzles and building functional beauty.

🚀 Engineering & Software Development
My journey began with a childhood fascination for electronics, leading me to hands-on experimentation with Arduino and ESP8266. Today, I bridge the gap between hardware and software. I’m a Full-Stack Developer experienced in JavaScript (Node.js, Vue.js, React), C#, and Python, and I enjoy exploring digital worlds through Unity and Unreal Engine. Currently, I am channeling my entrepreneurial energy into "GoodJob", a service marketplace startup where I lead the technical development.

🌎 A Lifelong Polyglot Journey
I believe that learning a language is like installing a new operating system for the mind. I don’t just study languages; I immerse myself in them. I am currently focusing on:

English & German: Building professional and academic fluency to bridge my engineering career with global opportunities.

Japanese: Exploring the logic and unique aesthetics of the language.

🎸 Art, Discipline & Growth
I believe a great engineer is fueled by diverse perspectives and a disciplined lifestyle. When I’m not coding or studying physics, you’ll find me:

Music: Translating emotions into sound through the electric guitar and piano. I’m also an avid vinyl collector, always hunting for the next great-sounding record.

Finance: Navigating the complexities of personal finance and stock investments, applying analytical thinking to market trends.

Lifestyle: I’m a firm believer in the "Atomic Habits" philosophy—the idea that small, consistent improvements lead to massive results. Whether I’m cycling or mastering a new skill, I prioritize the 1% daily gain.

My Vision: To blend the analytical discipline of physics with the creative freedom of software and art to build tools that truly matter.`,

  github: "https://github.com/utkysl",
  email: "mailto:utkuyesil189@gmail.com",
  linkedin: "https://www.linkedin.com/in/utku-ye%C5%9Fil-095a79325/",
  instagram: "https://www.instagram.com/utqy2606/",
};

const skills = [
  { label: "Python", color: "#facc15" },
  { label: "JavaScript", color: "#fbbf24" },
  { label: "Node.js", color: "#16a34a" },
  { label: "Vue.js", color: "#22c55e" },
  { label: "C#", color: "#7e22ce" },
  { label: "Unity", color: "#0891b2" },
];

const projects = [
  {
    title: "Kanji Quiz App",
    desc: "React app for practicing Japanese kanji.",
    href: "https://kanjiquizapp.netlify.app/",
  },
  {
    title: "Smart House",
    desc: "IoT Project with Esp8266",
    href: "https://github.com/utkysl/akilli-ev-v1",
  },
  {
    title: "Weather App",
    desc: "Simple NodeJs Project",
    href: "https://github.com/utkysl/Nodejs-Weather-App",
  },
];

const languages = [
  { name: "Turkish", level: "Native", flag: "/flags/tr.svg" },
  { name: "English", level: "B1+ / B2 (improving)", flag: "/flags/gb.svg" },
  { name: "Japanese", level: "~N5 mid", flag: "/flags/jp.svg" },
  { name: "German", level: "Beginner", flag: "/flags/de.svg" }
];


function formatMarkdown(text) {
  return text.replace(/\*\*(.*?)\*\*/g, "<strong>$1</strong>").replace(/\n/g, "<br/>");
}
</script>

<style scoped>
.page {
  min-height: 100vh;
  background: linear-gradient(to bottom, #0f172a, #1e293b, #0f172a);
  color: #f1f5f9;
  padding: 20px;
  max-width: 900px;
  margin: auto;
}
.hero {
  text-align: center;
  padding: 40px 0;
}
.avatar img {
  width: 180px;
  height: 180px;
  border-radius: 50%;
  object-fit: cover;
  border: 3px solid #5e0c0cff;
}
.name {
  font-size: 28px;
  margin-top: 10px;
}
.tagline {
  font-size: 16px;
  color: #94a3b8;
  margin-bottom: 15px;
}
.skills {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 8px;
  margin: 15px 0;
}
.badge {
  padding: 6px 12px;
  border-radius: 8px;
  font-size: 13px;
  font-weight: bold;
  color: #000;
}
.links {
  margin-top: 15px;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 10px;
}
.btn {
  background: rgba(255, 255, 255, 0.1);
  padding: 6px 12px;
  border-radius: 8px;
  color: #f1f5f9;
  text-decoration: none;
  font-size: 14px;
}
.btn:hover {
  background: rgba(255, 255, 255, 0.2);
}
.card {
  background: rgba(255, 255, 255, 0.05);
  border-radius: 12px;
  padding: 20px;
  margin-bottom: 20px;
}
.languages {
  list-style: none;
  padding: 0;
}
.languages li {
  margin: 6px 0;
}
.footer {
  text-align: center;
  margin-top: 30px;
  font-size: 12px;
  color: #94a3b8;
}

.language-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
  gap: 12px;
  margin-top: 10px;
}

.language-card {
  background: rgba(255, 255, 255, 0.1);
  padding: 12px;
  border-radius: 10px;
  text-align: center;
  transition: transform 0.2s, background 0.2s;
}

.language-card:hover {
  transform: translateY(-3px);
  background: rgba(255, 255, 255, 0.2);
}

.language-name {
  font-weight: bold;
  margin-bottom: 4px;
}

.language-level {
  font-size: 13px;
  color: #cbd5e1;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 16px;
  margin-top: 12px;
}

.project-card {
  display: block;
  background: rgba(255, 255, 255, 0.05);
  border-radius: 12px;
  padding: 16px;
  text-decoration: none;
  color: #e2e8f0;
  transition: transform 0.2s, background 0.2s;
}

.project-card:hover {
  transform: translateY(-4px);
  background: rgba(255, 255, 255, 0.1);
}

.project-title {
  font-weight: bold;
  font-size: 16px;
  margin-bottom: 6px;
}

.project-desc {
  font-size: 14px;
  color: #cbd5e1;
}

.flag-icon {
  width: 20px;
  height: 14px;
  margin-right: 6px;
  vertical-align: middle;
}


</style>
