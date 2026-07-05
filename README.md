# ilove
<!DOCTYPE html>
<html lang="ru">
<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">

<title>Для Миланы 🤍</title>

<link rel="stylesheet" href="style.css">

</head>

<body>

<!-- INTRO -->
<div id="intro">
    <div class="intro-content">
        <h1 class="intro-title">Для Миланы</h1>
        <p class="intro-subtitle">Любимой от любимого</p>
        <div class="intro-line"></div>
    </div>
</div>

<!-- PAGE 1 -->
<section class="page active" id="introPage">
    <div class="paper">
        <h1>Для моей любимой коти 🤍</h1>
        <button class="main-button" onclick="nextPage()">Открыть</button>
    </div>
</section>

<!-- TIMER -->
<section class="page">
    <div class="paper">
        <h2>Мы вместе</h2>
        <div class="timer">
            <div><h3 id="days">0</h3><span>дней</span></div>
            <div><h3 id="hours">00</h3><span>часов</span></div>
            <div><h3 id="minutes">00</h3><span>минут</span></div>
            <div><h3 id="seconds">00</h3><span>секунд</span></div>
        </div>
        <button class="main-button" onclick="nextPage()">Дальше</button>
    </div>
</section>

<!-- STORY -->
<section class="page">
    <div class="paper">
        <h2>Наша история</h2>
        <div id="gallery"></div>
    </div>
</section>

<!-- LETTER -->
<section class="page">
    <div class="paper">
        <h2>Письмо</h2>
        <div id="typedLetter"></div>
        <button class="main-button" onclick="nextPage()">Финал</button>
    </div>
</section>

<!-- FINAL -->
<section class="page">
    <div class="paper">
        <h1>Это только начало 🤍</h1>
        <p>Любимой от любимого</p>
    </div>
</section>

<div id="viewer">
    <img id="viewerImage">
    <button id="closeViewer">✕</button>
</div>

<script src="script.js"></script>
</body>
</html>
body{
margin:0;
font-family:sans-serif;
background:#f6f1e8;
color:#3b2f2a;
overflow-x:hidden;
}

.page{
min-height:100vh;
display:none;
justify-content:center;
align-items:center;
padding:40px;
}

.page.active{
display:flex;
}

.paper{
background:white;
padding:60px;
border-radius:25px;
max-width:900px;
width:100%;
box-shadow:0 20px 60px rgba(0,0,0,.1);
text-align:center;
}

.main-button{
margin-top:30px;
padding:15px 30px;
border:none;
border-radius:999px;
background:#a07c65;
color:white;
cursor:pointer;
}

.timer{
display:flex;
gap:20px;
justify-content:center;
margin-top:30px;
}

.timer h3{
font-size:40px;
margin:0;
}

#gallery img{
width:100%;
margin-top:20px;
border-radius:20px;
cursor:pointer;
}

#viewer{
position:fixed;
inset:0;
background:rgba(0,0,0,.8);
display:none;
justify-content:center;
align-items:center;
}

#viewer img{
max-width:90%;
max-height:90%;
}

#closeViewer{
position:absolute;
top:20px;
right:20px;
font-size:30px;
color:white;
background:none;
border:none;
}
let current=0;

const pages=document.querySelectorAll(".page");

function show(i){
pages.forEach(p=>p.classList.remove("active"));
pages[i].classList.add("active");
}

function nextPage(){
current++;
show(current);
}

/* TIMER */
const start=new Date("2025-08-01T00:36:00");

setInterval(()=>{
const now=new Date();
const d=now-start;

document.getElementById("days").textContent=Math.floor(d/86400000);
document.getElementById("hours").textContent=Math.floor(d/3600000%24);
document.getElementById("minutes").textContent=Math.floor(d/60000%60);
document.getElementById("seconds").textContent=Math.floor(d/1000%60);
},1000);

/* LETTER */
const text=`Дорогая Миланочка...
Я тебя очень люблю 🤍`;

let i=0;
setTimeout(()=>{
const el=document.getElementById("typedLetter");

function type(){
if(i<text.length){
el.textContent+=text[i++];
setTimeout(type,40);
}
}
type();
},2000);

/* PHOTOS */
const gallery=document.getElementById("gallery");

for(let i=1;i<=13;i++){
const img=document.createElement("img");
img.src=`photos/${i}.jpg`;
img.onclick=()=>{
document.getElementById("viewer").style.display="flex";
document.getElementById("viewerImage").src=img.src;
};
gallery.appendChild(img);
}

/* VIEWER */
document.getElementById("closeViewer").onclick=()=>{
document.getElementById("viewer").style.display="none";
};

