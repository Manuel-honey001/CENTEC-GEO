<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CENTEC – Ingénierie Géospatiale</title>

    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">

    <style>
        :root {
            --primary: #0b5ed7;
            --secondary: #00c6ff;
            --dark: #0a0a0a;
            --glass: rgba(255, 255, 255, 0.08);
            --transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: #0a0a0a;
            color: white;
            overflow-x: hidden;
            line-height: 1.6;
        }

        /* LOADER */
        #loader {
            position: fixed;
            width: 100%;
            height: 100%;
            background: #000;
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 9999;
        }

        #loader span {
            font-size: 1.5rem;
            letter-spacing: 2px;
            animation: pulse 1.5s infinite;
        }

        @keyframes pulse {
            0%, 100% { opacity: 0.3; transform: scale(0.95); }
            50% { opacity: 1; transform: scale(1); }
        }

        /* HEADER */
        header {
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            padding: 20px 5%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: rgba(0, 0, 0, 0.7);
            backdrop-filter: blur(15px);
            border-bottom: 1px solid rgba(255,255,255,0.1);
        }

        nav ul {
            display: flex;
            gap: 25px;
            list-style: none;
        }

        nav a {
            color: white;
            text-decoration: none;
            font-weight: 500;
            font-size: 0.9rem;
            transition: 0.3s;
        }

        nav a:hover { color: var(--secondary); }

        .menu-toggle {
            display: none;
            font-size: 24px;
            cursor: pointer;
        }

        /* HERO */
        .hero {
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            background: radial-gradient(circle at center, #001f3f 0%, #000 100%);
            padding: 0 20px;
        }

        .hero h1 {
            font-size: clamp(2rem, 8vw, 4rem);
            background: linear-gradient(90deg, #00c6ff, #0b5ed7);
            -webkit-background-clip: text;
            color: transparent;
            margin-bottom: 15px;
        }

        .btn {
            background: linear-gradient(135deg, #0b5ed7, #00c6ff);
            padding: 14px 30px;
            border-radius: 50px;
            text-decoration: none;
            color: white;
            font-weight: bold;
            margin-top: 25px;
            display: inline-block;
            transition: var(--transition);
            border: none;
            cursor: pointer;
        }

        .btn:hover {
            transform: scale(1.05);
            box-shadow: 0 10px 20px rgba(11, 94, 215, 0.4);
        }

        /* STATS */
        .stats {
            display: flex;
            justify-content: center;
            gap: 50px;
            padding: 60px 20px;
            background: rgba(255,255,255,0.02);
            text-align: center;
            flex-wrap: wrap;
        }

        .stats h2 { color: var(--secondary); font-size: 2.5rem; }

        /* SECTIONS */
        section {
            padding: 100px 5%;
            max-width: 1200px;
            margin: auto;
        }

        h2.section-title {
            text-align: center;
            margin-bottom: 50px;
            font-size: 2.5rem;
            position: relative;
        }

        /* DIRECTOR SECTION */
        .director-container {
            display: grid;
            grid-template-columns: 1fr 1.5fr;
            gap: 50px;
            align-items: center;
            background: var(--glass);
            padding: 40px;
            border-radius: 25px;
            border: 1px solid rgba(255,255,255,0.1);
        }

        .director-image img {
            width: 100%;
            border-radius: 20px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.5);
        }

        .director-text h2 { color: var(--secondary); margin: 10px 0; }
        .director-text p { font-style: italic; color: #ddd; margin-bottom: 20px; }
        .director-info strong { display: block; font-size: 1.2rem; color: white; }
        .director-info span { color: var(--secondary); font-size: 0.9rem; }

        /* GRID & CARDS */
        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 25px;
        }

        .card {
            background: var(--glass);
            padding: 30px;
            border-radius: 20px;
            border: 1px solid rgba(255,255,255,0.1);
            transition: var(--transition);
            text-align: center;
        }

        .card:hover {
            transform: translateY(-10px);
            background: rgba(255,255,255,0.12);
            border-color: var(--secondary);
        }

        .card i {
            font-size: 2.5rem;
            color: var(--secondary);
            margin-bottom: 20px;
        }

        /* FORM */
        form input, form textarea {
            width: 100%;
            padding: 15px;
            margin: 10px 0;
            background: var(--glass);
            border: 1px solid rgba(255,255,255,0.2);
            color: white;
            border-radius: 10px;
        }

        /* FOOTER */
        footer {
            padding: 50px;
            text-align: center;
            background: #050505;
        }

        .social-links { margin: 20px 0; font-size: 1.5rem; }
        .social-links i { margin: 0 15px; cursor: pointer; transition: 0.3s; }
        .social-links i:hover { color: var(--secondary); }

        /* WHATSAPP */
        .cta-wa {
            position: fixed;
            bottom: 30px;
            right: 30px;
            background: #25D366;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 30px;
            text-decoration: none;
            z-index: 1000;
            box-shadow: 0 10px 20px rgba(0,0,0,0.3);
        }

        /* RESPONSIVE */
        @media(max-width: 768px) {
            nav ul {
                display: none;
                flex-direction: column;
                position: absolute;
                top: 70px;
                right: 5%;
                background: #111;
                width: 200px;
                padding: 20px;
                border-radius: 15px;
            }
            nav ul.active { display: flex; }
            .menu-toggle { display: block; }
            .director-container { grid-template-columns: 1fr; text-align: center; }
        }
    </style>
</head>
<body>

    <div id="loader"><span>CENTEC...</span></div>

    <header>
        <h2 style="letter-spacing: 2px;">CENTEC</h2>
        <i class="fas fa-bars menu-toggle"></i>
        <nav>
            <ul>
                <li><a href="#about">À propos</a></li>
                <li><a href="#catalogue">Catalogue</a></li>
                <li><a href="#missions">Missions</a></li>
                <li><a href="#livrables">Livrables</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
        </nav>
    </header>

    <section class="hero">
        <h1>Géomatique & Ingénierie</h1>
        <p>Expertise en Drone, SIG et Analyse Spatiale de précision.</p>
        <a href="#catalogue" class="btn">Nos Formations</a>
    </section>

    <div class="stats">
        <div><h2>500+</h2><p>Étudiants formés</p></div>
        <div><h2>95%</h2><p>Taux de réussite</p></div>
        <div><h2>20+</h2><p>Partenaires Pros</p></div>
    </div>

    <section id="about">
        <div class="director-container">
            <div class="director-image">
                <img src="https://images.unsplash.com/photo-1560250097-0b93528c311a?auto=format&fit=crop&q=80&w=400" alt="Directeur Général">
            </div>
            <div class="director-text">
                <span class="btn" style="padding: 5px 15px; font-size: 0.7rem; margin: 0;">MOT DU DIRECTEUR</span>
                <h2>L'innovation au service du territoire</h2>
                <p>"Notre vision est de démocratiser l'accès aux technologies géospatiales de pointe. Chez CENTEC, nous formons une nouvelle génération d'ingénieurs capables de relever les défis cartographiques du 21ème siècle."</p>
                <div class="director-info">
                    <strong>Jean-Marc Kouassi</strong>
                    <span>Directeur Général / Expert SIG</span>
                </div>
            </div>
        </div>
    </section>

    <section id="catalogue">
        <h2 class="section-title">Notre Catalogue</h2>
        <div class="grid">
            <div class="card">
                <i class="fas fa-map-marked-alt"></i>
                <h3>DIGI MAP</h3>
                <p>Maîtrisez la cartographie numérique et les outils SIG modernes.</p>
            </div>
            <div class="card">
                <i class="fas fa-drone"></i>
                <h3>Drone Pro</h3>
                <p>Pilotage et photogrammétrie pour des relevés de haute précision.</p>
            </div>
            <div class="card">
                <i class="fas fa-database"></i>
                <h3>GeoSkill</h3>
                <p>Analyse de données spatiales et gestion de bases de données.</p>
            </div>
        </div>
    </section>

    <section id="missions" style="background: rgba(255,255,255,0.02);">
        <h2 class="section-title">Missions Terrain</h2>
        <div class="card" style="max-width: 800px; margin: auto;">
            <i class="fas fa-mountain-sun"></i>
            <h3>Simulation de levée de terrain</h3>
            <p>Mise en situation réelle avec planification de vol drone et acquisition de données GNSS sur site complexe.</p>
        </div>
    </section>

    <section id="livrables">
        <h2 class="section-title">Livrables Experts</h2>
        <div class="grid">
            <div class="card">
                <i class="fas fa-map"></i>
                <h3>Cartes SIG</h3>
            </div>
            <div class="card">
                <i class="fas fa-images"></i>
                <h3>Orthophotos</h3>
            </div>
            <div class="card">
                <i class="fas fa-layer-group"></i>
                <h3>MNT / MNE</h3>
            </div>
        </div>
    </section>

    <section id="contact">
        <h2 class="section-title">Contactez-nous</h2>
        <form style="max-width: 600px; margin: auto;">
            <input type="text" placeholder="Nom complet" required>
            <input type="email" placeholder="Adresse Email" required>
            <textarea placeholder="Votre message..." rows="5" required></textarea>
            <button type="submit" class="btn" style="width: 100%;">Envoyer le message</button>
        </form>
    </section>

    <a class="cta-wa" href="https://wa.me/225000000000" target="_blank">
        <i class="fab fa-whatsapp"></i>
    </a>

    <footer>
        <p>© 2026 CENTEC – Excellence en Ingénierie Géospatiale</p>
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CENTEC – Centre National d’Étude en Territoire et Cartographie</title>

    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">

    <style>
        :root {
            --primary: #0b5ed7;
            --secondary: #00c6ff;
            --dark: #0a0a0a;
            --glass: rgba(255, 255, 255, 0.05);
            --transition: all 0.3s ease;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            font-family: 'Segoe UI', sans-serif;
            background: #050505;
            color: #e0e0e0;
            line-height: 1.7;
            overflow-x: hidden;
        }

        /* LOADER */
        #loader {
            position: fixed; width: 100%; height: 100%; background: #000;
            display: flex; align-items: center; justify-content: center; z-index: 9999;
        }

        /* HEADER */
        header {
            position: fixed; width: 100%; top: 0; z-index: 1000;
            padding: 15px 5%; display: flex; justify-content: space-between; align-items: center;
            background: rgba(0,0,0,0.8); backdrop-filter: blur(15px); border-bottom: 1px solid rgba(255,255,255,0.1);
        }

        nav ul { display: flex; gap: 20px; list-style: none; }
        nav a { color: white; text-decoration: none; font-size: 0.9rem; font-weight: 500; }
        nav a:hover { color: var(--secondary); }

        /* HERO SECTION */
        .hero {
            height: 80vh; display: flex; flex-direction: column; justify-content: center;
            align-items: center; text-align: center; padding: 0 10%;
            background: linear-gradient(rgba(0,0,0,0.7), rgba(0,0,0,0.7)), url('https://images.unsplash.com/photo-1581091226825-a6a2a5aee158?auto=format&fit=crop&q=80&w=1920');
            background-size: cover; background-position: center;
        }

        .hero h1 { font-size: clamp(1.8rem, 5vw, 3.5rem); margin-bottom: 20px; color: white; line-height: 1.2; }
        .hero p { font-size: 1.2rem; color: var(--secondary); max-width: 800px; font-weight: 300; }

        /* SECTION STYLES */
        section { padding: 80px 8%; max-width: 1300px; margin: auto; }
        .section-title { font-size: 2rem; color: white; margin-bottom: 40px; text-align: center; }
        .section-title::after { content: ''; display: block; width: 60px; height: 3px; background: var(--secondary); margin: 15px auto; }

        /* TEXT CONTENT BOXES */
        .content-box {
            background: var(--glass); padding: 40px; border-radius: 20px;
            border: 1px solid rgba(255,255,255,0.1); margin-bottom: 30px;
        }

        .highlight { color: var(--secondary); font-weight: 600; }

        /* GRID FOR SERVICES/PROGRAMS */
        .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 25px; }
        .card {
            background: rgba(255,255,255,0.03); padding: 30px; border-radius: 15px;
            border: 1px solid rgba(255,255,255,0.05); transition: var(--transition);
        }
        .card:hover { background: rgba(255,255,255,0.08); transform: translateY(-5px); border-color: var(--secondary); }
        .card h3 { color: var(--secondary); margin-bottom: 15px; font-size: 1.3rem; }
        .card ul { list-style: none; margin-top: 15px; }
        .card ul li { font-size: 0.85rem; margin-bottom: 8px; color: #bbb; border-left: 2px solid var(--primary); padding-left: 10px; }

        /* VALUES SECTION */
        .values-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 20px; text-align: center; }
        .value-item i { font-size: 2rem; color: var(--secondary); margin-bottom: 15px; }

        /* CTA BUTTON */
        .btn {
            background: var(--primary); color: white; padding: 12px 30px; border-radius: 5px;
            text-decoration: none; display: inline-block; transition: 0.3s; font-weight: 600; border: none; cursor: pointer;
        }
        .btn:hover { background: var(--secondary); transform: scale(1.05); }

        footer { background: #000; padding: 40px 5%; text-align: center; border-top: 1px solid #222; }

        /* MOBILE */
        @media (max-width: 768px) {
            header { padding: 15px 20px; }
            nav ul { display: none; }
            .hero h1 { font-size: 1.8rem; }
        }
    </style>
</head>
<body>

<div id="loader"><span>Chargement de l'expertise CENTEC...</span></div>

<header>
    <h2 style="color:white; font-size: 1.5rem;">CENTEC</h2>
    <nav>
        <ul>
            <li><a href="#accueil">Accueil</a></li>
            <li><a href="#formations">Formations</a></li>
            <li><a href="#services">Services</a></li>
            <li><a href="#propos">À Propos</a></li>
            <li><a href="#contact">Contact</a></li>
        </ul>
    </nav>
</header>

<section class="hero" id="accueil">
    <h1>CENTEC</h1>
    <p>Maîtriser la géomatique pour mieux comprendre et gérer les territoires</p>
    <a href="#propos" class="btn" style="margin-top: 30px;">Découvrir le Centre</a>
</section>

<section>
    <div class="content-box">
        <h2 style="color: var(--secondary); margin-bottom: 20px;">Bienvenue au CENTEC</h2>
        <p>Le <strong>Centre National d’Étude en Territoire et Cartographie (CENTEC)</strong> est une structure spécialisée dans la <strong>formation professionnelle et l’expertise en géomatique appliquée</strong>.</p>
        <br>
        <p>Dans un contexte où les données territoriales jouent un rôle central dans la planification et la prise de décision, le CENTEC accompagne les <span class="highlight">administrations publiques, les bureaux d’études, les entreprises et les organisations de développement</span> dans la maîtrise des outils modernes d’analyse spatiale.</p>
    </div>
</section>

<section id="formations">
    <h2 class="section-title">Nos Programmes de Formation</h2>
    <div class="grid">
        <div class="card">
            <h3>DIGI MAP</h3>
            <p style="font-size: 0.9rem; margin-bottom: 10px; font-weight: bold;">Certification en Cartographie Numérique et SIG</p>
            <p>Apprenez à transformer les données territoriales en supports cartographiques clairs, pertinents et opérationnels pour l'aide à la décision.</p>
            <ul>
                <li>Conception de cartes thématiques</li>
                <li>Maîtrise des logiciels SIG</li>
                <li>Production de supports pros</li>
            </ul>
        </div>
        <div class="card">
            <h3>TeleSense Pro</h3>
            <p style="font-size: 0.9rem; margin-bottom: 10px; font-weight: bold;">Excellence en Télédétection Appliquée</p>
            <p>Consacré à l’analyse et au traitement des images satellites pour l’étude des territoires et de l’environnement.</p>
            <ul>
                <li>Analyse d'occupation du sol</li>
                <li>Suivi des changements territoriaux</li>
                <li>Études environnementales</li>
            </ul>
        </div>
        <div class="card">
            <h3>E-Enquêteur</h3>
            <p style="font-size: 0.9rem; margin-bottom: 10px; font-weight: bold;">Collecte Numérique de Données</p>
            <p>Maîtrisez les outils modernes de collecte de données géolocalisées sur le terrain pour des enquêtes fiables.</p>
            <ul>
                <li>Formulaires numériques</li>
                <li>Gestion d'enquêtes terrain</li>
                <li>Structuration de bases de données</li>
            </ul>
        </div>
        <div class="card">
            <h3>GeoSkill</h3>
            <p style="font-size: 0.9rem; margin-bottom: 10px; font-weight: bold;">Géomatique Appliquée Intensif</p>
            <p>Programme complet pour former des professionnels capables de maîtriser les outils essentiels de l'analyse spatiale.</p>
        </div>
    </div>
</section>

<section id="services" style="background: rgba(255,255,255,0.02); border-radius: 50px;">
    <h2 class="section-title">Services et Études</h2>
    <p style="text-align:center; margin-bottom: 40px;">Le CENTEC met son expertise au service de la production et de la valorisation des données territoriales.</p>
    
    <div class="grid">
        <div class="card">
            <i class="fas fa-database"></i>
            <h3>Collecte et Traitement</h3>
            <p>Mise en place de systèmes modernes de collecte de données géolocalisées, structurées et fiables.</p>
            <ul>
                <li>Conception de formulaires</li>
                <li>Nettoyage de bases de données</li>
                <li>Analyse des informations</li>
            </ul>
        </div>
        <div class="card">
            <i class="fas fa-map"></i>
            <h3>Cartographie Thématique</h3>
            <p>Visualiser et communiquer les informations territoriales via des cartes analytiques claires.</p>
            <ul>
                <li>Cartes d'infrastructures</li>
                <li>Supports pour rapports d'études</li>
                <li>Cartographie de projets</li>
            </ul>
        </div>
        <div class="card">
            <i class="fas fa-chart-line"></i>
            <h3>Analyse Géospatiale</h3>
            <p>Exploiter les données pour comprendre les dynamiques territoriales et orienter les décisions.</p>
            <ul>
                <li>Modélisation des dynamiques</li>
                <li>Analyse d'accessibilité</li>
                <li>Occupation des sols</li>
            </ul>
        </div>
    </div>
</section>

<section id="propos">
    <h2 class="section-title">À propos du CENTEC</h2>
    <div class="content-box">
        <h3>Notre Histoire</h3>
        <p>Créé en 2024, le CENTEC est né d’un <strong>constat issu de plusieurs années d’expérience professionnelle</strong>. Nous avons observé que de nombreuses institutions n’exploitent pas pleinement les outils de la géomatique, pourtant essentiels pour orienter les décisions stratégiques.</p>
    </div>

    <div class="values-grid" style="margin-top: 50px;">
        <div class="value-item">
            <i class="fas fa-star"></i>
            <h4>L'Excellence</h4>
            <p style="font-size: 0.8rem;">Standards professionnels les plus élevés.</p>
        </div>
        <div class="value-item">
            <i class="fas fa-check-circle"></i>
            <h4>Professionnalisme</h4>
            <p style="font-size: 0.8rem;">Rigueur, méthode et responsabilité.</p>
        </div>
        <div class="value-item">
            <i class="fas fa-lightbulb"></i>
            <h4>L'Innovation</h4>
            <p style="font-size: 0.8rem;">Technologies modernes et approches innovantes.</p>
        </div>
        <div class="value-item">
            <i class="fas fa-handshake"></i>
            <h4>L'Intégrité</h4>
            <p style="font-size: 0.8rem;">Transparence, éthique et confiance.</p>
        </div>
    </div>
</section>

<section style="background: var(--primary); color: white; border-radius: 30px; text-align: center;">
    <h2>L’humain au cœur de nos services</h2>
    <p style="max-width: 800px; margin: 20px auto;">Au-delà des technologies, les compétences humaines sont la clé de toute transformation durable. Nous accompagnons les professionnels dans leur évolution avec écoute et collaboration.</p>
</section>

<section id="contact">
    <h2 class="section-title">Nous contacter</h2>
    <div class="grid">
        <div style="padding: 20px;">
            <h3>Un partenaire pour vos projets</h3>
            <p>Le CENTEC intervient aux côtés des administrations, bureaux d'études, ONG et entreprises privées.</p>
            <br>
            <p><i class="fas fa-envelope"></i> contact@centec.ci</p>
            <p><i class="fas fa-phone"></i> +225 00 00 00 00 00</p>
        </div>
        <form class="content-box">
            <input type="text" placeholder="Nom de l'institution / Prénom" style="width:100%; padding:10px; margin-bottom:10px; background: rgba(0,0,0,0.3); border:1px solid #444; color:white;">
            <input type="email" placeholder="Email professionnel" style="width:100%; padding:10px; margin-bottom:10px; background: rgba(0,0,0,0.3); border:1px solid #444; color:white;">
            <textarea placeholder="Décrivez votre besoin en géomatique..." style="width:100%; padding:10px; height:100px; background: rgba(0,0,0,0.3); border:1px solid #444; color:white;"></textarea>
            <button class="btn" style="width: 100%; margin-top: 10px;">Envoyer la demande</button>
        </form>
    </div>
</section>

<footer>
    <p>© 2026 CENTEC – Centre National d’Étude en Territoire et Cartographie</p>
    <p style="font-size: 0.8rem; color: #666; margin-top: 10px;">Expertise • Formation • Innovation</p>
</footer>

<script>
    window.addEventListener("load", () => {
        document.getElementById("loader").style.display = "none";
    });

    // Simple animation au scroll
    const observer = new IntersectionObserver(entries => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                entry.target.style.opacity = 1;
                entry.target.style.transform = "translateY(0)";
            }
        });
    });

    document.querySelectorAll('section').forEach(section => {
        section.style.opacity = 0;
        section.style.transform = "translateY(20px)";
        section.style.transition = "all 0.6s ease-out";
        observer.observe(section);
    });
</script>

</body>
</html>

