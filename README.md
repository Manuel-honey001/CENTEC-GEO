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
            --transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; scroll-behavior: smooth; }

        body {
            font-family: 'Segoe UI', Roboto, sans-serif;
            background: var(--dark);
            color: #e0e0e0;
            line-height: 1.7;
            overflow-x: hidden;
        }

        /* --- HEADER & LOGO --- */
        header {
            position: fixed; width: 100%; top: 0; z-index: 1000;
            padding: 10px 5%; display: flex; justify-content: space-between; align-items: center;
            background: rgba(0, 0, 0, 0.9); backdrop-filter: blur(15px);
            border-bottom: 1px solid rgba(255,255,255,0.1);
        }

        .logo-container { display: flex; align-items: center; text-decoration: none; gap: 15px; }
        .logo-container img { height: 70px; width: auto; }
        .logo-text { border-left: 1px solid rgba(255,255,255,0.3); padding-left: 15px; }
        .logo-text h2 { color: white; font-size: 1.3rem; font-weight: 800; line-height: 1.1; }
        .logo-text span { color: var(--secondary); font-size: 0.65rem; text-transform: uppercase; }

        nav ul { display: flex; gap: 25px; list-style: none; }
        nav a { color: white; text-decoration: none; font-size: 0.85rem; font-weight: 600; text-transform: uppercase; transition: 0.3s; }
        nav a:hover { color: var(--secondary); }

        /* --- HERO --- */
        .hero {
            height: 100vh; display: flex; flex-direction: column; justify-content: center;
            align-items: center; text-align: center; padding: 0 10%;
            /* MODIFIER IMAGE DE FOND ICI --> */
            background: linear-gradient(rgba(0,0,0,0.7), rgba(0,0,0,0.8)), url('https://images.unsplash.com/photo-1581091226825-a6a2a5aee158?q=80&w=1920');
            background-size: cover; background-position: center;
        }

        /* --- SECTIONS --- */
        section { padding: 100px 8%; max-width: 1400px; margin: auto; }
        .section-title { font-size: 2.2rem; color: white; margin-bottom: 50px; text-align: center; text-transform: uppercase; }
        .content-box { background: var(--glass); padding: 50px; border-radius: 20px; border: 1px solid rgba(255,255,255,0.1); }

        /* --- DIRECTEUR --- */
        .director-box { display: grid; grid-template-columns: 1fr 2fr; gap: 40px; align-items: center; }
        .director-photo { width: 100%; border-radius: 15px; border: 4px solid var(--primary); }
        .director-name { color: white; font-size: 1.5rem; font-weight: 800; margin-top: 15px; }
        .director-title { color: var(--secondary); font-size: 0.9rem; font-weight: 600; text-transform: uppercase; }

        /* --- EQUIPE CARROUSEL --- */
        .team-container { position: relative; overflow: hidden; padding: 20px 0; }
        .team-slider { display: flex; gap: 30px; transition: transform 0.5s ease; cursor: grab; }
        .team-member { flex: 0 0 calc(25% - 22.5px); background: var(--glass); padding: 20px; border-radius: 15px; text-align: center; border: 1px solid rgba(255,255,255,0.1); }
        .team-member img { width: 120px; height: 120px; border-radius: 50%; border: 3px solid var(--primary); margin-bottom: 15px; }
        
        .nav-arrows { display: flex; justify-content: center; gap: 20px; margin-top: 30px; }
        .arrow { background: var(--primary); color: white; width: 45px; height: 45px; border-radius: 50%; display: flex; align-items: center; justify-content: center; cursor: pointer; transition: 0.3s; }
        .arrow:hover { background: var(--secondary); transform: scale(1.1); }

        /* --- FOOTER & CONTACT --- */
        footer { background: #000; padding: 80px 5% 40px; border-top: 1px solid #222; }
        .footer-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 40px; text-align: left; margin-bottom: 50px; }
        .contact-info i { color: var(--secondary); margin-right: 10px; width: 20px; }
        .social-icons a { color: white; font-size: 1.5rem; margin-right: 20px; transition: 0.3s; }
        .social-icons a:hover { color: var(--secondary); }

        /* Responsive */
        @media (max-width: 992px) { .director-box { grid-template-columns: 1fr; text-align: center; } .team-member { flex: 0 0 calc(50% - 15px); } }
        @media (max-width: 600px) { .team-member { flex: 0 0 100%; } }
    </style>
</head>
<body>

<header>
    <a href="#" class="logo-container">
        <img src="1000442449.jpg" alt="Logo CENTEC">
        <div class="logo-text">
            <h2>CENTEC GEO</h2>
            <span>Centre National d’Étude en<br>Territoire et Cartographie CI</span>
        </div>
    </a>
    <nav>
        <ul>
            <li><a href="#accueil">Accueil</a></li>
            <li><a href="#propos">À Propos</a></li>
            <li><a href="#services">Services</a></li>
            <li><a href="#equipe">Équipe</a></li>
            <li><a href="#contact">Contact</a></li>
        </ul>
    </nav>
</header>

<section class="hero" id="accueil">
    <h1 data-aos="zoom-out" data-aos-duration="1500">CENTEC GEO</h1>
    <p data-aos="fade-up" data-aos-delay="500">Maîtriser la géomatique pour mieux comprendre et gérer les territoires</p>
</section>

