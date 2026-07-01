<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Tienda Olympus Suplementos</title>

<style>
body{
margin:0;
font-family:Arial;
background:#0e0e0e;
color:#fff;
}

header{
padding:30px;
text-align:center;
background:#151515;
}

h1{color:#f5c542;margin:0}

input, select{
padding:10px;
margin:10px;
width:90%;
max-width:400px;
border-radius:8px;
border:none;
outline:none;
}

.container{
display:grid;
grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
gap:15px;
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
margin:10px 0;
}

.tag{
font-size:12px;
opacity:0.8;
color:#ffcc00;
}

.btn{
display:inline-block;
background:#25d366;
color:#fff;
padding:10px;
text-align:center;
border-radius:8px;
text-decoration:none;
margin-top:10px;
font-weight:bold;
}

.section{
padding:30px;
text-align:center;
}

.whatsapp{
position:fixed;
bottom:20px;
right:20px;
background:#25d366;
padding:15px;
border-radius:50px;
color:#fff;
text-decoration:none;
font-weight:bold;
z-index:999;
}

.instagram{
position:fixed;
bottom:80px;
right:20px;
background:linear-gradient(45deg,#f58529,#dd2a7b,#8134af);
padding:15px;
border-radius:50px;
color:#fff;
text-decoration:none;
font-weight:bold;
z-index:999;
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
</select>
</header>

<div class="container" id="store"></div>

<!-- INSTAGRAM -->
<section class="section">
<h2>📲 Instagram oficial</h2>
<p>Seguinos para ofertas y novedades</p>
<a class="btn" href="https://instagram.com/olympus.suplementossf" target="_blank">
IR A INSTAGRAM
</a>
</section>

<!-- WHATSAPP FLOAT -->
<a class="whatsapp" href="https://wa.me/5493425683418?text=Hola%20quiero%20info%20de%20los%20productos" target="_blank">
WhatsApp
</a>

<!-- INSTAGRAM FLOAT -->
<a class="instagram" href="https://instagram.com/olympus.suplementossf" target="_blank">
Instagram
</a>

<script>
const products = [
{n:"Integra Bar x10",p:25200,b:"INTEGRA"},
{n:"Vitalgy Chocolate x10",p:21000,b:"VITALGY"},
{n:"Vitalgy Arandanos x10",p:14000,b:"VITALGY"},
{n:"Vitalgy Cajú x10",p:14000,b:"VITALGY"},
{n:"Vitalgy Manzana x10",p:14000,b:"VITALGY"},
{n:"Vitalgy Cacao x10",p:14000,b:"VITALGY"},
{n:"Iron Bar x20",p:49000,b:"GENTECH"},

{n:"Whey 2Lb Star",p:63000,b:"STAR"},
{n:"Creatina Star Frutos Rojos",p:28000,b:"STAR"},
{n:"Mutan Mass 5kg",p:133000,b:"STAR"},

{n:"Whey ENA 2Lb",p:64400,b:"ENA"},
{n:"Ultra Mass 3k",p:92400,b:"ENA"},
{n:"Creatina ENA",p:28000,b:"ENA"},

{n:"Cafeína Nutremax",p:18200,b:"NUTREMAX"},
{n:"Creatina Nutremax",p:21000,b:"NUTREMAX"},
{n:"Energy Gel x12",p:21000,b:"NUTREMAX"},

{n:"Whey One Fit",p:42000,b:"ONEFIT"},
{n:"Creatina One Fit 500g",p:33600,b:"ONEFIT"},
{n:"Gainer One Fit",p:42000,b:"ONEFIT"},

{n:"Gold Whey 2Lb",p:84000,b:"GOLD"},
{n:"Omega 3 Gold",p:35000,b:"GOLD"},

{n:"Xtenght Whey 3k",p:210000,b:"XTRENGHT"},
{n:"Nitrogain 5k",p:119000,b:"XTRENGHT"},

{n:"Ashwagandha Geonat",p:18200,b:"GEONAT"},
{n:"Omega 3 Geonat",p:25200,b:"GEONAT"},
];

const store=document.getElementById("store");
const search=document.getElementById("search");
const filter=document.getElementById("filter");

function render(){
let q=search.value.toLowerCase();
let f=filter.value;

store.innerHTML="";

products
.filter(p=>{
return p.n.toLowerCase().includes(q) &&
(f==="all" || p.b===f);
})
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
