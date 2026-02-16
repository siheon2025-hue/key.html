<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>키 발급 + 결제</title>
  <script src="https://www.paypal.com/sdk/js?client-id=YOUR_CLIENT_ID&currency=USD"></script>
</head>
<body>
  <h1>키 발급 페이지</h1>
  
  <!-- 키 발급 버튼 -->
  <button id="getKeyBtn">키 발급받기</button>
  <p id="keyDisplay"></p>

  <!-- PayPal 버튼 -->
  <div id="paypal-button-container"></div>

  <script>
    // 1️⃣ 키 발급 함수
    function generateKey() {
      const chars = "ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789";
      let key = "DELTA-";
      for (let i = 0; i < 8; i++) {
        key += chars.charAt(Math.floor(Math.random() * chars.length));
      }
      return key;
    }

    document.getElementById("getKeyBtn").onclick = function() {
      const key = generateKey();
      document.getElementById("keyDisplay").innerText = "발급된 키: " + key;
    }

    // 2️⃣ PayPal 버튼
    paypal.Buttons({
      createOrder: function(data, actions) {
        return actions.order.create({
          purchase_units: [{
            amount: { value: '5.00' } // 결제 금액
          }]
        });
      },
      onApprove: function(data, actions) {
        return actions.order.capture().then(function(details) {
          alert('결제가 완료되었습니다! ' + details.payer.name.given_name + '님');
        });
      }
    }).render('#paypal-button-container');
  </script>
</body>
</html>      }
      return key;
    }

    document.getElementById("getKeyBtn").onclick = function() {
      const key = generateKey();
      document.getElementById("keyDisplay").innerText = "발급된 키: " + key;
    }
  </script>
</body>
</html>
