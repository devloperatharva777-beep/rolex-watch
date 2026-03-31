# rolex-watch
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>ROLEX — Timeless Precision</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Playfair+Display:wght@400;500;600;700&display=swap" rel="stylesheet" />
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --gold: #c8a96e;
      --gold-light: #e2c98a;
      --dark: #0a0a0a;
      --dark2: #111111;
      --dark3: #1a1a1a;
      --text: #f0ece4;
      --muted: #888;
    }

    html { scroll-behavior: smooth; }

    body {
      background: var(--dark);
      color: var(--text);
      font-family: 'Inter', sans-serif;
      overflow-x: hidden;
    }

    /* NAV */
    nav {
      position: fixed; top: 0; left: 0; right: 0;
      z-index: 100;
      display: flex; align-items: center; justify-content: space-between;
      padding: 20px 60px;
      background: rgba(10,10,10,0.85);
      backdrop-filter: blur(12px);
      border-bottom: 1px solid rgba(200,169,110,0.15);
    }
    .nav-logo {
      font-family: 'Playfair Display', serif;
      font-size: 22px;
      letter-spacing: 6px;
      color: var(--gold);
      text-transform: uppercase;
    }
    .nav-links { display: flex; gap: 40px; list-style: none; }
    .nav-links a {
      text-decoration: none;
      font-size: 12px;
      letter-spacing: 3px;
      text-transform: uppercase;
      color: var(--muted);
      transition: color 0.3s;
    }
    .nav-links a:hover { color: var(--gold); }
    .nav-cta {
      font-size: 11px; letter-spacing: 2px; text-transform: uppercase;
      padding: 10px 24px;
      border: 1px solid var(--gold);
      color: var(--gold);
      background: transparent;
      cursor: pointer;
      transition: all 0.3s;
    }
    .nav-cta:hover { background: var(--gold); color: var(--dark); }

    /* HERO */
    #hero {
      position: relative;
      width: 100%; height: 100vh;
      display: flex; align-items: center; justify-content: space-between;
      padding: 0 60px;
      overflow: hidden;
    }
    .hero-left {
      z-index: 2;
      max-width: 480px;
    }
    .hero-tag {
      font-size: 11px; letter-spacing: 4px; text-transform: uppercase;
      color: var(--gold); margin-bottom: 20px;
      display: flex; align-items: center; gap: 12px;
    }
    .hero-tag::before {
      content: ''; width: 40px; height: 1px; background: var(--gold);
    }
    .hero-title {
      font-family: 'Playfair Display', serif;
      font-size: clamp(48px, 6vw, 88px);
      line-height: 1.05;
      margin-bottom: 24px;
      color: var(--text);
    }
    .hero-title span { color: var(--gold); }
    .hero-subtitle {
      font-size: 14px; line-height: 1.8; color: var(--muted);
      margin-bottom: 40px; max-width: 360px;
    }
    .hero-btns { display: flex; gap: 16px; align-items: center; }
    .btn-primary {
      padding: 14px 36px;
      background: var(--gold);
      color: var(--dark);
      font-size: 11px; letter-spacing: 3px; text-transform: uppercase;
      border: none; cursor: pointer;
      font-family: 'Inter', sans-serif;
      font-weight: 600;
      transition: all 0.3s;
    }
    .btn-primary:hover { background: var(--gold-light); }
    .btn-ghost {
      font-size: 11px; letter-spacing: 3px; text-transform: uppercase;
      color: var(--muted); background: none; border: none;
      cursor: pointer; font-family: 'Inter', sans-serif;
      transition: color 0.3s;
      text-decoration: underline; text-underline-offset: 4px;
    }
    .btn-ghost:hover { color: var(--gold); }

    /* CANVAS */
    #watch-canvas {
      position: absolute;
      top: 0; left: 0;
      width: 100%; height: 100%;
      z-index: 1;
    }

    /* SCROLL INDICATOR */
    .scroll-hint {
      position: absolute; bottom: 40px; left: 50%;
      transform: translateX(-50%);
      z-index: 10;
      display: flex; flex-direction: column; align-items: center; gap: 8px;
      font-size: 10px; letter-spacing: 3px; text-transform: uppercase;
      color: var(--muted);
    }
    .scroll-line {
      width: 1px; height: 48px;
      background: linear-gradient(to bottom, var(--gold), transparent);
      animation: scrollPulse 1.8s ease-in-out infinite;
    }
    @keyframes scrollPulse {
      0%, 100% { opacity: 0.3; transform: scaleY(1); }
      50% { opacity: 1; transform: scaleY(1.15); }
    }

    /* STATS BAR */
    .stats-bar {
      display: flex;
      border-top: 1px solid rgba(200,169,110,0.12);
      border-bottom: 1px solid rgba(200,169,110,0.12);
    }
    .stat-item {
      flex: 1;
      padding: 36px 40px;
      border-right: 1px solid rgba(200,169,110,0.12);
      text-align: center;
    }
    .stat-item:last-child { border-right: none; }
    .stat-num {
      font-family: 'Playfair Display', serif;
      font-size: 36px; color: var(--gold);
      margin-bottom: 6px;
    }
    .stat-label {
      font-size: 10px; letter-spacing: 3px; text-transform: uppercase;
      color: var(--muted);
    }

    /* SECTIONS */
    section { padding: 120px 60px; }

    .section-tag {
      font-size: 10px; letter-spacing: 4px; text-transform: uppercase;
      color: var(--gold); margin-bottom: 16px;
      display: flex; align-items: center; gap: 12px;
    }
    .section-tag::before { content: ''; width: 28px; height: 1px; background: var(--gold); }
    .section-title {
      font-family: 'Playfair Display', serif;
      font-size: clamp(32px, 4vw, 52px);
      line-height: 1.15;
      margin-bottom: 20px;
    }
    .section-desc {
      font-size: 14px; line-height: 1.9; color: var(--muted);
      max-width: 480px;
    }

    /* FEATURES */
    #features { background: var(--dark2); }
    .features-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 2px;
      margin-top: 60px;
    }
    .feature-card {
      background: var(--dark3);
      padding: 48px 40px;
      transition: background 0.3s;
      position: relative; overflow: hidden;
    }
    .feature-card::before {
      content: '';
      position: absolute; top: 0; left: 0; right: 0;
      height: 2px;
      background: linear-gradient(to right, transparent, var(--gold), transparent);
      transform: scaleX(0);
      transition: transform 0.4s;
    }
    .feature-card:hover::before { transform: scaleX(1); }
    .feature-card:hover { background: #1f1f1f; }
    .feature-icon {
      width: 48px; height: 48px;
      border: 1px solid rgba(200,169,110,0.3);
      display: flex; align-items: center; justify-content: center;
      margin-bottom: 24px; font-size: 20px;
    }
    .feature-title {
      font-family: 'Playfair Display', serif;
      font-size: 20px; margin-bottom: 12px;
    }
    .feature-text { font-size: 13px; line-height: 1.8; color: var(--muted); }

    /* COLLECTION */
    #collection { background: var(--dark); }
    .collection-header {
      display: flex; align-items: flex-end;
      justify-content: space-between;
      margin-bottom: 60px;
    }
    .collection-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 24px;
    }
    .watch-card {
      background: var(--dark3);
      border: 1px solid rgba(200,169,110,0.08);
      padding: 40px 32px;
      position: relative;
      transition: border-color 0.3s, transform 0.3s;
      cursor: pointer;
    }
    .watch-card:hover {
      border-color: rgba(200,169,110,0.4);
      transform: translateY(-6px);
    }
    .watch-badge {
      position: absolute; top: 20px; right: 20px;
      font-size: 9px; letter-spacing: 2px; text-transform: uppercase;
      padding: 4px 10px;
      background: var(--gold); color: var(--dark);
    }
    .watch-mini-canvas {
      width: 100%; height: 200px;
      margin-bottom: 24px;
    }
    .watch-name {
      font-family: 'Playfair Display', serif;
      font-size: 22px; margin-bottom: 6px;
    }
    .watch-ref { font-size: 11px; letter-spacing: 2px; color: var(--muted); margin-bottom: 16px; }
    .watch-price { font-size: 18px; color: var(--gold); font-weight: 500; }
    .watch-price-label { font-size: 10px; color: var(--muted); letter-spacing: 2px; }

    /* SPECS */
    #specs { background: var(--dark2); }
    .specs-layout {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 80px;
      align-items: center;
      margin-top: 60px;
    }
    .specs-list { display: flex; flex-direction: column; gap: 0; }
    .spec-row {
      display: flex; justify-content: space-between; align-items: center;
      padding: 20px 0;
      border-bottom: 1px solid rgba(200,169,110,0.08);
    }
    .spec-key { font-size: 12px; letter-spacing: 2px; text-transform: uppercase; color: var(--muted); }
    .spec-val { font-size: 14px; color: var(--text); font-weight: 500; }
    .specs-canvas { width: 100%; height: 420px; }

    /* TESTIMONIAL */
    #testimonial {
      background: var(--dark);
      text-align: center;
      padding: 100px 60px;
    }
    .quote-mark {
      font-family: 'Playfair Display', serif;
      font-size: 80px; color: var(--gold); opacity: 0.3;
      line-height: 0.5; margin-bottom: 32px;
    }
    .quote-text {
      font-family: 'Playfair Display', serif;
      font-size: clamp(20px, 2.5vw, 32px);
      max-width: 720px; margin: 0 auto 32px;
      line-height: 1.5; color: var(--text);
    }
    .quote-author { font-size: 11px; letter-spacing: 4px; text-transform: uppercase; color: var(--gold); }

    /* FOOTER */
    footer {
      background: #050505;
      padding: 60px;
      border-top: 1px solid rgba(200,169,110,0.1);
      display: flex; align-items: center; justify-content: space-between;
    }
    .footer-logo {
      font-family: 'Playfair Display', serif;
      font-size: 20px; letter-spacing: 6px; color: var(--gold);
    }
    .footer-links { display: flex; gap: 32px; }
    .footer-links a {
      font-size: 11px; letter-spacing: 2px; text-transform: uppercase;
      color: var(--muted); text-decoration: none; transition: color 0.3s;
    }
    .footer-links a:hover { color: var(--gold); }
    .footer-copy { font-size: 11px; color: var(--muted); letter-spacing: 1px; }

    /* DIVIDER */
    .gold-divider {
      width: 60px; height: 1px;
      background: var(--gold);
      margin: 24px 0;
    }
  </style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-logo">Rolex</div>
  <ul class="nav-links">
    <li><a href="#hero">Home</a></li>
    <li><a href="#features">Craftsmanship</a></li>
    <li><a href="#collection">Collection</a></li>
    <li><a href="#specs">Movement</a></li>
  </ul>
  <button class="nav-cta">Book a Visit</button>
