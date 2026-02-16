<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>광고 후 키 발급</title>
<style>
body {background:#111;color:white;text-align:center;font-family:Arial;}
button {padding:10px 20px;margin:10px;}
#keyDisplay {font-weight:bold;color:#0f0;margin-top:10px;}
</style>
</head>
<body>

<h1>광고 보기 후 키 발급</h1>

<video id="adVideo" width="400" controls></video>
<br>
<button id="playAdBtn">광고 재생</button>
<button id="getKeyBtn" disabled>키 발급</button>
<p id="keyDisplay"></p>

<script>
// 랜덤 광고
const ads = [
  "https://www.w3schools.com/html/mov_bbb.mp4",
  "https://interactive-examples.mdn.mozilla.net/media/cc0-videos/flower.mp4"
];
const video = document.getElementById("adVideo");
video.src = ads[Math.floor(Math.random()*ads.length)];

const playBtn = document.getElementById("playAdBtn");
const keyBtn = document.getElementById("getKeyBtn");
const keyDisplay = document.getElementById("keyDisplay");

// 광고 재생 버튼
playBtn.onclick = () => {
  video.play();
};

// 10초 후 키 버튼 활성화
video.addEventListener("timeupdate", () => {
  if(video.currentTime >= 10){
    keyBtn.disabled = false;
  }
});

// 키 발급
keyBtn.onclick = () => {
  const key = "DELTA-1234ABCD"; // Roblox와 동일
  keyDisplay.innerText = "발급된 키: " + key;
  navigator.clipboard.writeText(key);
  alert("키가 복사되었습니다!");
};
</script>

</body>
</html>
