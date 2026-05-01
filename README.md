<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Sahan D Jayasingha – Portfolio</title>
<link href="https://fonts.googleapis.com/css2?family=Cinzel+Decorative:wght@700;900&family=Rajdhani:wght@300;400;500;600;700&family=Orbitron:wght@400;700;900&family=Crimson+Pro:ital,wght@0,300;0,400;1,300&display=swap" rel="stylesheet"/>
<style>
  :root {
    --black: #050505;
    --deep: #0a0a0a;
    --card: #111111;
    --border: #1e1e1e;
    --gold: #c9a84c;
    --gold-light: #e8c96a;
    --gold-dim: #8a6f2e;
    --red: #c0392b;
    --red-bright: #e74c3c;
    --white: #f5f5f0;
    --white-dim: #9a9a90;
    --font-display: 'Cinzel Decorative', serif;
    --font-tech: 'Orbitron', monospace;
    --font-body: 'Rajdhani', sans-serif;
    --font-accent: 'Crimson Pro', serif;
  }

  *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--black);
    color: var(--white);
    font-family: var(--font-body);
    overflow-x: hidden;
    cursor: none;
  }

  /* ── CUSTOM CURSOR ── */
  .cursor { position: fixed; width: 10px; height: 10px; background: var(--gold); border-radius: 50%; pointer-events: none; z-index: 9999; transform: translate(-50%,-50%); transition: transform .1s; }
  .cursor-ring { position: fixed; width: 36px; height: 36px; border: 1px solid var(--gold-dim); border-radius: 50%; pointer-events: none; z-index: 9998; transform: translate(-50%,-50%); transition: all .25s ease; }

  /* ── PRELOADER ── */
  #preloader {
    position: fixed; inset: 0; background: var(--black);
    display: flex; flex-direction: column; align-items: center; justify-content: center;
    z-index: 9000;
    transition: opacity .8s ease, visibility .8s ease;
  }
  #preloader.hidden { opacity: 0; visibility: hidden; }

  .preloader-text {
    font-family: var(--font-display);
    font-size: clamp(2rem, 6vw, 4.5rem);
    letter-spacing: .12em;
    color: var(--white);
    overflow: hidden;
    white-space: nowrap;
    text-align: center;
  }
  /* Mobile: 3 lines */
  @media (max-width: 600px) {
    .preloader-text {
      white-space: normal;
      display: flex; flex-direction: column; align-items: center;
      gap: 4px;
      font-size: clamp(1.5rem, 10vw, 2.5rem);
      line-height: 1.3;
    }
    .preloader-text .word { display: block; white-space: nowrap; }
  }
  .preloader-text .char {
    display: inline-block;
    opacity: 0;
    transform: translateY(60px);
    animation: charIn .05s forwards;
  }
  .preloader-text .char.gold { color: var(--gold); }

  @keyframes charIn {
    to { opacity: 1; transform: translateY(0); }
  }

  .preloader-line {
    width: 0; height: 2px;
    background: linear-gradient(90deg, transparent, var(--gold), var(--red), transparent);
    margin-top: 24px;
    animation: lineExpand 1s ease forwards;
    animation-delay: 2.2s;
  }
  @keyframes lineExpand { to { width: 420px; } }

  /* ── NAV ── */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 800;
    display: flex; align-items: center; justify-content: space-between;
    padding: 20px 6%;
    background: rgba(5,5,5,.92);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid var(--border);
    transform: translateY(-100%);
    animation: navDrop .6s ease forwards;
    animation-delay: 3.2s;
  }
  @keyframes navDrop { to { transform: translateY(0); } }

  .nav-logo {
    font-family: var(--font-display);
    font-size: .9rem;
    letter-spacing: .15em;
    color: var(--white);
  }
  .nav-logo span { color: var(--gold); }

  .nav-links { display: flex; gap: 36px; list-style: none; }
  .nav-links a {
    font-family: var(--font-tech);
    font-size: .65rem;
    letter-spacing: .2em;
    color: var(--white-dim);
    text-decoration: none;
    text-transform: uppercase;
    transition: color .3s;
    position: relative;
  }
  .nav-links a::after {
    content: ''; position: absolute; bottom: -4px; left: 0; width: 0; height: 1px;
    background: var(--gold); transition: width .3s;
  }
  .nav-links a:hover { color: var(--gold); }
  .nav-links a:hover::after { width: 100%; }

  /* ── HERO ── */
  #hero {
    min-height: 100vh;
    display: flex; align-items: center;
    padding: 100px 6% 60px;
    position: relative;
    overflow: hidden;
  }

  .hero-bg {
    position: absolute; inset: 0;
    background: radial-gradient(ellipse 80% 60% at 70% 50%, rgba(201,168,76,.07) 0%, transparent 60%),
                radial-gradient(ellipse 50% 40% at 20% 80%, rgba(192,57,43,.05) 0%, transparent 50%);
  }
  .hero-grid {
    position: absolute; inset: 0;
    background-image:
      linear-gradient(rgba(201,168,76,.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(201,168,76,.04) 1px, transparent 1px);
    background-size: 60px 60px;
    mask-image: radial-gradient(ellipse 80% 80% at 50% 50%, black 40%, transparent 100%);
  }

  .hero-inner {
    display: grid; grid-template-columns: 1fr auto;
    gap: 60px; align-items: center;
    width: 100%; max-width: 1200px; margin: 0 auto;
    position: relative; z-index: 1;
    opacity: 0; transform: translateY(30px);
    animation: fadeUp .8s ease forwards;
    animation-delay: 3.4s;
  }
  @keyframes fadeUp { to { opacity: 1; transform: translateY(0); } }

  .hero-tag {
    font-family: var(--font-tech);
    font-size: .6rem; letter-spacing: .35em;
    color: var(--red); text-transform: uppercase;
    margin-bottom: 20px;
    display: flex; align-items: center; gap: 12px;
  }
  .hero-tag::before {
    content: ''; width: 32px; height: 1px; background: var(--red);
  }

  h1.hero-name {
    font-family: var(--font-display);
    font-size: clamp(2.4rem, 5.5vw, 5rem);
    font-weight: 900;
    line-height: 1.05;
    letter-spacing: .04em;
    margin-bottom: 24px;
  }
  h1.hero-name .gold { color: var(--gold); text-shadow: 0 0 40px rgba(201,168,76,.4); }

  .hero-headline {
    font-family: var(--font-accent);
    font-size: clamp(.95rem, 1.8vw, 1.25rem);
    font-weight: 300; font-style: italic;
    color: var(--white-dim);
    margin-bottom: 40px;
    max-width: 540px;
    line-height: 1.7;
  }
  .hero-headline strong { color: var(--gold-light); font-style: normal; font-weight: 400; }

  .hero-stats {
    display: flex; gap: 40px; margin-bottom: 48px;
  }
  .stat-item { text-align: left; }
  .stat-num {
    font-family: var(--font-tech);
    font-size: 2.2rem; font-weight: 700;
    color: var(--gold);
    line-height: 1;
  }
  .stat-label {
    font-size: .7rem; letter-spacing: .2em;
    color: var(--white-dim); text-transform: uppercase;
    margin-top: 4px;
  }

  .hero-btns { display: flex; gap: 16px; flex-wrap: wrap; }
  .btn-primary {
    font-family: var(--font-tech);
    font-size: .65rem; letter-spacing: .25em;
    padding: 14px 36px;
    background: var(--gold);
    color: var(--black);
    border: none; cursor: none;
    text-decoration: none; text-transform: uppercase;
    font-weight: 700;
    clip-path: polygon(8px 0%, 100% 0%, calc(100% - 8px) 100%, 0% 100%);
    transition: background .3s, transform .2s;
  }
  .btn-primary:hover { background: var(--gold-light); transform: translateY(-2px); }

  .btn-ghost {
    font-family: var(--font-tech);
    font-size: .65rem; letter-spacing: .25em;
    padding: 13px 36px;
    background: transparent;
    color: var(--white);
    border: 1px solid var(--border);
    cursor: none;
    text-decoration: none; text-transform: uppercase;
    clip-path: polygon(8px 0%, 100% 0%, calc(100% - 8px) 100%, 0% 100%);
    transition: border-color .3s, color .3s, transform .2s;
  }
  .btn-ghost:hover { border-color: var(--gold); color: var(--gold); transform: translateY(-2px); }

  /* HERO PHOTO */
  .hero-photo-wrap {
    position: relative; width: 320px; height: 380px; flex-shrink: 0;
  }
  .hero-photo-frame {
    position: absolute; inset: 0;
    border: 1px solid var(--gold-dim);
    clip-path: polygon(20px 0%, 100% 0%, 100% calc(100% - 20px), calc(100% - 20px) 100%, 0% 100%, 0% 20px);
  }
  .hero-photo-frame::before {
    content: '';
    position: absolute; inset: 6px;
    border: 1px solid rgba(201,168,76,.2);
    clip-path: polygon(14px 0%, 100% 0%, 100% calc(100% - 14px), calc(100% - 14px) 100%, 0% 100%, 0% 14px);
  }
  .hero-photo-glow {
    position: absolute; inset: -20px;
    background: radial-gradient(ellipse at center, rgba(201,168,76,.12) 0%, transparent 70%);
    pointer-events: none;
  }
  .hero-photo {
    width: 100%; height: 100%;
    object-fit: cover;
    clip-path: polygon(20px 0%, 100% 0%, 100% calc(100% - 20px), calc(100% - 20px) 100%, 0% 100%, 0% 20px);
    filter: grayscale(20%) contrast(1.05);
    display: block;
  }
  .hero-photo-corner {
    position: absolute;
    width: 20px; height: 20px;
    border-color: var(--gold);
    border-style: solid;
  }
  .hpc-tl { top: -1px; left: -1px; border-width: 2px 0 0 2px; }
  .hpc-tr { top: -1px; right: -1px; border-width: 2px 2px 0 0; }
  .hpc-bl { bottom: -1px; left: -1px; border-width: 0 0 2px 2px; }
  .hpc-br { bottom: -1px; right: -1px; border-width: 0 2px 2px 0; }

  /* ── SECTION BASE ── */
  section { padding: 100px 6%; }
  .section-inner { max-width: 1200px; margin: 0 auto; }

  .section-label {
    font-family: var(--font-tech);
    font-size: .6rem; letter-spacing: .4em; color: var(--red);
    text-transform: uppercase; margin-bottom: 12px;
    display: flex; align-items: center; gap: 12px;
  }
  .section-label::before { content: ''; width: 24px; height: 1px; background: var(--red); }

  h2.section-title {
    font-family: var(--font-display);
    font-size: clamp(1.8rem, 3.5vw, 3rem);
    font-weight: 700; letter-spacing: .06em;
    margin-bottom: 60px;
    color: var(--white);
  }
  h2.section-title span { color: var(--gold); }

  /* ── ABOUT ── */
  #about { background: var(--deep); position: relative; overflow: hidden; }
  #about::before {
    content: 'ABOUT';
    position: absolute; right: -2%; top: 50%;
    transform: translateY(-50%);
    font-family: var(--font-display); font-size: 12rem; font-weight: 900;
    color: rgba(201,168,76,.03); pointer-events: none; letter-spacing: .1em;
    white-space: nowrap;
  }

  .about-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 80px; align-items: start; }

  .about-text p {
    font-size: 1.05rem; line-height: 1.85;
    color: rgba(245,245,240,.75);
    margin-bottom: 20px;
    font-weight: 300;
  }
  .about-text p strong { color: var(--gold-light); font-weight: 500; }

  .about-tags { display: flex; flex-wrap: wrap; gap: 10px; margin-top: 32px; }
  .tag {
    font-family: var(--font-tech); font-size: .58rem;
    letter-spacing: .2em; text-transform: uppercase;
    padding: 8px 18px;
    border: 1px solid var(--border);
    color: var(--white-dim);
    transition: border-color .3s, color .3s;
  }
  .tag:hover { border-color: var(--gold); color: var(--gold); }

  /* Education Timeline */
  .edu-timeline { position: relative; padding-left: 24px; }
  .edu-timeline::before {
    content: ''; position: absolute; left: 0; top: 8px; bottom: 8px;
    width: 1px; background: linear-gradient(to bottom, var(--gold), var(--red), transparent);
  }
  .edu-item {
    position: relative; margin-bottom: 36px; padding-left: 28px;
    opacity: 0; transform: translateX(-20px);
    transition: opacity .6s ease, transform .6s ease;
  }
  .edu-item.visible { opacity: 1; transform: translateX(0); }
  .edu-item::before {
    content: ''; position: absolute; left: -28px; top: 8px;
    width: 8px; height: 8px; border-radius: 50%;
    background: var(--gold); border: 2px solid var(--black);
    box-shadow: 0 0 10px var(--gold);
  }
  .edu-degree {
    font-family: var(--font-body); font-weight: 600; font-size: 1rem;
    color: var(--white); margin-bottom: 4px;
  }
  .edu-school {
    font-size: .85rem; color: var(--gold-dim);
    font-style: italic; margin-bottom: 4px;
  }
  .edu-year {
    font-family: var(--font-tech); font-size: .6rem;
    letter-spacing: .2em; color: var(--white-dim);
  }

  /* ── PROJECTS ── */
  #projects { background: #000000; }

  /* ── PROJECTS SPLIT LAYOUT ── */
  .projects-split {
    display: grid;
    grid-template-columns: 380px 1fr;
    gap: 60px;
    align-items: start;
  }

  /* LEFT: sticky image column */
  .projects-image-col { position: sticky; top: 100px; }

  .projects-img-frame {
    position: relative;
    overflow: hidden;
  }
  .projects-main-img {
    width: 100%; display: block;
    object-fit: cover; object-position: center top;
    filter: grayscale(15%) brightness(.9) contrast(1.08);
    aspect-ratio: 3/4;
  }
  .projects-img-label {
    position: absolute; bottom: 0; left: 0; right: 0;
    padding: 20px 20px 16px;
    background: linear-gradient(to top, rgba(5,5,5,.95), transparent);
  }
  .pil-tag {
    font-family: var(--font-tech); font-size: .58rem;
    letter-spacing: .3em; color: var(--gold);
    text-transform: uppercase;
    border: 1px solid var(--gold-dim);
    padding: 4px 12px;
  }

  /* RIGHT: projects list column */
  .projects-list-col {
    display: flex; flex-direction: column;
    border-top: 1px solid var(--border);
  }

  .proj-item {
    display: grid; grid-template-columns: 56px 1fr;
    gap: 0;
    padding: 36px 0;
    border-bottom: 1px solid var(--border);
    opacity: 0; transform: translateX(24px);
    transition: opacity .6s ease, transform .6s ease, background .3s;
    cursor: default;
  }
  .proj-item.visible { opacity: 1; transform: translateX(0); }
  .proj-item:hover { background: rgba(201,168,76,.03); }

  .proj-item-left {
    padding-top: 4px;
  }
  .proj-num {
    font-family: var(--font-tech); font-size: .75rem;
    font-weight: 700; color: var(--border);
    letter-spacing: .1em;
    transition: color .3s;
  }
  .proj-item:hover .proj-num { color: var(--gold); }

  .proj-item-right { padding-left: 8px; }

  .proj-year-tag {
    font-family: var(--font-tech); font-size: .56rem;
    letter-spacing: .3em; color: var(--red);
    margin-bottom: 10px; text-transform: uppercase;
  }
  .proj-title {
    font-family: var(--font-body); font-weight: 700;
    font-size: 1.15rem; color: var(--white);
    letter-spacing: .03em; margin-bottom: 12px;
    line-height: 1.3;
    transition: color .3s;
  }
  .proj-item:hover .proj-title { color: var(--gold-light); }
  .proj-desc {
    font-size: .88rem; line-height: 1.75;
    color: var(--white-dim); font-weight: 300;
    margin-bottom: 16px;
  }
  .proj-tags {
    display: flex; gap: 8px; flex-wrap: wrap;
  }
  .proj-tags span {
    font-family: var(--font-tech); font-size: .52rem;
    letter-spacing: .2em; text-transform: uppercase;
    padding: 4px 12px;
    border: 1px solid var(--border);
    color: var(--white-dim);
    transition: border-color .3s, color .3s;
  }
  .proj-item:hover .proj-tags span { border-color: var(--gold-dim); color: var(--gold-dim); }

  @media (max-width: 900px) {
    .hero-inner { grid-template-columns: 1fr; text-align: center; }
    .hero-photo-wrap { display: block; margin: 40px auto 0; width: 280px; height: 330px; }
    .hero-tag { justify-content: center; }
    .hero-tag::before { display: none; }
    .hero-headline { margin-left: auto; margin-right: auto; }
    .hero-stats { justify-content: center; }
    .hero-btns { justify-content: center; }
    .about-grid { grid-template-columns: 1fr; gap: 50px; }
    .skills-categories { grid-template-columns: 1fr; }
    nav .nav-links { display: none; }
    .projects-split { grid-template-columns: 1fr; gap: 40px; }
    .projects-image-col { position: static; }
    .projects-main-img { aspect-ratio: 4/3; }
  }

  /* ── SKILLS ── */
  #skills { background: var(--deep); }

  .skills-categories { display: grid; grid-template-columns: repeat(3, 1fr); gap: 40px; }

  .skill-cat-title {
    font-family: var(--font-tech); font-size: .65rem;
    letter-spacing: .3em; color: var(--red);
    text-transform: uppercase; margin-bottom: 28px;
    padding-bottom: 12px;
    border-bottom: 1px solid var(--border);
  }

  .skill-item { margin-bottom: 22px; }
  .skill-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 8px; }
  .skill-name { font-size: .85rem; color: var(--white); font-weight: 500; letter-spacing: .04em; }
  .skill-pct { font-family: var(--font-tech); font-size: .65rem; color: var(--gold); }
  .skill-bar { height: 3px; background: var(--border); position: relative; overflow: hidden; }
  .skill-fill {
    height: 100%; width: 0;
    background: linear-gradient(90deg, var(--gold-dim), var(--gold));
    transition: width 1.2s cubic-bezier(.4,0,.2,1);
    position: relative;
  }
  .skill-fill::after {
    content: ''; position: absolute; right: 0; top: -2px;
    width: 6px; height: 6px; border-radius: 50%;
    background: var(--gold-light);
    box-shadow: 0 0 8px var(--gold);
  }

  /* ── TOOLS ── */
  #tools { background: var(--black); }

  .tools-group { margin-bottom: 48px; }
  .tools-group-label {
    font-family: var(--font-tech); font-size: .58rem;
    letter-spacing: .35em; color: var(--white-dim);
    text-transform: uppercase; margin-bottom: 18px;
  }
  .tools-pills { display: flex; flex-wrap: wrap; gap: 10px; }
  .tool-pill {
    font-family: var(--font-body); font-size: .82rem; font-weight: 500;
    padding: 10px 22px;
    background: var(--card);
    border: 1px solid var(--border);
    color: var(--white-dim);
    letter-spacing: .05em;
    position: relative; overflow: hidden;
    transition: color .3s, border-color .3s;
    cursor: none;
  }
  .tool-pill::before {
    content: ''; position: absolute; left: -100%; top: 0;
    width: 100%; height: 100%;
    background: linear-gradient(90deg, transparent, rgba(201,168,76,.08), transparent);
    transition: left .5s ease;
  }
  .tool-pill:hover { color: var(--gold); border-color: var(--gold-dim); }
  .tool-pill:hover::before { left: 100%; }

  /* ── CONNECT ── */
  #connect { background: var(--deep); text-align: center; }

  .connect-tagline {
    font-family: var(--font-accent); font-size: 1.1rem;
    font-style: italic; color: var(--white-dim); margin-bottom: 56px;
  }

  .social-links { display: flex; justify-content: center; gap: 24px; flex-wrap: wrap; }
  .social-link {
    display: flex; align-items: center; gap: 14px;
    padding: 18px 32px;
    background: var(--card); border: 1px solid var(--border);
    color: var(--white); text-decoration: none;
    font-family: var(--font-body); font-weight: 500; font-size: .9rem;
    letter-spacing: .06em;
    transition: border-color .3s, color .3s, transform .3s;
    position: relative; overflow: hidden;
    clip-path: polygon(10px 0%, 100% 0%, calc(100% - 10px) 100%, 0% 100%);
  }
  .social-link::before {
    content: ''; position: absolute; inset: 0;
    background: linear-gradient(135deg, rgba(201,168,76,.07), transparent);
    opacity: 0; transition: opacity .3s;
  }
  .social-link:hover { border-color: var(--gold); color: var(--gold); transform: translateY(-4px); }
  .social-link:hover::before { opacity: 1; }
  .social-icon { font-size: 1.2rem; }

  /* ── FOOTER ── */
  footer {
    padding: 28px 6%;
    background: var(--black);
    border-top: 1px solid var(--border);
    display: flex; justify-content: space-between; align-items: center;
  }
  .footer-name {
    font-family: var(--font-display); font-size: .75rem;
    letter-spacing: .15em; color: var(--white-dim);
  }
  .footer-name span { color: var(--gold); }
  .footer-copy { font-size: .75rem; color: rgba(245,245,240,.3); letter-spacing: .1em; }

  /* ── SCROLL REVEAL ── */
  .reveal {
    opacity: 0; transform: translateY(30px);
    transition: opacity .7s ease, transform .7s ease;
  }
  .reveal.visible { opacity: 1; transform: translateY(0); }

  /* ── SCROLLBAR ── */
  ::-webkit-scrollbar { width: 4px; }
  ::-webkit-scrollbar-track { background: var(--black); }
  ::-webkit-scrollbar-thumb { background: var(--gold-dim); }

