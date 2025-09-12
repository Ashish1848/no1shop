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
      max-width:420px;
      padding:22px;
      border-radius:12px;
      box-shadow:0 6px 18px rgba(20,20,50,0.08);
      text-align:left;
    }
    h2{ margin:0 0 10px; font-size:20px; color:#222; }
    p{ margin:6px 0 14px; color:#444; }
    .methods { display:flex; gap:12px; margin-bottom:14px; }
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
    }
    .upi { background:#28a745; color:#fff; border: none; }
    .upi[disabled], .upi.disabled {
      background:#bcd9c4; cursor:not-allowed;
    }
    .cod-btn { background:#007bff; color:#fff; }
    .small-input { width:120px; padding:8px; border-radius:6px; border:1px solid #ddd; }
    @media(max-width:420px){
      .methods { flex-direction:column; }
    }
  </style>
</head>
<body>
  <div class="box">
    <h2>भुगतान विकल्प</h2>
    <p>कृपया भुगतान का तरीका चुनें — यदि आप <strong>Cash on Delivery</strong> चुनते हैं तो राशि स्वतः ₹159 हो जाएगी।</p>

    <div class="methods" role="radiogroup" aria-label="भुगतान विकल्प">
      <label class="method" title="UPI से भुगतान">
        <input type="radio" name="payMethod" id="method-upi" value="upi" checked>
        <span>UPI पे (PhonePe / GPay / Paytm)</span>
      </label>

      <label class="method" title="Cash on Delivery">
        <input type="radio" name="payMethod" id="method-cod" value="cod">
        <span>Cash on Delivery (COD)</span>
      </label>
    </div>

    <div>
      <label for="amount">राशि (₹): </label>
      <!-- उपयोगकर्ता को राशि बदलने का ऑप्शन (UPI के लिए) -->
      <input id="amount" class="small-input" type="number" min="1" step="1" value="100" />
      <div class="note">नोट: COD चुनने पर राशि स्वतः ₹159 हो जाएगी और UPI बटन डिसेबल रहेगा।</div>
    </div>

    <div class="amount-row">
      <div>अंतिम राशि:</div>
      <div class="amount" id="finalAmount">₹100</div>
    </div>

    <!-- UPI link button -->
    <a id="upiButton" class="pay-btn upi"
       href="upi://pay?pa=8816058313@upi&pn=Ashish%20Rajput&am=100&cu=INR"
       rel="noopener noreferrer">
      UPI से भुगतान करें (Open UPI app)
    </a>

    <!-- COD proceed button -->
    <button id="codButton" class="pay-btn cod-btn" style="display:none;">
      COD पर ऑर्डर करें (₹159 पर)
    </button>

    <p class="note" id="statusMsg" style="display:none;"></p>
  </div>

  <script>
    // UPI विवरण — अपनी ज़रूरत के मुताबिक बदल लें
    const UPI_ID = "8816058313@upi";
    const UPI_NAME = "Ashish Rajput";

    const methodUpi = document.getElementById("method-upi");
    const methodCod = document.getElementById("method-cod");
    const amountInput = document.getElementById("amount");
    const finalAmountEl = document.getElementById("finalAmount");
    const upiButton = document.getElementById("upiButton");
    const codButton = document.getElementById("codButton");
    const statusMsg = document.getElementById("statusMsg");

    // Helper: UPI intent URL builder
    function buildUpiHref(amount) {
      const pa = encodeURIComponent(UPI_ID);
      const pn = encodeURIComponent(UPI_NAME);
      const am = encodeURIComponent(String(amount));
      return `upi://pay?pa=${pa}&pn=${pn}&am=${am}&cu=INR`;
    }

    // Update UI based on selected method and amount
    function updateUI() {
      const isCod = methodCod.checked;
      let amount = Number(amountInput.value) || 0;

      if (isCod) {
        // जब COD चुना गया — राशि फिक्स 159
        amount = 159;
        amountInput.value = amount; // दिखाने के लिए भी सेट करें
        finalAmountEl.textContent = "₹" + amount;
        // Disable/grey-out UPI button
        upiButton.setAttribute("aria-disabled", "true");
        upiButton.classList.add("disabled");
        upiButton.setAttribute("disabled", "true");
        upiButton.href = "javascript:void(0);";
        // Show COD button, hide UPI button
        upiButton.style.display = "none";
        codButton.style.display = "block";
        statusMsg.style.display = "block";
        statusMsg.textContent = "आपने Cash on Delivery चुना है — अंतिम राशि ₹159 होगी।";
      } else {
        // UPI चुना गया — user-controlled amount
        // अगर user ने amount < 1 दिया तो 1 set करें
        if (amount < 1) amount = 1;
        finalAmountEl.textContent = "₹" + amount;
        upiButton.href = buildUpiHref(amount);
        upiButton.removeAttribute("disabled");
        upiButton.classList.remove("disabled");
        upiButton.style.display = "block";
        codButton.style.display = "none";
        statusMsg.style.display = "none";
      }
    }

    // Event listeners
    methodUpi.addEventListener("change", updateUI);
    methodCod.addEventListener("change", updateUI);
    amountInput.addEventListener("input", function(){
      // अगर COD selected है, amount input override कर देंगे
      if(methodCod.checked){
        amountInput.value = 159;
      }
      updateUI();
    });

    // COD button - यह अभी सिर्फ UI के लिए है, आप यहाँ order submission का ajax जोड़ सकते हैं
    codButton.addEventListener("click", function(){
      // यहाँ आप अपना ऑर्डर सबमिट करने वाली request भेज सकते हैं
      // अभी बस confirmation दिखा रहा हूँ
      alert("धन्यवाद! आपका ऑर्डर COD (₹159) पर लिया गया है। हम शीघ्र संपर्क करेंगे।");
      // अगर चाहें तो यहां redirect या फॉर्म सबमिट करें
    });

    // Initialize UI on page load
    updateUI();
  </script>
</body>
</html>
