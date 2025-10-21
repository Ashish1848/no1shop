<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Drone World</title>
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">
<style>
* {margin:0; padding:0; box-sizing:border-box; font-family: 'Roboto', sans-serif;}
body { background: linear-gradient(180deg,#f0f2f5,#e1e8f0); color:#333; }

/* Header */
header { background:#0d1b2a; color:#fff; padding:20px; text-align:center; }
header h1 { font-size:2.5em; margin-bottom:10px; }
nav a { color:#fff; text-decoration:none; margin:0 15px; font-weight:bold; }
nav a:hover { text-decoration:underline; }

/* Hero */
.hero { text-align:center; padding:50px 20px; background:#e1e8f0; }
.hero h2 { font-size:2.5em; margin-bottom:20px; color:#0d1b2a; }
.hero p { font-size:1.2em; margin-bottom:30px; }

/* Slider */
.slider { max-width:600px; margin:0 auto 30px auto; position:relative; border-radius:12px; overflow:hidden; box-shadow:0 5px 15px rgba(0,0,0,0.2); }
.slides img { width:100%; display:none; transition: transform 0.5s ease; border-radius:12px; }
.slides img.active { display:block; transform: scale(1.05); }

/* Prev/Next buttons */
.prev, .next { position:absolute; top:50%; transform:translateY(-50%); background:rgba(0,0,0,0.5); color:#fff; padding:10px; cursor:pointer; border:none; border-radius:50%; z-index:2; }
.prev { left:10px; }
.next { right:10px; }

/* Dots */
.dots { text-align:center; margin-top:10px; }
.dots span { display:inline-block; width:12px; height:12px; margin:0 5px; background:#bbb; border-radius:50%; cursor:pointer; transition:0.3s; }
.dots span.active { background:#ff6b00; transform:scale(1.2); }

/* Product Info */
.product-info { text-align:center; margin-bottom:50px; }
.product-info h3 { font-size:2em; margin-bottom:10px; color:#0d1b2a; }
.product-info p { font-size:1.1em; margin-bottom:20px; }
.product-info button {
  background: linear-gradient(45deg,#ff6b00,#ff3d00); color:#fff; border:none;
  padding:15px 30px; font-size:1.2em; cursor:pointer; border-radius:8px; box-shadow:0 5px 15px rgba(0,0,0,0.2);
  transition:0.3s;
}
.product-info button:hover { transform:scale(1.05); }

/* Features Section */
.features { display:grid; grid-template-columns:repeat(auto-fit, minmax(200px,1fr)); gap:20px; padding:50px 20px; background:#fff; }
.feature-card { background:#f8f8f8; border-radius:12px; padding:30px 20px; text-align:center; box-shadow:0 5px 15px rgba(0,0,0,0.1); transition:0.3s; cursor:pointer; }
.feature-card:hover { transform:translateY(-10px); box-shadow:0 10px 25px rgba(0,0,0,0.2); }
.feature-card i { font-size:2em; margin-bottom:15px; color:#ff6b00; display:block; }
.feature-card h4 { margin-bottom:10px; font-size:1.3em; color:#0d1b2a; }
.feature-card p { font-size:1em; }

/* Bottom Section - Why Choose */
.why-choose { background:#0d1b2a; color:#fff; padding:50px 20px; text-align:center; }
.why-choose h3 { font-size:2em; margin-bottom:30px; color:#ff6b00; }
.why-choose .cards { display:grid; grid-template-columns:repeat(auto-fit, minmax(200px,1fr)); gap:20px; }
.why-choose .card { background:#1b3a57; padding:20px; border-radius:12px; transition:0.3s; }
.why-choose .card:hover { transform:translateY(-10px); box-shadow:0 10px 20px rgba(0,0,0,0.3); }
.why-choose .card h4 { margin-bottom:10px; }
.why-choose .card p { font-size:0.95em; }

/* Return Policy Accordion */
.return-policy { background:#e1e8f0; padding:50px 20px; text-align:center; }
.return-policy h3 { font-size:2em; margin-bottom:20px; color:#0d1b2a; cursor:pointer; display:inline-block; }
.return-policy p { font-size:1.1em; max-width:700px; margin:20px auto 0 auto; line-height:1.6; display:none; transition:0.3s; }

/* Footer */
footer { background:#0d1b2a; color:#fff; text-align:center; padding:20px; margin-top:50px; }
footer a { color:#ff6b00; text-decoration:none; margin:0 10px; }

/* Responsive */
@media(max-width:768px){
  .hero h2 { font-size:2em; }
  .hero p { font-size:1em; }
  .product-info h3 { font-size:1.5em; }
  .why-choose .cards { grid-template-columns:1fr; }
  .features { grid-template-columns:1fr; }
}
</style>
<script src="https://kit.fontawesome.com/a076d05399.js" crossorigin="anonymous"></script>
</head>
<body>

<header>
  <h1>Drone World</h1>
  <nav>
    <a href="#">होम</a>
    <a href="#features">Features</a>
    <a href="#why-choose">Why Choose</a>
    <a href="#return-policy">Return Policy</a>
    <a href="#">संपर्क करें</a>
  </nav>
</header>

<section class="hero">
  <h2>असली ड्रोन का अनुभव</h2>
  <p>उच्च गुणवत्ता वाले ड्रोन आपके लिए तैयार।</p>

  <div class="slider">
    <div class="slides">
   <a href="https://ibb.co/93c6WW3s"><img src="https://i.ibb.co/wrBV44rM/41.jpg" /></a>
      <a href="https://ibb.co/CKdCJGWP"><img src="https://i.ibb.co/Wv98DJsV/image.jpg" /></a>
    <a href="https://imgbb.com/"><img src="https://i.ibb.co/RxSsNp1/IMG-20250919-WA0002.jpg" alt="IMG-20250919-WA0002" border="0" /></a>
    </div>
    <button class="prev">&#10094;</button>
    <button class="next">&#10095;</button>
  </div>
  <div class="dots">
    <span class="dot active"></span>
    <span class="dot"></span>
    <span class="dot"></span>
    <span class="dot"></span>
  </div>

  <div class="product-info">
    <h3>Drone X100</h3>
    <p>बेहतरीन कैमरा, स्टेबल फ्लाइट और लंबी बैटरी लाइफ।</p>
    <button>अभी खरीदें</button>
  </div>
</section>

<section id="features" class="features">
  <div class="feature-card">
    <i class="fas fa-camera"></i>
    <h4>उच्च गुणवत्ता कैमरा</h4>
    <p>4K वीडियो और HD फोटो के लिए बेहतरीन कैमरा।</p>
  </div>
  <div class="feature-card">
    <i class="fas fa-battery-full"></i>
    <h4>लंबी बैटरी लाइफ</h4>
    <p>एक बार चार्ज करने पर 30 मिनट की उड़ान।</p>
  </div>
  <div class="feature-card">
    <i class="fas fa-arrows-alt-v"></i>
    <h4>स्टेबल फ्लाइट</h4>
    <p>विंड और वातावरण के अनुसार स्थिर उड़ान।</p>
  </div>
  <div class="feature-card">
    <i class="fas fa-gamepad"></i>
    <h4>रिमोट कंट्रोल</h4>
    <p>स्मार्ट और आसान नियंत्रण रेंज के साथ।</p>
  </div>
</section>

<section id="why-choose" class="why-choose">
  <h3>क्यों चुनें Drone X100?</h3>
  <div class="cards">
    <div class="card">
      <h4>टॉप क्वालिटी मैटीरियल</h4>
      <p>मजबूत और हल्का फ्रेम, जो लंबे समय तक टिकता है।</p>
    </div>
    <div class="card">
      <h4>स्मार्ट टेक्नोलॉजी</h4>
      <p>उन्नत सेंसर और ऑटो फ्लाइट मोड्स।</p>
    </div>
    <div class="card">
      <h4>सुरक्षित और आसान</h4>
      <p>ऑटो स्टॉप और इमरजेंसी लैंडिंग फीचर।</p>
    </div>
    <div class="card">
      <h4>ग्राहक संतुष्टि</h4>
      <p>7 दिन रिटर्न पॉलिसी और फास्ट सपोर्ट।</p>
    </div>
  </div>
</section>

<section id="return-policy" class="return-policy">
  <h3>Return Policy</h3>
  <p>अगर आप अपने ड्रोन से संतुष्ट नहीं हैं, तो आप इसे खरीदने के 7 दिनों के भीतर रिटर्न कर सकते हैं। रिटर्न प्रक्रिया आसान और बिना किसी झंझट के है। कृपया उत्पाद को मूल पैकेजिंग में और सभी एक्सेसरीज के साथ लौटाएं। रिफंड आपके ऑर्डर के माध्यम से जल्दी प्रोसेस किया जाएगा।</p>
</section>

<footer>
  <p>&copy; 2025 Drone World | <a href="#">प्राइवेसी पॉलिसी</a> | <a href="#">टर्म्स & कंडीशंस</a></p>
</footer>

<script>
/* Slider */
let current = 0;
const slides = document.querySelectorAll('.slides img');
const dots = document.querySelectorAll('.dot');
const total = slides.length;

function showSlide(index){
  slides.forEach((img,i)=>{
    img.classList.remove('active');
    dots[i].classList.remove('active');
  });
  slides[index].classList.add('active');
  dots[index].classList.add('active');
  current = index;
}

document.querySelector('.next').addEventListener('click',()=>{ showSlide((current+1)%total); });
document.querySelector('.prev').addEventListener('click',()=>{ showSlide((current-1+total)%total); });
dots.forEach((dot,i)=>{ dot.addEventListener('click',()=>{ showSlide(i); }); });

// Auto slide
setInterval(()=>{ showSlide((current+1)%total); },3000);

// Return Policy Accordion
const policy = document.querySelector('.return-policy h3');
const policyText = document.querySelector('.return-policy p');
policy.addEventListener('click', ()=>{ policyText.style.display = policyText.style.display === 'block' ? 'none' : 'block'; });
</script>

</body>
</html>