</style>
</head>
<body>

<!-- CURSOR -->
<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- PRELOADER -->
<div id="preloader">
  <div class="preloader-text" id="preloaderText"></div>
  <div class="preloader-line"></div>
</div>

<!-- NAV -->
<nav>
  <div class="nav-logo">Sahan <span>D</span> Jayasingha</div>
  <ul class="nav-links">
    <li><a href="#home">Home</a></li>
    <li><a href="#about">About</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#tools">Tools</a></li>
    <li><a href="#connect">Connect</a></li>
  </ul>
</nav>

<!-- HERO (HOME) -->
<section id="home">
  <div class="hero-bg"></div>
  <div class="hero-grid"></div>
  <div class="hero-inner">
    <div class="hero-content">
      <div class="hero-tag">Portfolio — AI Engineering</div>
      <h1 class="hero-name">
        Sahan <span class="gold">D</span><br>Jayasingha
      </h1>
      <p class="hero-headline">
        <strong>AI Engineering Undergraduate</strong> · Founder of ESD Pvt Ltd<br>
        Full-Stack Developer &amp; Graphic Designer
      </p>
      <div class="hero-stats">
        <div class="stat-item">
          <div class="stat-num">3+</div>
          <div class="stat-label">Years Exp.</div>
        </div>
        <div class="stat-item">
          <div class="stat-num">4+</div>
          <div class="stat-label">Live Projects</div>
        </div>
        <div class="stat-item">
          <div class="stat-num">AI</div>
          <div class="stat-label">Specialization</div>
        </div>
      </div>
      <div class="hero-btns">
        <a href="#projects" class="btn-primary">View Projects</a>
        <a href="#connect" class="btn-ghost">Get In Touch</a>
      </div>
    </div>
    <div class="hero-photo-wrap">
      <div class="hero-photo-glow"></div>
      <div class="hero-photo-frame"></div>
      <img src="img1.jpg" alt="Sahan D Jayasingha" class="hero-photo" onerror="this.style.display='none'"/>
      <div class="hero-photo-corner hpc-tl"></div>
      <div class="hero-photo-corner hpc-tr"></div>
      <div class="hero-photo-corner hpc-bl"></div>
      <div class="hero-photo-corner hpc-br"></div>
    </div>
  </div>
