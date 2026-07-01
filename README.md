<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Olympus Suplementos PRO</title>

<style>
body{
margin:0;
font-family:Arial;
background:#0e0e0e;
color:#fff;
}

header{
padding:25px;
text-align:center;
background:#151515;
}

h1{color:#f5c542;margin:0}

input, select{
padding:10px;
margin:8px;
width:90%;
max-width:420px;
border-radius:8px;
border:none;
}

.container{
display:grid;
grid-template-columns:repeat(auto-fit,minmax(240px,1fr));
gap:12px;
padding:20px;
max-width:1200px;
margin:auto;
}

.card{
background:#1c1c1c;
padding:15px;
border-radius:10px;
border:1px solid #333;
display:flex;
flex-direction:column;
justify-content:space-between;
}

.price{
color:#00ff99;
font-weight:bold;
margin:8px 0;
}

.tag{
font-size:12px;
color:#ffcc00;
opacity:0.8;
}

.btn{
background:#25d366;
color:#fff;
padding:10px;
text-align:center;
border-radius:8px;
text-decoration:none;
font-weight:bold;
margin-top:10px;
}

.section{
text-align:center;
padding:25px;
}

.whatsapp{
position:fixed;
bottom:20px;
right:20px;
background:#25d366;
padding:14px;
border-radius:50px;
font-weight:bold;
color:#fff;
text-decoration:none;
}

.instagram{
position:fixed;
bottom:85px;
right:20px;
background:linear-gradient(45deg,#f58529,#dd2a7b,#8134af);
padding:14px;
border-radius:50px;
font-weight:bold;
color:#fff;
text-decoration:none;
}
</style>
</head>

<body>

<header>
<h1>🔥 OLYMPUS SUPLEMENTOS</h1>

<input type="text" id="search" placeholder="Buscar producto...">
<select id="filter">
<option value="all">Todas las marcas</option>
<option value="VITALGY">Vitalgy</option>
<option value="STAR">Star</option>
<option value="ENA">ENA</option>
<option value="NUTREMAX">Nutremax</option>
<option value="ONEFIT">One Fit</option>
<option value="GOLD">Gold</option>
<option value="XTRENGHT">Xtenght</option>
<option value="GEONAT">Geonat</option>
<option value="GENTECH">Gentech</option>
<option value="INTEGRA">Integra</option>
<option value="ENTRENUTS">Entrenuts</option>
<option value="GRANGER">Granger</option>
<option value="XBODY">Xbody</option>
<option value="HTN">HTN</option>
<option value="MERVICK">Mervick</option>
<option value="MAX FORCE">Max Force</option>
<option value="SQUADRA">Squadra</option>
</select>
</header>

<div class="container" id="store"></div>

<!-- INSTAGRAM -->
<section class="section">
<h2>📲 Instagram oficial</h2>
<p>@olympus.suplementossf</p>
<a class="btn" href="https://instagram.com/olympus.suplementossf" target="_blank">
IR A INSTAGRAM
</a>
</section>

<!-- WHATSAPP -->
<a class="whatsapp" href="https://wa.me/5493425683418?text=Hola%20quiero%20info%20de%20suplementos" target="_blank">
WhatsApp
</a>

<!-- INSTAGRAM FLOAT -->
<a class="instagram" href="https://instagram.com/olympus.suplementossf" target="_blank">
IG
</a>

<script>
const products = [

/* INTEGRA / VITALGY / GENTECH */
{n:"Integra Bar x10",p:25200,b:"INTEGRA"},
{n:"Vitalgy Chocolate x10",p:21000,b:"VITALGY"},
{n:"Vitalgy Arandanos x10",p:14000,b:"VITALGY"},
{n:"Vitalgy Cajú x10",p:14000,b:"VITALGY"},
{n:"Vitalgy Manzana x10",p:14000,b:"VITALGY"},
{n:"Vitalgy Cacao x10",p:14000,b:"VITALGY"},
{n:"Iron Bar x20",p:49000,b:"GENTECH"},

/* ENTRENUTS */
{n:"Pasta de Maní 370g",p:4200,b:"ENTRENUTS"},
{n:"Pasta Proteica Cookies",p:5600,b:"ENTRENUTS"},

/* GRANGER */
{n:"Pancakes 400g",p:14000,b:"GRANGER"},

/* STAR */
{n:"Creatina 300g FR",p:28000,b:"STAR"},
{n:"Creatina 300g NEUTRA",p:25200,b:"STAR"},
{n:"Whey 2Lb",p:63000,b:"STAR"},
{n:"Platinum 2Lb",p:67200,b:"STAR"},
{n:"Just Plant 2Lb",p:49000,b:"STAR"},
{n:"Mutan Mass 5kg",p:133000,b:"STAR"},
{n:"BCAA 270g",p:35000,b:"STAR"},
{n:"Glutamina 300g",p:33600,b:"STAR"},
{n:"Pump V8",p:35000,b:"STAR"},
{n:"Carnitina",p:16800,b:"STAR"},
{n:"Crea 1kg",p:98000,b:"STAR"},

/* ENA */
{n:"Whey 2Lb ENA",p:64400,b:"ENA"},
{n:"Ultra Mass 3kg",p:92400,b:"ENA"},
{n:"Creatina ENA",p:28000,b:"ENA"},
{n:"Pre War",p:36400,b:"ENA"},
{n:"ZMA",p:15400,b:"ENA"},
{n:"Carnitina x60",p:18200,b:"ENA"},

/* NUTREMAX */
{n:"Cafeina 200",p:18200,b:"NUTREMAX"},
{n:"Creatina 200g",p:21000,b:"NUTREMAX"},
{n:"Energy Gel x12",p:21000,b:"NUTREMAX"},
{n:"Recovery Drink",p:44800,b:"NUTREMAX"},

/* ONEFIT */
{n:"Whey One Fit",p:42000,b:"ONEFIT"},
{n:"Creatina 500g",p:33600,b:"ONEFIT"},
{n:"Gainer 1.5kg",p:42000,b:"ONEFIT"},

/* GOLD */
{n:"Whey Gold 2Lb",p:84000,b:"GOLD"},
{n:"Omega 3 Gold",p:35000,b:"GOLD"},

/* XTRENGHT */
{n:"Whey 3kg XTRENGHT",p:210000,b:"XTRENGHT"},
{n:"Nitrogain 5kg",p:119000,b:"XTRENGHT"},

/* GEONAT */
{n:"Ashwagandha",p:18200,b:"GEONAT"},
{n:"Omega 3 Geonat",p:25200,b:"GEONAT"},

/* XBODY / HTN / MERVICK / MAX FORCE / SQUADRA */
{n:"Whey XBODY 2lb",p:70000,b:"XBODY"},
{n:"Creatina HTN 500g",p:36400,b:"HTN"},
{n:"Protein Bar Mervick",p:23800,b:"MERVICK"},
{n:"Whey Max Force 3kg",p:77000,b:"MAX FORCE"},
{n:"Colageno Squadra",p:30800,b:"SQUADRA"}

];

const store=document.getElementById("store");
const search=document.getElementById("search");
const filter=document.getElementById("filter");

function render(){
let q=search.value.toLowerCase();
let f=filter.value;

store.innerHTML="";

products
.filter(p=>p.n.toLowerCase().includes(q) && (f==="all" || p.b===f))
.forEach(p=>{
store.innerHTML+=`
<div class="card">
<div class="tag">${p.b}</div>
<h3>${p.n}</h3>
<div class="price">$${p.p}</div>
<a class="btn" href="https://wa.me/5493425683418?text=Quiero%20${encodeURIComponent(p.n)}" target="_blank">
COMPRAR
</a>
</div>
`;
});
}

search.oninput=render;
filter.onchange=render;
render();
</script>

</body>
</html>
