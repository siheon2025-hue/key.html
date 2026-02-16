<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>랜덤 광고 후 키 발급</title>
  <style>
    body { font-family: Arial; padding: 20px; background:#111; color:white; text-align:center; }
    button { padding:10px 20px; margin-top:20px; }
    video { margin-top:20px; }
  </style>
</head>
<body>

<h1>광고 10초 시청 후 키 발급</h1>

<video id="adVideo" width="400" controls></video>

<br>
<button id="getKeyBtn" disabled>키 발급받기</button>
<p id="keyDisplay"></p>

<script>
const ads = [
  "https://www.w3schools.com/html/mov_bbb.mp4",
  "https://interactive-examples.mdn.mozilla.net/media/cc0-videos/flower.mp4"
];

const video = document.getElementById("adVideo");
const btn = document.getElementById("getKeyBtn");
const keyDisplay = document.getElementById("keyDisplay");

// 🎲 랜덤 광고 선택
video.src = ads[Math.floor(Math.random() * ads.length)];

video.addEventListener("timeupdate", () => {
  if(video.currentTime >= 10){
    btn.disabled = false;
  }
});

// 🔐 고정 키 (Roblox와 동일해야 함)
function generateKey(){
  return "DELTA-1234ABCD";
}

btn.onclick = () => {
  const key = generateKey();
  keyDisplay.innerText = "발급된 키: " + key;
  navigator.clipboard.writeText(key);
  alert("키가 복사되었습니다!");
};
</script>

</body>
</html>    const btn = document.getElementById('getKeyBtn');
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