</nav>

<!-- HERO -->
<section id="hero">
  <canvas id="watch-canvas"></canvas>
  <div class="hero-left">
    <div class="hero-tag">Since 1905</div>
    <h1 class="hero-title">A Crown<br/>for Every<br/><span>Achievement</span></h1>
    <p class="hero-subtitle">
      Masterpieces of Swiss precision engineering, designed to endure through generations and mark every milestone.
    </p>
    <div class="hero-btns">
      <button class="btn-primary" onclick="document.getElementById('collection').scrollIntoView({behavior:'smooth'})">Explore Collection</button>
      <button class="btn-ghost" onclick="document.getElementById('specs').scrollIntoView({behavior:'smooth'})">View Movement</button>
    </div>
  </div>
  <div class="scroll-hint">
    <div class="scroll-line"></div>
    Scroll
  </div>
</section>

<!-- STATS -->
<div class="stats-bar">
  <div class="stat-item"><div class="stat-num">1905</div><div class="stat-label">Founded</div></div>
  <div class="stat-item"><div class="stat-num">38+</div><div class="stat-label">Movements In-House</div></div>
  <div class="stat-item"><div class="stat-num">100%</div><div class="stat-label">Swiss Made</div></div>
  <div class="stat-item"><div class="stat-num">200m</div><div class="stat-label">Water Resistance</div></div>
