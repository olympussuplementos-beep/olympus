[index.html](https://github.com/user-attachments/files/29574632/index.html)
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
padding:15px;
text-align:center;
background:#151515;
position:sticky;
top:0;
z-index:10;
}

h1{
color:#f5c542;
margin:0;
font-size:18px;
}

input, select{
padding:10px;
margin:5px;
width:95%;
max-width:420px;
border-radius:8px;
border:none;
}

.container{
display:grid;
grid-template-columns:repeat(auto-fit,minmax(170px,1fr));
gap:12px;
padding:15px;
max-width:1200px;
margin:auto;
padding-bottom:220px; /* evita que el carrito tape productos */
}

.card{
background:#1c1c1c;
padding:10px;
border-radius:10px;
border:1px solid #333;
display:flex;
flex-direction:column;
justify-content:space-between;
min-height:120px;
}

.tag{
font-size:11px;
color:#ffcc00;
opacity:0.8;
margin-bottom:4px;
}

.price{
color:#00ff99;
font-weight:bold;
margin:6px 0;
}

.price.consultar{
color:#f5c542;
}

.btn{
background:#25d366;
color:#fff;
padding:8px;
border:none;
border-radius:8px;
cursor:pointer;
margin-top:auto;
font-size:12px;
}

.cart{
position:fixed;
left:10px;
right:10px;
bottom:10px;
background:#111;
padding:12px;
border-radius:12px;
max-height:180px;
overflow:auto;
font-size:12px;
border:1px solid #333;
z-index:20;
}

.cart h3{
margin:0 0 8px 0;
color:#f5c542;
}

.cart-item{
display:flex;
justify-content:space-between;
padding:3px 0;
border-bottom:1px solid #222;
}

.whatsapp{
position:fixed;
bottom:20px;
right:10px;
background:#25d366;
padding:12px;
border-radius:50px;
color:#fff;
text-decoration:none;
font-size:12px;
z-index:30;
}