</section>

<!-- ABOUT -->
<section id="about">
  <div class="section-inner">
    <div class="section-label">01 — About Me</div>
    <h2 class="section-title">Who I <span>Am</span></h2>
    <div class="about-grid">
      <div class="about-text reveal">
        <p>I am a <strong>21-year-old AI Engineering undergraduate</strong> at NSBM Green University (affiliated with the University of Plymouth), based in Homagama, Sri Lanka. I have a strong passion for software innovation and full-stack development.</p>
        <p>As the founder of <strong>E-Student Develop (ESD)</strong>, I focus on building digital platforms and mobile applications that empower the next generation of students. My technical toolkit includes HTML, CSS, Java, C, Python, and Dart.</p>
        <p>With a professional background as a <strong>Graphic Designer (Design Master)</strong>, I bridge the gap between technical functionality and creative design to build user-centric applications.</p>
        <div class="about-tags">
          <span class="tag">AI Engineering</span>
          <span class="tag">Full-Stack Dev</span>
          <span class="tag">Graphic Design</span>
          <span class="tag">ESD Founder</span>
          <span class="tag">Flutter</span>
          <span class="tag">React</span>
        </div>
      </div>
      <div class="edu-timeline">
        <div class="edu-item">
          <div class="edu-degree">BSc (Hons) in Artificial Intelligence</div>
          <div class="edu-school">NSBM Green University / University of Plymouth</div>
          <div class="edu-year">2024 — Present</div>
        </div>
        <div class="edu-item">
          <div class="edu-degree">Diploma in English Language</div>
          <div class="edu-school">Institute of Vocational &amp; Technological Guidance</div>
          <div class="edu-year">2024 — 2025</div>
        </div>
        <div class="edu-item">
          <div class="edu-degree">Foundation in Information Technology</div>
          <div class="edu-school">Esoft Metro Campus</div>
          <div class="edu-year">2022</div>
        </div>
        <div class="edu-item">
          <div class="edu-degree">Computer Studies Conducted</div>
          <div class="edu-school">OSIS Computer Institute</div>
          <div class="edu-year">2019</div>
        </div>
        <div class="edu-item">
          <div class="edu-degree">Certificate in Computer Application</div>
          <div class="edu-school">Kosmo Tec International</div>
          <div class="edu-year">2016 — 2017</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects">
  <div class="section-inner">
    <div class="section-label">02 — Work</div>
    <h2 class="section-title">Key <span>Projects</span></h2>
    <div class="projects-split">
      <div class="projects-image-col">
        <div class="projects-img-frame">
          <img src="img2.jpg" alt="Featured Work" class="projects-main-img" onerror="this.style.background='#000'"/>
        </div>
      </div>
      <div class="projects-list-col">
        <div class="proj-item reveal">
          <div class="proj-item-left"><div class="proj-num">01</div></div>
          <div class="proj-item-right">
            <div class="proj-year-tag">2026</div>
            <div class="proj-title">ESD Note Mobile Application</div>
            <p class="proj-desc">A mobile application designed for student productivity and educational resource management.</p>
            <div class="proj-tags"><span>Flutter</span><span>Dart</span><span>Mobile</span></div>
          </div>
        </div>
        <div class="proj-item reveal">
          <div class="proj-item-left"><div class="proj-num">02</div></div>
          <div class="proj-item-right">
            <div class="proj-year-tag">2024</div>
            <div class="proj-title">ESD Official Website</div>
            <p class="proj-desc">The central digital hub for E-Student Develop, showcasing educational services and tools.</p>
            <div class="proj-tags"><span>React</span><span>Web</span></div>
          </div>
        </div>
        <div class="proj-item reveal">
          <div class="proj-item-left"><div class="proj-num">03</div></div>
          <div class="proj-item-right">
            <div class="proj-year-tag">2025</div>
            <div class="proj-title">ESD Note Web Platform</div>
            <p class="proj-desc">A web-based extension of the ESD Note ecosystem for cross-platform accessibility.</p>
            <div class="proj-tags"><span>React</span><span>Web</span></div>
          </div>
        </div>
        <div class="proj-item reveal">
          <div class="proj-item-left"><div class="proj-num">04</div></div>
          <div class="proj-item-right">
            <div class="proj-year-tag">2024</div>
            <div class="proj-title">Custom Flutter Camera App (pro_cam)</div>
            <p class="proj-desc">A functional camera application built in Flutter with filters and gallery integration.</p>
            <div class="proj-tags"><span>Flutter</span><span>Camera API</span></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- SKILLS -->
