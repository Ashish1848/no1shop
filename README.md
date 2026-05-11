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
    background:linear-gradient(135deg,#ff0080,#ff4d6d,#ffb703);
    overflow:hidden;
}

/* MAIN CARD */

.card{
    width:90%;
    max-width:340px;
    padding:30px 20px;
    border-radius:25px;
    background:rgba(255,255,255,0.15);
    backdrop-filter:blur(10px);
    text-align:center;
    color:white;
    box-shadow:0 0 25px rgba(0,0,0,0.3);
    animation:updown 3s infinite ease-in-out;
}

/* TITLE */

h1{
    font-size:32px;
    margin-bottom:10px;
}

h2{
    font-size:28px;
    color:#fff700;
    margin-bottom:20px;
}

/* IMAGE */

img{
    width:140px;
    height:140px;
    border-radius:50%;
    border:4px solid white;
    object-fit:cover;
    margin-bottom:20px;
}

/* TEXT */

p{
    font-size:18px;
    line-height:30px;
}

/* BUTTON */

button{
    margin-top:25px;
    padding:14px 28px;
    border:none;
    border-radius:40px;
    background:white;
    color:#ff0080;
    font-size:18px;
    font-weight:bold;
    cursor:pointer;
    transition:0.3s;
}

button:hover{
    transform:scale(1.05);
    background:#fff700;
    color:black;
}

/* HEARTS */

.hearts span{
    position:absolute;
    bottom:-50px;
    font-size:24px;
    animation:heart 8s linear infinite;
}

.hearts span:nth-child(1){left:10%; animation-delay:0s;}
.hearts span:nth-child(2){left:30%; animation-delay:2s;}
.hearts span:nth-child(3){left:50%; animation-delay:4s;}
.hearts span:nth-child(4){left:70%; animation-delay:1s;}
.hearts span:nth-child(5){left:90%; animation-delay:3s;}

@keyframes heart{
    0%{
        transform:translateY(0) scale(0);
        opacity:1;
    }
    100%{
        transform:translateY(-900px) scale(1.5);
        opacity:0;
    }
}

/* FLOAT */

@keyframes updown{
    0%{transform:translateY(0);}
    50%{transform:translateY(-8px);}
    100%{transform:translateY(0);}
}

</style>
</head>

<body>

<div class="hearts">
    <span>💖</span>
    <span>🎂</span>
    <span>✨</span>
    <span>💝</span>
    <span>❤</span>
</div>

<div class="card">

    <h1>🎉 Happy Birthday 🎉</h1>

    <h2>Bhabhi Ji 💖</h2>

    <img src="https://cdn-icons-png.flaticon.com/512/4140/4140048.png">

    <p>
        Aap hamesha haste raho 😊<br>
        Aapki har wish puri ho ✨<br><br>
        Bhagwan aapko duniya ki<br>
        saari khushiyan de 💝
    </p>

    <button onclick="showWish()">
        Click Here 🎁
    </button>

</div>

<script>

function showWish(){

    alert("💖 Dear Bhabhi Ji 💖\n\nAap hamare ghar ki sabse special ho 😊\n\nHappy Birthday 🎂✨");

}

</script>

</body>
</html>
