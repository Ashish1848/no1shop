
<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Happy Birthday Bhabhi Ji</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;500;700&display=swap" rel="stylesheet">

<style>

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:'Poppins',sans-serif;
}

body{
    height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    overflow:hidden;
    background:linear-gradient(135deg,#ff0080,#ff4d6d,#ffb703);
}

/* PHONE SIZE CARD */

.phone{
    width:340px;
    height:690px;
    background:rgba(255,255,255,0.12);
    border-radius:40px;
    border:4px solid rgba(255,255,255,0.3);
    backdrop-filter:blur(12px);
    box-shadow:0 0 40px rgba(0,0,0,0.4);
    position:relative;
    overflow:hidden;
    padding:30px 20px;
    text-align:center;
    animation:float 3s ease-in-out infinite;
}

/* TOP CAMERA */

.camera{
    width:120px;
    height:25px;
    background:#111;
    border-radius:20px;
    position:absolute;
    top:10px;
    left:50%;
    transform:translateX(-50%);
}

h1{
    margin-top:70px;
    color:white;
    font-size:38px;
    text-shadow:0 0 15px white;
}

h2{
    color:#fff700;
    margin-top:10px;
    font-size:30px;
}

img{
    width:180px;
    height:180px;
    border-radius:50%;
    margin-top:25px;
    border:5px solid white;
    object-fit:cover;
    box-shadow:0 0 25px rgba(255,255,255,0.7);
}

p{
    color:white;
    margin-top:25px;
    font-size:18px;
    line-height:32px;
}

button{
    margin-top:35px;
    padding:16px 35px;
    border:none;
    border-radius:50px;
    background:white;
    color:#ff0080;
    font-size:20px;
    font-weight:bold;
    cursor:pointer;
    transition:0.4s;
    box-shadow:0 0 20px rgba(255,255,255,0.6);
}

button:hover{
    transform:scale(1.08);
    background:#fff700;
    color:#000;
}

/* FLOAT ANIMATION */

@keyframes float{
    0%{transform:translateY(0px);}
    50%{transform:translateY(-8px);}
    100%{transform:translateY(0px);}
}

/* HEARTS */

.hearts span{
    position:absolute;
    color:white;
    font-size:22px;
    animation:hearts 10s linear infinite;
    bottom:-100px;
}

.hearts span:nth-child(1){
    left:10%;
    animation-delay:0s;
}
.hearts span:nth-child(2){
    left:30%;
    animation-delay:2s;
}
.hearts span:nth-child(3){
    left:50%;
    animation-delay:4s;
}
.hearts span:nth-child(4){
    left:70%;
    animation-delay:1s;
}
.hearts span:nth-child(5){
    left:90%;
    animation-delay:3s;
}

@keyframes hearts{
    0%{
        transform:translateY(0) scale(0);
        opacity:1;
    }
    100%{
        transform:translateY(-900px) scale(1.5);
        opacity:0;
    }
}

</style>
</head>

<body>

<div class="phone">

    <div class="camera"></div>

    <div class="hearts">
        <span>💖</span>
        <span>🎂</span>
        <span>✨</span>
        <span>💝</span>
        <span>❤</span>
    </div>

    <h1>🎉 Happy Birthday 🎉</h1>

    <h2>Bhabhi Ji 💖</h2>

    <!-- PHOTO -->
    <img src="https://i.ibb.co/7QpKsCX/girl.png">

    <p>
        Aap hamare ghar ki<br>
        sabse pyari मुस्कान हो 😊<br><br>

        Bhagwan kare aapki har<br>
        wish puri ho ✨
    </p>

    <button onclick="wish()">
        Click Here 🎁
    </button>

</div>

<script>

function wish(){

    alert("💖 Dear Bhabhi Ji 💖\n\nAap hamesha khush raho 😊\n\nHappy Birthday 🎂✨");

}

</script>

</body>
</html>
