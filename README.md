<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SmartPetAI - Бесплатный ветеринарный ИИ-помощник</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #0071e3;
            --primary-light: #2997ff;
            --white: #ffffff;
            --black: #1d1d1f;
            --gray: #86868b;
            --gray-light: #f5f5f7;
            --green: #34c759;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
            color: var(--black);
            line-height: 1.5;
            overflow-x: hidden;
            background-color: var(--white);
        }
        
        .container {
            width: 100%;
            max-width: 1440px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        /* Header */
        header {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            z-index: 100;
            background-color: rgba(255, 255, 255, 0.8);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            padding: 15px 0;
            transition: all 0.3s ease;
        }
        
        header.scrolled {
            padding: 10px 0;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
        }
        
        .header-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            font-size: 24px;
            font-weight: 600;
            color: var(--primary);
            text-decoration: none;
            display: flex;
            align-items: center;
        }
        
        .logo i {
            margin-right: 10px;
        }
        
        nav ul {
            display: flex;
            list-style: none;
        }
        
        nav ul li {
            margin-left: 30px;
        }
        
        nav ul li a {
            text-decoration: none;
            color: var(--black);
            font-weight: 500;
            font-size: 15px;
            transition: color 0.3s;
        }
        
        nav ul li a:hover {
            color: var(--primary);
        }
        
        .mobile-menu-btn {
            display: none;
            background: none;
            border: none;
            font-size: 24px;
            cursor: pointer;
        }
        
        /* Hero Section */
        .hero {
            height: 100vh;
            min-height: 700px;
            display: flex;
            align-items: center;
            position: relative;
            overflow: hidden;
            background: linear-gradient(to bottom, #f5f5f7 0%, #ffffff 100%);
            padding-top: 80px;
        }
        
        .hero-content {
            width: 100%;
            max-width: 600px;
            z-index: 2;
        }
        
        .hero h1 {
            font-size: 56px;
            font-weight: 700;
            margin-bottom: 20px;
            line-height: 1.1;
        }
        
        .hero p {
            font-size: 24px;
            color: var(--gray);
            margin-bottom: 30px;
        }
        
        .cta-button {
            display: inline-block;
            background-color: var(--primary);
            color: var(--white);
            padding: 12px 30px;
            border-radius: 30px;
            text-decoration: none;
            font-weight: 500;
            font-size: 18px;
            transition: all 0.3s;
            border: none;
            cursor: pointer;
        }
        
        .cta-button:hover {
            background-color: var(--primary-light);
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0, 113, 227, 0.3);
        }
        
        .hero-image {
            position: absolute;
            right: -100px;
            bottom: 0;
            height: 90%;
            z-index: 1;
            transform: translateY(50px);
            opacity: 0;
            transition: all 1s ease;
        }
        
        .hero-image.animate {
            transform: translateY(0);
            opacity: 1;
        }
        
        /* Features Section */
        .features {
            padding: 120px 0;
            background-color: var(--white);
        }
        
        .section-title {
            text-align: center;
            font-size: 40px;
            font-weight: 700;
            margin-bottom: 80px;
        }
        
        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 40px;
        }
        
        .feature-card {
            text-align: center;
            padding: 40px 30px;
            border-radius: 20px;
            background-color: var(--gray-light);
            transition: all 0.3s ease;
            transform: translateY(20px);
            opacity: 0;
        }
        
        .feature-card.animate {
            transform: translateY(0);
            opacity: 1;
        }
        
        .feature-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.05);
        }
        
        .feature-icon {
            font-size: 50px;
            color: var(--primary);
            margin-bottom: 25px;
            display: inline-block;
        }
        
        .feature-card h3 {
            font-size: 22px;
            margin-bottom: 15px;
            font-weight: 600;
        }
        
        .feature-card p {
            color: var(--gray);
            font-size: 16px;
        }
        
        /* How It Works */
        .how-it-works {
            padding: 120px 0;
            background-color: var(--gray-light);
            position: relative;
            overflow: hidden;
        }
        
        .steps {
            display: flex;
            flex-direction: column;
            gap: 60px;
            position: relative;
            z-index: 2;
        }
        
        .step {
            display: flex;
            align-items: center;
            gap: 50px;
            opacity: 0;
            transform: translateX(-50px);
            transition: all 0.8s ease;
        }
        
        .step.animate {
            opacity: 1;
            transform: translateX(0);
        }
        
        .step:nth-child(even) {
            flex-direction: row-reverse;
            transform: translateX(50px);
        }
        
        .step:nth-child(even).animate {
            transform: translateX(0);
        }
        
        .step-content {
            flex: 1;
        }
        
        .step-number {
            font-size: 24px;
            font-weight: 600;
            color: var(--primary);
            margin-bottom: 15px;
        }
        
        .step-title {
            font-size: 28px;
            font-weight: 600;
            margin-bottom: 20px;
        }
        
        .step-description {
            color: var(--gray);
            font-size: 18px;
            line-height: 1.6;
        }
        
        .step-image {
            flex: 1;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
        }
        
        .step-image img {
            width: 100%;
            height: auto;
            display: block;
        }
        
        /* Testimonials */
        .testimonials {
            padding: 120px 0;
            background-color: var(--white);
        }
        
        .testimonials-slider {
            max-width: 800px;
            margin: 0 auto;
            position: relative;
        }
        
        .testimonial {
            text-align: center;
            padding: 0 20px;
            opacity: 0;
            transition: all 0.5s ease;
        }
        
        .testimonial.active {
            opacity: 1;
        }
        
        .testimonial-text {
            font-size: 24px;
            font-weight: 500;
            margin-bottom: 30px;
            line-height: 1.6;
        }
        
        .testimonial-author {
            font-weight: 600;
            margin-bottom: 5px;
        }
        
        .testimonial-role {
            color: var(--gray);
            font-size: 14px;
        }
        
        .testimonial-avatar {
            width: 80px;
            height: 80px;
            border-radius: 50%;
            object-fit: cover;
            margin: 0 auto 20px;
            border: 3px solid var(--primary);
        }
        
        .slider-controls {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-top: 40px;
        }
        
        .slider-dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background-color: #d9d9d9;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .slider-dot.active {
            background-color: var(--primary);
            transform: scale(1.2);
        }
        
        /* FAQ */
        .faq {
            padding: 120px 0;
            background-color: var(--gray-light);
        }
        
        .faq-container {
            max-width: 800px;
            margin: 0 auto;
        }
        
        .faq-item {
            margin-bottom: 15px;
            border-radius: 10px;
            overflow: hidden;
            background-color: var(--white);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            opacity: 0;
            transform: translateY(20px);
            transition: all 0.5s ease;
        }
        
        .faq-item.animate {
            opacity: 1;
            transform: translateY(0);
        }
        
        .faq-question {
            padding: 20px 25px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            cursor: pointer;
            font-weight: 600;
            font-size: 18px;
        }
        
        .faq-question i {
            transition: transform 0.3s;
        }
        
        .faq-item.active .faq-question i {
            transform: rotate(180deg);
        }
        
        .faq-answer {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.3s ease;
            padding: 0 25px;
        }
        
        .faq-item.active .faq-answer {
            max-height: 300px;
            padding: 0 25px 20px;
        }
        
        /* CTA Section */
        .cta-section {
            padding: 120px 0;
            text-align: center;
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-light) 100%);
            color: var(--white);
        }
        
        .cta-section h2 {
            font-size: 40px;
            font-weight: 700;
            margin-bottom: 20px;
        }
        
        .cta-section p {
            font-size: 20px;
            margin-bottom: 40px;
            max-width: 700px;
            margin-left: auto;
            margin-right: auto;
            opacity: 0.9;
        }
        
        .cta-button.white {
            background-color: var(--white);
            color: var(--primary);
        }
        
        .cta-button.white:hover {
            background-color: rgba(255, 255, 255, 0.9);
        }
        
        /* Footer */
        footer {
            background-color: var(--black);
            color: var(--white);
            padding: 60px 0 30px;
        }
        
        .footer-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 40px;
            margin-bottom: 50px;
        }
        
        .footer-logo {
            font-size: 24px;
            font-weight: 600;
            color: var(--white);
            margin-bottom: 20px;
            display: inline-block;
        }
        
        .footer-about p {
            opacity: 0.7;
            margin-bottom: 20px;
        }
        
        .social-links {
            display: flex;
            gap: 15px;
        }
        
        .social-links a {
            color: var(--white);
            font-size: 20px;
            opacity: 0.7;
            transition: opacity 0.3s;
        }
        
        .social-links a:hover {
            opacity: 1;
        }
        
        .footer-links h3 {
            font-size: 18px;
            font-weight: 600;
            margin-bottom: 20px;
        }
        
        .footer-links ul {
            list-style: none;
        }
        
        .footer-links ul li {
            margin-bottom: 10px;
        }
        
        .footer-links ul li a {
            color: var(--white);
            opacity: 0.7;
            text-decoration: none;
            transition: opacity 0.3s;
        }
        
        .footer-links ul li a:hover {
            opacity: 1;
        }
        
        .footer-bottom {
            text-align: center;
            padding-top: 30px;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            opacity: 0.7;
            font-size: 14px;
        }
        
        /* Animations */
        @keyframes float {
            0%, 100% {
                transform: translateY(0);
            }
            50% {
                transform: translateY(-10px);
            }
        }
        
        .floating {
            animation: float 3s ease-in-out infinite;
        }
        
        /* Parallax */
        .parallax {
            background-attachment: fixed;
            background-position: center;
            background-repeat: no-repeat;
            background-size: cover;
        }
        
        /* Responsive */
        @media (max-width: 1024px) {
            .hero h1 {
                font-size: 48px;
            }
            
            .hero p {
                font-size: 20px;
            }
            
            .hero-image {
                right: -150px;
            }
            
            .step {
                flex-direction: column;
                gap: 30px;
            }
            
            .step:nth-child(even) {
                flex-direction: column;
            }
            
            .step-image {
                width: 100%;
            }
        }
        
        @media (max-width: 768px) {
            nav ul {
                display: none;
            }
            
            .mobile-menu-btn {
                display: block;
            }
            
            .hero {
                text-align: center;
                padding-top: 100px;
            }
            
            .hero-content {
                margin: 0 auto;
            }
            
            .hero-image {
                position: relative;
                right: auto;
                margin: 40px auto 0;
                height: auto;
                width: 100%;
                max-width: 500px;
            }
            
            .section-title {
                font-size: 32px;
                margin-bottom: 50px;
            }
            
            .features, .how-it-works, .testimonials, .faq, .cta-section {
                padding: 80px 0;
            }
            
            .step-title {
                font-size: 24px;
            }
            
            .step-description {
                font-size: 16px;
            }
            
            .testimonial-text {
                font-size: 20px;
            }
            
            .cta-section h2 {
                font-size: 32px;
            }
            
            .cta-section p {
                font-size: 18px;
            }
        }
        
        @media (max-width: 480px) {
            .hero h1 {
                font-size: 36px;
            }
            
            .hero p {
                font-size: 18px;
            }
            
            .features-grid {
                grid-template-columns: 1fr;
            }
            
            .section-title {
                font-size: 28px;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header id="header">
        <div class="container header-container">
            <a href="#" class="logo">
                <i class="fas fa-paw"></i> SmartPetAI
            </a>
            <nav>
                <ul>
                    <li><a href="#features">Возможности</a></li>
                    <li><a href="#how-it-works">Как это работает</a></li>
                    <li><a href="#testimonials">Отзывы</a></li>
                    <li><a href="#faq">Вопросы</a></li>
                </ul>
            </nav>
            <button class="mobile-menu-btn">
                <i class="fas fa-bars"></i>
            </button>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="hero">
        <div class="container">
            <div class="hero-content">
                <h1>Ветеринарная помощь в один клик</h1>
                <p>Бесплатный ИИ-ассистент для здоровья вашего питомца. Круглосуточная поддержка без очередей и стресса.</p>
                <a href="#cta" class="cta-button">Попробовать бесплатно</a>
            </div>
            <img src="https://images.unsplash.com/photo-1586671267731-da2cf3ceeb80?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=800&q=80" alt="Довольная собака" class="hero-image">
        </div>
    </section>

    <!-- Features Section -->
    <section class="features" id="features">
        <div class="container">
            <h2 class="section-title">Почему SmartPetAI?</h2>
            <div class="features-grid">
                <div class="feature-card">
                    <div class="feature-icon floating">
                        <i class="fas fa-wallet"></i>
                    </div>
                    <h3>Бесплатно</h3>
                    <p>Полноценные консультации без скрытых платежей и подписок. Экономьте на визитах к ветеринару.</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon floating" style="animation-delay: 0.2s;">
                        <i class="fas fa-clock"></i>
                    </div>
                    <h3>24/7 Доступ</h3>
                    <p>Помощь в любое время дня и ночи. Не нужно ждать открытия клиники в экстренной ситуации.</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon floating" style="animation-delay: 0.4s;">
                        <i class="fas fa-brain"></i>
                    </div>
                    <h3>Искусственный интеллект</h3>
                    <p>Точные рекомендации на основе тысяч успешных диагнозов. Постоянное обучение и улучшение.</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon floating" style="animation-delay: 0.6s;">
                        <i class="fas fa-dog"></i>
                    </div>
                    <h3>Для всех питомцев</h3>
                    <p>Собаки, кошки, птицы, грызуны - наш бот поможет с любыми домашними животными.</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon floating" style="animation-delay: 0.8s;">
                        <i class="fas fa-heartbeat"></i>
                    </div>
                    <h3>Экстренные случаи</h3>
                    <p>Мгновенная оценка срочности ситуации и четкие инструкции при угрозе жизни питомца.</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon floating" style="animation-delay: 1s;">
                        <i class="fas fa-history"></i>
                    </div>
                    <h3>История здоровья</h3>
                    <p>Хранение всех консультаций и рекомендаций в одном месте для отслеживания динамики.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- How It Works -->
    <section class="how-it-works" id="how-it-works">
        <div class="container">
            <h2 class="section-title">Как это работает?</h2>
            <div class="steps">
                <div class="step">
                    <div class="step-content">
                        <div class="step-number">Шаг 1</div>
                        <h3 class="step-title">Опишите симптомы</h3>
                        <p class="step-description">Просто расскажите, что беспокоит вашего питомца. Наш ИИ задаст уточняющие вопросы, чтобы лучше понять ситуацию.</p>
                    </div>
                    <div class="step-image">
                        <img src="https://images.unsplash.com/photo-1583337130417-3346a1be7dee?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=800&q=80" alt="Человек с собакой">
                    </div>
                </div>
                <div class="step">
                    <div class="step-content">
                        <div class="step-number">Шаг 2</div>
                        <h3 class="step-title">Получите анализ</h3>
                        <p class="step-description">ИИ обработает информацию, сравнит с тысячами похожих случаев и даст предварительный диагноз с точностью до 92%.</p>
                    </div>
                    <div class="step-image">
                        <img src="https://images.unsplash.com/photo-1635433868510-5a0f03a1ec5b?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=800&q=80" alt="Ноутбук с анализом данных">
                    </div>
                </div>
                <div class="step">
                    <div class="step-content">
                        <div class="step-number">Шаг 3</div>
                        <h3 class="step-title">Получите рекомендации</h3>
                        <p class="step-description">Вы получите четкий план действий: домашнее лечение, срочный визит к ветеринару или экстренные меры.</p>
                    </div>
                    <div class="step-image">
                        <img src="https://images.unsplash.com/photo-1601758003122-53c40e686a19?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=800&q=80" alt="Ветеринар с собакой">
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Testimonials -->
    <section class="testimonials" id="testimonials">
        <div class="container">
            <h2 class="section-title">Отзывы владельцев</h2>
            <div class="testimonials-slider">
                <div class="testimonial active">
                    <img src="https://images.unsplash.com/photo-1438761681033-6461ffad8d80?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=800&q=80" alt="Анна К." class="testimonial-avatar">
                    <p class="testimonial-text">"SmartPetAI спас моего кота ночью, когда все клиники были закрыты. ИИ точно определил отравление и дал инструкции по первой помощи до утра."</p>
                    <div class="testimonial-author">Анна К.</div>
                    <div class="testimonial-role">владелица кота Барсика</div>
                </div>
                <div class="testimonial">
                    <img src="https://images.unsplash.com/photo-1544005313-94ddf0286df2?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=800&q=80" alt="Дмитрий С." class="testimonial-avatar">
                    <p class="testimonial-text">"Благодаря боту мы избежали ненужного визита к ветеринару. Оказалось, что симптомы были неопасными, и ИИ посоветовал просто наблюдать. Сэкономили время и деньги!"</p>
                    <div class="testimonial-author">Дмитрий С.</div>
                    <div class="testimonial-role">владелец собаки Рекса</div>
                </div>
                <div class="testimonial">
                    <img src="https://images.unsplash.com/photo-1554151228-14d9def656e4?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=800&q=80" alt="Елена М." class="testimonial-avatar">
                    <p class="testimonial-text">"Как владелица трех кошек, я постоянно пользуюсь SmartPetAI. Это как личный ветеринар в кармане. Особенно удобно вести историю болезней для каждого питомца."</p>
                    <div class="testimonial-author">Елена М.</div>
                    <div class="testimonial-role">владелица трех кошек</div>
                </div>
                <div class="slider-controls">
                    <div class="slider-dot active" data-slide="0"></div>
                    <div class="slider-dot" data-slide="1"></div>
                    <div class="slider-dot" data-slide="2"></div>
                </div>
            </div>
        </div>
    </section>

    <!-- FAQ -->
    <section class="faq" id="faq">
        <div class="container">
            <h2 class="section-title">Частые вопросы</h2>
            <div class="faq-container">
                <div class="faq-item">
                    <div class="faq-question">
                        <span>Насколько точны диагнозы SmartPetAI?</span>
                        <i class="fas fa-chevron-down"></i>
                    </div>
                    <div class="faq-answer">
                        <p>Точность предварительных диагнозов нашего ИИ составляет 92% для распространенных заболеваний и 85% для редких случаев. Однако мы всегда рекомендуем подтверждать серьезные диагнозы у ветеринара.</p>
                    </div>
                </div>
                <div class="faq-item">
                    <div class="faq-question">
                        <span>Как часто обновляются знания бота?</span>
                        <i class="fas fa-chevron-down"></i>
                    </div>
                    <div class="faq-answer">
                        <p>Наша база знаний обновляется ежедневно на основе последних ветеринарных исследований и реальных случаев. ИИ постоянно обучается на анонимизированных данных консультаций.</p>
                    </div>
                </div>
                <div class="faq-item">
                    <div class="faq-question">
                        <span>Может ли бот заменить ветеринара?</span>
                        <i class="fas fa-chevron-down"></i>
                    </div>
                    <div class="faq-answer">
                        <p>SmartPetAI не заменяет очного визита к ветеринару в серьезных случаях, но помогает определить срочность ситуации, оказать первую помощь и сэкономить время на первичной диагностике.</p>
                    </div>
                </div>
                <div class="faq-item">
                    <div class="faq-question">
                        <span>Как бот обрабатывает мои данные?</span>
                        <i class="fas fa-chevron-down"></i>
                    </div>
                    <div class="faq-answer">
                        <p>Все данные анонимизируются и хранятся в зашифрованном виде. Мы не передаем информацию третьим лицам и используем ее только для улучшения сервиса.</p>
                    </div>
                </div>
                <div class="faq-item">
                    <div class="faq-question">
                        <span>Почему сервис бесплатный?</span>
                        <i class="fas fa-chevron-down"></i>
                    </div>
                    <div class="faq-answer">
                        <p>Мы верим, что ветеринарная помощь должна быть доступна всем. Проект поддерживается за счет благотворительных взносов и партнерских программ с ветеринарными клиниками.</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- CTA Section -->
    <section class="cta-section" id="cta">
        <div class="container">
            <h2>Позаботьтесь о своем питомце прямо сейчас</h2>
            <p>SmartPetAI уже помог тысячам владельцев животных. Попробуйте бесплатно и вы!</p>
            <a href="#" class="cta-button white">Начать консультацию</a>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-container">
                <div class="footer-about">
                    <a href="#" class="footer-logo">
                        <i class="fas fa-paw"></i> SmartPetAI
                    </a>
                    <p>Бесплатный ИИ-ассистент для здоровья ваших питомцев. Доступно. Профессионально. Честно.</p>
                    <div class="social-links">
                        <a href="#"><i class="fab fa-telegram"></i></a>
                        <a href="#"><i class="fab fa-vk"></i></a>
                        <a href="#"><i class="fab fa-whatsapp"></i></a>
                        <a href="#"><i class="fab fa-youtube"></i></a>
                    </div>
                </div>
                <div class="footer-links">
                    <h3>SmartPetAI</h3>
                    <ul>
                        <li><a href="#features">Возможности</a></li>
                        <li><a href="#how-it-works">Как это работает</a></li>
                        <li><a href="#testimonials">Отзывы</a></li>
                        <li><a href="#faq">Вопросы</a></li>
                    </ul>
                </div>
                <div class="footer-links">
                    <h3>Поддержка</h3>
                    <ul>
                        <li><a href="#">Помощь</a></li>
                        <li><a href="#">Контакты</a></li>
                        <li><a href="#">Политика конфиденциальности</a></li>
                        <li><a href="#">Условия использования</a></li>
                    </ul>
                </div>
                <div class="footer-links">
                    <h3>Для ветеринаров</h3>
                    <ul>
                        <li><a href="#">Партнерская программа</a></li>
                        <li><a href="#">Для клиник</a></li>
                        <li><a href="#">Верификация</a></li>
                        <li><a href="#">Сотрудничество</a></li>
                    </ul>
                </div>
            </div>
            <div class="footer-bottom">
                <p>© 2023 SmartPetAI. Все права защищены.</p>
            </div>
        </div>
    </footer>

    <script>
        // Mobile Menu
        const mobileMenuBtn = document.querySelector('.mobile-menu-btn');
        const nav = document.querySelector('nav ul');
        
        mobileMenuBtn.addEventListener('click', () => {
            nav.style.display = nav.style.display === 'flex' ? 'none' : 'flex';
        });
        
        // Smooth Scrolling
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                
                const targetId = this.getAttribute('href');
                if (targetId === '#') return;
                
                const targetElement = document.querySelector(targetId);
                if (targetElement) {
                    window.scrollTo({
                        top: targetElement.offsetTop - 80,
                        behavior: 'smooth'
                    });
                    
                    // Close mobile menu if open
                    if (window.innerWidth <= 768) {
                        nav.style.display = 'none';
                    }
                }
            });
        });
        
        // Header Scroll Effect
        const header = document.getElementById('header');
        window.addEventListener('scroll', () => {
            if (window.scrollY > 50) {
                header.classList.add('scrolled');
            } else {
                header.classList.remove('scrolled');
            }
        });
        
        // Hero Image Animation
        const heroImage = document.querySelector('.hero-image');
        window.addEventListener('load', () => {
            heroImage.classList.add('animate');
        });
        
        // Feature Cards Animation
        const featureCards = document.querySelectorAll('.feature-card');
        const animateFeatures = () => {
            featureCards.forEach((card, index) => {
                setTimeout(() => {
                    card.classList.add('animate');
                }, index * 200);
            });
        };
        
        // Steps Animation
        const steps = document.querySelectorAll('.step');
        const animateSteps = () => {
            steps.forEach((step, index) => {
                setTimeout(() => {
                    step.classList.add('animate');
                }, index * 300);
            });
        };
        
        // FAQ Animation
        const faqItems = document.querySelectorAll('.faq-item');
        const animateFaq = () => {
            faqItems.forEach((item, index) => {
                setTimeout(() => {
                    item.classList.add('animate');
                }, index * 200);
            });
        };
        
        // Testimonials Slider
        const testimonials = document.querySelectorAll('.testimonial');
        const dots = document.querySelectorAll('.slider-dot');
        let currentSlide = 0;
        
        const showSlide = (index) => {
            testimonials.forEach(testimonial => testimonial.classList.remove('active'));
            dots.forEach(dot => dot.classList.remove('active'));
            
            testimonials[index].classList.add('active');
            dots[index].classList.add('active');
            currentSlide = index;
        };
        
        dots.forEach((dot, index) => {
            dot.addEventListener('click', () => showSlide(index));
        });
        
        // Auto slide change
        setInterval(() => {
            let nextSlide = (currentSlide + 1) % testimonials.length;
            showSlide(nextSlide);
        }, 5000);
        
        // FAQ Accordion
        faqItems.forEach(item => {
            const question = item.querySelector('.faq-question');
            question.addEventListener('click', () => {
                item.classList.toggle('active');
            });
        });
        
        // Intersection Observer for animations
        const observerOptions = {
            threshold: 0.1
        };
        
        const featuresObserver = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    animateFeatures();
                    featuresObserver.unobserve(entry.target);
                }
            });
        }, observerOptions);
        
        const stepsObserver = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    animateSteps();
                    stepsObserver.unobserve(entry.target);
                }
            });
        }, observerOptions);
        
        const faqObserver = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    animateFaq();
                    faqObserver.unobserve(entry.target);
                }
            });
        }, observerOptions);
        
        // Observe sections
        const featuresSection = document.querySelector('.features');
        const howItWorksSection = document.querySelector('.how-it-works');
        const faqSection = document.querySelector('.faq');
        
        if (featuresSection) featuresObserver.observe(featuresSection);
        if (howItWorksSection) stepsObserver.observe(howItWorksSection);
        if (faqSection) faqObserver.observe(faqSection);
        
        // Parallax Effect
        window.addEventListener('scroll', () => {
            const scrollPosition = window.scrollY;
            const parallaxElements = document.querySelectorAll('.parallax');
            
            parallaxElements.forEach(element => {
                element.style.backgroundPositionY = scrollPosition * 0.5 + 'px';
            });
        });
    </script>
</body>
</html>