</div>

<!-- FEATURES -->
<section id="features">
  <div class="section-tag">Craftsmanship</div>
  <h2 class="section-title">Engineered for<br/>Eternity</h2>
  <p class="section-desc">Every Rolex is born from a relentless pursuit of perfection — combining centuries-old artisanal expertise with modern precision technology.</p>

  <div class="features-grid">
    <div class="feature-card">
      <div class="feature-icon">⚙️</div>
      <div class="feature-title">In-House Movement</div>
      <p class="feature-text">Every movement is entirely designed, developed, and manufactured in Rolex's Geneva facilities to exacting tolerances.</p>
    </div>
    <div class="feature-card">
      <div class="feature-icon">💎</div>
      <div class="feature-title">Oystersteel</div>
      <p class="feature-text">A unique alloy from the 904L steel family — more corrosion-resistant and brilliantly polished than standard surgical steel.</p>
    </div>
    <div class="feature-card">
      <div class="feature-icon">🛡️</div>
      <div class="feature-title">Oyster Case</div>
      <p class="feature-text">The world's first waterproof wristwatch case. Hermetically sealed to protect the movement against water, dust, and pressure.</p>
    </div>
    <div class="feature-card">
      <div class="feature-icon">🔋</div>
      <div class="feature-title">Perpetual Rotor</div>
      <p class="feature-text">The self-winding Perpetual rotor continuously harnesses energy from the wearer's wrist to power the movement indefinitely.</p>
    </div>
    <div class="feature-card">
      <div class="feature-icon">🌡️</div>
      <div class="feature-title">Superlative Chronometer</div>
      <p class="feature-text">Independently tested and certified by COSC, then further regulated by Rolex to ±2 seconds per day accuracy.</p>
    </div>
    <div class="feature-card">
      <div class="feature-icon">✨</div>
      <div class="feature-title">Parachrom Hairspring</div>
      <p class="feature-text">Made from a paramagnetic alloy that is 10× more resistant to shocks and impervious to magnetic fields.</p>
    </div>
  </div>
</section>

<!-- COLLECTION -->
<section id="collection">
  <div class="collection-header">
    <div>
      <div class="section-tag">Models</div>
      <h2 class="section-title">Iconic<br/>Collection</h2>
    </div>
    <p class="section-desc" style="max-width:320px;">Each model is a universe of its own — shaped by decades of refinement and purpose.</p>
  </div>
  <div class="collection-grid">
    <div class="watch-card">
      <div class="watch-badge">Bestseller</div>
      <canvas class="watch-mini-canvas" id="c1"></canvas>
      <div class="watch-name">Submariner</div>
      <div class="watch-ref">Ref. 126610LN</div>
      <div class="watch-price-label">Starting From</div>
      <div class="watch-price">$9,150</div>
    </div>
    <div class="watch-card">
      <canvas class="watch-mini-canvas" id="c2"></canvas>
      <div class="watch-name">Daytona</div>
      <div class="watch-ref">Ref. 116500LN</div>
      <div class="watch-price-label">Starting From</div>
      <div class="watch-price">$14,550</div>
    </div>
    <div class="watch-card">
      <div class="watch-badge">New</div>
      <canvas class="watch-mini-canvas" id="c3"></canvas>
      <div class="watch-name">GMT-Master II</div>
      <div class="watch-ref">Ref. 126710BLRO</div>
      <div class="watch-price-label">Starting From</div>
      <div class="watch-price">$10,700</div>
    </div>
  </div>
