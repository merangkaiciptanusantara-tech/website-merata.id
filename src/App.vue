<script setup>
import { computed, onMounted, ref } from 'vue'

const isMenuOpen = ref(false)
const theme = ref('light')
const activeProjectCategory = ref('websites')
const assetBase = import.meta.env.BASE_URL
const isDark = computed(() => theme.value === 'dark')

const services = [
  { number: '01', title: 'Web Development', category: 'DIGITAL PRODUCT', description: 'Website cepat, responsif, dan mudah dikembangkan sesuai kebutuhan bisnismu.', icon: '↗', image: `${assetBase}layanan/web-development.svg`, imageAlt: 'Ilustrasi pengembangan website' },
  { number: '02', title: 'UI/UX Design', category: 'PRODUCT DESIGN', description: 'Alur dan antarmuka yang jelas agar produk terasa mudah digunakan.', icon: '✳', image: `${assetBase}layanan/ui-ux-design.svg`, imageAlt: 'Ilustrasi proses desain UI dan UX' },
  { number: '03', title: 'Mobile Apps', category: 'MOBILE APPLICATION', description: 'Aplikasi mobile untuk mendekatkan layananmu kepada pengguna.', icon: '▣', image: `${assetBase}layanan/mobile-apps.svg`, imageAlt: 'Ilustrasi aplikasi pada ponsel' },
  { number: '04', title: 'Graphic Design', category: 'VISUAL IDENTITY', description: 'Identitas dan materi visual yang konsisten untuk berbagai kanal.', icon: '◉', image: `${assetBase}layanan/graphic-design.svg`, imageAlt: 'Ilustrasi proses desain grafis' },
  { number: '05', title: 'API & Integrasi', category: 'SYSTEM INTEGRATION', description: 'Menghubungkan aplikasi dan layanan agar data bekerja bersama.', icon: '⌘', image: `${assetBase}layanan/api-integrasi.svg`, imageAlt: 'Ilustrasi integrasi antarsistem' },
  { number: '06', title: 'Digital Growth', category: 'SOCIAL MEDIA', description: 'Dukungan digital untuk membantu brand menjangkau lebih banyak orang.', icon: '◎', image: `${assetBase}layanan/digital-growth.svg`, imageAlt: 'Ilustrasi pertumbuhan jangkauan digital' },
]

