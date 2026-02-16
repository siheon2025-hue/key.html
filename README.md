<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>키 발급 사이트</title>
</head>
<body>
  <h1>안녕하세요! 키 발급 페이지</h1>
  <p>여기에 회원가입, 인증, PayPal 결제, 키 발급 로직을 넣을 수 있습니다.</p>
  <div id="paypal-button-container"></div>
</body>
</html>
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>키 발급 사이트</title>
</head>
<body>
  <h1>키 발급 페이지</h1>
  <button id="getKeyBtn">키 발급받기</button>
  <p id="keyDisplay"></p>

  <script>
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
  </script>
</body>
</html>
