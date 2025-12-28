<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>WIN Gaming</title>
<style>
body{
    margin:0;
    font-family:Arial, sans-serif;
    background:#0f172a;
    color:white;
}
header{
    background:linear-gradient(45deg,#ff9800,#ff5722);
    padding:15px;
    text-align:center;
    font-size:26px;
    font-weight:bold;
}
nav{
    display:flex;
    justify-content:space-around;
    background:#020617;
    padding:10px 0;
}
nav a{
    color:white;
    text-decoration:none;
    font-weight:bold;
}
section{
    padding:20px;
}
.card{
    background:#020617;
    border-radius:12px;
    padding:15px;
    margin-bottom:15px;
    box-shadow:0 0 10px rgba(0,0,0,0.5);
}
.btn{
    display:inline-block;
    padding:10px 18px;
    background:#22c55e;
    color:black;
    border-radius:8px;
    text-decoration:none;
    font-weight:bold;
}
.games{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(150px,1fr));
    gap:15px;
}
.game{
    background:#111827;
    padding:15px;
    border-radius:10px;
    text-align:center;
}
footer{
    background:#020617;
    text-align:center;
    padding:15px;
    font-size:14px;
}
input{
    width:100%;
    padding:10px;
    margin:8px 0;
    border-radius:6px;
    border:none;
}
</style>
</head>

<body>

<header>🎮 WIN Gaming</header>

<nav>
    <a href="#home">Home</a>
    <a href="#games">Games</a>
    <a href="#login">Login</a>
    <a href="#wallet">Wallet</a>
</nav>

<section id="home">
    <div class="card">
        <h2>🔥 India’s Trusted Gaming Platform</h2>
        <p>खेलिए और जीतिए असली पैसे 💰</p>
        <a class="btn" href="#login">अभी Join करें</a>
    </div>
</section>

<section id="games">
    <h2>🎯 Popular Games</h2>
    <div class="games">
        <div class="game">✈️ Aviator<br><br><a class="btn" href="#">Play</a></div>
        <div class="game">🎨 Color Trading<br><br><a class="btn" href="#">Play</a></div>
        <div class="game">🎲 Dice Game<br><br><a class="btn" href="#">Play</a></div>
        <div class="game">🃏 Card Game<br><br><a class="btn" href="#">Play</a></div>
    </div>
</section>

<section id="login">
    <div class="card">
        <h2>🔐 Login / Register</h2>
        <input type="text" placeholder="Mobile Number">
        <input type="password" placeholder="Password">
        <a class="btn" href="#">Login</a>
    </div>
</section>

<section id="wallet">
    <div class="card">
        <h2>💳 Recharge / Withdraw</h2>
        <p>✔ Minimum Recharge: ₹100</p>
        <p>✔ Fast Withdrawal</p>
        <a class="btn" href="https://wa.me/918816058313">📲 WhatsApp Support</a>
    </div>
</section>

<footer>
    © 2025 WIN Gaming | All Rights Reserved
</footer>

</body>
</html>
