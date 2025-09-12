<!DOCTYPE html>
<html lang="hi">
<head>
  <meta charset="utf-8" />
  <title>भुगतान करें</title>
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <style>
    body {
      font-family: "Noto Sans", Arial, sans-serif;
      background:#f6f7fb;
      margin:0;
      padding:30px 15px;
      display:flex;
      align-items:center;
      justify-content:center;
      min-height:100vh;
    }
    .box{
      background:#fff;
      width:100%;
      max-width:440px;
      padding:22px;
      border-radius:12px;
      box-shadow:0 6px 18px rgba(20,20,50,0.08);
      text-align:left;
    }
    h2{ margin:0 0 10px; font-size:20px; color:#222; }
    p{ margin:6px 0 14px; color:#444; }
    .methods { display:flex; flex-wrap:wrap; gap:12px; margin-bottom:14px; }
    .method {
      display:flex; align-items:center; gap:8px;
      padding:8px 12px; border-radius:8px; cursor:pointer;
      border:1px solid #e6e9ef;
    }
    .method input { transform:scale(1.1); }
    .amount-row { display:flex; align-items:center; justify-content:space-between; margin-top:12px; }
    .amount {
      font-size:22px; font-weight:700; color:#111;
    }
    .note { font-size:13px; color:#666; margin-top:10px; }
    .pay-btn {
      display:block;
      width:100%;
      text-align:center;
      padding:12px 14px;
      margin-top:18px;
      border-radius:8px;
      text-decoration:none;
      font-size:16px;
      font-weight:600;
      border:none;
      cursor:pointer;
      background:#28a745; 
      color:#fff;
    }
    .small-input { width:120px; padding:8px; border-radius:6px; border:1px solid #ddd; }
    #qrBox {
      display:none;
      text-align:center;
      margin-top:15px;
    }
    #qrBox img {
      width:200px;
      height:200px;
      border:1px solid #ccc;
      padding:5px;
      border-radius:8px;
      background:#fff;
    }
    @media(max-width:420px){
      .methods { flex-direction:column; }
    }
  </style>
</head>
<body>
  <div class="box">
    <h2>भुगतान विकल्प</h2>
    <p>कृपया भुगतान का तरीका चुनें।</p>

    <div class="methods" role="radiogroup" aria-label="भुगतान विकल्प">
      <label class="method">
        <input type="radio" name="payMethod" id="method-upi" value="upi" checked>
        <span>UPI पे</span>
      </label>

      <label class="method">
        <input type="radio" name="payMethod" id="method-cod" value="cod">
        <span>Cash on Delivery (COD)</span>
      </label>

      <label class="method">
        <input type="radio" name="payMethod" id="method-qr" value="qr">
        <span>QR Code </span>
      </label>
    </div>

    <div id="upiAmountBox">
      <label for="amount">राशि (₹): </label>
      <input id="amount" class="small-input" type="number" min="1" step="1" value="799" />
    </div>

    <div class="amount-row">
      <div>अंतिम राशि:</div>
      <div class="amount" id="finalAmount">₹799</div>
    </div>

    <!-- Payment button -->
    <a id="payButton" class="pay-btn"
       href="upi://pay?pa=1848ashish@fam=Ashish%20Rajput&am=799&cu=INR">
       भुगतान करें
    </a>

    <!-- QR Code Box -->
    <div id="qrBox">
      <p>इस QR को स्कैन करके UPI पेमेंट करें:</p>
      <!-- Google Chart API से QR कोड -->
      <img id="qrImage" src="https://ibb.co/bgVHLtmk" alt="UPI QR Code" />
    </div>
  </div>

  <script>
    const UPI_ID = "8816058313@upi";
    const UPI_NAME = "Ashish Rajput";

    const methodUpi = document.getElementById("method-upi");
    const methodCod = document.getElementById("method-cod");
    const methodQr = document.getElementById("method-qr");
    const amountInput = document.getElementById("amount");
    const finalAmountEl = document.getElementById("finalAmount");
    const payButton = document.getElementById("payButton");
    const upiAmountBox = document.getElementById("upiAmountBox");
    const qrBox = document.getElementById("qrBox");
    const qrImage = document.getElementById("qrImage");

    // UPI लिंक बनाने का फ़ंक्शन
    function buildUpiHref(amount) {
      const pa = encodeURIComponent(UPI_ID);
      const pn = encodeURIComponent(UPI_NAME);
      const am = encodeURIComponent(String(amount));
      return `upi://pay?pa=${pa}&pn=${pn}&am=${am}&cu=INR`;
    }

    // QR कोड URL बनाना
    function buildQr(amount) {
      const url = buildUpiHref(amount);
      return `https://chart.googleapis.com/chart?cht=qr&chs=300x300&chl=${encodeURIComponent(url)}`;
    }

    function updateUI() {
      let amount = Number(amountInput.value) || 0;

      if (methodCod.checked) {
        amount = 159; // COD पर fix
        upiAmountBox.style.display = "none";
        qrBox.style.display = "none";
        payButton.style.display = "block";
        payButton.href = buildUpiHref(amount);
      } else if (methodUpi.checked) {
        if (amount < 1) amount = 1;
        upiAmountBox.style.display = "block";
        qrBox.style.display = "none";
        payButton.style.display = "block";
        payButton.href = buildUpiHref(amount);
      } else if (methodQr.checked) {
        if (amount < 1) amount = 1;
        upiAmountBox.style.display = "block";
        qrBox.style.display = "block";
        payButton.style.display = "none";
        qrImage.src = buildQr(amount);
      }

      finalAmountEl.textContent = "₹" + amount;
    }

    methodUpi.addEventListener("change", updateUI);
    methodCod.addEventListener("change", updateUI);
    methodQr.addEventListener("change", updateUI);
    amountInput.addEventListener("input", updateUI);

    updateUI();
  </script>
</body>
</html>
