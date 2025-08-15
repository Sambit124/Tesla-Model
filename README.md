<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tesla Model S - Interactive Showcase</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #000000 0%, #1a1a1a 100%);
            color: white;
            overflow-x: hidden;
            line-height: 1.6;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Header */
        header {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(0, 0, 0, 0.9);
            backdrop-filter: blur(10px);
            z-index: 1000;
            padding: 15px 0;
            transition: all 0.3s ease;
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 28px;
            font-weight: bold;
            color: #ff0000;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 30px;
        }

        .nav-links a {
            color: white;
            text-decoration: none;
            transition: color 0.3s ease;
            font-weight: 500;
        }

        .nav-links a:hover {
            color: #ff0000;
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            background: linear-gradient(45deg, #000000, #1a1a1a, #333333);
            overflow: hidden;
        }

        .hero-content {
            text-align: center;
            z-index: 2;
            max-width: 800px;
        }

        .hero h1 {
            font-size: 4rem;
            margin-bottom: 20px;
            background: linear-gradient(45deg, #ff0000, #ffffff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: glow 2s ease-in-out infinite alternate;
        }

        @keyframes glow {
            from { filter: drop-shadow(0 0 5px #ff0000); }
            to { filter: drop-shadow(0 0 20px #ff0000); }
        }

        .hero p {
            font-size: 1.3rem;
            margin-bottom: 30px;
            opacity: 0.9;
        }

        .cta-button {
            display: inline-block;
            padding: 15px 40px;
            background: linear-gradient(45deg, #ff0000, #cc0000);
            color: white;
            text-decoration: none;
            border-radius: 30px;
            font-weight: bold;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(255, 0, 0, 0.3);
        }

        .cta-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(255, 0, 0, 0.5);
        }

        /* Tesla Model Display */
        .model-showcase {
            padding: 100px 0;
            background: #111111;
        }

        .model-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 60px;
            align-items: center;
            margin-bottom: 80px;
        }

        .model-image {
            position: relative;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 20px 40px rgba(255, 0, 0, 0.2);
            transition: transform 0.3s ease;
        }

        .model-image:hover {
            transform: scale(1.05);
        }

        .model-image img {
            width: 100%;
            height: 400px;
            object-fit: cover;
            transition: all 0.3s ease;
        }

        .model-info {
            padding: 20px;
        }

        .model-info h2 {
            font-size: 2.5rem;
            margin-bottom: 20px;
            color: #ff0000;
        }

        .model-info p {
            font-size: 1.1rem;
            margin-bottom: 25px;
            opacity: 0.9;
        }

        .specs {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 20px;
            margin-top: 30px;
        }

        .spec-item {
            background: rgba(255, 255, 255, 0.05);
            padding: 20px;
            border-radius: 10px;
            text-align: center;
            transition: all 0.3s ease;
            border: 1px solid rgba(255, 0, 0, 0.2);
        }

        .spec-item:hover {
            background: rgba(255, 0, 0, 0.1);
            transform: translateY(-5px);
        }

        .spec-value {
            font-size: 2rem;
            font-weight: bold;
            color: #ff0000;
            display: block;
        }

        .spec-label {
            font-size: 0.9rem;
            opacity: 0.8;
        }

        /* Interactive Controls */
        .controls-section {
            padding: 80px 0;
            background: linear-gradient(135deg, #1a1a1a, #000000);
        }

        .controls-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            margin-top: 50px;
        }

        .control-panel {
            background: rgba(255, 255, 255, 0.05);
            padding: 30px;
            border-radius: 15px;
            border: 1px solid rgba(255, 0, 0, 0.2);
            transition: all 0.3s ease;
        }

        .control-panel:hover {
            background: rgba(255, 0, 0, 0.1);
            transform: translateY(-5px);
        }

        .control-panel h3 {
            color: #ff0000;
            margin-bottom: 20px;
            font-size: 1.3rem;
        }

        .color-options {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }

        .color-btn {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            border: 2px solid white;
            cursor: pointer;
            transition: transform 0.3s ease;
        }

        .color-btn:hover {
            transform: scale(1.2);
        }

        .color-btn.red { background: #ff0000; }
        .color-btn.white { background: #ffffff; }
        .color-btn.black { background: #000000; }
        .color-btn.blue { background: #0066cc; }
        .color-btn.silver { background: #c0c0c0; }

        .slider-container {
            margin: 20px 0;
        }

        .slider {
            width: 100%;
            height: 5px;
            border-radius: 5px;
            background: #333;
            outline: none;
            -webkit-appearance: none;
        }

        .slider::-webkit-slider-thumb {
            -webkit-appearance: none;
            appearance: none;
            width: 20px;
            height: 20px;
            border-radius: 50%;
            background: #ff0000;
            cursor: pointer;
        }

        .toggle-switch {
            position: relative;
            display: inline-block;
            width: 60px;
            height: 34px;
            margin: 10px 0;
        }

        .toggle-switch input {
            opacity: 0;
            width: 0;
            height: 0;
        }

        .slider-toggle {
            position: absolute;
            cursor: pointer;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background-color: #333;
            transition: .4s;
            border-radius: 34px;
        }

        .slider-toggle:before {
            position: absolute;
            content: "";
            height: 26px;
            width: 26px;
            left: 4px;
            bottom: 4px;
            background-color: white;
            transition: .4s;
            border-radius: 50%;
        }

        input:checked + .slider-toggle {
            background-color: #ff0000;
        }

        input:checked + .slider-toggle:before {
            transform: translateX(26px);
        }

        /* 360 View Section */
        .view-360 {
            padding: 80px 0;
            background: #000000;
            text-align: center;
        }

        .view-360 h2 {
            font-size: 2.5rem;
            margin-bottom: 30px;
            color: #ff0000;
        }

        .rotation-container {
            position: relative;
            max-width: 800px;
            margin: 0 auto;
            height: 500px;
            background: radial-gradient(circle, #1a1a1a, #000000);
            border-radius: 20px;
            overflow: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .tesla-3d {
            width: 90%;
            height: 90%;
            transition: transform 0.1s ease;
            cursor: grab;
        }

        .tesla-3d:active {
            cursor: grabbing;
        }

        .tesla-3d img {
            width: 100%;
            height: 100%;
            object-fit: contain;
        }

        .rotation-controls {
            margin-top: 30px;
            display: flex;
            justify-content: center;
            gap: 20px;
        }

        .rotation-btn {
            padding: 10px 20px;
            background: rgba(255, 0, 0, 0.2);
            border: 1px solid #ff0000;
            color: white;
            border-radius: 5px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .rotation-btn:hover {
            background: #ff0000;
        }

        /* Footer */
        footer {
            background: #000000;
            padding: 50px 0;
            text-align: center;
            border-top: 1px solid #333;
        }

        .footer-content {
            margin-bottom: 30px;
        }

        .footer-links {
            display: flex;
            justify-content: center;
            gap: 30px;
            margin-bottom: 20px;
        }

        .footer-links a {
            color: #ccc;
            text-decoration: none;
            transition: color 0.3s ease;
        }

        .footer-links a:hover {
            color: #ff0000;
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .hero h1 {
                font-size: 2.5rem;
            }

            .model-container {
                grid-template-columns: 1fr;
                gap: 40px;
            }

            .nav-links {
                display: none;
            }

            .specs {
                grid-template-columns: 1fr;
            }

            .controls-grid {
                grid-template-columns: 1fr;
            }
        }

        /* Loading Animation */
        .loading {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: #000;
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            transition: opacity 0.5s ease;
        }

        .loading-spinner {
            width: 50px;
            height: 50px;
            border: 3px solid #333;
            border-top: 3px solid #ff0000;
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
    </style>
</head>
<body>
    <!-- Loading Screen -->
    <div class="loading" id="loading">
        <div class="loading-spinner"></div>
    </div>

    <!-- Header -->
    <header>
        <nav class="container">
            <div class="logo">TESLA</div>
            <ul class="nav-links">
                <li><a href="#home">Home</a></li>
                <li><a href="#models">Models</a></li>
                <li><a href="#configure">Configure</a></li>
                <li><a href="#360view">360° View</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
        </nav>
    </header>

    <!-- Hero Section -->
    <section class="hero" id="home">
        <div class="hero-content">
            <h1>Tesla Model S</h1>
            <p>Experience the future of automotive excellence with cutting-edge technology and unparalleled performance.</p>
            <a href="#models" class="cta-button">Explore Models</a>
        </div>
    </section>

    <!-- Model Showcase -->
    <section class="model-showcase" id="models">
        <div class="container">
            <div class="model-container">
                <div class="model-image">
                    <img src="https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/b2ddfacf-a3f0-4e09-9e95-0358c7682065.png" alt="Tesla Model S luxury electric sedan in pearl white color parked on a modern concrete surface with dramatic lighting showcasing its sleek aerodynamic design and distinctive LED headlights" id="mainModelImage" />
                </div>
                <div class="model-info">
                    <h2>Model S Plaid</h2>
                    <p>The quickest accelerating sedan ever built. With tri-motor all-wheel drive, the Model S Plaid delivers incredible performance and efficiency.</p>
                    <div class="specs">
                        <div class="spec-item">
                            <span class="spec-value">1020</span>
                            <span class="spec-label">Horsepower</span>
                        </div>
                        <div class="spec-item">
                            <span class="spec-value">1.99s</span>
                            <span class="spec-label">0-60 mph</span>
                        </div>
                        <div class="spec-item">
                            <span class="spec-value">396mi</span>
                            <span class="spec-label">Range</span>
                        </div>
                        <div class="spec-item">
                            <span class="spec-value">200mph</span>
                            <span class="spec-label">Top Speed</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Interactive Controls -->
    <section class="controls-section" id="configure">
        <div class="container">
            <h2 style="text-align: center; font-size: 2.5rem; color: #ff0000; margin-bottom: 20px;">Configure Your Tesla</h2>
            <p style="text-align: center; opacity: 0.9; margin-bottom: 50px;">Customize every aspect of your Tesla to match your preferences</p>
            
            <div class="controls-grid">
                <div class="control-panel">
                    <h3>Exterior Color</h3>
                    <p>Choose from our premium paint options</p>
                    <div class="color-options">
                        <div class="color-btn red" onclick="changeColor('red')" title="Red Multi-Coat"></div>
                        <div class="color-btn white" onclick="changeColor('white')" title="Pearl White"></div>
                        <div class="color-btn black" onclick="changeColor('black')" title="Solid Black"></div>
                        <div class="color-btn blue" onclick="changeColor('blue')" title="Deep Blue Metallic"></div>
                        <div class="color-btn silver" onclick="changeColor('silver')" title="Midnight Silver Metallic"></div>
                    </div>
                </div>

                <div class="control-panel">
                    <h3>Performance Settings</h3>
                    <p>Adjust your driving experience</p>
                    <div class="slider-container">
                        <label>Acceleration: <span id="accelValue">50</span>%</label>
                        <input type="range" min="0" max="100" value="50" class="slider" id="accelSlider" oninput="updateAcceleration(this.value)">
                    </div>
                    <div class="slider-container">
                        <label>Regenerative Braking: <span id="regenValue">75</span>%</label>
                        <input type="range" min="0" max="100" value="75" class="slider" id="regenSlider" oninput="updateRegen(this.value)">
                    </div>
                </div>

                <div class="control-panel">
                    <h3>Autopilot Features</h3>
                    <p>Enable advanced driving assistance</p>
                    <div>
                        <label>
                            <span>Full Self-Driving</span>
                            <div class="toggle-switch">
                                <input type="checkbox" id="fsdToggle" onchange="toggleFSD()">
                                <span class="slider-toggle"></span>
                            </div>
                        </label>
                    </div>
                    <div style="margin-top: 15px;">
                        <label>
                            <span>Enhanced Autopilot</span>
                            <div class="toggle-switch">
                                <input type="checkbox" id="autopilotToggle" onchange="toggleAutopilot()" checked>
                                <span class="slider-toggle"></span>
                            </div>
                        </label>
                    </div>
                </div>

                <div class="control-panel">
                    <h3>Interior Options</h3>
                    <p>Personalize your cabin experience</p>
                    <div class="slider-container">
                        <label>Ambient Lighting: <span id="lightValue">60</span>%</label>
                        <input type="range" min="0" max="100" value="60" class="slider" id="lightSlider" oninput="updateLighting(this.value)">
                    </div>
                    <div style="margin-top: 15px;">
                        <label>
                            <span>Premium Audio</span>
                            <div class="toggle-switch">
                                <input type="checkbox" id="audioToggle" onchange="toggleAudio()" checked>
                                <span class="slider-toggle"></span>
                            </div>
                        </label>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- 360 View Section -->
    <section class="view-360" id="360view">
        <div class="container">
            <h2>360° Model View</h2>
            <p style="opacity: 0.9; margin-bottom: 40px;">Drag to rotate and explore every angle of your Tesla</p>
            
            <div class="rotation-container">
                <div class="tesla-3d" id="tesla3d">
                    <img src="https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/037fa5d4-69b0-4fd9-848b-66e35fb058c7.png" alt="Tesla Model S shown from a three-quarter front view angle in metallic silver paint with premium wheels and distinctive Tesla design elements against a gradient background" id="rotationImage" />
                </div>
            </div>
            
            <div class="rotation-controls">
                <button class="rotation-btn" onclick="rotateModel('left')">Rotate Left</button>
                <button class="rotation-btn" onclick="resetRotation()">Reset View</button>
                <button class="rotation-btn" onclick="rotateModel('right')">Rotate Right</button>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer id="contact">
        <div class="container">
            <div class="footer-content">
                <h3 style="color: #ff0000; margin-bottom: 20px;">Ready to Experience Tesla?</h3>
                <p>Join the electric revolution and drive into the future today.</p>
            </div>
            <div class="footer-links">
                <a href="#order">Order Now</a>
                <a href="#test-drive">Schedule Test Drive</a>
                <a href="#support">Support</a>
                <a href="#careers">Careers</a>
                <a href="#investors">Investors</a>
            </div>
            <p style="opacity: 0.6; margin-top: 20px;">© 2024 Tesla, Inc. All rights reserved.</p>
        </div>
    </footer>

    <script>
        // Global variables
        let currentRotation = 0;
        let isRotating = false;
        let startX = 0;

        // Page load animation
        window.addEventListener('load', function() {
            setTimeout(() => {
                document.getElementById('loading').style.opacity = '0';
                setTimeout(() => {
                    document.getElementById('loading').style.display = 'none';
                }, 500);
            }, 1500);
        });

        // Smooth scrolling for navigation links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });

        // Color change functionality
        function changeColor(color) {
            const mainImage = document.getElementById('mainModelImage');
            const rotationImage = document.getElementById('rotationImage');
            
            let altText = '';
            switch(color) {
                case 'red':
                    altText = 'Tesla Model S in vibrant red multi-coat paint finish showcasing the premium exterior with dramatic lighting and sleek automotive design';
                    break;
                case 'white':
                    altText = 'Tesla Model S in pearl white paint with premium finish displaying elegant curves and modern electric vehicle aesthetics';
                    break;
                case 'black':
                    altText = 'Tesla Model S in solid black paint with glossy finish highlighting the sophisticated and powerful design elements';
                    break;
                case 'blue':
                    altText = 'Tesla Model S in deep blue metallic paint with lustrous finish emphasizing the luxury and innovation of electric mobility';
                    break;
                case 'silver':
                    altText = 'Tesla Model S in midnight silver metallic paint with reflective finish showcasing technological advancement and premium craftsmanship';
                    break;
            }
            
            // Add visual feedback
            document.querySelectorAll('.color-btn').forEach(btn => {
                btn.style.transform = 'scale(1)';
                btn.style.boxShadow = 'none';
            });
            
            event.target.style.transform = 'scale(1.2)';
            event.target.style.boxShadow = '0 0 20px rgba(255, 255, 255, 0.8)';
            
            // Update image alt text
            mainImage.alt = altText;
            rotationImage.alt = altText;
            
            // Add color change effect
            mainImage.style.filter = 'brightness(0.8)';
            setTimeout(() => {
                mainImage.style.filter = 'brightness(1)';
            }, 200);
        }

        // Performance slider updates
        function updateAcceleration(value) {
            document.getElementById('accelValue').textContent = value;
            
            // Visual feedback based on value
            const slider = document.getElementById('accelSlider');
            slider.style.background = `linear-gradient(to right, #ff0000 0%, #ff0000 ${value}%, #333 ${value}%, #333 100%)`;
        }

        function updateRegen(value) {
            document.getElementById('regenValue').textContent = value;
            
            const slider = document.getElementById('regenSlider');
            slider.style.background = `linear-gradient(to right, #ff0000 0%, #ff0000 ${value}%, #333 ${value}%, #333 100%)`;
        }

        function updateLighting(value) {
            document.getElementById('lightValue').textContent = value;
            
            const slider = document.getElementById('lightSlider');
            slider.style.background = `linear-gradient(to right, #ff0000 0%, #ff0000 ${value}%, #333 ${value}%, #333 100%)`;
            
            // Visual effect for lighting
            document.body.style.background = `linear-gradient(135deg, 
                rgba(${value * 2.55}, 0, 0, 0.1) 0%, 
                #000000 ${100 - value}%, 
                #1a1a1a 100%)`;
        }

        // Toggle functions
        function toggleFSD() {
            const toggle = document.getElementById('fsdToggle');
            console.log('Full Self-Driving:', toggle.checked ? 'Enabled' : 'Disabled');
        }

        function toggleAutopilot() {
            const toggle = document.getElementById('autopilotToggle');
            console.log('Enhanced Autopilot:', toggle.checked ? 'Enabled' : 'Disabled');
        }

        function toggleAudio() {
            const toggle = document.getElementById('audioToggle');
            console.log('Premium Audio:', toggle.checked ? 'Enabled' : 'Disabled');
        }

        // 360 degree rotation functionality
        function rotateModel(direction) {
            const rotationAmount = direction === 'left' ? -45 : 45;
            currentRotation += rotationAmount;
            
            const tesla3d = document.getElementById('tesla3d');
            tesla3d.style.transform = `rotateY(${currentRotation}deg)`;
        }

        function resetRotation() {
            currentRotation = 0;
            const tesla3d = document.getElementById('tesla3d');
            tesla3d.style.transform = `rotateY(0deg)`;
        }

        // Mouse drag rotation
        const tesla3d = document.getElementById('tesla3d');

        tesla3d.addEventListener('mousedown', (e) => {
            isRotating = true;
            startX = e.clientX;
            tesla3d.style.cursor = 'grabbing';
        });

        document.addEventListener('mousemove', (e) => {
            if (isRotating) {
                const deltaX = e.clientX - startX;
                currentRotation += deltaX * 0.5;
                tesla3d.style.transform = `rotateY(${currentRotation}deg)`;
                startX = e.clientX;
            }
        });

        document.addEventListener('mouseup', () => {
            isRotating = false;
            tesla3d.style.cursor = 'grab';
        });

        // Touch support for mobile
        tesla3d.addEventListener('touchstart', (e) => {
            isRotating = true;
            startX = e.touches[0].clientX;
        });

        tesla3d.addEventListener('touchmove', (e) => {
            if (isRotating) {
                e.preventDefault();
                const deltaX = e.touches[0].clientX - startX;
                currentRotation += deltaX * 0.5;
                tesla3d.style.transform = `rotateY(${currentRotation}deg)`;
                startX = e.touches[0].clientX;
            }
        });

        tesla3d.addEventListener('touchend', () => {
            isRotating = false;
        });

        // Parallax scrolling effect
        window.addEventListener('scroll', () => {
            const scrolled = window.pageYOffset;
            const hero = document.querySelector('.hero');
            
            if (hero) {
                hero.style.transform = `translateY(${scrolled * 0.5}px)`;
            }
        });

        // Initialize sliders with gradient backgrounds
        document.addEventListener('DOMContentLoaded', function() {
            updateAcceleration(50);
            updateRegen(75);
            updateLighting(60);
        });

        // Add intersection observer for animations
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        }, observerOptions);

        // Observe elements for animation
        document.querySelectorAll('.control-panel, .spec-item, .model-image').forEach(el => {
            el.style.opacity = '0';
            el.style.transform = 'translateY(30px)';
            el.style.transition = 'all 0.6s ease';
            observer.observe(el);
        });
    </script>
</body>
</html>