<section id="skills">
  <div class="section-inner">
    <div class="section-label">03 — Expertise</div>
    <h2 class="section-title">Technical <span>Skills</span></h2>
    <div class="skills-categories reveal">
      <div class="skill-cat">
        <div class="skill-cat-title">Development</div>
        <div class="skill-item"><div class="skill-header"><span class="skill-name">React</span><span class="skill-pct">100%</span></div><div class="skill-bar"><div class="skill-fill" data-w="100"></div></div></div>
        <div class="skill-item"><div class="skill-header"><span class="skill-name">HTML / CSS</span><span class="skill-pct">90%</span></div><div class="skill-bar"><div class="skill-fill" data-w="90"></div></div></div>
        <div class="skill-item"><div class="skill-header"><span class="skill-name">JavaScript</span><span class="skill-pct">85%</span></div><div class="skill-bar"><div class="skill-fill" data-w="85"></div></div></div>
      </div>
      <div class="skill-cat">
        <div class="skill-cat-title">Marketing &amp; AI</div>
        <div class="skill-item"><div class="skill-header"><span class="skill-name">Email Marketing</span><span class="skill-pct">100%</span></div><div class="skill-bar"><div class="skill-fill" data-w="100"></div></div></div>
        <div class="skill-item"><div class="skill-header"><span class="skill-name">ChatGPT &amp; AI Tools</span><span class="skill-pct">95%</span></div><div class="skill-bar"><div class="skill-fill" data-w="95"></div></div></div>
      </div>
      <div class="skill-cat">
        <div class="skill-cat-title">Design</div>
        <div class="skill-item"><div class="skill-header"><span class="skill-name">Canva &amp; Canva AI</span><span class="skill-pct">95%</span></div><div class="skill-bar"><div class="skill-fill" data-w="95"></div></div></div>
        <div class="skill-item"><div class="skill-header"><span class="skill-name">Brand Design</span><span class="skill-pct">85%</span></div><div class="skill-bar"><div class="skill-fill" data-w="85"></div></div></div>
      </div>
    </div>
  </div>
