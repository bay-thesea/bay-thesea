<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>bay-thesea — catatan kajian</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=DM+Sans:wght@300;400;500&family=Amiri:wght@400;700&display=swap" rel="stylesheet">
<style>
  :root {
    --sea:       #4a7c8e;
    --sea-light: #7bafc0;
    --sea-pale:  #ddeef3;
    --sage:      #6b8f71;
    --sage-light:#a8c4a2;
    --sage-pale: #e8f0e8;
    --sand:      #f7f3ed;
    --sand-dark: #ede5d8;
    --warm:      #c4956a;
    --warm-pale: #f5e9dc;
    --ink:       #2a2420;
    --ink-mid:   #5a4e46;
    --ink-light: #8a7e76;
    --white:     #fdfcfb;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--white);
    color: var(--ink);
    font-family: 'DM Sans', sans-serif;
    font-size: 15px;
    line-height: 1.7;
    overflow-x: hidden;
  }

  /* ── NAV ── */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 18px 48px;
    background: rgba(253,252,251,0.88);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid rgba(74,124,142,0.12);
  }

  .nav-logo {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.5rem;
    font-weight: 600;
    color: var(--sea);
    letter-spacing: 0.02em;
    text-decoration: none;
  }

  .nav-logo span { color: var(--sage); }

  .nav-links {
    display: flex;
    gap: 32px;
    list-style: none;
  }

  .nav-links a {
    font-size: 0.82rem;
    font-weight: 500;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    color: var(--ink-mid);
    text-decoration: none;
    transition: color 0.2s;
  }

  .nav-links a:hover { color: var(--sea); }

  /* ── HERO ── */
  .hero {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    padding: 120px 24px 80px;
    position: relative;
    overflow: hidden;
  }

  /* Layered wave background */
  .hero::before {
    content: '';
    position: absolute;
    inset: 0;
    background:
      radial-gradient(ellipse 80% 60% at 50% 110%, rgba(74,124,142,0.18) 0%, transparent 70%),
      radial-gradient(ellipse 60% 40% at 80% 20%, rgba(107,143,113,0.10) 0%, transparent 60%),
      radial-gradient(ellipse 40% 30% at 10% 60%, rgba(196,149,106,0.08) 0%, transparent 50%);
    pointer-events: none;
  }

  /* Floating circles */
  .hero-bubble {
    position: absolute;
    border-radius: 50%;
    pointer-events: none;
    animation: drift linear infinite;
  }

  .hero-bubble:nth-child(1) {
    width: 320px; height: 320px;
    top: -80px; right: -60px;
    background: radial-gradient(circle, rgba(123,175,192,0.15), transparent);
    animation-duration: 18s;
  }
  .hero-bubble:nth-child(2) {
    width: 200px; height: 200px;
    bottom: 80px; left: -40px;
    background: radial-gradient(circle, rgba(168,196,162,0.2), transparent);
    animation-duration: 22s; animation-delay: -8s;
  }
  .hero-bubble:nth-child(3) {
    width: 140px; height: 140px;
    top: 30%; right: 15%;
    background: radial-gradient(circle, rgba(196,149,106,0.12), transparent);
    animation-duration: 15s; animation-delay: -4s;
  }

  @keyframes drift {
    0%, 100% { transform: translateY(0px) rotate(0deg); }
    33% { transform: translateY(-18px) rotate(5deg); }
    66% { transform: translateY(10px) rotate(-3deg); }
  }

  .hero-eyebrow {
    font-size: 0.75rem;
    font-weight: 500;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: var(--sea);
    margin-bottom: 20px;
    opacity: 0;
    animation: fadeUp 0.9s ease forwards 0.2s;
  }

  .hero-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(3.5rem, 8vw, 6.5rem);
    font-weight: 300;
    line-height: 1.05;
    color: var(--ink);
    margin-bottom: 6px;
    opacity: 0;
    animation: fadeUp 0.9s ease forwards 0.4s;
  }

  .hero-title em {
    font-style: italic;
    color: var(--sea);
  }

  .hero-title .sage { color: var(--sage); }

  .hero-arabic {
    font-family: 'Amiri', serif;
    font-size: 1.6rem;
    color: var(--ink-light);
    margin: 16px 0 24px;
    opacity: 0;
    animation: fadeUp 0.9s ease forwards 0.6s;
  }

  .hero-desc {
    max-width: 480px;
    font-size: 0.95rem;
    color: var(--ink-mid);
    line-height: 1.8;
    margin-bottom: 40px;
    opacity: 0;
    animation: fadeUp 0.9s ease forwards 0.8s;
  }

  .hero-cta {
    display: flex;
    gap: 14px;
    justify-content: center;
    flex-wrap: wrap;
    opacity: 0;
    animation: fadeUp 0.9s ease forwards 1s;
  }

  .btn-primary {
    background: var(--sea);
    color: #fff;
    padding: 13px 32px;
    border-radius: 100px;
    font-size: 0.85rem;
    font-weight: 500;
    letter-spacing: 0.04em;
    text-decoration: none;
    transition: background 0.2s, transform 0.2s, box-shadow 0.2s;
    box-shadow: 0 4px 20px rgba(74,124,142,0.25);
  }

  .btn-primary:hover {
    background: #3d6a7a;
    transform: translateY(-2px);
    box-shadow: 0 8px 28px rgba(74,124,142,0.35);
  }

  .btn-secondary {
    background: transparent;
    color: var(--sage);
    padding: 13px 28px;
    border-radius: 100px;
    border: 1.5px solid var(--sage-light);
    font-size: 0.85rem;
    font-weight: 500;
    text-decoration: none;
    transition: all 0.2s;
  }

  .btn-secondary:hover {
    background: var(--sage-pale);
    transform: translateY(-2px);
  }

  /* wave divider */
  .wave-divider {
    width: 100%;
    overflow: hidden;
    line-height: 0;
    margin-top: -2px;
  }

  .wave-divider svg { display: block; width: 100%; }

  /* ── ABOUT STRIP ── */
  .about-strip {
    background: var(--sea);
    padding: 56px 48px;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 60px;
    flex-wrap: wrap;
  }

  .about-strip .arabic-big {
    font-family: 'Amiri', serif;
    font-size: 2.4rem;
    color: rgba(255,255,255,0.9);
    line-height: 1.6;
    text-align: right;
    direction: rtl;
    flex: 1;
    min-width: 260px;
  }

  .about-strip .about-text {
    flex: 1;
    min-width: 260px;
    max-width: 420px;
  }

  .about-strip .about-text h2 {
    font-family: 'Cormorant Garamond', serif;
    font-size: 2rem;
    font-weight: 400;
    color: #fff;
    margin-bottom: 12px;
    line-height: 1.3;
  }

  .about-strip .about-text p {
    color: rgba(255,255,255,0.78);
    font-size: 0.9rem;
    line-height: 1.8;
  }

  .about-strip .about-text .ref {
    font-size: 0.75rem;
    color: rgba(255,255,255,0.5);
    margin-top: 10px;
  }

  /* ── KAJIAN SECTION ── */
  .section {
    padding: 88px 48px;
    max-width: 1100px;
    margin: 0 auto;
  }

  .section-eyebrow {
    font-size: 0.72rem;
    font-weight: 500;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: var(--sage);
    margin-bottom: 10px;
  }

  .section-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: 2.6rem;
    font-weight: 400;
    color: var(--ink);
    line-height: 1.2;
    margin-bottom: 48px;
  }

  .section-title em { font-style: italic; color: var(--sea); }

  /* Kajian cards grid */
  .kajian-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 28px;
  }

  .kajian-card {
    background: var(--white);
    border: 1px solid var(--sand-dark);
    border-radius: 20px;
    overflow: hidden;
    text-decoration: none;
    transition: transform 0.25s, box-shadow 0.25s;
    display: block;
  }

  .kajian-card:hover {
    transform: translateY(-6px);
    box-shadow: 0 16px 48px rgba(74,124,142,0.14);
  }

  .card-top {
    padding: 28px 28px 0;
  }

  .card-tag {
    display: inline-block;
    font-size: 0.68rem;
    font-weight: 500;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    padding: 4px 12px;
    border-radius: 100px;
    margin-bottom: 14px;
  }

  .tag-sea { background: var(--sea-pale); color: var(--sea); }
  .tag-sage { background: var(--sage-pale); color: var(--sage); }
  .tag-warm { background: var(--warm-pale); color: var(--warm); }

  .card-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.4rem;
    font-weight: 600;
    color: var(--ink);
    line-height: 1.35;
    margin-bottom: 8px;
  }

  .card-arabic {
    font-family: 'Amiri', serif;
    font-size: 1.05rem;
    color: var(--ink-light);
    direction: rtl;
    text-align: right;
    margin-bottom: 12px;
  }

  .card-desc {
    font-size: 0.85rem;
    color: var(--ink-mid);
    line-height: 1.7;
  }

  .card-bottom {
    padding: 20px 28px 24px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-top: 1px solid var(--sand-dark);
    margin-top: 20px;
  }

  .card-meta {
    font-size: 0.75rem;
    color: var(--ink-light);
  }

  .card-meta strong {
    display: block;
    color: var(--ink-mid);
    font-size: 0.78rem;
  }

  .card-arrow {
    width: 36px; height: 36px;
    border-radius: 50%;
    background: var(--sand);
    display: flex; align-items: center; justify-content: center;
    color: var(--sea);
    font-size: 1rem;
    transition: background 0.2s, transform 0.2s;
  }

  .kajian-card:hover .card-arrow {
    background: var(--sea);
    color: #fff;
    transform: rotate(45deg);
  }

  /* Featured card */
  .kajian-card.featured {
    grid-column: 1 / -1;
    display: grid;
    grid-template-columns: 1fr 1fr;
  }

  .kajian-card.featured .card-top { padding: 36px 36px 36px; }
  .kajian-card.featured .card-bottom {
    border-top: none;
    border-left: 1px solid var(--sand-dark);
    margin-top: 0;
    padding: 36px;
    flex-direction: column;
    align-items: flex-start;
    gap: 16px;
    background: var(--sand);
  }

  .featured-label {
    font-size: 0.7rem;
    font-weight: 500;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--warm);
    margin-bottom: 8px;
  }

  .featured-desc {
    font-size: 0.88rem;
    color: var(--ink-mid);
    line-height: 1.8;
  }

  .featured-kiat {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin-top: 8px;
  }

  .kiat-pill {
    font-size: 0.72rem;
    padding: 4px 12px;
    border-radius: 100px;
    background: #fff;
    border: 1px solid var(--sand-dark);
    color: var(--ink-mid);
  }

  .read-link {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    font-size: 0.82rem;
    font-weight: 500;
    color: var(--sea);
    text-decoration: none;
    margin-top: auto;
    transition: gap 0.2s;
  }

  .read-link:hover { gap: 12px; }

  /* ── QUOTE SECTION ── */
  .quote-section {
    background: var(--sand);
    padding: 80px 48px;
    text-align: center;
    position: relative;
    overflow: hidden;
  }

  .quote-section::before {
    content: '"';
    position: absolute;
    top: -40px; left: 50%;
    transform: translateX(-50%);
    font-family: 'Cormorant Garamond', serif;
    font-size: 20rem;
    color: rgba(74,124,142,0.05);
    line-height: 1;
    pointer-events: none;
  }

  .quote-section blockquote {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(1.4rem, 3vw, 2.2rem);
    font-weight: 300;
    font-style: italic;
    color: var(--ink);
    max-width: 680px;
    margin: 0 auto 20px;
    line-height: 1.5;
    position: relative;
    z-index: 1;
  }

  .quote-section cite {
    font-size: 0.8rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--ink-light);
    font-style: normal;
  }

  /* ── ABOUT ME ── */
  .about-me {
    padding: 88px 48px;
    max-width: 1100px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 72px;
    align-items: center;
  }

  .about-me-text .eyebrow {
    font-size: 0.72rem;
    font-weight: 500;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: var(--warm);
    margin-bottom: 14px;
  }

  .about-me-text h2 {
    font-family: 'Cormorant Garamond', serif;
    font-size: 2.4rem;
    font-weight: 400;
    color: var(--ink);
    line-height: 1.2;
    margin-bottom: 20px;
  }

  .about-me-text h2 em { font-style: italic; color: var(--sea); }

  .about-me-text p {
    font-size: 0.92rem;
    color: var(--ink-mid);
    line-height: 1.85;
    margin-bottom: 14px;
  }

  .about-me-text .ig-link {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    font-size: 0.82rem;
    font-weight: 500;
    color: var(--sage);
    text-decoration: none;
    margin-top: 8px;
    padding: 10px 20px;
    border: 1.5px solid var(--sage-light);
    border-radius: 100px;
    transition: all 0.2s;
  }

  .about-me-text .ig-link:hover {
    background: var(--sage-pale);
  }

  .about-me-visual {
    position: relative;
  }

  .about-card {
    background: var(--sea);
    border-radius: 24px;
    padding: 40px 36px;
    color: #fff;
    position: relative;
    overflow: hidden;
  }

  .about-card::before {
    content: '';
    position: absolute;
    bottom: -40px; right: -40px;
    width: 180px; height: 180px;
    border-radius: 50%;
    background: rgba(255,255,255,0.06);
  }

  .about-card::after {
    content: '';
    position: absolute;
    top: -20px; left: -20px;
    width: 100px; height: 100px;
    border-radius: 50%;
    background: rgba(255,255,255,0.05);
  }

  .about-card .card-wave {
    font-family: 'Cormorant Garamond', serif;
    font-size: 3rem;
    margin-bottom: 16px;
  }

  .about-card h3 {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.8rem;
    font-weight: 400;
    margin-bottom: 10px;
  }

  .about-card p {
    font-size: 0.88rem;
    color: rgba(255,255,255,0.78);
    line-height: 1.8;
  }

  .stat-row {
    display: flex;
    gap: 24px;
    margin-top: 24px;
    padding-top: 24px;
    border-top: 1px solid rgba(255,255,255,0.15);
  }

  .stat { text-align: center; }
  .stat .num {
    font-family: 'Cormorant Garamond', serif;
    font-size: 2rem;
    font-weight: 600;
    color: #fff;
    line-height: 1;
  }
  .stat .label {
    font-size: 0.72rem;
    color: rgba(255,255,255,0.6);
    margin-top: 4px;
    letter-spacing: 0.05em;
  }

  /* ── FOOTER ── */
  footer {
    background: var(--ink);
    padding: 48px;
    text-align: center;
  }

  footer .footer-logo {
    font-family: 'Cormorant Garamond', serif;
    font-size: 2rem;
    font-weight: 300;
    color: var(--sea-light);
    margin-bottom: 8px;
  }

  footer .footer-logo span { color: var(--sage-light); }

  footer p {
    font-size: 0.78rem;
    color: rgba(255,255,255,0.35);
    margin-top: 6px;
  }

  footer .footer-arabic {
    font-family: 'Amiri', serif;
    font-size: 1.2rem;
    color: rgba(255,255,255,0.5);
    margin: 16px 0 8px;
  }

  /* ── ANIMATIONS ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(22px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  /* ── RESPONSIVE ── */
  @media (max-width: 768px) {
    nav { padding: 16px 20px; }
    .nav-links { display: none; }
    .about-strip { padding: 40px 24px; gap: 32px; }
    .section { padding: 60px 24px; }
    .kajian-card.featured { grid-template-columns: 1fr; }
    .kajian-card.featured .card-bottom { border-left: none; border-top: 1px solid var(--sand-dark); }
    .about-me { grid-template-columns: 1fr; gap: 40px; padding: 60px 24px; }
    .quote-section { padding: 60px 24px; }
    footer { padding: 40px 24px; }
    .about-strip { flex-direction: column; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <a href="index.html" class="nav-logo">bay<span>-thesea</span></a>
  <ul class="nav-links">
    <li><a href="index.html">Home</a></li>
    <li><a href="direktori.html">Semua Kajian</a></li>
    <li><a href="#tentang">Tentang</a></li>
  </ul>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-bubble"></div>
  <div class="hero-bubble"></div>
  <div class="hero-bubble"></div>

  <div class="hero-eyebrow">Catatan Kajian</div>

  <h1 class="hero-title">
    bay<em>-the</em><span class="sage">sea</span>
  </h1>

  <div class="hero-arabic">بِسْمِ اللَّهِ الرَّحْمَٰنِ الرَّحِيمِ</div>

  <p class="hero-desc">
    Semoga catatan ini bisa memberikan manfaat untuk yang membaca dan yang menuliskan.
  </p>

  <div class="hero-cta">
    <a href="direktori.html" class="btn-primary">Baca Semua Kajian</a>
    <a href="#kajian-terbaru" class="btn-secondary">Kajian Terbaru</a>
  </div>
</section>

<!-- WAVE DIVIDER -->
<div class="wave-divider">
  <svg viewBox="0 0 1440 60" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path d="M0,30 C240,60 480,0 720,30 C960,60 1200,0 1440,30 L1440,60 L0,60 Z" fill="#4a7c8e"/>
  </svg>
</div>

<!-- ABOUT STRIP -->
<div class="about-strip">
  <div class="arabic-big">
    إِنَّمَا يَخْشَى اللَّهَ مِنْ عِبَادِهِ الْعُلَمَاءُ
  </div>
  <div class="about-text">
    <h2>Sesungguhnya yang takut kepada Allah di antara hamba-hamba-Nya hanyalah para ulama</h2>
    <p>Setiap catatan di sini adalah ikhtiar kecil untuk menjaga ilmu agar tidak hanya singgah di telinga, tapi mengendap di hati dan berbuah amal.</p>
    <div class="ref">QS. Fatir: 28</div>
  </div>
</div>

<!-- KAJIAN TERBARU -->
<section class="section" id="kajian-terbaru">
  <div class="section-eyebrow">Kajian Terbaru</div>
  <h2 class="section-title">Yang baru saja <em>dicatat</em></h2>

  <div class="kajian-grid">

    <!-- Featured Card -->
    <a href="tazkiyatun-nufus.html" class="kajian-card" style="grid-column: 1 / -1;">
      <div class="card-top">
        <div class="featured-label">✦ Kajian Terbaru</div>
        <div class="card-tag tag-sea">Tazkiyah</div>
        <div class="card-title">Tazkiyatun Nufus — Kiat 1 sampai 5</div>
        <div class="card-arabic">تزكية النفس</div>
        <p class="card-desc">Menelusuri kiat-kiat membersihkan hati dari syirik, syahwat, dan syubhat berdasarkan Al-Qur'an dan Sunnah.</p>
      </div>
      <div class="card-bottom">
        <div class="card-meta">
          <strong>Ustadz Ahmad Rasyid Bazher حفظه الله</strong>
        </div>
        <div class="card-arrow">→</div>
      </div>
    </a>



  </div>
</section>

<!-- QUOTE -->
<div class="quote-section">
  <blockquote>
    "Ilmu meninggikan rumah yang tidak memiliki tiang penyangga, sedangkan kebodohan meruntuhkan rumah kemuliaan dan kehormatan."
  </blockquote>
  <cite>— Ibnul Qayyim Al-Jauziyyah رحمه الله · Madarij As-Salikin</cite>
</div>

<!-- ABOUT ME -->
<section class="about-me" id="tentang">
  <div class="about-me-text">
    <div class="eyebrow">Tentang blog ini</div>
    <h2>Halo, selamat datang di <em>bay-thesea</em> 🌊</h2>
    <p>
      Blog ini lahir dari kebiasaan mencatat kajian — supaya ilmu yang didapat tidak cepat lupa dan bisa bermanfaat juga buat orang lain yang tidak sempat hadir.
    </p>
    <p>
      Nama <em>bay-thesea</em> terinspirasi dari kata "by the sea" — karena laut itu tenang, luas, dan dalam. Semoga setiap catatan di sini bisa dirasakan seperti itu.
    </p>
    <p style="font-size:0.82rem; color:var(--ink-light);">
      Semua catatan ditulis sesuai kemampuan, bukan karena ahli — melainkan karena ingin ikut menjaga ilmu. Wallahu a'lam bishawwab.
    </p>
    <a href="https://instagram.com/bay_thesea" target="_blank" class="ig-link">
      📷 @bay_thesea
    </a>
  </div>

  <div class="about-me-visual">
    <div class="about-card">
      <div class="card-wave">🌊</div>
      <h3>bay-thesea</h3>
      <p>Catatan kajian — ditulis dengan niat semoga menjadi amal jariyah.</p>
      <div class="stat-row">
        <div class="stat">
          <div class="num">1</div>
          <div class="label">Kajian</div>
        </div>
        <div class="stat">
          <div class="num">5</div>
          <div class="label">Kiat tercatat</div>
        </div>
        <div class="stat">
          <div class="num">∞</div>
          <div class="label">Semoga bermanfaat</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">bay<span>-thesea</span></div>
  <div class="footer-arabic">وَمَا تَوْفِيقِي إِلَّا بِاللَّهِ</div>
  <p>@bay_thesea</p>
  <p style="margin-top:4px;">Semoga Allah menerima dan menjadikannya amal jariyah. آمين</p>
</footer>

</body>
</html>