<section id="propos">
    <div class="content-box director-box" data-aos="fade-right">
        <div>
            <img src="photo-directeur.jpg" alt="Wilfried Codjo" class="director-photo">
            <div class="director-name">WILFRIED CODJO</div>
            <div class="director-title">GÉOMATICIEN - SPÉCIALISTE EN PHOTOGRAMMÉTRIE</div>
        </div>
        <div data-aos="fade-left" data-aos-delay="300">
            <h3>Le Mot du Directeur</h3>
            <br>
            <p style="font-style: italic; font-size: 1.1rem;">"Le CENTEC est né d’un constat : celui de la nécessité d'intégrer les technologies spatiales au cœur de nos stratégies de développement. Notre mission est de vous fournir l'expertise et les outils pour transformer chaque donnée géographique en une décision éclairée."</p>
        </div>
    </div>
</section>

<section style="background: rgba(255,255,255,0.01);">
    <h2 class="section-title" data-aos="fade-up">Pourquoi nous choisir ?</h2>
    <div class="footer-grid">
        <div class="content-box" data-aos="flip-left" style="padding: 30px; text-align: center;">
            <i class="fas fa-microchip fa-3x" style="color:var(--secondary); margin-bottom:20px;"></i>
            <h4>Technologie de pointe</h4>
            <p>Utilisation des derniers capteurs drones et logiciels SIG.</p>
        </div>
        <div class="content-box" data-aos="flip-left" data-aos-delay="200" style="padding: 30px; text-align: center;">
            <i class="fas fa-user-graduate fa-3x" style="color:var(--secondary); margin-bottom:20px;"></i>
            <h4>Expertise Certifiée</h4>
            <p>Une équipe de spécialistes passionnés et expérimentés.</p>
        </div>
        <div class="content-box" data-aos="flip-left" data-aos-delay="400" style="padding: 30px; text-align: center;">
            <i class="fas fa-map-marked-alt" style="font-size: 3rem; color:var(--secondary); margin-bottom:20px;"></i>
            <h4>Précision Garantie</h4>
            <p>Des relevés au centimètre pour vos projets d'ingénierie.</p>
        </div>
    </div>
</section>

<section id="equipe">
    <h2 class="section-title" data-aos="fade-up">Notre Équipe</h2>
    <div class="team-container">
        <div class="team-slider" id="slider">
            <div class="team-member">
                <img src="membre1.jpg" alt="Expert">
                <h4>Nom Prénom</h4>
                <p>Expert SIG</p>
            </div>
            <div class="team-member">
                <img src="membre2.jpg" alt="Expert">
                <h4>Nom Prénom</h4>
                <p>Pilote Drone</p>
            </div>
            <div class="team-member">
                <img src="membre3.jpg" alt="Expert">
                <h4>Nom Prénom</h4>
                <p>Analyste Télédétection</p>
            </div>
            <div class="team-member">
                <img src="membre4.jpg" alt="Expert">
                <h4>Nom Prénom</h4>
                <p>Responsable DATA</p>
            </div>
        </div>
    </div>
    <div class="nav-arrows">
        <div class="arrow" onclick="moveSlider(-1)"><i class="fas fa-chevron-left"></i></div>
        <div class="arrow" onclick="moveSlider(1)"><i class="fas fa-chevron-right"></i></div>
    </div>
</section>

<footer id="contact">
    <div class="footer-grid">
        <div>
            <h3 style="color:white; margin-bottom: 20px;">CENTEC GEO</h3>
            <p>L'excellence en géomatique au service du territoire.</p>
            <div class="social-icons" style="margin-top: 20px;">
                <a href="#"><i class="fab fa-linkedin"></i></a>
                <a href="#"><i class="fab fa-facebook"></i></a>
                <a href="#"><i class="fab fa-whatsapp"></i></a>
            </div>
        </div>
        <div class="contact-info">
            <h3 style="color:white; margin-bottom: 20px;">Nous Trouver</h3>
            <p><i class="fas fa-map-marker-alt"></i> Siège Social : Cocody 2 Plateaux, Abidjan</p>
            <p><i class="fas fa-phone"></i> +225 00 00 00 00 00</p>
            <p><i class="fas fa-envelope"></i> contact@centec.ci</p>
        </div>
        <div>
            <h3 style="color:white; margin-bottom: 20px;">Horaires</h3>
            <p>Lun - Ven : 08:00 - 18:00</p>
            <p>Sam : Sur rendez-vous</p>
        </div>
    </div>
    <div style="text-align: center; border-top: 1px solid #222; padding-top: 20px; font-size: 0.8rem;">
        © 2026 CENTEC GEO – Centre National d’Étude en Territoire et Cartographie CI
    </div>
</footer>

<script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
<script>
    AOS.init({ duration: 1000, once: true });

    // Gestion du slider équipe
    let currentPos = 0;
    const slider = document.getElementById('slider');
    
    function moveSlider(direction) {
        const memberWidth = document.querySelector('.team-member').offsetWidth + 30;
        const maxScroll = slider.scrollWidth - slider.parentElement.offsetWidth;
        
        currentPos += direction * memberWidth;
        
        if (currentPos < 0) currentPos = 0;
        if (currentPos > maxScroll) currentPos = maxScroll;
        
        slider.style.transform = `translateX(-${currentPos}px)`;
    }
</script>

</body>
</html>
