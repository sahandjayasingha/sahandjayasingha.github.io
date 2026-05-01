<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sahan D Jayasingha | Professional Portfolio</title>
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@500&family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    <!-- Font Awesome for Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <!-- AOS Animation Library -->
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">
    
    <style>
        :root {
            --bg-black: #0a0a0a;
            --gold: #d4af37;
            --white: #ffffff;
            --red: #e63946;
            --text-gray: #b0b0b0;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            scroll-behavior: smooth;
        }

        body {
            background-color: var(--bg-black);
            color: var(--white);
            font-family: 'Poppins', sans-serif;
            overflow-x: hidden;
        }

        /* --- Typing Preloader --- */
        #loader {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100vh;
            background: var(--bg-black);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            transition: opacity 0.8s ease;
        }

        .typing-text {
            font-family: 'JetBrains Mono', monospace;
            font-size: 2.5rem;
            color: var(--white);
            border-right: 4px solid var(--gold);
            white-space: nowrap;
            overflow: hidden;
            width: 0;
            animation: typing 2.5s steps(20, end) forwards, blink 0.8s infinite;
        }

        .typing-text span { color: var(--gold); }

        @keyframes typing { from { width: 0; } to { width: 100%; } }
        @keyframes blink { 50% { border-color: transparent; } }

        /* --- Navigation --- */
        nav {
            padding: 20px 10%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: rgba(10, 10, 10, 0.9);
            position: sticky;
            top: 0;
            z-index: 100;
            border-bottom: 1px solid rgba(212, 175, 55, 0.2);
        }

        .logo { font-size: 1.5rem; font-weight: 700; color: var(--white); }
        .logo span { color: var(--gold); }

        .nav-links { list-style: none; display: flex; }
        .nav-links li { margin-left: 30px; }
        .nav-links a { text-decoration: none; color: var(--white); font-size: 0.9rem; transition: 0.3s; }
        .nav-links a:hover { color: var(--gold); }

        /* --- Hero Section --- */
        .hero {
            height: 90vh;
            display: flex;
            align-items: center;
            padding: 0 10%;
            justify-content: space-between;
        }

        .hero-content { max-width: 600px; }
        .hero-content h2 { color: var(--gold); font-size: 1.2rem; margin-bottom: 10px; }
        .hero-content h1 { font-size: 3.5rem; margin-bottom: 20px; }
        .hero-content p { color: var(--text-gray); line-height: 1.8; margin-bottom: 30px; }

        .hero-image {
            width: 400px;
            height: 400px;
            border: 5px solid var(--gold);
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 0 30px rgba(212, 175, 55, 0.3);
        }

        .hero-image img { width: 100%; height: 100%; object-fit: cover; }

        .btn {
            padding: 12px 30px;
            background: transparent;
            border: 2px solid var(--gold);
            color: var(--gold);
            text-decoration: none;
            font-weight: 600;
            transition: 0.4s;
            border-radius: 5px;
        }

        .btn:hover { background: var(--gold); color: var(--bg-black); }

        /* --- Key Projects Section --- */
        .projects { padding: 100px 10%; background: #0f0f0f; }
        .section-title { text-align: center; font-size: 2.5rem; margin-bottom: 60px; }
        .section-title span { color: var(--gold); }

        .project-row {
            display: flex;
            gap: 50px;
            align-items: center;
            background: #1a1a1a;
            padding: 30px;
            border-radius: 15px;
            border-left: 5px solid var(--red);
        }

        .project-img { flex: 1; border-radius: 10px; overflow: hidden; }
        .project-img img { width: 100%; height: auto; transition: 0.5s; }
        .project-img img:hover { transform: scale(1.05); }

        .project-details { flex: 1; }
        .project-details h3 { font-size: 1.8rem; margin-bottom: 15px; color: var(--gold); }
        .project-details ul { list-style: none; color: var(--text-gray); }
        .project-details li { margin-bottom: 10px; display: flex; align-items: center; }
        .project-details li i { color: var(--red); margin-right: 10px; }

        /* --- Skills Section --- */
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            padding: 50px 10%;
        }

        .skill-card {
            background: #1a1a1a;
            padding: 20px;
            border-radius: 10px;
            transition: 0.3s;
            border-bottom: 3px solid transparent;
        }

        .skill-card:hover { border-color: var(--gold); transform: translateY(-5px); }
        .skill-info { display: flex; justify-content: space-between; margin-bottom: 10px; }
        .skill-bar { height: 8px; background: #333; border-radius: 5px; overflow: hidden; }
        .skill-progress { height: 100%; background: linear-gradient(to right, var(--gold), var(--red)); }

        /* --- Footer --- */
        footer {
            padding: 50px 10%;
            text-align: center;
            border-top: 1px solid #333;
        }

        .social-icons a {
            font-size: 1.5rem;
            color: var(--white);
            margin: 0 15px;
            transition: 0.3s;
        }

        .social-icons a:hover { color: var(--gold); }

        @media (max-width: 992px) {
            .hero, .project-row { flex-direction: column; text-align: center; }
            .hero-image { width: 300px; height: 300px; margin-top: 30px; }
            .project-img { order: 1; }
            .project-details { order: 2; }
        }
    </style>
</head>
<body>

    <!-- Loading Animation Screen -->
    <div id="loader">
        <div class="typing-text">Sahan <span>D</span> Jayasingha</div>
    </div>

    <!-- Main Content -->
    <nav>
        <div class="logo">Sahan <span>D</span> Jayasingha</div>
        <ul class="nav-links">
            <li><a href="#home">Home</a></li>
            <li><a href="#about">About</a></li>
            <li><a href="#projects">Projects</a></li>
            <li><a href="#contact">Contact</a></li>
        </ul>
    </nav>

    <section id="home" class="hero">
        <div class="hero-content" data-aos="fade-right">
            <h2>Welcome to my Portfolio</h2>
            <h1>Hi, I'm Sahan <span>D</span> Jayasingha</h1>
            <p>AI Engineering Undergraduate at NSBM | Founder of ESD pvt ltd | Full-Stack Web Developer | Graphic Designer & App Developer with 3+ Years of Experience.</p>
            <a href="https://github.com/sahandjayasingha" class="btn"><i class="fab fa-github"></i> View GitHub</a>
        </div>
        <div class="hero-image" data-aos="zoom-in">
            <img src="input_file_0.png" alt="Sahan D Jayasingha Profile">
        </div>
    </section>

    <section id="projects" class="projects">
        <h2 class="section-title">Key <span>Projects</span></h2>
        <div class="project-row" data-aos="fade-up">
            <div class="project-img">
                <img src="input_file_1.png" alt="Featured Project">
            </div>
            <div class="project-details">
                <h3>Impactful Digital Innovations</h3>
                <ul>
                    <li><i class="fas fa-check-circle"></i> <strong>ESD Note Mobile App:</strong> Student Productivity Platform (2026)</li>
                    <li><i class="fas fa-check-circle"></i> <strong>ESD Official Website:</strong> Educational Hub</li>
                    <li><i class="fas fa-check-circle"></i> <strong>Pro Cam App:</strong> Custom Flutter Camera Solution</li>
                    <li><i class="fas fa-check-circle"></i> <strong>Thenu Mart:</strong> E-commerce Clothing Brand</li>
                </ul>
                <p style="margin-top: 20px; color: var(--text-gray);">Bridging technical functionality and creative design to empower users globally.</p>
            </div>
        </div>
    </section>

    <section id="skills" class="projects" style="background: var(--bg-black);">
        <h2 class="section-title">Technical <span>Expertise</span></h2>
        <div class="skills-grid">
            <div class="skill-card" data-aos="flip-left">
                <div class="skill-info"><span>React</span><span>100%</span></div>
                <div class="skill-bar"><div class="skill-progress" style="width: 100%;"></div></div>
            </div>
            <div class="skill-card" data-aos="flip-left" data-aos-delay="100">
                <div class="skill-info"><span>Python</span><span>80%</span></div>
                <div class="skill-bar"><div class="skill-progress" style="width: 80%;"></div></div>
            </div>
            <div class="skill-card" data-aos="flip-left" data-aos-delay="200">
                <div class="skill-info"><span>Dart/Flutter</span><span>70%</span></div>
                <div class="skill-bar"><div class="skill-progress" style="width: 70%;"></div></div>
            </div>
            <div class="skill-card" data-aos="flip-left" data-aos-delay="300">
                <div class="skill-info"><span>Graphic Design</span><span>95%</span></div>
                <div class="skill-bar"><div class="skill-progress" style="width: 95%;"></div></div>
            </div>
        </div>
    </section>

    <footer id="contact">
        <h2 style="margin-bottom: 20px;">Let's <span>Connect</span></h2>
        <div class="social-icons">
            <a href="https://www.linkedin.com/in/sahan-darshana-226bb4333/"><i class="fab fa-linkedin"></i></a>
            <a href="https://github.com/sahandjayasingha"><i class="fab fa-github"></i></a>
            <a href="https://www.facebook.com/sahan.darshana.707221"><i class="fab fa-facebook"></i></a>
            <a href="https://www.instagram.com/sd_jayasingha"><i class="fab fa-instagram"></i></a>
        </div>
        <p style="margin-top: 30px; font-size: 0.8rem; color: var(--text-gray);">&copy; 2026 Sahan D Jayasingha. All Rights Reserved.</p>
    </footer>

    <!-- AOS Script -->
    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script>
        // Initialize Animations
        AOS.init({ duration: 1000, once: true });

        // Hide Preloader after animation
        window.addEventListener('load', () => {
            setTimeout(() => {
                const loader = document.getElementById('loader');
                loader.style.opacity = '0';
                setTimeout(() => {
                    loader.style.display = 'none';
                }, 800);
            }, 3000); // Loader displays for 3 seconds
        });
    </script>
</body>
</html>
