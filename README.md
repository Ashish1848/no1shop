<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Happy Birthday Bhabhi Ji</title>

<style>

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:Arial,sans-serif;
}

body{
    height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    overflow:hidden;
    background:linear-gradient(135deg,#ff006e,#8338ec,#3a86ff);
}

/* PHONE FRAME */

.phone{
    width:340px;
    height:680px;
    background:#111;
    border-radius:40px;
    padding:12px;
    box-shadow:
    0 0 25px rgba(0,0,0,0.5),
    0 0 50px rgba(255,255,255,0.2);
    position:relative;
}

/* SCREEN */

.screen{
    width:100%;
    height:100%;
    border-radius:32px;
    overflow:hidden;
    position:relative;
    background:linear-gradient(180deg,#ff4d6d,#ff758f,#ffb703);
    display:flex;
    flex-direction:column;
    align-items:center;
    text-align:center;
    padding:25px 18px;
}

/* TOP NOTCH */

.notch{
    width:120px;
    height:22px;
    background:#000;
    border-radius:20px;
    margin-bottom:20px;
}

/* HEARTS */

.hearts span{
    position:absolute;
    bottom:-50px;
    font-size:22px;
    animation:fly 8s linear infinite;
}

.hearts span:nth-child(1){left:10%; animation-delay:0s;}
.hearts span:nth-child(2){left:25%; animation-delay:2s;}
.hearts span:nth-child(3){left:45%; animation-delay:4s;}
.hearts span:nth-child(4){left:65%; animation-delay:1s;}
.hearts span:nth-child(5){left:85%; animation-delay:3s;}

@keyframes fly{
    0%{
        transform:translateY(0) scale(0);
        opacity:1;
    }
    100%{
        transform:translateY(-800px) scale(1.5);
        opacity:0;
    }
}

/* TEXT */

h1{
    color:white;
    font-size:34px;
    margin-top:15px;
    text-shadow:0 0 10px rgba(255,255,255,0.8);
}

h2{
    color:#fff700;
    font-size:30px;
    margin-top:8px;
}

/* IMAGE */

.photo{
    width:160px;
    height:160px;
    border-radius:50%;
    overflow:hidden;
    border:5px solid white;
    margin-top:25px;
    box-shadow:0 0 25px rgba(255,255,255,0.7);
}

.photo img{
    width:100%;
    height:100%;
    object-fit:cover;
}

/* MESSAGE */

p{
    color:white;
    font-size:19px;
    line-height:32px;
    margin-top:25px;
}

/* BUTTON */

button{
    margin-top:auto;
    margin-bottom:25px;
    padding:15px 35px;
    border:none;
    border-radius:40px;
    background:white;
    color:#ff006e;
    font-size:20px;
    font-weight:bold;
    cursor:pointer;
    transition:0.3s;
    box-shadow:0 0 20px rgba(255,255,255,0.5);
}

button:active{
    transform:scale(0.95);
}

/* POPUP */

.popup{
    position:absolute;
    inset:0;
    background:rgba(0,0,0,0.8);
    display:none;
    justify-content:center;
    align-items:center;
    padding:20px;
}

.popup-box{
    width:100%;
    background:white;
    border-radius:25px;
    padding:30px 20px;
    text-align:center;
    animation:zoom 0.5s ease;
}

.popup-box h3{
    color:#ff006e;
    font-size:28px;
    margin-bottom:15px;
}

.popup-box p{
    color:#333;
    font-size:18px;
    line-height:30px;
}

.popup-box button{
    margin-top:20px;
    background:#ff006e;
    color:white;
}

@keyframes zoom{
    from{
        transform:scale(0.5);
        opacity:0;
    }
    to{
        transform:scale(1);
        opacity:1;
    }
}

</style>
</head>

<body>

<div class="phone">

<div class="screen">

<div class="hearts">
<span>💖</span>
<span>🎂</span>
<span>✨</span>
<span>💝</span>
<span>❤</span>
</div>

<div class="notch"></div>

<h1>🎉 Happy Birthday 🎉</h1>

<h2>Bhabhi Ji 💖</h2>

<div class="photo">
<img src="https://cdn-icons-png.flaticon.com/512/4140/4140048.png">
</div>

<p>
Aap hamesha khush raho 😊<br>
Aapki har wish puri ho ✨<br><br>
Aap hamare ghar ki<br>
sabse pyari smile ho 💝
</p>

<button onclick="openPopup()">
Open Surprise 🎁
</button>

<div class="popup" id="popup">

<div class="popup-box">

<h3>💖 Dear Bhabhi Ji 💖</h3>

<p>
Aap jaisi caring aur pyari<br>
Bhabhi sabko nahi milti 😊<br><br>

Bhagwan aapko hamesha<br>
khush rakhe ✨<br><br>

🎂 Happy Birthday 🎂
</p>

<button onclick="closePopup()">
Close
</button>

</div>

</div>

</div>
</div>

<script>

function openPopup(){
document.getElementById("popup").style.display="flex";
}

function closePopup(){
document.getElementById("popup").style.display="none";
}

</script>

</body>
</html>