const websiteProjects = [
  { name: 'Amanah Citra Cemerlang', type: 'COMPANY PROFILE · WEB DEVELOPMENT', domain: 'amanahcitracemerlang.id', url: 'https://amanahcitracemerlang.id/', preview: `${assetBase}portofolio/web1.png`, summary: 'Website profil dan informasi program LPK ACC Japan Centre.' },
  { name: 'Garuda Mestakung Indonesia', type: 'EDUCATION · WEB DEVELOPMENT', domain: 'garudamestakungindonesia.my.id', url: 'https://garudamestakungindonesia.my.id/', preview: `${assetBase}portofolio/web2.png`, summary: 'Website LPK GMI untuk mengenalkan program pelatihan dan kerja ke Jepang.' },
  { name: 'Rakerda Jateng 2025', type: 'EVENT · WEB DEVELOPMENT', domain: 'rakerdajateng2025.my.id', url: 'https://rakerdajateng2025.my.id/', preview: `${assetBase}portofolio/web3.jpeg`, summary: 'Website informasi dan pendaftaran peserta Rakerda PD IAI Jateng Tahun 2025.' },
  { name: 'TPQ Al Istiqomah & MDTA Hidayatul Ulum Talang', type: 'EDUCATION · WEB DEVELOPMENT', domain: 'TPQ AL ISTIQOMAH · TALANG', preview: `${assetBase}portofolio/web4.png`, summary: 'Website TPQ Al Istiqomah dan MDTA Hidayatul Ulum Talang.' },
  { name: 'Sistem E-Repo', type: 'INFORMATION SYSTEM · WEB DEVELOPMENT', domain: 'PORTOFOLIO WEBSITE · 05', preview: `${assetBase}portofolio/web5.jpg`, summary: 'Dashboard untuk mengelola data manajerial, berkas, paket kuesioner, pengguna, dan laporan.' },
  { name: 'Fit Work & Rampcheck Mayasari Bakti', type: 'INTERNAL SYSTEM · WEB DEVELOPMENT', domain: 'PORTOFOLIO WEBSITE · 06', preview: `${assetBase}portofolio/web6.png`, summary: 'Antarmuka sistem Fit Work & Rampcheck untuk pemeriksaan kendaraan dan operasional.' },
  { name: 'Tegal Learning Center', type: 'EDUCATION · WEB DEVELOPMENT', domain: 'PORTOFOLIO WEBSITE · 07', preview: `${assetBase}portofolio/web7.jpg`, summary: 'Website Tegal Learning Center dengan tampilan yang menyesuaikan berbagai perangkat.' },
  { name: 'Todo List Application — Poltek Harber', type: 'CAMPUS SYSTEM · WEB DEVELOPMENT', domain: 'PORTOFOLIO WEBSITE · 08', preview: `${assetBase}portofolio/web8.png`, summary: 'Halaman masuk aplikasi daftar tugas untuk membantu pengguna mengelola aktivitas.' },
  { name: 'Aplikasi Surat Desa Bongkok', type: 'VILLAGE INFORMATION SYSTEM · WEB DEVELOPMENT', domain: 'PORTOFOLIO WEBSITE · 09', preview: `${assetBase}portofolio/web9.png`, summary: 'Dashboard administrasi surat desa dengan pengelolaan surat dan data penduduk.' },
  { name: 'EPIN PHB — Ensiklopedia Pintar', type: 'EDUCATION · WEB DEVELOPMENT', domain: 'PORTOFOLIO WEBSITE · 10', preview: `${assetBase}portofolio/web10.png`, summary: 'Website edukasi anak untuk mengenal buah melalui konten interaktif dan ilustrasi ceria.' },
  { name: 'Klasifikasi Jenis Air Laut', type: 'EDUCATION · WEB DEVELOPMENT', domain: 'PORTOFOLIO WEBSITE · 11', preview: `${assetBase}portofolio/web11.png`, summary: 'Website informasi tentang proses penyulingan air laut menjadi air tawar.' },
  { name: 'Daya Angkut', type: 'CALCULATION SYSTEM · WEB DEVELOPMENT', domain: 'PORTOFOLIO WEBSITE · 12', preview: `${assetBase}portofolio/web12.png`, summary: 'Dashboard untuk menghitung daya angkut kendaraan seperti pikap, truk, bus, dan angkot.' },
]

const graphicDesignProjects = [
  { name: 'Erlangga Goes to Campus', type: 'EDUCATIONAL CAMPAIGN', preview: `${assetBase}portofolio/desain1.jpg`, summary: 'Poster kampanye belajar dari rumah yang mengajak pelajar tetap produktif.' },
  { name: 'Say No to Drugs', type: 'PUBLIC AWARENESS INFOGRAPHIC', preview: `${assetBase}portofolio/desain2.jpg`, summary: 'Infografik edukasi tentang dampak narkoba bagi kesehatan dan masa depan.' },
  { name: 'I Love Bali', type: 'ILLUSTRATION', preview: `${assetBase}portofolio/desain3.jpg`, summary: 'Ilustrasi karakter dengan busana tradisional Bali dalam desain bertema budaya.' },
  { name: 'E-PIN Seri Buah', type: 'CHILDREN’S BOOK COVER', preview: `${assetBase}portofolio/desain4.jpg`, summary: 'Sampul buku edukasi anak untuk mengenal beragam buah melalui ilustrasi ceria.' },
  { name: 'Landing Page Mix Ceker Sayap', type: 'FOOD PROMOTION · WEB VISUAL', preview: `${assetBase}portofolio/desain5.jpg`, summary: 'Visual promosi website kuliner untuk memperkenalkan menu dan mendorong pemesanan.' },
  { name: 'Glint Creative Website', type: 'WEBSITE VISUAL CONCEPT', preview: `${assetBase}portofolio/desain6.jpg`, summary: 'Konsep website agensi kreatif bernuansa gelap untuk desktop dan perangkat mobile.' },
  { name: 'Desa Digital', type: 'MOBILE APP PROMOTION', preview: `${assetBase}portofolio/desain7.jpg`, summary: 'Visual aplikasi desa digital untuk berita, wisata, dan layanan administrasi.' },
  { name: 'Liberty Koi Center', type: 'WEBSITE VISUAL CONCEPT', preview: `${assetBase}portofolio/desain8.jpg`, summary: 'Konsep website pusat koi dengan katalog ikan, galeri, edukasi, dan testimoni.' },
  { name: 'AHA Food', type: 'FOOD PROMOTION · WEB VISUAL', preview: `${assetBase}portofolio/desain10.jpg`, summary: 'Desain promosi AHA Food yang menonjolkan menu, identitas brand, dan ajakan memesan.' },
  { name: 'Rihanturisma', type: 'TOURISM WEBSITE VISUAL', preview: `${assetBase}portofolio/desain11.jpg`, summary: 'Konsep website pariwisata dengan informasi mitra, galeri, dan peta lokasi.' },
  { name: 'Alur Pembuatan Website', type: 'PROCESS INFOGRAPHIC', preview: `${assetBase}portofolio/desain12.jpg`, summary: 'Infografik alur proyek website dari analisis kebutuhan hingga serah terima.' },
  { name: 'Company Profile Invation Tech', type: 'COMPANY PROFILE · PRINT DESIGN', preview: `${assetBase}portofolio/desain13.jpg`, summary: 'Brosur profil layanan teknologi yang memadukan layanan, identitas brand, dan kontak.' },
  { name: 'PHB — The True Vocational Campus', type: 'CAMPUS ILLUSTRATION', preview: `${assetBase}portofolio/desain14.jpg`, summary: 'Ilustrasi gedung kampus dan mahasiswa untuk materi promosi Politeknik Harapan Bersama.' },
]

