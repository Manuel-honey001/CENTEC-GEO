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
            --dark: #0a0f1a; 
            --darker: #070b14;
            --glass: rgba(255, 255, 255, 0.03);
            --transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; scroll-behavior: smooth; }

        body {
            font-family: 'Segoe UI', Roboto, sans-serif;
            background-color: var(--dark);
            background-image: radial-gradient(circle at 50% 0%, #162035 0%, var(--dark) 70%);
            color: #e0e6ed;
            line-height: 1.7;
            overflow-x: hidden;
        }

        /* --- HEADER --- */
        header {
            position: fixed; width: 100%; top: 0; z-index: 1000;
            padding: 10px 5%; display: flex; justify-content: space-between; align-items: center;
            background: rgba(7, 11, 20, 0.85); backdrop-filter: blur(20px);
            border-bottom: 1px solid rgba(255,255,255,0.05);
        }

        .logo-container { display: flex; align-items: center; text-decoration: none; gap: 15px; }
        .logo-container img { height: 70px; width: auto; }
        
        .logo-text { border-left: 1px solid rgba(255,255,255,0.2); padding-left: 15px; }
        .logo-text h2 { color: white; font-size: 1.4rem; font-weight: 900; line-height: 1.1; margin: 0; }
        .logo-text span { color: var(--secondary); font-size: 0.65rem; text-transform: uppercase; font-weight: 600; display: block; margin-top: 3px; }

        .menu-btn {
            background: var(--primary);
            color: white; width: 45px; height: 45px;
            display: flex; align-items: center; justify-content: center;
            border-radius: 12px; cursor: pointer; transition: 0.3s; border: none;
        }
        .menu-btn:hover { background: var(--secondary); transform: translateY(-2px); }

        /* NAV OVERLAY */
        .nav-overlay {
            position: fixed; top: 0; right: -100%; width: 300px; height: 100vh;
            background: var(--darker); z-index: 2000;
            display: flex; flex-direction: column; padding: 100px 40px;
            transition: 0.5s; border-left: 2px solid var(--primary);
        }
        .nav-overlay.active { right: 0; }
        .nav-overlay a {
            color: white; text-decoration: none; font-size: 1.1rem; margin-bottom: 25px;
            text-transform: uppercase; font-weight: bold; transition: 0.3s;
        }
        .nav-overlay a:hover { color: var(--secondary); padding-left: 10px; }
        .close-menu { position: absolute; top: 30px; right: 30px; font-size: 2rem; color: white; cursor: pointer; }

        /* --- HERO --- */
        .hero {
            height: 100vh; display: flex; flex-direction: column; justify-content: center;
            align-items: center; text-align: center; padding: 0 10%;
            background: linear-gradient(rgba(10, 15, 26, 0.6), rgba(10, 15, 26, 0.9)), url('https://images.unsplash.com/photo-1581091226825-a6a2a5aee158?q=80&w=1920');
            background-size: cover; background-position: center;
        }
        .hero h1 { font-size: clamp(2.5rem, 8vw, 5rem); color: white; margin-bottom: 15px; }
        .hero p { font-size: 1.4rem; color: var(--secondary); font-weight: 300; }

        /* --- STATS --- */
        .stats-container {
            max-width: 1200px; margin: -80px auto 0; padding: 0 5%;
            display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 25px; position: relative; z-index: 100;
        }
        .stat-card {
            background: rgba(22, 32, 53, 0.8); backdrop-filter: blur(15px);
            padding: 40px 30px; border-radius: 20px; border: 1px solid rgba(255,255,255,0.1);
            text-align: center; box-shadow: 0 20px 40px rgba(0,0,0,0.3); transition: var(--transition);
        }
        .stat-card h2 { font-size: 3rem; color: white; font-weight: 900; background: linear-gradient(to right, #fff, var(--secondary)); -webkit-background-clip: text; -webkit-text-fill-color: transparent; }
        .stat-card p { font-size: 0.85rem; text-transform: uppercase; letter-spacing: 2px; color: var(--secondary); font-weight: 700; }

        /* --- SECTIONS --- */
        section { padding: 100px 8%; max-width: 1400px; margin: auto; }
        .section-title { font-size: 2.2rem; color: white; margin-bottom: 20px; text-align: center; text-transform: uppercase; letter-spacing: 3px; }
        .section-subtitle { text-align: center; color: #a0aec0; margin-bottom: 60px; max-width: 700px; margin-left: auto; margin-right: auto; }
        .section-title::after { content: ''; display: block; width: 60px; height: 4px; background: var(--primary); margin: 20px auto; border-radius: 2px; }
        
        .content-box { background: var(--glass); padding: 50px; border-radius: 30px; border: 1px solid rgba(255,255,255,0.05); }

        /* --- DIRECTEUR --- */
        .director-box { display: grid; grid-template-columns: 1fr 2fr; gap: 60px; align-items: center; }
        .director-photo { width: 100%; max-width: 350px; border-radius: 25px; border: 2px solid rgba(0,198,255,0.3); }
        .director-name { color: white; font-size: 1.5rem; font-weight: 800; margin-top: 20px; }
        .director-title { color: var(--secondary); font-size: 0.8rem; text-transform: uppercase; }

        /* --- GRID CARDS (FORMATIONS & SERVICES) --- */
        .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(320px, 1fr)); gap: 35px; }
        .card { background: rgba(255,255,255,0.02); padding: 45px; border-radius: 25px; border: 1px solid rgba(255,255,255,0.05); transition: var(--transition); }
        .card:hover { transform: translateY(-12px); border-color: var(--secondary); background: rgba(255,255,255,0.04); }
        .card i { font-size: 2.8rem; color: var(--secondary); margin-bottom: 25px; display: block; }
        .card h3 { color: white; font-size: 1.5rem; margin-bottom: 20px; }
        .card ul li { font-size: 0.95rem; margin-bottom: 12px; color: #a0aec0; padding-left: 30px; position: relative; list-style: none; }
        .card ul li::before { content: '\f058'; font-family: 'Font Awesome 5 Free'; font-weight: 900; position: absolute; left: 0; color: var(--primary); }

        /* --- ACTUALITÉS --- */
        .news-card { background: var(--darker); border-radius: 25px; overflow: hidden; border: 1px solid rgba(255,255,255,0.05); transition: 0.4s; }
        .news-card:hover { border-color: var(--secondary); }
        .news-img { width: 100%; height: 230px; background-size: cover; background-position: center; position: relative; }
        .news-content { padding: 30px; }
        .news-date { color: var(--secondary); font-size: 0.75rem; font-weight: 800; text-transform: uppercase; letter-spacing: 1px; }

        /* --- ÉQUIPE (SLIDER) --- */
        .team-wrapper { position: relative; overflow: hidden; padding: 10px 0; }
        .team-slider { display: flex; gap: 25px; transition: transform 0.6s cubic-bezier(0.23, 1, 0.32, 1); }
        .team-member { 
            flex: 0 0 calc(33.333% - 17px); 
            background: rgba(255,255,255,0.03); 
            padding: 40px 20px; 
            border-radius: 25px; 
            text-align: center; 
            border: 1px solid rgba(255,255,255,0.05);
            transition: var(--transition);
        }
        .team-member:hover { transform: scale(1.05); background: rgba(255,255,255,0.07); border-color: var(--secondary); }
        .member-img { width: 120px; height: 120px; border-radius: 50%; object-fit: cover; margin: 0 auto 20px; border: 3px solid var(--primary); padding: 5px; }
        .team-member-name { color: white; font-size: 1.4rem; font-weight: bold; margin-bottom: 5px; }
        .team-member-job { color: var(--secondary); font-size: 0.9rem; text-transform: uppercase; font-weight: 600; }

        .nav-arrows { display: flex; justify-content: center; gap: 20px; margin-top: 40px; }
        .arrow { width: 50px; height: 50px; border-radius: 50%; background: var(--primary); color: white; display: flex; align-items: center; justify-content: center; cursor: pointer; border: none; transition: 0.3s; }
        .arrow:hover { background: var(--secondary); }

        /* --- FOOTER --- */
        footer { background: var(--darker); padding: 100px 8% 40px; border-top: 1px solid rgba(255,255,255,0.05); }
        .footer-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 60px; }
        .contact-list li { margin-bottom: 25px; display: flex; align-items: center; gap: 20px; color: #a0aec0; list-style: none; }
        .contact-list i { color: var(--secondary); font-size: 1.2rem; background: rgba(0,198,255,0.1); padding: 12px; border-radius: 12px; }

        .btn {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white; padding: 16px 40px; border-radius: 50px; text-decoration: none;
            display: inline-block; font-weight: 700; text-transform: uppercase; transition: 0.3s; border: none; cursor: pointer;
        }

        @media (max-width: 992px) { .director-box { grid-template-columns: 1fr; text-align: center; } .team-member { flex: 0 0 calc(50% - 13px); } }
        @media (max-width: 600px) { .team-member { flex: 0 0 100%; } }
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
    <button class="menu-btn" onclick="toggleMenu()"><i class="fas fa-bars"></i></button>
</header>

<div class="nav-overlay" id="navOverlay">
    <i class="fas fa-times close-menu" onclick="toggleMenu()"></i>
    <a href="#accueil" onclick="toggleMenu()">Accueil</a>
    <a href="#propos" onclick="toggleMenu()">À Propos</a>
    <a href="#formations" onclick="toggleMenu()">Formations</a>
    <a href="#services" onclick="toggleMenu()">Services</a>
    <a href="#actualites" onclick="toggleMenu()">Actualités</a>
    <a href="#equipe" onclick="toggleMenu()">Équipe</a>
    <a href="#contact" onclick="toggleMenu()">Contact</a>
</div>

<section class="hero" id="accueil">
    <h1 data-aos="fade-down" data-aos-duration="1200">CENTEC GEO</h1>
    <p data-aos="fade-up" data-aos-delay="400">Maîtriser la géomatique pour mieux comprendre et gérer les territoires</p>
</section>

<div class="stats-container">
    <div class="stat-card" data-aos="zoom-in">
        <h2>+500</h2>
        <p>Professionnels Formés</p>
    </div>
    <div class="stat-card" data-aos="zoom-in" data-aos-delay="200">
        <h2>+120</h2>
        <p>Missions Drones</p>
    </div>
    <div class="stat-card" data-aos="zoom-in" data-aos-delay="400">
        <h2>25</h2>
        <p>Partenaires Publics</p>
    </div>
</div>

<section id="propos">
    <div class="content-box director-box" data-aos="fade-up">
        <div style="text-align: center;">
            <img src="photo_wilfried_codjo.jpg" alt="Wilfried Codjo" class="director-photo">
            <div class="director-name">WILFRIED CODJO</div>
            <div class="director-title">GÉOMATICIEN - EXPERT PHOTOGRAMMÉTRIE</div>
        </div>
        <div>
            <h2 style="color: var(--secondary); margin-bottom: 25px;">Le Mot du Directeur</h2>
            <p style="font-style: italic; font-size: 1.15rem; color: #fff; border-left: 4px solid var(--primary); padding-left: 25px; margin-bottom: 25px;">
                "Transformer chaque donnée territoriale en une décision stratégique éclairée est au cœur de notre engagement."
            </p>
            <p style="color: #a0aec0;">Le <strong>CENTEC GEO</strong> est une institution de référence en Côte d'Ivoire. Nous formons les cadres de demain aux outils SIG et à la télédétection.</p>
        </div>
    </div>
</section>

<section id="formations">
    <h2 class="section-title" data-aos="fade-up">Nos Formations</h2>
    <div class="grid">
        <div class="card" data-aos="fade-up">
            <i class="fas fa-map-marked-alt"></i>
            <h3>DIGI MAP</h3>
            <ul>
                <li>Maîtrise de QGIS & ArcGIS Pro</li>
                <li>Conception cartographique</li>
                <li>Analyse spatiale complexe</li>
            </ul>
        </div>
        <div class="card" data-aos="fade-up" data-aos-delay="200">
            <i class="fas fa-satellite"></i>
            <h3>TeleSense Pro</h3>
            <ul>
                <li>Télédétection & Imagerie</li>
                <li>Traitement spectral</li>
                <li>Suivi environnemental</li>
            </ul>
        </div>
        <div class="card" data-aos="fade-up" data-aos-delay="400">
            <i class="fas fa-mobile-alt"></i>
            <h3>E-Enquêteur</h3>
            <ul>
                <li>Collecte mobile (Kobo/ODK)</li>
                <li>Gestion de bases de données</li>
                <li>Inventaires géolocalisés</li>
            </ul>
        </div>
    </div>
</section>

<section id="services">
    <h2 class="section-title" data-aos="fade-up">Nos Services</h2>
    <div class="grid">
        <div class="card" data-aos="zoom-in">
            <i class="fas fa-paper-plane"></i>
            <h3>Photogrammétrie</h3>
            <p>Modélisation 3D et relevés par drones haute résolution pour vos projets.</p>
        </div>
        <div class="card" data-aos="zoom-in" data-aos-delay="200">
            <i class="fas fa-draw-polygon"></i>
            <h3>Solutions SIG</h3>
            <p>Conception et implémentation de systèmes d'information sur mesure.</p>
        </div>
        <div class="card" data-aos="zoom-in" data-aos-delay="400">
            <i class="fas fa-server"></i>
            <h3>Ingénierie DATA</h3>
            <p>Administration de bases de données spatiales pour les collectivités.</p>
        </div>
    </div>
</section>

<section id="actualites">
    <h2 class="section-title" data-aos="fade-up">Actualités</h2>
    <div class="grid">
        <div class="news-card" data-aos="fade-up">
            <div class="news-img" style="background-image: url('https://images.unsplash.com/photo-1473960104312-3c712850684b'); height: 230px; background-size: cover;"></div>
            <div class="news-content">
                <span class="news-date">Avril 2026</span>
                <h4 style="color:white; margin:15px 0;">L'IA et la Géomatique</h4>
                <p style="font-size:0.9rem; color: #a0aec0;">Intégration de l'intelligence artificielle pour l'analyse prédictive.</p>
                <a href="#" style="color:var(--secondary); text-decoration:none; font-weight:bold; display:block; margin-top:15px;">LIRE PLUS →</a>
            </div>
        </div>
        <div class="news-card" data-aos="fade-up" data-aos-delay="200">
            <div class="news-img" style="background-image: url('https://images.unsplash.com/photo-1508614589041-895b88991e3e'); height: 230px; background-size: cover;"></div>
            <div class="news-content">
                <span class="news-date">Mars 2026</span>
                <h4 style="color:white; margin:15px 0;">Projet Cadastre</h4>
                <p style="font-size:0.9rem; color: #a0aec0;">Signature d'une convention pour la numérisation foncière.</p>
                <a href="#" style="color:var(--secondary); text-decoration:none; font-weight:bold; display:block; margin-top:15px;">LIRE PLUS →</a>
            </div>
        </div>
    </div>
</section>

<section id="equipe">
    <h2 class="section-title" data-aos="fade-up">Notre Équipe</h2>
    <p class="section-subtitle" data-aos="fade-up">Bienvenue dans notre section dédiée à l'équipe. Nous sommes passionnés par notre travail et heureux de vous présenter les membres qui composent notre équipe dynamique.</p>
    
    <div class="team-wrapper">
        <div class="team-slider" id="slider">
            <div class="team-member" data-aos="fade-up">
                <img src="https://i.pravatar.cc/150?u=alice" alt="Alice" class="member-img">
                <div class="team-member-name">Alice Dupont</div>
                <div class="team-member-job">Chef de Projet</div>
            </div>
            <div class="team-member" data-aos="fade-up" data-aos-delay="100">
                <img src="https://i.pravatar.cc/150?u=bob" alt="Bob" class="member-img">
                <div class="team-member-name">Bob Martin</div>
                <div class="team-member-job">Développeur Frontend</div>
            </div>
            <div class="team-member" data-aos="fade-up" data-aos-delay="200">
                <img src="https://i.pravatar.cc/150?u=carla" alt="Carla" class="member-img">
                <div class="team-member-name">Carla Jean</div>
                <div class="team-member-job">Designer UI/UX</div>
            </div>
        </div>
    </div>
    
    <div class="nav-arrows">
        <button class="arrow" onclick="moveSlider(-1)"><i class="fas fa-chevron-left"></i></button>
        <button class="arrow" onclick="moveSlider(1)"><i class="fas fa-chevron-right"></i></button>
    </div>

    <p style="text-align: center; margin-top: 50px; color: #a0aec0; font-style: italic;">
        Nous espérons que vous apprécierez en apprendre davantage sur notre équipe et notre culture de collaboration et d'innovation.
    </p>
</section>

<footer id="contact">
    <div class="footer-grid">
        <div>
            <h2 style="color: white; margin-bottom: 25px;">CENTEC GEO</h2>
            <p style="color: #a0aec0; margin-bottom: 30px;">L’expertise géospatiale de référence en Côte d'Ivoire.</p>
            <div style="display: flex; gap: 15px;">
                <a href="#" style="color: white; font-size: 1.5rem;"><i class="fab fa-linkedin"></i></a>
                <a href="#" style="color: white; font-size: 1.5rem;"><i class="fab fa-facebook"></i></a>
            </div>
        </div>
        <div>
            <h3 style="color: white; margin-bottom: 30px;">Contact</h3>
            <ul class="contact-list">
                <li><i class="fas fa-map-marker-alt"></i> Cocody 2 Plateaux, Abidjan</li>
                <li><i class="fas fa-phone-alt"></i> +225 00 00 00 00</li>
                <li><i class="fas fa-envelope"></i> contact@centec.ci</li>
            </ul>
        </div>
        <div style="text-align: center;">
            <h3 style="color: white; margin-bottom: 30px;">Partenariat</h3>
            <a href="mailto:contact@centec.ci" class="btn">Devenir Partenaire</a>
        </div>
    </div>
    <div style="text-align: center; margin-top: 50px; color: #4a5568; font-size: 0.8rem; border-top: 1px solid rgba(255,255,255,0.05); padding-top: 30px;">
        © 2026 CENTEC GEO – Expertise en Géomatique
    </div>
</footer>

<script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
<script>
    AOS.init({ duration: 1000, once: true });
    function toggleMenu() { document.getElementById('navOverlay').classList.toggle('active'); }

    let currentScroll = 0;
    const slider = document.getElementById('slider');
    function moveSlider(direction) {
        const cardWidth = document.querySelector('.team-member').offsetWidth + 25;
        const maxScroll = slider.scrollWidth - slider.parentElement.offsetWidth;
        currentScroll += direction * cardWidth;
        if (currentScroll < 0) currentScroll = 0;
        if (currentScroll > maxScroll) currentScroll = maxScroll;
        slider.style.transform = `translateX(-${currentScroll}px)`;
    }
</script>

</body>
</html>