</section>

<!-- SPECS -->
<section id="specs">
  <div class="section-tag">Technical Excellence</div>
  <h2 class="section-title">The Calibre 3235<br/>Movement</h2>
  <div class="specs-layout">
    <div class="specs-list">
      <div class="spec-row"><span class="spec-key">Calibre</span><span class="spec-val">3235</span></div>
      <div class="spec-row"><span class="spec-key">Type</span><span class="spec-val">Automatic, Self-Winding</span></div>
      <div class="spec-row"><span class="spec-key">Diameter</span><span class="spec-val">28.80 mm</span></div>
      <div class="spec-row"><span class="spec-key">Jewels</span><span class="spec-val">31</span></div>
      <div class="spec-row"><span class="spec-key">Frequency</span><span class="spec-val">28,800 vph (4 Hz)</span></div>
      <div class="spec-row"><span class="spec-key">Power Reserve</span><span class="spec-val">Approx. 70 hours</span></div>
      <div class="spec-row"><span class="spec-key">Certification</span><span class="spec-val">Superlative Chronometer</span></div>
      <div class="spec-row"><span class="spec-key">Water Resistance</span><span class="spec-val">300 m / 1,000 ft</span></div>
    </div>
    <canvas class="specs-canvas" id="specs-canvas"></canvas>
  </div>
</section>

<!-- TESTIMONIAL -->
<section id="testimonial">
  <div class="quote-mark">"</div>
  <p class="quote-text">A Rolex doesn't just tell the time — it tells your story. It's a companion to the moments that define a life.</p>
  <div class="gold-divider" style="margin: 0 auto 20px;"></div>
  <div class="quote-author">— The Rolex Philosophy</div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">Rolex</div>
  <div class="footer-links">
    <a href="#">Watches</a>
    <a href="#">Certified Pre-Owned</a>
    <a href="#">Retailers</a>
    <a href="#">Heritage</a>
    <a href="#">Contact</a>
  </div>
  <div class="footer-copy">© 2024 Rolex SA, Geneva</div>
</footer>

<!-- THREE.JS -->
<script type="importmap">
{
  "imports": {
    "three": "https://cdn.jsdelivr.net/npm/three@0.167.0/build/three.module.js",
    "three/addons/": "https://cdn.jsdelivr.net/npm/three@0.167.0/examples/jsm/"
  }
}
</script>
<script type="module">
import * as THREE from 'three';
import { OrbitControls } from 'three/addons/controls/OrbitControls.js';

const GOLD = 0xc8a96e;
const DARK_GOLD = 0x8a6f3a;
const BLACK = 0x0d0d0d;
const SILVER = 0xcccccc;
const WHITE = 0xffffff;

