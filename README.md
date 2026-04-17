<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CENTEC GEO – Centre National d’Étude en Territoire et Cartographie CI</title>

    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">

    <style>
        :root {
            --primary: #0b5ed7;
            --secondary: #00c6ff;
            --dark: #050505;
            --glass: rgba(255, 255, 255, 0.05);
            --transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; scroll-behavior: smooth; }

        body {
            font-family: 'Segoe UI', Roboto, sans-serif;
            background: var(--dark);
            color: #e0e0e0;
            line-height: 1.7;
            overflow-x: hidden;
        }

        /* --- HEADER --- */
        header {
            position: fixed; width: 100%; top: 0; z-index: 1000;
            padding: 10px 5%; display: flex; justify-content: space-between; align-items: center;
            background: rgba(0, 0, 0, 0.95); backdrop-filter: blur(15px);
            border-bottom: 1px solid rgba(255,255,255,0.1);
        }

        .logo-container { display: flex; align-items: center; text-decoration: none; gap: 15px; }
        .logo-container img { height: 75px; width: auto; }
        
        .logo-text { border-left: 1px solid rgba(255,255,255,0.3); padding-left: 15px; }
        .logo-text h2 { color: white; font-size: 1.5rem; font-weight: 900; line-height: 1.1; margin: 0; }
        .logo-text span { color: var(--secondary); font-size: 0.7rem; text-transform: uppercase; font-weight: 600; display: block; margin-top: 3px; }

        .menu-btn {
            background: var(--primary);
            color: white; width: 45px; height: 45px;
            display: flex; align-items: center; justify-content: center;
            border-radius: 8px; cursor: pointer; transition: 0.3s; border: none;
        }
        .menu-btn:hover { background: var(--secondary); transform: scale(1.05); }

        /* NAV OVERLAY */
        .nav-overlay {
            position: fixed; top: 0; right: -100%; width: 300px; height: 100vh;
            background: rgba(0,0,0,0.98); z-index: 2000;
            display: flex; flex-direction: column; padding: 100px 40px;
            transition: 0.5s; border-left: 2px solid var(--primary);
        }
        .nav-overlay.active { right: 0; }
        .nav-overlay a {
            color: white; text-decoration: none; font-size: 1.2rem; margin-bottom: 25px;
            text-transform: uppercase; font-weight: bold; transition: 0.3s;
        }
        .nav-overlay a:hover { color: var(--secondary); padding-left: 10px; }
        .close-menu { position: absolute; top: 30px; right: 30px; font-size: 2rem; color: white; cursor: pointer; }

        /* --- HERO --- */
        .hero {
            height: 100vh; display: flex; flex-direction: column; justify-content: center;
            align-items: center; text-align: center; padding: 0 10%;
            background: linear-gradient(rgba(0,0,0,0.7), rgba(0,0,0,0.8)), url('https://images.unsplash.com/photo-1581091226825-a6a2a5aee158?q=80&w=1920');
            background-size: cover; background-position: center;
        }
        .hero h1 { font-size: clamp(2.5rem, 8vw, 5rem); color: white; }
        .hero p { font-size: 1.4rem; color: var(--secondary); font-weight: 300; }

        /* --- SECTIONS --- */
        section { padding: 100px 8%; max-width: 1400px; margin: auto; }
        .section-title { font-size: 2.5rem; color: white; margin-bottom: 60px; text-align: center; text-transform: uppercase; letter-spacing: 2px; }
        .section-title::after { content: ''; display: block; width: 80px; height: 4px; background: var(--primary); margin: 20px auto; }
        
        .content-box { background: var(--glass); padding: 50px; border-radius: 25px; border: 1px solid rgba(255,255,255,0.1); }

        /* --- DIRECTEUR --- */
        .director-box { display: grid; grid-template-columns: 1fr 2fr; gap: 50px; align-items: center; }
        .director-photo { width: 100%; max-width: 350px; border-radius: 20px; border: 5px solid var(--primary); }
        .director-name { color: white; font-size: 1.6rem; font-weight: 800; margin-top: 15px; }
        .director-title { color: var(--secondary); font-size: 0.85rem; text-transform: uppercase; }

        /* --- GRID & CARDS --- */
        .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(320px, 1fr)); gap: 30px; }
        .card { background: rgba(255,255,255,0.03); padding: 40px; border-radius: 20px; border: 1px solid rgba(255,255,255,0.05); transition: var(--transition); }
        .card:hover { transform: translateY(-15px); border-color: var(--secondary); background: rgba(255,255,255,0.08); }
        .card i { font-size: 3rem; color: var(--secondary); margin-bottom: 25px; display: block; }
        .card h3 { color: white; margin-bottom: 15px; }
        .card ul { list-style: none; margin-top: 15px; }
        .card ul li { font-size: 0.9rem; margin-bottom: 10px; color: #bbb; padding-left: 25px; position: relative; }
        .card ul li::before { content: '\f058'; font-family: 'Font Awesome 5 Free'; font-weight: 900; position: absolute; left: 0; color: var(--primary); }

        /* --- EQUIPE SLIDER --- */
        .team-wrapper { position: relative; overflow: hidden; }
        .team-slider { display: flex; gap: 30px; transition: transform 0.6s cubic-bezier(0.23, 1, 0.32, 1); }
        .team-member { flex: 0 0 calc(25% - 22.5px); background: var(--glass); padding: 30px; border-radius: 20px; text-align: center; }
        .team-member img { width: 140px; height: 140px; border-radius: 50%; object-fit: cover; border: 4px solid var(--primary); margin-bottom: 20px; }
        
        .nav-arrows { display: flex; justify-content: center; gap: 20px; margin-top: 40px; }
        .arrow { width: 50px; height: 50px; border-radius: 50%; background: var(--primary); color: white; display: flex; align-items: center; justify-content: center; cursor: pointer; border: none; transition: 0.3s; }
        .arrow:hover { background: var(--secondary); transform: scale(1.1); }

        /* --- BOUTON PARTENARIAT --- */
        .btn {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white; padding: 15px 35px; border-radius: 50px; text-decoration: none;
            display: inline-block; font-weight: 700; text-transform: uppercase; transition: 0.3s; border: none;
        }
        .btn:hover { transform: translateY(-3px); box-shadow: 0 10px 20px rgba(0,198,255,0.3); }

        /* --- FOOTER --- */
        footer { background: #000; padding: 80px 8% 40px; border-top: 1px solid #222; }
        .footer-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 50px; }
        .contact-list { list-style: none; margin-top: 20px; }
        .contact-list li { margin-bottom: 20px; display: flex; align-items: center; gap: 20px; font-size: 1.1rem; }
        .contact-list i { color: var(--secondary); font-size: 1.4rem; background: rgba(255,255,255,0.05); padding: 12px; border-radius: 10px; }
        .social-box { margin-top: 30px; display: flex; gap: 15px; }
        .social-box a { width: 50px; height: 50px; background: rgba(255,255,255,0.05); border-radius: 10px; display: flex; align-items: center; justify-content: center; color: white; text-decoration: none; transition: 0.3s; font-size: 1.3rem; }
        .social-box a:hover { background: var(--primary); transform: translateY(-5px); }

        @media (max-width: 992px) { .director-box { grid-template-columns: 1fr; text-align: center; } .team-member { flex: 0 0 calc(50% - 15px); } }
        @media (max-width: 600px) { .team-member { flex: 0 0 100%; } .logo-text span { font-size: 0.55rem; } }
    </style>
</head>
<body>

<header>
    <a href="#" class="logo-container">
        <img src="1000442449.jpg" alt="CENTEC GEO">
        <div class="logo-text">
            <h2>CENTEC GEO</h2>
            <span>Centre National d'Étude en Territoire et Cartographie CI</span>
        </div>
    </a>
    <button class="menu-btn" onclick="toggleMenu()"><i class="fas fa-th-large"></i></button>
</header>

<div class="nav-overlay" id="navOverlay">
    <i class="fas fa-times close-menu" onclick="toggleMenu()"></i>
    <a href="#accueil" onclick="toggleMenu()">Accueil</a>
    <a href="#propos" onclick="toggleMenu()">À Propos</a>
    <a href="#formations" onclick="toggleMenu()">Nos Formations</a>
    <a href="#services" onclick="toggleMenu()">Nos Services</a>
    <a href="#equipe" onclick="toggleMenu()">Notre Équipe</a>
    <a href="#contact" onclick="toggleMenu()">Contact</a>
</div>

<section class="hero" id="accueil">
    <h1 data-aos="zoom-out" data-aos-duration="1500">CENTEC GEO</h1>
    <p data-aos="fade-up" data-aos-delay="500">Maîtriser la géomatique pour mieux comprendre et gérer les territoires</p>
</section>

<section id="propos">
    <div class="content-box director-box" data-aos="fade-up">
        <div style="text-align: center;">
            <img src="photo_wilfried_codjo.jpg" alt="Wilfried Codjo" class="director-photo">
            <div class="director-name">WILFRIED CODJO</div>
            <div class="director-title">GÉOMATICIEN - SPÉCIALISTE EN PHOTOGRAMMÉTRIE</div>
        </div>
        <div>
            <h2 style="color: var(--secondary); margin-bottom: 20px;">Le Mot du Directeur</h2>
            <p style="font-style: italic; font-size: 1.15rem; border-left: 4px solid var(--primary); padding-left: 20px; margin-bottom: 20px;">
                "Le CENTEC est né d’un constat : la nécessité d'intégrer les technologies spatiales au cœur de nos stratégies de développement. Notre mission est de vous fournir l'expertise pour transformer chaque donnée territoriale en une décision éclairée."
            </p>
            <p>Le <strong>Centre National d’Étude en Territoire et Cartographie (CENTEC)</strong> est un pilier de l'innovation géospatiale en Côte d'Ivoire, offrant des solutions de pointe pour l'analyse des territoires.</p>
        </div>
    </div>
</section>

<section id="formations" style="background: rgba(255,255,255,0.01);">
    <h2 class="section-title" data-aos="fade-up">Nos Formations</h2>
    <div class="grid">
        <div class="card" data-aos="fade-up">
            <i class="fas fa-map-marked-alt"></i>
            <h3>DIGI MAP</h3>
            <ul>
                <li>Maîtrise de QGIS & ArcGIS Pro</li>
                <li>Sémiologie graphique & Cartographie</li>
                <li>Analyse de données géospatiales</li>
            </ul>
        </div>
        <div class="card" data-aos="fade-up" data-aos-delay="200">
            <i class="fas fa-satellite"></i>
            <h3>TeleSense Pro</h3>
            <ul>
                <li>Télédétection & Imagerie</li>
                <li>Classification d'occupation du sol</li>
                <li>Indices de végétation (NDVI)</li>
            </ul>
        </div>
        <div class="card" data-aos="fade-up" data-aos-delay="400">
            <i class="fas fa-mobile-alt"></i>
            <h3>E-Enquêteur</h3>
            <ul>
                <li>Formulaires KoboToolbox</li>
                <li>Collecte mobile géolocalisée</li>
                <li>Bases de données SQL/PostGIS</li>
            </ul>
        </div>
    </div>
</section>

<section id="services">
    <h2 class="section-title" data-aos="fade-up">Nos Services</h2>
    <div class="grid">
        <div class="card" data-aos="zoom-in">
            <i class="fas fa-drone"></i>
            <h3>Photogrammétrie Drone</h3>
            <p>Production de MNT/MNS, orthophotos haute résolution et cubatures précises.</p>
        </div>
        <div class="card" data-aos="zoom-in" data-aos-delay="200">
            <i class="fas fa-city"></i>
            <h3>Aménagement Urbain</h3>
            <p>Études de planification territoriale et diagnostic urbain par le SIG.</p>
        </div>
        <div class="card" data-aos="zoom-in" data-aos-delay="400">
            <i class="fas fa-database"></i>
            <h3>Ingénierie de Données</h3>
            <p>Structuration et hébergement de Systèmes d'Information Géographique (SIG).</p>
        </div>
    </div>
</section>

<section id="equipe" style="background: rgba(255,255,255,0.01);">
    <h2 class="section-title" data-aos="fade-up">Notre Équipe</h2>
    <div class="team-wrapper">
        <div class="team-slider" id="slider">
            <div class="team-member">
                <img src="expert1.jpg" alt="Expert">
                <h4>Nom Prénom</h4>
                <p>Expert SIG</p>
            </div>
            <div class="team-member">
                <img src="expert2.jpg" alt="Expert">
                <h4>Nom Prénom</h4>
                <p>Spécialiste Drone</p>
            </div>
            <div class="team-member">
                <img src="expert3.jpg" alt="Expert">
                <h4>Nom Prénom</h4>
                <p>Analyste DATA</p>
            </div>
            <div class="team-member">
                <img src="expert4.jpg" alt="Expert">
                <h4>Nom Prénom</h4>
                <p>Géographe</p>
            </div>
        </div>
    </div>
    <div class="nav-arrows">
        <button class="arrow" onclick="moveSlider(-1)"><i class="fas fa-chevron-left"></i></button>
        <button class="arrow" onclick="moveSlider(1)"><i class="fas fa-chevron-right"></i></button>
    </div>
</section>

<section id="contact">
    <h2 class="section-title" data-aos="fade-up">Partenariat</h2>
    <div class="content-box" style="text-align: center;" data-aos="zoom-in">
        <p style="font-size: 1.2rem; margin-bottom: 30px;">
            Collaborons pour bâtir des solutions territoriales innovantes. <br>
            Le CENTEC GEO accompagne les institutions et entreprises dans leur transformation numérique.
        </p>
        <a href="mailto:contact@centec.ci" class="btn">Proposer une collaboration</a>
    </div>
</section>

<footer>
    <div class="footer-grid">
        <div data-aos="fade-right">
            <h2 style="color: white; margin-bottom: 20px;">CENTEC GEO</h2>
            <p>L’expertise géospatiale au service du développement durable.</p>
            <div class="social-box">
                <a href="#"><i class="fab fa-linkedin-in"></i></a>
                <a href="#"><i class="fab fa-facebook-f"></i></a>
                <a href="#"><i class="fab fa-whatsapp"></i></a>
            </div>
        </div>
        <div data-aos="fade-left">
            <h3 style="color: white; margin-bottom: 25px;">Contact & Siège</h3>
            <ul class="contact-list">
                <li><i class="fas fa-map-marker-alt"></i> Cocody 2 Plateaux, Abidjan, CI</li>
                <li><i class="fas fa-phone-alt"></i> +225 00 00 00 00 00</li>
                <li><i class="fas fa-envelope"></i> contact@centec.ci</li>
            </ul>
        </div>
    </div>
    <div style="text-align: center; margin-top: 60px; color: #555; font-size: 0.85rem; border-top: 1px solid #222; padding-top: 30px;">
        © 2026 CENTEC GEO – Centre National d'Étude en Territoire et Cartographie CI
    </div>
</footer>

<script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
<script>
    AOS.init({ duration: 1000, once: true });
    function toggleMenu() { document.getElementById('navOverlay').classList.toggle('active'); }

    let currentScroll = 0;
    const slider = document.getElementById('slider');
    function moveSlider(direction) {
        const cardWidth = document.querySelector('.team-member').offsetWidth + 30;
        const maxScroll = slider.scrollWidth - slider.parentElement.offsetWidth;
        currentScroll += direction * cardWidth;
        if (currentScroll < 0) currentScroll = 0;
        if (currentScroll > maxScroll) currentScroll = maxScroll;
        slider.style.transform = `translateX(-${currentScroll}px)`;
    }
</script>

</body>
</html>
