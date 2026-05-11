
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
      font-family: Arial, sans-serif;
    }

    body{
      min-height:100vh;
      display:flex;
      justify-content:center;
      align-items:center;
      background:linear-gradient(135deg,#ff1744,#ff4d6d,#ff758f,#ff9a8b,#fad0c4);
      overflow:hidden;
    }

    .card{
      width:95%;
      max-width:360px;
      min-height:75vh;
      overflow:hidden;
      max-width:420px;
      background:white;
      border-radius:25px;
      padding:35px 22px;
      text-align:center;
      box-shadow:0 20px 50px rgba(0,0,0,0.35); border:4px solid rgba(255,255,255,0.4); backdrop-filter:blur(5px);
      animation:float 3s ease-in-out infinite;
      position:relative;
      z-index:2;
    }

    @keyframes float{
      0%{transform:translateY(0px);}
      50%{transform:translateY(-10px);}
      100%{transform:translateY(0px);}
    }

    .heart{
      position:absolute;
      color:#ff1744;
      font-size:20px;
      animation:fall 5s linear infinite;
      opacity:0.7;
    }

    @keyframes fall{
      0%{
        transform:translateY(-100px) rotate(0deg);
      }
      100%{
        transform:translateY(100vh) rotate(360deg);
      }
    }

    h1{
      color:#ff1744;
      font-size:34px;
      margin-bottom:10px;
    }

    h2{
      color:#333;
      margin-bottom:15px;
    }

    p{
      color:#555;
      line-height:1.7;
      font-size:18px;
      margin-bottom:20px;
    }

    .btn{
      padding:14px 28px;
      border:none;
      border-radius:50px;
      background:linear-gradient(45deg,#ff1744,#ff5e78);
      color:white;
      font-size:18px;
      cursor:pointer;
      transition:0.3s;
      box-shadow:0 8px 20px rgba(255,23,68,0.4);
    }

    .btn:hover{
      transform:scale(1.08);
    }

    .hidden-message{
      margin-top:25px;
      display:none;
      animation:fade 1s ease;
    }

    @keyframes fade{
      from{opacity:0; transform:translateY(20px);}
      to{opacity:1; transform:translateY(0);}
    }

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


