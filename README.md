<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Olympus Suplementos</title>

<style>
body{
margin:0;
font-family:Arial;
background:#0e0e0e;
color:#fff;
}

header{
padding:18px;
text-align:center;
background:#151515;
}

h1{
color:#f5c542;
margin:0;
font-size:18px;
}

input, select{
padding:10px;
margin:6px;
width:95%;
max-width:420px;
border-radius:8px;
border:none;
font-size:14px;
}

.container{
display:grid;
grid-template-columns:repeat(auto-fit,minmax(160px,1fr));
gap:10px;
padding:10px;
max-width:1200px;
margin:auto;
}

.card{
background:#1c1c1c;
padding:10px;
border-radius:10px;
border:1px solid #333;
display:flex;
flex-direction:column;
}

.tag{
font-size:11px;
color:#ffcc00;
opacity:0.8;
}

.price{
color:#00ff99;
font-weight:bold;
margin:6px 0;
}

.btn{
background:#25d366;
color:#fff;
padding:8px;
border:none;
border-radius:8px;
cursor:pointer;
margin-top:6px;
font-size:12px;
}

.cart{
position:fixed;
left:8px;
right:8px;
bottom:8px;
background:#111;
padding:10px;
border-radius:10px;
max-height:200px;
overflow:auto;
font-size:12px;
border:1px solid #333;
}

.cart h3{
margin:0 0 8px 0;
color:#f5c542;
}

.cart-item{
display:flex;
justify-content:space-between;
border-bottom:1px solid #222;
padding:4px 0;
}

.whatsapp{
position:fixed;
bottom:18px;
right:10px;
background:#25d366;
padding:12px;
border-radius:50px;
color:#fff;
text-decoration:none;
font-size:12px;
}

.instagram{
position:fixed;
bottom:75px;
right:10px;
background:linear-gradient(45deg,#f58529,#dd2a7b,#8134af);
padding:12px;
border-radius:50px;
color:#fff;
text-decoration:none;
font-size:12px;
}
</style>
</head>

<body>

<header>
<h1>🔥 OLYMPUS SUPLEMENTOS</h1>

<input id="search" placeholder="Buscar producto...">

<select id="filter">
<option value="all">Todas las marcas</option>
<option value="INTEGRA">INTEGRA</option>
<option value="VITALGY">VITALGY</option>
<option value="GENTECH">GENTECH</option>
<option value="STAR">STAR</option>
<option value="ENA">ENA</option>
<option value="NUTREMAX">NUTREMAX</option>
<option value="ONEFIT">ONEFIT</option>
<option value="GOLD">GOLD</option>
<option value="GEONAT">GEONAT</option>
<option value="XBODY">XBODY</option>
<option value="HTN">HTN</option>
<option value="MERVICK">MERVICK</option>
<option value="MAX FORCE">MAX FORCE</option>
<option value="SQUADRA">SQUADRA</option>
</select>
</header>

<div class="container" id="store"></div>

<div class="cart">
<h3>🛒 Carrito</h3>
<div id="cartItems"></div>
<h4>Total: $<span id="total">0</span></h4>
<button class="btn" onclick="checkout()">FINALIZAR COMPRA</button>
</div>

<a class="whatsapp" href="https://wa.me/5493425842765">WhatsApp</a>
<a class="instagram" href="https://instagram.com/olympus.suplementossf">Instagram</a>

<script>

const products = [

{n:"Integra Bar x10",p:25200,b:"INTEGRA"},
{n:"Vitalgy Bar x10",p:21000,b:"VITALGY"},
{n:"Vitalgy Arandanos x10",p:14000,b:"VITALGY"},
{n:"Vitalgy Cajú x10",p:14000,b:"VITALGY"},
{n:"Vitalgy Manzana x10",p:14000,b:"VITALGY"},
{n:"Vitalgy Cacao x10",p:14000,b:"VITALGY"},

{n:"Iron Bar x20",p:49000,b:"GENTECH"},

{n:"Pasta de Maní 370g",p:4200,b:"ENTRENUTS"},
{n:"Pasta Proteica Cookies",p:5600,b:"ENTRENUTS"},

{n:"Pancakes 400g",p:14000,b:"GRANGER"},

{n:"Creatina 300g",p:28000,b:"STAR"},
{n:"Whey 2Lb",p:63000,b:"STAR"},
{n:"Mutan Mass 5kg",p:133000,b:"STAR"},
{n:"Glutamina 300g",p:33600,b:"STAR"},
{n:"Carnitina",p:16800,b:"STAR"},

{n:"Whey ENA 2Lb",p:64400,b:"ENA"},
{n:"Ultra Mass 3kg",p:92400,b:"ENA"},
{n:"Pre War",p:36400,b:"ENA"},
{n:"Creatina ENA",p:28000,b:"ENA"},

{n:"Cafeina 200",p:18200,b:"NUTREMAX"},
{n:"Creatina 200g",p:21000,b:"NUTREMAX"},
{n:"Energy Gel x12",p:21000,b:"NUTREMAX"},

{n:"Whey ONEFIT",p:42000,b:"ONEFIT"},
{n:"Creatina 500g",p:33600,b:"ONEFIT"},
{n:"Gainer 1.5kg",p:42000,b:"ONEFIT"},

{n:"Whey GOLD 2Lb",p:84000,b:"GOLD"},
{n:"Omega 3",p:35000,b:"GOLD"},

{n:"Ashwagandha",p:18200,b:"GEONAT"},
{n:"Omega 3 GEONAT",p:25200,b:"GEONAT"},

{n:"Whey XBODY 2lb",p:70000,b:"XBODY"},
{n:"Creatina HTN 500g",p:36400,b:"HTN"},
{n:"Protein Bar MERVICK",p:23800,b:"MERVICK"},
{n:"Whey MAX FORCE 3kg",p:77000,b:"MAX FORCE"},
{n:"Colageno SQUADRA",p:30800,b:"SQUADRA"}

];

let cart = [];

function add(n,p){
cart.push({n,p});
render();
}

function remove(i){
cart.splice(i,1);
render();
}

function total(){
return cart.reduce((a,b)=>a+b.p,0);
}

function render(){

let s = document.getElementById("store");
let q = document.getElementById("search").value.toLowerCase();
let f = document.getElementById("filter").value;

s.innerHTML = "";

products
.filter(p => p.n.toLowerCase().includes(q) && (f === "all" || p.b === f))
.forEach(p => {
s.innerHTML += `
<div class="card">
<div class="tag">${p.b}</div>
<div>${p.n}</div>
<div class="price">$${p.p}</div>
<button class="btn" onclick="add('${p.n}',${p.p})">AGREGAR</button>
</div>`;
});

document.getElementById("cartItems").innerHTML =
cart.map((p,i)=>`
<div class="cart-item">
<span>${p.n}</span>
<span>$${p.p} <button onclick="remove(${i})">X</button></span>
</div>
`).join("");

document.getElementById("total").innerText = total();
}

function checkout(){
let msg = "🛒 PEDIDO OLYMPUS:%0A%0A";

cart.forEach(p=>{
msg += "✔ " + p.n + " $" + p.p + "%0A";
});

msg += "%0A💰 TOTAL: $" + total();

window.open("https://wa.me/5493425842765?text=" + msg, "_blank");
}

render();

</script>

</body>
</html>
