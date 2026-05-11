<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Bhabhi Ji Birthday Surprise</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family: 'Poppins', sans-serif;
}

body{
    height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    overflow:hidden;
    background:linear-gradient(135deg,#ff0080,#ff8c00,#ffd700);
}

.card{
    position:relative;
    width:350px;
    height:500px;
    background:rgba(255,255,255,0.15);
    backdrop-filter:blur(10px);
    border-radius:25px;
    border:2px solid rgba(255,255,255,0.3);
    box-shadow:0 0 30px rgba(0,0,0,0.3);
    text-align:center;
    padding:30px;
    color:white;
    overflow:hidden;
    animation:float 3s ease-in-out infinite;
}

.card::before{
    content:"";
    position:absolute;
    width:500px;
    height:500px;
    background:rgba(255,255,255,0.1);
    border-radius:50%;
    top:-250px;
    left:-100px;
}

h1{
    font-size:40px;
    margin-top:40px;
    text-shadow:0 0 10px #fff;
}

h2{
    font-size:28px;
    margin-top:15px;
    color:#fff700;
}

p{
    margin-top:25px;
    font-size:18px;
    line-height:30px;
}

button{
    margin-top:35px;
    padding:15px 35px;
    border:none;
    border-radius:50px;
    background:white;
    color:#ff0080;
    font-size:18px;
    font-weight:bold;
    cursor:pointer;
    transition:0.4s;
}

button:hover{
    transform:scale(1.1);
    background:#fff700;
}

@keyframes float{
    0%{transform:translateY(0px);}
    50%{transform:translateY(-10px);}
    100%{transform:translateY(0px);}
}

.hearts{
    position:absolute;
    width:100%;
    height:100%;
    top:0;
    left:0;
    overflow:hidden;
    z-index:-1;
}

.hearts span{
    position:absolute;
    display:block;
    color:white;
    font-size:25px;
    animation:animate 10s linear infinite;
}

@keyframes animate{
    0%{
        transform:translateY(100vh) scale(0);
        opacity:1;
    }
    100%{
        transform:translateY(-100vh) scale(1.5);
        opacity:0;
    }
}
</style>
</head>

<body>

<div class="hearts">
    <span style="left:10%; animation-delay:0s;">❤</span>
    <span style="left:25%; animation-delay:2s;">💖</span>
    <span style="left:40%; animation-delay:4s;">✨</span>
    <span style="left:55%; animation-delay:1s;">🎂</span>
    <span style="left:70%; animation-delay:3s;">💝</span>
    <span style="left:85%; animation-delay:5s;">❤</span>
</div>

<div class="card">

    <h1>🎉 Happy Birthday 🎉</h1>

    <h2>Bhabhi Ji 💖</h2>

    <p>
        Aap hamesha haste raho 😊<br>
        Aapki har wish puri ho ✨<br><br>
        Bhagwan aapko duniya ki<br>
        saari khushiyan de 💝
    </p>

    <button onclick="showMessage()">
        Click Here 🎁
    </button>

</div>

<script>
function showMessage(){
    alert("💖 Dear Bhabhi Ji 💖\n\nAap is duniya ki sabse pyari aur special Bhabhi ho 😊\n\nHappy Birthday Once Again 🎂✨");
}
</script>

</body>
</html>    }

    .cake{
      font-size:80px;
      margin-bottom:15px;
    }

    .glow{
      position:absolute;
      width:200px;
      height:200px;
      background:rgba(255,105,180,0.25);
      border-radius:50%;
      top:-60px;
      right:-60px;
      filter:blur(40px);
      animation:pulse 3s infinite;
    }

    @keyframes pulse{
      0%{transform:scale(1);opacity:0.6;}
      50%{transform:scale(1.3);opacity:1;}
      100%{transform:scale(1);opacity:0.6;}
    }

    .special{
      color:#ff1744;
      font-size:22px;
      font-weight:bold;
    }
  

    @media(max-width:480px){
      .card{
        width:92%;
        min-height:80vh;
        border-radius:30px;
        padding:40px 20px;
      }

      h1{
        font-size:32px;
      }

      h2{
        font-size:28px;
      }

      .btn{
        width:100%;
        padding:16px;
        font-size:20px;
      }

      .special{
        font-size:24px;
      }
    }
  </style>
</head>
<body>

  <audio autoplay loop>
    <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mp3">
  </audio>

  <div class="card">
    <div class="glow"></div>
    <div class="cake">🎂✨🎉💖</div>

    <h1>Happy Birthday</h1>
    <h2>Bhabhi Ji ❤️</h2>

    <p>
      Aaj ka din bahut special hai,
      kyuki aaj hamari pyari Bhabhi Ji ka birthday hai ✨🎉
      
      Aapki smile sabko khush kar deti hai ❤️
    </p>

    <button class="btn" onclick="showMessage()">
      Click For Magic ✨
    </button>

    <div class="hidden-message" id="msg">
      <p class="special">
        Bhabhi Ji ❤️
        
        Aap hamesha haste raho 😊
        
        Bhagwan aapko har khushi de 🌸
        
        Aapki life hamesha smile aur pyar se bhari rahe ❤️
        
        Aap hamare ghar ki muskan ho ❤️✨
        
        Aapka har din khushiyon se bhara rahe 🌸
        
        🎂 Happy Birthday Bhabhi Ji 🎉
      </p>
    </div>
  </div>

  <script>
    function showMessage(){
      document.getElementById('msg').style.display='block';
    }

    // Floating hearts and sparkles
    for(let i=0;i<25;i++){
      let heart=document.createElement('div');
      heart.classList.add('heart');
      heart.innerHTML='❤';
      heart.style.left=Math.random()*100+'vw';
      heart.style.animationDuration=(Math.random()*3+2)+'s';
      heart.style.fontSize=(Math.random()*20+15)+'px';
      document.body.appendChild(heart);
    }
  </script>

</body>
</html>
```


