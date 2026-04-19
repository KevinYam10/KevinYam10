<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<style>
  @import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&family=Share+Tech+Mono&display=swap');

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: #0a0a0f;
    color: #c9d1d9;
    font-family: 'Share Tech Mono', monospace;
    font-size: 13px;
    line-height: 1.6;
    padding: 32px 20px;
    min-height: 100vh;
  }

  .readme {
    max-width: 860px;
    margin: 0 auto;
    background: #0d1117;
    border: 2px solid #30363d;
    padding: 32px;
    image-rendering: pixelated;
  }

  /* Pixel heading */
  .pixel-title {
    font-family: 'Press Start 2P', monospace;
    font-size: 13px;
    color: #58a6ff;
    letter-spacing: 2px;
    text-shadow: 0 0 12px #58a6ff88, 2px 2px 0 #003366;
    margin-bottom: 4px;
    animation: flicker 4s infinite;
  }
  .pixel-sub {
    font-family: 'Press Start 2P', monospace;
    font-size: 8px;
    color: #3fb950;
    letter-spacing: 1px;
    text-shadow: 0 0 8px #3fb95066;
    margin-bottom: 24px;
  }

  @keyframes flicker {
    0%,96%,100% { opacity:1; }
    97% { opacity:0.7; }
    98% { opacity:1; }
    99% { opacity:0.6; }
  }

  /* Blinking cursor */
  .cursor::after {
    content: '█';
    animation: blink 1s step-end infinite;
    color: #3fb950;
    margin-left: 4px;
  }
  @keyframes blink { 50% { opacity: 0; } }

  /* Pixel divider */
  .px-divider {
    height: 2px;
    background: repeating-linear-gradient(
      90deg,
      #30363d 0px, #30363d 4px,
      transparent 4px, transparent 8px
    );
    margin: 20px 0;
  }

  /* Section label */
  .section-label {
    font-family: 'Press Start 2P', monospace;
    font-size: 7px;
    color: #8b949e;
    letter-spacing: 3px;
    text-transform: uppercase;
    margin-bottom: 12px;
  }

  /* About block */
  .about-grid {
    display: grid;
    grid-template-columns: auto 1fr;
    gap: 20px;
    align-items: start;
    margin-bottom: 24px;
  }

  .pixel-avatar {
    width: 96px;
    height: 96px;
    image-rendering: pixelated;
    border: 3px solid #30363d;
    box-shadow: 4px 4px 0 #58a6ff44;
    flex-shrink: 0;
    position: relative;
    overflow: hidden;
  }

  /* SVG pixel art character */
  .avatar-svg {
    width: 96px;
    height: 96px;
  }

  .about-text p {
    color: #8b949e;
    margin-bottom: 6px;
    font-size: 12px;
  }
  .about-text p span {
    color: #c9d1d9;
  }
  .about-text .highlight {
    color: #58a6ff;
  }

  /* Stats row */
  .stats-row {
    display: flex;
    gap: 12px;
    flex-wrap: wrap;
    margin-bottom: 24px;
  }

  .stat-card {
    background: #161b22;
    border: 1px solid #30363d;
    padding: 10px 14px;
    flex: 1;
    min-width: 120px;
    position: relative;
  }
  .stat-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0;
    width: 4px; height: 100%;
    background: var(--accent);
  }
  .stat-label {
    font-size: 10px;
    color: #8b949e;
    display: block;
    margin-bottom: 4px;
  }
  .stat-val {
    font-family: 'Press Start 2P', monospace;
    font-size: 10px;
    color: var(--accent);
    text-shadow: 0 0 8px var(--accent);
  }

  /* Tech stack */
  .tech-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
    gap: 8px;
    margin-bottom: 24px;
  }

  .tech-item {
    background: #161b22;
    border: 1px solid #30363d;
    padding: 8px 12px;
    display: flex;
    align-items: center;
    gap: 8px;
    transition: border-color 0.15s;
    cursor: default;
  }
  .tech-item:hover {
    border-color: var(--c);
    box-shadow: inset 0 0 12px var(--c)22;
  }
  .tech-icon {
    font-size: 16px;
    width: 20px;
    text-align: center;
  }
  .tech-name {
    font-size: 11px;
    color: #c9d1d9;
  }
  .tech-level {
    margin-left: auto;
    font-size: 9px;
    color: var(--c);
    font-family: 'Press Start 2P', monospace;
  }

  /* Skill bar */
  .skill-row {
    margin-bottom: 10px;
  }
  .skill-header {
    display: flex;
    justify-content: space-between;
    margin-bottom: 4px;
  }
  .skill-name { font-size: 11px; color: #c9d1d9; }
  .skill-pct { font-size: 10px; color: #8b949e; }
  .skill-bar-bg {
    height: 8px;
    background: #21262d;
    position: relative;
    image-rendering: pixelated;
  }
  .skill-bar-fill {
    height: 100%;
    background: repeating-linear-gradient(
      90deg,
      var(--bc) 0px, var(--bc) 6px,
      transparent 6px, transparent 8px
    );
    box-shadow: 0 0 6px var(--bc);
    width: 0;
    transition: width 1.2s ease;
  }

  /* Projects */
  .project-card {
    background: #161b22;
    border: 1px solid #30363d;
    padding: 14px;
    margin-bottom: 8px;
    position: relative;
    transition: border-color 0.2s;
  }
  .project-card:hover { border-color: #58a6ff; }
  .project-card::after {
    content: '▶';
    position: absolute;
    right: 12px;
    top: 14px;
    font-size: 10px;
    color: #30363d;
  }
  .proj-name {
    font-family: 'Press Start 2P', monospace;
    font-size: 8px;
    color: #58a6ff;
    margin-bottom: 6px;
  }
  .proj-desc { font-size: 11px; color: #8b949e; }
  .proj-tag {
    display: inline-block;
    background: #21262d;
    border: 1px solid #30363d;
    padding: 2px 6px;
    font-size: 10px;
    color: #3fb950;
    margin-top: 6px;
    margin-right: 4px;
  }

  /* Footer */
  .px-footer {
    text-align: center;
    padding-top: 16px;
  }
  .px-footer .pixel-text {
    font-family: 'Press Start 2P', monospace;
    font-size: 7px;
    color: #3fb950;
    letter-spacing: 2px;
    animation: flicker 3s infinite;
  }

  /* Scanlines overlay */
  .scanlines {
    pointer-events: none;
    position: fixed;
    top: 0; left: 0; right: 0; bottom: 0;
    background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0,0,0,0.05) 2px,
      rgba(0,0,0,0.05) 4px
    );
    z-index: 999;
  }

  /* Badge-style gif placeholders */
  .badges {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
    margin-bottom: 16px;
  }
  .badge {
    background: #161b22;
    border: 1px solid #30363d;
    padding: 4px 10px;
    font-size: 10px;
    color: #c9d1d9;
    display: flex;
    align-items: center;
    gap: 5px;
  }
  .badge .dot {
    width: 6px; height: 6px;
    background: var(--dc);
    display: inline-block;
    animation: pulse 2s infinite;
  }
  @keyframes pulse { 0%,100%{opacity:1} 50%{opacity:0.3} }
</style>
</head>
<body>
<div class="scanlines"></div>
<div class="readme">

  <!-- HEADER -->
  <div class="pixel-title cursor">KEVIN EFREN YAM HUICAB</div>
  <div class="pixel-sub">// SOFTWARE DEVELOPER · CAMPECHE, MX</div>

  <div class="badges">
    <span class="badge"><span class="dot" style="--dc:#3fb950"></span>Android Dev</span>
    <span class="badge"><span class="dot" style="--dc:#58a6ff"></span>Flutter</span>
    <span class="badge"><span class="dot" style="--dc:#f78166"></span>Backend Integration</span>
    <span class="badge"><span class="dot" style="--dc:#d2a8ff"></span>Open to collab</span>
  </div>

  <div class="px-divider"></div>

  <!-- ABOUT -->
  <div class="section-label">// about.txt</div>
  <div class="about-grid">
    <div class="pixel-avatar">
      <svg class="avatar-svg" viewBox="0 0 16 16" xmlns="http://www.w3.org/2000/svg" style="image-rendering:pixelated">
        <!-- dark bg -->
        <rect width="16" height="16" fill="#0d1117"/>
        <!-- head -->
        <rect x="4" y="1" width="8" height="7" fill="#c9a26d"/>
        <!-- hair -->
        <rect x="4" y="1" width="8" height="2" fill="#1a1005"/>
        <rect x="3" y="2" width="1" height="3" fill="#1a1005"/>
        <rect x="12" y="2" width="1" height="3" fill="#1a1005"/>
        <!-- eyes -->
        <rect x="5" y="5" width="2" height="1" fill="#58a6ff"/>
        <rect x="9" y="5" width="2" height="1" fill="#58a6ff"/>
        <!-- smile -->
        <rect x="6" y="7" width="4" height="1" fill="#f0c08a"/>
        <rect x="5" y="6" width="1" height="1" fill="#c9a26d"/>
        <rect x="10" y="6" width="1" height="1" fill="#c9a26d"/>
        <!-- body: dark shirt -->
        <rect x="3" y="8" width="10" height="5" fill="#161b22"/>
        <!-- collar accent -->
        <rect x="6" y="8" width="4" height="1" fill="#30363d"/>
        <!-- code symbol on shirt -->
        <rect x="7" y="10" width="2" height="1" fill="#3fb950"/>
        <!-- arms -->
        <rect x="1" y="8" width="2" height="4" fill="#c9a26d"/>
        <rect x="13" y="8" width="2" height="4" fill="#c9a26d"/>
        <!-- legs -->
        <rect x="4" y="13" width="3" height="3" fill="#21262d"/>
        <rect x="9" y="13" width="3" height="3" fill="#21262d"/>
      </svg>
    </div>
    <div class="about-text">
      <p>👾 <span>Desarrollador de software</span> con enfoque en <span class="highlight">apps móviles Android</span> y <span class="highlight">Flutter</span>.</p>
      <p>📍 <span>Hecelchakán, Campeche, México</span></p>
      <p>🔧 Trabajo con <span>Kotlin · Dart · Java · REST APIs · BLoC</span></p>
      <p>📄 Experto en automatización de documentos <span>(DOCX, PPTX, JSON)</span></p>
      <p>🧠 Me gusta construir herramientas que hagan el trabajo <span class="highlight">más cómodo y rápido</span>.</p>
      <p>🎯 <span>Actualmente enfocado</span> en proyectos de gestión y campo.</p>
    </div>
  </div>

  <div class="px-divider"></div>

  <!-- STATS -->
  <div class="section-label">// stats.json</div>
  <div class="stats-row">
    <div class="stat-card" style="--accent:#3fb950">
      <span class="stat-label">REPOS</span>
      <span class="stat-val">2+</span>
    </div>
    <div class="stat-card" style="--accent:#58a6ff">
      <span class="stat-label">ACHIEVEMENTS</span>
      <span class="stat-val">5 🏆</span>
    </div>
    <div class="stat-card" style="--accent:#d2a8ff">
      <span class="stat-label">MAIN LANG</span>
      <span class="stat-val">DART</span>
    </div>
    <div class="stat-card" style="--accent:#f78166">
      <span class="stat-label">FOCUS</span>
      <span class="stat-val">MOBILE</span>
    </div>
  </div>

  <div class="px-divider"></div>

  <!-- SKILLS -->
  <div class="section-label">// skills.exe</div>
  <div style="margin-bottom:24px">
    <div class="skill-row">
      <div class="skill-header"><span class="skill-name">Android / Kotlin</span><span class="skill-pct">85%</span></div>
      <div class="skill-bar-bg"><div class="skill-bar-fill" style="--bc:#3fb950;width:85%"></div></div>
    </div>
    <div class="skill-row">
      <div class="skill-header"><span class="skill-name">Flutter / Dart</span><span class="skill-pct">80%</span></div>
      <div class="skill-bar-bg"><div class="skill-bar-fill" style="--bc:#58a6ff;width:80%"></div></div>
    </div>
    <div class="skill-row">
      <div class="skill-header"><span class="skill-name">REST APIs / JSON</span><span class="skill-pct">88%</span></div>
      <div class="skill-bar-bg"><div class="skill-bar-fill" style="--bc:#d2a8ff;width:88%"></div></div>
    </div>
    <div class="skill-row">
      <div class="skill-header"><span class="skill-name">Automatización DOCX/PPTX</span><span class="skill-pct">82%</span></div>
      <div class="skill-bar-bg"><div class="skill-bar-fill" style="--bc:#f78166;width:82%"></div></div>
    </div>
    <div class="skill-row">
      <div class="skill-header"><span class="skill-name">BLoC / State Management</span><span class="skill-pct">75%</span></div>
      <div class="skill-bar-bg"><div class="skill-bar-fill" style="--bc:#ffa657;width:75%"></div></div>
    </div>
    <div class="skill-row">
      <div class="skill-header"><span class="skill-name">BigQuery / SQL</span><span class="skill-pct">70%</span></div>
      <div class="skill-bar-bg"><div class="skill-bar-fill" style="--bc:#3fb950;width:70%"></div></div>
    </div>
  </div>

  <div class="px-divider"></div>

  <!-- TECH STACK -->
  <div class="section-label">// stack.config</div>
  <div class="tech-grid">
    <div class="tech-item" style="--c:#3fb950"><span class="tech-icon">🤖</span><span class="tech-name">Android Studio</span><span class="tech-level">●●●●○</span></div>
    <div class="tech-item" style="--c:#58a6ff"><span class="tech-icon">🐦</span><span class="tech-name">Flutter</span><span class="tech-level">●●●●○</span></div>
    <div class="tech-item" style="--c:#d2a8ff"><span class="tech-icon">🎯</span><span class="tech-name">Dart</span><span class="tech-level">●●●●○</span></div>
    <div class="tech-item" style="--c:#ffa657"><span class="tech-icon">☕</span><span class="tech-name">Kotlin</span><span class="tech-level">●●●●○</span></div>
    <div class="tech-item" style="--c:#f78166"><span class="tech-icon">🔥</span><span class="tech-name">Firebase</span><span class="tech-level">●●●○○</span></div>
    <div class="tech-item" style="--c:#3fb950"><span class="tech-icon">🗄️</span><span class="tech-name">SQLite / Drift</span><span class="tech-level">●●●○○</span></div>
    <div class="tech-item" style="--c:#58a6ff"><span class="tech-icon">📡</span><span class="tech-name">REST / Retrofit</span><span class="tech-level">●●●●●</span></div>
    <div class="tech-item" style="--c:#d2a8ff"><span class="tech-icon">📊</span><span class="tech-name">BigQuery / JSON</span><span class="tech-level">●●●●○</span></div>
  </div>

  <div class="px-divider"></div>

  <!-- PROJECTS -->
  <div class="section-label">// projects/</div>
  <div class="project-card">
    <div class="proj-name">📦 InvetariApp</div>
    <div class="proj-desc">App Android para creación de inventarios personalizados, editables y descargables. Diseñada para ser cómoda y sencilla para cualquier usuario.</div>
    <span class="proj-tag">Dart</span>
    <span class="proj-tag">Flutter</span>
    <span class="proj-tag">SQLite</span>
  </div>
  <div class="project-card">
    <div class="proj-name">🗺️ App de Gestión Territorial</div>
    <div class="proj-desc">Sistema móvil para levantamiento de ciudadanos en campo: captación, visitas, fotos con geolocalización, sincronización con web.</div>
    <span class="proj-tag">Android</span>
    <span class="proj-tag">Kotlin</span>
    <span class="proj-tag">REST API</span>
    <span class="proj-tag">Mapas</span>
  </div>
  <div class="project-card">
    <div class="proj-name">💰 PreciOfertas (WIP)</div>
    <div class="proj-desc">Agregadora de precios de MercadoLibre, Amazon y Walmart. Alertas en tiempo real cuando un producto baja de precio.</div>
    <span class="proj-tag">Flutter</span>
    <span class="proj-tag">BLoC</span>
    <span class="proj-tag">Firebase</span>
    <span class="proj-tag">APIs</span>
  </div>

  <div class="px-divider"></div>

  <!-- FOOTER -->
  <div class="px-footer">
    <div class="pixel-text">[ PRESS START TO COLLABORATE ]</div>
    <div style="margin-top:10px;font-size:10px;color:#8b949e">
      github.com/KevinYam10 · Hecelchakán, Camp. MX
    </div>
  </div>

</div>
</body>
</html>