// ─── HERO 3D WATCH ───────────────────────────────────────────────
function buildHeroWatch() {
  const canvas = document.getElementById('watch-canvas');
  const W = window.innerWidth, H = window.innerHeight;
  const renderer = new THREE.WebGLRenderer({ canvas, antialias: true, alpha: true });
  renderer.setSize(W, H);
  renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));
  renderer.shadowMap.enabled = true;
  renderer.shadowMap.type = THREE.PCFSoftShadowMap;
  renderer.outputColorSpace = THREE.SRGBColorSpace;
  renderer.toneMapping = THREE.ACESFilmicToneMapping;
  renderer.toneMappingExposure = 1.2;

  const scene = new THREE.Scene();
  const camera = new THREE.PerspectiveCamera(45, W / H, 0.1, 100);
  camera.position.set(3.5, 1.5, 5);
  camera.lookAt(0, 0, 0);

  // Lights
  const ambient = new THREE.AmbientLight(0xffffff, 0.3);
  scene.add(ambient);

  const keyLight = new THREE.DirectionalLight(0xfff5e0, 2.5);
  keyLight.position.set(5, 8, 5);
  keyLight.castShadow = true;
  keyLight.shadow.mapSize.set(2048, 2048);
  keyLight.shadow.camera.near = 0.1;
  keyLight.shadow.camera.far = 30;
  keyLight.shadow.camera.left = -10;
  keyLight.shadow.camera.right = 10;
  keyLight.shadow.camera.top = 10;
  keyLight.shadow.camera.bottom = -10;
  scene.add(keyLight);

  const fillLight = new THREE.PointLight(0xc8a96e, 1.5, 20);
  fillLight.position.set(-4, 2, 3);
  scene.add(fillLight);

  const rimLight = new THREE.DirectionalLight(0xffffff, 1.2);
  rimLight.position.set(-3, 3, -5);
  scene.add(rimLight);

  const watch = new THREE.Group();
  watch.name = 'heroWatch';
  scene.add(watch);

  // CASE
  const caseMat = new THREE.MeshStandardMaterial({
    color: 0xb8b8b8, metalness: 0.95, roughness: 0.12,
    envMapIntensity: 1.2
  });
  const caseGeo = new THREE.CylinderGeometry(1.05, 1.05, 0.34, 64);
  const caseMesh = new THREE.Mesh(caseGeo, caseMat);
  caseMesh.name = 'case';
  caseMesh.castShadow = true;
  watch.add(caseMesh);

  // BEZEL
  const bezelMat = new THREE.MeshStandardMaterial({
    color: GOLD, metalness: 0.9, roughness: 0.1
  });
  const bezelGeo = new THREE.TorusGeometry(1.05, 0.12, 16, 64);
  const bezel = new THREE.Mesh(bezelGeo, bezelMat);
  bezel.name = 'bezel';
  bezel.position.y = 0.17;
  bezel.rotation.x = Math.PI / 2;
  watch.add(bezel);

  // BEZEL INNER RING
  const bInnerGeo = new THREE.TorusGeometry(0.97, 0.05, 8, 64);
  const bInner = new THREE.Mesh(bInnerGeo, new THREE.MeshStandardMaterial({ color: DARK_GOLD, metalness: 0.95, roughness: 0.08 }));
  bInner.name = 'bezelInner';
  bInner.position.y = 0.17;
  bInner.rotation.x = Math.PI / 2;
  watch.add(bInner);

  // DIAL FACE
  const dialMat = new THREE.MeshStandardMaterial({ color: 0x080808, metalness: 0.1, roughness: 0.7 });
  const dialGeo = new THREE.CylinderGeometry(0.94, 0.94, 0.04, 64);
  const dial = new THREE.Mesh(dialGeo, dialMat);
  dial.name = 'dial';
  dial.position.y = 0.19;
  watch.add(dial);

  // GOLD DIAL RING
  const dialRingGeo = new THREE.TorusGeometry(0.94, 0.04, 8, 64);
  const dialRing = new THREE.Mesh(dialRingGeo, new THREE.MeshStandardMaterial({ color: GOLD, metalness: 0.95, roughness: 0.1 }));
  dialRing.name = 'dialRing';
  dialRing.position.y = 0.19;
  dialRing.rotation.x = Math.PI / 2;
  watch.add(dialRing);

  // HOUR MARKERS
  for (let i = 0; i < 12; i++) {
    const ang = (i / 12) * Math.PI * 2;
    const markerGeo = i % 3 === 0
      ? new THREE.BoxGeometry(0.055, 0.01, 0.18)
      : new THREE.BoxGeometry(0.04, 0.01, 0.11);
    const marker = new THREE.Mesh(markerGeo, new THREE.MeshStandardMaterial({ color: GOLD, metalness: 0.9, roughness: 0.1, emissive: 0xc8a96e, emissiveIntensity: 0.1 }));
    marker.name = `marker_${i}`;
    marker.position.set(Math.sin(ang) * 0.76, 0.215, Math.cos(ang) * 0.76);
    marker.rotation.y = ang;
    watch.add(marker);
  }

  // HANDS
  function makeHand(w, h, d, color, emissive) {
    const geo = new THREE.BoxGeometry(w, d, h);
    const mat = new THREE.MeshStandardMaterial({ color, metalness: 0.8, roughness: 0.15, emissive, emissiveIntensity: 0.15 });
    return new THREE.Mesh(geo, mat);
  }

  const hourHand = makeHand(0.06, 0.48, 0.022, GOLD, 0xc8a96e);
  hourHand.name = 'hourHand';
  hourHand.position.set(0, 0.228, 0.14);
  watch.add(hourHand);

  const minuteHand = makeHand(0.04, 0.7, 0.022, 0xdddddd, 0xffffff);
  minuteHand.name = 'minuteHand';
  minuteHand.position.set(0, 0.232, 0.22);
  watch.add(minuteHand);

  const secondHand = makeHand(0.018, 0.8, 0.022, 0xff3333, 0xff0000);
  secondHand.name = 'secondHand';
  secondHand.position.set(0, 0.236, 0.24);
  watch.add(secondHand);

  // CENTER DOT
  const centerDot = new THREE.Mesh(
    new THREE.CylinderGeometry(0.055, 0.055, 0.04, 24),
    new THREE.MeshStandardMaterial({ color: GOLD, metalness: 0.95, roughness: 0.1 })
  );
  centerDot.name = 'centerDot';
  centerDot.position.y = 0.24;
  watch.add(centerDot);

  // CROWN
  const crownGroup = new THREE.Group();
  crownGroup.name = 'crown';
  const crownBody = new THREE.Mesh(
    new THREE.CylinderGeometry(0.065, 0.065, 0.22, 16),
    new THREE.MeshStandardMaterial({ color: 0xaaaaaa, metalness: 0.95, roughness: 0.1 })
  );
  crownBody.rotation.z = Math.PI / 2;
  crownGroup.add(crownBody);
  crownGroup.position.set(1.14, 0.04, 0);
  watch.add(crownGroup);

  // LUGS
  const lugMat = new THREE.MeshStandardMaterial({ color: 0xb8b8b8, metalness: 0.9, roughness: 0.15 });
  const lugPositions = [[0.55, 0, 1.08], [-0.55, 0, 1.08], [0.55, 0, -1.08], [-0.55, 0, -1.08]];
  lugPositions.forEach((pos, i) => {
    const lug = new THREE.Mesh(new THREE.BoxGeometry(0.22, 0.28, 0.38), lugMat);
    lug.name = `lug_${i}`;
    lug.position.set(...pos);
    watch.add(lug);
  });

  // STRAP
  const strapMat = new THREE.MeshStandardMaterial({ color: 0x111111, roughness: 0.85, metalness: 0.05 });
  const topStrap = new THREE.Mesh(new THREE.BoxGeometry(0.85, 0.18, 1.5), strapMat);
  topStrap.name = 'strapTop';
  topStrap.position.set(0, -0.05, 1.8);
  watch.add(topStrap);

  const bottomStrap = new THREE.Mesh(new THREE.BoxGeometry(0.85, 0.18, 1.3), strapMat);
  bottomStrap.name = 'strapBottom';
  bottomStrap.position.set(0, -0.05, -1.8);
  watch.add(bottomStrap);

  // GLASS
  const glassMat = new THREE.MeshPhysicalMaterial({
    color: 0xffffff, metalness: 0, roughness: 0,
    transmission: 0.92, opacity: 0.15, transparent: true,
    ior: 1.5, thickness: 0.05, reflectivity: 0.8
  });
  const glass = new THREE.Mesh(new THREE.CylinderGeometry(0.94, 0.94, 0.06, 64), glassMat);
  glass.name = 'glass';
  glass.position.y = 0.23;
  watch.add(glass);

  // CASEBACK EDGE
  const backGeo = new THREE.CylinderGeometry(1.04, 1.04, 0.06, 64);
  const back = new THREE.Mesh(backGeo, new THREE.MeshStandardMaterial({ color: 0xaaaaaa, metalness: 0.9, roughness: 0.2 }));
  back.name = 'caseback';
  back.position.y = -0.19;
  watch.add(back);

  // Controls
  const controls = new OrbitControls(camera, renderer.domElement);
  controls.enableDamping = true;
  controls.dampingFactor = 0.05;
  controls.autoRotate = true;
  controls.autoRotateSpeed = 1.2;
  controls.enablePan = false;
  controls.minDistance = 3;
  controls.maxDistance = 12;

  watch.rotation.x = 0.3;

  function animate() {
    requestAnimationFrame(animate);

    const now = new Date();
    const s = now.getSeconds() + now.getMilliseconds() / 1000;
    const m = now.getMinutes() + s / 60;
    const h = (now.getHours() % 12) + m / 60;

    const sAng = (s / 60) * Math.PI * 2;
    const mAng = (m / 60) * Math.PI * 2;
    const hAng = (h / 12) * Math.PI * 2;

    hourHand.position.set(Math.sin(hAng) * 0.14, 0.228, Math.cos(hAng) * 0.14);
    hourHand.rotation.y = hAng;
    minuteHand.position.set(Math.sin(mAng) * 0.22, 0.232, Math.cos(mAng) * 0.22);
    minuteHand.rotation.y = mAng;
    secondHand.position.set(Math.sin(sAng) * 0.24, 0.236, Math.cos(sAng) * 0.24);
    secondHand.rotation.y = sAng;

    controls.update();
    renderer.render(scene, camera);
  }
  animate();

  window.addEventListener('resize', () => {
    const W2 = window.innerWidth, H2 = window.innerHeight;
    camera.aspect = W2 / H2;
    camera.updateProjectionMatrix();
    renderer.setSize(W2, H2);
  });
}