.instagram{
position:fixed;
bottom:80px;
right:10px;
background:linear-gradient(45deg,#f58529,#dd2a7b,#8134af);
padding:12px;
border-radius:50px;
color:#fff;
text-decoration:none;
font-size:12px;
z-index:30;
}
</style>
</head>

<body>

<header>
<h1>🔥 OLYMPUS SUPLEMENTOS</h1>

<input id="search" placeholder="Buscar producto..." oninput="render()">

<select id="filter" onchange="render()">
<option value="all">Todas las marcas</option>
<option value="INTEGRA">INTEGRA</option>
<option value="VITALGY">VITALGY</option>
<option value="GENTECH">GENTECH</option>
<option value="ENTRENUTS">ENTRENUTS</option>
<option value="GRANGER">GRANGER</option>
<option value="STAR">STAR</option>
<option value="ENA">ENA</option>
<option value="NUTREMAX">NUTREMAX</option>
<option value="ONEFIT">ONE FIT</option>
<option value="XBODY">XBODY</option>
<option value="HTN">HTN</option>
<option value="XTRENGHT">XTRENGHT</option>
<option value="GOLD">GOLD</option>
<option value="QUELOPALEO">QUELOPALEÓ</option>
<option value="MERVICK">MERVICK</option>
<option value="MAX FORCE">MAX FORCE</option>
<option value="GEONAT">GEONAT</option>
<option value="SQUADRA">SQUADRA</option>
</select>
</header>

<div class="container" id="store"></div>

<div class="cart">
<h3>🛒 Carrito</h3>
<div id="cartItems"></div>
<h4>Total: $<span id="total">0</span></h4>
<button onclick="checkout()" style="background:#25d366;border:none;padding:8px;border-radius:8px;color:#fff;width:100%">
FINALIZAR COMPRA
</button>
</div>

<a class="whatsapp" href="https://wa.me/5493425842765">WhatsApp</a>
<a class="instagram" href="https://instagram.com/olympus.suplementossf">Instagram</a>

<script>

const WA_NUMBER = "5493425842765";

const products = [

/* INTEGRA */
{n:"Barra Proteica x10",p:28000,b:"INTEGRA"},

/* VITALGY BAR */
{n:"Barra Proteica x10 (Chocolate)",p:18200,b:"VITALGY"},
{n:"Arandanos x10",p:15400,b:"VITALGY"},
{n:"Cajú x10",p:15400,b:"VITALGY"},
{n:"Manzana x10",p:15400,b:"VITALGY"},
{n:"Cacao x10",p:15400,b:"VITALGY"},

/* GENTECH */
{n:"Iron Bar x20",p:49000,b:"GENTECH"},

/* ENTRENUTS */
{n:"Pasta de Maní 370g (Neutra/Coco/Cacao)",p:4200,b:"ENTRENUTS"},
{n:"Pasta Proteica (Cookies)",p:5600,b:"ENTRENUTS"},

/* GRANGER */
{n:"Pancakes 400g (Chocolate/Vainilla)",p:14000,b:"GRANGER"},

/* STAR */
{n:"Creatina Doypack 300g (Frutos Rojos)",p:28000,b:"STAR"},
{n:"Creatina Doypack 300g (Neutra)",p:25200,b:"STAR"},
{n:"Whey Doypack 2Lb",p:75600,b:"STAR"},
{n:"Platinum 2Lb",p:79800,b:"STAR"},
{n:"Just Plant 2Lb",p:53200,b:"STAR"},
{n:"Just Whey 2Lb",p:81200,b:"STAR"},
{n:"Whey Collagen 2Lb",p:63000,b:"STAR"},
{n:"Mutan Mass 1.5kg",p:54600,b:"STAR"},
{n:"Mtor Bcaa 270g",p:null,b:"STAR"},
{n:"Glutamina 300g",p:36400,b:"STAR"},
{n:"Bcaa 2000 x120",p:null,b:"STAR"},
{n:"Tnt Dinamity",p:30800,b:"STAR"},
{n:"Pump V8",p:37800,b:"STAR"},
{n:"Thermo Fuel",p:26600,b:"STAR"},
{n:"Carnitina",p:18200,b:"STAR"},
{n:"Vit C",p:11200,b:"STAR"},
{n:"Collagen 210g",p:23800,b:"STAR"},
{n:"Collagen Sport/Plus",p:28000,b:"STAR"},
{n:"Omega 3",p:39200,b:"STAR"},
{n:"Shaker Got 700ml",p:12600,b:"STAR"},
{n:"Shaker Corto 500ml",p:12600,b:"STAR"},

/* ENA */
{n:"Whey 100% 2Lb",p:71400,b:"ENA"},
{n:"True Made 2Lb",p:95200,b:"ENA"},
{n:"Ultra Mass 1.5kg",p:60200,b:"ENA"},
{n:"Ultra Mass 3kg",p:105000,b:"ENA"},
{n:"Creatina 300g Doypack (Naranja/Frutos/Neutra)",p:28000,b:"ENA"},
{n:"Creatina + Electrolitos 335g",p:33600,b:"ENA"},
{n:"Pre War 400g",p:36400,b:"ENA"},
{n:"Reload 220g",p:26600,b:"ENA"},
{n:"Oxido Nitrico",p:23800,b:"ENA"},
{n:"Multivitamin x60",p:22400,b:"ENA"},
{n:"Cafeina x60",p:14000,b:"ENA"},
{n:"Magnesio x60",p:16800,b:"ENA"},
{n:"Bcaa 120 cap",p:21000,b:"ENA"},
{n:"Zma 60 cap",p:15400,b:"ENA"},
{n:"Ripped x60 cap",p:15400,b:"ENA"},
{n:"Hidroxy Max",p:16800,b:"ENA"},
{n:"Carnitina x60",p:18200,b:"ENA"},
{n:"Protein Bar x16",p:35000,b:"ENA"},
{n:"Colageno Sport",p:36400,b:"ENA"},

/* NUTREMAX */
{n:"Cafeina 200",p:18200,b:"NUTREMAX"},
{n:"Cafeina Booster",p:16800,b:"NUTREMAX"},
{n:"Pro Salts",p:12600,b:"NUTREMAX"},
{n:"Carnitina",p:21000,b:"NUTREMAX"},
{n:"Beta 1600",p:16800,b:"NUTREMAX"},
{n:"Sport Fuel x10",p:25200,b:"NUTREMAX"},
{n:"Amino Pro 250g",p:25200,b:"NUTREMAX"},
{n:"Caramañola 500cc",p:14000,b:"NUTREMAX"},
{n:"Creatina 200g",p:21000,b:"NUTREMAX"},
{n:"Hidromax 1320",p:23800,b:"NUTREMAX"},
{n:"Hidromax x20",p:16800,b:"NUTREMAX"},
{n:"Energy Gel x12",p:21000,b:"NUTREMAX"},
{n:"Endurance c/Aminos x12",p:28000,b:"NUTREMAX"},
{n:"Extreme Energy x20",p:19600,b:"NUTREMAX"},
{n:"Recovery Drink 1500g",p:44800,b:"NUTREMAX"},
{n:"Recovery Drink x10",p:25200,b:"NUTREMAX"},

/* ONE FIT */
{n:"D3+K2",p:21000,b:"ONEFIT"},
{n:"Multivitaminico",p:18200,b:"ONEFIT"},
{n:"Creatina 200g",p:16800,b:"ONEFIT"},
{n:"Creatina 500g",p:33600,b:"ONEFIT"},
{n:"Gainer 1.5kg",p:42000,b:"ONEFIT"},
{n:"Whey Doypack 2Lb",p:49000,b:"ONEFIT"},
{n:"Colageno 240g",p:21000,b:"ONEFIT"},
{n:"Vitam C 150g",p:12600,b:"ONEFIT"},
{n:"Bcaa 360g",p:25200,b:"ONEFIT"},
{n:"Amino Esenciales 300g",p:28000,b:"ONEFIT"},
{n:"Potasio 150g",p:12600,b:"ONEFIT"},
{n:"Magnesio 150g",p:12600,b:"ONEFIT"},
{n:"Omega 3",p:28000,b:"ONEFIT"},
{n:"Oxido Nitrico 210g",p:22400,b:"ONEFIT"},
{n:"Pre Entreno 300g",p:25200,b:"ONEFIT"},

/* XBODY */
{n:"Whey 2Lb",p:81200,b:"XBODY"},
{n:"Crea 300g",p:22400,b:"XBODY"},
{n:"Crea 1kg",p:77000,b:"XBODY"},

/* HTN */
{n:"Creatina 250g",p:22400,b:"HTN"},
{n:"Creatina 500g",p:36400,b:"HTN"},
{n:"Whey Protein 2Lb",p:63000,b:"HTN"},
{n:"Soy Protein Vegetal",p:53200,b:"HTN"},

/* XTRENGHT */
{n:"Creatina 250g",p:26600,b:"XTRENGHT"},
{n:"Best Whey 2Lb",p:70000,b:"XTRENGHT"},
{n:"Best Whey 3kg",p:210000,b:"XTRENGHT"},
{n:"Advanced Whey 2Lb",p:91000,b:"XTRENGHT"},
{n:"Nitrogain 1.5kg",p:42000,b:"XTRENGHT"},
{n:"Nitrogain 5kg",p:119000,b:"XTRENGHT"},

/* GOLD */
{n:"Whey 2Lb",p:84000,b:"GOLD"},
{n:"Whey 5Lb",p:210000,b:"GOLD"},
{n:"Creatina 300g",p:28000,b:"GOLD"},
{n:"Vegetal Protein Lb",p:49000,b:"GOLD"},
{n:"Vitamin",p:21000,b:"GOLD"},
{n:"Omega 3",p:35000,b:"GOLD"},

/* QUELOPALEÓ */
{n:"Barritas Proteicas x12 (Chocolate Negro)",p:21000,b:"QUELOPALEO"},
{n:"Barritas Proteicas x12 (Chocolate Blanco)",p:21000,b:"QUELOPALEO"},

/* MERVICK */
{n:"Low Carb Bar x12",p:28000,b:"MERVICK"},
{n:"Protein Bar 46g x12",p:23800,b:"MERVICK"},
{n:"Protein Bar 65g x12",p:28000,b:"MERVICK"},
{n:"Race Gel",p:19600,b:"MERVICK"},

/* MAX FORCE */
{n:"Whey 3kg",p:77000,b:"MAX FORCE"},
{n:"Creatina 250g (Neutro)",p:16800,b:"MAX FORCE"},
{n:"Creatina 300g (Sabor)",p:16800,b:"MAX FORCE"},
{n:"Glutamina 250g",p:18200,b:"MAX FORCE"},
{n:"Bcaa 280g (Sabor)",p:21000,b:"MAX FORCE"},
{n:"Colageno 300g (Sabor)",p:21000,b:"MAX FORCE"},
{n:"Multivitam",p:16800,b:"MAX FORCE"},
{n:"Bcaa 120 cap",p:16800,b:"MAX FORCE"},

/* GEONAT */
{n:"Ashwagandha",p:19600,b:"GEONAT"},
{n:"Multivitaminico Goom",p:18200,b:"GEONAT"},
{n:"Colageno (Pastillas)",p:16800,b:"GEONAT"},
{n:"Colageno 375g (7 en 1)",p:33600,b:"GEONAT"},
{n:"Magnesio",p:12600,b:"GEONAT"},
{n:"Citrato de Magnesio",p:15400,b:"GEONAT"},
{n:"Citrato de Magnesio Goom",p:18200,b:"GEONAT"},
{n:"Bisglicinato de Magnesio",p:19600,b:"GEONAT"},
{n:"Treonato de Magnesio",p:22400,b:"GEONAT"},
{n:"Omega 3 (30 comp)",p:14000,b:"GEONAT"},
{n:"Omega 3 (60 comp)",p:25200,b:"GEONAT"},
{n:"Vitamina D",p:12600,b:"GEONAT"},
{n:"Vitamina C",p:11200,b:"GEONAT"},
{n:"Vitamina C Goom x30",p:14000,b:"GEONAT"},
{n:"Probiótico",p:18200,b:"GEONAT"},
{n:"Lax Fibras",p:14000,b:"GEONAT"},
{n:"Resveratrol",p:19600,b:"GEONAT"},
{n:"Melena de León",p:21000,b:"GEONAT"},
{n:"Black Maca",p:21000,b:"GEONAT"},
{n:"Cúrcuma Plus",p:19600,b:"GEONAT"},
{n:"Ginseng",p:19600,b:"GEONAT"},
{n:"Ginkgo Biloba",p:11200,b:"GEONAT"},
{n:"Pell Care",p:18200,b:"GEONAT"},
{n:"Ácido Hialurónico",p:19600,b:"GEONAT"},
{n:"L-Cistina",p:18200,b:"GEONAT"},
{n:"Vitamina B12",p:16800,b:"GEONAT"},

/* SQUADRA */
{n:"Colageno 410g",p:33600,b:"SQUADRA"},
{n:"Whey 1kg",p:47600,b:"SQUADRA"}

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

function consultar(n){
let msg = "Hola, quiero consultar el precio de: " + n;
window.open("https://wa.me/" + WA_NUMBER + "?text=" + encodeURIComponent(msg), "_blank");
}

function render(){

let s = document.getElementById("store");
let q = document.getElementById("search").value.toLowerCase();
let f = document.getElementById("filter").value;

s.innerHTML = "";

products
.filter(p =>
p.n.toLowerCase().includes(q) &&
(f === "all" || p.b === f)
)
.forEach(p=>{
if(p.p === null){
s.innerHTML += `
<div class="card">
<div class="tag">${p.b}</div>
<div>${p.n}</div>
<div class="price consultar">Consultar precio</div>
<button class="btn" onclick='consultar(${JSON.stringify(p.n)})'>CONSULTAR</button>
</div>`;
} else {
s.innerHTML += `
<div class="card">
<div class="tag">${p.b}</div>
<div>${p.n}</div>
<div class="price">$${p.p.toLocaleString("es-AR")}</div>
<button class="btn" onclick='add(${JSON.stringify(p.n)},${p.p})'>AGREGAR</button>
</div>`;
}
});

document.getElementById("cartItems").innerHTML =
cart.map((p,i)=>`
<div class="cart-item">
<span>${p.n}</span>
<span>$${p.p.toLocaleString("es-AR")} <button onclick="remove(${i})">X</button></span>
</div>
`).join("");

document.getElementById("total").innerText = total().toLocaleString("es-AR");
}

function checkout(){
let msg = "🛒 PEDIDO OLYMPUS:\n\n";

cart.forEach(p=>{
msg += "✔ " + p.n + " $" + p.p.toLocaleString("es-AR") + "\n";
});

msg += "\n💰 TOTAL: $" + total().toLocaleString("es-AR");

window.open("https://wa.me/" + WA_NUMBER + "?text=" + encodeURIComponent(msg), "_blank");
}

render();

</script>

</body>
</html>
