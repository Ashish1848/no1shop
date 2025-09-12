<!DOCTYPE html>
<html lang="hi">
<head>
  <meta charset="UTF-8">
  <title>भुगतान करें</title>
  <style>
    body { 
      text-align: center; 
      font-family: sans-serif; 
      background: #f8f8f8; 
      padding: 30px; 
    }
    .box {
      background: white;
      padding: 20px;
      margin: 0 auto;
      max-width: 500px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    img {
      width: 300px;
      margin: 20px 0;
      border: 1px solid #ccc;
      padding: 10px;
      border-radius: 10px;
    }
    button {
      padding: 10px 20px;
      background: #4CAF50;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      font-size: 16px;
    }
    .success {
      color: green;
      margin-top: 20px;
      font-weight: bold;
      display: none;
    }
    hr {
      margin: 20px 0;
    }
    #userDetails p {
      text-align: left;
      margin-left: 30px;
    }
    #codNote {
      display: none;
      margin-top: 15px;
      background: #fff3cd;
      padding: 10px;
      border: 1px solid #ffeeba;
      border-radius: 5px;
      color: #856404;
    }
    .payment-options {
      margin-top: 20px;
      text-align: left;
    }
    .payment-options label {
      display: block;
      margin: 10px 0;
      font-size: 16px;
    }

    @media(max-width: 600px) {
      .container {
        flex-direction: column;
        align-items: center;
      }
      img {
        max-width: 100%;
        height: auto;
      }
      .payment-options {
        text-align: center;
      }
      #userDetails p {
        margin-left: 0;
        text-align: center;
      }
    }




 body { 
      text-align: center; 
      font-family: sans-serif; 
      background: #f8f8f8; 
      padding: 30px; 
    }
    .box {
      background: white;
      padding: 20px;
      margin: 0 auto;
      max-width: 400px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    h2 { color: #333; }
    .pay-btn {
      display: inline-block;
      padding: 12px 25px;
      background: #4CAF50;
      color: #fff;
      font-size: 18px;
      text-decoration: none;
      border-radius: 8px;
      margin-top: 20px;
      transition: 0.3s;
    }
    .pay-btn:hover {
      background: #45a049;
    }









  </style>
</head>
<body>

  <div class="box">
    <h2>QR कोड स्कैन करें और भुगतान करें</h2>
    <p><strong>राशि:</strong> ₹799</p>
    <a href="https://ibb.co/bgVHLtmk"><img src="https://i.ibb.co/cc9btq3j/2222.jpg" alt="2222" border="0"></a>
    <p>UPI (GPay, PhonePe, Paytm) </p>
    <p><strong>UPI ID:</strong> <span style="color:green;">1848ashish@fam</span></p>

    <br>

    <div class="payment-options">
      <h3>भुगतान का तरीका चुनें:</h3>
      <label>
        <input type="radio" name="paymentMethod" value="online" checked> ऑनलाइन पेमेंट
      </label>
      <label>
        <input type="radio" name="paymentMethod" value="cod"> कैश ऑन डिलीवरी (COD)
      </label>

      <div id="codNote">
        <strong>नोट:</strong> कैश ऑन डिलीवरी पर <span style="color:red;">20%</span> एडवांस पेमेंट अनिवार्य है।
      </div>
    </div>

    <br>







<div class="box">
    <h2>UPI से भुगतान करें</h2>
    <p>भुगतान करने के लिए नीचे दिए गए बटन पर क्लिक करें:</p>
    
    <!-- यहां अपना असली UPI ID और राशि डालें -->
    <a class="pay-btn" 
       href="upi://pay?pa=1848ashish@fam=Ashish%20Rajput&am=100&cu=INR">
       ₹159 भुगतान करें
    </a>
  </div>




   

  <script>
    // LocalStorage से यूज़र की जानकारी पढ़ना
    const user = JSON.parse(localStorage.getItem("userData"));
    if (user) {
      document.getElementById("userDetails").innerHTML = `
        <hr>
        <h3>आपकी जानकारी:</h3>
        <p><strong>नाम:</strong> ${user.name}</p>
        <p><strong>फोन:</strong> ${user.phone}</p>
        <p><strong>प्रोफेशन:</strong> ${user.profession}</p>
        <p><strong>पता:</strong> ${user.address}</p>
      `;
    }

    // COD Note Toggle
    const paymentRadios = document.getElementsByName("paymentMethod");
    const codNote = document.getElementById("codNote");

    for (let radio of paymentRadios) {
      radio.addEventListener("change", function () {
        if (this.value === "cod") {
          codNote.style.display = "block";
        } else {
          codNote.style.display = "none";
        }
      });
    }

    function confirmPayment() {
      document.getElementById("successMsg").style.display = "block";
      console.log("User Data Sent:", user);
      // Redirect example:
      // setTimeout(() => { window.location.href = "thankyou.html"; }, 3000);
    }
  </script>

</body>
</html>