</section>

<!-- CONNECT -->
<section id="connect">
  <div class="section-inner">
    <div class="section-label" style="justify-content:center;">04 — Contact</div>
    <h2 class="section-title" style="text-align:center;">Connect With <span>Me</span></h2>
    <div class="social-links reveal">
      <a href="https://github.com/sahandjayasingha" target="_blank" class="social-link">GitHub</a>
      <a href="https://www.linkedin.com/in/sahan-darshana-226bb4333/" target="_blank" class="social-link">LinkedIn</a>
    </div>
  </div>
</section>

<footer>
  <div class="footer-name">Sahan <span>D</span> Jayasingha</div>
  <div class="footer-copy">© 2026 — All Rights Reserved</div>
</footer>

<script>
// ── CURSOR
const cursor = document.getElementById('cursor');
const ring = document.getElementById('cursorRing');
let mx=0,my=0,rx=0,ry=0;
document.addEventListener('mousemove',e=>{
  mx=e.clientX; my=e.clientY;
  cursor.style.left=mx+'px'; cursor.style.top=my+'px';
});
(function animRing(){
  rx+=(mx-rx)*.12; ry+=(my-ry)*.12;
  ring.style.left=rx+'px'; ring.style.top=ry+'px';
  requestAnimationFrame(animRing);
})();
document.querySelectorAll('a,button,.tool-pill,.tag').forEach(el=>{
  el.addEventListener('mouseenter',()=>{ ring.style.transform='translate(-50%,-50%) scale(2)'; ring.style.borderColor='var(--gold)'; });
  el.addEventListener('mouseleave',()=>{ ring.style.transform='translate(-50%,-50%) scale(1)'; ring.style.borderColor='var(--gold-dim)'; });
});

