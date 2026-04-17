<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CENTEC – Ingénierie Géospatiale</title>

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">

<style>
:root{
--primary:#0b5ed7;
--secondary:#00c6ff;
--dark:#0a0a0a;
--glass:rgba(255,255,255,0.08);
}

*{margin:0;padding:0;box-sizing:border-box;}

body{
font-family:Segoe UI,sans-serif;
background:#0a0a0a;
color:white;
overflow-x:hidden;
}

/* LOADER */
#loader{
position:fixed;
width:100%;
height:100%;
background:#000;
display:flex;
align-items:center;
justify-content:center;
z-index:9999;
}

#loader span{
font-size:2rem;
animation:pulse 1s infinite;
}

@keyframes pulse{
0%{opacity:0.3;}
50%{opacity:1;}
100%{opacity:0.3;}
}

/* HEADER */
header{
position:fixed;
width:100%;
top:0;
z-index:1000;
padding:15px;
display:flex;
justify-content:space-between;
background:rgba(0,0,0,0.6);
backdrop-filter:blur(10px);
}

nav ul{
display:flex;
gap:20px;
list-style:none;
}

nav a{
color:white;
text-decoration:none;
font-weight:600;
}

.menu-toggle{
display:none;
font-size:24px;
}

/* HERO */
.hero{
height:100vh;
display:flex;
flex-direction:column;
justify-content:center;
align-items:center;
text-align:center;
background:radial-gradient(circle,#001,#000);
}

.hero h1{
font-size:3rem;
background:linear-gradient(90deg,#00c6ff,#0b5ed7);
-webkit-background-clip:text;
color:transparent;
}

.btn{
background:linear-gradient(135deg,#0b5ed7,#00c6ff);
padding:12px 20px;
border-radius:30px;
text-decoration:none;
color:white;
margin-top:20px;
}

/* SECTION */
section{
padding:80px 20px;
max-width:1200px;
margin:auto;
}

/* GRID */
.grid{
display:grid;
grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
gap:20px;
}

/* CARD */
.card{
background:var(--glass);
backdrop-filter:blur(10px);
padding:20px;
border-radius:15px;
transition:0.3s;
border:1px solid rgba(255,255,255,0.1);
}

.card:hover{
transform:translateY(-10px);
}

/* STATS */
.stats{
display:flex;
justify-content:space-around;
text-align:center;
flex-wrap:wrap;
}

/* FOOTER */
footer{
background:#000;
text-align:center;
padding:30px;
}

/* WHATSAPP */
.cta{
position:fixed;
bottom:20px;
right:20px;
background:#25D366;
padding:12px;
border-radius:50%;
color:white;
}

/* MOBILE */
@media(max-width:768px){
nav ul{
display:none;
flex-direction:column;
background:#000;
position:absolute;
top:60px;
right:0;
padding:20px;
}
nav ul.active{display:flex;}
.menu-toggle{display:block;}
.hero h1{font-size:2rem;}
}
</style>
</head>

<body>

<div id="loader"><span>Chargement...</span></div>

<header>
<h2>CENTEC</h2>
<i class="fas fa-bars menu-toggle"></i>
<nav>
<ul>
<li><a href="#about">À propos</a></li>
<li><a href="#catalogue">Catalogue</a></li>
<li><a href="#missions">Missions</a></li>
<li><a href="#livrables">Livrables</a></li>
<li><a href="#team">Équipe</a></li>
<li><a href="#contact">Contact</a></li>
</ul>
</nav>
</header>

<section class="hero">
<h1>Géomatique & Ingénierie</h1>
<p>Formation • Drones • Analyse spatiale</p>
<a href="#catalogue" class="btn">Explorer</a>
</section>

<section class="stats">
<div><h2>500+</h2><p>Étudiants</p></div>
<div><h2>95%</h2><p>Succès</p></div>
<div><h2>20+</h2><p>Projets</p></div>
</section>

<section id="catalogue">
<h2>Catalogue</h2>
<div class="grid">
<div class="card"><h3>DIGI MAP</h3></div>
<div class="card"><h3>Drone Pro</h3></div>
<div class="card"><h3>GeoSkill</h3></div>
</div>
</section>

<section id="missions">
<h2>Missions</h2>
<div class="card">Simulation de levée terrain avec drone</div>
</section>

<section id="livrables">
<h2>Livrables</h2>
<div class="grid">
<div class="card">Cartes SIG</div>
<div class="card">Orthophoto</div>
<div class="card">MNT</div>
</div>
</section>

<section id="team">
<h2>Équipe</h2>
<div class="grid">
<div class="card">Expert SIG</div>
<div class="card">Drone Specialist</div>
<div class="card">Analyste</div>
</div>
</section>

<section id="contact">
<h2>Contact</h2>
<form>
<input type="text" placeholder="Nom" style="width:100%;padding:10px;margin:10px 0;">
<input type="email" placeholder="Email" style="width:100%;padding:10px;margin:10px 0;">
<textarea placeholder="Message" style="width:100%;padding:10px;margin:10px 0;"></textarea>
<button class="btn">Envoyer</button>
</form>
</section>

<a class="cta" href="https://wa.me/225000000000">💬</a>

<footer>
<p>© 2026 CENTEC</p>
<i class="fab fa-facebook"></i>
<i class="fab fa-linkedin"></i>
<i class="fab fa-tiktok"></i>
</footer>

<script>
// LOADER
window.addEventListener("load",()=>document.getElementById("loader").style.display="none");

// MENU MOBILE
const toggle=document.querySelector(".menu-toggle");
const nav=document.querySelector("nav ul");
toggle.onclick=()=>nav.classList.toggle("active");

// SCROLL ANIMATION
const observer=new IntersectionObserver(entries=>{
entries.forEach(entry=>{
if(entry.isIntersecting){
entry.target.style.opacity=1;
entry.target.style.transform="translateY(0)";
}
});
});

document.querySelectorAll("section, .card").forEach(el=>{
el.style.opacity=0;
el.style.transform="translateY(50px)";
el.style.transition="0.6s";
observer.observe(el);
});
</script>

</body>
</html>
