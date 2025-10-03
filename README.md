<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>K. Kiran | AI & Computer Vision Specialist</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        :root {
            --primary: #0a192f;
            --secondary: #112240;
            --accent: #64ffda;
            --accent-light: #52d1ff;
            --text: #e6f1ff;
            --text-light: #a8b2d1;
        }

        body {
            overflow-x: hidden;
            background-color: var(--primary);
            color: var(--text);
            scroll-behavior: smooth;
            min-height: 100vh;
        }

        /* Loading Screen */
        .loading-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: var(--primary);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            transition: opacity 0.5s ease, visibility 0.5s ease;
        }

        .loading-screen.hidden {
            opacity: 0;
            visibility: hidden;
        }

        .loading-logo {
            font-size: 2.5rem;
            font-weight: 700;
            color: var(--accent);
            margin-bottom: 20px;
            position: relative;
            overflow: hidden;
        }

        .loading-logo::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 3px;
            background: linear-gradient(90deg, transparent, var(--accent), transparent);
            animation: loadingLine 2s infinite;
        }

        .loading-bar-container {
            width: 200px;
            height: 4px;
            background: rgba(100, 255, 218, 0.2);
            border-radius: 4px;
            overflow: hidden;
        }

        .loading-bar {
            height: 100%;
            width: 0%;
            background: var(--accent);
            border-radius: 4px;
            transition: width 0.3s ease;
        }

        /* Main Container */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* GitHub Intro Section */
        .github-intro {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
            background: linear-gradient(135deg, var(--primary) 0%, var(--secondary) 50%, #233554 100%);
        }

        .intro-content {
            text-align: center;
            z-index: 2;
            position: relative;
            max-width: 800px;
            padding: 40px;
            background: rgba(17, 34, 64, 0.7);
            border-radius: 20px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(100, 255, 218, 0.1);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
        }

        .avatar-container {
            width: 150px;
            height: 150px;
            margin: 0 auto 30px;
            position: relative;
        }

        .avatar {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--accent), var(--accent-light));
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3.5rem;
            color: var(--primary);
            animation: pulseAvatar 4s infinite ease-in-out;
            box-shadow: 0 0 30px rgba(100, 255, 218, 0.5);
        }

        .avatar-ring {
            position: absolute;
            top: -5px;
            left: -5px;
            right: -5px;
            bottom: -5px;
            border-radius: 50%;
            border: 2px solid transparent;
            border-top: 2px solid var(--accent);
            border-right: 2px solid var(--accent-light);
            animation: rotateRing 3s linear infinite;
        }

        .intro-content h1 {
            font-size: 3rem;
            margin-bottom: 1rem;
            font-weight: 700;
            background: linear-gradient(90deg, var(--accent), var(--accent-light));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            opacity: 0;
            transform: translateY(30px);
            animation: fadeInUp 1s ease forwards 0.5s;
        }

        .intro-content .tagline {
            font-size: 1.5rem;
            margin-bottom: 2rem;
            color: var(--text-light);
            opacity: 0;
            transform: translateY(30px);
            animation: fadeInUp 1s ease forwards 0.8s;
        }

        .intro-content .description {
            font-size: 1.1rem;
            line-height: 1.6;
            margin-bottom: 2.5rem;
            color: var(--text-light);
            opacity: 0;
            transform: translateY(30px);
            animation: fadeInUp 1s ease forwards 1.1s;
        }

        /* Interest Cards */
        .interests {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 20px;
            margin-bottom: 2.5rem;
        }

        .interest-card {
            background: rgba(23, 42, 69, 0.7);
            border-radius: 10px;
            padding: 20px;
            width: 200px;
            transition: all 0.3s ease;
            border: 1px solid rgba(100, 255, 218, 0.1);
            opacity: 0;
            transform: translateY(30px);
        }

        .interest-card.animated {
            animation: fadeInUp 0.8s ease forwards;
        }

        .interest-card:nth-child(1).animated {
            animation-delay: 1.4s;
        }

        .interest-card:nth-child(2).animated {
            animation-delay: 1.6s;
        }

        .interest-card:nth-child(3).animated {
            animation-delay: 1.8s;
        }

        .interest-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.3);
            border-color: var(--accent);
        }

        .interest-icon {
            font-size: 2.5rem;
            color: var(--accent);
            margin-bottom: 15px;
        }

        .interest-card h3 {
            font-size: 1.2rem;
            margin-bottom: 10px;
            color: var(--text);
        }

        .interest-card p {
            color: var(--text-light);
            font-size: 0.9rem;
            line-height: 1.5;
        }

        /* Social Links */
        .social-links {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-bottom: 2.5rem;
        }

        .social-link {
            width: 50px;
            height: 50px;
            background: rgba(23, 42, 69, 0.7);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--text-light);
            font-size: 1.5rem;
            text-decoration: none;
            transition: all 0.3s ease;
            border: 1px solid rgba(100, 255, 218, 0.1);
            opacity: 0;
            transform: translateY(30px);
        }

        .social-link.animated {
            animation: fadeInUp 0.8s ease forwards;
        }

        .social-link:nth-child(1).animated {
            animation-delay: 2s;
        }

        .social-link:nth-child(2).animated {
            animation-delay: 2.1s;
        }

        .social-link:nth-child(3).animated {
            animation-delay: 2.2s;
        }

        .social-link:nth-child(4).animated {
            animation-delay: 2.3s;
        }

        .social-link:hover {
            background: rgba(100, 255, 218, 0.1);
            color: var(--accent);
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(100, 255, 218, 0.2);
            border-color: var(--accent);
        }

        /* CTA Button */
        .cta-button {
            display: inline-block;
            padding: 15px 35px;
            background: transparent;
            color: var(--accent);
            border: 1px solid var(--accent);
            border-radius: 5px;
            text-decoration: none;
            font-weight: 600;
            letter-spacing: 1px;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
            opacity: 0;
            transform: translateY(30px);
            animation: fadeInUp 1s ease forwards 2.5s;
        }

        .cta-button::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(100, 255, 218, 0.2), transparent);
            transition: left 0.5s;
        }

        .cta-button:hover {
            background: rgba(100, 255, 218, 0.1);
            box-shadow: 0 0 15px rgba(100, 255, 218, 0.4);
            transform: translateY(-3px);
        }

        .cta-button:hover::before {
            left: 100%;
        }

        /* Animated Background Shapes */
        .bg-shapes {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            z-index: 0;
            overflow: hidden;
        }

        .shape {
            position: absolute;
            border-radius: 50%;
            background: rgba(100, 255, 218, 0.1);
            animation: float 15s infinite linear;
        }

        .shape:nth-child(1) {
            width: 300px;
            height: 300px;
            top: -150px;
            left: -150px;
            animation-delay: 0s;
        }

        .shape:nth-child(2) {
            width: 200px;
            height: 200px;
            bottom: -100px;
            right: 10%;
            animation-delay: 3s;
            animation-duration: 20s;
        }

        .shape:nth-child(3) {
            width: 150px;
            height: 150px;
            top: 20%;
            right: -75px;
            animation-delay: 6s;
            animation-duration: 25s;
        }

        /* Particle Background */
        #particles-js {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            z-index: 1;
        }

        /* Floating Elements */
        .floating-elements {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            z-index: 1;
        }

        .floating-element {
            position: absolute;
            opacity: 0.1;
            color: var(--accent);
            font-size: 2rem;
            transition: all 0.5s ease;
        }

        .floating-element:hover {
            opacity: 0.3;
            transform: scale(1.2);
        }

        /* Animations */
        @keyframes fadeInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes float {
            0% {
                transform: translate(0, 0) rotate(0deg);
            }
            33% {
                transform: translate(30px, -50px) rotate(120deg);
            }
            66% {
                transform: translate(-20px, 20px) rotate(240deg);
            }
            100% {
                transform: translate(0, 0) rotate(360deg);
            }
        }

        @keyframes loadingLine {
            0% {
                transform: translateX(-100%);
            }
            50% {
                transform: translateX(100%);
            }
            100% {
                transform: translateX(-100%);
            }
        }

        @keyframes pulseAvatar {
            0%, 100% {
                transform: scale(1);
                box-shadow: 0 0 30px rgba(100, 255, 218, 0.5);
            }
            50% {
                transform: scale(1.05);
                box-shadow: 0 0 50px rgba(100, 255, 218, 0.8);
            }
        }

        @keyframes rotateRing {
            0% {
                transform: rotate(0deg);
            }
            100% {
                transform: rotate(360deg);
            }
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .intro-content {
                padding: 30px 20px;
            }
            
            .intro-content h1 {
                font-size: 2.2rem;
            }
            
            .intro-content .tagline {
                font-size: 1.2rem;
            }
            
            .intro-content .description {
                font-size: 1rem;
            }
            
            .interests {
                flex-direction: column;
                align-items: center;
            }
            
            .interest-card {
                width: 100%;
                max-width: 300px;
            }
            
            .social-links {
                flex-wrap: wrap;
            }
        }
    </style>