// ── PRELOADER TYPE ANIMATION
const isMobile = window.innerWidth <= 600;
const container = document.getElementById('preloaderText');

if(isMobile){
  const lines = [
    { text: 'Sahan', gold: false },
    { text: 'D',     gold: true  },
    { text: 'Jayasingha', gold: false }
  ];
  let totalDelay = 0;
  lines.forEach(line => {
    const wordSpan = document.createElement('span');
    wordSpan.className = 'word';
    for(let i = 0; i < line.text.length; i++){
      const s = document.createElement('span');
      s.className = 'char' + (line.gold ? ' gold' : '');
      s.textContent = line.text[i];
      s.style.animationDelay = totalDelay + 'ms';
      wordSpan.appendChild(s);
      totalDelay += 80;
    }
    container.appendChild(wordSpan);
    totalDelay += 140;
  });
} else {
  const nameText = "Sahan D Jayasingha";
  let charDelay = 0;
  for(let i = 0; i < nameText.length; i++){
    const s = document.createElement('span');
    s.className = 'char' + (nameText[i]==='D' && nameText[i-1]===' ' && nameText[i+1]===' ' ? ' gold' : '');
    s.textContent = nameText[i]===' ' ? '\u00A0' : nameText[i];
    s.style.animationDelay = charDelay + 'ms';
    container.appendChild(s);
    charDelay += nameText[i]===' ' ? 60 : 80;
  }
}
setTimeout(()=>{
  document.getElementById('preloader').classList.add('hidden');
}, 3200);

