<!doctype html>
<html lang="hi">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>WIN — Gaming Portal (Demo) — Games Integrated</title>
<style>
  :root{--bg1:#040714;--bg2:#071233;--card:#071229;--accent:#ff6b00;--accent2:#7c3aed;--muted:#98a8bf;--white:#eef7ff}
  *{box-sizing:border-box}
  body{margin:0;font-family:Inter,system-ui,Arial;background:linear-gradient(180deg,var(--bg1),var(--bg2));color:var(--muted);-webkit-font-smoothing:antialiased}
  a{color:inherit}
  .container{max-width:1200px;margin:0 auto;padding:20px}
  header{display:flex;align-items:center;justify-content:space-between;padding:14px 0}
  .brand{display:flex;align-items:center;gap:12px}
  .logo{width:48px;height:48px;border-radius:10px;background:linear-gradient(135deg,var(--accent),var(--accent2));display:flex;align-items:center;justify-content:center;font-weight:800;color:#041026}
  nav{display:flex;gap:10px;align-items:center}
  .nav-btn{background:transparent;border:1px solid rgba(255,255,255,0.04);padding:8px 12px;border-radius:8px;color:var(--muted);cursor:pointer}
  .primary{background:linear-gradient(90deg,var(--accent),var(--accent2));color:#041026;border:0;padding:8px 12px;border-radius:8px;cursor:pointer}

  .hero{display:grid;grid-template-columns:1fr 420px;gap:24px;align-items:center;margin-top:18px}
  .hero-card{background:linear-gradient(180deg,rgba(255,255,255,0.02),transparent);padding:24px;border-radius:14px}
  h1{color:var(--white);margin:0 0 8px}
  p.lead{color:var(--muted);margin:0 0 16px}

  .stats{display:flex;gap:12px;margin-top:12px}
  .stat{background:rgba(255,255,255,0.02);padding:12px;border-radius:10px;flex:1;text-align:center}
  .stat .num{color:var(--white);font-weight:800;font-size:18px}

  .games{display:grid;grid-template-columns:repeat(auto-fit,minmax(180px,1fr));gap:12px;margin-top:18px}
  .game{background:linear-gradient(180deg,rgba(255,255,255,0.01),transparent);padding:12px;border-radius:12px;display:flex;flex-direction:column;gap:8px}
  .game .thumb{height:100px;border-radius:8px;background:linear-gradient(135deg,#0b1228,#071233);display:flex;align-items:center;justify-content:center;color:var(--muted);font-weight:700}
  .game button{margin-top:auto;padding:8px;border-radius:8px;border:0;cursor:pointer}
  .play{background:linear-gradient(90deg,var(--accent),var(--accent2));color:#041026}

  .card{background:var(--card);padding:12px;border-radius:12px}
  footer{margin-top:24px;padding:18px 0;color:var(--muted);font-size:13px;text-align:center}

  /* game modal */
  .modal{position:fixed;left:0;top:0;right:0;bottom:0;display:flex;align-items:center;justify-content:center;background:rgba(1,2,6,0.6);z-index:999}
  .modal .box{width:100%;max-width:920px;background:linear-gradient(180deg,#07122b,#041124);border-radius:12px;padding:18px;color:var(--muted)}

  /* responsive */
  @media(max-width:960px){.hero{grid-template-columns:1fr} .logo{width:42px;height:42px}}
</style>
</head>
<body>
  <div class="container">
    <header>
      <div class="brand">
        <div class="logo">W</div>
        <div>
          <div style="font-weight:800;color:var(--white)">WIN</div>
          <div style="font-size:12px;color:var(--muted)">Real-like Demo • No real money</div>
        </div>
      </div>

      <nav>
        <button class="nav-btn" onclick="navigate('home')">Home</button>
        <button class="nav-btn" onclick="navigate('games')">Games</button>
        <button class="nav-btn" onclick="navigate('wallet')">Wallet</button>
        <button class="nav-btn" onclick="navigate('about')">About</button>
        <button class="primary" id="topLogin" onclick="openAuth()">Login / Register</button>
      </nav>
    </header>

    <main id="page">
      <!-- Home -->
      <section id="home">
        <div class="hero">
          <div class="hero-card">
            <h1>खेलो, जीतों और प्रैक्टिस करो — डेमो पोर्टल</h1>
            <p class="lead">यह एक realistic-looking demo है। असली पैसे की लेन-देन यहाँ नहीं होती। रजिस्टर करो, वॉलेट में पैसों को simulate करो और गेम खेलकर परीक्षण करो।</p>

            <div class="stats">
              <div class="stat"><div class="num">12,345</div><div class="small">Players</div></div>
              <div class="stat"><div class="num">₹1,23,456</div><div class="small">Daily volume (sim)</div></div>
              <div class="stat"><div class="num">98%</div><div class="small">Uptime</div></div>
            </div>

            <div style="margin-top:14px;display:flex;gap:10px;align-items:center">
              <button class="primary" onclick="navigate('games')">Play Now</button>
              <button class="nav-btn" onclick="openAuth()">Sign In</button>
            </div>

            <div style="margin-top:18px">
              <h3 style="color:var(--white);margin:0 0 8px">Featured Games</h3>
              <div class="games" id="featured"></div>
            </div>
          </div>

          <div class="card">
            <div style="display:flex;flex-direction:column;gap:8px">
              <div style="display:flex;justify-content:space-between;align-items:center">
                <div>
                  <div class="small">Your balance</div>
                  <div style="font-weight:800;color:var(--white);font-size:20px" id="bal">₹0</div>
                </div>
                <div>
                  <button class="nav-btn" onclick="addQuick(100)">+₹100</button>
                </div>
              </div>

              <div style="margin-top:12px">
                <button class="primary" onclick="navigate('wallet')">Wallet</button>
                <button class="nav-btn" onclick="navigate('games')" style="margin-left:8px">My Games</button>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Games page -->
      <section id="games" style="display:none;margin-top:18px">
        <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:12px">
          <h2 style="margin:0;color:var(--white)">Games</h2>
          <div class="small">Play simulated demo games</div>
        </div>

        <div class="games" id="gamesGrid"></div>
      </section>

      <!-- Wallet -->
      <section id="wallet" style="display:none;margin-top:18px">
        <div style="display:grid;grid-template-columns:1fr 360px;gap:12px">
          <div class="card">
            <h3 style="color:var(--white)">Wallet</h3>
            <div class="small">Add money (simulation), request withdraw (demo)</div>
            <div style="margin-top:12px">
              <label class="small">Quick add</label>
              <select id="quickAddMain" style="margin-top:8px;padding:8px;border-radius:8px;background:transparent;color:var(--white);border:1px solid rgba(255,255,255,0.03)">
                <option value="50">₹50</option>
                <option value="100">₹100</option>
                <option value="500">₹500</option>
                <option value="1000">₹1000</option>
              </select>
              to add <input type="add to app in app 
              " name="" id="">
              <div style="display:flex;gap:8px;margin-top:8px"><button class="primary" onclick="addQuickFromWallet()">Add</button><button class="nav-btn" onclick="openWithdrawBox()">Withdraw</button></div>

              <div id="withdrawPanel" style="display:none;margin-top:10px">
                <label class="small">Amount</label>
                <input id="withdrawAmtMain" type="number" placeholder="₹100" style="width:100%;padding:8px;border-radius:8px;background:transparent;color:var(--white);border:1px solid rgba(255,255,255,0.03);margin-top:6px" />
                <label class="small" style="margin-top:8px">UPI / Wallet (demo)</label>
                <input id="withdrawToMain" placeholder="example@upi" style="width:100%;padding:8px;border-radius:8px;background:transparent;color:var(--white);border:1px solid rgba(255,255,255,0.03);margin-top:6px" />
                <div style="margin-top:8px;display:flex;gap:8px"><button class="primary" onclick="requestWithdrawMain()">Request withdraw</button><button class="nav-btn" onclick="closeWithdrawBox()">Cancel</button></div>
              </div>

              <div style="margin-top:12px">
                <div class="small">Transaction history</div>
                <div id="txMain" class="log" style="margin-top:8px"></div>
              </div>
            </div>
          </div>

          <div class="card">
            <h3 style="color:var(--white)">My account</h3>
            <div class="small">Register / login to save session (localStorage)</div>
            <div style="margin-top:10px" id="authSmall"></div>
          </div>
        </div>
      </section>

      <!-- About -->
      <section id="about" style="display:none;margin-top:18px">
        <div class="card">
          <h2 style="margin:0;color:var(--white)">About This Demo</h2>
          <p class="small">यह एक demo प्रोजेक्ट है जिसे तुम customize कर सकते हो — रंग, लोगो, गेम्स, और backend integration जोड़कर इसे production-ready बना सकते हो।</p>
        </div>
      </section>

    </main>

    
    <footer>© WIN Demo — For testing only. Replace branding and integrate payment gateway for production.</footer>
  </div>

  <!-- GAME MODAL: Coin Flip & Color Prediction integrated -->
  <div id="gameModal" class="modal" style="display:none">
    <div class="box">
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:8px">
        <div id="gameTitle" style="font-weight:800;color:var(--white)"></div>
        <div><button class="nav-btn" onclick="closeGame()">Close</button></div>
      </div>

      <div id="gameArea" style="display:grid;grid-template-columns:1fr 320px;gap:12px">
        <div class="card" id="gameMain"></div>
        <div class="card" id="gameSide"></div>
      </div>
    </div>
  </div>

<script>
// Client-side demo with 2 playable games: Coin Flip and Color Prediction
const LS='win_demo_users_v2';
let users = JSON.parse(localStorage.getItem(LS) || '{}');
let current = localStorage.getItem('win_demo_current') || null;

const featured = [
  {id:'coinflip',name:'Coin Flip',desc:'Heads or tails — 2x payout (1% fee)'},
  {id:'colorpred',name:'Color Prediction',desc:'Pick a color — 2.8x payout (demo)'}
];

function init(){
  renderFeatured(); renderGames(); renderTop(); renderBal(); renderAuthSmall(); renderTxMain();
}

function navigate(page){ document.querySelectorAll('main section').forEach(s=>s.style.display='none'); document.getElementById(page).style.display = 'block'; window.scrollTo({top:0,behavior:'smooth'}); }

function openAuth(){ const email = prompt('Enter email for register/login (demo)'); if(!email) return; const e = email.trim().toLowerCase(); if(!users[e]){ const p = prompt('Set a password (min 6)'); if(!p || p.length<6){ alert('Password too short'); return; } users[e] = {password:p,balance:0,tx:[],withdraws:[]}; localStorage.setItem(LS,JSON.stringify(users)); current = e; localStorage.setItem('win_demo_current',current); alert('Registered and logged in (demo)'); init(); } else { const p = prompt('Enter password to login'); if(p !== users[e].password){ alert('Invalid'); return; } current = e; localStorage.setItem('win_demo_current',current); alert('Logged in'); init(); } }

function renderTop(){ document.getElementById('topLogin').innerText = current ? 'Account' : 'Login / Register'; }
function renderFeatured(){ const el = document.getElementById('featured'); el.innerHTML = featured.map(g=>`<div class="game"><div style="font-weight:700;color:var(--white)">${g.name}</div><div class="small">${g.desc}</div><div style="margin-top:auto"><button class="play" onclick="openGame('${g.id}')">Play</button></div></div>`).join(''); }
function renderGames(){ const el = document.getElementById('gamesGrid'); el.innerHTML = featured.map(g=>`<div class="game"><div class="thumb">${g.name}</div><div style="font-weight:700;color:var(--white)">${g.name}</div><div class="small">${g.desc}</div><div style="margin-top:auto"><button class="play" onclick="openGame('${g.id}')">Play</button></div></div>`).join(''); }

function renderBal(){ document.getElementById('bal').innerText = '₹' + ((current && users[current]) ? users[current].balance : 0); }
function addQuick(a){ if(!current){ alert('Login first'); return; } users[current].balance = (users[current].balance||0) + a; users[current].tx.unshift({type:'add',amount:a,ts:Date.now(),note:'quick add'}); localStorage.setItem(LS,JSON.stringify(users)); renderBal(); renderTxMain(); }

function openGame(id){ // build game UI inside modal
  document.getElementById('gameModal').style.display='flex';
  document.getElementById('gameTitle').innerText = featured.find(f=>f.id===id).name;
  const main = document.getElementById('gameMain');
  const side = document.getElementById('gameSide');
  main.innerHTML = '';
  side.innerHTML = '';

  if(id==='coinflip'){
    main.innerHTML = `
      <h3 style="color:var(--white)">Coin Flip</h3>
      <div class="small">Choose Heads or Tails. Win returns ~2x (1% fee on profit).</div>
      <div style="margin-top:12px">
        <label class="small">Bet amount (₹)</label>
        <input id="cfBet" type="number" value="50" min="1" style="width:140px;padding:8px;border-radius:8px;background:transparent;color:var(--white);border:1px solid rgba(255,255,255,0.03)" />
        <label class="small" style="margin-top:8px">Choose</label>
        <select id="cfChoose" style="width:160px;padding:8px;border-radius:8px;background:transparent;color:var(--white);border:1px solid rgba(255,255,255,0.03)">
          <option value="heads">Heads</option>
          <option value="tails">Tails</option>
        </select>
        <div style="margin-top:10px"><button class="primary" onclick="playCoin()">Place Bet</button></div>
      </div>
    `;
    side.innerHTML = `<div class="small">Last outcomes</div><div id="cfRecent" class="log" style="margin-top:8px"></div>`;
    renderCFRecent();
  }

  if(id==='colorpred'){
    main.innerHTML = `
      <h3 style="color:var(--white)">Color Prediction</h3>
      <div class="small">Pick a color (Red/Green/Blue). If correct you win 2.8x (demo odds)</div>
      <div style="margin-top:12px">
        <label class="small">Bet amount (₹)</label>
        <input id="cpBet" type="number" value="50" min="1" style="width:140px;padding:8px;border-radius:8px;background:transparent;color:var(--white);border:1px solid rgba(255,255,255,0.03)" />
        <label class="small" style="margin-top:8px">Choose color</label>
        <select id="cpChoose" style="width:160px;padding:8px;border-radius:8px;background:transparent;color:var(--white);border:1px solid rgba(255,255,255,0.03)">
          <option value="red">Red</option>
          <option value="green">Green</option>
          <option value="blue">Blue</option>
        </select>
        <div style="margin-top:10px"><button class="primary" onclick="playColor()">Place Bet</button></div>
      </div>
    `;
    side.innerHTML = `<div class="small">Last outcomes</div><div id="cpRecent" class="log" style="margin-top:8px"></div>`;
    renderCPRecent();
  }
}

function closeGame(){ document.getElementById('gameModal').style.display='none'; }

// Coin Flip logic
function playCoin(){ if(!current){ alert('Login first'); return; } const bet = Number(document.getElementById('cfBet').value||0); const choose = document.getElementById('cfChoose').value; if(bet<=0){ alert('Enter bet'); return; } if(bet>users[current].balance){ alert('Insufficient'); return; } users[current].balance -= bet; const outcome = Math.random()<0.5 ? 'heads' : 'tails'; const win = outcome===choose; let payout = 0; if(win){ payout = bet*2; const fee = Math.round((payout-bet)*0.01*100)/100; payout -= fee; users[current].balance += payout; } const tx={type:'game',game:'coinflip',bet,choose,outcome,win,payout,ts:Date.now()}; users[current].tx.unshift(tx); // store recent
 users[current].cfRecent = users[current].cfRecent || []; users[current].cfRecent.unshift(tx); localStorage.setItem(LS,JSON.stringify(users)); renderBal(); renderTxMain(); renderCFRecent(); document.getElementById('result').textContent = win ? `WIN ₹${payout}` : `LOSE -₹${bet}`; }
function renderCFRecent(){ const el = document.getElementById('cfRecent'); if(!el) return; const arr = (current && users[current] && users[current].cfRecent) ? users[current].cfRecent.slice(0,20) : []; el.innerHTML = arr.map(r=>{ const d=new Date(r.ts).toLocaleString(); return `<div style="padding:6px;border-bottom:1px solid rgba(255,255,255,0.02)">${d} — ${r.choose} vs ${r.outcome} • ${r.win?`WIN +₹${r.payout}`:`LOSE -₹${r.bet}`}</div>`}).join(''); }

// Color Prediction logic
function playColor(){ if(!current){ alert('Login first'); return; } const bet = Number(document.getElementById('cpBet').value||0); const choose = document.getElementById('cpChoose').value; if(bet<=0){ alert('Enter bet'); return; } if(bet>users[current].balance){ alert('Insufficient'); return; } users[current].balance -= bet; // outcome: random among 3
 const colors=['red','green','blue']; const outcome = colors[Math.floor(Math.random()*3)]; const win = outcome===choose; let payout = 0; if(win){ payout = Math.round(bet * 2.8 * 100)/100; users[current].balance += payout; }
 const tx={type:'game',game:'colorpred',bet,choose,outcome,win,payout,ts:Date.now()}; users[current].tx.unshift(tx); users[current].cpRecent = users[current].cpRecent || []; users[current].cpRecent.unshift(tx); localStorage.setItem(LS,JSON.stringify(users)); renderBal(); renderTxMain(); renderCPRecent(); document.getElementById('result').textContent = win ? `WIN ₹${payout}` : `LOSE -₹${bet}`; }
function renderCPRecent(){ const el = document.getElementById('cpRecent'); if(!el) return; const arr = (current && users[current] && users[current].cpRecent) ? users[current].cpRecent.slice(0,20) : []; el.innerHTML = arr.map(r=>{ const d=new Date(r.ts).toLocaleString(); return `<div style="padding:6px;border-bottom:1px solid rgba(255,255,255,0.02)">${d} — ${r.choose} vs ${r.outcome} • ${r.win?`WIN +₹${r.payout}`:`LOSE -₹${r.bet}`}</div>`}).join(''); }

// Wallet and auth functions
function addQuickFromWallet(){ const val = Number(document.getElementById('quickAddMain').value); if(!current){ alert('Login first'); return; } users[current].balance = (users[current].balance||0) + val; users[current].tx.unshift({type:'add',amount:val,ts:Date.now(),note:'quick add'}); localStorage.setItem(LS,JSON.stringify(users)); renderBal(); renderTxMain(); }
function openWithdrawBox(){ document.getElementById('withdrawPanel').style.display='block'; }
function closeWithdrawBox(){ document.getElementById('withdrawPanel').style.display='none'; }
function requestWithdrawMain(){ if(!current){ alert('Login first'); return; } const amt = Number(document.getElementById('withdrawAmtMain').value||0); const to = document.getElementById('withdrawToMain').value.trim(); if(amt<=0 || !to){ alert('Enter amount and destination'); return; } if(amt > users[current].balance){ alert('Insufficient'); return; } users[current].balance -= amt; const req = {id:'WD'+Date.now(),amount:amt,to,ts:Date.now(),status:'requested'}; users[current].withdraws.unshift(req); users[current].tx.unshift({type:'withdraw_request',amount:amt,ts:Date.now(),note:to}); localStorage.setItem(LS,JSON.stringify(users)); renderBal(); renderTxMain(); alert('Withdraw requested (demo)'); closeWithdrawBox(); }

function renderTxMain(){ const el = document.getElementById('txMain'); if(!current || !users[current]){ el.innerText = 'Login to see history'; return; } const list = users[current].tx || []; el.innerHTML = list.slice(0,50).map(i=>{ const d = new Date(i.ts).toLocaleString(); if(i.type==='add') return `<div style=\"padding:6px;border-bottom:1px solid rgba(255,255,255,0.03)\"><strong style=\"color:#b6f7d0\">+₹${i.amount}</strong> — ${d}</div>`; if(i.type==='withdraw_request') return `<div style=\"padding:6px;border-bottom:1px solid rgba(255,255,255,0.03)\"><strong style=\"color:#ffb3b3\">-₹${i.amount}</strong> — ${d} • to ${i.note}</div>`; if(i.type==='game') return `<div style=\"padding:6px;border-bottom:1px solid rgba(255,255,255,0.03)\">${d} — ${i.game} • ${i.choose} vs ${i.outcome} • ${i.win?`WIN +₹${i.payout}`:`LOSE -₹${i.bet}`}</div>`; return `<div style=\"padding:6px;border-bottom:1px solid rgba(255,255,255,0.03)\">${d} — ${i.type}</div>` }).join(''); }

function renderAuthSmall(){ const el = document.getElementById('authSmall'); if(current && users[current]){ el.innerHTML = `<div style=\"font-weight:700;color:var(--white)\">${current}</div><div class=\"small\">Balance: ₹${users[current].balance}</div><div style=\"margin-top:8px\"><button class=\"nav-btn\" onclick=\"logoutUser()\">Logout</button></div>`; } else { el.innerHTML = `<div class=\"small\">You are not logged in.</div><div style=\"margin-top:8px\"><button class=\"primary\" onclick=\"openAuth()\">Login / Register</button></div>`; } }
function logoutUser(){ current = null; localStorage.removeItem('win_demo_current'); renderAuthSmall(); renderTop(); renderBal(); }

// admin demo
function adminMark(){ const pwd = prompt('Admin password (demo)'); if(pwd !== 'admin123') return alert('Wrong'); let all=[]; Object.entries(users).forEach(([em,ud]) => (ud.withdraws||[]).forEach(w=> all.push({em,w}))); if(all.length===0) return alert('No withdraws'); let msg='Withdraws:\n'; all.forEach((a,i)=> msg += `${i+1}. ${a.em} — ₹${a.w.amount} to ${a.w.to} id:${a.w.id}\n`); msg += '\nOpen console to mark paid'; alert(msg); console.log('ADMIN withdraws',all); const id = prompt('Enter withdraw id to mark paid'); if(!id) return; Object.entries(users).forEach(([em,ud])=>{ const idx = (ud.withdraws||[]).findIndex(x=>x.id===id); if(idx>=0){ ud.withdraws[idx].status='paid'; ud.tx.unshift({type:'withdraw_paid',amount:ud.withdraws[idx].amount,ts:Date.now(),note:'paid'}); localStorage.setItem(LS,JSON.stringify(users)); alert('Marked'); renderTxMain(); } }); }

// init
init();

</script>
</body>
</html>
