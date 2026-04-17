<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>CENTEC – Centre de Formation & Géomatique</title>

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css" />

<style>
:root {
  --primary:#0b5ed7;
  --secondary:#198754;
  --dark:#111;
  --text:#222;
}

*{box-sizing:border-box;}

body{
  margin:0;
  font-family:Segoe UI, sans-serif;
  color:var(--text);
  background:white;
  line-height:1.6;
  scroll-behavior:smooth;
}

/* HEADER */
header{
  position:sticky;
  top:0;
  z-index:1000;
  background:linear-gradient(135deg,#7ec8ff,#2ea3ff);
  color:white;
  padding:1rem;
  backdrop-filter: blur(10px);
}

nav{
  display:flex;
  flex-wrap:wrap;
  gap:10px;
}

nav a{
  color:white;
  text-decoration:none;
  font-weight:600;
}

/* HERO */
.hero{
  background:linear-gradient(rgba(0,0,0,0.5),rgba(0,0,0,0.5)),
  url('https://images.unsplash.com/photo-1504384308090-c894fdcc538d');
  background-size:cover;
  background-position:center;
  color:white;
  text-align:center;
  padding:5rem 1rem;
  animation: zoomHero 8s infinite alternate ease-in-out;
}

@keyframes zoomHero {
  from {background-size:100%;}
  to {background-size:110%;}
}

/* SECTION */
section{
  padding:3rem 1rem;
  max-width:1200px;
  margin:auto;
}

/* TITRES */
h2{
  font-size:2rem;
  position:relative;
}

h2::after{
  content:"";
  width:70px;
  height:4px;
  background:linear-gradient(90deg,#0b5ed7,#00c6ff);
  display:block;
  margin-top:8px;
}

/* GRID */
.grid{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(240px,1fr));
  gap:1.2rem;
}

/* CARDS */
.card{
  background:white;
  border-radius:16px;
  padding:1.2rem;
  box-shadow:0 10px 25px rgba(0,0,0,0.08);
  transition:0.4s;
  position:relative;
  overflow:hidden;
}

.card::before{
  content:"";
  position:absolute;
  width:200%;
  height:200%;
  background:linear-gradient(120deg,transparent,rgba(255,255,255,0.3),transparent);
  transform:rotate(25deg);
  top:-100%;
  left:-100%;
  transition:0.6s;
}

.card:hover::before{
  top:100%;
  left:100%;
}

.card:hover{
  transform:translateY(-10px) scale(1.02);
  box-shadow:0 20px 45px rgba(0,0,0,0.15);
}

/* BUTTON */
.btn{
  display:inline-block;
  background:linear-gradient(135deg,#198754,#0b5ed7);
  color:white;
  padding:10px 18px;
  border-radius:30px;
  text-decoration:none;
  font-weight:bold;
  margin-top:10px;
  box-shadow:0 10px 25px rgba(0,0,0,0.2);
}

.btn:hover{
  transform:translateY(-3px);
}

/* BADGE */
.badge{
  background:var(--primary);
  color:white;
  padding:4px 10px;
  border-radius:20px;
  font-size:12px;
}

/* PROGRAM */
.program-banner{
  height:120px;
  background:#ddd;
  display:flex;
  align-items:center;
  justify-content:center;
  border-radius:10px;
  margin-bottom:10px;
}

/* SCROLL ANIMATION */
.reveal{
  opacity:0;
  transform:translateY(40px);
  transition:0.8s;
}

.reveal.active{
  opacity:1;
  transform:translateY(0);
}

/* WHATSAPP */
.cta-whatsapp{
  position:fixed;
  bottom:15px;
  right:15px;
  background:#25D366;
  color:white;
  padding:12px 14px;
  border-radius:50px;
  text-decoration:none;
  box-shadow:0 0 15px rgba(37,211,102,0.8);
}

/* FOOTER */
footer{
  background:var(--dark);
  color:white;
  text-align:center;
  padding:2rem;
}

footer a{
  color:white;
  margin:0 10px;
}

/* MOBILE */
@media(max-width:768px){
  h2{font-size:1.6rem;}
}
</style>
</head>

<body>

<header>
<h1>CENTEC</h1>
<nav>
<a href="#accueil">Accueil</a>
<a href="#apropos">À propos</a>
<a href="#pourquoi">Pourquoi</a>
<a href="#programmes">Programmes</a>
<a href="#seminaires">Séminaires</a>
<a href="#contact">Contact</a>
</nav>
</header>

<section class="hero reveal" id="accueil">
<h2>Former les experts de la géomatique</h2>
<p>SIG, drones, cartographie et analyse territoriale</p>
<a class="btn" href="#programmes">Découvrir</a>
</section>

<section id="apropos" class="reveal">
<h2>À propos</h2>
<p>CENTEC forme des professionnels en géomatique appliquée avec une approche pratique et moderne.</p>
</section>

<section id="pourquoi" class="reveal">
<h2>Pourquoi CENTEC ?</h2>
<div class="grid">
<div class="card"><h3>Pratique</h3><p>Cas réels terrain.</p></div>
<div class="card"><h3>Expertise</h3><p>Outils professionnels.</p></div>
<div class="card"><h3>Progression</h3><p>Débutant à expert.</p></div>
<div class="card"><h3>Accompagnement</h3><p>Suivi personnalisé.</p></div>
</div>
</section>

<section id="programmes" class="reveal">
<h2>Programmes</h2>
<div class="grid">

<div class="card">
<div class="program-banner">DIGI MAP</div>
<h3>DIGI MAP</h3>
<span class="badge">SIG</span>
<p>Cartographie complète</p>
</div>

<div class="card">
<div class="program-banner">TeleSense</div>
<h3>Télédétection</h3>
<span class="badge">Drone</span>
<p>Analyse d’images</p>
</div>

</div>
</section>

<section id="seminaires" class="reveal">
<h2>Séminaires</h2>
<div class="grid">
<div class="card"><h3>Webmapping</h3></div>
<div class="card"><h3>Drones</h3></div>
</div>
</section>

<section id="contact" class="reveal">
<h2>Contact</h2>
<form action="https://formsubmit.co/centrecartographie@gmail.com" method="POST">
<input type="text" placeholder="Nom" required style="width:100%;padding:10px;margin:5px 0;">
<input type="email" placeholder="Email" required style="width:100%;padding:10px;margin:5px 0;">
<textarea placeholder="Message" style="width:100%;padding:10px;margin:5px 0;"></textarea>
<button class="btn">Envoyer</button>
</form>
</section>

<a class="cta-whatsapp" href="#">WhatsApp</a>

<footer>
<p>CENTEC © 2026</p>
<div>
<a href="#"><i class="fab fa-facebook"></i></a>
<a href="#"><i class="fab fa-linkedin"></i></a>
<a href="#"><i class="fab fa-tiktok"></i></a>
</div>
</footer>

<script>
// SCROLL ANIMATION
const reveals = document.querySelectorAll(".reveal");

window.addEventListener("scroll", () => {
  reveals.forEach(el => {
    const top = el.getBoundingClientRect().top;
    const windowHeight = window.innerHeight;
    if(top < windowHeight - 80){
      el.classList.add("active");
    }
  });
});

// HEADER DYNAMIQUE
window.addEventListener("scroll", () => {
  const header = document.querySelector("header");
  header.style.background = window.scrollY > 50
    ? "rgba(46,163,255,0.9)"
    : "linear-gradient(135deg,#7ec8ff,#2ea3ff)";
});

// WHATSAPP AUTO MESSAGE
document.querySelector(".cta-whatsapp").href =
"https://wa.me/225000000000?text=Bonjour%20je%20veux%20plus%20d'informations%20sur%20les%20formations%20CENTEC";
</script>

</body>
</html>
