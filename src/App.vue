<script setup>
import { computed, onMounted, ref } from 'vue'

const isMenuOpen = ref(false)
const theme = ref('light')
const assetBase = import.meta.env.BASE_URL
const isDark = computed(() => theme.value === 'dark')
const services = [
  { number: '01', title: 'Web Development', category: 'SOFTWARE HOUSE', description: 'Website dan aplikasi web yang dibangun untuk kebutuhan nyata bisnismu—cepat, responsif, dan siap berkembang.', image: 'https://images.unsplash.com/photo-1460925895917-afdab827c52f?auto=format&fit=crop&w=1100&q=85', icon: '↗' },
  { number: '02', title: 'UI/UX Design', category: 'PRODUCT DESIGN', description: 'Pengalaman digital yang mudah dipahami, nyaman digunakan, dan terasa konsisten dengan brand kamu.', image: 'https://images.unsplash.com/photo-1558655146-9f40138edfeb?auto=format&fit=crop&w=1100&q=85', icon: '✳' },
  { number: '03', title: 'Mobile Apps Development', category: 'MOBILE APPLICATION', description: 'Aplikasi mobile yang dirancang untuk memudahkan pengguna dan mendukung kebutuhan bisnismu.', image: 'https://images.unsplash.com/photo-1512941937669-90a1b58e7e9c?auto=format&fit=crop&w=1100&q=85', icon: '↗' },
  { number: '04', title: 'Graphic Design', category: 'VISUAL IDENTITY', description: 'Materi visual yang konsisten dan menarik untuk memperkuat identitas brand di berbagai kanal.', image: 'https://images.unsplash.com/photo-1541701494587-cb58502866ab?auto=format&fit=crop&w=1100&q=85', icon: '✳' },
  { number: '05', title: 'API Service Development', category: 'API & INTEGRATION', description: 'API untuk menghubungkan website, aplikasi, dan layanan pihak ketiga agar data serta fitur dapat bekerja bersama.', image: 'https://images.unsplash.com/photo-1558494949-ef010cbdcc31?auto=format&fit=crop&w=1100&q=85', icon: '↔' },
  { number: '06', title: 'Push Like Follower', category: 'SOCIAL MEDIA', description: 'Layanan push like dan follower untuk membantu meningkatkan interaksi serta jangkauan akunmu.', image: 'https://images.unsplash.com/photo-1611162617474-5b21e879e113?auto=format&fit=crop&w=1100&q=85', icon: '＋' },
]
const projects = [
  { name: 'Amanah Citra Cemerlang', type: 'COMPANY PROFILE · WEB DEVELOPMENT', domain: 'amanahcitracemerlang.id', url: 'https://amanahcitracemerlang.id/', preview: `${assetBase}portofolio/web1.png`, summary: 'Website profil dan informasi program LPK ACC Japan Centre.' },
  { name: 'Garuda Mestakung Indonesia', type: 'EDUCATION · WEB DEVELOPMENT', domain: 'garudamestakungindonesia.my.id', url: 'https://garudamestakungindonesia.my.id/', preview: `${assetBase}portofolio/web2.png`, summary: 'Website LPK GMI untuk mengenalkan program pelatihan dan kerja ke Jepang.' },
  { name: 'Rakerda Jateng 2025', type: 'EVENT · WEB DEVELOPMENT', domain: 'rakerdajateng2025.my.id', url: 'https://rakerdajateng2025.my.id/', preview: `${assetBase}portofolio/web3.jpeg`, summary: 'Website informasi dan pendaftaran peserta Rakerda PD IAI Jateng Tahun 2025.' },
  { name: 'TPQ Al Istiqomah & MDTA Hidayatul Ulum Talang', type: 'EDUCATION · WEB DEVELOPMENT', domain: 'TPQ AL ISTIQOMAH · TALANG', preview: `${assetBase}portofolio/web4.png`, summary: 'Website TPQ Al Istiqomah dan MDTA Hidayatul Ulum Talang.' },
]
const steps = [
  { number: '01', title: 'Dengar & pahami', description: 'Kami mulai dari tujuan dan kebutuhanmu.' },
  { number: '02', title: 'Rancang solusi', description: 'Strategi dan detail disusun dengan jelas.' },
  { number: '03', title: 'Bangun & bertumbuh', description: 'Solusi diluncurkan dan siap dikembangkan.' },
]

function scrollTo(id) {
  isMenuOpen.value = false
  document.getElementById(id)?.scrollIntoView({ behavior: 'smooth' })
}

function toggleTheme() {
  theme.value = isDark.value ? 'light' : 'dark'
  localStorage.setItem('mcn-theme', theme.value)
}

onMounted(() => {
  const savedTheme = localStorage.getItem('mcn-theme')
  theme.value = savedTheme || (window.matchMedia('(prefers-color-scheme: dark)').matches ? 'dark' : 'light')
})
</script>

