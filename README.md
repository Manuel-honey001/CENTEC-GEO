# CENTEC GEO 
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>CENTEC – Géomatique & Ingénierie Géospatiale</title>

  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css"/>

  <style>
    :root{
      --primary:#0b5ed7;
      --secondary:#198754;
      --dark:#111;
      --text:#222;
      --bg:#f5f7fa;
    }

    *{box-sizing:border-box;}
    body{
      margin:0;
      font-family:Segoe UI, sans-serif;
      color:var(--text);
      background:white;
      line-height:1.6;
    }

    html{scroll-behavior:smooth;}

    header{
      position:sticky;
      top:0;
      z-index:1000;
      background:linear-gradient(135deg,#7ec8ff,#2ea3ff);
      color:white;
      padding:1rem;
    }

    nav{
      display:flex;
      flex-wrap:wrap;
      gap:10px;
      margin-top:10px;
    }

    nav a{
      color:white;
      text-decoration:none;
      font-weight:600;
      font-size:14px;
    }

    .hero{
      background:linear-gradient(rgba(0,0,0,0.55),rgba(0,0,0,0.55)),
      url('https://images.unsplash.com/photo-1504384308090-c894fdcc538d');
      background-size:cover;
      background-position:center;
      color:white;
      text-align:center;
      padding:5rem 1rem;
    }

    section{
      padding:3rem 1rem;
      max-width:1200px;
      margin:auto;
    }

    h2::after{
      content:"";
      width:60px;
      height:4px;
      background:var(--primary);
      display:block;
      margin-top:6px;
      border-radius:10px;
    }

    .grid{
      display:grid;
      grid-template-columns:repeat(auto-fit,minmax(240px,1fr));
      gap:1.2rem;
    }

    .card{
      background:white;
      border-radius:16px;
      padding:1.2rem;
      box-shadow:0 10px 25px rgba(0,0,0,0.08);
      transition:0.3s;
    }

    .card:hover{
      transform:translateY(-6px);
    }

    .tag{
      display:inline-block;
      background:var(--primary);
      color:white;
      padding:4px 10px;
      border-radius:20px;
      font-size:12px;
      margin-bottom:8px;
    }

    .btn{
      display:inline-block;
      background:var(--secondary);
      color:white;
      padding:10px 16px;
      border-radius:30px;
      text-decoration:none;
      font-weight:bold;
      margin-top:10px;
    }

    .mission-box{
      background:#f8f9fa;
      padding:1rem;
      border-left:4px solid var(--primary);
      border-radius:10px;
    }

    footer{
      background:var(--dark);
      color:white;
      text-align:center;
      padding:2rem 1rem;
    }

    footer a{
      color:white;
      margin:0 8px;
      text-decoration:none;
    }

    @media(max-width:768px){
      .hero{padding:4rem 1rem;}
    }
  </style>
</head>

<body>

<header>
  <h1>CENTEC</h1>
  <nav>
    <a href="#accueil">Accueil</a>
    <a href="#catalogue">Catalogue</a>
    <a href="#missions">Missions</a>
    <a href="#livrables">Livrables</a>
    <a href="#equipe">Équipe</a>
    <a href="#contact">Contact</a>
  </nav>
</header>

<!-- HERO -->
<section class="hero" id="accueil">
  <h2>Ingénierie Géospatiale & Formation Terrain</h2>
  <p>SIG • Drones • Télédétection • Analyse spatiale</p>
  <a class="btn" href="#catalogue">Voir le catalogue</a>
</section>

<!-- CATALOGUE FORMATIONS -->
<section id="catalogue">
  <h2>Catalogue des formations</h2>

  <div class="grid">

    <div class="card">
      <span class="tag">SIG</span>
      <h3>DIGI MAP</h3>
      <p>Cartographie numérique professionnelle de la donnée à la carte finale.</p>
      <a class="btn" href="#contact">S'inscrire</a>
    </div>

    <div class="card">
      <span class="tag">Drones</span>
      <h3>TeleSense Pro</h3>
      <p>Acquisition et traitement d’images aériennes pour analyse terrain.</p>
      <a class="btn" href="#contact">S'inscrire</a>
    </div>

    <div class="card">
      <span class="tag">Analyse</span>
      <h3>GeoSkill</h3>
      <p>Analyse spatiale avancée pour projets environnement et BTP.</p>
      <a class="btn" href="#contact">S'inscrire</a>
    </div>

    <div class="card">
      <span class="tag">Data</span>
      <h3>E-Enquêteur</h3>
      <p>Collecte et traitement de données terrain géolocalisées.</p>
      <a class="btn" href="#contact">S'inscrire</a>
    </div>

  </div>
</section>

<!-- MISSIONS -->
<section id="missions">
  <h2>Missions terrain simulées</h2>

  <div class="mission-box">
    <h3>Levée topographique urbaine</h3>
    <ul>
      <li>Surface : 5 hectares</li>
      <li>Outil : drone + SIG</li>
      <li>Résultat : orthophoto + MNT + carte finale</li>
      <li>Durée : 30 minutes acquisition + traitement</li>
    </ul>
  </div>

  <div class="mission-box" style="margin-top:1rem;">
    <h3>Analyse environnementale</h3>
    <ul>
      <li>Étude de zone agricole</li>
      <li>Classification satellite</li>
      <li>Rapport d’aide à la décision</li>
    </ul>
  </div>
</section>

<!-- LIVRABLES -->
<section id="livrables">
  <h2>Livrables professionnels</h2>

  <div class="grid">
    <div class="card"><h3>Cartes SIG</h3><p>Cartographie exploitable pour projets réels.</p></div>
    <div class="card"><h3>Orthophotos</h3><p>Images aériennes corrigées et mesurables.</p></div>
    <div class="card"><h3>MNT / MNE</h3><p>Modèles numériques de terrain.</p></div>
    <div class="card"><h3>Rapports techniques</h3><p>Analyse complète pour prise de décision.</p></div>
  </div>
</section>

<!-- EQUIPE -->
<section id="equipe">
  <h2>Équipe technique</h2>

  <div class="grid">
    <div class="card"><h3>Ingénieur SIG</h3><p>Analyse et modélisation spatiale.</p></div>
    <div class="card"><h3>Expert Drones</h3><p>Acquisition et traitement aérien.</p></div>
    <div class="card"><h3>Analyste Data</h3><p>Interprétation géospatiale avancée.</p></div>
    <div class="card"><h3>Coordinateur</h3><p>Suivi pédagogique et projets.</p></div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <h2>Contact & inscription</h2>

  <form action="https://formsubmit.co/centrecartographie@gmail.com" method="POST">
    <input type="text" name="nom" placeholder="Nom" required style="width:100%;padding:10px;margin:5px 0;">
    <input type="email" name="email" placeholder="Email" required style="width:100%;padding:10px;margin:5px 0;">
    <textarea name="message" placeholder="Message" style="width:100%;padding:10px;margin:5px 0;"></textarea>
    <button class="btn" type="submit">Envoyer</button>
  </form>
</section>

<!-- FOOTER -->
<footer>
  <p>CENTEC © 2026</p>

  <div>
    <a href="#"><i class="fab fa-facebook"></i></a>
    <a href="#"><i class="fab fa-linkedin"></i></a>
    <a href="#"><i class="fab fa-tiktok"></i></a>
  </div>
</footer>

</body>
</html>
