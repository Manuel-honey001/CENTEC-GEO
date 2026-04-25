<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CENTEC GEO</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Poppins', sans-serif;
}

body {
    background: #f5f7fa;
    color: #333;
}

/* HEADER */
header {
    background: #0a2540;
    color: white;
    padding: 15px 40px;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

header h1 {
    font-size: 22px;
}

nav a {
    color: white;
    margin-left: 20px;
    text-decoration: none;
    font-weight: 400;
}

nav a:hover {
    color: #00b4d8;
}

/* HERO */
.hero {
    background: linear-gradient(rgba(10,37,64,0.8), rgba(10,37,64,0.8)), url('https://images.unsplash.com/photo-1581092580497-e0d23cbdf1dc');
    background-size: cover;
    background-position: center;
    color: white;
    text-align: center;
    padding: 100px 20px;
}

.hero h2 {
    font-size: 40px;
    margin-bottom: 10px;
}

.hero p {
    font-size: 18px;
}

.btn {
    display: inline-block;
    margin-top: 20px;
    padding: 12px 25px;
    background: #00b4d8;
    color: white;
    text-decoration: none;
    border-radius: 5px;
}

.btn:hover {
    background: #0096c7;
}

/* SECTION */
.section {
    padding: 60px 40px;
    text-align: center;
}

.section h2 {
    margin-bottom: 30px;
    font-size: 28px;
}

/* SERVICES */
.services {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 20px;
}

.card {
    background: white;
    padding: 25px;
    width: 280px;
    border-radius: 10px;
    box-shadow: 0 5px 15px rgba(0,0,0,0.1);
    transition: 0.3s;
}

.card:hover {
    transform: translateY(-5px);
}

/* FOOTER */
footer {
    background: #0a2540;
    color: white;
    text-align: center;
    padding: 20px;
}

/* RESPONSIVE */
@media(max-width: 768px){
    .hero h2 {
        font-size: 28px;
    }

    .services {
        flex-direction: column;
        align-items: center;
    }
}
</style>
</head>

<body>

<header>
    <h1>CENTEC GEO</h1>
    <nav>
        <a href="#">Accueil</a>
        <a href="#">Services</a>
        <a href="#">Formations</a>
        <a href="#">Contact</a>
    </nav>
</header>

<section class="hero">
    <h2>Expertise en Géomatique & Drone</h2>
    <p>Des solutions innovantes pour vos projets territoriaux</p>
    <a href="#" class="btn">Nous contacter</a>
</section>

<section class="section">
    <h2>Nos Services</h2>
    <div class="services">
        <div class="card">
            <h3>Webmapping</h3>
            <p>Création de cartes interactives et applications SIG.</p>
        </div>

        <div class="card">
            <h3>Drone Mapping</h3>
            <p>Collecte de données aériennes haute précision.</p>
        </div>

        <div class="card">
            <h3>Formation</h3>
            <p>Programmes pratiques en géomatique et SIG.</p>
        </div>
    </div>
</section>

<section class="section">
    <h2>À propos</h2>
    <p>
        CENTEC GEO accompagne les entreprises et institutions dans la valorisation
        des données géospatiales grâce à des technologies modernes et innovantes.
    </p>
</section>

<footer>
    <p>© 2026 CENTEC GEO - Tous droits réservés</p>
</footer>

<script>
// Petite animation scroll
document.querySelectorAll('a[href^="#"]').forEach(anchor => {
    anchor.addEventListener('click', function(e) {
        e.preventDefault();
        document.querySelector(this.getAttribute('href'))?.scrollIntoView({
            behavior: 'smooth'
        });
    });
});
</script>

</body>
</html>
