<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Sahan D Jayasingha | Professional Portfolio</title>
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
    /* Cursor is now default */
  }

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
  }
  .preloader-text .char {
    display: inline-block;
    opacity: 0;
    transform: translateY(60px);
    animation: charIn .05s forwards;
  }
  .preloader-text .char.gold { color: var(--gold); }

  @keyframes charIn { to { opacity: 1; transform: translateY(0); } }

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

  .nav-logo { font-family: var(--font-display); font-size: .9rem; letter-spacing: .15em; color: var(--white); }
  .nav-logo span { color: var(--gold); }

  .nav-links { display: flex; gap: 36px; list-style: none; }
  .nav-links a {
    font-family: var(--font-tech); font-size: .65rem; letter-spacing: .2em; color: var(--white-dim);
    text-decoration: none; text-transform: uppercase; transition: color .3s; position: relative;
  }
  .nav-links a:hover { color: var(--gold); }

  /* ── HOME / HERO ── */
  #home {
    min-height: 100vh;
    display: flex; align-items: center;
    padding: 100px 6% 60px;
    position: relative;
    overflow: hidden;
  }

  .hero-bg {
    position: absolute; inset: 0;
    background: radial-gradient(ellipse 80% 60% at 70% 50%, rgba(201,168,76,.07) 0%, transparent 60%);
  }

  .hero-inner {
    display: grid; grid-template-columns: 1fr auto;
    gap: 60px; align-items: center;
    width: 100%; max-width: 1200px; margin: 0 auto;
    position: relative; z-index: 1;
    animation: fadeUp .8s ease forwards; animation-delay: 3.4s; opacity: 0;
  }
  @keyframes fadeUp { to { opacity: 1; transform: translateY(0); } }

  .hero-name { font-family: var(--font-display); font-size: clamp(2.4rem, 5.5vw, 5rem); font-weight: 900; line-height: 1.05; margin-bottom: 24px; }
  .hero-name .gold { color: var(--gold); }

  .hero-headline { font-family: var(--font-accent); font-size: 1.1rem; color: var(--white-dim); margin-bottom: 40px; max-width: 540px; }

  /* HERO PHOTO */
  .hero-photo-wrap { position: relative; width: 320px; height: 400px; }
  .hero-photo {
    width: 100%; height: 100%; object-fit: cover;
    clip-path: polygon(20px 0%, 100% 0%, 100% calc(100% - 20px), calc(100% - 20px) 100%, 0% 100%, 0% 20px);
    border: 1px solid var(--gold-dim);
  }

  /* ── PROJECTS (Featured Split) ── */
  #projects { background: var(--black); padding: 100px 6%; }
  .projects-featured-row {
    display: grid; grid-template-columns: 1fr 1fr;
    gap: 80px; align-items: center; margin-bottom: 100px;
  }
  .featured-image-container img {
    width: 100%; height: auto;
    /* No border or shadow as requested to blend with black bg */
    display: block;
    filter: brightness(0.9) contrast(1.1);
  }

  .featured-details { padding-right: 20px; }
  .section-label { font-family: var(--font-tech); font-size: .6rem; color: var(--red); margin-bottom: 12px; display: flex; align-items: center; gap: 10px; text-transform: uppercase; }
  .section-label::before { content: ''; width: 20px; height: 1px; background: var(--red); }
  
  .project-title-large { font-family: var(--font-display); font-size: 2.5rem; margin-bottom: 20px; color: var(--gold); }
  .project-desc-large { font-size: 1.05rem; line-height: 1.8; color: var(--white-dim); margin-bottom: 30px; }

  /* ── SKILLS & OTHERS ── */
  section { padding: 100px 6%; }
  .section-title { font-family: var(--font-display); font-size: 2.5rem; margin-bottom: 50px; }
  .section-title span { color: var(--gold); }

  .skills-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 30px; }
  .skill-card { background: var(--card); padding: 30px; border: 1px solid var(--border); }
  .skill-name { font-family: var(--font-tech); font-size: .8rem; color: var(--white); margin-bottom: 15px; display: block; }
  
  .btn-primary {
    display: inline-block; font-family: var(--font-tech); padding: 15px 35px;
    background: var(--gold); color: var(--black); text-decoration: none; font-weight: 700;
    clip-path: polygon(10px 0%, 100% 0%, calc(100% - 10px) 100%, 0% 100%);
  }

  /* ── RESPONSIVE ── */
  @media (max-width: 900px) {
    .hero-inner, .projects-featured-row { grid-template-columns: 1fr; text-align: center; }
    .hero-photo-wrap { margin: 0 auto; }
    .section-label { justify-content: center; }
    .featured-image-container { order: 1; }
    .featured-details { order: 2; }
  }
