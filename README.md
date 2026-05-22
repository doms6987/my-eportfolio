
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Dominic Mercurio<title/>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --ink: #0e0e0e;
    --paper: #f5f0e8;
    --accent: #c8472a;
    --gold: #c9a84c;
    --muted: #7a7060;
    --line: rgba(14,14,14,0.12);
    --card-bg: #ffffff;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--paper);
    color: var(--ink);
    font-family: 'DM Sans', sans-serif;
    font-weight: 300;
    font-size: 16px;
    line-height: 1.75;
    overflow-x: hidden;
  }

  /* ── NOISE TEXTURE ── */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 0;
    opacity: .5;
  }

  /* ── NAV ── */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 1.2rem 3rem;
    background: rgba(245,240,232,0.92);
    backdrop-filter: blur(10px);
    border-bottom: 1px solid var(--line);
  }

  .nav-logo {
    font-family: 'Playfair Display', serif;
    font-size: 1.1rem;
    font-weight: 700;
    letter-spacing: .05em;
    color: var(--ink);
    text-decoration: none;
  }

  .nav-links {
    display: flex;
    gap: 2.5rem;
    list-style: none;
  }

  .nav-links a {
    font-size: .8rem;
    font-weight: 500;
    letter-spacing: .12em;
    text-transform: uppercase;
    color: var(--muted);
    text-decoration: none;
    transition: color .2s;
  }

  .nav-links a:hover { color: var(--accent); }

  /* ── HERO ── */
  .hero {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    padding: 8rem 2rem 4rem;
    position: relative;
    overflow: hidden;
  }

  .hero-bg-text {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-family: 'Playfair Display', serif;
    font-size: clamp(8rem, 22vw, 22rem);
    font-weight: 900;
    color: rgba(14,14,14,0.04);
    white-space: nowrap;
    pointer-events: none;
    user-select: none;
    letter-spacing: -.02em;
  }

  .hero-eyebrow {
    font-size: .75rem;
    font-weight: 500;
    letter-spacing: .25em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 1.5rem;
    opacity: 0;
    animation: fadeUp .8s .2s forwards;
  }

  .hero h1 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(3rem, 8vw, 7rem);
    font-weight: 900;
    line-height: 1.0;
    letter-spacing: -.02em;
    max-width: 900px;
    opacity: 0;
    animation: fadeUp .8s .4s forwards;
  }

  .hero h1 em {
    font-style: italic;
    color: var(--accent);
  }

  .hero-sub {
    margin-top: 1.5rem;
    font-size: 1.05rem;
    color: var(--muted);
    max-width: 520px;
    opacity: 0;
    animation: fadeUp .8s .6s forwards;
  }

  .hero-rule {
    width: 60px;
    height: 2px;
    background: var(--gold);
    margin: 2.5rem auto;
    opacity: 0;
    animation: fadeUp .8s .8s forwards;
  }

  .hero-meta {
    font-size: .8rem;
    letter-spacing: .1em;
    text-transform: uppercase;
    color: var(--muted);
    opacity: 0;
    animation: fadeUp .8s 1s forwards;
  }

  .scroll-hint {
    position: absolute;
    bottom: 2.5rem;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: .5rem;
    color: var(--muted);
    font-size: .7rem;
    letter-spacing: .15em;
    text-transform: uppercase;
    opacity: 0;
    animation: fadeUp .8s 1.4s forwards;
  }

  .scroll-line {
    width: 1px;
    height: 40px;
    background: linear-gradient(to bottom, var(--muted), transparent);
    animation: scrollPulse 2s 1.6s infinite;
  }

  /* ── LESSON SECTIONS ── */
  .section {
    position: relative;
    z-index: 1;
  }

  .section-header {
    display: flex;
    align-items: center;
    gap: 1.5rem;
    padding: 5rem 3rem 2rem;
    max-width: 1200px;
    margin: 0 auto;
  }

  .lesson-num {
    font-family: 'Playfair Display', serif;
    font-size: 5rem;
    font-weight: 900;
    color: var(--line);
    line-height: 1;
    flex-shrink: 0;
    transition: color .3s;
  }

  .section:hover .lesson-num { color: rgba(200,71,42,0.15); }

  .section-title-block { flex: 1; }

  .section-tag {
    font-size: .7rem;
    font-weight: 500;
    letter-spacing: .2em;
    text-transform: uppercase;
    color: var(--accent);
    display: block;
    margin-bottom: .4rem;
  }

  .section-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(1.5rem, 3vw, 2.5rem);
    font-weight: 700;
    line-height: 1.15;
    color: var(--ink);
  }

  /* ── JOURNAL CARD ── */
  .journal-card {
    max-width: 1200px;
    margin: 0 auto 6rem;
    padding: 0 3rem;
    display: grid;
    gap: 2rem;
  }

  .journal-card.two-col {
    grid-template-columns: 1fr 1fr;
  }

  .entry {
    background: var(--card-bg);
    border: 1px solid var(--line);
    padding: 2.5rem;
    position: relative;
    overflow: hidden;
    transition: transform .3s ease, box-shadow .3s ease;
  }

  .entry:hover {
    transform: translateY(-4px);
    box-shadow: 0 20px 60px rgba(0,0,0,.08);
  }

  .entry::before {
    content: '';
    position: absolute;
    top: 0; left: 0;
    width: 3px;
    height: 100%;
    background: var(--accent);
    transform: scaleY(0);
    transform-origin: top;
    transition: transform .4s ease;
  }

  .entry:hover::before { transform: scaleY(1); }

  .entry-icon {
    width: 44px;
    height: 44px;
    border-radius: 50%;
    background: var(--paper);
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 1.2rem;
    font-size: 1.3rem;
  }

  .entry h3 {
    font-family: 'Playfair Display', serif;
    font-size: 1.25rem;
    font-weight: 700;
    margin-bottom: 1rem;
    color: var(--ink);
  }

  .entry p {
    font-size: .925rem;
    color: #3a3530;
    line-height: 1.8;
  }

  /* Full-width entry */
  .entry.full {
    grid-column: 1 / -1;
  }

  /* ── QUOTE BLOCK ── */
  .quote-block {
    max-width: 1200px;
    margin: 0 auto 6rem;
    padding: 0 3rem;
  }

  .quote-inner {
    background: var(--ink);
    color: var(--paper);
    padding: 3.5rem 4rem;
    position: relative;
    overflow: hidden;
  }

  .quote-inner::after {
    content: '"';
    position: absolute;
    right: 2rem;
    bottom: -2rem;
    font-family: 'Playfair Display', serif;
    font-size: 16rem;
    font-weight: 900;
    color: rgba(255,255,255,0.04);
    line-height: 1;
    pointer-events: none;
  }

  .quote-text {
    font-family: 'Playfair Display', serif;
    font-size: clamp(1.1rem, 2vw, 1.5rem);
    font-style: italic;
    line-height: 1.6;
    font-weight: 400;
    position: relative;
    z-index: 1;
  }

  .quote-source {
    margin-top: 1.5rem;
    font-size: .75rem;
    letter-spacing: .15em;
    text-transform: uppercase;
    color: var(--gold);
    position: relative;
    z-index: 1;
  }

  /* ── DIVIDER ── */
  .divider {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 3rem;
    border: none;
    border-top: 1px solid var(--line);
    margin-bottom: 0;
  }

  /* ── FOOTER ── */
  footer {
    border-top: 1px solid var(--line);
    padding: 3rem;
    text-align: center;
    color: var(--muted);
    font-size: .8rem;
    letter-spacing: .08em;
    position: relative;
    z-index: 1;
  }

  footer strong {
    font-family: 'Playfair Display', serif;
    font-size: 1rem;
    color: var(--ink);
    display: block;
    margin-bottom: .4rem;
  }

  /* ── INDEX STRIP ── */
  .index-strip {
    max-width: 1200px;
    margin: 0 auto 5rem;
    padding: 0 3rem;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 0;
    border: 1px solid var(--line);
    overflow: hidden;
  }

  .index-item {
    padding: 1.8rem 1.5rem;
    border-right: 1px solid var(--line);
    cursor: pointer;
    transition: background .2s;
  }

  .index-item:last-child { border-right: none; }
  .index-item:hover { background: rgba(200,71,42,.05); }

  .index-item-num {
    font-size: .7rem;
    letter-spacing: .2em;
    text-transform: uppercase;
    color: var(--accent);
    display: block;
    margin-bottom: .4rem;
  }

  .index-item-title {
    font-family: 'Playfair Display', serif;
    font-size: .95rem;
    font-weight: 700;
    line-height: 1.3;
    color: var(--ink);
  }

  /* ── ANIMATIONS ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  @keyframes scrollPulse {
    0%, 100% { opacity: 1; }
    50% { opacity: 0.3; }
  }

  .reveal {
    opacity: 0;
    transform: translateY(30px);
    transition: opacity .7s ease, transform .7s ease;
  }

  .reveal.visible {
    opacity: 1;
    transform: translateY(0);
  }

  /* ── RESPONSIVE ── */
  @media (max-width: 768px) {
    nav { padding: 1rem 1.5rem; }
    .nav-links { gap: 1.2rem; }
    .nav-links a { font-size: .7rem; }
    .section-header, .journal-card, .quote-block, .index-strip { padding: 0 1.5rem; }
    .section-header { flex-direction: column; align-items: flex-start; gap: .5rem; padding-top: 4rem; }
    .lesson-num { font-size: 3rem; }
    .journal-card.two-col { grid-template-columns: 1fr; }
    .index-strip { grid-template-columns: 1fr 1fr; }
    .quote-inner { padding: 2rem; }
    .index-strip { margin: 0 1.5rem 4rem; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <a href="#" class="nav-logo">Dominic Mercurio E-Portfolio</a>
  <ul class="nav-links">
    <li><a href="#lesson8">Lesson 8–9</a></li>
    <li><a href="#lesson10">Lesson 10–11</a></li>
    <li><a href="#lesson12">Lesson 12</a></li>
  </ul>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-bg-text">JOURNAL</div>
  <p class="hero-eyebrow">Science & Technology — EVSU 2026</p>
  <h1>A <em>Journey</em><br>Through Ideas</h1>
  <p class="hero-sub">Reflective journal entries exploring technology, life sciences, and our planet — from Gutenberg's press to climate change.</p>
  <div class="hero-rule"></div>
  <p class="hero-meta">Eastern Visayas State University &nbsp;·&nbsp; 2026</p>
  <div class="scroll-hint">
    <span>Scroll</span>
    <div class="scroll-line"></div>
  </div>
</section>

<!-- LESSON INDEX -->
<div class="index-strip reveal" id="index">
  <div class="index-item" onclick="document.getElementById('lesson8').scrollIntoView({behavior:'smooth'})">
    <span class="index-item-num">Lesson 08</span>
    <div class="index-item-title">The Information Age</div>
  </div>
  <div class="index-item" onclick="document.getElementById('lesson9').scrollIntoView({behavior:'smooth'})">
    <span class="index-item-num">Lesson 09</span>
    <div class="index-item-title">Nano World</div>
  </div>
  <div class="index-item" onclick="document.getElementById('lesson10').scrollIntoView({behavior:'smooth'})">
    <span class="index-item-num">Lesson 10</span>
    <div class="index-item-title">Gene Therapy</div>
  </div>
  <div class="index-item" onclick="document.getElementById('lesson11').scrollIntoView({behavior:'smooth'})">
    <span class="index-item-num">Lesson 11</span>
    <div class="index-item-title">Biodiversity & GMOs</div>
  </div>
</div>

<!-- ═══ LESSON 8 ═══ -->
<section class="section" id="lesson8">
  <div class="section-header reveal">
    <div class="lesson-num">08</div>
    <div class="section-title-block">
      <span class="section-tag">The Information Age</span>
      <h2 class="section-title">Johannes Gutenberg<br>to Social Media</h2>
    </div>
  </div>

  <div class="journal-card two-col reveal">
    <div class="entry">
      <div class="entry-icon">📖</div>
      <h3>Breaking the Knowledge Monopoly</h3>
      <p>Before Gutenberg, knowledge was a scarce currency controlled by the elite. The printing press shattered this monopoly by making books affordable, empowering individuals to think independently and proving that true power lies not in hoarding information, but in distributing it.</p>
    </div>
    <div class="entry">
      <div class="entry-icon">🌐</div>
      <h3>From Broadcast to Conversation</h3>
      <p>If Gutenberg enabled people to <em>consume</em> information, the digital age empowered everyone to <em>produce</em> it — moving us from a "one-to-many" broadcast model to a "many-to-many" global conversation that bypasses traditional gatekeepers entirely.</p>
    </div>
    <div class="entry full">
      <div class="entry-icon">⚖️</div>
      <h3>The Paradox of Abundance</h3>
      <p>This evolution presents a sobering paradox: an abundance of information has not created an abundance of wisdom. While Gutenberg's era fought a scarcity of knowledge, we are drowning in its surplus — where truth and falsehood travel at the same speed, amplified by algorithms designed for engagement rather than education. Ultimately, technology is a mirror of human nature. The tools have evolved from lead stamps to invisible code, but the responsibility to discern truth has shifted entirely upon us. We must transition from passive consumers of data to intentional seekers of truth.</p>
    </div>
  </div>

  <div class="quote-block reveal">
    <div class="quote-inner">
      <p class="quote-text">"Technology is a mirror of human nature; the tools have evolved from lead stamps to invisible code, but the responsibility has shifted — leaving the duty of discernment entirely upon us."</p>
      <p class="quote-source">Lesson 8 Reflection · The Information Age</p>
    </div>
  </div>
</section>

<hr class="divider">

<!-- ═══ LESSON 9 ═══ -->
<section class="section" id="lesson9">
  <div class="section-header reveal">
    <div class="lesson-num">09</div>
    <div class="section-title-block">
      <span class="section-tag">Nanotechnology</span>
      <h2 class="section-title">The Nano World</h2>
    </div>
  </div>

  <div class="journal-card two-col reveal">
    <div class="entry">
      <div class="entry-icon">🔬</div>
      <h3>Mastering the Invisible</h3>
      <p>Humanity's greatest scientific leaps come from mastering the invisible. For centuries, our understanding of nature was limited by what the human eye could see, but nanotechnology completely redefined our relationship with matter — allowing us to manipulate materials at the nanoscale, between 1 and 100 nanometers.</p>
    </div>
    <div class="entry">
      <div class="entry-icon">⚛️</div>
      <h3>Feynman's Vision</h3>
      <p>The foundation of modern nanoscience traces back to physicist Richard Feynman's prophetic 1959 talk, <em>"There's Plenty of Room at the Bottom,"</em> which introduced the possibility of manipulating individual atoms. Decades later, the Scanning Probe Microscope (SPM) and Atomic Force Microscope (AFM) turned that vision into reality.</p>
    </div>
    <div class="entry full">
      <div class="entry-icon">🏗️</div>
      <h3>Building from the Atom Up</h3>
      <p>By learning to manipulate materials at the nanoscale, we transitioned from merely observing the physical world to actively restructuring it from the atom up. What began as theoretical concepts by visionaries like Norio Taniguchi and K. Eric Drexler soon became a tangible reality that revolutionized electronics, computing, and materials science — unlocking the ability to see and build at the atomic level by literally "feeling" surfaces with a mechanical probe.</p>
    </div>
  </div>
</section>

<hr class="divider">

<!-- ═══ LESSON 10 ═══ -->
<section class="section" id="lesson10">
  <div class="section-header reveal">
    <div class="lesson-num">10</div>
    <div class="section-title-block">
      <span class="section-tag">Biotechnology</span>
      <h2 class="section-title">Gene Therapy</h2>
    </div>
  </div>

  <div class="journal-card two-col reveal">
    <div class="entry">
      <div class="entry-icon">🧬</div>
      <h3>Rewriting the Blueprint</h3>
      <p>Gene therapy is a treatment that changes or replaces damaged genes to help prevent or cure diseases. It is considered one of the most important advancements in modern medicine because it gives hope to people who suffer from genetic disorders — offering long-term solutions rather than temporary symptom management.</p>
    </div>
    <div class="entry">
      <div class="entry-icon">⚠️</div>
      <h3>Immense Responsibility</h3>
      <p>Because this technology involves rewriting the blueprint of human life, it must be used with immense responsibility. Gene therapy carries distinct biological risks, such as off-target effects — where a gene is mistakenly altered in the wrong place — or unintended immune reactions that must be carefully managed.</p>
    </div>
  </div>

  <div class="quote-block reveal">
    <div class="quote-inner">
      <p class="quote-text">"Gene therapy has the potential to fundamentally transform human healthcare by treating complex illnesses at their genetic source — pushing the boundaries of what is possible in modern medicine."</p>
      <p class="quote-source">Lesson 10 Reflection · Gene Therapy</p>
    </div>
  </div>
</section>

<hr class="divider">

<!-- ═══ LESSON 11 ═══ -->
<section class="section" id="lesson11">
  <div class="section-header reveal">
    <div class="lesson-num">11</div>
    <div class="section-title-block">
      <span class="section-tag">Life Sciences</span>
      <h2 class="section-title">Biodiversity, GMOs<br>& a Healthy Society</h2>
    </div>
  </div>

  <div class="journal-card two-col reveal">
    <div class="entry">
      <div class="entry-icon">🌿</div>
      <h3>The Web of Life</h3>
      <p>Biodiversity is essential because it supports all life on Earth, creating a complex web where plants, animals, and humans rely on one another. It provides critical ecosystem services — such as clean air and water, fertile soil, food, and the raw materials used in modern medicine — that human society needs to survive and thrive every day.</p>
    </div>
    <div class="entry">
      <div class="entry-icon">🌾</div>
      <h3>The Role of GMOs</h3>
      <p>Genetically Modified Organisms (GMOs) are plants, animals, or microorganisms whose genetic material has been altered using biotechnology to improve traits like crop yield, nutritional value, and shelf life. By engineering crops to be resistant to pests, droughts, and diseases, GMOs serve as a powerful tool for strengthening global food security.</p>
    </div>
  </div>
</section>

<hr class="divider">

<!-- ═══ LESSON 12 ═══ -->
<section class="section" id="lesson12">
  <div class="section-header reveal">
    <div class="lesson-num">12</div>
    <div class="section-title-block">
      <span class="section-tag">Environmental Science</span>
      <h2 class="section-title">Climate Change &<br>Environmental Awareness</h2>
    </div>
  </div>

  <div class="journal-card two-col reveal">
    <div class="entry">
      <div class="entry-icon">🌡️</div>
      <h3>The Greenhouse Effect</h3>
      <p>Climate change is primarily driven by the accelerated release of greenhouse gases — carbon dioxide (CO₂) and methane (CH₄) — which come from burning fossil fuels, industrial pollution, agricultural practices, and widespread deforestation. These gases act like a blanket around the planet, trapping heat and causing global temperatures to rise at an unprecedented rate.</p>
    </div>
    <div class="entry">
      <div class="entry-icon">🌍</div>
      <h3>Human Hands Hold the Answer</h3>
      <p>Climate change is a crisis created by human actions, which means the solutions must also come from us. Environmental awareness is not just about understanding the science of global warming; it is about realizing that our daily choices, policy decisions, and technological innovations dictate the future of our planet.</p>
    </div>
    <div class="entry full">
      <div class="entry-icon">💡</div>
      <h3>A Call to Action</h3>
      <p>The enhanced greenhouse effect is causing global temperatures to rise at an unprecedented rate — yet this lesson's most powerful message is one of agency. The same human ingenuity that accelerated climate change is also capable of reversing it. Every individual choice, every policy reform, and every technological breakthrough brings us one step closer to the world we want to leave behind. This lesson reminded me that awareness without action is incomplete; we must be stewards of the Earth.</p>
    </div>
  </div>

  <div class="quote-block reveal">
    <div class="quote-inner">
      <p class="quote-text">"Environmental awareness is not just about understanding the science of global warming; it is about realizing that our daily choices, policy decisions, and technological innovations dictate which future becomes our reality."</p>
      <p class="quote-source">Lesson 12 Reflection · Climate Change & Environmental Awareness</p>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <strong>Science & Technology Journal Portfolio</strong>
  Eastern Visayas State University &nbsp;·&nbsp; 2026
  <br><br>
  <span style="font-size:.7rem; letter-spacing:.15em; text-transform:uppercase; color:var(--accent);">Lessons 8 · 9 · 10 · 11 · 12</span>
</footer>

<script>
  // Intersection Observer for reveal animations
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry, i) => {
      if (entry.isIntersecting) {
        setTimeout(() => {
          entry.target.classList.add('visible');
        }, 80 * (Array.from(reveals).indexOf(entry.target) % 4));
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.1 });

  reveals.forEach(el => observer.observe(el));
</script>
</body>
</html>
