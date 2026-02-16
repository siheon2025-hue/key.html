<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>광고 후 키 발급</title>
  <style>
    body { font-family: Arial; padding: 20px; background-color: #f0f0f0; }
    button { padding: 10px 20px; margin-top: 20px; }
    #keyDisplay { font-weight: bold; color: #0070f0; margin-top: 10px; }
  </style>
</head>
<body>
  <h1>광고를 10초 이상 보면 키 발급!</h1>

  <!-- 광고 영역 -->
  <video id="adVideo" width="400" controls>
    <source src="https://www.w3schools.com/html/mov_bbb.mp4" type="video/mp4">
    브라우저가 video 태그를 지원하지 않습니다.
  </video>

  <!-- 키 발급 버튼 -->
  <button id="getKeyBtn" disabled>키 발급받기</button>
  <p id="keyDisplay"></p>

  <script>
    const video = document.getElementById('adVideo');
    const btn = document.getElementById('getKeyBtn');
    const keyDisplay = document.getElementById('keyDisplay');

    // 광고 10초 시청 후 버튼 활성화
    video.addEventListener('timeupdate', () => {
      if(video.currentTime >= 10){
        btn.disabled = false;
      }
    });

    // 랜덤 키 생성
    function generateKey() {
      const chars = "ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789";
      let key = "DELTA-";
      for(let i = 0; i < 8; i++){
        key += chars.charAt(Math.floor(Math.random() * chars.length));
      }
      return key;
    }

    // 키 발급 버튼 클릭
    btn.onclick = () => {
      const key = generateKey();
      keyDisplay.innerText = "발급된 키: " + key;
      navigator.clipboard.writeText(key); // 클립보드 복사
      alert("키가 발급되었습니다! Roblox에서 입력하세요.");

      // Roblox 서버 연동 시 예시 (서버 API 호출)
      // fetch("https://your-roblox-server.com/register_key", {
      //   method: "POST",
      //   headers: { 'Content-Type': 'application/json' },
      //   body: JSON.stringify({ key: key })
      // });
    }
  </script>
</body>
</html>