</head>
<body>
    <!-- Loading Screen -->
    <div class="loading-screen" id="loadingScreen">
        <div class="loading-logo">K. Kiran</div>
        <div class="loading-bar-container">
            <div class="loading-bar" id="loadingBar"></div>
        </div>
    </div>

    <!-- GitHub Introduction Section -->
    <section class="github-intro">
        <!-- Animated Background Shapes -->
        <div class="bg-shapes">
            <div class="shape"></div>
            <div class="shape"></div>
            <div class="shape"></div>
        </div>
        
        <!-- Particle Background -->
        <div id="particles-js"></div>
        
        <!-- Floating Elements -->
        <div class="floating-elements">
            <i class="fas fa-brain floating-element" style="top: 20%; left: 10%; animation: float 20s infinite linear;"></i>
            <i class="fas fa-robot floating-element" style="top: 60%; left: 85%; animation: float 25s infinite linear reverse;"></i>
            <i class="fas fa-camera floating-element" style="top: 80%; left: 15%; animation: float 18s infinite linear;"></i>
            <i class="fas fa-microchip floating-element" style="top: 30%; left: 80%; animation: float 22s infinite linear reverse;"></i>
        </div>
        
        <div class="container">
            <div class="intro-content">
                <div class="avatar-container">
                    <div class="avatar">
                        <i class="fas fa-user"></i>
                    </div>
                    <div class="avatar-ring"></div>
                </div>
                
                <h1>K. Kiran</h1>
                <p class="tagline">AI & Computer Vision Specialist</p>
                <p class="description">
                    Passionate about artificial intelligence and its transformative potential. 
                    Currently focused on computer vision and image processing, constantly learning 
                    and exploring new techniques to solve complex problems. Looking to collaborate 
                    on innovative AI and deep learning projects.
                </p>
                
                <div class="interests">
                    <div class="interest-card">
                        <div class="interest-icon">
                            <i class="fas fa-brain"></i>
                        </div>
                        <h3>AI Research</h3>
                        <p>Developing intelligent systems and algorithms</p>
                    </div>
                    
                    <div class="interest-card">
                        <div class="interest-icon">
                            <i class="fas fa-eye"></i>
                        </div>
                        <h3>Computer Vision</h3>
                        <p>Creating systems that interpret visual information</p>
                    </div>
                    
                    <div class="interest-card">
                        <div class="interest-icon">
                            <i class="fas fa-image"></i>
                        </div>
                        <h3>Image Processing</h3>
                        <p>Manipulating and analyzing digital images</p>
                    </div>
                </div>
                
                <div class="social-links">
                    <a href="https://www.linkedin.com/in/kinnera-kiran/" class="social-link" target="_blank">
                        <i class="fab fa-linkedin"></i>
                    </a>
                    <a href="https://x.com/KKiranAI" class="social-link" target="_blank">
                        <i class="fab fa-twitter"></i>
                    </a>
                    <a href="https://github.com/MrKinneraKiran" class="social-link" target="_blank">
                        <i class="fab fa-github"></i>
                    </a>
                    <a href="https://scholar.google.com/citations?user=BElmcKwAAAAJ" class="social-link" target="_blank">
                        <i class="fab fa-google"></i>
                    </a>
                </div>
                
                <a href="https://github.com/MrKinneraKiran" class="cta-button" target="_blank">
                    View My GitHub Profile
                </a>
            </div>
        </div>
    </section>

    <!-- Particle.js Library -->
    <script src="https://cdn.jsdelivr.net/particles.js/2.0.0/particles.min.js"></script>
    
    <script>
        // Loading screen animation
        document.addEventListener('DOMContentLoaded', function() {
            const loadingScreen = document.getElementById('loadingScreen');
            const loadingBar = document.getElementById('loadingBar');
            
            // Simulate loading progress
            let progress = 0;
            const interval = setInterval(() => {
                progress += Math.random() * 15;
                if (progress >= 100) {
                    progress = 100;
                    clearInterval(interval);
                    
                    // Hide loading screen after a short delay
                    setTimeout(() => {
                        loadingScreen.classList.add('hidden');
                    }, 500);
                }
                loadingBar.style.width = `${progress}%`;
            }, 200);
            
            // Initialize particles.js
            particlesJS('particles-js', {
                particles: {
                    number: {
                        value: 80,
                        density: {
                            enable: true,
                            value_area: 800
                        }
                    },
                    color: {
                        value: "#64ffda"
                    },
                    shape: {
                        type: "circle"
                    },
                    opacity: {
                        value: 0.5,
                        random: true
                    },
                    size: {
                        value: 3,
                        random: true
                    },
                    line_linked: {
                        enable: true,
                        distance: 150,
                        color: "#52d1ff",
                        opacity: 0.4,
                        width: 1
                    },
                    move: {
                        enable: true,
                        speed: 2,
                        direction: "none",
                        random: true,
                        straight: false,
                        out_mode: "out",
                        bounce: false
                    }
                },
                interactivity: {
                    detect_on: "canvas",
                    events: {
                        onhover: {
                            enable: true,
                            mode: "grab"
                        },
                        onclick: {
                            enable: true,
                            mode: "push"
                        },
                        resize: true
                    }
                },
                retina_detect: true
            });
            
            // Animate elements when they come into view
            window.addEventListener('scroll', function() {
                const interestCards = document.querySelectorAll('.interest-card');
                const socialLinks = document.querySelectorAll('.social-link');
                
                // Interest cards
                interestCards.forEach(card => {
                    if (isElementInViewport(card)) {
                        card.classList.add('animated');
                    }
                });
                
                // Social links
                socialLinks.forEach(link => {
                    if (isElementInViewport(link)) {
                        link.classList.add('animated');
                    }
                });
            });
            
            // Helper function to check if element is in viewport
            function isElementInViewport(el) {
                const rect = el.getBoundingClientRect();
                return (
                    rect.top >= 0 &&
                    rect.left >= 0 &&
                    rect.bottom <= (window.innerHeight || document.documentElement.clientHeight) &&
                    rect.right <= (window.innerWidth || document.documentElement.clientWidth)
                );
            }
            
            // Trigger animations on load
            setTimeout(() => {
                const interestCards = document.querySelectorAll('.interest-card');
                const socialLinks = document.querySelectorAll('.social-link');
                
                interestCards.forEach(card => {
                    card.classList.add('animated');
                });
                
                socialLinks.forEach(link => {
                    link.classList.add('animated');
                });
            }, 1500);
        });
    </script>
</body>
</html>
