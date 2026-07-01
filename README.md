<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>OLYMPUS SUPLEMENTOS SF</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
</head>
<body class="bg-gray-100 font-sans">

  <!-- Header -->
  <header class="bg-black text-white py-6 text-center shadow-lg">
    <h1 class="text-3xl font-bold">OLYMPUS SUPLEMENTOS SF</h1>
    <nav class="mt-2">
      <a href="#productos" class="mx-3 hover:text-green-400">Productos</a>
      <a href="https://www.instagram.com/olympus.suplementossf" target="_blank" class="mx-3 hover:text-green-400">Instagram</a>
    </nav>
  </header>

  <!-- Hero -->
  <section class="bg-cover bg-center h-96 flex items-center justify-center text-white text-4xl font-bold shadow-inner" style="background-image: url('placeholder.jpg');">
    ¡Potencia tu rendimiento!
  </section>

  <!-- Productos -->
  <section id="productos" class="py-12 px-6">
    <h2 class="text-2xl font-bold text-center mb-8">Catálogo de Productos</h2>

    <!-- INTEGRA BAR -->
    <div class="border rounded mb-4">
      <button onclick="toggleSection('integra')" class="w-full text-left px-4 py-2 bg-black text-white font-bold">
        INTEGRA BAR
      </button>
      <div id="integra" class="hidden px-6 py-4 bg-gray-50">
        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
          <div class="bg-white shadow rounded p-4 text-center">
            <img src="placeholder.jpg" alt="Barra proteica" class="mx-auto mb-2 rounded">
            <h3 class="font-semibold">Barra proteica x10 (Maní/Chocolate)</h3>
            <p class="text-green-600 font-bold">$25.200</p>
            <button onclick="agregarCarrito('Barra proteica x10', 25200)" class="mt-2 bg-green-500 text-white px-4 py-2 rounded">Agregar al carrito</button>
          </div>
        </div>
      </div>
    </div>

    <!-- VITALGY BAR -->
    <div class="border rounded mb-4">
      <button onclick="toggleSection('vitalgy')" class="w-full text-left px-4 py-2 bg-black text-white font-bold">
        VITALGY BAR
      </button>
      <div id="vitalgy" class="hidden px-6 py-4 bg-gray-50">
        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
          <div class="bg-white shadow rounded p-4 text-center">
            <img src="placeholder.jpg" alt="Barra proteica chocolate" class="mx-auto mb-2 rounded">
            <h3 class="font-semibold">Barra Proteica x10 (Chocolate)</h3>
            <p class="text-green-600 font-bold">$21.000</p>
            <button onclick="agregarCarrito('Barra Proteica Chocolate x10', 21000)" class="mt-2 bg-green-500 text-white px-4 py-2 rounded">Agregar al carrito</button>
          </div>
          <div class="bg-white shadow rounded p-4 text-center">
            <img src="placeholder.jpg" alt="Barra arándanos" class="mx-auto mb-2 rounded">
            <h3 class="font-semibold">Arándanos x10</h3>
            <p class="text-green-600 font-bold">$14.000</p>
            <button onclick="agregarCarrito('Arándanos x10', 14000)" class="mt-2 bg-green-500 text-white px-4 py-2 rounded">Agregar al carrito</button>
          </div>
          <div class="bg-white shadow rounded p-4 text-center">
            <img src="placeholder.jpg" alt="Barra cajú" class="mx-auto mb-2 rounded">
            <h3 class="font-semibold">Cajú x10</h3>
            <p class="text-green-600 font-bold">$14.000</p>
            <button onclick="agregarCarrito('Cajú x10', 14000)" class="mt-2 bg-green-500 text-white px-4 py-2 rounded">Agregar al carrito</button>
          </div>
          <div class="bg-white shadow rounded p-4 text-center">
            <img src="placeholder.jpg" alt="Barra manzana" class="mx-auto mb-2 rounded">
            <h3 class="font-semibold">Manzana x10</h3>
            <p class="text-green-600 font-bold">$14.000</p>
            <button onclick="agregarCarrito('Manzana x10', 14000)" class="mt-2 bg-green-500 text-white px-4 py-2 rounded">Agregar al carrito</button>
          </div>
          <div class="bg-white shadow rounded p-4 text-center">
            <img src="placeholder.jpg" alt="Barra cacao" class="mx-auto mb-2 rounded">
            <h3 class="font-semibold">Cacao x10</h3>
            <p class="text-green-600 font-bold">$14.000</p>
            <button onclick="agregarCarrito('Cacao x10', 14000)" class="mt-2 bg-green-500 text-white px-4 py-2 rounded">Agregar al carrito</button>
          </div>
        </div>
      </div>
    </div>

    <!-- Aquí continúan los bloques para cada marca: GENTECH, STAR, ENA, NUTREMAX, ONE FIT, XBODY, HTN, XTRENGHT, GOLD, QUELOPALEÓ, MERVICK, MAX FORCE, GEONAT, SQUADRA -->
    <!-- Cada producto con su precio final (+40%) y placeholder de imagen -->
  </section>

  <!-- Carrito -->
  <section id="carrito" class="py-12 px-6 bg-gray-200">
    <h2 class="text-2xl font-bold text-center mb-8">Carrito de Compras</h2>
    <div id="listaCarrito" class="max-w-xl mx-auto bg-white p-6 rounded-lg shadow-lg">
      <ul id="itemsCarrito" class="mb-4"></ul>
      <p class="text-lg font-bold">Total: $<span id="totalCarrito">0</span></p>
      <a id="whatsappLink" href="#" target="_blank" class="mt-4 inline-block bg-green-500 text-white px-6 py-2 rounded hover:bg-green-600">Finalizar por WhatsApp</a>
    </div>
  </section>

  <!-- Footer -->
  <footer class="bg-black text-white text-center py-6 mt-12">
    <p>© 2026 OLYMPUS SUPLEMENTOS SF</p>
    <p>Síguenos en <a href="https://www.instagram.com/olympus.suplementossf" target="_blank" class="text-green-400 hover:underline">Instagram</a></p>
  </footer>

  <!-- Botón flotante WhatsApp -->
  <a href="https://wa.me/5493425842765" target="_blank" class="fixed bottom-6 right-6 bg-green-500 text-white w-16 h-16 rounded-full flex items-center justify-center shadow-lg hover:bg-green-600 transition">
    <i class="fab fa-whatsapp text-3xl"></i>
  </a>

  <!-- Script Carrito -->
  <script>
    let carrito = [];
    let total = 0;

    function agregarCarrito(producto, precio) {
      carrito.push({producto, precio});
      total += precio;
      actualizarCarrito();
    }

    function actualizarCarrito() {
      const itemsCarrito = document.getElementById('itemsCarrito');
      itemsCarrito.innerHTML = '';
      carrito.forEach(item => {
        const li = document.createElement('li');
        li.textContent = `${item.producto} - $${item.precio}`;
        itemsCarrito.appendChild(li);
      });
      document.getElementById('totalCarrito').textContent = total;

      const mensaje = carrito.map(item => `${item.producto} - $${item.precio}`).join('%0A');
      const link = `https://wa.me/5493425842765?text=Hola! Quiero
