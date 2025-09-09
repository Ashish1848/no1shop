<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1"/>
<title>WIN — Earn & Play</title>
<meta name="theme-color" content="#16a34a"/>
<style>
  :root{
    --brand:#16a34a; --brand-2:#22c55e; --bg:#0b1020; --text:#f8fafc; --muted:#94a3b8;
    --card:#0f172a; --card-2:#0b1226; --stroke:#1e293b; --shadow:0 10px 30px rgba(0,0,0,.25);
  }
  *{box-sizing:border-box}
  html,body{margin:0;background:var(--bg);color:var(--text);font-family:system-ui,-apple-system,Segoe UI,Roboto,Arial}
  img{max-width:100%;display:block}
  a{color:inherit;text-decoration:none}
  .btn{display:inline-block;background:var(--brand);color:#fff;padding:10px 16px;border-radius:10px;border:0;cursor:pointer}
  .btn.ghost{background:transparent;border:1px solid var(--stroke)}
  .pill{display:inline-flex;gap:8px;align-items:center;background:#0ea5e9;color:#fff;padding:6px 10px;border-radius:999px;font-size:13px}
  .muted{color:var(--muted);}

  /* Header */
  header{position:sticky;top:0;z-index:50;background:rgba(11,16,32,.75);backdrop-filter:blur(10px);border-bottom:1px solid var(--stroke)}
  .nav{max-width:1080px;margin:0 auto;display:flex;align-items:center;justify-content:space-between;padding:10px 14px;gap:10px}
  .brand{font-weight:800}
  .top-left{display:flex;align-items:center;gap:10px;flex-wrap:wrap}
  .top-right{display:flex;align-items:center;gap:8px;flex-wrap:wrap}
  .userbar{display:flex;gap:8px;align-items:center}
  .kv{background:#0a1124;border:1px solid var(--stroke);border-radius:10px;padding:6px 10px;font-size:13px}
  .kv b{color:#e2e8f0}

  /* Sections & containers */
  .wrap{max-width:980px;margin:0 auto;padding:0 14px}
  .section{max-width:1080px;margin:0 auto;padding:10px 14px 18px}
  .container{max-width:580px;margin:16px auto;background:linear-gradient(180deg,#0f172a,#0b1226);border:1px solid var(--stroke);border-radius:14px;padding:16px;box-shadow:var(--shadow)}
  input,button,select{width:100%;padding:12px;border:1px solid var(--stroke);background:#0a1022;color:#e2e8f0;border-radius:10px;margin:8px 0;font-size:16px}

  /* Home */
  .hero{max-width:1080px;margin:0 auto;padding:16px 14px 8px}
  .hero-grid{display:grid;grid-template-columns:1.1fr .9fr;gap:16px}
  .hero-card{background:linear-gradient(160deg,#0b1226,#111936 60%,#0b1226);border:1px solid var(--stroke);border-radius:18px;padding:18px;box-shadow:var(--shadow)}
  .hero h1{margin:0 0 8px;font-size:28px}
  .points{display:flex;gap:8px;flex-wrap:wrap;margin-top:8px}
  .points span{background:#0f1b34;border:1px solid var(--stroke);padding:6px 10px;border-radius:999px;font-size:12px;color:#cbd5e1}
  .hero-img{display:flex;align-items:center;justify-content:center}
  .hero-img img{border-radius:16px;border:1px solid var(--stroke)}

  /* Game grid */
  .grid{display:grid;gap:12px;grid-template-columns:repeat(2,minmax(0,1fr))}
  @media (min-width:900px){ .grid{grid-template-columns:repeat(4,minmax(0,1fr))} }
  .card{background:linear-gradient(180deg,#0f172a,#0b1226);border:1px solid var(--stroke);border-radius:14px;overflow:hidden;box-shadow:var(--shadow)}
  .card .thumb{aspect-ratio:16/10;background:#0a0f1f}
  .card .body{padding:10px}
  .card h3{margin:0 0 6px;font-size:16px}
  .badge{display:inline-block;font-size:11px;background:#052e16;color:#86efac;border:1px solid #064e3b;padding:4px 8px;border-radius:999px;margin-top:6px}
  .card .cta{padding:10px}

  /* Games areas */
  #home,#loginForm,#registerForm,#dashboard,#games,#game-color,#game-spin,#game-quiz,#game-tap,#game-num,#game-mem,#recharge,#withdraw,#history,#admin{display:none}
  .stat{display:flex;gap:8px;margin:10px 0}
  .stat .box{flex:1;background:#0a1124;border:1px solid var(--stroke);border-radius:12px;padding:10px;text-align:center}

  /* Color game UI */
  .row{display:flex;gap:8px;align-items:center;flex-wrap:wrap}
  .roundpill{display:inline-flex;gap:6px;align-items:center;background:#13223e;border:1px solid var(--stroke);padding:6px 10px;border-radius:999px;font-size:13px}
  .timer{font-variant-numeric:tabular-nums}
  .resultbox{margin-top:8px;padding:10px;background:#0a1124;border:1px solid var(--stroke);border-radius:10px}

  /* Overlay lock */
  .lockOverlay{
    position:fixed;inset:0;background:rgba(0,0,0,.6);display:none;align-items:center;justify-content:center;z-index:60;
  }
  .lockModal{
    width:min(92vw,420px);background:#0f172a;border:1px solid var(--stroke);border-radius:14px;padding:18px;box-shadow:var(--shadow);text-align:center
  }

  /* Table */
  table{width:100%;border-collapse:collapse}
  th,td{border:1px solid var(--stroke);padding:8px;font-size:14px}
  th{background:#0a1328;text-align:left}

  /* Mobile */
  @media (max-width:720px){
    .hero-grid{grid-template-columns:1fr}
    .top-left,.top-right{gap:6px}
  }
</style>
</head>
<body>

<!-- ===== Header (Deposit/Withdraw + User details) ===== -->
<header>
  <div class="nav">
    <div class="top-left">
      <div class="brand">WIN</div>
      <span id="topBalance" class="pill">₹0</span>
      <div class="userbar">
        <div class="kv">👤 <b id="uNameBar">Guest</b></div>
        <div class="kv">🆔 <b id="uIdBar">-</b></div>
      </div>
    </div>
    <div class="top-right">
      <button class="btn ghost" onclick="go('recharge')">Deposit</button>
      <button class="btn ghost" onclick="go('withdraw')">Withdraw</button>
      <button id="goHomeBtn" class="btn ghost" onclick="go('home')">Home</button>
      <button id="logoutBtn" class="btn ghost" onclick="logout()" style="display:none;">Logout</button>
    </div>
  </div>
</header>

<!-- ===== Login lock overlay ===== -->
<div class="lockOverlay" id="lock">
  <div class="lockModal">
    <h3>Login आवश्यक 🔐</h3>
    <p class="muted">जीतने/रियल वैल्यू फीचर्स इस्तेमाल करने से पहले कृपया Login/Register करें।</p>
    <div class="row" style="justify-content:center;margin-top:10px">
      <button class="btn" onclick="showLogin();closeLock()">Login</button>
      <button class="btn ghost" onclick="showRegister();closeLock()">Register</button>
    </div>
  </div>
</div>

<!-- ===== HOME (landing) ===== -->
<section id="home">
  <div class="hero">
    <div class="hero-grid">
      <div class="hero-card">
        <h1>Earn & Play — Mobile First 🎮</h1>
        <p class="muted">गेम्स खेलें, टास्क करें — रिवॉर्ड्स पाएँ। UPI QR से Deposit करें, Withdraw रिक्वेस्ट भेजें।</p>
        <div class="points">
          <span>📱 Mobile UI</span><span>💳 UPI Deposit</span><span>🛡️ Login Lock</span><span>⚡ Fast</span>
        </div>
        <div class="row" style="margin-top:14px">
          <button class="btn" onclick="showLogin()">Login</button>
          <button class="btn ghost" onclick="showRegister()">Register</button>
          <button class="btn ghost" onclick="go('games')">Browse Games</button>
        </div>
      </div>
      <div class="hero-img">
        <!-- 🔁 अपनी इमेज बदलें -->
        <img src="https://images.unsplash.com/photo-1542751371-adc38448a05e?q=80&w=1200&auto=format&fit=crop" alt="Games">
      </div>
    </div>
  </div>

  <div class="section">
    <h2>Top Games</h2>
    <div class="grid">
      <div class="card">
        <div class="thumb"><img src="https://images.unsplash.com/photo-1520975730396-1f569974198d?q=80&w=1000&auto=format&fit=crop" alt=""></div>
        <div class="body"><h3>Color Pick</h3><div class="muted">Timer + Result Number</div><span class="badge">Demo</span></div>
        <div class="cta"><button class="btn" onclick="openGame('game-color')">Play</button></div>
      </div>
      <div class="card">
        <div class="thumb"><img src="https://images.unsplash.com/photo-1511512578047-dfb367046420?q=80&w=1000&auto=format&fit=crop" alt=""></div>
        <div class="body"><h3>Spin & Win</h3><div class="muted">Cost ₹1 • Random</div><span class="badge">Demo</span></div>
        <div class="cta"><button class="btn" onclick="openGame('game-spin')">Play</button></div>
      </div>
      <div class="card">
        <div class="thumb"><img src="https://images.unsplash.com/photo-1509228468518-180dd4864904?q=80&w=1000&auto=format&fit=crop" alt=""></div>
        <div class="body"><h3>Quick Quiz</h3><div class="muted">3 Qs • Win ₹10</div><span class="badge">Demo</span></div>
        <div class="cta"><button class="btn" onclick="openGame('game-quiz')">Play</button></div>
      </div>
      <div class="card">
        <div class="thumb"><img src="https://images.unsplash.com/photo-1511512578047-dfb367046420?q=80&w=1000&auto=format&fit=crop" alt=""></div>
        <div class="body"><h3>Tap to Earn</h3><div class="muted">15 taps = ₹1</div><span class="badge">Demo</span></div>
        <div class="cta"><button class="btn" onclick="openGame('game-tap')">Play</button></div>
      </div>

      <!-- Extra demos -->
      <div class="card">
        <div class="thumb"><img src="https://images.unsplash.com/photo-1600962815717-d49b6db8ff5d?q=80&w=1000&auto=format&fit=crop" alt=""></div>
        <div class="body"><h3>Number Guess</h3><div class="muted">0–9 में अनुमान</div><span class="badge">Demo</span></div>
        <div class="cta"><button class="btn" onclick="openGame('game-num')">Play</button></div>
      </div>
      <div class="card">
        <div class="thumb"><img src="https://images.unsplash.com/photo-1518779578993-ec3579fee39f?q=80&w=1000&auto=format&fit=crop" alt=""></div>
        <div class="body"><h3>Memory Flip</h3><div class="muted">शॉर्ट टर्म मेमोरी</div><span class="badge">Demo</span></div>
        <div class="cta"><button class="btn" onclick="openGame('game-mem')">Play</button></div>
      </div>
    </div>
  </div>
</section>

<!-- ===== AUTH + APP ===== -->
<div class="wrap">

  <!-- Login -->
  <div class="container" id="loginForm">
    <h2>लॉगिन</h2>
    <input id="loginUser" placeholder="यूज़रनेम">
    <input id="loginPass" type="password" placeholder="पासवर्ड">
    <button class="btn" onclick="login()">Login</button>
    <p class="muted">खाता नहीं है? <a class="btn ghost" style="display:inline-block;padding:6px 10px" onclick="showRegister()">Register</a></p>
  </div>

  <!-- Register -->
  <div class="container" id="registerForm">
    <h2>रजिस्टर</h2>
    <input id="regUser" placeholder="यूज़रनेम">
    <input id="regPass" type="password" placeholder="पासवर्ड">
    <button class="btn" onclick="register()">Register</button>
    <p class="muted">पहले से खाता है? <a class="btn ghost" style="display:inline-block;padding:6px 10px" onclick="showLogin()">Login</a></p>
  </div>

  <!-- Dashboard -->
  <div class="container" id="dashboard">
    <h2>स्वागत है, <span id="userName"></span> 🎉</h2>
    <div class="stat">
      <div class="box">बैलेंस<br><b>₹<span id="balance">0</span></b></div>
      <div class="box">रेफ़रल बोनस<br><b>₹<span id="refBonus">0</span></b></div>
      <div class="box">गेम्स खेले<br><b><span id="gamesPlayed">0</span></b></div>
    </div>
    <div class="row">
      <button class="btn ghost" onclick="go('games')">🎮 Games</button>
      <button class="btn ghost" onclick="go('recharge')">💰 Deposit</button>
      <button class="btn ghost" onclick="go('withdraw')">🏧 Withdraw</button>
      <button class="btn ghost" onclick="go('history')">📜 History</button>
      <button class="btn ghost" onclick="go('admin')">🛠️ Admin</button>
    </div>
    <div class="container" style="margin-top:12px">
      <div class="muted">आपका रेफ़रल लिंक</div>
      <div id="refLink" style="word-break:break-all"></div>
      <small class="muted">लिंक शेयर करें, हर जॉइन पर बोनस।</small>
    </div>
  </div>

  <!-- Games hub (same cards list, just inside app) -->
  <div class="section" id="games" style="padding:0">
    <h2>🎮 Games</h2>
    <div class="grid">
      <div class="card"><div class="thumb"><img src="https://images.unsplash.com/photo-1520975730396-1f569974198d?q=80&w=1000&auto=format&fit=crop"></div><div class="body"><h3>Color Pick</h3><div class="muted">Timer + Number</div></div><div class="cta"><button class="btn" onclick="openGame('game-color')">Play</button></div></div>
      <div class="card"><div class="thumb"><img src="https://images.unsplash.com/photo-1511512578047-dfb367046420?q=80&w=1000&auto=format&fit=crop"></div><div class="body"><h3>Spin & Win</h3><div class="muted">Cost ₹1</div></div><div class="cta"><button class="btn" onclick="openGame('game-spin')">Play</button></div></div>
      <div class="card"><div class="thumb"><img src="https://images.unsplash.com/photo-1509228468518-180dd4864904?q=80&w=1000&auto=format&fit=crop"></div><div class="body"><h3>Quick Quiz</h3><div class="muted">3 Qs • ₹10</div></div><div class="cta"><button class="btn" onclick="openGame('game-quiz')">Play</button></div></div>
      <div class="card"><div class="thumb"><img src="https://images.unsplash.com/photo-1511512578047-dfb367046420?q=80&w=1000&auto=format&fit=crop"></div><div class="body"><h3>Tap to Earn</h3><div class="muted">15 taps = ₹1</div></div><div class="cta"><button class="btn" onclick="openGame('game-tap')">Play</button></div></div>
      <div class="card"><div class="thumb"><img src="https://images.unsplash.com/photo-1600962815717-d49b6db8ff5d?q=80&w=1000&auto=format&fit=crop"></div><div class="body"><h3>Number Guess</h3><div class="muted">0–9</div></div><div class="cta"><button class="btn" onclick="openGame('game-num')">Play</button></div></div>
      <div class="card"><div class="thumb"><img src="https://images.unsplash.com/photo-1518779578993-ec3579fee39f?q=80&w=1000&auto=format&fit=crop"></div><div class="body"><h3>Memory Flip</h3><div class="muted">Demo</div></div><div class="cta"><button class="btn" onclick="openGame('game-mem')">Play</button></div></div>
    </div>
    <div style="margin-top:14px"><button class="btn ghost" onclick="go('dashboard')">⬅️ Dashboard</button></div>
  </div>

  <!-- GAME: Color Pick (with timer + round + result number) -->
  <div class="container" id="game-color">
    <div class="row">
      <span class="roundpill">Round: <b id="cpRound">1</b></span>
      <span class="roundpill">⏳ Time: <b class="timer" id="cpTime">10</b>s</span>
      <span class="roundpill">Result #: <b id="cpNum">-</b></span>
    </div>
    <h2>🎨 Color Pick</h2>
    <div class="muted">रंग चुनें (Red/Green/Blue). टाइम खत्म होने पर रिज़ल्ट घोषित होगा। सही रंग पर Win, वरना Lose.</div>
    <div class="row" style="margin-top:8px">
      <button class="btn" onclick="cpChoose('red')">Red (Bet ₹2)</button>
      <button class="btn" onclick="cpChoose('green')">Green (Bet ₹2)</button>
      <button class="btn" onclick="cpChoose('blue')">Blue (Bet ₹2)</button>
      <button class="btn ghost" onclick="cpReset(true)">↻ Reset</button>
    </div>
    <div class="resultbox">
      <div id="cpStatus" class="muted">रंग चुनें और टाइमर का इंतज़ार करें…</div>
      <div id="colorResult" class="muted"></div>
    </div>
    <button class="btn ghost" onclick="go('games')">⬅️ Games</button>
  </div>

  <!-- Spin -->
  <div class="container" id="game-spin">
    <h2>🎡 Spin & Win</h2>
    <div class="needle"></div>
    <div class="wheel" id="wheel"></div>
    <div class="centerDot"></div>
    <button class="btn" onclick="spin()">Spin (Cost ₹1)</button>
    <p id="spinMsg" class="muted"></p>
    <button class="btn ghost" onclick="go('games')">⬅️ Games</button>
  </div>

  <!-- Quiz -->
  <div class="container" id="game-quiz">
    <h2>🧠 Quick Quiz</h2>
    <div id="qBox"></div>
    <p id="quizMsg" class="muted"></p>
    <button class="btn ghost" onclick="go('games')">⬅️ Games</button>
  </div>

  <!-- Tap -->
  <div class="container" id="game-tap">
    <h2>👆 Tap to Earn</h2>
    <p class="muted">10 सेकंड में जितना हो सके टैप करें।</p>
    <button id="tapBtn" onclick="tapOnce()" disabled>Start First</button>
    <p>टैप: <b><span id="tapCount">0</span></b> | समय: <b><span id="tapTime">10</span>s</b></p>
    <button class="btn" onclick="startTap()">Start</button>
    <p id="tapMsg" class="muted"></p>
    <button class="btn ghost" onclick="go('games')">⬅️ Games</button>
  </div>

  <!-- Extra demo placeholders -->
  <div class="container" id="game-num"><h2>🔢 Number Guess</h2><p class="muted">0–9 में अनुमान (डेमो, जल्द जोड़ेंगे)।</p><button class="btn ghost" onclick="go('games')">⬅️ Games</button></div>
  <div class="container" id="game-mem"><h2>🧠 Memory Flip</h2><p class="muted">डेमो प्लेसहोल्डर।</p><button class="btn ghost" onclick="go('games')">⬅️ Games</button></div>

  <!-- Recharge (QR + UPI) -->
  <div class="container" id="recharge">
    <h2>💰 Deposit (UPI)</h2>
    <p class="muted">UPI से पेमेंट करने के लिए QR स्कैन करें या नीचे “Pay via UPI App” दबाएँ।</p>
    <div style="text-align:center; margin:12px 0;">
      <!-- 🔁 आपका QR -->
      <img src="https://i.ibb.co/cc9btq3j/2222.jpg" alt="UPI QR" style="max-width:260px;border:1px solid var(--stroke);border-radius:12px;">
    </div>
    <a id="upiLink" href="#" class="btn" style="text-align:center">Pay via UPI App</a>
    <div class="container" style="margin-top:14px">
      <h3 style="margin:4px 0 8px;">भुगतान विवरण</h3>
      <p class="muted" style="margin-top:-6px;">पेमेंट के बाद UTR/Txn ID भरें। वेरिफ़ाई होने पर बैलेंस जोड़ा जाएगा।</p>
      <input id="rcName" placeholder="आपका नाम">
      <input id="rcAmount" type="number" placeholder="Amount (₹)" min="1">
      <input id="rcTxn" placeholder="UTR / Transaction ID">
      <button class="btn" onclick="saveRechargeRequest()">सबमिट करें</button>
      <p class="muted">सपोर्ट (WhatsApp): <a href="https://wa.me/8816058313" target="_blank">8816058313</a></p>
    </div>
    <button class="btn ghost" onclick="go('dashboard')">⬅️ Dashboard</button>
  </div>

  <!-- Withdraw -->
  <div class="container" id="withdraw">
    <h2>🏧 Withdraw</h2>
    <input id="wdAmount" type="number" placeholder="Amount (₹)">
    <input id="wdUpi" placeholder="UPI ID (उदा: name@upi)">
    <button class="btn" onclick="doWithdraw()">Request Withdraw</button>
    <p class="muted">डेमो में रिक्वेस्ट बनती है, बैलेंस से राशि घटती है और हिस्ट्री में दिखती है।</p>
    <button class="btn ghost" onclick="go('dashboard')">⬅️ Dashboard</button>
  </div>

  <!-- History -->
  <div class="container" id="history">
    <h2>📜 Transactions</h2>
    <div id="historyBox"></div>
    <button class="btn ghost" onclick="go('dashboard')">⬅️ Dashboard</button>
  </div>

  <!-- Admin -->
  <div class="container" id="admin">
    <h2>🛠️ Admin (Local Demo)</h2>
    <div class="stat">
      <div class="box">User<br><b id="admUser">-</b></div>
      <div class="box">Balance<br><b>₹<span id="admBal">0</span></b></div>
      <div class="box">Games<br><b><span id="admGames">0</span></b></div>
    </div>
    <button class="btn ghost" onclick="exportData()">Export JSON</button>
    <button class="btn ghost" onclick="clearAll()">Clear All (Logout)</button>
    <p class="muted">यह सिर्फ़ इस डिवाइस/ब्राउज़र का डेटा है। असली एडमिन के लिए सर्वर + DB चाहिए।</p>
    <button class="btn ghost" onclick="go('dashboard')">⬅️ Dashboard</button>
  </div>

</div>

<script>
  // ===== Storage helpers =====
  const INR=(n)=>Number(n||0).toFixed(0);
  const now=()=>new Date().toLocaleString();
  const get=(k,d=null)=>JSON.parse(localStorage.getItem(k)??JSON.stringify(d));
  const put=(k,v)=>localStorage.setItem(k,JSON.stringify(v));
  const setBal=(v)=>localStorage.setItem('balance',String(Number(v)));
  const getBal=()=>Number(localStorage.getItem('balance')||0);
  const pushTxn=(t)=>{const x=get('txns',[]);x.unshift(t);put('txns',x);renderHistory();};
  const incStat=(k)=>localStorage.setItem(k,String(1+Number(localStorage.getItem(k)||0)));
  const getU=()=>localStorage.getItem('user')||'';
  const isLogged=()=> !!localStorage.getItem('user');

  // ===== Section show/hide =====
  function show(id){
    for(const sec of ['home','loginForm','registerForm','dashboard','games','game-color','game-spin','game-quiz','game-tap','game-num','game-mem','recharge','withdraw','history','admin']){
      const el=document.getElementById(sec); if(el) el.style.display = (sec===id)?'block':'none';
    }
    document.getElementById('logoutBtn').style.display =
      ['dashboard','games','game-color','game-spin','game-quiz','game-tap','game-num','game-mem','recharge','withdraw','history','admin'].includes(id)
      ? 'inline-block':'none';
    syncTop();
  }
  const go=(id)=>{ show(id); if(id==='game-quiz')loadQuiz(); if(id==='history')renderHistory(); if(id==='admin')fillAdmin(); };

  // ===== Login lock overlay =====
  function openGame(id){
    if(!isLogged()){ openLock(); return; }
    go(id);
  }
  function openLock(){ document.getElementById('lock').style.display='flex'; }
  function closeLock(){ document.getElementById('lock').style.display='none'; }

  // ===== Auth (Auto-register on first login) =====
  function showRegister(){ show('registerForm'); }
  function showLogin(){ show('loginForm'); }

  function register(){
    const u=document.getElementById('regUser').value.trim();
    const p=document.getElementById('regPass').value.trim();
    if(!u||!p) return alert('कृपया सभी फील्ड भरें');
    const uid = 'U' + Math.floor(100000+Math.random()*899999);
    localStorage.setItem('user',u); localStorage.setItem('userId',uid); localStorage.setItem('pass',p);
    setBal(50); localStorage.setItem('gamesPlayed','0'); localStorage.setItem('refBonus','0'); put('txns',[]);
    pushTxn({type:'signup_bonus',amount:50,ts:now(),status:'success',note:'Signup bonus'});
    alert('रजिस्ट्रेशन सफल! ₹50 बोनस मिला'); openDashboard(u);
  }
  function login(){
    const u=document.getElementById('loginUser').value.trim();
    const p=document.getElementById('loginPass').value.trim();
    const su=localStorage.getItem('user'), sp=localStorage.getItem('pass');
    if(su&&sp){
      if(u===su&&p===sp) openDashboard(u); else alert('गलत यूज़रनेम या पासवर्ड');
    }else{
      if(!u||!p) return alert('पहली बार के लिए यूज़रनेम/पासवर्ड भरें');
      const uid='U'+Math.floor(100000+Math.random()*899999);
      localStorage.setItem('user',u); localStorage.setItem('userId',uid); localStorage.setItem('pass',p);
      setBal(50); localStorage.setItem('gamesPlayed','0'); localStorage.setItem('refBonus','0'); put('txns',[]);
      pushTxn({type:'signup_bonus',amount:50,ts:now(),status:'success',note:'Auto signup bonus'});
      alert(`नया अकाउंट बन गया! स्वागत है, ${u} — ₹50 बोनस मिला`); openDashboard(u);
    }
  }
  function openDashboard(u){
    document.getElementById('userName').innerText=u;
    document.getElementById('refLink').innerText = location.origin + location.pathname + '?ref=' + encodeURIComponent(u);
    const uid = localStorage.getItem('userId')||'-';
    document.getElementById('uNameBar').innerText = u||'Guest';
    document.getElementById('uIdBar').innerText = uid;
    if(new URLSearchParams(location.search).get('ref') && !localStorage.getItem('refCredited')){
      localStorage.setItem('refCredited','1'); const bonus=10; setBal(getBal()+bonus);
      localStorage.setItem('refBonus',String(Number(localStorage.getItem('refBonus')||0)+bonus));
      pushTxn({type:'referral_bonus',amount:bonus,ts:now(),status:'success',note:'Ref link login'});
    }
    show('dashboard');
  }
  function logout(){ localStorage.removeItem('user'); localStorage.removeItem('userId'); show('home'); syncTop(); }

  // ===== Top sync =====
  function syncTop(){
    document.getElementById('balance').innerText = INR(getBal());
    document.getElementById('topBalance').innerText = '₹'+INR(getBal());
    document.getElementById('gamesPlayed').innerText = localStorage.getItem('gamesPlayed')||0;
    document.getElementById('refBonus').innerText = INR(localStorage.getItem('refBonus')||0);
    document.getElementById('uNameBar').innerText = getU() || 'Guest';
    document.getElementById('uIdBar').innerText = localStorage.getItem('userId') || '-';
  }

  // ===== Recharge (UPI deep link) =====
  (function setupUpiLink(){
    const upiId='1848ashish@fam';
    const payeeName=encodeURIComponent('Ashish Rajput'); // 🔁 बदलें
    const amtInput=document.getElementById('rcAmount');
    function buildLink(){ const am=Number(amtInput?.value||0); const base=`upi://pay?pa=${upiId}&pn=${payeeName}&cu=INR`; return am>0? `${base}&am=${am}`: base; }
    const a=document.getElementById('upiLink'); if(a){ a.href=buildLink(); amtInput?.addEventListener('input',()=>{ a.href=buildLink(); }); }
  })();
  function saveRechargeRequest(){
    if(!isLogged()) return openLock();
    const name=(document.getElementById('rcName')?.value||'').trim();
    const amt=Number(document.getElementById('rcAmount')?.value||0);
    const txn=(document.getElementById('rcTxn')?.value||'').trim();
    if(!name) return alert('कृपया नाम भरें');
    if(!(amt>0)) return alert('कृपया सही Amount भरें');
    if(txn.length<6) return alert('सही UTR/Txn ID भरें');
    pushTxn({type:'recharge_request',amount:amt,ts:now(),status:'pending',note:`Name:${name} | UTR:${txn}`});
    alert('रिक्वेस्ट सबमिट हो गई। वेरिफ़ाई होने पर बैलेंस जोड़ा जाएगा।');
  }

  // ===== Withdraw =====
  function doWithdraw(){
    if(!isLogged()) return openLock();
    const a=Number(document.getElementById('wdAmount').value||0);
    const upi=(document.getElementById('wdUpi').value||'').trim();
    if(a<=0) return alert('सही राशि डालें');
    if(a>getBal()) return alert('पर्याप्त बैलेंस नहीं');
    if(!/^[\w.\-]+@\w+$/.test(upi)) return alert('सही UPI ID डालें');
    setBal(getBal()-a);
    pushTxn({type:'withdraw',amount:a,ts:now(),status:'pending',upi,note:'Demo withdraw'});
    alert(`Withdraw Request बनी: ₹${a}`);
    syncTop();
  }

  // ===== History / Admin =====
  function renderHistory(){
    const box=document.getElementById('historyBox');
    const rows=get('txns',[]);
    if(!rows.length){ box.innerHTML='<p class="muted">कोई ट्रांजैक्शन नहीं</p>'; return; }
    let html='<table><thead><tr><th>समय</th><th>टाइप</th><th>राशि</th><th>स्टेटस</th><th>नोट</th></tr></thead><tbody>';
    rows.forEach(r=>{ html+=`<tr><td>${r.ts||''}</td><td>${r.type}</td><td>₹${INR(r.amount||0)}</td><td>${r.status||'-'}</td><td>${r.note||''}</td></tr>`; });
    html+='</tbody></table>'; box.innerHTML=html;
  }
  function fillAdmin(){
    document.getElementById('admUser').innerText=getU()||'-';
    document.getElementById('admBal').innerText=INR(getBal());
    document.getElementById('admGames').innerText=localStorage.getItem('gamesPlayed')||0;
  }
  function exportData(){
    const data={user:getU(),userId:localStorage.getItem('userId')||'-',balance:getBal(),gamesPlayed:localStorage.getItem('gamesPlayed')||0,refBonus:localStorage.getItem('refBonus')||0,txns:get('txns',[])};
    const blob=new Blob([JSON.stringify(data,null,2)],{type:'application/json'});
    const url=URL.createObjectURL(blob); const a=document.createElement('a'); a.href=url; a.download='export.json'; a.click(); URL.revokeObjectURL(url);
  }
  function clearAll(){ if(!confirm('सारा लोकल डेटा क्लियर कर दें?')) return; localStorage.clear(); location.reload(); }

  // ===== Games =====
  // Color Pick — round timer + result number + win/lose both
  let cpRound=1, cpTime=10, cpTimer=null, cpChoice=null;
  function cpTick(){
    cpTime--; document.getElementById('cpTime').innerText=cpTime;
    if(cpTime<=0){ clearInterval(cpTimer); cpResolve(); }
  }
  function cpStart(){
    cpTime=10; cpChoice=null; document.getElementById('cpTime').innerText=cpTime;
    document.getElementById('cpNum').innerText='-';
    document.getElementById('cpStatus').innerText='रंग चुनें और टाइमर का इंतज़ार करें…';
    document.getElementById('colorResult').innerText='';
    clearInterval(cpTimer); cpTimer=setInterval(cpTick,1000);
  }
  function cpChoose(c){
    if(!isLogged()) return openLock();
    const cost=2; if(getBal()<cost) return alert('बैलेंस कम है');
    // एक ही राउंड में एक बार चुनने दें
    if(cpChoice){ alert('आपने इस राउंड में रंग चुन लिया है।'); return; }
    setBal(getBal()-cost); cpChoice=c; document.getElementById('cpStatus').innerText='चयन दर्ज: '+c.toUpperCase()+'. परिणाम की प्रतीक्षा…'; syncTop();
  }
  function cpResolve(){
    const colors=['red','green','blue'];
    const resultColor=colors[Math.floor(Math.random()*colors.length)];
    const resultNum=Math.floor(Math.random()*10); // 0–9
    document.getElementById('cpNum').innerText=String(resultNum);
    let msg=`Result: ${resultColor.toUpperCase()} • Num ${resultNum} — `;
    if(cpChoice && resultColor===cpChoice){
      setBal(getBal()+5);
      msg += 'जीत! +₹5';
      pushTxn({type:'game_color',amount:+3,ts:now(),status:'success',note:`Win (${cpChoice}) #${resultNum}`});
    }else if(cpChoice){
      msg += 'हार! -₹2';
      pushTxn({type:'game_color',amount:-2,ts:now(),status:'success',note:`Lose (${cpChoice}) #${resultNum}`});
    }else{
      msg += 'No bet';
    }
    document.getElementById('colorResult').innerText=msg;
    incStat('gamesPlayed'); syncTop();
    // अगला राउंड ऑटो
    cpRound++; document.getElementById('cpRound').innerText=cpRound;
    setTimeout(()=>cpStart(),1200);
  }
  function cpReset(hard=false){ if(hard){ cpRound=1; document.getElementById('cpRound').innerText=cpRound; } cpStart(); }
  
  // Spin
  const prizes=[0,2,5,1,10,3,0,7];
  (function buildWheel(){
    const w=document.getElementById('wheel'); if(!w) return; const n=prizes.length;
    for(let i=0;i<n;i++){ const s=document.createElement('div'); s.className='slice'; s.style.transform=`rotate(${(360/n)*i}deg)`; s.style.background=i%2?'#0b2440':'#0f2e54'; w.appendChild(s); }
  })();
  let spinning=false;
  function spin(){
    if(!isLogged()) return openLock();
    const cost=1; if(spinning) return; if(getBal()<cost) return alert('बैलेंस कम है'); setBal(getBal()-cost); spinning=true;
    const w=document.getElementById('wheel'); const n=prizes.length;
    const idx=Math.floor(Math.random()*n); const deg=360/n; const target=360*(5+Math.random()*3)+idx*deg+deg/2;
    w.style.transition='transform 2.5s ease-out'; w.style.transform=`rotate(${target}deg)`;
    setTimeout(()=>{ const win=prizes[idx]; if(win>0){ setBal(getBal()+win); document.getElementById('spinMsg').innerText=`जीता: ₹${win}`; } else { document.getElementById('spinMsg').innerText='कोई इनाम नहीं 😅'; }
      pushTxn({type:'game_spin',amount:win-cost,ts:now(),status:'success',note:`Spin result ₹${win}`}); incStat('gamesPlayed'); syncTop(); spinning=false; },2600);
  }

  // Quiz
  const QUIZ=[{q:'भारत की राजधानी?',opts:['मुंबई','दिल्ली','जयपुर','कोलकाता'],a:1},{q:'HTML का फुल फॉर्म?',opts:['Hyperlinks and Text Markup','Hyper Text Markup Language','Home Tool Markup','High Text Machine Language'],a:1},{q:'2 + 2 = ?',opts:['3','4','5','22'],a:1},];
  let qi=0,quizDone=false;
  function loadQuiz(){
    if(!isLogged()) return openLock();
    const box=document.getElementById('qBox'); box.innerHTML='';
    if(qi>=QUIZ.length){ if(!quizDone){ setBal(getBal()+10); pushTxn({type:'game_quiz',amount:+10,ts:now(),status:'success',note:'Quiz reward'}); quizDone=true; }
      document.getElementById('quizMsg').innerText='क्विज़ पूरा! +₹10'; syncTop(); return; }
    const {q,opts,a}=QUIZ[qi]; const h=document.createElement('div'); const title=document.createElement('h3'); title.textContent=(qi+1)+'. '+q; h.appendChild(title);
    opts.forEach((t,i)=>{ const b=document.createElement('button'); b.className='btn ghost'; b.style.margin='6px 0'; b.textContent=t;
      b.onclick=()=>{ if(b.classList.contains('done')) return; if(i===a){ b.style.borderColor='#22c55e'; qi++; setTimeout(loadQuiz,400); } else { b.style.borderColor='#ef4444'; } b.classList.add('done'); };
      h.appendChild(b);
    }); box.appendChild(h); document.getElementById('quizMsg').innerText='';
  }

  // Tap
  let tap=0,left=10,timer=null,started=false;
  function startTap(){
    if(!isLogged()) return openLock();
    tap=0; left=10; started=true;
    document.getElementById('tapCount').innerText=tap; document.getElementById('tapTime').innerText=left;
    document.getElementById('tapMsg').innerText=''; document.getElementById('tapBtn').disabled=false; clearInterval(timer);
    timer=setInterval(()=>{ left--; document.getElementById('tapTime').innerText=left;
      if(left<=0){ clearInterval(timer); document.getElementById('tapBtn').disabled=true; started=false;
        const earn=Math.floor(tap/15); setBal(getBal()+earn); pushTxn({type:'game_tap',amount:+earn,ts:now(),status:'success',note:`Taps: ${tap}`});
        document.getElementById('tapMsg').innerText=`टैप: ${tap} → कमाई: ₹${earn}`; incStat('gamesPlayed'); syncTop();
      }
    },1000);
  }
  function tapOnce(){ if(!started) return; tap++; document.getElementById('tapCount').innerText=tap; }

  // ===== Init =====
  (function init(){
    show('home');
    const u=localStorage.getItem('user'); if(u){ document.getElementById('loginUser').value=u; }
    renderHistory();
    // Color game initial start (view पर शुरू होगा)
    const onShowColor=()=>{ if(document.getElementById('game-color').style.display==='block'){ cpStart(); } };
    // View change observer (simple)
    const origShow=show; window.show=(id)=>{ origShow(id); if(id==='game-color') cpStart(); };
  })();
</script>

</body>
</html>
