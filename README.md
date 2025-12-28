<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>WIN Gaming</title>

<style>
body{
    margin:0;
    font-family: 'Segoe UI', sans-serif;
    background:#0b1220;
    color:#fff;
}
header{
    background:#111827;
    padding:15px;
    display:flex;
    justify-content:space-between;
    align-items:center;
}
header h1{
    margin:0;
    color:#22c55e;
}
header span{
    background:#16a34a;
    padding:6px 12px;
    border-radius:20px;
    font-size:14px;
}

nav{
    display:flex;
    justify-content:space-around;
    background:#020617;
    padding:10px 0;
}
nav a{
    color:#fff;
    text-decoration:none;
    font-weight:600;
}

.container{ padding:15px; }

.card{
    background:#020617;
    padding:15px;
    border-radius:12px;
    margin-bottom:15px;
}

.btn{
    display:block;
    text-align:center;
    background:#22c55e;
    color:#000;
    padding:12px;
    border-radius:10px;
    text-decoration:none;
    font-weight:bold;
    margin-top:10px;
}

.games{
    display:grid;
    grid-template-columns:repeat(2,1fr);
    gap:12px;
}
.game{
    background:#111827;
    padding:15px;
    border-radius:12px;
    text-align:center;
}
.game img{
    width:60px;
    margin-bottom:8px;
}

input{
    width:100%;
    padding:12px;
    margin-top:10px;
    border-radius:8px;
    border:none;
    background:#111827;
    color:white;
}

.wallet{
    display:flex;
    justify-content:space-between;
    background:linear-gradient(45deg,#16a34a,#22c55e);
    padding:15px;
    border-radius:12px;
    color:black;
}

.fixed-whatsapp{
    position:fixed;
    bottom:15px;
    right:15px;
    background:#25D366;
    padding:12px 16px;
    border-radius:50px;
}
.fixed-whatsapp a{
    color:white;
    text-decoration:none;
    font-weight:bold;
}

footer{
    text-align:center;
    padding:15px;
    font-size:13px;
    background:#020617;
}
</style>
</head>

<body>

<header>
    <h1>WIN</h1>
    <span>Wallet ₹500</span>
</header>

<nav>
    <a href="#home">Home</a>
    <a href="#games">Games</a>
    <a href="#wallet">Wallet</a>
    <a href="#login">Login</a>
</nav>

<div class="container">

<section id="home" class="card">
    <h2>🔥 Trusted Real Gaming Platform</h2>
    <p>Play Games & Earn Real Money</p>
    <a class="btn" href="#games">Play Now</a>
</section>

<section id="games">
    <h3>🎮 Games</h3>
    <div class="games">
        <div class="game">
            ✈️<br><b>Aviator</b>
            <a class="btn" href="#">Play</a>
        </div>
        <div class="game">
            🎨<br><b>Color Trading</b>
            <a class="btn" href="#">Play</a>
        </div>
        <div class="game">
            🎲<br><b>Dice</b>
            <a class="btn" href="#">Play</a>
        </div>
        <div class="game">
            🃏<br><b>Card</b>
            <a class="btn" href="#">Play</a>
        </div>
    </div>
</section>

<section id="wallet" class="card">
    <h3>💰 Wallet</h3>
    <div class="wallet">
        <div>
            <b>Balance</b><br>₹500
        </div>
        <div>
            <b>Bonus</b><br>₹50
        </div>
    </div>
    <a class="btn" href="#deposit">Deposit</a>
    <a class="btn" href="#withdraw">Withdraw</a>
</section>

<section id="deposit" class="card">
    <h3>➕ Deposit</h3>
    <input placeholder="Enter Amount">
    <a class="btn" href="#">Pay Now</a>
</section>

<section id="withdraw" class="card">
    <h3>➖ Withdraw</h3>
    <input placeholder="Enter Amount">
    <input placeholder="UPI ID">
    <a class="btn" href="#">Withdraw</a>
</section>

<section id="login" class="card">
    <h3>🔐 Login / Register</h3>
    <input placeholder="Mobile Number">
    <input placeholder="Password">
    <a class="btn" href="#">Login</a>
</section>

</div>

<div class="fixed-whatsapp">
    <a href="https://wa.me/918816058313">WhatsApp</a>
</div>

<footer>
    © 2025 WIN Gaming | All Rights Reserved
</footer>

</body>
</html>
