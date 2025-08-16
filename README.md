<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Surprise for Cheeku 💝</title>
  <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Roboto&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      padding: 0;
      font-family: 'Roboto', sans-serif;
      background: linear-gradient(135deg, #ffe6f0, #ffe0f7);
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      text-align: center;
      color: #333;
    }

    .screen {
      background: #fff;
      padding: 40px;
      border-radius: 20px;
      box-shadow: 0 8px 25px rgba(0, 0, 0, 0.2);
      max-width: 500px;
      animation: fadeIn 1s ease;
    }

    h1 {
      font-family: 'Great Vibes', cursive;
      font-size: 2.5em;
      color: #e91e63;
      margin-bottom: 20px;
    }

    p {
      font-size: 1.1em;
      line-height: 1.6;
      margin-bottom: 20px;
    }

    button {
      margin-top: 20px;
      padding: 12px 25px;
      font-size: 1em;
      background-color: #e91e63;
      color: #fff;
      border: none;
      border-radius: 25px;
      cursor: pointer;
      transition: 0.3s;
    }

    button:hover {
      background-color: #d81b60;
    }

    #mainContent {
      display: none;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(30px); }
      to { opacity: 1; transform: translateY(0); }
    }
  </style>
</head>
<body>

  <!-- First Screen -->
  <div class="screen" id="startScreen">
    <h1>Hey Cheeku 💌</h1>
    <p>Tere liye ek chhota sa reply hai...<br> Click karo dekhne ke liye 🥺</p>
    <button onclick="showMain()">Click to Reveal 💖</button>
  </div>

  <!-- Main Content -->
  <div class="screen" id="mainContent">
    <h1>Thank You, Cheeku 💕</h1>
    <p>
      Tumhari wish ne mera birthday ko aur bhi khaas bana diya...<br>
      Sach kahu toh, tum ho toh sab kuch perfect lagta hai 😇
    </p>
    <p>
      Thank you kehna chhota lagega, lekin phir bhi...<br>
      Thank you for being mine 🫶

      hor ha I LOVE YOU☺️   jada serious mat lena  ye Friendship wala hai 😊
    </p>
    <button onclick="showMore()">Click Again 😳</button>
    <div id="moreMsg" style="display:none; margin-top: 20px; color:#4caf50;">
      Aaj tumne wish kiya...<br>
      uske liye ek bar or thanks 💍✨
        ❤️‍🩹I LOVE YOU ❤️‍🩹
    </div>
  </div>

  <script>
    function showMain() {
      document.getElementById('startScreen').style.display = 'none';
      document.getElementById('mainContent').style.display = 'block';
    }

    function showMore() {
      document.getElementById('moreMsg').style.display = 'block';
    }
  </script>

</body>
</html>
