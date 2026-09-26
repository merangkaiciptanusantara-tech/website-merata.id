<script setup>
import { computed, onMounted, ref } from 'vue'

const isMenuOpen = ref(false)
const submitted = ref(false)
const theme = ref('light')
const assetBase = import.meta.env.BASE_URL
const form = ref({ name: '', email: '', service: '' })
const isDark = computed(() => theme.value === 'dark')
const services = [
  { number: '01', title: 'Web Development', category: 'SOFTWARE HOUSE', description: 'Website dan aplikasi web yang dibangun untuk kebutuhan nyata bisnismu—cepat, responsif, dan siap berkembang.', image: 'https://images.unsplash.com/photo-1460925895917-afdab827c52f?auto=format&fit=crop&w=1100&q=85', icon: '↗' },
  { number: '02', title: 'UI/UX Design', category: 'PRODUCT DESIGN', description: 'Pengalaman digital yang mudah dipahami, nyaman digunakan, dan terasa konsisten dengan brand kamu.', image: 'https://images.unsplash.com/photo-1558655146-9f40138edfeb?auto=format&fit=crop&w=1100&q=85', icon: '✳' },
  { number: '03', title: 'Jasa Push Followers', category: 'SOCIAL MEDIA', description: 'Dukungan pertumbuhan followers untuk membantu memperluas jangkauan dan membangun bukti sosial akunmu.', image: 'https://images.unsplash.com/photo-1611162617474-5b21e879e113?auto=format&fit=crop&w=1100&q=85', icon: '＋' },
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

function submitForm() {
  submitted.value = true
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

      <section class="ticker" aria-label="Layanan utama"><div class="ticker-track"><div class="ticker-group"><span>WEB DEVELOPMENT</span><b>✳</b><span>UI/UX DESIGN</span><b>✳</b><span>SOCIAL MEDIA GROWTH</span><b>✳</b><span>SOFTWARE HOUSE</span><b>✳</b></div><div class="ticker-group" aria-hidden="true"><span>WEB DEVELOPMENT</span><b>✳</b><span>UI/UX DESIGN</span><b>✳</b><span>SOCIAL MEDIA GROWTH</span><b>✳</b><span>SOFTWARE HOUSE</span><b>✳</b></div></div></section>

      <section id="services" class="services section-pad">
        <div class="section-heading">
          <div><p class="eyebrow">01 / YANG KAMI KERJAKAN</p><h2>Solusi digital<br /><em>yang berarti.</em></h2></div>
          <p class="heading-note">Dari ide pertama hingga siap bertumbuh, kami merancang solusi yang pas untuk langkah berikutnya.</p>
        </div>
        <div class="service-cards">
          <article v-for="service in services" :key="service.number" class="service-card">
            <div class="card-image"><img :src="service.image" :alt="service.title" loading="lazy" /><span class="service-number">{{ service.number }}</span><span class="card-icon">{{ service.icon }}</span></div>
            <div class="card-content"><span class="service-tag">{{ service.category }}</span><h3>{{ service.title }}</h3><p>{{ service.description }}</p><button class="card-link" @click="scrollTo('contact')">Diskusikan layanan <span>↗</span></button></div>
          </article>
        </div>
      </section>

      <section id="process" class="process section-pad">
        <div class="process-intro"><p class="eyebrow">02 / CARA KAMI BEKERJA</p><h2>Jelas dari<br /><em>awal.</em></h2><p>Kolaborasi yang baik dimulai dengan mendengarkan, lalu bergerak bersama.</p></div>
        <div class="steps"><article v-for="step in steps" :key="step.number" class="step"><span class="step-number">{{ step.number }}</span><div><h3>{{ step.title }}</h3><p>{{ step.description }}</p></div><span class="step-arrow">↗</span></article></div>
      </section>

      <section id="contact" class="contact section-pad">
        <div class="contact-copy"><p class="eyebrow">03 / MULAI SESUATU</p><h2>Ada ide?<br /><em>Ayo wujudkan.</em></h2><p class="friendly-note">Ceritakan kebutuhan web, UI/UX, atau pertumbuhan media sosialmu. Kami siap mendengarkan.</p>
          <div class="social-links"><a href="https://wa.me/6285794909132" target="_blank" rel="noreferrer"><span>WhatsApp</span><strong>Chat sekarang ↗</strong></a><a href="https://www.instagram.com/merata.id/" target="_blank" rel="noreferrer"><span>Instagram</span><strong>@merata.id ↗</strong></a><a href="https://www.tiktok.com/@merata.id" target="_blank" rel="noreferrer"><span>TikTok</span><strong>@merata.id ↗</strong></a></div>
        </div>
        <form class="contact-form" @submit.prevent="submitForm">
          <template v-if="!submitted"><p class="form-heading">Ceritakan rencanamu<span>✳</span></p><label>Nama<input v-model="form.name" required type="text" placeholder="Nama lengkap" /></label><label>Email<input v-model="form.email" required type="email" placeholder="nama@email.com" /></label><label>Layanan yang diminati<select v-model="form.service" required><option disabled value="">Pilih layanan</option><option>Web Development</option><option>UI/UX Design</option><option>Jasa Push Followers</option></select></label><button class="button-primary submit-button" type="submit">Kirim brief <span>↗</span></button></template>
          <div v-else class="success-state"><span class="success-icon">✓</span><h3>Terima kasih, {{ form.name }}.</h3><p>Brief kamu sudah kami terima. Silakan lanjutkan percakapan melalui WhatsApp.</p><a href="https://wa.me/6285794909132" target="_blank" rel="noreferrer">Buka WhatsApp ↗</a></div>
        </form>
      </section>
    </main>

    <footer class="footer section-pad"><div class="footer-top"><a class="brand footer-brand" href="#top" @click.prevent="scrollTo('top')"><img :src="`${assetBase}${isDark ? 'merangkai-cipta-nusantara-dark.png' : 'merangkai-cipta-nusantara.png'}`" alt="Merangkai Cipta Nusantara" /></a><p>Software House<br />Adiwerna · Tegal · Jawa Tengah</p><button class="back-top" @click="scrollTo('top')">Kembali ke atas ↑</button></div><div class="footer-bottom"><span>© {{ new Date().getFullYear() }} Merangkai Cipta Nusantara</span><span>Merangkai ide. Mencipta kemungkinan.</span></div></footer>
  </div>
</template>
