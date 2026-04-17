<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CENTEC GEO – Centre National d’Étude en Territoire et Cartographie CI</title>

    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">

    <style>
        :root {
            --primary: #0b5ed7;
            --secondary: #00c6ff;
            --dark: #050505;
            --glass: rgba(255, 255, 255, 0.05);
            --transition: all 0.3s ease;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            background: var(--dark);
            color: #e0e0e0;
            line-height: 1.7;
            overflow-x: hidden;
        }

        /* --- LOADER --- */
        #loader {
            position: fixed; width: 100%; height: 100%; background: #000;
            display: flex; align-items: center; justify-content: center; z-index: 9999;
        }
        #loader span { color: white; letter-spacing: 5px; animation: pulse 1.5s infinite; font-weight: bold;}
        @keyframes pulse { 0%, 100% { opacity: 0.3; } 50% { opacity: 1; } }

        /* --- HEADER & LOGO --- */
        header {
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            padding: 10px 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: rgba(0, 0, 0, 0.9);
            backdrop-filter: blur(15px);
            border-bottom: 1px solid rgba(255,255,255,0.1);
        }

        .logo-container {
            display: flex;
            align-items: center;
            text-decoration: none;
            gap: 15px;
        }

        .logo-container img {
            height: 70px; 
            width: auto;
        }

        .logo-text {
            display: flex;
            flex-direction: column;
            border-left: 1px solid rgba(255,255,255,0.3);
            padding-left: 15px;
        }

        .logo-text h2 {
            color: white;
            font-size: 1.3rem;
            font-weight: 800;
            letter-spacing: 1px;
            margin: 0;
            line-height: 1.1;
        }

        .logo-text span {
            color: var(--secondary);
            font-size: 0.65rem;
            font-weight: 600;
            text-transform: uppercase;
            line-height: 1.2;
            margin-top: 4px;
        }

        /* --- NAVIGATION --- */
        nav ul { display: flex; gap: 25px; list-style: none; }
        nav a { 
            color: white; 
            text-decoration: none; 
            font-size: 0.85rem; 
            font-weight: 600; 
            text-transform: uppercase;
            transition: var(--transition);
        }
        nav a:hover { color: var(--secondary); }

        .menu-toggle { display: none; color: white; font-size: 1.5rem; cursor: pointer; }

        /* --- HERO SECTION --- */
        .hero {
            height: 85vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 0 10%;
            background: linear-gradient(rgba(0,0,0,0.7), rgba(0,0,0,0.8)), 
                        url('https://images.unsplash.com/photo-1581091226825-a6a2a5aee158?auto=format&fit=crop&q=80&w=1920');
            background-size: cover;
            background-position: center;
        }

        .hero h1 { font-size: clamp(2rem, 6vw, 4rem); margin-bottom: 20px; color: white; }
        .hero p { font-size: 1.3rem; color: var(--secondary); max-width: 900px; font-weight: 300; }

        /* --- SECTIONS COMMUNES --- */
        section { padding: 100px 8%; max-width: 1400px; margin: auto; }
        .section-title { font-size: 2.2rem; color: white; margin-bottom: 50px; text-align: center; text-transform: uppercase; }
        .section-title::after { content: ''; display: block; width: 80px; height: 4px; background: var(--primary); margin: 15px auto; }

        .content-box {
            background: var(--glass);
            padding: 50px;
            border-radius: 20px;
            border: 1px solid rgba(255,255,255,0.1);
            box-shadow: 0 20px 40px rgba(0,0,0,0.3);
        }

        .highlight { color: var(--secondary); font-weight: 600; }

        /* --- GRID & CARDS --- */
        .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(320px, 1fr)); gap: 30px; }
        .card {
            background: rgba(255,255,255,0.03);
            padding: 40px;
            border-radius: 15px;
            border: 1px solid rgba(255,255,255,0.05);
            transition: var(--transition);
        }
        .card:hover { 
            background: rgba(255,255,255,0.07); 
            transform: translateY(-10px); 
            border-color: var(--secondary); 
        }
        .card i { font-size: 2.5rem; color: var(--secondary); margin-bottom: 20px; display: block; }
        .card h3 { color: white; margin-bottom: 15px; font-size: 1.4rem; }
        .card ul { list-style: none; margin-top: 15px; }
        .card ul li { font-size: 0.9rem; margin-bottom: 10px; color: #ccc; position: relative; padding-left: 20px; }
        .card ul li::before { content: '→'; position: absolute; left: 0; color: var(--primary); }

        /* --- BOUTONS --- */
        .btn {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            padding: 15px 35px;
            border-radius: 5px;
            text-decoration: none;
            display: inline-block;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 1px;
            transition: 0.3s;
            border: none;
            cursor: pointer;
        }
        .btn:hover { transform: scale(1.05); box-shadow: 0 10px 20px rgba(0, 198, 255, 0.3); }

        /* --- NOUVELLE SECTION : MOT DU DIRECTEUR --- */
        .director-box {
            display: grid;
            grid-template-columns: 1fr 2fr;
            gap: 40px;
            align-items: center;
        }
        .director-photo {
            width: 100%;
            height: auto;
            border-radius: 15px;
            border: 5px solid rgba(255,255,255,0.1);
            object-fit: cover;
        }
        .director-text {
            font-style: italic;
            color: #ddd;
        }
        .director-signature {
            margin-top: 20px;
            font-weight: bold;
            color: white;
            font-style: normal;
        }

        /* --- NOUVELLE SECTION : POURQUOI NOUS CHOISIR --- */
        .why-us-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
        }
        .why-us-card {
            background: rgba(255,255,255,0.02);
            padding: 30px;
            border-radius: 10px;
            border: 1px solid rgba(255,255,255,0.05);
            text-align: center;
            transition: var(--transition);
        }
        .why-us-card:hover {
            border-color: var(--primary);
            background: rgba(255,255,255,0.05);
        }
        .why-us-card i {
            font-size: 2rem;
            color: var(--primary);
            margin-bottom: 15px;
        }
        .why-us-card h4 {
            color: white;
            margin-bottom: 10px;
        }

        /* --- NOUVELLE SECTION : NOTRE EQUIPE (CARROUSEL) --- */
        #equipe {
            overflow: hidden; /* Important pour masquer ce qui dépasse */
            position: relative;
            padding-bottom: 60px; /* Espace pour les contrôles si besoin */
        }
        .team-slider-container {
            width: 100%;
            overflow: hidden;
            cursor: grab;
        }
        .team-slider {
            display: flex;
            gap: 30px;
            transition: transform 0.5s ease-out; /* Animation fluide */
        }
        .team-member {
            flex: 0 0 calc(25% - 22.5px); /* 4 membres par ligne sur grand écran */
            background: var(--glass);
            border-radius: 15px;
            padding: 20px;
            text-align: center;
            border: 1px solid rgba(255,255,255,0.05);
        }
        .team-member img {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            object-fit: cover;
            margin-bottom: 15px;
            border: 3px solid var(--primary);
        }
        .team-member h4 { color: white; margin-bottom: 5px; }
        .team-member p { color: var(--secondary); font-size: 0.8rem; text-transform: uppercase; font-weight: bold;}

        /* --- FOOTER --- */
        footer { background: #000; padding: 60px 5%; text-align: center; border-top: 1px solid #222; }
        .social-links i { margin: 0 15px; font-size: 1.5rem; cursor: pointer; transition: 0.3s; }
        .social-links i:hover { color: var(--secondary); }

        /* --- RESPONSIVE --- */
        @media (max-width: 1024px) {
            .logo-text { display: none; }
            .team-member { flex: 0 0 calc(33.33% - 20px); } /* 3 membres sur tablette */
        }
        @media (max-width: 768px) {
            header { padding: 10px 20px; }
            nav ul { display: none; }
            .hero h1 { font-size: 2.2rem; }
            .director-box { grid-template-columns: 1fr; text-align: center; }
            .director-photo { max-width: 200px; margin: auto; }
            .team-member { flex: 0 0 calc(50% - 15px); } /* 2 membres sur grand mobile */
        }
        @media (max-width: 480px) {
            .team-member { flex: 0 0 100%; } /* 1 membre sur petit mobile */
        }
    </style>
</head>
<body>

<div id="loader"><span>CENTEC GEO...</span></div>

<header>
    <a href="#accueil" class="logo-container">
        <img src="1000442449.jpg" alt="CENTEC GEO Logo">
        <div class="logo-text">
            <h2>CENTEC GEO</h2>
            <span>Centre National d’Étude en<br>Territoire et Cartographie CI</span>
        </div>
    </a>
    
    <i class="fas fa-bars menu-toggle"></i>
    
    <nav>
        <ul>
            <li><a href="#accueil">Accueil</a></li>
            <li><a href="#propos">À Propos</a></li>
            <li><a href="#formations">Formations</a></li>
            <li><a href="#services">Services</a></li>
            <li><a href="#equipe">Équipe</a></li>
            <li><a href="#contact">Contact</a></li>
        </ul>
    </nav>
</header>

<section class="hero" id="accueil">
    <h1>CENTEC GEO</h1>
    <p>Maîtriser la géomatique pour mieux comprendre et gérer les territoires</p>
    <a href="#formations" class="btn" style="margin-top: 40px;">Nos Certifications</a>
</section>

<section id="propos">
    <div class="content-box" style="margin-bottom: 40px;">
        <h2 style="color: var(--secondary); margin-bottom: 25px;">Bienvenue au CENTEC</h2>
        <p>Le <strong>Centre National d’Étude en Territoire et Cartographie (CENTEC)</strong> est une structure spécialisée dans la <strong>formation professionnelle et l’expertise en géomatique appliquée</strong>.</p>
        <br>
        <p>Le centre intervient notamment dans les domaines de la <span class="highlight">cartographie numérique, des systèmes d’information graphique (SIG), de la télédétection, de la collecte de données géolocalisées, du pilotage de drone et photogrammétrie</span>.</p>
    </div>

    <div class="content-box director-box">
        <img src="director-placeholder.jpg" alt="Photo du Directeur" class="director-photo">
        <div>
            <h3>Le Mot du Directeur</h3>
            <br>
            <p class="director-text">"Notre ambition est de démocratiser l'accès aux technologies géospatiales de pointe. Nous formons des experts capables de transformer la donnée territoriale en levier de développement durable pour la Côte d'Ivoire et la sous-région."</p>
            <p class="director-signature">Nom du Directeur<br>Directeur Général</p>
        </div>
    </div>
</section>

<section id="why-us" style="background: rgba(255,255,255,0.01);">
    <h2 class="section-title">Pourquoi nous choisir ?</h2>
    <div class="why-us-grid">
        <div class="why-us-card">
            <i class="fas fa-certificate"></i>
            <h4>Certifications Reconnues</h4>
            <p>Des programmes validés par des experts du secteur.</p>
        </div>
        <div class="why-us-card">
            <i class="fas fa-chalkboard-teacher"></i>
            <h4>Experts Praticiens</h4>
            <p>Formateurs issus du monde professionnel.</p>
        </div>
        <div class="why-us-card">
            <i class="fas fa-drone"></i>
            <h4>Équipements de Pointe</h4>
            <p>Accès aux dernières technologies (Drones, GNSS, SIG).</p>
        </div>
        <div class="why-us-card">
            <i class="fas fa-handshake"></i>
            <h4>Accompagnement Pro</h4>
            <p>Suivi post-formation et insertion facilitée.</p>
        </div>
    </div>
</section>

<section id="formations">
    <h2 class="section-title">Nos Programmes de Formation</h2>
    <div class="grid">
        <div class="card">
            <i class="fas fa-map-marked-alt"></i>
            <h3>DIGI MAP</h3>
            <p>Programme de Certification en Cartographie Numérique et Système d’Information Géographique.</p>
            <ul>
                <li>Maîtrise de la cartographie numérique</li>
                <li>Conception de cartes thématiques</li>
                <li>Production de supports d'aide à la décision</li>
            </ul>
        </div>
        <div class="card">
            <i class="fas fa-satellite"></i>
            <h3>TeleSense Pro</h3>
            <p>Programme d’Excellence en Télédétection Appliquée pour l'analyse des images satellites.</p>
            <ul>
                <li>Analyse d'images satellites</li>
                <li>Suivi des changements territoriaux</li>
                <li>Études environnementales</li>
            </ul>
        </div>
        <div class="card">
            <i class="fas fa-mobile-alt"></i>
            <h3>E-Enquêteur</h3>
            <p>Programme de renforcement des compétences en collecte numérique de données de terrain.</p>
            <ul>
                <li>Collecte géolocalisée</li>
                <li>Gestion des enquêtes numériques</li>
                <li>Outils modernes de terrain</li>
            </ul>
        </div>
        <div class="card">
            <i class="fas fa-layer-group"></i>
            <h3>GeoSkill</h3>
            <p>Programme Professionnel intensif pour maîtriser les outils essentiels de l’analyse spatiale.</p>
        </div>
    </div>
</section>

<section id="services" style="background: rgba(255,255,255,0.01);">
    <h2 class="section-title">Services et Études</h2>
    <div class="grid">
        <div class="card">
            <h3>Collecte de Données</h3>
            <p>Mise en place de systèmes modernes de collecte et de gestion de données géographiques.</p>
        </div>
        <div class="card">
            <h3>Cartographie Thématique</h3>
            <p>Réalisation de cartes analytiques pour représenter les réalités et les dynamiques spatiales.</p>
        </div>
        <div class="card">
            <h3>Analyse Géospatiale</h3>
            <p>Exploitation des données pour comprendre les territoires et orienter les décisions stratégiques.</p>
        </div>
    </div>
</section>

<section id="equipe">
    <h2 class="section-title">Notre Équipe</h2>
    <div class="team-slider-container">
        <div class="team-slider">
            <div class="team-member">
                <img src="profile-placeholder.jpg" alt="Nom du Membre">
                <h4>Nom du Membre</h4>
                <p>Poste / Service</p>
            </div>
            <div class="team-member">
                <img src="profile-placeholder.jpg" alt="Nom du Membre">
                <h4>Nom du Membre</h4>
                <p>Poste / Service</p>
            </div>
            <div class="team-member">
                <img src="profile-placeholder.jpg" alt="Nom du Membre">
                <h4>Nom du Membre</h4>
                <p>Poste / Service</p>
            </div>
            <div class="team-member">
                <img src="profile-placeholder.jpg" alt="Nom du Membre">
                <h4>Nom du Membre</h4>
                <p>Poste / Service</p>
            </div>
            <div class="team-member">
                <img src="profile-placeholder.jpg" alt="Nom du Membre">
                <h4>Nom du Membre 5</h4>
                <p>Poste / Service</p>
            </div>
            <div class="team-member">
                <img src="profile-placeholder.jpg" alt="Nom du Membre">
                <h4>Nom du Membre 6</h4>
                <p>Poste / Service</p>
            </div>
        </div>
    </div>
</section>

<section id="contact">
    <h2 class="section-title">Devenir Partenaire</h2>
    <div class="content-box" style="text-align: center;">
        <p style="margin-bottom: 30px;">Nous accompagnons les administrations, les bureaux d’études et les ONG dans l’intégration de la géomatique au cœur de leurs stratégies.</p>
        <a href="mailto:contact@centec.ci" class="btn">Envoyer une demande d'étude</a>
    </div>
</section>

<footer>
    <p>© 2026 CENTEC GEO – Excellence en Géomatique Appliquée</p>
    <p style="font-size: 0.75rem; color: #555; margin-top: 10px;">Centre National d’Étude en Territoire et Cartographie CI</p>
    <div class="social-links" style="margin-top: 20px;">
        <i class="fab fa-linkedin"></i>
        <i class="fab fa-facebook"></i>
    </div>
</footer>

<script>
    // Suppression du loader
    window.addEventListener("load", () => {
        const loader = document.getElementById("loader");
        loader.style.opacity = "0";
        setTimeout(() => loader.style.display = "none", 500);
    });

    // Animation simple au scroll (Observer)
    const observer = new IntersectionObserver(entries => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                entry.target.style.opacity = 1;
                entry.target.style.transform = "translateY(0)";
            }
        });
    });

    document.querySelectorAll('section, .card, .content-box, .why-us-card').forEach(el => {
        el.style.opacity = 0;
        el.style.transform = "translateY(20px)";
        el.style.transition = "all 0.6s ease-out";
        observer.observe(el);
    });

    // --- JAVASCRIPT : CARROUSEL EQUIPE (INFINI AUTOMATIQUE) ---
    const slider = document.querySelector('.team-slider');
    const members = document.querySelectorAll('.team-member');
    
    // Dupliquer les membres pour l'effet infini
    members.forEach(member => {
        const clone = member.cloneNode(true);
        slider.appendChild(clone);
    });

    let currentTranslate = 0;
    const scrollSpeed = 1; // Ajuste la vitesse ici (plus bas = plus lent)

    function animateSlider() {
        currentTranslate -= scrollSpeed;
        
        // Calculer la largeur totale d'un set de membres (y compris le gap)
        const totalWidth = (members[0].offsetWidth + 30) * members.length;

        // Si on a fait défiler tout le premier set, on reset sans transition visuelle
        if (Math.abs(currentTranslate) >= totalWidth) {
            currentTranslate = 0;
        }

        slider.style.transform = `translateX(${currentTranslate}px)`;
        requestAnimationFrame(animateSlider); // Boucle d'animation fluide
    }

    // Lancer l'animation une fois que tout est chargé
    window.addEventListener('load', animateSlider);

</script>

</body>
</html>
