
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>OutilMalin - Tes outils intelligents</title>
<style>
*{box-sizing:border-box}
body{margin:0;font-family:Arial,sans-serif;background:#f3f5fb;color:#20243a}
header{background:#202b55;color:white;padding:24px;text-align:center}
header h1{margin:0;font-size:30px}
nav{display:flex;justify-content:center;gap:12px;flex-wrap:wrap;margin-top:18px}
button{border:0;border-radius:9px;padding:12px 18px;cursor:pointer;font-weight:bold;background:#5268e8;color:white}
button:hover{opacity:.85}
nav button{background:white;color:#202b55}
main{max-width:950px;margin:35px auto;padding:15px}
.card{background:white;padding:25px;border-radius:16px;margin-bottom:20px;box-shadow:0 5px 20px #0000000d}
h2{margin-top:0}
textarea{width:100%;min-height:180px;padding:15px;border:1px solid #ccd1df;border-radius:10px;font-size:16px;resize:vertical}
.actions{display:flex;gap:9px;flex-wrap:wrap;margin-top:15px}
.hidden{display:none}
footer{text-align:center;padding:25px;color:#777}
</style>
</head>
<body>
<header>
<h1>OutilMalin</h1>
<p>Tous tes outils de texte au même endroit.</p>
<nav>
<button onclick="show('home')">Accueil</button>
<button onclick="show('tools')">Mes outils</button>
<button onclick="show('premium')">Premium</button>
</nav>
</header>

<main>
<section id="home" class="card">
<h2>Bienvenue sur OutilMalin !</h2>
<p>Gagne du temps avec des outils simples et gratuits.</p>
<button onclick="show('tools')">Découvrir les outils</button>
</section>

<section id="tools" class="card hidden">
<h2>Outils de texte</h2>
<p>Écris ou colle ton texte ci-dessous :</p>
<textarea id="txt" placeholder="Écris ton texte ici..."></textarea>
<div class="actions">
<button onclick="transform('upper')">MAJUSCULES</button>
<button onclick="transform('lower')">minuscules</button>
<button onclick="transform('clean')">Nettoyer</button>
<button onclick="copyText()">Copier</button>
<button onclick="clearText()">Effacer</button>
</div>
<p id="message"></p>
</section>

<section id="premium" class="card hidden">
<h2>OutilMalin Premium</h2>
<p>Découvre bientôt des fonctionnalités supplémentaires !</p>
<h2>5,99 € / mois</h2>
<p>Version de démonstration : aucun paiement réel n'est activé.</p>
</section>
</main>

<footer>© 2026 OutilMalin - Créé pour simplifier ton quotidien.</footer>

<script>
function show(id){
document.querySelectorAll('main section').forEach(s=>s.classList.add('hidden'));
document.getElementById(id).classList.remove('hidden');
}
function transform(type){
let t=document.getElementById('txt');
if(type==='upper')t.value=t.value.toUpperCase();
if(type==='lower')t.value=t.value.toLowerCase();
if(type==='clean')t.value=t.value.trim().replace(/\s+/g,' ');
}
async function copyText(){
let t=document.getElementById('txt');
try{
await navigator.clipboard.writeText(t.value);
document.getElementById('message').textContent='Texte copié !';
}catch(e){
document.getElementById('message').textContent='Copie non disponible sur ce navigateur.';
}
}
function clearText(){
document.getElementById('txt').value='';
document.getElementById('message').textContent='';
}
</script>
</body>
</html>
