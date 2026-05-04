<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>LUNA STORE</title>

<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@500&family=Montserrat:wght@300;400&display=swap" rel="stylesheet">

<style>

body {
    margin: 0;
    font-family: 'Montserrat', sans-serif;
    color: #111;
}

/* HEADER */
header {
    display: flex;
    justify-content: space-between;
    padding: 20px 50px;
    border-bottom: 1px solid #eee;
}

.logo {
    font-family: 'Playfair Display', serif;
    font-size: 24px;
}

nav a {
    margin-left: 20px;
    text-decoration: none;
    color: black;
    font-size: 13px;
}

/* CARRITO ICONO */
.cart {
    cursor: pointer;
    font-size: 14px;
}

.cart span {
    background: black;
    color: white;
    padding: 2px 6px;
    font-size: 11px;
    margin-left: 5px;
}

/* HERO */
.hero {
    height: 90vh;
    background: url('https://images.unsplash.com/photo-1520975916090-3105956dac38') center/cover no-repeat;
    display: flex;
    justify-content: center;
    align-items: center;
}

.hero-text {
    color: white;
    text-align: center;
}

.hero-text h1 {
    font-size: 48px;
    font-family: 'Playfair Display', serif;
}

/* PRODUCTOS */
.productos {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    padding: 40px;
    gap: 25px;
}

.producto img {
    width: 100%;
}

.producto h3 {
    font-size: 14px;
}

.producto p {
    color: #666;
    font-size: 13px;
}

/* BOTÓN */
.btn {
    border: 1px solid black;
    padding: 6px 12px;
    font-size: 12px;
    cursor: pointer;
    transition: 0.3s;
}

.btn:hover {
    background: black;
    color: white;
}

/* CARRITO PANEL */
.cart-panel {
    position: fixed;
    right: -350px;
    top: 0;
    width: 350px;
    height: 100%;
    background: white;
    border-left: 1px solid #eee;
    padding: 20px;
    transition: 0.4s;
}

.cart-panel.active {
    right: 0;
}

.cart-item {
    display: flex;
    justify-content: space-between;
    margin-bottom: 10px;
}

.total {
    margin-top: 20px;
    font-weight: bold;
}

/* RESPONSIVE */
@media(max-width:600px){
    header {
        flex-direction: column;
        align-items: center;
    }
}

</style>
</head>
<body>

<header>
    <div class="logo">LUNA STORE</div>

    <nav>
        <a href="#">NUEVO</a>
        <a href="#">VESTIDOS</a>
        <a href="#">CONJUNTOS</a>
    </nav>

    <div class="cart" onclick="toggleCart()">
        🛒 Carrito <span id="count">0</span>
    </div>
</header>

<section class="hero">
    <div class="hero-text">
        <h1>Nueva Colección</h1>
        <p>Elegancia minimalista</p>
    </div>
</section>

<section class="productos">

    <div class="producto">
        <img src="https://images.unsplash.com/photo-1520975661595-6453be3f7070" alt="">
        <h3>Vestido Satinado</h3>
        <p>S/ 129</p>
        <button class="btn" onclick="addToCart('Vestido Satinado',129)">Comprar</button>
    </div>

    <div class="producto">
        <img src="https://images.unsplash.com/photo-1521334884684-d80222895322" alt="">
        <h3>Blusa Elegante</h3>
        <p>S/ 75</p>
        <button class="btn" onclick="addToCart('Blusa Elegante',75)">Comprar</button>
    </div>

    <div class="producto">
        <img src="https://images.unsplash.com/photo-1490481651871-ab68de25d43d" alt="">
        <h3>Conjunto Beige</h3>
        <p>S/ 160</p>
        <button class="btn" onclick="addToCart('Conjunto Beige',160)">Comprar</button>
    </div>

</section>

<!-- PANEL CARRITO -->
<div class="cart-panel" id="cartPanel">
    <h3>Carrito</h3>
    <div id="cartItems"></div>
    <div class="total" id="total">Total: S/ 0</div>
</div>

<script>

let cart = [];

function toggleCart(){
    document.getElementById("cartPanel").classList.toggle("active");
}

function addToCart(nombre, precio){
    cart.push({nombre, precio});
    renderCart();
}

function renderCart(){
    let items = document.getElementById("cartItems");
    let total = 0;

    items.innerHTML = "";

    cart.forEach(item => {
        items.innerHTML += `
        <div class="cart-item">
            <span>${item.nombre}</span>
            <span>S/ ${item.precio}</span>
        </div>`;
        total += item.precio;
    });

    document.getElementById("total").innerText = "Total: S/ " + total;
    document.getElementById("count").innerText = cart.length;
}

</script>

</body>
</html>
