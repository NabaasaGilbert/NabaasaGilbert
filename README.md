<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Developer Profile | GitHub</title>
    <!-- Importing Fonts: Inter for UI, Fira Code for code snippets -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;600&family=Inter:wght@400;600;800&display=swap" rel="stylesheet">
    <!-- FontAwesome for Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <style>
        /* --- CSS Variables & Reset --- */
        :root {
            --bg-body: #0d1117;
            --bg-card: #161b22;
            --bg-input: #010409;
            --border-color: #30363d;
            --text-main: #c9d1d9;
            --text-muted: #8b949e;
            --accent-primary: #58a6ff;
            --accent-secondary: #238636; /* GitHub Green */
            --accent-tertiary: #a371f7;
            --glow: 0 0 10px rgba(88, 166, 255, 0.15);
            --font-ui: 'Inter', sans-serif;
            --font-code: 'Fira Code', monospace;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            background-color: var(--bg-body);
            color: var(--text-main);
            font-family: var(--font-ui);
            line-height: 1.6;
            overflow-x: hidden;
        }

        a {
            text-decoration: none;
            color: inherit;
            transition: 0.3s ease;
        }

        ul {
            list-style: none;
        }

        /* --- Utility Classes --- */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        .btn {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            padding: 10px 20px;
            border-radius: 6px;
            font-weight: 600;
            font-size: 0.95rem;
            border: 1px solid var(--border-color);
            background-color: var(--bg-card);
            color: var(--text-main);
            cursor: pointer;
            transition: all 0.2s ease;
        }

        .btn:hover {
            border-color: var(--text-muted);
            transform: translateY(-2px);
        }

        .btn-primary {
            background-color: var(--accent-secondary);
            border-color: rgba(255,255,255,0.1);
            color: white;
        }

        .btn-primary:hover {
            background-color: #2ea043;
            border-color: rgba(255,255,255,0.2);
        }

        .section-title {
            font-size: 1.8rem;
            margin-bottom: 2rem;
            color: var(--text-main);
            border-bottom: 1px solid var(--border-color);
            padding-bottom: 10px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .section-title i {
            color: var(--accent-primary);
        }

        /* --- Header / Nav --- */
        header {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(13, 17, 23, 0.85);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid var(--border-color);
            z-index: 1000;
            padding: 15px 0;
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-family: var(--font-code);
            font-weight: 700;
            font-size: 1.2rem;
            color: var(--text-main);
        }

        .logo span {
            color: var(--accent-primary);
        }

        .nav-links {
            display: flex;
            gap: 25px;
        }

        .nav-links a {
            font-size: 0.9rem;
            font-weight: 600;
            color: var(--text-muted);
        }

        .nav-links a:hover {
            color: var(--accent-primary);
        }

        /* --- Hero Section --- */
        .hero {
            padding: 140px 0 80px;
            display: grid;
            grid-template-columns: 1.2fr 0.8fr;
            gap: 40px;
            align-items: center;
        }

        .hero-content h1 {
            font-size: 3.5rem;
            line-height: 1.1;
            margin-bottom: 20px;
            background: linear-gradient(135deg, #fff 0%, #8b949e 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .hero-content .tagline {
            font-family: var(--font-code);
            color: var(--accent-primary);
            margin-bottom: 20px;
            display: block;
        }

        .hero-content p {
            color: var(--text-muted);
            font-size: 1.1rem;
            max-width: 500px;
            margin-bottom: 30px;
        }

        .hero-stats {
            display: flex;
            gap: 30px;
            margin-top: 30px;
        }

        .stat-item h3 {
            font-size: 1.5rem;
            color: var(--text-main);
        }

        .stat-item span {
            font-size: 0.85rem;
            color: var(--text-muted);
        }

        /* Terminal Window Animation */
        .terminal-window {
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: 8px;
            box-shadow: 0 20px 50px rgba(0,0,0,0.5);
            overflow: hidden;
            font-family: var(--font-code);
            font-size: 0.9rem;
        }

        .terminal-header {
            background: #010409;
            padding: 10px 15px;
            display: flex;
            gap: 8px;
            border-bottom: 1px solid var(--border-color);
        }

        .dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
        }

        .red { background: #ff5f56; }
        .yellow { background: #ffbd2e; }
        .green { background: #27c93f; }

        .terminal-body {
            padding: 20px;
            color: var(--text-main);
        }

        .command-line {
            display: flex;
            gap: 10px;
            margin-bottom: 10px;
        }

        .prompt {
            color: var(--accent-secondary);
        }

        .cursor {
            display: inline-block;
            width: 8px;
            height: 15px;
            background: var(--accent-primary);
            animation: blink 1s infinite;
            vertical-align: middle;
        }

        @keyframes blink {
            0%, 100% { opacity: 1; }
            50% { opacity: 0; }
        }

        /* --- Tech Stack --- */
        .tech-stack {
            padding: 40px 0;
            border-top: 1px solid var(--border-color);
            border-bottom: 1px solid var(--border-color);
            background: rgba(22, 27, 34, 0.5);
            overflow: hidden;
        }

        .tech-track {
            display: flex;
            gap: 40px;
            width: max-content;
            animation: scroll 20s linear infinite;
        }

        .tech-item {
            display: flex;
            align-items: center;
            gap: 10px;
            font-family: var(--font-code);
            color: var(--text-muted);
            font-size: 1.1rem;
        }

        .tech-item i {
            font-size: 1.4rem;
            color: var(--text-main);
        }

        @keyframes scroll {
            0% { transform: translateX(0); }
            100% { transform: translateX(-50%); }
        }

        /* --- Repositories Grid --- */
        .repositories {
            padding: 80px 0;
        }

        .repo-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
            gap: 20px;
        }

        .repo-card {
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: 6px;
            padding: 20px;
            transition: 0.3s ease;
            position: relative;
            top: 0;
        }

        .repo-card:hover {
            border-color: var(--text-muted);
            top: -5px;
            box-shadow: var(--glow);
        }

        .repo-header {
            display: flex;
            align-items: center;
            gap: 8px;
            margin-bottom: 10px;
        }

        .repo-header i {
            color: var(--text-muted);
        }

        .repo-title {
            font-weight: 700;
            color: var(--accent-primary);
            font-size: 1.1rem;
        }

        .public-tag {
            border: 1px solid var(--border-color);
            border-radius: 12px;
            font-size: 0.7rem;
            padding: 0 6px;
            color: var(--text-muted);
            margin-left: auto;
        }

        .repo-desc {
            font-size: 0.9rem;
            color: var(--text-muted);
            margin-bottom: 20px;
            min-height: 40px;
        }

        .repo-meta {
            display: flex;
            gap: 15px;
            font-size: 0.8rem;
            color: var(--text-muted);
            align-items: center;
        }

        .lang-dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            display: inline-block;
        }

        .star-btn {
            margin-left: auto;
            background: none;
            border: none;
            color: var(--text-muted);
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 4px;
        }

        .star-btn:hover {
            color: var(--accent-primary);
        }

        /* --- Contribution Graph Simulation --- */
        .contributions {
            padding: 50px 0;
            background: var(--bg-card);
            border-top: 1px solid var(--border-color);
            border-bottom: 1px solid var(--border-color);
        }

        .graph-container {
            display: flex;
            gap: 10px;
            justify-content: space-between;
            align-items: center;
        }

        .graph-text {
            flex: 1;
        }
        
        .graph-text h3 {
            margin-bottom: 10px;
            font-size: 1.4rem;
        }

        .css-graph {
            display: grid;
            grid-template-rows: repeat(7, 12px);
            grid-template-columns: repeat(20, 12px);
            gap: 4px;
            flex: 1;
            max-width: 350px;
        }

        .square {
            background-color: #161b22;
            border-radius: 2px;
        }

        .l1 { background-color: #0e4429; }
        .l2 { background-color: #006d32; }
        .l3 { background-color: #26a641; }
        .l4 { background-color: #39d353; }

        /* --- Footer --- */
        footer {
            padding: 40px 0;
            text-align: center;
            border-top: 1px solid var(--border-color);
            font-size: 0.9rem;
            color: var(--text-muted);
        }

        .social-links {
            margin-bottom: 20px;
            display: flex;
            justify-content: center;
            gap: 20px;
        }

        .social-links a {
            font-size: 1.5rem;
            color: var(--text-muted);
        }

        .social-links a:hover {
            color: var(--accent-primary);
        }

        /* --- Mobile Responsive --- */
        @media (max-width: 768px) {
            .hero {
                grid-template-columns: 1fr;
                text-align: center;
                padding-top: 100px;
            }

            .hero-stats {
                justify-content: center;
            }

            .terminal-window {
                margin-top: 40px;
            }

            .nav-links {
                display: none; /* Simple hiding for this demo, usually use hamburger menu */
            }

            .logo {
                margin: 0 auto;
            }

            .graph-container {
                flex-direction: column;
                text-align: center;
            }
        }
    </style>
</head>
<body>

    <!-- Navigation -->
    <header>
        <div class="container">
            <nav>
                <a href="#" class="logo">&lt;Dev<span>Profile</span>/&gt;</a>
                <div class="nav-links">
                    <a href="#home">Home</a>
                    <a href="#about">About</a>
                    <a href="#repos">Repositories</a>
                    <a href="#contact">Contact</a>
                </div>
                <a href="#contact" class="btn btn-primary" style="display: none; @media(min-width: 768px){display:inline-flex;}">
                    <i class="fab fa-github"></i> Follow Me
                </a>
            </nav>
        </div>
    </header>

    <!-- Main Content -->
    <main>
        
        <!-- Hero Section -->
        <section class="hero container" id="home">
            <div class="hero-content">
                <span class="tagline">Hi, my name is</span>
                <h1 id="typing-text">Alex Developer</h1>
                <p>I build accessible, pixel-perfect, and performant web experiences. Passionate about open source and creative coding.</p>
                
                <div style="display: flex; gap: 15px; flex-wrap: wrap; justify-content: center; @media(min-width:768px){justify-content: flex-start;}">
                    <a href="#repos" class="btn btn-primary">
                        <i class="fas fa-code-branch"></i> View Projects
                    </a>
                    <a href="mailto:email@example.com" class="btn">
                        <i class="far fa-envelope"></i> Contact Me
                    </a>
                </div>

                <div class="hero-stats">
                    <div class="stat-item">
                        <h3>50+</h3>
                        <span>Repositories</span>
                    </div>
                    <div class="stat-item">
                        <h3>1.2k</h3>
                        <span>Stars</span>
                    </div>
                    <div class="stat-item">
                        <h3>200+</h3>
                        <span>Followers</span>
                    </div>
                </div>
            </div>

            <!-- Terminal Visual -->
            <div class="terminal-window">
                <div class="terminal-header">
                    <div class="dot red"></div>
                    <div class="dot yellow"></div>
                    <div class="dot green"></div>
                </div>
                <div class="terminal-body">
                    <div class="command-line">
                        <span class="prompt">➜</span>
                        <span>~/portfolio</span>
                        <span class="cursor"></span>
                    </div>
                    <div style="color: var(--text-muted); margin-top: 5px;">
                        <span style="color: #ff7b72;">const</span> developer = {<br>
                        &nbsp;&nbsp;name: <span style="color: #a5d6ff;">"Alex"</span>,<br>
                        &nbsp;&nbsp;skills: [<span style="color: #a5d6ff;">"HTML"</span>, <span style="color: #a5d6ff;">"CSS"</span>, <span style="color: #a5d6ff;">"JS"</span>],<br>
                        &nbsp;&nbsp;hardWorker: <span style="color: #79c0ff;">true</span>,<br>
                        &nbsp;&nbsp;hireable: <span style="color: #79c0ff;">function</span>() {<br>
                        &nbsp;&nbsp;&nbsp;&nbsp;<span style="color: #ff7b72;">return</span> <span style="color: #a5d6ff;">"Let's talk!"</span>;<br>
                        &nbsp;&nbsp;}<br>
                        };
                    </div>
                </div>
            </div>
        </section>

        <!-- Infinite Tech Stack -->
        <div class="tech-stack">
            <div class="tech-track">
                <!-- Duplicated items for seamless infinite scroll -->
                <div class="tech-item"><i class="fab fa-js"></i> JavaScript</div>
                <div class="tech-item"><i class="fab fa-react"></i> React</div>
                <div class="tech-item"><i class="fab fa-python"></i> Python</div>
                <div class="tech-item"><i class="fab fa-node"></i> Node.js</div>
                <div class="tech-item"><i class="fab fa-html5"></i> HTML5</div>
                <div class="tech-item"><i class="fab fa-css3-alt"></i> CSS3</div>
                <div class="tech-item"><i class="fab fa-git-alt"></i> Git</div>
                <div class="tech-item"><i class="fab fa-docker"></i> Docker</div>
                <div class="tech-item"><i class="fab fa-figma"></i> Figma</div>
                <!-- Repeat -->
                <div class="tech-item"><i class="fab fa-js"></i> JavaScript</div>
                <div class="tech-item"><i class="fab fa-react"></i> React</div>
                <div class="tech-item"><i class="fab fa-python"></i> Python</div>
                <div class="tech-item"><i class="fab fa-node"></i> Node.js</div>
                <div class="tech-item"><i class="fab fa-html5"></i> HTML5</div>
                <div class="tech-item"><i class="fab fa-css3-alt"></i> CSS3</div>
                <div class="tech-item"><i class="fab fa-git-alt"></i> Git</div>
                <div class="tech-item"><i class="fab fa-docker"></i> Docker</div>
                <div class="tech-item"><i class="fab fa-figma"></i> Figma</div>
            </div>
        </div>

        <!-- Repositories Section -->
        <section class="repositories container" id="repos">
            <h2 class="section-title"><i class="fas fa-book"></i> Pinned Repositories</h2>
            
            <div class="repo-grid">
                <!-- Repo Card 1 -->
                <div class="repo-card">
                    <div class="repo-header">
                        <i class="fas fa-book"></i>
                        <a href="#" class="repo-title">awesome-portfolio</a>
                        <span class="public-tag">Public</span>
                    </div>
                    <p class="repo-desc">A clean, dark-mode portfolio template for developers hosted on GitHub Pages.</p>
                    <div class="repo-meta">
                        <span><span class="lang-dot" style="background: #f1e05a;"></span> JavaScript</span>
                        <span><i class="far fa-star"></i> 42</span>
                        <span><i class="fas fa-code-branch"></i> 15</span>
                        <button class="star-btn" title="Star this repo"><i class="far fa-star"></i></button>
                    </div>
                </div>

                <!-- Repo Card 2 -->
                <div class="repo-card">
                    <div class="repo-header">
                        <i class="fas fa-book"></i>
                        <a href="#" class="repo-title">api-dashboard</a>
                        <span class="public-tag">Public</span>
                    </div>
                    <p class="repo-desc">A visualization dashboard to track API latency and uptime metrics.</p>
                    <div class="repo-meta">
                        <span><span class="lang-dot" style="background: #3178c6;"></span> TypeScript</span>
                        <span><i class="far fa-star"></i> 128</span>
                        <span><i class="fas fa-code-branch"></i> 30</span>
                        <button class="star-btn" title="Star this repo"><i class="far fa-star"></i></button>
                    </div>
                </div>

                <!-- Repo Card 3 -->
                <div class="repo-card">
                    <div class="repo-header">
                        <i class="fas fa-book"></i>
                        <a href="#" class="repo-title">css-grid-experiments</a>
                        <span class="public-tag">Public</span>
                    </div>
                    <p class="repo-desc">Collection of complex CSS grid layouts and animation experiments.</p>
                    <div class="repo-meta">
                        <span><span class="lang-dot" style="background: #563d7c;"></span> CSS</span>
                        <span><i class="far fa-star"></i> 85</span>
                        <span><i class="fas fa-code-branch"></i> 12</span>
                        <button class="star-btn" title="Star this repo"><i class="far fa-star"></i></button>
                    </div>
                </div>

                <!-- Repo Card 4 -->
                <div class="repo-card">
                    <div class="repo-header">
                        <i class="fas fa-book"></i>
                        <a href="#" class="repo-title">cli-tools</a>
                        <span class="public-tag">Public</span>
                    </div>
                    <p class="repo-desc">Useful CLI tools written in Python for automating daily dev tasks.</p>
                    <div class="repo-meta">
                        <span><span class="lang-dot" style="background: #3572A5;"></span> Python</span>
                        <span><i class="far fa-star"></i> 67</span>
                        <span><i class="fas fa-code-branch"></i> 8</span>
                        <button class="star-btn" title="Star this repo"><i class="far fa-star"></i></button>
                    </div>
                </div>
            </div>
        </section>

        <!-- Contribution Graph Simulation -->
        <section class="contributions">
            <div class="container graph-container">
                <div class="graph-text">
                    <h3><i class="fas fa-chart-bar"></i> Contribution Activity</h3>
                    <p style="color: var(--text-muted); max-width: 400px;">
                        I am consistently pushing code. This visualization represents my commitment to open source and learning.
                    </p>
                    <div style="margin-top: 20px;">
                        <span class="btn" style="font-size: 0.8rem;">View on GitHub</span>
                    </div>
                </div>
                
                <!-- CSS-only graph -->
                <div class="css-graph">
                    <!-- Row 1 -->
                    <div class="square l4"></div><div class="square l2"></div><div class="square l3"></div><div class="square"></div><div class="square l1"></div><div class="square l4"></div><div class="square l4"></div><div class="square l2"></div><div class="square"></div><div class="square l1"></div><div class="square"></div><div class="square l3"></div><div class="square l4"></div><div class="square l1"></div><div class="square"></div><div class="square l2"></div><div class="square l4"></div><div class="square"></div><div class="square"></div><div class="square l3"></div>
                    <!-- Row 2 -->
                    <div class="square l3"></div><div class="square l4"></div><div class="square l1"></div><div class="square l2"></div><div class="square"></div><div class="square l3"></div><div class="square"></div><div class="square l1"></div><div class="square l4"></div><div class="square l3"></div><div class="square"></div><div class="square"></div><div class="square l2"></div><div class="square l1"></div><div class="square l4"></div><div class="square l3"></div><div class="square l2"></div><div class="square"></div><div class="square l1"></div><div class="square l4"></div>
                    <!-- Row 3 -->
                    <div class="square"></div><div class="square l1"></div><div class="square"></div><div class="square l3"></div><div class="square l4"></div><div class="square l1"></div><div class="square l2"></div><div class="square"></div><div class="square"></div><div class="square l1"></div><div class="square l2"></div><div class="square l4"></div><div class="square l3"></div><div class="square"></div><div class="square l1"></div><div class="square l2"></div><div class="square"></div><div class="square l4"></div><div class="square l3"></div><div class="square"></div>
                    <!-- Row 4 -->
                    <div class="square l2"></div><div class="square l3"></div><div class="square l4"></div><div class="square"></div><div class="square l1"></div><div class="square l2"></div><div class="square l3"></div><div class="square l4"></div><div class="square l1"></div><div class="square"></div><div class="square l3"></div><div class="square l2"></div><div class="square"></div><div class="square l1"></div><div class="square l4"></div><div class="square"></div><div class="square l3"></div><div class="square l2"></div><div class="square l1"></div><div class="square"></div>
                    <!-- Row 5 -->
                    <div class="square l4"></div><div class="square"></div><div class="square l2"></div><div class="square l1"></div><div class="square l3"></div><div class="square"></div><div class="square l4"></div><div class="square l1"></div><div class="square l2"></div><div class="square l3"></div><div class="square"></div><div class="square l4"></div><div class="square l1"></div><div class="square"></div><div class="square l2"></div><div class="square l3"></div><div class="square l4"></div><div class="square"></div><div class="square l1"></div><div class="square l2"></div>
                    <!-- Row 6 -->
                    <div class="square l1"></div><div class="square l2"></div><div class="square"></div><div class="square l4"></div><div class="square l3"></div><div class="square l1"></div><div class="square"></div><div class="square l2"></div><div class="square l4"></div><div class="square"></div><div class="square l1"></div><div class="square l3"></div><div class="square l2"></div><div class="square l4"></div><div class="square"></div><div class="square l1"></div><div class="square l2"></div><div class="square"></div><div class="square l4"></div><div class="square l3"></div>
                    <!-- Row 7 -->
                    <div class="square l3"></div><div class="square l4"></div><div class="square l1"></div><div class="square l2"></div><div class="square"></div><div class="square l3"></div><div class="square l4"></div><div class="square"></div><div class="square l1"></div><div class="square l2"></div><div class="square l3"></div><div class="square l4"></div><div class="square"></div><div class="square l1"></div><div class="square l2"></div><div class="square l3"></div><div class="square l4"></div><div class="square"></div><div class="square l1"></div><div class="square l2"></div>
                </div>
            </div>
        </section>

    </main>

    <!-- Footer -->
    <footer id="contact">
        <div class="container">
            <div class="social-links">
                <a href="#" aria-label="GitHub"><i class="fab fa-github"></i></a>
                <a href="#" aria-label="Twitter"><i class="fab fa-twitter"></i></a>
                <a href="#" aria-label="LinkedIn"><i class="fab fa-linkedin"></i></a>
                <a href="#" aria-label="Dev.to"><i class="fab fa-dev"></i></a>
            </div>
            <p>&copy; <span id="year"></span> Alex Developer. Built with HTML & CSS.</p>
        </div>
    </footer>

    <!-- Simple Scripts -->
    <script>
        // Update Copyright Year
        document.getElementById('year').textContent = new Date().getFullYear();

        // Simple Typing Effect for Header
        const textElement = document.getElementById('typing-text');
        const roles = ["Full Stack Dev", "Open Source", "UI/UX Enthusiast"];
        let roleIndex = 0;
        let charIndex = 0;
        let isDeleting = false;

        function typeEffect() {
            const currentRole = roles[roleIndex];
            
            if (isDeleting) {
                textElement.textContent = currentRole.substring(0, charIndex - 1);
                charIndex--;
            } else {
                textElement.textContent = currentRole.substring(0, charIndex + 1);
                charIndex++;
            }

            let typeSpeed = isDeleting ? 50 : 100;

            if (!isDeleting && charIndex === currentRole.length) {
                isDeleting = true;
                typeSpeed = 2000; // Pause at end
            } else if (isDeleting && charIndex === 0) {
                isDeleting = false;
                roleIndex = (roleIndex + 1) % roles.length;
                typeSpeed = 500; // Pause before new word
            }

            setTimeout(typeEffect, typeSpeed);
        }

        document.addEventListener('DOMContentLoaded', typeEffect);

        // Simple Star Button Interaction
        const starBtns = document.querySelectorAll('.star-btn');
        starBtns.forEach(btn => {
            btn.addEventListener('click', function() {
                const icon = this.querySelector('i');
                if (icon.classList.contains('far')) {
                    icon.classList.remove('far');
                    icon.classList.add('fas');
                    icon.style.color = '#e3b341';
                    this.style.color = '#e3b341';
                } else {
                    icon.classList.remove('fas');
                    icon.classList.add('far');
                    icon.style.color = '';
                    this.style.color = '';
                }
            });
        });
    </script>
</body>
</html>
