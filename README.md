<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Farmacia Nieto - Tu camino hacia el bienestar</title>
    <meta name="description" content="Farmacia especializada en elaboración magistral personalizada. Medicina ortomolecular, dermocosmética, homeopatía y más. Atención personalizada desde 1996.">
    <meta name="keywords" content="farmacia, medicamentos magistrales, homeopatía, dermocosmética, probióticos, medicina ortomolecular">
    
    <link rel="preload" href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap" as="style">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --primary-color: #86a486;
            --primary-dark: #2d4a2d;
            --primary-light: #9bb49b;
            --accent-color: #e8f4e8;
            --text-dark: #2c2c2c;
            --text-light: #5a5a5a;
            --white: #ffffff;
            --off-white: #fafafa;
            --shadow-light: rgba(134, 164, 134, 0.12);
            --shadow-medium: rgba(134, 164, 134, 0.22);
            --transition-smooth: all 0.35s cubic-bezier(0.4, 0, 0.2, 1);
            --border-radius: 20px;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
            line-height: 1.6;
            color: var(--text-dark);
            overflow-x: hidden;
            background: var(--off-white);
        }

        .loading-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, var(--accent-color), var(--white));
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 9999;
            transition: opacity 0.5s ease, visibility 0.5s ease;
        }

        .loading-screen.hidden {
            opacity: 0;
            visibility: hidden;
        }

        .loader {
            width: 60px;
            height: 60px;
            border: 4px solid var(--accent-color);
            border-top: 4px solid var(--primary-color);
            border-radius: 50%;
            animation: spin 1s linear infinite;
            box-shadow: 0 4px 15px var(--shadow-light);
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        .header {
            position: fixed;
            top: 0;
            width: 100%;
            height: 82px;
            background: rgba(255, 255, 255, 0.96);
            backdrop-filter: blur(20px);
            border-bottom: 1px solid rgba(134, 164, 134, 0.15);
            display: flex;
            align-items: center;
            padding: 0 5%;
            z-index: 1000;
            transition: var(--transition-smooth);
        }

        .header.scrolled {
            background: rgba(255, 255, 255, 0.98);
            box-shadow: 0 6px 25px rgba(0,0,0,0.08);
        }

        .logo {
            display: flex;
            align-items: center;
            font-size: 30px;
            font-weight: 800;
            color: var(--primary-color);
            margin-right: 45px;
            cursor: pointer;
            transition: var(--transition-smooth);
        }

        .logo:hover {
            transform: scale(1.03);
            filter: drop-shadow(0 4px 12px var(--shadow-light));
        }

        .logo-icon {
            width: 42px;
            height: 42px;
            margin-right: 13px;
            background: linear-gradient(135deg, var(--primary-color), var(--primary-light));
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 21px;
            box-shadow: 0 4px 15px var(--shadow-light);
        }

        .nav-menu {
            display: flex;
            list-style: none;
            gap: 32px;
            margin-left: auto;
        }

        .nav-item {
            color: var(--text-light);
            text-decoration: none;
            font-weight: 500;
            padding: 11px 16px;
            border-radius: 10px;
            transition: var(--transition-smooth);
            position: relative;
        }

        .nav-item::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 50%;
            width: 0;
            height: 2px;
            background: linear-gradient(90deg, var(--primary-color), var(--primary-light));
            transition: var(--transition-smooth);
            transform: translateX(-50%);
            border-radius: 2px;
        }

        .nav-item:hover::after,
        .nav-item.active::after {
            width: 75%;
        }

        .nav-item:hover,
        .nav-item.active {
            background: rgba(134, 164, 134, 0.08);
            color: var(--primary-color);
            transform: translateY(-1px);
        }

        .mobile-menu-btn {
            display: none;
            background: none;
            border: none;
            font-size: 24px;
            cursor: pointer;
            color: var(--primary-color);
        }

        .contact-btn {
            background: linear-gradient(135deg, var(--primary-color), var(--primary-light));
            color: white;
            padding: 13px 26px;
            border: none;
            border-radius: 25px;
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition-smooth);
            box-shadow: 0 6px 18px var(--shadow-light);
            margin-left: 22px;
        }

        .contact-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 28px var(--shadow-medium);
        }

        .hero {
            background: linear-gradient(135deg, #f8fcf8 0%, var(--accent-color) 100%);
            padding: 125px 5% 85px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            text-align: center;
            min-height: 100vh;
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            right: 0;
            width: 320px;
            height: 320px;
            background: radial-gradient(circle, var(--shadow-light), transparent 70%);
            border-radius: 50%;
            transform: translate(160px, -160px);
            animation: float 7s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translate(160px, -160px) rotate(0deg); }
            50% { transform: translate(160px, -160px) rotate(8deg) scale(1.05); }
        }

        .hero-content {
            max-width: 800px;
            margin: 0 auto;
        }

        .hero-content h1 {
            font-size: clamp(34px, 5.5vw, 60px);
            font-weight: 900;
            color: var(--primary-dark);
            margin-bottom: 22px;
            line-height: 1.15;
            opacity: 0;
            animation: fadeInUp 1s ease 0.2s forwards;
        }

        .hero-subtitle {
            font-size: clamp(21px, 3.2vw, 30px);
            color: var(--primary-color);
            margin-bottom: 30px;
            font-weight: 600;
            opacity: 0;
            animation: fadeInUp 1s ease 0.4s forwards;
        }

        .hero-description {
            font-size: 20px;
            color: var(--text-light);
            margin-bottom: 42px;
            line-height: 1.7;
            max-width: 720px;
            margin-left: auto;
            margin-right: auto;
            opacity: 0;
            animation: fadeInUp 1s ease 0.6s forwards;
        }

        .hero-buttons {
            display: flex;
            gap: 20px;
            flex-wrap: wrap;
            justify-content: center;
            opacity: 0;
            animation: fadeInUp 1s ease 0.8s forwards;
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .btn-primary {
            background: linear-gradient(135deg, var(--primary-color), var(--primary-light));
            color: white;
            padding: 16px 32px;
            border: none;
            border-radius: 50px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition-smooth);
            box-shadow: 0 12px 35px var(--shadow-light);
            text-decoration: none;
            display: inline-flex;
            align-items: center;
            gap: 9px;
        }

        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 18px 45px var(--shadow-medium);
        }

        .btn-secondary {
            background: transparent;
            color: var(--primary-color);
            padding: 16px 32px;
            border: 2px solid var(--primary-color);
            border-radius: 50px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition-smooth);
            text-decoration: none;
            display: inline-flex;
            align-items: center;
            gap: 9px;
        }

        .btn-secondary:hover {
            background: var(--primary-color);
            color: white;
            transform: translateY(-3px);
            box-shadow: 0 12px 30px var(--shadow-medium);
        }

        .professional-highlight {
            background: linear-gradient(145deg, var(--white) 0%, #f9faf9 100%);
            border-radius: 28px;
            padding: 45px 40px;
            box-shadow: 0 28px 65px var(--shadow-light), 0 8px 25px rgba(134, 164, 134, 0.08);
            text-align: center;
            max-width: 620px;
            margin: 70px auto 0;
            transition: var(--transition-smooth);
            border: 1px solid rgba(134, 164, 134, 0.12);
            position: relative;
            overflow: hidden;
            opacity: 0;
            animation: slideInUp 1s ease 1s forwards;
        }

        .professional-highlight::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 5px;
            background: linear-gradient(90deg, var(--primary-color), var(--primary-light), var(--primary-color));
        }

        .professional-highlight:hover {
            transform: translateY(-6px) scale(1.02);
            box-shadow: 0 35px 80px var(--shadow-medium), 0 15px 35px rgba(134, 164, 134, 0.15);
        }

        @keyframes slideInUp {
            from {
                opacity: 0;
                transform: translateY(50px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .highlight-content {
            position: relative;
        }

        .highlight-icon {
            font-size: 64px;
            margin-bottom: 22px;
            display: block;
            filter: drop-shadow(0 6px 18px var(--shadow-light));
            transition: var(--transition-smooth);
        }

        .highlight-content h3 {
            color: var(--primary-color);
            font-size: 17px;
            margin-bottom: 10px;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 1.2px;
        }

        .highlight-content h4 {
            color: var(--primary-dark);
            font-size: 28px;
            margin-bottom: 10px;
            font-weight: 700;
        }

        .highlight-content > p {
            color: var(--primary-color);
            font-size: 17px;
            font-weight: 500;
            margin-bottom: 28px;
        }

        .highlight-stats {
            display: flex;
            justify-content: space-around;
            margin: 28px 0;
            padding: 22px 0;
            border-top: 1px solid rgba(134, 164, 134, 0.2);
            border-bottom: 1px solid rgba(134, 164, 134, 0.2);
        }

        .highlight-stats .stat {
            text-align: center;
        }

        .highlight-stats .number {
            display: block;
            font-size: 30px;
            font-weight: 900;
            color: var(--primary-color);
            line-height: 1;
        }

        .highlight-stats .label {
            font-size: 11px;
            color: var(--text-light);
            text-transform: uppercase;
            letter-spacing: 1px;
            font-weight: 600;
            margin-top: 6px;
        }

        .credentials-mini {
            margin-top: 22px;
        }

        .credentials-mini p {
            color: var(--text-light);
            font-size: 14px;
            line-height: 1.6;
            margin-bottom: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }

        .services {
            padding: 80px 5%;
            background: white;
        }

        .section-title {
            text-align: center;
            font-size: clamp(28px, 5vw, 42px);
            font-weight: 800;
            color: var(--primary-dark);
            margin-bottom: 20px;
            position: relative;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            width: 60px;
            height: 4px;
            background: linear-gradient(90deg, var(--primary-color), var(--primary-light));
            border-radius: 2px;
            transform: translateX(-50%);
        }

        .section-subtitle {
            text-align: center;
            font-size: 20px;
            color: var(--primary-color);
            margin-bottom: 60px;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
        }

        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 40px;
            margin-top: 60px;
        }

        .service-card {
            background: linear-gradient(135deg, #f8fcf8, var(--white));
            border-radius: var(--border-radius);
            padding: 40px 30px;
            text-align: center;
            border: 2px solid rgba(134, 164, 134, 0.1);
            transition: var(--transition-smooth);
            cursor: pointer;
            position: relative;
            overflow: hidden;
            opacity: 0;
            transform: translateY(30px);
        }

        .service-card.animate {
            opacity: 1;
            transform: translateY(0);
        }

        .service-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: linear-gradient(90deg, var(--primary-color), var(--primary-light));
            transform: scaleX(0);
            transition: var(--transition-smooth);
        }

        .service-card:hover::before {
            transform: scaleX(1);
        }

        .service-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 25px 50px var(--shadow-light);
            border-color: var(--primary-color);
        }

        .service-icon {
            font-size: 48px;
            margin-bottom: 20px;
            display: block;
            filter: drop-shadow(0 5px 10px rgba(134, 164, 134, 0.3));
            transition: var(--transition-smooth);
        }

        .service-card:hover .service-icon {
            transform: scale(1.1) rotate(5deg);
        }

        .testimonials {
            padding: 80px 5%;
            background: linear-gradient(135deg, var(--accent-color), var(--white));
        }

        .testimonials-slider {
            max-width: 800px;
            margin: 0 auto;
            position: relative;
        }

        .testimonial {
            background: white;
            padding: 40px;
            border-radius: var(--border-radius);
            box-shadow: 0 20px 40px var(--shadow-light);
            text-align: center;
            margin: 0 20px;
        }

        .testimonial-text {
            font-size: 18px;
            font-style: italic;
            color: var(--text-light);
            margin-bottom: 20px;
            line-height: 1.6;
        }

        .testimonial-author {
            font-weight: 600;
            color: var(--primary-dark);
            font-size: 16px;
        }

        .testimonial-rating {
            color: #ffd700;
            font-size: 20px;
            margin-bottom: 15px;
        }

        .about {
            padding: 80px 5%;
            background: linear-gradient(135deg, #f8fcf8 0%, var(--accent-color) 100%);
        }

        .about-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 60px;
            align-items: center;
        }

        .stats {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 30px;
            margin-top: 40px;
        }

        .stat-item {
            text-align: center;
            padding: 25px;
            background: white;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
            transition: var(--transition-smooth);
            border: 2px solid transparent;
        }

        .stat-item:hover {
            transform: translateY(-5px);
            border-color: var(--primary-color);
            box-shadow: 0 15px 40px var(--shadow-light);
        }

        .stat-number {
            font-size: 36px;
            font-weight: 900;
            color: var(--primary-color);
            display: block;
        }

        .stat-label {
            color: var(--text-light);
            font-size: 14px;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-top: 8px;
        }

        .contact {
            padding: 80px 5%;
            background: var(--primary-dark);
            color: white;
        }

        .contact-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 60px;
            align-items: center;
        }

        .contact-item {
            display: flex;
            align-items: center;
            margin-bottom: 25px;
            padding: 20px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            transition: var(--transition-smooth);
            cursor: pointer;
            border: 2px solid transparent;
        }

        .contact-item:hover {
            background: rgba(255, 255, 255, 0.15);
            transform: translateX(10px);
            border-color: var(--primary-light);
        }

        .contact-form {
            background: rgba(255, 255, 255, 0.1);
            padding: 40px;
            border-radius: var(--border-radius);
            backdrop-filter: blur(10px);
            border: 2px solid rgba(255, 255, 255, 0.2);
        }

        .form-group {
            margin-bottom: 25px;
        }

        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 15px;
            border: 2px solid rgba(255, 255, 255, 0.2);
            border-radius: 10px;
            background: rgba(255, 255, 255, 0.1);
            color: white;
            font-size: 16px;
            transition: var(--transition-smooth);
        }

        .form-group input:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: var(--primary-light);
            background: rgba(255, 255, 255, 0.15);
            box-shadow: 0 0 20px rgba(155, 180, 155, 0.3);
        }

        .footer {
            background: var(--primary-dark);
            color: white;
            padding: 60px 5% 30px;
        }

        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 40px;
            margin-bottom: 40px;
        }

        .footer-section h3 {
            color: var(--primary-light);
            margin-bottom: 20px;
            font-size: 20px;
        }

        .footer-section p {
            margin-bottom: 10px;
            opacity: 0.9;
        }

        .social-links {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }

        .social-link {
            display: inline-block;
            padding: 10px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            color: white;
            text-decoration: none;
            transition: var(--transition-smooth);
        }

        .social-link:hover {
            background: var(--primary-color);
            transform: translateY(-3px);
        }

        .footer-bottom {
            border-top: 1px solid rgba(255, 255, 255, 0.2);
            padding-top: 30px;
            text-align: center;
            opacity: 0.8;
        }

        .whatsapp-float {
            position: fixed;
            bottom: 30px;
            right: 30px;
            width: 60px;
            height: 60px;
            background: #25d366;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 30px;
            text-decoration: none;
            box-shadow: 0 10px 30px rgba(37, 211, 102, 0.4);
            transition: var(--transition-smooth);
            z-index: 1000;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0% { box-shadow: 0 0 0 0 rgba(37, 211, 102, 0.7); }
            70% { box-shadow: 0 0 0 10px rgba(37, 211, 102, 0); }
            100% { box-shadow: 0 0 0 0 rgba(37, 211, 102, 0); }
        }

        .whatsapp-float:hover {
            transform: scale(1.1);
            box-shadow: 0 15px 40px rgba(37, 211, 102, 0.6);
        }

        .back-to-top {
            position: fixed;
            bottom: 30px;
            left: 30px;
            width: 50px;
            height: 50px;
            background: var(--primary-color);
            border: none;
            border-radius: 50%;
            color: white;
            font-size: 20px;
            cursor: pointer;
            transition: var(--transition-smooth);
            opacity: 0;
            visibility: hidden;
            z-index: 1000;
        }

        .back-to-top.show {
            opacity: 1;
            visibility: visible;
        }

        .back-to-top:hover {
            background: var(--primary-light);
            transform: translateY(-3px);
        }

        @media (max-width: 768px) {
            .mobile-menu-btn {
                display: block;
            }

            .nav-menu {
                position: fixed;
                top: 80px;
                left: -100%;
                width: 100%;
                height: calc(100vh - 80px);
                background: rgba(255, 255, 255, 0.98);
                backdrop-filter: blur(20px);
                flex-direction: column;
                justify-content: flex-start;
                padding: 40px 5%;
                transition: left 0.3s ease;
            }

            .nav-menu.active {
                left: 0;
            }

            .hero {
                padding: 100px 5% 60px;
                text-align: center;
            }

            .about-content,
            .contact-content {
                grid-template-columns: 1fr;
                gap: 40px;
            }

            .services-grid {
                grid-template-columns: 1fr;
            }

            .stats {
                grid-template-columns: 1fr;
            }

            .whatsapp-float {
                bottom: 20px;
                right: 20px;
                width: 50px;
                height: 50px;
                font-size: 24px;
            }

            .back-to-top {
                bottom: 80px;
                left: 20px;
                width: 40px;
                height: 40px;
                font-size: 16px;
            }
        }

        @media (prefers-reduced-motion: reduce) {
            * {
                animation-duration: 0.01ms !important;
                animation-iteration-count: 1 !important;
                transition-duration: 0.01ms !important;
            }
        }

        .sr-only {
            position: absolute;
            width: 1px;
            height: 1px;
            padding: 0;
            margin: -1px;
            overflow: hidden;
            clip: rect(0, 0, 0, 0);
            white-space: nowrap;
            border: 0;
        }

        button:focus,
        input:focus,
        textarea:focus,
        a:focus {
            outline: 2px solid var(--primary-color);
            outline-offset: 2px;
        }
    </style>