const uiuxProjects = [
  { name: 'Website Invation Tech', type: 'UI/UX DESIGN · WEB', preview: `${assetBase}portofolio/uiux1.png`, summary: 'Rancangan website agensi teknologi yang merangkum profil, layanan, portofolio, dan formulir kontak.' },
]

const appProjects = [
  { name: 'Movielas', type: 'MOBILE APPLICATION · CONCEPT', preview: `${assetBase}portofolio/aplikasi1.jpg`, summary: 'Konsep aplikasi hiburan dengan pengenalan suara, rekomendasi, dan alur akun pengguna.' },
  { name: 'SIMOLANG — Sistem Monitoring E-Tilang', type: 'MOBILE APPLICATION · CONCEPT', preview: `${assetBase}portofolio/aplikasi2.jpg`, summary: 'Konsep aplikasi e-tilang dengan riwayat, unggah gambar, login, registrasi, dan chatbot Simo.' },
]

const projectGroups = [
  { id: 'websites', title: 'Website', shortTitle: 'Web', kicker: '01 / WEB DEVELOPMENT', projects: websiteProjects, description: 'Website dan sistem digital yang dibangun untuk kebutuhan nyata.' },
  { id: 'graphic-design', title: 'Graphic Design', shortTitle: 'Graphic Design', kicker: '02 / VISUAL DESIGN', projects: graphicDesignProjects, description: 'Identitas visual, ilustrasi, materi promosi, dan desain editorial.' },
  { id: 'uiux', title: 'UI/UX Design', shortTitle: 'UI/UX', kicker: '03 / PRODUCT DESIGN', projects: uiuxProjects, description: 'Rancangan pengalaman dan antarmuka yang mudah dipahami.' },
  { id: 'applications', title: 'Aplikasi', shortTitle: 'Aplikasi', kicker: '04 / MOBILE APPLICATION', projects: appProjects, description: 'Konsep aplikasi mobile yang dirancang untuk kebutuhan penggunanya.' },
]

const activeProjects = computed(() => projectGroups.find((group) => group.id === activeProjectCategory.value)?.projects ?? [])
const activeProjectGroup = computed(() => projectGroups.find((group) => group.id === activeProjectCategory.value) ?? projectGroups[0])
const totalProjects = computed(() => projectGroups.reduce((total, group) => total + group.projects.length, 0))

