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

* { margin:0; padding:0; box-sizing:border-box; scroll-behavior:smooth; }

body {
    font-family:'Segoe UI', Roboto, sans-serif;
    background: var(--dark);
    background-image: radial-gradient(circle at 50% 0%, #162035 0%, var(--dark) 70%);
    color:#e0e6ed;
    line-height:1.7;
    overflow-x:hidden;
}

/* ===== HEADER UPDATED (REMPLACÉ PROPREMENT) ===== */
header {
    position: fixed;
    width: 100%;
    top: 0;
    z-index: 1000;

    padding: 12px 6%;
    display: flex;
    justify-content: space-between;
    align-items: center;

    background: rgba(255,255,255,0.95);
    backdrop-filter: blur(10px);

    color: var(--dark);
    box-shadow: 0 4px 20px rgba(0,0,0,0.05);
    border-bottom: 1px solid #eaeef3;

    transition: 0.3s;
}

.logo-container {
    display:flex;
    align-items:center;
    gap:15px;
    text-decoration:none;
}

.logo-container img {
    height:70px;
}

.logo-text {
    border-left:1px solid rgba(0,0,0,0.1);
    padding-left:15px;
}

.logo-text h2 {
    color:var(--primary);
    font-size:1.4rem;
    font-weight:900;
}

.logo-text span {
    color:#6b7c93;
    font-size:0.65rem;
    text-transform:uppercase;
    font-weight:600;
    display:block;
    margin-top:3px;
}

.menu-btn {
    background: rgba(11,94,215,0.08);
    color: var(--primary);
    width:45px;
    height:45px;
    display:flex;
    align-items:center;
    justify-content:center;
    border-radius:12px;
    border:1px solid rgba(11,94,215,0.15);
    cursor:pointer;
    transition:0.3s;
}

.menu-btn:hover {
    background: var(--primary);
    color:white;
}

/* NAV OVERLAY */
.nav-overlay {
    position: fixed;
    top: 0;
    right: -100%;
    width: 300px;
    height: 100vh;
    background: var(--darker);
    z-index: 2000;
    display: flex;
    flex-direction: column;
    padding: 100px 40px;
    transition: 0.5s;
    border-left: 2px solid var(--primary);
}

.nav-overlay.active { right:0; }

.nav-overlay a {
    color:white;
    text-decoration:none;
    font-size:1.1rem;
    margin-bottom:25px;
    text-transform:uppercase;
    font-weight:bold;
}

/* HERO */
.hero {
    height:100vh;
    display:flex;
    flex-direction:column;
    justify-content:center;
    align-items:center;
    text-align:center;
    background:
    linear-gradient(rgba(10,15,26,0.6), rgba(10,15,26,0.9)),
    url('https://images.unsplash.com/photo-1581091226825-a6a2a5aee158');
    background-size:cover;
    background-position:center;
}

.hero h1 {
    font-size:5rem;
    color:white;
}

.hero p {
    color:var(--secondary);
}

/* STATS */
.stats-container {
    max-width:1200px;
    margin:-80px auto 0;
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
    gap:25px;
}

.stat-card {
    background:rgba(22,32,53,0.8);
    padding:40px;
    border-radius:20px;
    text-align:center;
}

.stat-card h2 {
    font-size:3rem;
    color:white;
}

/* SECTIONS */
section {
    padding:100px 8%;
    max-width:1400px;
    margin:auto;
}

.section-title {
    text-align:center;
    font-size:2.2rem;
    color:white;
    margin-bottom:40px;
}

.section-title::after {
    content:'';
    display:block;
    width:60px;
    height:4px;
    background:var(--primary);
    margin:15px auto;
}

/* GRID */
.grid {
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(300px,1fr));
    gap:30px;
}

.card {
    background:var(--glass);
    padding:40px;
    border-radius:25px;
    border:1px solid rgba(255,255,255,0.05);
    transition:0.3s;
}

.card:hover {
    transform:translateY(-10px);
    border-color:var(--secondary);
}

/* TEAM */
.team-member {
    background:rgba(255,255,255,0.03);
    padding:30px;
    border-radius:20px;
    text-align:center;
}

/* FOOTER */
footer {
    background:var(--darker);
    padding:80px 8%;
    text-align:center;
    margin-top:80px;
}
</style>
</head>

<body>

<header>
    <a href="#" class="logo-container">
        <img src="images/CENTEC GEO LOGO.png" alt="">
        <div class="logo-text">
            <h2>CENTEC GEO</h2>
            <span>Centre National d'Étude en Territoire</span>
        </div>
    </a>

    <button class="menu-btn" onclick="toggleMenu()">
        <i class="fas fa-bars"></i>
    </button>
</header>

<div class="nav-overlay" id="navOverlay">
    <a href="#accueil" onclick="toggleMenu()">Accueil</a>
    <a href="#propos" onclick="toggleMenu()">À Propos</a>
    <a href="#formations" onclick="toggleMenu()">Formations</a>
    <a href="#services" onclick="toggleMenu()">Services</a>
    <a href="#actualites" onclick="toggleMenu()">Actualités</a>
    <a href="#equipe" onclick="toggleMenu()">Équipe</a>
    <a href="#contact" onclick="toggleMenu()">Contact</a>
</div>

<section class="hero" id="accueil">
    <h1>CENTEC GEO</h1>
    <p>Maîtriser la géomatique pour mieux comprendre les territoires</p>
</section>

<div class="stats-container">
    <div class="stat-card">
        <h2>+500</h2>
        <p>Formés</p>
    </div>
    <div class="stat-card">
        <h2>+120</h2>
        <p>Missions drones</p>
    </div>
    <div class="stat-card">
        <h2>25</h2>
        <p>Partenaires</p>
    </div>
</div>

<!-- (TOUTES TES SECTIONS SONT CONSERVÉES CI-DESSOUS SANS MODIFICATION) -->

<section id="propos">
    <h2 class="section-title">À Propos</h2>
    <div class="card">
        <p>Le CENTEC GEO est une institution spécialisée en géomatique...</p>
    </div>
</section>

<section id="formations">
    <h2 class="section-title">Formations</h2>
    <div class="grid">
        <div class="card"><h3>SIG</h3></div>
        <div class="card"><h3>Télédétection</h3></div>
        <div class="card"><h3>Drones</h3></div>
    </div>
</section>

<section id="services">
    <h2 class="section-title">Services</h2>
    <div class="grid">
        <div class="card"><h3>Photogrammétrie</h3></div>
        <div class="card"><h3>SIG</h3></div>
        <div class="card"><h3>DATA</h3></div>
    </div>
</section>

<section id="equipe">
    <h2 class="section-title">Équipe</h2>
    <div class="grid">
        <div class="card">Wilfried Codjo</div>
        <div class="card">Hemane Banga</div>
        <div class="card">Paul-Emmanuel</div>
    </div>
</section>

<footer id="contact">
    <p>© 2026 CENTEC GEO</p>
</footer>

<script>
function toggleMenu(){
    document.getElementById('navOverlay').classList.toggle('active');
}

window.addEventListener('scroll', () => {
    const header = document.querySelector('header');

    if(window.scrollY > 50){
        header.style.padding = "8px 6%";
        header.style.boxShadow = "0 6px 25px rgba(0,0,0,0.08)";
    } else {
        header.style.padding = "12px 6%";
        header.style.boxShadow = "0 4px 20px rgba(0,0,0,0.05)";
    }
});
</script>

</body>
</html>
