<!DOCTYPE html>
<html lang="fa">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title> Game sxs</title>
<style>
/* ================== پایه ================== */
body{
  margin:0;
  font-family:Tahoma,sans-serif;
  background: linear-gradient(120deg,#0b0c1c,#1a1a2e);
  color:#fff;
  text-align:center;
  overflow-x:hidden;
}
header{
  padding:20px;
  font-size:28px;
  font-weight:bold;
  text-shadow:0 0 10px #0ff;
}

/* ================== Top Box ================== */
.top-box{
  width:100%;
  height:250px; /* برای موبایل بهینه شد */
  background:url("https://cdn.jsdelivr.net/gh/SHAKI0010/apk-files-shaki@main/5936243320109599784.jpg") center top/cover no-repeat;
  border-bottom:3px solid #0ff;
  position:relative;
  overflow:hidden;
}

/* خطوط نور متحرک */
.top-box::before{
  content:'';
  position:absolute;
  top:0; left:0;
  width:100%; height:100%;
  background:linear-gradient(90deg, rgba(0,255,255,0.1) 0%, rgba(255,0,255,0.1) 50%, rgba(0,255,0,0.1) 100%);
  animation: lightMove 6s linear infinite;
}
@keyframes lightMove{
  0%{transform:translateX(-100%);}
  100%{transform:translateX(100%);}
}

/* ================== مراحل ================== */
.step{
  display:none;
  padding:25px 15px;
  opacity:0;
  transform:translateY(30px);
  transition: all 0.6s ease;
}
.step.active{
  display:block;
  opacity:1;
  transform:translateY(0);
}

/* عنوان مرحله */
h2{
  margin-bottom:25px;
  text-shadow:0 0 15px #0ff;
}

/* ================== گزینه‌ها ================== */
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
  font-size:20px;
  border-radius:16px;
  cursor:pointer;
  border:2px solid #334155;
  color:#fff;
  background:linear-gradient(135deg,#111827,#1f2937);
  animation: rainbowNeon 4s linear infinite;
  transition:0.3s;
}
.option:hover{
  transform:scale(1.1);
  box-shadow:0 0 20px #0ff,0 0 40px #0ff;
}
.option.selected{
  background:#0ff;
  color:#000;
  box-shadow:0 0 30px #0ff,0 0 60px #0ff;
}

/* نئون متحرک گزینه‌ها */
@keyframes rainbowNeon{
  0%{border-color:#ff0000; box-shadow:0 0 5px #ff0000;}
  16%{border-color:#ff8800; box-shadow:0 0 10px #ff8800;}
  33%{border-color:#ffff00; box-shadow:0 0 15px #ffff00;}
  50%{border-color:#00ff00; box-shadow:0 0 20px #00ff00;}
  66%{border-color:#00ffff; box-shadow:0 0 25px #00ffff;}
  83%{border-color:#0000ff; box-shadow:0 0 30px #0000ff;}
  100%{border-color:#ff00ff; box-shadow:0 0 35px #ff00ff;}
}

/* ================== دکمه ادامه ================== */
button{
  margin-top:25px;
  padding:16px 50px;
  font-size:20px;
  border:none;
  border-radius:12px;
  cursor:pointer;
  display:none;
  color:#fff;
  background: linear-gradient(135deg,#ff3c00,#ffdd00,#ff3c00);
  position:relative;
  overflow:hidden;
  box-shadow:0 0 15px #ff3c00,0 0 30px #ffdd00;
  transition:0.3s;
}
button.show{display:inline-block;}
button::before{
  content:'';
  position:absolute;
  top:-50%; left:-50%;
  width:200%; height:200%;
  background: radial-gradient(circle, rgba(255,140,0,0.5), rgba(255,0,0,0));
  animation: flame 1s linear infinite;
  z-index:-1;
}
button:hover{
  transform:scale(1.1);
  box-shadow:0 0 25px #ff3c00,0 0 50px #ffdd00;
}
@keyframes flame{
  0%{transform:translate(0,0) scale(1);}
  50%{transform:translate(10px,-10px) scale(1.1);}
  100%{transform:translate(0,0) scale(1);}
}

/* ================== اسلایدر سن ================== */
input[type=range]{
  -webkit-appearance:none;
  width:90%;
  max-width:280px;
  height:14px;
  border-radius:7px;
  background:#334155;
  outline:none;
  margin:20px 0;
}
input[type=range]::-webkit-slider-thumb{
  -webkit-appearance:none;
  width:40px; height:40px; border-radius:50%;
  background:#0ff;
  cursor:pointer;
  box-shadow:0 0 20px #0ff;
}
input[type=range]:active::-webkit-slider-thumb{transform:scale(1.2);}
input[type=range]::-moz-range-thumb{
  width:40px;height:40px;border-radius:50%;
  background:#0ff;
  cursor:pointer;
  box-shadow:0 0 20px #0ff;
}
#ageDisplay{
  font-size:26px;
  font-weight:bold;
  margin-top:10px;
  animation: rainbowNeonText 4s linear infinite;
}
@keyframes rainbowNeonText{
  0%{color:#ff0000; text-shadow:0 0 5px #ff0000;}
  16%{color:#ff8800; text-shadow:0 0 10px #ff8800;}
  33%{color:#ffff00; text-shadow:0 0 15px #ffff00;}
  50%{color:#00ff00; text-shadow:0 0 20px #00ff00;}
  66%{color:#00ffff; text-shadow:0 0 25px #00ffff;}
  83%{color:#0000ff; text-shadow:0 0 30px #0000ff;}
  100%{color:#ff00ff; text-shadow:0 0 35px #ff00ff;}
}

/* ================== دکمه دانلود ================== */
.download-btn{
  background:#38bdf8;
  color:#000;
  box-shadow:0 0 25px #38bdf8;
  display:inline-block;
  margin-top:30px;
  animation: btnGlow 1s infinite alternate;
}
@keyframes btnGlow{
  0%{ box-shadow:0 0 10px #22c55e;}
  50%{ box-shadow:0 0 25px #38bdf8;}
  100%{ box-shadow:0 0 40px #0ff;}
}

/* ================== ریسپانسیو موبایل ================== */
@media(max-width:480px){
  header{font-size:24px; padding:15px;}
  .option{width:70px;height:70px;line-height:70px;font-size:18px;}
  input[type=range]{width:95%;}
  #ageDisplay{font-size:22px;}
  .top-box{height:200px;}
  button{padding:14px 40px; font-size:18px;}
}
</style>
</head>
<body>

<header>🎮 Game sxs 🥵</header>
<div class="top-box"></div>

<!-- مرحله 1 -->
<div class="step active" id="step1">
<h2>1/5<br>سبک بازی خود را انتخاب کنید</h2>
<div class="options">
<div class="option" onclick="selectOption(this,1)">گی</div>
<div class="option" onclick="selectOption(this,1)">لزبین</div>
<div class="option" onclick="selectOption(this,1)">کلاسیک</div>
<div class="option" onclick="selectOption(this,1)">تریسام</div>
<div class="option" onclick="selectOption(this,1)">خشن</div>
<div class="option" onclick="selectOption(this,1)">ریلکس</div>
</div>
<button id="btn1" onclick="nextStep(2)">ادامه</button>
</div>

<!-- مرحله 2 -->
<div class="step" id="step2">
<h2>2/5<br>لطفا جنسیت خود را انتخاب کنید</h2>
<div class="options">
<div class="option" onclick="selectOption(this,2)">مرد</div>
<div class="option" onclick="selectOption(this,2)">زن</div>
</div>
<button id="btn2" onclick="nextStep(3)">ادامه</button>
</div>

<!-- مرحله 3 -->
<div class="step" id="step3">
<h2>3/5<br>سن خود را انتخاب کنید</h2>
<input type="range" id="age" min="16" max="70" value="25" oninput="updateAge(this.value)">
<div id="ageDisplay">25 سال</div>
<button id="btn3" onclick="nextStep(4)">ادامه</button>
</div>

<!-- مرحله 4 -->
<div class="step" id="step4">
<h2>4/5</h2>
<p>برای اجرای بازی، فایل بازی را دانلود کنید</p>
<button class="download-btn" onclick="downloadGame()">دانلود بازی</button>
</div>

<script>
function selectOption(el,step){
  document.querySelectorAll('#step'+step+' .option').forEach(o=>o.classList.remove('selected'));
  el.classList.add('selected');
  document.getElementById('btn'+step).classList.add('show');
}
function nextStep(step){
  const current=document.querySelector('.step.active');
  current.classList.remove('active');
  setTimeout(()=>{document.getElementById('step'+step).classList.add('active');},100);
}
function updateAge(val){
  document.getElementById('ageDisplay').innerText=val+" سال";
  if(val>=16 && val<=70){document.getElementById('btn3').classList.add('show');}
  else{document.getElementById('btn3').classList.remove('show');}
}
function downloadGame(){
  window.location.href="https://cdn.jsdelivr.net/gh/SHAKI0010/apk-files-shaki@main/Game_sxs_1.apk";
}
</script>

</body>
</html>
