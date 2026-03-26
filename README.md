<!DOCTYPE html>
<html lang="uz">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Husan Suyunov — Portfolio</title>
  <link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;700;800&family=JetBrains+Mono:wght@300;400;700&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --bg: #080c14;
      --bg2: #0d1320;
      --surface: #111927;
      --border: #1e2d45;
      --cyan: #00f7ff;
      --cyan-dim: #00c6cc;
      --green: #39ff7e;
      --orange: #ff8c00;
      --purple: #a78bfa;
      --text: #d4e6f1;
      --text-muted: #5b7a9a;
      --card-bg: rgba(13, 19, 32, 0.85);
    }

    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: 'JetBrains Mono', monospace;
      min-height: 100vh;
      overflow-x: hidden;
    }

    /* ─── BG grid ─── */
    body::before {
      content: '';
      position: fixed;
      inset: 0;
      background-image:
        linear-gradient(rgba(0,247,255,.03) 1px, transparent 1px),
        linear-gradient(90deg, rgba(0,247,255,.03) 1px, transparent 1px);
      background-size: 40px 40px;
      pointer-events: none;
      z-index: 0;
    }

    .container {
      max-width: 900px;
      margin: 0 auto;
      padding: 60px 24px 100px;
      position: relative;
      z-index: 1;
    }

    /* ─── HERO ─── */
    .hero {
      text-align: center;
      padding: 60px 0 50px;
      position: relative;
    }

    .hero-glow {
      position: absolute;
      width: 500px;
      height: 300px;
      background: radial-gradient(ellipse, rgba(0,247,255,.12) 0%, transparent 70%);
      top: 0; left: 50%;
      transform: translateX(-50%);
      pointer-events: none;
    }

    .avatar-wrap {
      position: relative;
      display: inline-block;
      margin-bottom: 28px;
    }
    .avatar-wrap img {
      width: 120px; height: 120px;
      border-radius: 50%;
      border: 2px solid var(--cyan);
      display: block;
      filter: brightness(1.1);
    }
    .avatar-ring {
      position: absolute;
      inset: -8px;
      border-radius: 50%;
      border: 1px dashed rgba(0,247,255,.35);
      animation: spin 20s linear infinite;
    }
    .avatar-dot {
      position: absolute;
      width: 10px; height: 10px;
      background: var(--green);
      border-radius: 50%;
      bottom: 8px; right: 8px;
      border: 2px solid var(--bg);
      box-shadow: 0 0 8px var(--green);
    }

    @keyframes spin { to { transform: rotate(360deg); } }

    .hero-name {
      font-family: 'Syne', sans-serif;
      font-size: clamp(2rem, 5vw, 3rem);
      font-weight: 800;
      letter-spacing: -1px;
      color: #fff;
      line-height: 1;
      margin-bottom: 10px;
    }
    .hero-name span { color: var(--cyan); }

    .hero-title {
      font-family: 'Space Mono', monospace;
      font-size: .78rem;
      color: var(--text-muted);
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-bottom: 28px;
    }

    .typing-line {
      font-size: .9rem;
      color: var(--cyan);
      margin-bottom: 32px;
      min-height: 1.4em;
    }
    .typing-line span { border-right: 2px solid var(--cyan); padding-right: 2px; animation: blink .7s infinite; }
    @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0} }

    .badge-row {
      display: flex;
      gap: 10px;
      justify-content: center;
      flex-wrap: wrap;
    }
    .badge {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      padding: 6px 14px;
      border: 1px solid var(--border);
      border-radius: 4px;
      font-size: .72rem;
      letter-spacing: 1px;
      text-transform: uppercase;
      color: var(--text-muted);
      background: var(--surface);
      transition: all .2s;
      text-decoration: none;
    }
    .badge:hover { border-color: var(--cyan); color: var(--cyan); background: rgba(0,247,255,.05); }
    .badge .dot { width:6px;height:6px;border-radius:50%;background:currentColor; }

    /* ─── SECTION ─── */
    section { margin-top: 64px; }

    .section-label {
      display: flex;
      align-items: center;
      gap: 12px;
      font-family: 'Space Mono', monospace;
      font-size: .65rem;
      letter-spacing: 3px;
      text-transform: uppercase;
      color: var(--text-muted);
      margin-bottom: 24px;
    }
    .section-label::before {
      content: '';
      width: 28px; height: 1px;
      background: var(--cyan);
    }
    .section-label::after {
      content: '';
      flex: 1; height: 1px;
      background: var(--border);
    }

    /* ─── ABOUT ─── */
    .about-card {
      background: var(--card-bg);
      border: 1px solid var(--border);
      border-radius: 8px;
      padding: 28px 32px;
      position: relative;
      overflow: hidden;
    }
    .about-card::before {
      content: '';
      position: absolute;
      top: 0; left: 0;
      width: 3px; height: 100%;
      background: linear-gradient(180deg, var(--cyan), transparent);
    }
    .about-card p {
      font-size: .85rem;
      line-height: 1.9;
      color: var(--text);
    }
    .about-card p + p { margin-top: 12px; }
    .hl { color: var(--cyan); font-weight: 700; }
    .hl2 { color: var(--green); font-weight: 700; }

    /* ─── SKILLS ─── */
    .skills-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
      gap: 12px;
    }
    .skill-item {
      background: var(--card-bg);
      border: 1px solid var(--border);
      border-radius: 6px;
      padding: 14px 18px;
      display: flex;
      align-items: center;
      gap: 12px;
      font-size: .82rem;
      transition: all .2s;
    }
    .skill-item:hover {
      border-color: rgba(0,247,255,.4);
      background: rgba(0,247,255,.04);
      transform: translateY(-2px);
    }
    .skill-icon { font-size: 1.2rem; width: 26px; text-align: center; }
    .skill-name { color: var(--text); }
    .skill-tag {
      margin-left: auto;
      font-size: .6rem;
      letter-spacing: 1px;
      padding: 2px 7px;
      border-radius: 3px;
      text-transform: uppercase;
    }
    .tag-main { background: rgba(0,247,255,.12); color: var(--cyan); }
    .tag-sec  { background: rgba(57,255,126,.1);  color: var(--green); }
    .tag-other{ background: rgba(167,139,250,.1); color: var(--purple); }

    /* ─── TECH STACK ─── */
    .tech-row {
      display: flex; flex-wrap: wrap; gap: 10px;
    }
    .tech-pill {
      display: flex; align-items: center; gap: 7px;
      padding: 7px 14px;
      border: 1px solid var(--border);
      border-radius: 999px;
      font-size: .75rem;
      color: var(--text-muted);
      background: var(--surface);
      transition: all .2s;
    }
    .tech-pill:hover { border-color: var(--cyan); color: var(--text); }
    .tech-pill img { width:16px; height:16px; }

    /* ─── STATS ─── */
    .stats-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 14px;
    }
    .stats-card {
      background: var(--card-bg);
      border: 1px solid var(--border);
      border-radius: 8px;
      overflow: hidden;
      text-align: center;
    }
    .stats-card img { width: 100%; display: block; }
    .stats-card.wide { grid-column: 1 / -1; }

    /* ─── QUOTE ─── */
    .quote-block {
      text-align: center;
      padding: 40px 20px;
      position: relative;
    }
    .quote-text {
      font-family: 'Syne', sans-serif;
      font-size: clamp(1.1rem, 3vw, 1.6rem);
      font-weight: 700;
      color: #fff;
      line-height: 1.5;
    }
    .quote-text .q-cyan { color: var(--cyan); }
    .quote-text .q-green{ color: var(--green); }
    .quote-attr {
      margin-top: 12px;
      font-size: .7rem;
      letter-spacing: 2px;
      color: var(--text-muted);
      text-transform: uppercase;
    }

    /* ─── FOOTER ─── */
    .footer {
      margin-top: 80px;
      border-top: 1px solid var(--border);
      padding-top: 30px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      gap: 12px;
    }
    .footer-left {
      font-size: .7rem;
      color: var(--text-muted);
      letter-spacing: 1px;
    }
    .views-badge {
      display: flex; align-items: center; gap: 8px;
      font-size: .7rem;
      color: var(--text-muted);
    }
    .views-dot { width:6px;height:6px;border-radius:50%;background:var(--cyan);box-shadow:0 0 6px var(--cyan); }

    /* ─── ANIMATIONS ─── */
    .fade-up {
      opacity: 0;
      transform: translateY(24px);
      animation: fadeUp .6s ease forwards;
    }
    @keyframes fadeUp { to { opacity:1; transform:none; } }
    .d1 { animation-delay: .1s; }
    .d2 { animation-delay: .2s; }
    .d3 { animation-delay: .3s; }
    .d4 { animation-delay: .4s; }
    .d5 { animation-delay: .5s; }
    .d6 { animation-delay: .6s; }
  </style>