<template>
  <div class="site-shell" :data-theme="theme">
    <header class="topbar">
      <a class="brand" href="#top" aria-label="Merangkai Cipta Nusantara" @click.prevent="scrollTo('top')">
        <img :src="`${assetBase}${isDark ? 'merata-id-logo-dark.png' : 'merata-id-logo.png'}`" alt="merata.id" />
      </a>
      <button class="menu-toggle" :aria-expanded="isMenuOpen" :aria-label="isMenuOpen ? 'Tutup navigasi' : 'Buka navigasi'" aria-controls="main-navigation" @click="isMenuOpen = !isMenuOpen">
        <span></span><span></span>
      </button>
      <nav id="main-navigation" class="nav-links" :class="{ open: isMenuOpen }" aria-label="Navigasi utama">
        <a href="#services" @click.prevent="scrollTo('services')">Layanan</a>
        <a href="#projects" @click.prevent="scrollTo('projects')">Our Projects</a>
        <a href="#process" @click.prevent="scrollTo('process')">Cara kerja</a>
        <a href="#contact" @click.prevent="scrollTo('contact')">Kontak</a>
        <button class="theme-toggle" :aria-label="isDark ? 'Aktifkan mode terang' : 'Aktifkan mode gelap'" :aria-pressed="isDark" @click="toggleTheme">
          <span class="theme-icon">{{ isDark ? '☀' : '☾' }}</span><span>{{ isDark ? 'Terang' : 'Gelap' }}</span>
        </button>
        <button class="nav-cta" @click="scrollTo('contact')">Mulai proyek <span>↗</span></button>
      </nav>
    </header>

    <main id="top">
      <section class="hero section-pad">
        <div class="hero-copy">
          <p class="eyebrow"><span class="pulse-dot"></span> SOFTWARE HOUSE · DIGITAL GROWTH</p>
          <h1>Ide bagus.<br /><em>Jadi nyata.</em></h1>
          <p class="hero-intro">Merangkai Cipta Nusantara membantu bisnis membangun produk digital dan tumbuh lebih kuat di dunia online.</p>
          <div class="hero-actions">
            <button class="button-primary" @click="scrollTo('contact')">Ceritakan proyekmu <span>↗</span></button>
            <button class="button-text" @click="scrollTo('services')">Jelajahi layanan <span>↓</span></button>
          </div>
          <div class="hero-proof"><span class="proof-mark">✳</span><span>Partner digital untuk ide yang ingin berkembang.</span></div>
        </div>
        <div class="hero-art" aria-label="Identitas visual Merangkai Cipta Nusantara">
          <div class="art-glow"></div><div class="art-ring ring-one"></div><div class="art-ring ring-two"></div>
          <div class="art-card"><img :src="`${assetBase}${isDark ? 'merangkai-cipta-nusantara-dark.png' : 'merangkai-cipta-nusantara.png'}`" alt="Logo Merangkai Cipta Nusantara" /><span>DESIGN · BUILD · GROW</span></div>
          <span class="art-index index-top">MCN / 01</span><span class="art-index index-bottom">BUILT FOR WHAT'S NEXT</span>
          <span class="art-star">✳</span>
        </div>
        <div class="hero-bottom"><span>01 — 03</span><span>SCROLL TO EXPLORE ↓</span></div>
      </section>

      <section class="ticker" aria-label="Layanan utama"><div class="ticker-track"><div class="ticker-group"><span>WEB DEVELOPMENT</span><b>✳</b><span>UI/UX DESIGN</span><b>✳</b><span>MOBILE APPS</span><b>✳</b><span>GRAPHIC DESIGN</span><b>✳</b><span>API SERVICE</span><b>✳</b><span>PUSH LIKE FOLLOWER</span><b>✳</b></div><div class="ticker-group" aria-hidden="true"><span>WEB DEVELOPMENT</span><b>✳</b><span>UI/UX DESIGN</span><b>✳</b><span>MOBILE APPS</span><b>✳</b><span>GRAPHIC DESIGN</span><b>✳</b><span>API SERVICE</span><b>✳</b><span>PUSH LIKE FOLLOWER</span><b>✳</b></div></div></section>

      <section id="services" class="services section-pad">
        <div class="section-heading">
          <div><p class="eyebrow">01 / YANG KAMI KERJAKAN</p><h2>Solusi digital<br /><em>yang berarti.</em></h2></div>
          <p class="heading-note">Web, aplikasi mobile, desain visual, hingga layanan media sosial untuk membantu bisnismu melangkah maju.</p>
        </div>
        <div class="service-cards">
          <article v-for="service in services" :key="service.number" class="service-card">
            <div class="card-image"><img :src="service.image" :alt="service.title" loading="lazy" /><span class="service-number">{{ service.number }}</span><span class="card-icon">{{ service.icon }}</span></div>
            <div class="card-content"><span class="service-tag">{{ service.category }}</span><h3>{{ service.title }}</h3><p>{{ service.description }}</p><button class="card-link" @click="scrollTo('contact')">Diskusikan layanan <span>↗</span></button></div>
          </article>
        </div>
      </section>

      <section id="projects" class="projects section-pad">
        <div class="section-heading">
          <div><p class="eyebrow">02 / WEB DEVELOPMENT</p><h2>Our<br /><em>projects.</em></h2></div>
          <p class="heading-note">Beberapa website yang kami bangun untuk membantu brand dan acara hadir lebih kuat secara digital.</p>
        </div>
        <div class="project-grid">
          <article v-for="(project, index) in projects" :key="project.name" class="project-card">
            <a v-if="project.url" class="project-preview" :href="project.url" target="_blank" rel="noreferrer" :aria-label="`Lihat website ${project.name}`">
              <div class="browser-bar"><span class="browser-dots"><i></i><i></i><i></i></span><span class="browser-domain">{{ project.domain }}</span><span class="browser-open">↗</span></div>
              <div class="preview-screen"><div class="preview-fallback"><span>WEB PROJECT / 0{{ index + 1 }}</span><strong>{{ project.name }}</strong></div><img :src="project.preview" :alt="`Preview website ${project.name}`" loading="lazy" @error="$event.target.style.display = 'none'" /></div>
            </a>
            <div v-else class="project-preview">
              <div class="browser-bar"><span class="browser-dots"><i></i><i></i><i></i></span><span class="browser-domain">{{ project.domain }}</span></div>
              <div class="preview-screen"><div class="preview-fallback"><span>WEB PROJECT / 0{{ index + 1 }}</span><strong>{{ project.name }}</strong></div><img :src="project.preview" :alt="`Preview website ${project.name}`" loading="lazy" @error="$event.target.style.display = 'none'" /></div>
            </div>
            <div class="project-info"><span class="project-type">{{ project.type }}</span><h3>{{ project.name }}</h3><p>{{ project.summary }}</p><a v-if="project.url" class="project-link" :href="project.url" target="_blank" rel="noreferrer">Kunjungi website <span>↗</span></a></div>
          </article>
        </div>
      </section>

      <section id="process" class="process section-pad">
        <div class="process-intro"><p class="eyebrow">03 / CARA KAMI BEKERJA</p><h2>Jelas dari<br /><em>awal.</em></h2><p>Kolaborasi yang baik dimulai dengan mendengarkan, lalu bergerak bersama.</p></div>
        <div class="steps"><article v-for="step in steps" :key="step.number" class="step"><span class="step-number">{{ step.number }}</span><div><h3>{{ step.title }}</h3><p>{{ step.description }}</p></div><span class="step-arrow">↗</span></article></div>
      </section>

      <section id="contact" class="contact section-pad">
        <div class="contact-copy"><p class="eyebrow">04 / MULAI SESUATU</p><h2>Ada ide?<br /><em>Ayo wujudkan.</em></h2><p class="friendly-note">Ceritakan kebutuhan web, UI/UX, atau pertumbuhan media sosialmu. Kami siap mendengarkan.</p>
          <div class="social-links"><a href="https://wa.me/6285794909132" target="_blank" rel="noreferrer"><span>WhatsApp</span><strong>Chat sekarang ↗</strong></a><a href="https://www.instagram.com/merata.id_/" target="_blank" rel="noreferrer"><span>Instagram</span><strong>@merata.id ↗</strong></a><a href="https://www.tiktok.com/@merata.id" target="_blank" rel="noreferrer"><span>TikTok</span><strong>@merata.id ↗</strong></a></div>
        </div>
        <aside class="contact-card">
          <div class="contact-card-top"><span>SIAP MULAI PROYEK</span><span>MCN · 01</span></div>
          <div class="contact-card-orbit orbit-a"></div><div class="contact-card-orbit orbit-b"></div>
          <span class="contact-card-star">✳</span>
          <div class="contact-card-content"><span class="contact-card-kicker">Satu obrolan bisa jadi langkah pertama.</span><h3>Yuk, ceritakan<br />rencanamu.</h3><p>Hubungi tim kami langsung untuk konsultasi layanan dan kebutuhan proyekmu.</p><a class="contact-whatsapp" href="https://wa.me/6285794909132?text=Halo%20Merangkai%20Cipta%20Nusantara%2C%20saya%20ingin%20konsultasi%20proyek." target="_blank" rel="noreferrer"><span>Hubungi via WhatsApp</span><b>↗</b></a></div>
          <span class="contact-card-foot">WEB · APP · DESIGN · DIGITAL</span>
        </aside>
      </section>
    </main>

    <footer class="footer section-pad"><div class="footer-top"><a class="brand footer-brand" href="#top" @click.prevent="scrollTo('top')"><img :src="`${assetBase}${isDark ? 'merangkai-cipta-nusantara-dark.png' : 'merangkai-cipta-nusantara.png'}`" alt="Merangkai Cipta Nusantara" /></a><p>Software House<br />Adiwerna · Tegal · Jawa Tengah</p><button class="back-top" @click="scrollTo('top')">Kembali ke atas ↑</button></div><div class="footer-bottom"><span>© {{ new Date().getFullYear() }} Merangkai Cipta Nusantara</span><span>Merangkai ide. Mencipta kemungkinan.</span></div></footer>
  </div>
</template>
