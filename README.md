<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>WIN Gaming</title>

<style>
body{
  margin:0;
  font-family:Segoe UI, sans-serif;
  background:#0b1220;
  color:#fff;
}
header{
  background:#111827;
  padding:12px;
  display:flex;
  justify-content:space-between;
  align-items:center;
}
header h1{margin:0;color:#22c55e;font-size:20px;}
header span{
  background:#16a34a;
  padding:5px 10px;
  border-radius:20px;
  font-size:13px;
}

nav{
  display:flex;
  justify-content:space-around;
  background:#020617;
  padding:10px 0;
  position:sticky;
  bottom:0;
}

nav a{color:#fff;text-decoration:none;font-size:14px;}

.container{padding:12px;}

.card{
  background:#020617;
  padding:12px;
  border-radius:12px;
  margin-bottom:12px;
}

.btn{
  display:block;
  text-align:center;
  background:#22c55e;
  color:#000;
  padding:14px;
  border-radius:10px;
  font-weight:bold;
  margin-top:10px;
}

.games{
  display:grid;
  grid-template-columns:repeat(2,1fr);
  gap:10px;
}
.game{
  background:#111827;
  padding:12px;
  border-radius:12px;
  text-align:center;
}

input{
  width:100%;
  padding:14px;
  margin-top:8px;
  border-radius:8px;
  border:none;
  background:#111827;
  color:white;
  font-size:16px;
}

.wallet{
  display:flex;
  justify-content:space-between;
  background:linear-gradient(45deg,#16a34a,#22c55e);
  padding:14px;
  border-radius:12px;
  color:black;
}

.fixed-whatsapp{
  position:fixed;
  bottom:70px;
  right:15px;
  background:#25D366;
  padding:12px 16px;
  border-radius:50px;
}

footer{
  text-align:center;
  padding:12px;
  font-size:12px;
  background:#020617;
}
</style>
</head>

<body>

<header>
  <h1>WIN</h1>
  <span id="walletAmount">Wallet ₹0</span>
</header>

<nav>
  <a href="#home">Home</a>
  <a href="#games">Games</a>
  <a href="#wallet">Wallet</a>
  <a href="#login">Login</a>
</nav>

<div class="container">

<section id="home" class="card">
  <h3>🔥 Trusted Gaming Platform</h3>
  <p>Play & Earn (Demo Games)</p>
</section>

<section id="games" class="card">
  <h3>🎮 Games</h3>
  <div class="games">
    <div class="game">✈️ Aviator<br><a class="btn" onclick="playGame()">Play</a></div>
    <div class="game">🎨 Color<br><a class="btn" onclick="playGame()">Play</a></div>
    <div class="game">🎲 Dice<br><a class="btn" onclick="playGame()">Play</a></div>
    <div class="game">🃏 Card<br><a class="btn" onclick="playGame()">Play</a></div>
  </div>
</section>

<section id="wallet" class="card">
  <h3>💰 Wallet</h3>
  <div class="wallet">
    <div>Balance<br><b id="bal">₹0</b></div>
    <div>Bonus<br><b>₹0</b></div>
  </div>
  <a class="btn" href="#deposit">Deposit</a>
  <a class="btn" href="#withdraw">Withdraw</a>
</section>

<section id="deposit" class="card">
  <h3>➕ Deposit (Request)</h3>
  <input id="depAmount" placeholder="Amount">
  <a class="btn" onclick="deposit()">Submit Request</a>
</section>

<section id="withdraw" class="card">
  <h3>➖ Withdraw (Request)</h3>
  <input id="withAmount" placeholder="Amount">
  <input id="upi" placeholder="UPI ID">
  <a class="btn" onclick="withdraw()">Submit Request</a>
</section>

<section id="login" class="card">
  <h3>🔐 Login / Register</h3>
  <input id="mobile" placeholder="Mobile">
  <input id="password" type="password" placeholder="Password">
  <a class="btn" onclick="login()">Login</a>
</section>

</div>

<div class="fixed-whatsapp">
  <a href="https://wa.me/918816058313" style="color:white;">WhatsApp</a>
</div>

<footer>© 2025 WIN Gaming</footer>

<!-- Firebase -->
<script src="https://www.gstatic.com/firebasejs/9.23.0/firebase-app-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/9.23.0/firebase-auth-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/9.23.0/firebase-firestore-compat.js"></script>

<script>
firebase.initializeApp({
 apiKey:"AIzaSyDA9-9l1QBb6Yjo2GC7n1C03MFyWQv-vvE",
 authDomain:"win-gaming-e5a1e.firebaseapp.com",
 projectId:"win-gaming-e5a1e"
});

const auth=firebase.auth();
const db=firebase.firestore();

function login(){
 let m=mobile.value;
 let p=password.value;
 let e=m+"@win.com";
 auth.signInWithEmailAndPassword(e,p).catch(()=>{
  auth.createUserWithEmailAndPassword(e,p).then(u=>{
   db.collection("users").doc(u.user.uid).set({balance:0});
  });
 });
}

auth.onAuthStateChanged(u=>{
 if(u){
  db.collection("users").doc(u.uid).get().then(d=>{
   let b=d.data().balance;
   bal.innerText="₹"+b;
   walletAmount.innerText="Wallet ₹"+b;
  });
 }
});

function deposit(){
 if(!auth.currentUser)return alert("Login first");
 db.collection("deposits").add({
  uid:auth.currentUser.uid,
  amount:depAmount.value,
  status:"pending"
 });
 alert("Deposit request sent");
}

function withdraw(){
 if(!auth.currentUser)return alert("Login first");
 db.collection("withdraws").add({
  uid:auth.currentUser.uid,
  amount:withAmount.value,
  upi:upi.value,
  status:"pending"
 });
 alert("Withdraw request sent");
}

function playGame(){
 alert("Demo game started 🎮 (Real provider later)");
}
</script>

</body>
</html>