// ─── MINI WATCH CARDS ────────────────────────────────────────────
function buildMiniWatch(canvasId, dialColor, bezelColor, accentColor) {
  const canvas = document.getElementById(canvasId);
  if (!canvas) return;
  const renderer = new THREE.WebGLRenderer({ canvas, antialias: true, alpha: true });
  const W = canvas.clientWidth, H = canvas.clientHeight;
  renderer.setSize(W, H);
  renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));
  renderer.outputColorSpace = THREE.SRGBColorSpace;
  renderer.toneMapping = THREE.ACESFilmicToneMapping;
  renderer.toneMappingExposure = 1.3;

  const scene = new THREE.Scene();
  const camera = new THREE.PerspectiveCamera(40, W / H, 0.1, 50);
  camera.position.set(0, 3.8, 0.1);
  camera.lookAt(0, 0, 0);

  scene.add(new THREE.AmbientLight(0xffffff, 0.5));
  const d1 = new THREE.DirectionalLight(0xfff0cc, 3);
  d1.position.set(3, 5, 3);
  scene.add(d1);
  const d2 = new THREE.DirectionalLight(0xffffff, 1.2);
  d2.position.set(-3, 4, -2);
  scene.add(d2);

  const g = new THREE.Group();
  g.name = `miniGroup_${canvasId}`;
  scene.add(g);

  // Case
  g.add(Object.assign(new THREE.Mesh(
    new THREE.CylinderGeometry(1, 1, 0.3, 64),
    new THREE.MeshStandardMaterial({ color: 0xb0b0b0, metalness: 0.95, roughness: 0.1 })
  ), { name: `case_${canvasId}` }));

  // Bezel
  const bezelM = new THREE.Mesh(
    new THREE.TorusGeometry(1, 0.11, 16, 64),
    new THREE.MeshStandardMaterial({ color: bezelColor, metalness: 0.9, roughness: 0.1 })
  );
  bezelM.name = `bezel_${canvasId}`;
  bezelM.rotation.x = Math.PI / 2;
  bezelM.position.y = 0.15;
  g.add(bezelM);

  // Dial
  g.add(Object.assign(new THREE.Mesh(
    new THREE.CylinderGeometry(0.88, 0.88, 0.04, 64),
    new THREE.MeshStandardMaterial({ color: dialColor, metalness: 0.3, roughness: 0.6 })
  ), { name: `dial_${canvasId}`, position: new THREE.Vector3(0, 0.17, 0) }));

  // Markers
  for (let i = 0; i < 12; i++) {
    const a = (i / 12) * Math.PI * 2;
    const mk = new THREE.Mesh(
      new THREE.BoxGeometry(0.045, 0.01, 0.1),
      new THREE.MeshStandardMaterial({ color: accentColor, metalness: 0.9, roughness: 0.1 })
    );
    mk.name = `mk_${canvasId}_${i}`;
    mk.position.set(Math.sin(a) * 0.72, 0.2, Math.cos(a) * 0.72);
    mk.rotation.y = a;
    g.add(mk);
  }

  // Hands
  const hH = new THREE.Mesh(new THREE.BoxGeometry(0.05, 0.008, 0.42),
    new THREE.MeshStandardMaterial({ color: accentColor, metalness: 0.9, roughness: 0.1 }));
  hH.name = `hourH_${canvasId}`;
  hH.position.y = 0.21;
  g.add(hH);

  const mH = new THREE.Mesh(new THREE.BoxGeometry(0.032, 0.008, 0.62),
    new THREE.MeshStandardMaterial({ color: 0xffffff, metalness: 0.8, roughness: 0.1 }));
  mH.name = `minH_${canvasId}`;
  mH.position.y = 0.215;
  g.add(mH);

  const sH = new THREE.Mesh(new THREE.BoxGeometry(0.015, 0.008, 0.72),
    new THREE.MeshStandardMaterial({ color: 0xff3333, metalness: 0.8, roughness: 0.1 }));
  sH.name = `secH_${canvasId}`;
  sH.position.y = 0.22;
  g.add(sH);

  // Center
  g.add(Object.assign(new THREE.Mesh(
    new THREE.CylinderGeometry(0.05, 0.05, 0.04, 24),
    new THREE.MeshStandardMaterial({ color: accentColor, metalness: 0.95, roughness: 0.1 })
  ), { name: `center_${canvasId}`, position: new THREE.Vector3(0, 0.22, 0) }));

  let angle = 0;
  function loop() {
    requestAnimationFrame(loop);
    angle += 0.008;
    g.rotation.y = angle;

    const now = new Date();
    const s = now.getSeconds() + now.getMilliseconds() / 1000;
    const m = now.getMinutes() + s / 60;
    const h = (now.getHours() % 12) + m / 60;

    hH.rotation.y = -(h / 12) * Math.PI * 2;
    mH.rotation.y = -(m / 60) * Math.PI * 2;
    sH.rotation.y = -(s / 60) * Math.PI * 2;

    renderer.render(scene, camera);
  }
  loop();
}

