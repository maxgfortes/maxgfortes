
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<style>
  @import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Rajdhani:wght@400;500;600;700&family=Space+Mono:ital,wght@0,400;0,700;1,400&display=swap');

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: #0a0a0a;
    color: #c8c8c8;
    font-family: 'Space Mono', monospace;
    min-height: 100vh;
    overflow-x: hidden;
  }

  .readme {
    max-width: 860px;
    margin: 0 auto;
    padding: 2.5rem 2rem 4rem;
    background: #0d0d0d;
    border-left: 1px solid #1e1e1e;
    border-right: 1px solid #1e1e1e;
    min-height: 100vh;
  }

  /* ─── ANIMATIONS ─── */
  @keyframes fadeDown {
    from { opacity: 0; transform: translateY(-18px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(18px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  @keyframes fadeIn {
    from { opacity: 0; }
    to   { opacity: 1; }
  }
  @keyframes slideRight {
    from { opacity: 0; transform: translateX(-24px); }
    to   { opacity: 1; transform: translateX(0); }
  }
  @keyframes barGrow {
    from { width: 0; }
    to   { width: var(--w); }
  }
  @keyframes pulse {
    0%, 100% { opacity: 1; }
    50%       { opacity: 0.4; }
  }
  @keyframes scanline {
    0%   { transform: translateY(-100%); }
    100% { transform: translateY(100vh); }
  }
  @keyframes borderGlow {
    0%, 100% { box-shadow: 0 0 0px #3a3a3a; }
    50%       { box-shadow: 0 0 8px #3a3a3a; }
  }
  @keyframes typeIn {
    from { width: 0; }
    to   { width: 100%; }
  }
  @keyframes blink {
    0%, 100% { border-right-color: #888; }
    50%       { border-right-color: transparent; }
  }

  .anim-fd   { animation: fadeDown  0.6s ease forwards; opacity: 0; }
  .anim-fu   { animation: fadeUp    0.6s ease forwards; opacity: 0; }
  .anim-fi   { animation: fadeIn    0.6s ease forwards; opacity: 0; }
  .anim-sr   { animation: slideRight 0.5s ease forwards; opacity: 0; }

  .d1  { animation-delay: 0.1s; }
  .d2  { animation-delay: 0.3s; }
  .d3  { animation-delay: 0.5s; }
  .d4  { animation-delay: 0.7s; }
  .d5  { animation-delay: 0.9s; }
  .d6  { animation-delay: 1.1s; }
  .d7  { animation-delay: 1.3s; }
  .d8  { animation-delay: 1.5s; }
  .d9  { animation-delay: 1.7s; }
  .d10 { animation-delay: 1.9s; }
  .d11 { animation-delay: 2.1s; }
  .d12 { animation-delay: 2.3s; }

  /* ─── SCANLINE OVERLAY ─── */
  .readme::before {
    content: '';
    position: fixed;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: rgba(255,255,255,0.03);
    animation: scanline 8s linear infinite;
    pointer-events: none;
    z-index: 99;
  }

  /* ─── HEADER ─── */
  .header {
    text-align: center;
    padding-bottom: 2rem;
    border-bottom: 1px solid #1e1e1e;
    margin-bottom: 2rem;
  }

  .avatar-wrap {
    display: flex;
    justify-content: center;
    margin-bottom: 1.2rem;
  }

  .avatar {
    width: 88px; height: 88px;
    border-radius: 50%;
    background: #111;
    border: 1px solid #2a2a2a;
    display: flex; align-items: center; justify-content: center;
    font-family: 'Rajdhani', sans-serif;
    font-size: 28px;
    font-weight: 700;
    color: #888;
    position: relative;
    animation: borderGlow 3s ease-in-out infinite;
  }

  .avatar::after {
    content: '';
    position: absolute;
    inset: -4px;
    border-radius: 50%;
    border: 1px dashed #222;
    animation: borderGlow 3s ease-in-out infinite reverse;
  }

  .title {
    font-family: 'Rajdhani', sans-serif;
    font-size: 2.4rem;
    font-weight: 700;
    color: #e0e0e0;
    letter-spacing: 0.08em;
    line-height: 1.1;
    text-transform: uppercase;
    margin-bottom: 0.3rem;
  }

  .subtitle {
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.75rem;
    color: #555;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    margin-bottom: 1.2rem;
  }

  /* ─── TYPING LINE ─── */
  .typing-line {
    display: inline-block;
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.78rem;
    color: #666;
    overflow: hidden;
    white-space: nowrap;
    border-right: 2px solid #888;
    animation: typeIn 2.2s steps(40) 1.8s forwards,
               blink   0.75s step-end 1.8s infinite;
    width: 0;
    max-width: 100%;
  }

  /* ─── BADGES ─── */
  .badges {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    justify-content: center;
    margin-top: 1rem;
  }

  .badge {
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.68rem;
    color: #777;
    background: #111;
    border: 1px solid #222;
    border-radius: 3px;
    padding: 3px 10px;
    letter-spacing: 0.05em;
    transition: border-color 0.2s, color 0.2s;
    text-decoration: none;
  }
  .badge:hover { border-color: #444; color: #aaa; }
  .badge .dot { display: inline-block; width: 6px; height: 6px; border-radius: 50%; margin-right: 5px; vertical-align: middle; }
  .dot-green  { background: #3d7a3d; animation: pulse 2s ease-in-out infinite; }
  .dot-gray   { background: #444; }
  .dot-yellow { background: #7a7030; }

  /* ─── SECTION ─── */
  .section { margin-bottom: 2.2rem; }

  .section-label {
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.65rem;
    color: #3a3a3a;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    margin-bottom: 0.7rem;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: #1a1a1a;
  }

  .section-title {
    font-family: 'Rajdhani', sans-serif;
    font-size: 1.15rem;
    font-weight: 600;
    color: #bbb;
    letter-spacing: 0.06em;
    text-transform: uppercase;
    margin-bottom: 0.8rem;
  }

  /* ─── ABOUT / DESCRIPTION ─── */
  .about-text {
    font-size: 0.78rem;
    color: #666;
    line-height: 1.85;
    border-left: 2px solid #1e1e1e;
    padding-left: 1rem;
  }
  .about-text em { color: #888; font-style: normal; }

  /* ─── STATS GRID ─── */
  .stats-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
    margin-bottom: 1.5rem;
  }

  .stat-card {
    background: #111;
    border: 1px solid #1e1e1e;
    border-radius: 4px;
    padding: 1rem 0.8rem;
    text-align: center;
    transition: border-color 0.25s;
  }
  .stat-card:hover { border-color: #333; }

  .stat-number {
    font-family: 'Rajdhani', sans-serif;
    font-size: 1.6rem;
    font-weight: 700;
    color: #d0d0d0;
    line-height: 1;
    margin-bottom: 0.3rem;
    display: block;
  }
  .stat-label {
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.6rem;
    color: #3a3a3a;
    letter-spacing: 0.15em;
    text-transform: uppercase;
  }

  /* ─── LANG BARS ─── */
  .lang-row {
    margin-bottom: 0.9rem;
  }
  .lang-header {
    display: flex;
    justify-content: space-between;
    margin-bottom: 0.35rem;
  }
  .lang-name {
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.72rem;
    color: #777;
  }
  .lang-pct {
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.68rem;
    color: #444;
  }
  .bar-track {
    height: 2px;
    background: #1a1a1a;
    border-radius: 1px;
    overflow: hidden;
  }
  .bar-fill {
    height: 100%;
    border-radius: 1px;
    background: #3a3a3a;
    width: var(--w);
    animation: barGrow 1s ease forwards;
    animation-delay: var(--d, 0.3s);
    width: 0;
  }

  /* ─── SKILL TAGS ─── */
  .skills {
    display: flex;
    flex-wrap: wrap;
    gap: 7px;
  }
  .skill-tag {
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.65rem;
    color: #555;
    background: #111;
    border: 1px solid #1e1e1e;
    border-radius: 2px;
    padding: 4px 10px;
    letter-spacing: 0.05em;
    transition: all 0.2s;
  }
  .skill-tag:hover { color: #999; border-color: #333; background: #151515; }

  /* ─── ACTIVITY GRID ─── */
  .activity-grid {
    display: grid;
    grid-template-columns: repeat(52, 1fr);
    gap: 3px;
  }
  .activity-cell {
    aspect-ratio: 1;
    border-radius: 1px;
    background: #141414;
    transition: background 0.2s;
    cursor: default;
  }
  .activity-cell.l1 { background: #1e1e1e; }
  .activity-cell.l2 { background: #2a2a2a; }
  .activity-cell.l3 { background: #3a3a3a; }
  .activity-cell.l4 { background: #555; }
  .activity-cell:hover { background: #777 !important; }

  /* ─── RECENT REPOS ─── */
  .repo-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
  }
  .repo-card {
    background: #111;
    border: 1px solid #1e1e1e;
    border-radius: 4px;
    padding: 1rem;
    transition: border-color 0.25s;
  }
  .repo-card:hover { border-color: #2e2e2e; }
  .repo-name {
    font-family: 'Rajdhani', sans-serif;
    font-size: 0.95rem;
    font-weight: 600;
    color: #aaa;
    margin-bottom: 0.35rem;
    letter-spacing: 0.04em;
  }
  .repo-desc {
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.62rem;
    color: #444;
    line-height: 1.6;
    margin-bottom: 0.7rem;
  }
  .repo-meta {
    display: flex;
    gap: 12px;
    align-items: center;
  }
  .repo-lang-dot {
    width: 8px; height: 8px;
    border-radius: 50%;
    background: #3a3a3a;
    display: inline-block;
    margin-right: 4px;
    vertical-align: middle;
  }
  .repo-lang {
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.6rem;
    color: #444;
  }
  .repo-stars {
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.6rem;
    color: #3a3a3a;
  }

  /* ─── FOOTER ─── */
  .footer {
    text-align: center;
    padding-top: 2rem;
    border-top: 1px solid #151515;
    margin-top: 2rem;
  }
  .footer-text {
    font-family: 'Share Tech Mono', monospace;
    font-size: 0.62rem;
    color: #2a2a2a;
    letter-spacing: 0.12em;
  }

  .divider {
    height: 1px;
    background: #141414;
    margin: 2rem 0;
  }

  @media (max-width: 520px) {
    .stats-grid { grid-template-columns: repeat(2, 1fr); }
    .repo-grid  { grid-template-columns: 1fr; }
    .activity-grid { grid-template-columns: repeat(26, 1fr); }
    .title { font-size: 1.7rem; }
  }
</style>
</head>
<body>
<div class="readme">

  <!-- HEADER -->
  <header class="header">
    <div class="avatar-wrap anim-fd d1">
      <div class="avatar">◆</div>
    </div>

    <h1 class="title anim-fd d2">votre_nom</h1>
    <p class="subtitle anim-fd d3">// software engineer — systems &amp; interfaces</p>

    <div class="anim-fi d4">
      <span class="typing-line">crafting dark, minimal tools for a brighter world.</span>
    </div>

    <div class="badges anim-fu d5">
      <span class="badge"><span class="dot dot-green"></span>open to work</span>
      <span class="badge"><span class="dot dot-gray"></span>brazil — UTC-3</span>
      <span class="badge"><span class="dot dot-yellow"></span>5 repos this month</span>
      <span class="badge">profile views: 3.2k</span>
      <span class="badge">followers: 142</span>
    </div>
  </header>

  <!-- ABOUT -->
  <section class="section anim-sr d5">
    <p class="section-label">01 — about</p>
    <p class="about-text">
      Building tools at the intersection of <em>performance</em> and <em>aesthetics</em>.<br>
      Obsessed with clean architecture, dark terminals, and code that reads like prose.<br>
      Currently deep in <em>distributed systems</em> and <em>language runtimes</em>.
    </p>
  </section>

  <div class="divider anim-fi d6"></div>

  <!-- STATS -->
  <section class="section anim-fu d6">
    <p class="section-label">02 — github stats</p>
    <div class="stats-grid">
      <div class="stat-card">
        <span class="stat-number">847</span>
        <span class="stat-label">commits</span>
      </div>
      <div class="stat-card">
        <span class="stat-number">34</span>
        <span class="stat-label">repos</span>
      </div>
      <div class="stat-card">
        <span class="stat-number">142</span>
        <span class="stat-label">followers</span>
      </div>
      <div class="stat-card">
        <span class="stat-number">2.1k</span>
        <span class="stat-label">stars</span>
      </div>
    </div>
  </section>

  <div class="divider anim-fi d7"></div>

  <!-- LANGUAGES -->
  <section class="section anim-sr d7">
    <p class="section-label">03 — top languages</p>
    <div style="margin-top: 0.5rem;">
      <div class="lang-row">
        <div class="lang-header">
          <span class="lang-name">TypeScript</span>
          <span class="lang-pct">41%</span>
        </div>
        <div class="bar-track"><div class="bar-fill" style="--w:41%; --d:0.7s;"></div></div>
      </div>
      <div class="lang-row">
        <div class="lang-header">
          <span class="lang-name">Rust</span>
          <span class="lang-pct">27%</span>
        </div>
        <div class="bar-track"><div class="bar-fill" style="--w:27%; --d:0.9s;"></div></div>
      </div>
      <div class="lang-row">
        <div class="lang-header">
          <span class="lang-name">Go</span>
          <span class="lang-pct">18%</span>
        </div>
        <div class="bar-track"><div class="bar-fill" style="--w:18%; --d:1.1s;"></div></div>
      </div>
      <div class="lang-row">
        <div class="lang-header">
          <span class="lang-name">Python</span>
          <span class="lang-pct">9%</span>
        </div>
        <div class="bar-track"><div class="bar-fill" style="--w:9%; --d:1.3s;"></div></div>
      </div>
      <div class="lang-row">
        <div class="lang-header">
          <span class="lang-name">Shell</span>
          <span class="lang-pct">5%</span>
        </div>
        <div class="bar-track"><div class="bar-fill" style="--w:5%; --d:1.5s;"></div></div>
      </div>
    </div>
  </section>

  <div class="divider anim-fi d8"></div>

  <!-- SKILLS -->
  <section class="section anim-fu d8">
    <p class="section-label">04 — stack</p>
    <div class="skills">
      <span class="skill-tag">node.js</span>
      <span class="skill-tag">react</span>
      <span class="skill-tag">next.js</span>
      <span class="skill-tag">rust</span>
      <span class="skill-tag">go</span>
      <span class="skill-tag">docker</span>
      <span class="skill-tag">kubernetes</span>
      <span class="skill-tag">postgresql</span>
      <span class="skill-tag">redis</span>
      <span class="skill-tag">graphql</span>
      <span class="skill-tag">terraform</span>
      <span class="skill-tag">linux</span>
      <span class="skill-tag">neovim</span>
      <span class="skill-tag">git</span>
      <span class="skill-tag">ci/cd</span>
      <span class="skill-tag">llm apis</span>
    </div>
  </section>

  <div class="divider anim-fi d9"></div>

  <!-- ACTIVITY GRID -->
  <section class="section anim-fd d9">
    <p class="section-label">05 — contribution graph</p>
    <div class="activity-grid" id="agrid"></div>
  </section>

  <div class="divider anim-fi d10"></div>

  <!-- REPOS -->
  <section class="section anim-fu d10">
    <p class="section-label">06 — pinned repos</p>
    <div class="repo-grid">
      <div class="repo-card">
        <div class="repo-name">◆ noctis-cli</div>
        <div class="repo-desc">a minimal, fast CLI toolkit for terminal workflows. pipes. filters. beauty.</div>
        <div class="repo-meta">
          <span class="repo-lang"><span class="repo-lang-dot"></span>Rust</span>
          <span class="repo-stars">★ 312</span>
        </div>
      </div>
      <div class="repo-card">
        <div class="repo-name">◆ void-db</div>
        <div class="repo-desc">embedded key-value store with zero-copy reads and WAL persistence.</div>
        <div class="repo-meta">
          <span class="repo-lang"><span class="repo-lang-dot"></span>Go</span>
          <span class="repo-stars">★ 207</span>
        </div>
      </div>
      <div class="repo-card">
        <div class="repo-name">◆ shade-ui</div>
        <div class="repo-desc">monochromatic component library. dark by default. no opinions, just shadows.</div>
        <div class="repo-meta">
          <span class="repo-lang"><span class="repo-lang-dot"></span>TypeScript</span>
          <span class="repo-stars">★ 184</span>
        </div>
      </div>
      <div class="repo-card">
        <div class="repo-name">◆ signal-rs</div>
        <div class="repo-desc">reactive state primitives for Rust. fine-grained, zero-alloc subscriptions.</div>
        <div class="repo-meta">
          <span class="repo-lang"><span class="repo-lang-dot"></span>Rust</span>
          <span class="repo-stars">★ 96</span>
        </div>
      </div>
    </div>
  </section>

  <div class="divider anim-fi d11"></div>

  <!-- FOOTER -->
  <footer class="footer anim-fi d12">
    <p class="footer-text">// last sync: 2026-05-30 · generated by readme engine v0.9.1</p>
  </footer>

</div>

<script>
  const grid = document.getElementById('agrid');
  const levels = [0,0,0,1,1,1,2,2,3,4];
  for (let i = 0; i < 52 * 7; i++) {
    const cell = document.createElement('div');
    const lvl = levels[Math.floor(Math.random() * levels.length)];
    cell.className = 'activity-cell' + (lvl > 0 ? ' l' + lvl : '');
    grid.appendChild(cell);
  }
</script>
</body>
</html>