</style>
</head>
<body>

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
    <li><a href="#connect">Connect</a></li>
  </ul>
</nav>

<!-- HOME SECTION -->
<section id="home">
  <div class="hero-bg"></div>
  <div class="hero-inner">
    <div class="hero-content">
      <div class="section-label">AI Engineering Portfolio</div>
      <h1 class="hero-name">Sahan <span class="gold">D</span><br>Jayasingha</h1>
      <p class="hero-headline">
        <strong>AI Engineering Undergraduate</strong> · Founder of ESD Pvt Ltd<br>
        Full-Stack Developer &amp; Graphic Designer
      </p>
      <div class="hero-btns">
        <a href="#projects" class="btn-primary">Explore Work</a>
      </div>
    </div>
    <div class="hero-photo-wrap">
      <!-- Image 1 for Home Section -->
      <img src="img1.jpg" alt="Sahan D Jayasingha" class="hero-photo" onerror="this.src='https://via.placeholder.com/320x400/111/c9a84c?text=Sahan+D+Jayasingha'">
    </div>
  </div>
</section>

<!-- PROJECTS SECTION -->
<section id="projects">
  <div class="section-inner">
    <div class="section-label">01 — Featured Project</div>
    
    <!-- Image 2 on left, details on right -->
    <div class="projects-featured-row reveal">
      <div class="featured-image-container">
        <img src="img2.jpg" alt="Key Project Visual" onerror="this.src='https://via.placeholder.com/600x400/050505/c9a84c?text=Project+Visual'">
      </div>
      <div class="featured-details">
        <h2 class="project-title-large">ESD Note Ecosystem</h2>
        <p class="project-desc-large">
          A comprehensive suite of digital tools including the <strong>ESD Note Mobile App</strong> and Web Platform, designed to revolutionize student productivity in 2026. 
          Bridging technical functionality with user-centric design.
        </p>
        <div style="display:flex; gap:15px;">
           <span class="tag" style="border: 1px solid var(--border); padding: 5px 15px; font-size: 0.7rem;">FLUTTER</span>
           <span class="tag" style="border: 1px solid var(--border); padding: 5px 15px; font-size: 0.7rem;">REACT</span>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- CONNECT -->
<section id="connect" style="text-align:center; background: var(--deep);">
  <div class="section-label" style="justify-content:center;">02 — Contact</div>
  <h2 class="section-title">Let's <span>Connect</span></h2>
  <div style="display:flex; justify-content:center; gap:30px; flex-wrap:wrap; margin-top:40px;">
    <a href="https://github.com/sahandjayasingha" class="tag" style="text-decoration:none; color:var(--white); border:1px solid var(--border); padding:15px 30px;">GITHUB</a>
    <a href="https://www.linkedin.com/in/sahan-darshana-226bb4333/" class="tag" style="text-decoration:none; color:var(--white); border:1px solid var(--border); padding:15px 30px;">LINKEDIN</a>
  </div>
</section>

<footer style="padding:40px 6%; border-top:1px solid var(--border); display:flex; justify-content:space-between; font-size:0.8rem; color:var(--white-dim);">
  <div>Sahan <span>D</span> Jayasingha</div>
  <div>© 2026 — Portfolio</div>
</footer>

<script>
// ── PRELOADER TYPE ANIMATION
const nameStr = "Sahan D Jayasingha";
const goldChar = "D";
const container = document.getElementById('preloaderText');
let charDelay = 0;

for(let i=0; i<nameStr.length; i++){
  const s = document.createElement('span');
  s.className = 'char' + (nameStr[i]===goldChar ? ' gold' : '');
  s.textContent = nameStr[i]==' ' ? '\u00A0' : nameStr[i];
  s.style.animationDelay = charDelay+'ms';
  container.appendChild(s);
  charDelay += nameStr[i]==' ' ? 60 : 80;
}

setTimeout(()=>{
  document.getElementById('preloader').classList.add('hidden');
}, 3100);

// ── SCROLL REVEAL
const revealEls = document.querySelectorAll('.reveal');
const io = new IntersectionObserver((entries)=>{
  entries.forEach((e)=>{
    if(e.isIntersecting) e.target.style.opacity = "1";
  });
},{threshold:.15});
revealEls.forEach(el=>io.observe(el));
</script>

</body>
</html>
