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
        <div class="social-links">
            <i class="fab fa-facebook"></i>
            <i class="fab fa-linkedin"></i>
            <i class="fab fa-tiktok"></i>
        </div>
    </footer>

    <script>
        // LOADER
        window.addEventListener("load", () => {
            const loader = document.getElementById("loader");
            loader.style.opacity = "0";
            setTimeout(() => loader.style.display = "none", 500);
        });

        // MENU MOBILE
        const toggle = document.querySelector(".menu-toggle");
        const nav = document.querySelector("nav ul");
        toggle.onclick = () => nav.classList.toggle("active");

        // SCROLL ANIMATIONS
        const observerOptions = { threshold: 0.1 };
        const observer = new IntersectionObserver(entries => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = "1";
                    entry.target.style.transform = "translateY(0)";
                }
            });
        }, observerOptions);

        document.querySelectorAll("section, .card, .director-container").forEach(el => {
            el.style.opacity = "0";
            el.style.transform = "translateY(30px)";
            el.style.transition = "all 0.8s ease-out";
            observer.observe(el);
        });
    </script>
</body>
</html>