// ── SCROLL REVEAL
const revealEls = document.querySelectorAll('.reveal, .edu-item, .proj-item');
const io = new IntersectionObserver((entries)=>{
  entries.forEach((e,i)=>{
    if(e.isIntersecting){
      setTimeout(()=>e.target.classList.add('visible'), i*80);
    }
  });
},{threshold:.15});
revealEls.forEach(el=>io.observe(el));

// ── SKILL BARS
const bars = document.querySelectorAll('.skill-fill');
const barObs = new IntersectionObserver((entries)=>{
  entries.forEach(e=>{
    if(e.isIntersecting){
      e.target.style.width = e.target.dataset.w + '%';
      barObs.unobserve(e.target);
    }
  });
},{threshold:.3});
bars.forEach(b=>barObs.observe(b));

// ── ACTIVE NAV HIGHLIGHT
const sections = document.querySelectorAll('section[id]');
const navLinks = document.querySelectorAll('.nav-links a');
window.addEventListener('scroll',()=>{
  let current='';
  sections.forEach(s=>{
    if(window.scrollY>=s.offsetTop-160) current=s.id;
  });
  navLinks.forEach(a=>{
    a.style.color = a.getAttribute('href')==='#'+current ? 'var(--gold)' : '';
  });
});
</script>
</body>
</html>
