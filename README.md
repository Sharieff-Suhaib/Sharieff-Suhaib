<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Suhaib Sharieff – Developer Profile</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;700;800&family=DM+Mono:wght@300;400;500&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #070910;
    --surface: #0d1117;
    --border: rgba(255,255,255,0.07);
    --accent: #00e5ff;
    --accent2: #7c3aed;
    --accent3: #f59e0b;
    --text: #e2e8f0;
    --muted: #64748b;
    --card: rgba(255,255,255,0.03);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Mono', monospace;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Animated grid background */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,229,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,229,255,0.03) 1px, transparent 1px);
    background-size: 60px 60px;
    pointer-events: none;
    z-index: 0;
  }

  .glow-blob {
    position: fixed;
    border-radius: 50%;
    filter: blur(120px);
    pointer-events: none;
    z-index: 0;
  }
  .glow-blob.one { width: 500px; height: 500px; background: rgba(0,229,255,0.06); top: -100px; left: -100px; }
  .glow-blob.two { width: 400px; height: 400px; background: rgba(124,58,237,0.07); bottom: 0; right: -100px; }

  .container {
    position: relative;
    z-index: 1;
    max-width: 860px;
    margin: 0 auto;
    padding: 60px 24px 100px;
  }

  /* ── HEADER ── */
  .header {
    display: flex;
    align-items: flex-start;
    gap: 32px;
    margin-bottom: 64px;
    animation: fadeUp 0.8s ease both;
  }

  .avatar-wrap {
    position: relative;
    flex-shrink: 0;
  }

  .avatar {
    width: 88px; height: 88px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    display: flex; align-items: center; justify-content: center;
    font-family: 'Syne', sans-serif;
    font-size: 32px; font-weight: 800;
    color: #000;
    position: relative;
    z-index: 1;
  }

  .avatar-ring {
    position: absolute; inset: -4px;
    border-radius: 50%;
    background: conic-gradient(var(--accent), var(--accent2), var(--accent3), var(--accent));
    animation: spin 4s linear infinite;
    z-index: 0;
  }
  .avatar-ring::after {
    content: '';
    position: absolute; inset: 4px;
    border-radius: 50%;
    background: var(--bg);
  }

  @keyframes spin { to { transform: rotate(360deg); } }

  .header-text { flex: 1; }

  .greeting {
    font-size: 13px; letter-spacing: 0.15em; text-transform: uppercase;
    color: var(--accent); margin-bottom: 8px;
  }

  .name {
    font-family: 'Syne', sans-serif;
    font-size: clamp(28px, 5vw, 44px);
    font-weight: 800;
    line-height: 1.1;
    letter-spacing: -0.02em;
    background: linear-gradient(90deg, #fff 0%, var(--accent) 60%);
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    margin-bottom: 10px;
  }

  .tagline {
    color: var(--muted); font-size: 14px; line-height: 1.6;
    max-width: 420px;
  }

  .connect-btn {
    display: inline-flex; align-items: center; gap: 8px;
    margin-top: 18px;
    padding: 10px 20px;
    border: 1px solid var(--accent);
    border-radius: 6px;
    color: var(--accent);
    font-family: 'DM Mono', monospace;
    font-size: 12px; letter-spacing: 0.1em;
    text-decoration: none;
    text-transform: uppercase;
    transition: all 0.2s;
    background: rgba(0,229,255,0.05);
  }
  .connect-btn:hover {
    background: rgba(0,229,255,0.12);
    box-shadow: 0 0 20px rgba(0,229,255,0.2);
  }

  /* ── SECTION ── */
  .section { margin-bottom: 56px; animation: fadeUp 0.8s ease both; }
  .section:nth-child(2) { animation-delay: 0.1s; }
  .section:nth-child(3) { animation-delay: 0.2s; }
  .section:nth-child(4) { animation-delay: 0.3s; }
  .section:nth-child(5) { animation-delay: 0.4s; }

  .section-label {
    font-size: 11px; letter-spacing: 0.2em; text-transform: uppercase;
    color: var(--muted); margin-bottom: 20px;
    display: flex; align-items: center; gap: 12px;
  }
  .section-label::after {
    content: '';
    flex: 1; height: 1px;
    background: var(--border);
  }

  /* ── SKILL GRID ── */
  .skill-group { margin-bottom: 28px; }
  .skill-group-title {
    font-size: 11px; letter-spacing: 0.15em; text-transform: uppercase;
    color: var(--accent2); margin-bottom: 14px;
    display: flex; align-items: center; gap: 8px;
  }
  .skill-group-title::before {
    content: '';
    width: 6px; height: 6px; border-radius: 50%;
    background: var(--accent2);
  }

  .skills-row {
    display: flex; flex-wrap: wrap; gap: 10px;
  }

  .skill-chip {
    display: flex; align-items: center; gap: 8px;
    padding: 8px 14px;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 6px;
    font-size: 13px;
    color: var(--text);
    transition: all 0.2s;
    cursor: default;
  }
  .skill-chip:hover {
    border-color: var(--accent);
    background: rgba(0,229,255,0.06);
    color: var(--accent);
    transform: translateY(-2px);
    box-shadow: 0 4px 16px rgba(0,229,255,0.1);
  }
  .skill-chip .dot {
    width: 6px; height: 6px; border-radius: 50%;
  }

  /* category colors */
  .cat-frontend .dot { background: #38bdf8; }
  .cat-frontend:hover { border-color: #38bdf8; color: #38bdf8; background: rgba(56,189,248,0.06); }
  .cat-backend .dot { background: #4ade80; }
  .cat-backend:hover { border-color: #4ade80; color: #4ade80; background: rgba(74,222,128,0.06); }
  .cat-db .dot { background: #fb923c; }
  .cat-db:hover { border-color: #fb923c; color: #fb923c; background: rgba(251,146,60,0.06); }
  .cat-java .dot { background: #f87171; }
  .cat-java:hover { border-color: #f87171; color: #f87171; background: rgba(248,113,113,0.06); }
  .cat-ml .dot { background: #a78bfa; }
  .cat-ml:hover { border-color: #a78bfa; color: #a78bfa; background: rgba(167,139,250,0.06); }
  .cat-systems .dot { background: var(--accent3); }
  .cat-systems:hover { border-color: var(--accent3); color: var(--accent3); background: rgba(245,158,11,0.06); }

  /* ── STATS ── */
  .stats-grid {
    display: grid; grid-template-columns: 1fr 1fr; gap: 16px;
  }
  .stat-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 10px;
    overflow: hidden;
    transition: border-color 0.2s, box-shadow 0.2s;
  }
  .stat-card:hover {
    border-color: rgba(0,229,255,0.3);
    box-shadow: 0 0 24px rgba(0,229,255,0.06);
  }
  .stat-card img {
    width: 100%; display: block;
    filter: brightness(0.95);
  }

  @media (max-width: 540px) {
    .stats-grid { grid-template-columns: 1fr; }
    .header { flex-direction: column; }
  }

  /* ── FOOTER ── */
  .footer {
    text-align: center;
    padding-top: 40px;
    border-top: 1px solid var(--border);
    color: var(--muted);
    font-size: 12px;
    letter-spacing: 0.05em;
    animation: fadeUp 0.8s 0.5s ease both;
  }
  .footer a { color: var(--accent); text-decoration: none; }
  .footer a:hover { text-decoration: underline; }

  /* ── STATUS BADGE ── */
  .status {
    display: inline-flex; align-items: center; gap: 6px;
    font-size: 11px; letter-spacing: 0.05em;
    color: #4ade80;
    margin-top: 10px;
  }
  .status-dot {
    width: 6px; height: 6px; border-radius: 50%;
    background: #4ade80;
    animation: pulse 2s infinite;
  }
  @keyframes pulse {
    0%, 100% { opacity: 1; }
    50% { opacity: 0.3; }
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to   { opacity: 1; transform: translateY(0); }
  }
</style>
</head>
<body>
<div class="glow-blob one"></div>
<div class="glow-blob two"></div>

<div class="container">

  <!-- HEADER -->
  <header class="header">
    <div class="avatar-wrap">
      <div class="avatar-ring"></div>
      <div class="avatar">SS</div>
    </div>
    <div class="header-text">
      <p class="greeting">// Hello, world!</p>
      <h1 class="name">Suhaib Sharieff</h1>
      <p class="tagline">Full-stack developer building scalable web systems — from reactive frontends to distributed backends and intelligent ML pipelines.</p>
      <div class="status"><span class="status-dot"></span> Open to opportunities</div>
      <a class="connect-btn" href="mailto:suhaibsharieff05@gmail.com">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,12 2,6"/></svg>
        suhaibsharieff05@gmail.com
      </a>
    </div>
  </header>

  <!-- SKILLS -->
  <section class="section">
    <p class="section-label">Technical Skillset</p>

    <div class="skill-group">
      <div class="skill-group-title">Frontend</div>
      <div class="skills-row">
        <span class="skill-chip cat-frontend"><span class="dot"></span>HTML5</span>
        <span class="skill-chip cat-frontend"><span class="dot"></span>CSS3</span>
        <span class="skill-chip cat-frontend"><span class="dot"></span>JavaScript</span>
        <span class="skill-chip cat-frontend"><span class="dot"></span>TypeScript</span>
        <span class="skill-chip cat-frontend"><span class="dot"></span>React</span>
        <span class="skill-chip cat-frontend"><span class="dot"></span>Next.js</span>
        <span class="skill-chip cat-frontend"><span class="dot"></span>Tailwind CSS</span>
        <span class="skill-chip cat-frontend"><span class="dot"></span>Bootstrap</span>
      </div>
    </div>

    <div class="skill-group">
      <div class="skill-group-title">Backend & APIs</div>
      <div class="skills-row">
        <span class="skill-chip cat-backend"><span class="dot"></span>Node.js</span>
        <span class="skill-chip cat-backend"><span class="dot"></span>Express.js</span>
        <span class="skill-chip cat-backend"><span class="dot"></span>Spring Boot</span>
        <span class="skill-chip cat-backend"><span class="dot"></span>Spring MVC</span>
        <span class="skill-chip cat-backend"><span class="dot"></span>Java Servlets</span>
      </div>
    </div>

    <div class="skill-group">
      <div class="skill-group-title">Databases</div>
      <div class="skills-row">
        <span class="skill-chip cat-db"><span class="dot"></span>MongoDB</span>
        <span class="skill-chip cat-db"><span class="dot"></span>PostgreSQL</span>
      </div>
    </div>

    <div class="skill-group">
      <div class="skill-group-title">Machine Learning</div>
      <div class="skills-row">
        <span class="skill-chip cat-ml"><span class="dot"></span>Python</span>
        <span class="skill-chip cat-ml"><span class="dot"></span>Scikit-learn</span>
        <span class="skill-chip cat-ml"><span class="dot"></span>Pandas / NumPy</span>
        <span class="skill-chip cat-ml"><span class="dot"></span>ML Pipelines</span>
      </div>
    </div>

    <div class="skill-group">
      <div class="skill-group-title">Systems & Languages</div>
      <div class="skills-row">
        <span class="skill-chip cat-systems"><span class="dot"></span>C</span>
        <span class="skill-chip cat-systems"><span class="dot"></span>C++</span>
        <span class="skill-chip cat-java"><span class="dot"></span>Java</span>
        <span class="skill-chip cat-systems"><span class="dot"></span>Linux</span>
      </div>
    </div>
  </section>

  <!-- GITHUB STATS -->
  <section class="section">
    <p class="section-label">GitHub Statistics</p>
    <div class="stats-grid">
      <div class="stat-card">
        <img src="https://github-readme-stats.vercel.app/api?username=Sharieff-Suhaib&show_icons=true&theme=transparent&hide_border=true&title_color=00e5ff&icon_color=7c3aed&text_color=e2e8f0&bg_color=00000000" alt="GitHub Stats" loading="lazy"/>
      </div>
      <div class="stat-card">
        <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Sharieff-Suhaib&layout=compact&theme=transparent&hide_border=true&title_color=00e5ff&text_color=e2e8f0&bg_color=00000000" alt="Top Languages" loading="lazy"/>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer class="footer">
    <p>🚀 Let's build something remarkable — <a href="mailto:suhaibsharieff05@gmail.com">get in touch</a></p>
    <p style="margin-top:8px; color: #334155;">github.com/Sharieff-Suhaib</p>
  </footer>

</div>
</body>
</html>