</head>
<body>
    <div class="loading-screen" id="loadingScreen">
        <div class="loader"></div>
    </div>

    <header class="header" id="header">
        <div class="logo">
            <div class="logo-icon">⚕️</div>
            Farmacia Nieto
        </div>
        <nav class="nav-menu" id="navMenu">
            <a href="#inicio" class="nav-item" data-section="inicio">Inicio</a>
            <a href="#servicios" class="nav-item" data-section="servicios">Servicios</a>
            <a href="#testimonios" class="nav-item" data-section="testimonios">Testimonios</a>
            <a href="#nosotros" class="nav-item" data-section="nosotros">Nosotros</a>
            <a href="#contacto" class="nav-item" data-section="contacto">Contacto</a>
        </nav>
        <button class="mobile-menu-btn" id="mobileMenuBtn" aria-label="Menú móvil">
            <span>☰</span>
        </button>
        <button class="contact-btn" onclick="openWhatsApp()">
            💬 WhatsApp
        </button>
    </header>

    <main>
        <section id="inicio" class="hero">
            <div class="hero-content">
                <h1>Tu camino hacia el bienestar</h1>
                <p class="hero-subtitle">Elaboración Magistral Personalizada</p>
                <p class="hero-description">
                    Bajo la dirección técnica de Patricia Victoria Nieto, farmacéutica con una larga trayectoria, 
                    te ofrecemos productos de calidad y una atención de excelencia personalizada para cuidar tu salud.
                </p>
                <div class="hero-buttons">
                    <a href="#servicios" class="btn-primary">
                        <span>🔍</span> Conocer Servicios
                    </a>
                    <a href="#" class="btn-secondary" onclick="openWhatsApp()">
                        <span>💬</span> Consultar Ahora
                    </a>
                </div>
            </div>
            
            <div class="professional-highlight">
                <div class="highlight-content">
                    <span class="highlight-icon">⚕️</span>
                    <h3>Dirección Técnica</h3>
                    <h4>Patricia Victoria Nieto</h4>
                    <p>Farmacéutica Profesional</p>
                    
                    <div class="highlight-stats">
                        <div class="stat">
                            <span class="number">28+</span>
                            <span class="label">Años</span>
                        </div>
                        <div class="stat">
                            <span class="number">1000+</span>
                            <span class="label">Pacientes</span>
                        </div>
                        <div class="stat">
                            <span class="number">8</span>
                            <span class="label">Especialidades</span>
                        </div>
                    </div>
                    
                    <div class="credentials-mini">
                        <p><span>🎓</span> Matrícula del Colegio de Farmacéuticos</p>
                        <p><span>🔬</span> Especialista en Elaboración Magistral</p>
                        <p><span>📍</span> Universidad Nacional</p>
                        <p><span>⭐</span> Desde 1996 al servicio de la comunidad</p>
                    </div>
                </div>
            </div>
        </section>

        <section id="servicios" class="services">
            <h2 class="section-title">Nuestros Servicios</h2>
            <p class="section-subtitle">
                Formulaciones personalizadas según las necesidades de cada paciente
            </p>
            
            <div class="services-grid">
                <div class="service-card">
                    <span class="service-icon">💊</span>
                    <h3>Medicina Ortomolecular</h3>
                    <p>Tratamientos personalizados basados en el equilibrio molecular óptimo para restaurar la salud natural del organismo.</p>
                </div>
                
                <div class="service-card">
                    <span class="service-icon">✨</span>
                    <h3>Dermocosmética</h3>
                    <p>Productos especializados para el cuidado de la piel, formulados específicamente para cada tipo y necesidad.</p>
                </div>
                
                <div class="service-card">
                    <span class="service-icon">🌿</span>
                    <h3>Homeopatía</h3>
                    <p>Preparaciones homeopáticas tradicionales elaboradas con los más altos estándares de calidad y pureza.</p>
                </div>
                
                <div class="service-card">
                    <span class="service-icon">🔬</span>
                    <h3>Alopatía</h3>
                    <p>Medicamentos alopáticos preparados magistralmente según prescripción médica con máxima precisión.</p>
                </div>
                
                <div class="service-card">
                    <span class="service-icon">🧘‍♀️</span>
                    <h3>Fitoterapia</h3>
                    <p>Tratamientos naturales a base de plantas medicinales, respaldados por la tradición y la ciencia moderna.</p>
                </div>
                
                <div class="service-card">
                    <span class="service-icon">🌸</span>
                    <h3>Florales</h3>
                    <p>Esencias florales de Bach y otros sistemas para el equilibrio emocional y el bienestar integral.</p>
                </div>
                
                <div class="service-card">
                    <span class="service-icon">🦠</span>
                    <h3>Probióticos</h3>
                    <p>Formulaciones probióticas específicas para restaurar y mantener el equilibrio de la flora intestinal.</p>
                </div>
                
                <div class="service-card">
                    <span class="service-icon">🧬</span>
                    <h3>Hormonas Bioidénticas</h3>
                    <p>Terapias hormonales personalizadas con hormonas bioidénticas para el equilibrio hormonal natural.</p>
                </div>
            </div>
        </section>

        <section id="testimonios" class="testimonials">
            <h2 class="section-title">Lo que dicen nuestros pacientes</h2>
            <p class="section-subtitle">Testimonios reales de personas que confían en nosotros</p>
            
            <div class="testimonials-slider">
                <div class="testimonial" id="testimonial1">
                    <div class="testimonial-rating">⭐⭐⭐⭐⭐</div>
                    <p class="testimonial-text">
                        "La atención personalizada de Patricia es excepcional. Los medicamentos magistrales me han ayudado enormemente con mi tratamiento."
                    </p>
                    <p class="testimonial-author">- María González</p>
                </div>
                
                <div class="testimonial" id="testimonial2" style="display: none;">
                    <div class="testimonial-rating">⭐⭐⭐⭐⭐</div>
                    <p class="testimonial-text">
                        "Desde hace años confío en Farmacia Nieto para mis medicamentos homeopáticos. Siempre con la mejor calidad y asesoramiento."
                    </p>
                    <p class="testimonial-author">- Carlos Rodríguez</p>
                </div>
                
                <div class="testimonial" id="testimonial3" style="display: none;">
                    <div class="testimonial-rating">⭐⭐⭐⭐⭐</div>
                    <p class="testimonial-text">
                        "Los productos dermatológicos personalizados han transformado el cuidado de mi piel. Excelente servicio y profesionalismo."
                    </p>
                    <p class="testimonial-author">- Ana Martínez</p>
                </div>
            </div>
            
            <div style="text-align: center; margin-top: 30px;">
                <button class="btn-secondary" onclick="prevTestimonial()">← Anterior</button>
                <button class="btn-secondary" onclick="nextTestimonial()" style="margin-left: 20px;">Siguiente →</button>
            </div>
        </section>

        <section id="nosotros" class="about">
            <div class="about-content">
                <div class="about-text">
                    <h2>Acerca de Nosotros</h2>
                    <div class="director-info">
                        <h3>Dirección Técnica: Patricia Victoria Nieto</h3>
                        <p class="director-credentials">
                            <strong>Farmacéutica Profesional</strong> | Matrícula del Colegio de Farmacéuticos<br>
                            <strong>Especialista en Elaboración Magistral</strong> | Universidad Nacional<br>
                            <strong>28 años de experiencia</strong> | Desde 1996 al servicio de la comunidad
                        </p>
                    </div>
                    <p>
                        Desde 1996, nos dedicamos a brindar soluciones farmacéuticas personalizadas. Bajo la dirección 
                        técnica de Patricia Victoria Nieto, contamos con un equipo altamente capacitado que trabaja 
                        incansablemente para ofrecer productos de calidad y una atención de excelencia.
                    </p>
                    <p>
                        Nuestro personal amable y comprometido está listo para brindarte asesoramiento personalizado 
                        y recomendaciones confiables, siempre pensando en cuidar tu salud y bienestar.
                    </p>
                    
                    <div class="stats">
                        <div class="stat-item">
                            <span class="stat-number" data-count="28">0</span>
                            <span class="stat-label">Años de Experiencia</span>
                        </div>
                        <div class="stat-item">
                            <span class="stat-number" data-count="1000">0</span>
                            <span class="stat-label">Pacientes Satisfechos</span>
                        </div>
                        <div class="stat-item">
                            <span class="stat-number" data-count="8">0</span>
                            <span class="stat-label">Especialidades</span>
                        </div>
                        <div class="stat-item">
                            <span class="stat-number" data-count="365">0</span>
                            <span class="stat-label">Días al Año</span>
                        </div>
                    </div>
                </div>
                
                <div class="about-visual">
                    <div class="experience-badge">
                        <h3>Desde 1996</h3>
                        <p>Cuidando de ti de manera personalizada</p>
                        <div style="margin-top: 20px;">
                            <span style="font-size: 60px;">🏆</span>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section id="contacto" class="contact">
            <div class="contact-content">
                <div class="contact-info">
                    <h2>Contactanos</h2>
                    <p style="margin-bottom: 40px; font-size: 18px; opacity: 0.9;">
                        Para más asesoramiento y consultas, comunicate con nosotros. 
                        ¡Cuidamos de ti de manera personalizada!
                    </p>
                    
                    <div class="contact-item" onclick="openWhatsApp()">
                        <span class="contact-icon">📱</span>
                        <div class="contact-details">
                            <h4>WhatsApp</h4>
                            <p>(+54) 291432-7031</p>
                        </div>
                    </div>
                    
                    <div class="contact-item" onclick="window.open('mailto:farmacia.nieto@hotmail.com', '_blank')">
                        <span class="contact-icon">✉️</span>
                        <div class="contact-details">
                            <h4>Email</h4>
                            <p>farmacia.nieto@hotmail.com</p>
                        </div>
                    </div>
                    
                    <div class="contact-item">
                        <span class="contact-icon">📍</span>
                        <div class="contact-details">
                            <h4>Ubicación</h4>
                            <p>Bahía Blanca, Buenos Aires, Argentina</p>
                        </div>
                    </div>
                    
                    <div class="contact-item" onclick="window.open('https://instagram.com/farmacia.nieto', '_blank')">
                        <span class="contact-icon">📷</span>
                        <div class="contact-details">
                            <h4>Instagram</h4>
                            <p>@farmacia.nieto</p>
                        </div>
                    </div>
                    
                    <div class="contact-item">
                        <span class="contact-icon">⏰</span>
                        <div class="contact-details">
                            <h4>Horarios</h4>
                            <p>Lun-Vie: 8:00-20:00<br>Sáb: 8:00-13:00</p>
                        </div>
                    </div>
                </div>
                
                <div class="contact-form">
                    <h3 style="margin-bottom: 30px; color: var(--primary-light);">Envíanos tu consulta</h3>
                    <form id="contactForm">
                        <div class="form-group">
                            <label for="nombre">Nombre Completo *</label>
                            <input type="text" id="nombre" name="nombre" placeholder="Tu nombre" required>
                        </div>
                        
                        <div class="form-group">
                            <label for="email">Email *</label>
                            <input type="email" id="email" name="email" placeholder="tu@email.com" required>
                        </div>
                        
                        <div class="form-group">
                            <label for="telefono">Teléfono</label>
                            <input type="tel" id="telefono" name="telefono" placeholder="Tu teléfono">
                        </div>
                        
                        <div class="form-group">
                            <label for="servicio">Servicio de interés</label>
                            <select id="servicio" name="servicio" style="width: 100%; padding: 15px; border: 2px solid rgba(255, 255, 255, 0.2); border-radius: 10px; background: rgba(255, 255, 255, 0.1); color: white; font-size: 16px;">
                                <option value="">Selecciona un servicio</option>
                                <option value="medicina-ortomolecular">Medicina Ortomolecular</option>
                                <option value="dermocosmetica">Dermocosmética</option>
                                <option value="homeopatia">Homeopatía</option>
                                <option value="alopatia">Alopatía</option>
                                <option value="fitoterapia">Fitoterapia</option>
                                <option value="florales">Florales</option>
                                <option value="probioticos">Probióticos</option>
                                <option value="hormonas">Hormonas Bioidénticas</option>
                                <option value="consulta-general">Consulta General</option>
                            </select>
                        </div>
                        
                        <div class="form-group">
                            <label for="consulta">Consulta *</label>
                            <textarea id="consulta" name="consulta" rows="4" placeholder="¿En qué podemos ayudarte?" required></textarea>
                        </div>
                        
                        <button type="submit" class="btn-primary" style="width: 100%;">
                            <span>📤</span> Enviar Consulta
                        </button>
                    </form>
                </div>
            </div>
        </section>
    </main>

    <footer class="footer">
        <div class="footer-content">
            <div class="footer-section">
                <h3>Farmacia Nieto</h3>
                <p>Tu camino hacia el bienestar desde 1996. Elaboración magistral personalizada con la más alta calidad.</p>
                <div class="social-links">
                    <a href="#" class="social-link" onclick="openWhatsApp()" aria-label="WhatsApp">📱</a>
                    <a href="mailto:farmacia.nieto@hotmail.com" class="social-link" aria-label="Email">✉️</a>
                    <a href="https://instagram.com/farmacia.nieto" class="social-link" target="_blank" aria-label="Instagram">📷</a>
                </div>
            </div>
            
            <div class="footer-section">
                <h3>Servicios</h3>
                <p>Medicina Ortomolecular</p>
                <p>Dermocosmética</p>
                <p>Homeopatía</p>
                <p>Fitoterapia</p>
                <p>Probióticos</p>
                <p>Hormonas Bioidénticas</p>
            </div>
            
            <div class="footer-section">
                <h3>Contacto</h3>
                <p>📱 (+54) 291432-7031</p>
                <p>✉️ farmacia.nieto@hotmail.com</p>
                <p>📷 @farmacia.nieto</p>
                <p>📍 Bahía Blanca, Buenos Aires</p>
                <p>⏰ Lun-Vie: 8:00-20:00 | Sáb: 8:00-13:00</p>
            </div>
            
            <div class="footer-section">
                <h3>Información</h3>
                <p>Directora Técnica: Patricia Victoria Nieto</p>
                <p>Matrícula Profesional</p>
                <p>28+ años de experiencia</p>
                <p>Elaboración Magistral</p>
                <p>Atención Personalizada</p>
            </div>
        </div>
        
        <div class="footer-bottom">
            <p>&copy; 2024 Farmacia Nieto. Todos los derechos reservados. | Diseñado con ❤️ para tu bienestar</p>
        </div>
    </footer>

    <a href="#" class="whatsapp-float" onclick="openWhatsApp()" aria-label="Contactar por WhatsApp">
        💬
    </a>
    
    <button class="back-to-top" id="backToTop" onclick="scrollToTop()" aria-label="Volver arriba">
        ↑
    </button>

    <script>
        let currentTestimonial = 0;
        const testimonials = ['testimonial1', 'testimonial2', 'testimonial3'];
        
        window.addEventListener('load', function() {
            setTimeout(() => {
                document.getElementById('loadingScreen').classList.add('hidden');
            }, 1000);
        });

        document.getElementById('mobileMenuBtn').addEventListener('click', function() {
            const navMenu = document.getElementById('navMenu');
            navMenu.classList.toggle('active');
            this.innerHTML = navMenu.classList.contains('active') ? '✕' : '☰';
        });

        window.addEventListener('scroll', function() {
            const header = document.getElementById('header');
            const backToTop = document.getElementById('backToTop');
            
            if (window.scrollY > 100) {
                header.classList.add('scrolled');
                backToTop.classList.add('show');
            } else {
                header.classList.remove('scrolled');
                backToTop.classList.remove('show');
            }
        });

        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                    
                    const navMenu = document.getElementById('navMenu');
                    const menuBtn = document.getElementById('mobileMenuBtn');
                    navMenu.classList.remove('active');
                    menuBtn.innerHTML = '☰';
                }
            });
        });

        window.addEventListener('scroll', function() {
            const sections = document.querySelectorAll('section[id]');
            const navItems = document.querySelectorAll('.nav-item');
            
            let current = '';
            sections.forEach(section => {
                const sectionTop = section.offsetTop;
                const sectionHeight = section.clientHeight;
                if (window.scrollY >= sectionTop - 200) {
                    current = section.getAttribute('id');
                }
            });
            
            navItems.forEach(item => {
                item.classList.remove('active');
                if (item.getAttribute('data-section') === current) {
                    item.classList.add('active');
                }
            });
        });

        function showTestimonial(index) {
            testimonials.forEach((id, i) => {
                const testimonial = document.getElementById(id);
                testimonial.style.display = i === index ? 'block' : 'none';
                testimonial.style.opacity = i === index ? '1' : '0';
            });
        }

        function nextTestimonial() {
            currentTestimonial = (currentTestimonial + 1) % testimonials.length;
            showTestimonial(currentTestimonial);
        }

        function prevTestimonial() {
            currentTestimonial = currentTestimonial === 0 ? testimonials.length - 1 : currentTestimonial - 1;
            showTestimonial(currentTestimonial);
        }

        setInterval(nextTestimonial, 5000);

        function animateCounters() {
            const counters = document.querySelectorAll('.stat-number');
            counters.forEach(counter => {
                const target = parseInt(counter.getAttribute('data-count'));
                const increment = target / 50;
                let current = 0;
                
                const timer = setInterval(() => {
                    current += increment;
                    if (current >= target) {
                        current = target;
                        clearInterval(timer);
                    }
                    counter.textContent = Math.floor(current) + (target === 1000 ? '+' : target === 365 ? '' : '+');
                }, 40);
            });
        }

        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    if (entry.target.classList.contains('service-card')) {
                        entry.target.classList.add('animate');
                    }
                    if (entry.target.classList.contains('stat-item')) {
                        animateCounters();
                    }
                }
            });
        }, observerOptions);

        document.querySelectorAll('.service-card, .stat-item').forEach(el => {
            observer.observe(el);
        });

        function openWhatsApp() {
            const message = "Hola, me gustaría obtener información sobre sus servicios farmacéuticos. ¡Gracias!";
            const whatsappURL = `https://wa.me/5492914327031?text=${encodeURIComponent(message)}`;
            window.open(whatsappURL, '_blank');
        }

        document.getElementById('contactForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const formData = new FormData(this);
            const nombre = formData.get('nombre');
            const email = formData.get('email');
            const telefono = formData.get('telefono') || 'No proporcionado';
            const servicio = formData.get('servicio') || 'Consulta general';
            const consulta = formData.get('consulta');
            
            const mensaje = `¡Hola! Soy ${nombre}.

📧 Email: ${email}
📞 Teléfono: ${telefono}
🔍 Servicio de interés: ${servicio}

📝 Consulta: ${consulta}

¡Espero su respuesta! Gracias.`;
            
            const whatsappURL = `https://wa.me/5492914327031?text=${encodeURIComponent(mensaje)}`;
            window.open(whatsappURL, '_blank');
            
            alert('¡Gracias por tu consulta! Te redirigimos a WhatsApp para una respuesta rápida.');
            this.reset();
        });

        function scrollToTop() {
            window.scrollTo({
                top: 0,
                behavior: 'smooth'
            });
        }

        document.querySelectorAll('.service-card').forEach(card => {
            card.addEventListener('mouseenter', function() {
                this.style.transform = 'translateY(-10px) scale(1.02)';
            });
            
            card.addEventListener('mouseleave', function() {
                this.style.transform = 'translateY(0) scale(1)';
            });
        });

        document.addEventListener('keydown', function(e) {
            if (e.key === 'Escape') {
                const navMenu = document.getElementById('navMenu');
                const menuBtn = document.getElementById('mobileMenuBtn');
                navMenu.classList.remove('active');
                menuBtn.innerHTML = '☰';
            }
        });

        document.addEventListener('DOMContentLoaded', function() {
            console.log('⚕️ Farmacia Nieto - Sitio web cargado correctamente');
            console.log('📱 WhatsApp: +54 291432-7031');
            console.log('✉️ Email: farmacia.nieto@hotmail.com');
            console.log('📍 Ubicación: Bahía Blanca, Buenos Aires, Argentina');
        });
    </script>
</body>
</html>