</head>
<body>
<div class="container">

  <!-- HERO -->
  <div class="hero fade-up">
    <div class="hero-glow"></div>
    <div class="avatar-wrap">
      <img src="https://avatars.githubusercontent.com/u/109731657?v=4" alt="Husan Suyunov"/>
      <div class="avatar-ring"></div>
      <div class="avatar-dot"></div>
    </div>
    <div class="hero-name"><span>Husan</span> Suyunov</div>
    <div class="hero-title">Python Developer · Data Analyst · NLP Specialist</div>
    <div class="typing-line" id="typer"><span></span></div>
    <div class="badge-row">
      <a class="badge" href="https://github.com/xusanbek0039">
        <div class="dot"></div> xusanbek0039
      </a>
      <a class="badge" href="https://t.me/husanbek_coder">
        <div class="dot"></div> @husanbek_coder
      </a>
    </div>
  </div>

  <!-- ABOUT -->
  <section class="fade-up d1">
    <div class="section-label">about</div>
    <div class="about-card">
      <p>
        Men — <span class="hl">Python Developer</span>, <span class="hl">Data Analyst</span> va
        <span class="hl">NLP</span> yo'nalishida rivojlanayotgan kuchli mutaxassisman.
      </p>
      <p>
        📊 Data bilan ishlash, analiz qilish va undan foydali natijalar chiqarish — mening asosiy skillim.
      </p>
      <p>
        🤖 NLP orqali <span class="hl2">chatbotlar</span>, aqlli tizimlar va AI yechimlar ustida ishlayman.
      </p>
      <p>
        🚀 Har kuni o'rganaman, real loyihalar qilaman va o'saman.
      </p>
    </div>
  </section>

  <!-- SKILLS -->
  <section class="fade-up d2">
    <div class="section-label">skills</div>
    <div class="skills-grid">
      <div class="skill-item">
        <span class="skill-icon">🐍</span>
        <span class="skill-name">Python</span>
        <span class="skill-tag tag-main">core</span>
      </div>
      <div class="skill-item">
        <span class="skill-icon">🌐</span>
        <span class="skill-name">Django</span>
        <span class="skill-tag tag-main">backend</span>
      </div>
      <div class="skill-item">
        <span class="skill-icon">📊</span>
        <span class="skill-name">Pandas / NumPy</span>
        <span class="skill-tag tag-sec">data</span>
      </div>
      <div class="skill-item">
        <span class="skill-icon">🤖</span>
        <span class="skill-name">NLP & AI</span>
        <span class="skill-tag tag-sec">ai</span>
      </div>
      <div class="skill-item">
        <span class="skill-icon">⚛️</span>
        <span class="skill-name">React</span>
        <span class="skill-tag tag-other">frontend</span>
      </div>
      <div class="skill-item">
        <span class="skill-icon">🗄️</span>
        <span class="skill-name">PostgreSQL / MySQL</span>
        <span class="skill-tag tag-other">db</span>
      </div>
      <div class="skill-item">
        <span class="skill-icon">🐧</span>
        <span class="skill-name">Linux</span>
        <span class="skill-tag tag-other">ops</span>
      </div>
      <div class="skill-item">
        <span class="skill-icon">🔀</span>
        <span class="skill-name">Git</span>
        <span class="skill-tag tag-other">tools</span>
      </div>
    </div>
  </section>

  <!-- TECH STACK -->
  <section class="fade-up d3">
    <div class="section-label">tech stack</div>
    <div class="tech-row">
      <div class="tech-pill"><img src="https://skillicons.dev/icons?i=python" />Python</div>
      <div class="tech-pill"><img src="https://skillicons.dev/icons?i=django" />Django</div>
      <div class="tech-pill"><img src="https://skillicons.dev/icons?i=react"  />React</div>
      <div class="tech-pill"><img src="https://skillicons.dev/icons?i=js"     />JavaScript</div>
      <div class="tech-pill"><img src="https://skillicons.dev/icons?i=html"   />HTML5</div>
      <div class="tech-pill"><img src="https://skillicons.dev/icons?i=css"    />CSS3</div>
      <div class="tech-pill"><img src="https://skillicons.dev/icons?i=postgres"/>PostgreSQL</div>
      <div class="tech-pill"><img src="https://skillicons.dev/icons?i=mysql"  />MySQL</div>
      <div class="tech-pill"><img src="https://skillicons.dev/icons?i=git"    />Git</div>
      <div class="tech-pill"><img src="https://skillicons.dev/icons?i=linux"  />Linux</div>
    </div>
  </section>

  <!-- GITHUB STATS -->
  <section class="fade-up d4">
    <div class="section-label">github stats</div>
    <div class="stats-grid">
      <div class="stats-card">
        <img src="https://github-readme-stats.vercel.app/api?username=xusanbek0039&show_icons=true&theme=tokyonight&hide_border=true&bg_color=0d1320&title_color=00f7ff&icon_color=39ff7e&text_color=d4e6f1" alt="Stats"/>
      </div>
      <div class="stats-card">
        <img src="https://github-readme-streak-stats.herokuapp.com/?user=xusanbek0039&theme=tokyonight&hide_border=true&background=0d1320&stroke=1e2d45&ring=00f7ff&fire=ff8c00&currStreakLabel=00f7ff" alt="Streak"/>
      </div>
      <div class="stats-card wide">
        <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=xusanbek0039&layout=compact&theme=tokyonight&hide_border=true&bg_color=0d1320&title_color=00f7ff&text_color=d4e6f1" alt="Languages"/>
      </div>
    </div>
  </section>

  <!-- TROPHY -->
  <section class="fade-up d5">
    <div class="section-label">trophies</div>
    <div class="stats-card wide">
      <img src="https://github-profile-trophy.vercel.app/?username=xusanbek0039&theme=tokyonight&no-frame=true&column=7&margin-w=8" alt="Trophies" style="width:100%;"/>
    </div>
  </section>

  <!-- ACTIVITY -->
  <section class="fade-up d5">
    <div class="section-label">activity graph</div>
    <div class="stats-card wide">
      <img src="https://github-readme-activity-graph.vercel.app/graph?username=xusanbek0039&theme=tokyo-night&hide_border=true&bg_color=0d1320" alt="Activity" style="width:100%;"/>
    </div>
  </section>

  <!-- SNAKE -->
  <section class="fade-up d5">
    <div class="section-label">contribution snake</div>
    <div class="stats-card wide" style="padding:10px;">
      <img src="https://raw.githubusercontent.com/xusanbek0039/xusanbek0039/output/github-contribution-grid-snake.svg" alt="Snake" style="width:100%;display:block;"/>
    </div>
  </section>

  <!-- QUOTE -->
  <section class="fade-up d6">
    <div class="quote-block">
      <div class="quote-text">
        "<span class="q-cyan">Code</span> + <span class="q-green">Data</span> + AI = Future 🚀"
      </div>
      <div class="quote-attr">— Husan Suyunov</div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer class="footer fade-up d6">
    <div class="footer-left">© 2025 Husan Suyunov · All rights reserved</div>
    <div class="views-badge">
      <div class="views-dot"></div>
      <img src="https://komarev.com/ghpvc/?username=xusanbek0039&color=00f7ff&style=flat-square&label=views" alt="Views"/>
    </div>
  </footer>

</div>

<script>
  // Typing animation
  const lines = [
    'Python Developer 🐍',
    'Data Analyst 📊',
    'NLP & AI Enthusiast 🤖',
    'Full-Stack Developer 🌐',
  ];
  let li = 0, ci = 0, deleting = false;
  const el = document.querySelector('#typer span');
  function type() {
    const cur = lines[li];
    if (!deleting) {
      el.textContent = cur.slice(0, ++ci);
      if (ci === cur.length) { deleting = true; setTimeout(type, 1800); return; }
    } else {
      el.textContent = cur.slice(0, --ci);
      if (ci === 0) { deleting = false; li = (li + 1) % lines.length; }
    }
    setTimeout(type, deleting ? 45 : 80);
  }
  type();
</script>
</body>
</html>
