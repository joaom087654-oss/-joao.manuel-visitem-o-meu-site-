<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>João Manuel | Portfólio TI</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --bg: #0a0a0a;
            --card-bg: #111111;
            --primary: #00d4ff;
            --secondary: #7b2fff;
            --accent: #ff2d95;
            --text: #e0e0e0;
            --text-secondary: #a0a0a0;
            --border: #252525;
            --glow: rgba(0, 212, 255, 0.3);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', 'Inter', system-ui, sans-serif;
            background: var(--bg);
            color: var(--text);
            overflow-x: hidden;
            min-height: 100vh;
            cursor: default;
            -webkit-font-smoothing: antialiased;
        }

        /* Canvas para partículas de fundo */
        #particles-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
            pointer-events: none;
        }

        /* Grid de fundo animada */
        .bg-grid {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
            pointer-events: none;
            background-image:
                linear-gradient(rgba(0, 212, 255, 0.03) 1px, transparent 1px),
                linear-gradient(90deg, rgba(0, 212, 255, 0.03) 1px, transparent 1px);
            background-size: 60px 60px;
            animation: gridMove 20s linear infinite;
        }

        @keyframes gridMove {
            0% {
                background-position: 0 0, 0 0;
            }
            100% {
                background-position: 60px 60px, -60px 60px;
            }
        }

        /* Container principal */
        .main-container {
            position: relative;
            z-index: 1;
            max-width: 1100px;
            margin: 0 auto;
            padding: 20px;
        }

        /* Header / Hero */
        .hero {
            text-align: center;
            padding: 60px 20px 40px;
            position: relative;
        }

        .hero-badge {
            display: inline-block;
            padding: 8px 20px;
            border: 1px solid var(--border);
            border-radius: 50px;
            font-size: 0.85rem;
            color: var(--primary);
            letter-spacing: 2px;
            text-transform: uppercase;
            margin-bottom: 25px;
            background: rgba(0, 212, 255, 0.05);
            backdrop-filter: blur(10px);
            animation: fadeInDown 0.8s ease-out;
            position: relative;
            overflow: hidden;
        }

        .hero-badge::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: conic-gradient(transparent, rgba(0, 212, 255, 0.2), transparent, rgba(123, 47, 255, 0.2), transparent);
            animation: badgeSpin 4s linear infinite;
        }

        .hero-badge span {
            position: relative;
            z-index: 1;
        }

        @keyframes badgeSpin {
            100% {
                transform: rotate(360deg);
            }
        }

        @keyframes fadeInDown {
            from {
                opacity: 0;
                transform: translateY(-20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .hero-name {
            font-size: clamp(2.8rem, 7vw, 5rem);
            font-weight: 800;
            letter-spacing: -2px;
            line-height: 1;
            margin-bottom: 10px;
            background: linear-gradient(135deg, #ffffff 0%, #00d4ff 40%, #7b2fff 70%, #ff2d95 100%);
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: shimmer 3s ease-in-out infinite;
            background-size: 300% 300%;
        }

        @keyframes shimmer {
            0%,
            100% {
                background-position: 0% 50%;
            }
            50% {
                background-position: 100% 50%;
            }
        }

        .hero-subtitle {
            font-size: 1.3rem;
            color: var(--text-secondary);
            font-weight: 400;
            letter-spacing: 3px;
            text-transform: uppercase;
            margin-bottom: 15px;
            animation: fadeInUp 0.8s ease-out 0.2s both;
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .hero-tagline {
            font-size: 1rem;
            color: #666;
            max-width: 500px;
            margin: 0 auto 30px;
            line-height: 1.6;
            animation: fadeInUp 0.8s ease-out 0.4s both;
        }

        /* Redes sociais na hero */
        .hero-social {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-top: 20px;
            animation: fadeInUp 0.8s ease-out 0.5s both;
        }

        .hero-social a {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 45px;
            height: 45px;
            border-radius: 50%;
            background: var(--card-bg);
            border: 1px solid var(--border);
            color: var(--text);
            font-size: 1.2rem;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            position: relative;
            overflow: hidden;
            text-decoration: none;
        }

        .hero-social a::before {
            content: '';
            position: absolute;
            inset: 0;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            opacity: 0;
            transition: opacity 0.3s;
        }

        .hero-social a:hover {
            border-color: transparent;
            transform: translateY(-5px);
            box-shadow: 0 15px 35px var(--glow);
            color: #fff;
        }

        .hero-social a:hover::before {
            opacity: 1;
        }

        .hero-social a i {
            position: relative;
            z-index: 1;
        }

        /* Seções */
        .section {
            margin: 30px 0 50px;
            animation: fadeInUp 0.8s ease-out both;
        }

        .section:nth-child(2) {
            animation-delay: 0.3s;
        }
        .section:nth-child(3) {
            animation-delay: 0.5s;
        }
        .section:nth-child(4) {
            animation-delay: 0.7s;
        }

        .section-title {
            font-size: 1.1rem;
            text-transform: uppercase;
            letter-spacing: 4px;
            color: var(--primary);
            margin-bottom: 25px;
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .section-title::before {
            content: '';
            width: 30px;
            height: 2px;
            background: var(--primary);
            box-shadow: 0 0 10px var(--primary);
        }

        /* Cards de skills */
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 15px;
        }

        .skill-card {
            background: var(--card-bg);
            border: 1px solid var(--border);
            border-radius: 16px;
            padding: 25px;
            position: relative;
            overflow: hidden;
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            cursor: pointer;
        }

        .skill-card::after {
            content: '';
            position: absolute;
            top: -100%;
            left: -100%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle at center, rgba(0, 212, 255, 0.08) 0%, transparent 70%);
            opacity: 0;
            transition: opacity 0.4s;
        }

        .skill-card:hover {
            border-color: var(--primary);
            transform: translateY(-5px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.5), 0 0 30px var(--glow);
        }

        .skill-card:hover::after {
            opacity: 1;
            animation: cardGlow 2s linear infinite;
        }

        @keyframes cardGlow {
            0% {
                transform: rotate(0deg);
            }
            100% {
                transform: rotate(360deg);
            }
        }

        .skill-card i {
            font-size: 2rem;
            margin-bottom: 12px;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .skill-card h3 {
            font-size: 1.1rem;
            margin-bottom: 6px;
            position: relative;
            z-index: 1;
        }

        .skill-card p {
            font-size: 0.85rem;
            color: var(--text-secondary);
            position: relative;
            z-index: 1;
            line-height: 1.5;
        }

        .skill-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-top: 12px;
            position: relative;
            z-index: 1;
        }

        .skill-tag {
            font-size: 0.7rem;
            padding: 5px 12px;
            border-radius: 20px;
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid var(--border);
            color: var(--text-secondary);
            letter-spacing: 1px;
            transition: all 0.3s;
        }

        .skill-card:hover .skill-tag {
            border-color: rgba(0, 212, 255, 0.3);
            color: var(--primary);
        }

        /* Projetos */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
        }

        .project-card {
            background: var(--card-bg);
            border: 1px solid var(--border);
            border-radius: 20px;
            padding: 30px;
            position: relative;
            overflow: hidden;
            transition: all 0.4s;
        }

        .project-card:hover {
            border-color: var(--secondary);
            box-shadow: 0 20px 40px rgba(123, 47, 255, 0.2);
            transform: translateY(-3px);
        }

        .project-icon {
            font-size: 2.5rem;
            margin-bottom: 15px;
            display: block;
        }

        .project-card h3 {
            font-size: 1.2rem;
            margin-bottom: 8px;
        }

        .project-card p {
            font-size: 0.85rem;
            color: var(--text-secondary);
            line-height: 1.5;
        }

        .project-tech {
            display: flex;
            flex-wrap: wrap;
            gap: 6px;
            margin-top: 15px;
        }

        .project-tech span {
            font-size: 0.7rem;
            padding: 4px 10px;
            border-radius: 15px;
            background: rgba(123, 47, 255, 0.1);
            color: #b388ff;
            border: 1px solid rgba(123, 47, 255, 0.2);
        }

        /* Linha do tempo / experiência */
        .timeline {
            position: relative;
            padding-left: 30px;
            border-left: 1px solid var(--border);
        }

        .timeline-item {
            margin-bottom: 25px;
            position: relative;
        }

        .timeline-item::before {
            content: '';
            position: absolute;
            left: -35px;
            top: 5px;
            width: 10px;
            height: 10px;
            border-radius: 50%;
            background: var(--primary);
            box-shadow: 0 0 15px var(--primary);
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%,
            100% {
                box-shadow: 0 0 10px var(--primary);
            }
            50% {
                box-shadow: 0 0 25px var(--primary), 0 0 50px var(--primary);
            }
        }

        .timeline-item h4 {
            font-size: 1rem;
            color: #fff;
        }

        .timeline-item .date {
            font-size: 0.75rem;
            color: var(--primary);
            letter-spacing: 2px;
            margin-bottom: 5px;
        }

        .timeline-item p {
            font-size: 0.85rem;
            color: var(--text-secondary);
        }

        /* Botões flutuantes */
        .floating-buttons {
            position: fixed;
            bottom: 30px;
            right: 30px;
            z-index: 1000;
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .float-btn {
            width: 55px;
            height: 55px;
            border-radius: 50%;
            border: none;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.4rem;
            color: #fff;
            text-decoration: none;
            position: relative;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.4);
            animation: floatIn 0.6s ease-out both;
        }

        .float-btn:nth-child(1) {
            animation-delay: 1s;
            background: #25D366;
        }
        .float-btn:nth-child(2) {
            animation-delay: 1.1s;
            background: #EA4335;
        }

        @keyframes floatIn {
            from {
                opacity: 0;
                transform: translateX(60px) scale(0.5);
            }
            to {
                opacity: 1;
                transform: translateX(0) scale(1);
            }
        }

        .float-btn:hover {
            transform: translateY(-8px) scale(1.1);
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.5);
        }

        .float-btn::after {
            content: attr(data-tooltip);
            position: absolute;
            right: 65px;
            background: var(--card-bg);
            color: #fff;
            padding: 8px 15px;
            border-radius: 20px;
            font-size: 0.8rem;
            white-space: nowrap;
            opacity: 0;
            pointer-events: none;
            transition: all 0.3s;
            border: 1px solid var(--border);
        }

        .float-btn:hover::after {
            opacity: 1;
            right: 70px;
        }

        .float-btn .pulse-ring {
            position: absolute;
            inset: 0;
            border-radius: 50%;
            animation: ringPulse 2s infinite;
            border: 2px solid currentColor;
            opacity: 0.6;
        }

        @keyframes ringPulse {
            0% {
                transform: scale(1);
                opacity: 0.6;
            }
            100% {
                transform: scale(1.6);
                opacity: 0;
            }
        }

        /* Footer */
        .footer {
            text-align: center;
            padding: 40px 20px;
            border-top: 1px solid var(--border);
            margin-top: 40px;
            color: #555;
            font-size: 0.85rem;
        }

        .footer .glow-text {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
            font-weight: 600;
        }

        /* Efeito de scanline */
        .scanline {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 999;
            background: repeating-linear-gradient(0deg,
                    transparent,
                    transparent 2px,
                    rgba(0, 0, 0, 0.03) 2px,
                    rgba(0, 0, 0, 0.03) 4px);
        }

        /* Responsivo */
        @media (max-width: 768px) {
            .hero-name {
                font-size: 2.5rem;
            }
            .floating-buttons {
                bottom: 20px;
                right: 20px;
                gap: 8px;
            }
            .float-btn {
                width: 48px;
                height: 48px;
                font-size: 1.2rem;
            }
            .float-btn::after {
                display: none;
            }
            .skills-grid,
            .projects-grid {
                grid-template-columns: 1fr;
            }
        }

        /* Scrollbar */
        ::-webkit-scrollbar {
            width: 6px;
        }
        ::-webkit-scrollbar-track {
            background: var(--bg);
        }
        ::-webkit-scrollbar-thumb {
            background: #252525;
            border-radius: 3px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #333;
        }
    </style>
</head>
<body>

    <!-- Scanline effect -->
    <div class="scanline"></div>

    <!-- Grid de fundo -->
    <div class="bg-grid"></div>

    <!-- Canvas para partículas -->
    <canvas id="particles-canvas"></canvas>

    <!-- Container principal -->
    <div class="main-container">
        <!-- Hero -->
        <header class="hero">
            <div class="hero-badge"><span> Seja bem vindo ao meu portifólio </span></div>
            <h1 class="hero-name">João Manuel</h1>
            <p class="hero-subtitle">Estudante de TI  Informática</p>
            <p class="hero-tagline">
                Apaixonado por tecnologia, programação e tudo que envolve o mundo digital.
                Transformando ideias em código e criando o futuro, uma linha de cada vez.
            </p>
            <div class="hero-social">
                <a href="https://www.instagram.com/joaomanuel8951?igsh=YWY4bzVrMXJ2ejRz" target="_blank" rel="noopener" title="Instagram">
                    <i class="fab fa-instagram"></i>
                </a>
                <a href="mailto:joao.m181818@gmail.com" title="Email">
                    <i class="fas fa-envelope"></i>
                </a>
                <a href="https://wa.me/244959448730" target="_blank" rel="noopener" title="WhatsApp">
                    <i class="fab fa-whatsapp"></i>
                </a>
            </div>
        </header>

        <!-- Skills / Habilidades -->
        <section class="section">
            <h2 class="section-title">Competências Técnicas</h2>
            <div class="skills-grid">
                <div class="skill-card">
                    <i class="fas fa-code"></i>
                    <h3>Programação</h3>
                    <p>Domínio de múltiplas linguagens e paradigmas de programação.</p>
                    <div class="skill-tags">
                        <span class="skill-tag">Python</span>
                        <span class="skill-tag">JavaScript</span>
                        <span class="skill-tag">Java</span>
                        <span class="skill-tag">C/C++</span>
                        <span class="skill-tag">PHP</span>
                    </div>
                </div>
                <div class="skill-card">
                    <i class="fas fa-globe"></i>
                    <h3>Desenvolvimento Web</h3>
                    <p>Criação de sites e aplicações web modernas e responsivas.</p>
                    <div class="skill-tags">
     
