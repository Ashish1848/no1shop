<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>WIN Gaming</title>

<style>
body{
    margin:0;
    font-family:'Segoe UI',sans-serif;
    background:#0b1220;
    color:white;
}
header{
    background:#020617;
    padding:15px;
    display:flex;
    justify-content:space-between;
    align-items:center;
}
header h1{margin:0;color:#22c55e}
header span{
    background:#16a34a;
    padding:6px 14px;
    border-radius:20px;
    color:black;
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
    font-weight:600;
}
.container{padding:15px}
.card{
    background:#020617;
    padding:15px;
    border-radius:14px;
    margin-bottom:15px;
}
.btn{
    width:100%;
    padding:12px;
    margin-top:10px;
    border:none;
    border-radius:10px;
    background:#22c55e;
    font-weight:bold;
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
.games{
    display:grid;
    grid-template-columns:repeat(2,1fr);
    gap:12px;
}
.game{
    background:#111827;
    padding:15px;
    border-radius:14px;
    text-align:center;
}
#loginBox{max-width:360px;margin:80px auto}
#app{display:none}
#qrBox{display:none;text-align:center}
footer{
    text-align:center;
    padding:15px;
    font-size:13px;
    background:#020617;
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
</style>
</head>

<body>

<!-- LOGIN -->
<div id="loginBox" class="card">
<h2>🔐 WIN Login</h2>
<input id="user" placeholder="Username / Mobile">
<input id="pass" type="password" placeholder="Password">
<button class="btn" onclick="login()">Login</button>
</div>

<!-- APP -->
<div id="app">

<header>
<h1>WIN</h1>
<span>₹ <span id="bal">500</span></span>
</header>

<nav>
<a href="#games">Games</a>
<a href="#wallet">Wallet</a>
<a onclick="logout()">Logout</a>
</nav>

<div class="container">

<section class="card">
<h3>🔥 Trusted Real Gaming Platform</h3>
<p>Play Games & Earn Real Money</p>
</section>

<section id="wallet" class="card">
<h3>💰 Wallet</h3>
<button class="btn" onclick="showQR()">➕ Deposit</button>
<button class="btn" onclick="withdraw()">➖ Withdraw</button>

<div id="qrBox">
<p>Scan & Pay</p>
<!-- 👇 अपना QR IMAGE यहाँ डाल देना -->
<a href="https://imgbb.com/"><img src="https://i.ibb.co/cc9btq3j/2222.jpg" alt="2222" border="0" /></a> <br>
<input id="amt" placeholder="Enter Amount">
<button class="btn" onclick="deposit()">Submit Request</button>
</div>
</section>

<section id="games">
<h3>🎮 Games</h3>

<div class="games">
<div class="game">
✈️<br><b>Aviator</b>
<button class="btn" onclick="aviator()">Play</button>
</div>

<div class="game">
🎨<br><b>Color Game</b>
<button class="btn" onclick="colorGame()">Play</button>
</div>

<div class="game">
🎲<br><b>Dice</b>
<button class="btn" onclick="dice()">Play</button>
</div>

<div class="game">
🎡<br><b>Spin</b>
<button class="btn" onclick="spin()">Play</button>
</div>
</div>

<p id="result"></p>
</section>

</div>

<footer>© 2025 WIN Gaming</footer>

<div class="fixed-whatsapp">
<a href="https://wa.me/918816058313">WhatsApp</a>
</div>

</div>

<script>
let balance = 500;
const bal = document.getElementById("bal");
const res = document.getElementById("result");

function login(){
 document.getElementById("loginBox").style.display="none";
 document.getElementById("app").style.display="block";
}

function logout(){
 location.reload();
}

function update(){ bal.innerText = balance }

function showQR(){
 document.getElementById("qrBox").style.display="block";
}

function deposit(){
 alert("Deposit request sent ₹"+amt.value+"\n(Admin approval pending)");
}

function withdraw(){
 alert("Withdraw request sent");
}

function aviator(){
 let m=(Math.random()*3+1).toFixed(2);
 balance+=20;
 res.innerText="✈️ Crash at "+m+"x | +₹20";
 update();
}

function colorGame(){
 if(Math.random()>0.5){balance+=10;res.innerText="🎨 You Won +₹10";}
 else{balance-=10;res.innerText="🎨 You Lost -₹10";}
 update();
}

function dice(){
 let d=Math.floor(Math.random()*6)+1;
 balance+=d;
 res.innerText="🎲 Dice "+d+" | +₹"+d;
 update();
}

function spin(){
 let p=Math.floor(Math.random()*50);
 balance+=p;
 res.innerText="🎡 Spin Won ₹"+p;
 update();
}
</script>

</body>
</html>