const steps = [
  { number: '01', title: 'Dengar & pahami', description: 'Kita mulai dengan tujuan, kebutuhan, dan tantangan proyekmu.' },
  { number: '02', title: 'Rancang solusi', description: 'Kami susun arah visual dan solusi yang sesuai kebutuhan.' },
  { number: '03', title: 'Bangun & bertumbuh', description: 'Solusi diluncurkan, dievaluasi, lalu siap dikembangkan.' },
]

function scrollTo(id) {
  isMenuOpen.value = false
  document.getElementById(id)?.scrollIntoView({ behavior: 'smooth' })
}

function projectNumber(project, index) {
  const filename = project.preview.split('/').pop()
  return String(filename?.match(/\d+/)?.[0] || index + 1).padStart(2, '0')
}

function toggleTheme() {
  theme.value = isDark.value ? 'light' : 'dark'
  try {
    localStorage.setItem('mcn-theme', theme.value)
  } catch {
    // Theme still works for this page view when browser storage is unavailable.
  }
}

onMounted(() => {
  try {
    const savedTheme = localStorage.getItem('mcn-theme')
    theme.value = savedTheme === 'dark' ? 'dark' : 'light'
  } catch {
    theme.value = 'light'
  }
})
</script>

<template>
  <div class="site-shell" :data-theme="theme">
    <header class="topbar">
      <a class="brand" href="#top" aria-label="Merangkai Cipta Nusantara" @click.prevent="scrollTo('top')">
        <img :src="`${assetBase}${isDark ? 'merata-id-logo-dark.png' : 'merata-id-logo.png'}`" alt="" />
        <span class="brand-text"><strong>merata.id</strong><small>Merangkai Cipta Nusantara</small></span>
      </a>
      <button class="menu-toggle" :aria-expanded="isMenuOpen" :aria-label="isMenuOpen ? 'Tutup navigasi' : 'Buka navigasi'" aria-controls="main-navigation" @click="isMenuOpen = !isMenuOpen">
        <span></span><span></span>
      </button>
      <nav id="main-navigation" class="nav-links" :class="{ open: isMenuOpen }" aria-label="Navigasi utama">
        <a href="#services" @click.prevent="scrollTo('services')">Layanan</a>
        <a href="#projects" @click.prevent="scrollTo('projects')">Portofolio</a>
        <a href="#process" @click.prevent="scrollTo('process')">Cara kerja</a>
        <button class="theme-toggle" :aria-label="isDark ? 'Aktifkan mode terang' : 'Aktifkan mode gelap'" :aria-pressed="isDark" @click="toggleTheme"><span>{{ isDark ? '☼' : '◐' }}</span></button>
        <button class="nav-cta" @click="scrollTo('contact')">Mulai proyek <span>↗</span></button>
      </nav>
    </header>

    <main id="top">
      <section class="hero section-pad">
        <div class="hero-copy">
          <p class="eyebrow"><span class="pulse-dot"></span> SOFTWARE HOUSE · TEGAL, INDONESIA</p>
          <h1>Ide bagus,<br /><em>jadi luar biasa.</em></h1>
          <p class="hero-intro">Kami merangkai ide menjadi website, aplikasi, dan pengalaman digital yang membantu bisnis bergerak maju.</p>
          <div class="hero-actions">
            <button class="button-primary" @click="scrollTo('projects')">Jelajahi karya <span>↗</span></button>
            <button class="button-text" @click="scrollTo('contact')">Ceritakan idemu</button>
          </div>
          <div class="hero-note"><span class="hero-note-mark">✳</span><span>Partner digital untuk ide yang ingin berkembang.</span></div>
        </div>
        <div class="hero-visual">
          <div class="hero-visual-label"><span>MCN / DIGITAL STUDIO</span><span>01 — 28</span></div>
          <div class="hero-main-image" aria-label="Animasi ilustrasi produk digital Merangkai Cipta Nusantara" role="img">
            <div class="studio-animation" aria-hidden="true">
              <div class="studio-glow"></div>
              <div class="studio-orbit studio-orbit-a"></div><div class="studio-orbit studio-orbit-b"></div>
              <div class="studio-window"><div class="studio-window-bar"><i></i><i></i><i></i><span>merata.id / digital studio</span></div><div class="studio-window-content"><div class="studio-window-copy"><span class="studio-kicker">IDE MENJADI NYATA</span><b>Build something<br /><em>meaningful.</em></b><span class="studio-line"></span><span class="studio-button"></span></div><div class="studio-window-art"><span class="studio-art-ring"></span><span class="studio-art-cube">?</span><span class="studio-art-dot"></span></div></div></div>
              <div class="studio-float studio-float-code"><span>{ }</span><b>Clean code</b><small>01 — 04</small></div>
              <div class="studio-float studio-float-design"><span>?</span><b>Thoughtful design</b></div>
              <div class="studio-status"><i></i> DIGITAL EXPERIENCES, MADE WITH CARE</div>
            </div>
          </div>
          <div class="hero-float-card hero-float-top"><span class="float-icon">✳</span><div><strong>Design that works.</strong><small>Dirancang untuk pengguna.</small></div></div>
          <div class="hero-float-card hero-float-bottom"><img :src="`${assetBase}portofolio/aplikasi2.jpg`" alt="" /><div><small>BUILT WITH PURPOSE</small><strong>Digital, terasa dekat.</strong></div></div>
          <span class="hero-orbit orbit-one"></span><span class="hero-orbit orbit-two"></span>
        </div>
        <div class="hero-scroll"><span>SCROLL UNTUK JELAJAHI</span><span>↓</span></div>
      </section>

      <section class="intro-strip section-pad" aria-label="Ringkasan portofolio">
        <p>Ide lokal.<br /><strong>Dampak digital.</strong></p>
        <div class="intro-stats"><div><strong>12<span>+</span></strong><small>Website</small></div><div><strong>13</strong><small>Visual design</small></div><div><strong>28</strong><small>Karya digital</small></div></div>
      </section>

      <section id="services" class="services section-pad">
        <div class="section-heading">
          <div><p class="eyebrow">01 / LAYANAN KAMI</p><h2>Solusi yang pas,<br /><em>dibuat sepenuh hati.</em></h2></div>
          <p class="heading-note">Dari ide awal hingga produk digital siap digunakan, kami bantu setiap langkahnya.</p>
        </div>
        <div class="service-grid">
          <article v-for="service in services" :key="service.number" class="service-card" :class="{ featured: service.number === '01' }">
            <div class="service-card-top"><span>{{ service.category }}</span><span class="service-icon">{{ service.icon }}</span></div>
            <div class="service-image"><img :src="service.image" :alt="service.imageAlt" loading="lazy" /></div>
            <span class="service-number">{{ service.number }}</span>
            <h3>{{ service.title }}</h3><p>{{ service.description }}</p>
            <button class="service-arrow" :aria-label="`Diskusikan ${service.title}`" @click="scrollTo('contact')">↗</button>
          </article>
        </div>
      </section>

      <section id="projects" class="projects section-pad">
        <div class="section-heading project-section-heading">
          <div><p class="eyebrow">02 / PORTOFOLIO</p><h2>Yang sudah<br /><em>kami rangkai.</em></h2></div>
          <p class="heading-note">Pilihan karya website, desain, UI/UX, dan aplikasi yang kami kerjakan bersama klien.</p>
        </div>
        <div class="project-tabs-wrap">
          <div class="project-tabs" role="group" aria-label="Kategori portofolio">
            <button v-for="group in projectGroups" :key="group.id" class="project-tab" :class="{ active: activeProjectCategory === group.id }" :aria-pressed="activeProjectCategory === group.id" @click="activeProjectCategory = group.id">
              <span>{{ group.shortTitle }}</span><small>{{ String(group.projects.length).padStart(2, '0') }}</small>
            </button>
          </div>
          <div class="project-tab-status"><span>{{ activeProjectGroup.kicker }}</span><span>{{ String(activeProjects.length).padStart(2, '0') }} KARYA</span></div>
        </div>
        <div class="project-panel" aria-live="polite">
          <div class="project-panel-intro"><h3>{{ activeProjectGroup.title }}</h3><p>{{ activeProjectGroup.description }}</p></div>
          <TransitionGroup name="project" tag="div" class="project-grid" :class="{ 'project-grid-single': activeProjects.length === 1 }">
            <article v-for="(project, index) in activeProjects" :key="project.name" class="project-card" :data-category="activeProjectCategory">
              <component :is="project.url ? 'a' : 'div'" class="project-preview" :href="project.url || undefined" :target="project.url ? '_blank' : undefined" :rel="project.url ? 'noreferrer' : undefined" :aria-label="project.url ? `Kunjungi website ${project.name}` : undefined">
                <div v-if="activeProjectCategory === 'websites'" class="browser-bar"><span class="browser-dots"><i></i><i></i><i></i></span><span>{{ project.domain }}</span><b v-if="project.url">↗</b></div>
                <div class="preview-screen"><div class="preview-index">{{ activeProjectGroup.shortTitle.toUpperCase() }} / {{ projectNumber(project, index) }}</div><img :src="project.preview" :alt="`Preview ${project.name}`" loading="lazy" @error="$event.target.style.display = 'none'" /><span class="preview-open">↗</span></div>
              </component>
              <div class="project-info"><div class="project-type">{{ project.type }}</div><h4>{{ project.name }}</h4><p>{{ project.summary }}</p><a v-if="project.url" class="project-link" :href="project.url" target="_blank" rel="noreferrer">Kunjungi website <span>↗</span></a><span v-else class="project-link-static">Project showcase <span>✳</span></span></div>
            </article>
          </TransitionGroup>
        </div>
      </section>

      <section id="process" class="process section-pad">
        <div class="process-heading"><p class="eyebrow">03 / CARA KAMI BEKERJA</p><h2>Kolaborasi yang<br /><em>terasa mudah.</em></h2><p>Langkah yang jelas, komunikasi terbuka, dan tujuan yang kita sepakati bersama.</p></div>
        <div class="process-grid"><article v-for="step in steps" :key="step.number" class="process-card"><div class="process-card-top"><span>{{ step.number }}</span><span>STEP</span></div><div class="process-mark">{{ step.number === '01' ? '↗' : step.number === '02' ? '✳' : '→' }}</div><h3>{{ step.title }}</h3><p>{{ step.description }}</p></article></div>
      </section>

      <section id="contact" class="contact section-pad">
        <div class="contact-panel">
          <div class="contact-copy"><p class="eyebrow"><span class="pulse-dot"></span> 04 / MULAI SESUATU</p><h2>Punya ide?<br /><em>Ayo wujudkan.</em></h2><p class="friendly-note">Ceritakan kebutuhan website, desain, atau aplikasi yang sedang kamu siapkan. Kita mulai dari obrolan sederhana.</p><a class="contact-whatsapp" href="https://wa.me/6285794909132?text=Halo%20Merangkai%20Cipta%20Nusantara%2C%20saya%20ingin%20konsultasi%20proyek." target="_blank" rel="noreferrer"><span>Mulai obrolan di WhatsApp</span><b>↗</b></a></div>
          <div class="contact-details"><span class="contact-details-label">TEMUKAN KAMI DI</span><a href="https://www.instagram.com/merata.id_/" target="_blank" rel="noreferrer"><span>Instagram</span><b>@merata.id ↗</b></a><a href="https://www.tiktok.com/@merata.id" target="_blank" rel="noreferrer"><span>TikTok</span><b>@merata.id ↗</b></a><div class="contact-location"><span class="location-dot"></span><span>Adiwerna, Tegal<br />Jawa Tengah, Indonesia</span></div></div>
          <span class="contact-decoration">✳</span>
        </div>
      </section>
    </main>

    <footer class="footer section-pad"><div class="footer-main"><a class="brand footer-brand" href="#top" @click.prevent="scrollTo('top')"><img :src="`${assetBase}${isDark ? 'merata-id-logo-dark.png' : 'merata-id-logo.png'}`" alt="" /><span class="brand-text"><strong>merata.id</strong><small>Merangkai Cipta Nusantara</small></span></a><p>Merangkai ide.<br /><strong>Mencipta kemungkinan.</strong></p><button class="back-top" @click="scrollTo('top')">Kembali ke atas ↑</button></div><div class="footer-bottom"><span>© {{ new Date().getFullYear() }} Merangkai Cipta Nusantara</span><span>WEB · DESIGN · DIGITAL</span></div></footer>
  </div>
</template>