// ─── SPECS CANVAS ────────────────────────────────────────────────
function buildSpecsWatch() {
  const canvas = document.getElementById('specs-canvas');
  if (!canvas) return;
  const renderer = new THREE.WebGLRenderer({ canvas, antialias: true, alpha: true });
  const W = canvas.clientWidth || 500;
  const H = canvas.clientHeight || 420;
  renderer.setSize(W, H);
  renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));
  renderer.outputColorSpace = THREE.SRGBColorSpace;
  renderer.toneMapping = THREE.ACESFilmicToneMapping;
  renderer.toneMappingExposure = 1.3;

  const scene = new THREE.Scene();
  const camera = new THREE.PerspectiveCamera(40, W / H, 0.1, 50);
  camera.position.set(2, 2.5, 4);
  camera.lookAt(0, 0, 0);

  scene.add(new THREE.AmbientLight(0xffffff, 0.4));
  const d1 = new THREE.DirectionalLight(0xfff5cc, 3);
  d1.position.set(4, 6, 4);
  scene.add(d1);
  const d2 = new THREE.DirectionalLight(0xffffff, 1);
  d2.position.set(-4, 3, -3);
  scene.add(d2);
  const pt = new THREE.PointLight(0xc8a96e, 2, 15);
  pt.position.set(-2, 3, 2);
  scene.add(pt);

  const watch = new THREE.Group();
  watch.name = 'specsWatch';
  scene.add(watch);

  // Same full watch build
  const silvMat = new THREE.MeshStandardMaterial({ color: 0xb0b0b0, metalness: 0.95, roughness: 0.12 });
  const goldMat = new THREE.MeshStandardMaterial({ color: GOLD, metalness: 0.9, roughness: 0.1 });

  watch.add(Object.assign(new THREE.Mesh(new THREE.CylinderGeometry(1.05, 1.05, 0.32, 64), silvMat), { name: 'specCase' }));

  const specBezel = new THREE.Mesh(new THREE.TorusGeometry(1.05, 0.11, 16, 64), goldMat);
  specBezel.name = 'specBezel';
  specBezel.rotation.x = Math.PI / 2;
  specBezel.position.y = 0.16;
  watch.add(specBezel);

  watch.add(Object.assign(new THREE.Mesh(new THREE.CylinderGeometry(0.92, 0.92, 0.04, 64),
    new THREE.MeshStandardMaterial({ color: 0x05050a, roughness: 0.65, metalness: 0.15 })),
    { name: 'specDial', position: new THREE.Vector3(0, 0.18, 0) }));

  for (let i = 0; i < 12; i++) {
    const a = (i / 12) * Math.PI * 2;
    const mk = new THREE.Mesh(
      new THREE.BoxGeometry(i % 3 === 0 ? 0.055 : 0.038, 0.01, i % 3 === 0 ? 0.17 : 0.1),
      new THREE.MeshStandardMaterial({ color: GOLD, metalness: 0.9, roughness: 0.1 })
    );
    mk.name = `specMk_${i}`;
    mk.position.set(Math.sin(a) * 0.74, 0.21, Math.cos(a) * 0.74);
    mk.rotation.y = a;
    watch.add(mk);
  }

  const hH2 = new THREE.Mesh(new THREE.BoxGeometry(0.06, 0.01, 0.46),
    new THREE.MeshStandardMaterial({ color: GOLD, metalness: 0.9, roughness: 0.1 }));
  hH2.name = 'specHH';
  hH2.position.y = 0.225;
  watch.add(hH2);

  const mH2 = new THREE.Mesh(new THREE.BoxGeometry(0.038, 0.01, 0.68),
    new THREE.MeshStandardMaterial({ color: 0xeeeeee, metalness: 0.8, roughness: 0.1 }));
  mH2.name = 'specMH';
  mH2.position.y = 0.23;
  watch.add(mH2);

  const sH2 = new THREE.Mesh(new THREE.BoxGeometry(0.015, 0.01, 0.78),
    new THREE.MeshStandardMaterial({ color: 0xff2222, metalness: 0.8, roughness: 0.1 }));
  sH2.name = 'specSH';
  sH2.position.y = 0.235;
  watch.add(sH2);

  watch.add(Object.assign(new THREE.Mesh(new THREE.CylinderGeometry(0.055, 0.055, 0.04, 24), goldMat),
    { name: 'specCenter', position: new THREE.Vector3(0, 0.235, 0) }));

  watch.add(Object.assign(new THREE.Mesh(
    new THREE.CylinderGeometry(0.94, 0.94, 0.06, 64),
    new THREE.MeshPhysicalMaterial({ transmission: 0.9, transparent: true, opacity: 0.1, roughness: 0, metalness: 0, ior: 1.5 })
  ), { name: 'specGlass', position: new THREE.Vector3(0, 0.22, 0) }));

  const controls = new OrbitControls(camera, renderer.domElement);
  controls.enableDamping = true;
  controls.dampingFactor = 0.06;
  controls.autoRotate = true;
  controls.autoRotateSpeed = 2;
  controls.enablePan = false;

  watch.rotation.x = 0.4;

  function loop() {
    requestAnimationFrame(loop);
    const now = new Date();
    const s = now.getSeconds() + now.getMilliseconds() / 1000;
    const m = now.getMinutes() + s / 60;
    const h = (now.getHours() % 12) + m / 60;
    hH2.rotation.y = -(h / 12) * Math.PI * 2;
    mH2.rotation.y = -(m / 60) * Math.PI * 2;
    sH2.rotation.y = -(s / 60) * Math.PI * 2;
    controls.update();
    renderer.render(scene, camera);
  }
  loop();
}

// Init all
buildHeroWatch();

// Wait for layout to settle
window.addEventListener('load', () => {
  buildMiniWatch('c1', 0x060606, 0x222222, GOLD);
  buildMiniWatch('c2', 0xfafafa, GOLD, DARK_GOLD);
  buildMiniWatch('c3', 0x080808, 0x1a1a1a, 0xe8c080);
  buildSpecsWatch();
});
</script>
</body>
</html>
