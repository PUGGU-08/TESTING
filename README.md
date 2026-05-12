<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ALL HAIL</title>
<link href="https://fonts.googleapis.com/css2?family=Cinzel+Decorative:wght@700;900&family=Cinzel:wght@400;600&display=swap" rel="stylesheet">
<style>
* { margin: 0; padding: 0; box-sizing: border-box; }

body {
  background: #0a0408;
  min-height: 100vh;
  overflow-x: hidden;
  font-family: 'Cinzel', serif;
  color: #f5d96e;
}

#stars { position: fixed; inset: 0; z-index: 0; pointer-events: none; }

.floor {
  position: fixed;
  bottom: 0; left: 0; right: 0;
  height: 38%;
  background: linear-gradient(to top, #1a0e05 0%, #2a1508 60%, transparent 100%);
  z-index: 1;
}
.floor::before {
  content: '';
  position: absolute; inset: 0;
  background-image:
    repeating-linear-gradient(90deg, rgba(255,200,80,0.04) 0, rgba(255,200,80,0.04) 1px, transparent 1px, transparent 80px),
    repeating-linear-gradient(0deg,  rgba(255,200,80,0.04) 0, rgba(255,200,80,0.04) 1px, transparent 1px, transparent 60px);
}

.divine-rays {
  position: absolute;
  width: 600px; height: 600px;
  top: 50%; left: 50%;
  transform: translate(-50%, -50%);
  z-index: 2;
  animation: raysRotate 20s linear infinite;
}
.ray {
  position: absolute;
  top: 50%; left: 50%;
  width: 300px; height: 3px;
  transform-origin: left center;
  background: linear-gradient(to right, rgba(255,215,0,0.5), transparent);
  border-radius: 2px;
}
@keyframes raysRotate {
  from { transform: translate(-50%,-50%) rotate(0deg); }
  to   { transform: translate(-50%,-50%) rotate(360deg); }
}

.halo-glow {
  position: absolute;
  width: 420px; height: 420px;
  top: 50%; left: 50%;
  transform: translate(-50%, -50%);
  border-radius: 50%;
  background: radial-gradient(circle, rgba(255,200,60,0.22) 0%, rgba(255,160,0,0.1) 40%, transparent 70%);
  z-index: 3;
  animation: haloPulse 3s ease-in-out infinite;
}
@keyframes haloPulse {
  0%,100% { transform: translate(-50%,-50%) scale(1);    opacity: 0.8; }
  50%      { transform: translate(-50%,-50%) scale(1.12); opacity: 1; }
}

.scene {
  position: relative;
  min-height: 100vh;
  display: flex; align-items: center; justify-content: center;
  z-index: 5;
  padding: 80px 20px 40px;
}

.frame-wrap { position: relative; z-index: 10; }

.altar-base {
  width: 310px; height: 28px;
  background: linear-gradient(to bottom, #c8960c, #7a5800);
  border-radius: 4px 4px 0 0;
  margin: 0 auto;
  box-shadow: 0 6px 30px rgba(255,180,0,0.3);
  position: relative;
}
.altar-base::before {
  content: '\2736 \2736 \2736';
  position: absolute; top: 50%; left: 50%;
  transform: translate(-50%,-50%);
  color: #ffe88a; font-size: 11px; letter-spacing: 6px;
}

.picture-frame {
  background: #1c0d00;
  border: 6px solid #c8960c;
  outline: 2px solid #7a5800;
  padding: 14px;
  position: relative;
  box-shadow:
    0 0 0 1px #7a5800,
    0 0 40px rgba(255,180,0,0.45),
    0 0 90px rgba(255,140,0,0.2),
    inset 0 0 20px rgba(255,180,0,0.08);
}
.picture-frame::before, .picture-frame::after {
  font-size: 20px; position: absolute; color: #c8960c; line-height: 1;
}
.picture-frame::before { content: '\2736'; top: 4px; left: 6px; }
.picture-frame::after  { content: '\2736'; top: 4px; right: 6px; }
.corner-bl { position: absolute; bottom: 4px; left: 6px;  font-size: 20px; color: #c8960c; }
.corner-br { position: absolute; bottom: 4px; right: 6px; font-size: 20px; color: #c8960c; }

.picture-inner {
  width: 260px; height: 220px;
  background: #120800;
  position: relative;
  display: flex; align-items: center; justify-content: center;
  overflow: hidden;
}
.picture-inner::after {
  content: '';
  position: absolute; inset: 0;
  background: radial-gradient(circle at 50% 40%, rgba(255,200,60,0.12), transparent 70%);
  pointer-events: none; z-index: 3;
  animation: shimmerPulse 2.5s ease-in-out infinite;
}
@keyframes shimmerPulse {
  0%,100% { opacity: 0.7; } 50% { opacity: 1; }
}

.photo-placeholder {
  font-size: 72px; z-index: 2; position: relative;
  filter: drop-shadow(0 0 18px rgba(255,200,0,0.8));
  animation: photoFloat 4s ease-in-out infinite;
}
@keyframes photoFloat {
  0%,100% { transform: translateY(0) scale(1); }
  50%      { transform: translateY(-8px) scale(1.04); }
}

.halo-ring {
  position: absolute; top: -44px; left: 50%; transform: translateX(-50%);
  width: 90px; height: 26px;
  border: 4px solid #f5d96e; border-radius: 50%;
  box-shadow: 0 0 14px rgba(245,217,110,0.8), 0 0 30px rgba(245,217,110,0.4);
  animation: haloRingPulse 2s ease-in-out infinite;
}
@keyframes haloRingPulse {
  0%,100% { box-shadow: 0 0 14px rgba(245,217,110,0.8), 0 0 30px rgba(245,217,110,0.4); }
  50%      { box-shadow: 0 0 24px rgba(245,217,110,1),   0 0 60px rgba(245,217,110,0.7); }
}

.worshipper {
  position: absolute; bottom: -30px; font-size: 64px;
  filter: drop-shadow(0 0 12px rgba(255,180,0,0.5));
}
.w-left  { left: -200px;  animation: bowLeft  2.5s ease-in-out infinite; transform-origin: bottom center; }
.w-left2 { left: -320px;  font-size: 50px; animation: bowLeft 3s ease-in-out infinite; animation-delay: 0.4s; }
.w-right { right: -200px; animation: bowRight 2.5s ease-in-out infinite; transform-origin: bottom center; }
.w-right2{ right: -320px; font-size: 50px; animation: bowRight 3s ease-in-out infinite; animation-delay: 0.4s; }

@keyframes bowLeft {
  0%,100% { transform: rotate(-5deg)  translateY(0); }
  50%      { transform: rotate(-35deg) translateY(10px); }
}
@keyframes bowRight {
  0%,100% { transform: rotate(5deg)  translateY(0)   scaleX(-1); }
  50%      { transform: rotate(35deg) translateY(10px) scaleX(-1); }
}

.candle-wrap {
  position: absolute; bottom: -50px;
  display: flex; flex-direction: column; align-items: center;
}
.candle-wrap.c-l1 { left: -100px; }
.candle-wrap.c-l2 { left: -60px; }
.candle-wrap.c-r1 { right: -100px; }
.candle-wrap.c-r2 { right: -60px; }

.flame {
  width: 12px; height: 20px;
  background: radial-gradient(ellipse at 50% 80%, #fff 10%, #ffd700 40%, #ff8c00 70%, transparent 100%);
  border-radius: 50% 50% 30% 30%;
  animation: flameFlicker 0.5s ease-in-out infinite;
  box-shadow: 0 0 10px 4px rgba(255,180,0,0.4);
  margin-bottom: 1px;
}
@keyframes flameFlicker {
  0%,100% { transform: scaleX(1)    scaleY(1)    translateX(0); }
  25%      { transform: scaleX(0.85) scaleY(1.1)  translateX(1px); }
  75%      { transform: scaleX(1.1)  scaleY(0.95) translateX(-1px); }
}
.candle-body {
  width: 14px; height: 55px;
  background: linear-gradient(to right, #e8e0c8, #fffef0, #d4cba8);
  border-radius: 2px 2px 0 0;
  box-shadow: 0 0 8px rgba(255,180,0,0.2);
  position: relative;
}
.candle-body::after {
  content: ''; position: absolute; top: 0; left: 0; right: 0; height: 8px;
  background: linear-gradient(to bottom, #c8b86a, #e8d890);
  border-radius: 2px 2px 0 0;
}

.offering {
  position: fixed; font-size: 28px;
  pointer-events: none; z-index: 20;
  animation: offeringFloat 5s ease-in-out infinite;
  filter: drop-shadow(0 0 8px rgba(255,200,0,0.6));
}
.of1 { top: 20%; left: 6%;   animation-delay: 0s;   font-size: 32px; }
.of2 { top: 30%; right: 7%;  animation-delay: 0.8s; }
.of3 { top: 60%; left: 4%;   animation-delay: 1.6s; font-size: 24px; }
.of4 { top: 65%; right: 5%;  animation-delay: 2.4s; font-size: 34px; }
.of5 { top: 15%; right: 15%; animation-delay: 1.2s; font-size: 22px; }
.of6 { top: 75%; left: 15%;  animation-delay: 0.5s; font-size: 26px; }
@keyframes offeringFloat {
  0%,100% { transform: translateY(0)    rotate(-6deg); }
  50%      { transform: translateY(-18px) rotate(6deg); }
}

.title-wrap {
  position: fixed; top: 0; left: 0; right: 0;
  z-index: 30; text-align: center;
  padding: 18px 0 12px;
  background: linear-gradient(to bottom, rgba(10,4,8,0.95), transparent);
}
.title-main {
  font-family: 'Cinzel Decorative', serif;
  font-size: 42px; font-weight: 900;
  color: #f5d96e; letter-spacing: 10px;
  text-shadow: 0 0 10px rgba(255,200,60,0.9), 0 0 30px rgba(255,160,0,0.5), 0 0 60px rgba(255,120,0,0.3);
  animation: titleGlow 3s ease-in-out infinite;
}
.title-sub {
  font-family: 'Cinzel', serif;
  font-size: 13px; color: #b8902a; letter-spacing: 8px; margin-top: 4px;
}
@keyframes titleGlow {
  0%,100% { text-shadow: 0 0 10px rgba(255,200,60,0.9), 0 0 30px rgba(255,160,0,0.5); }
  50%      { text-shadow: 0 0 20px rgba(255,220,80,1),   0 0 60px rgba(255,180,0,0.9), 0 0 100px rgba(255,120,0,0.5); }
}

.ticker {
  position: fixed; bottom: 0; left: 0; right: 0;
  background: rgba(10,4,8,0.9);
  border-top: 1px solid #7a5800;
  padding: 10px 0; overflow: hidden; z-index: 30;
}
.ticker-inner {
  display: inline-block; white-space: nowrap;
  animation: tickerScroll 24s linear infinite;
  font-size: 14px; color: #c8960c; letter-spacing: 4px;
}
@keyframes tickerScroll {
  from { transform: translateX(100vw); }
  to   { transform: translateX(-100%); }
}

.prayer {
  position: absolute;
  background: rgba(20,10,0,0.85);
  border: 1.5px solid #7a5800; border-radius: 10px;
  padding: 7px 14px; font-size: 13px; color: #f5d96e;
  letter-spacing: 1px; white-space: nowrap;
  animation: prayerPulse 3s ease-in-out infinite;
}
.pr-l1 { bottom: 30px; left: -240px; animation-delay: 0s; }
.pr-l2 { bottom: 70px; left: -210px; animation-delay: 1s;   font-size: 11px; }
.pr-r1 { bottom: 30px; right: -240px; animation-delay: 0.5s; }
.pr-r2 { bottom: 70px; right: -210px; animation-delay: 1.5s; font-size: 11px; }
@keyframes prayerPulse {
  0%,100% { opacity: 0.7; } 50% { opacity: 1; }
}

#particles { position: fixed; inset: 0; pointer-events: none; z-index: 4; }
</style>
</head>
<body>

<canvas id="stars"></canvas>
<canvas id="particles"></canvas>
<div class="floor"></div>

<div class="title-wrap">
  <div class="title-main">PUGGU</div>
  <div class="title-sub">bow before the PUGGU</div>
</div>

<div class="offering of1">&#128081;</div>
<div class="offering of2">&#11088;</div>
<div class="offering of3">&#128142;</div>
<div class="offering of4">&#129689;</div>
<div class="offering of5">&#10024;</div>
<div class="offering of6">&#127802;</div>

<div class="scene">
  <div class="frame-wrap">

    <div class="divine-rays" id="rays"></div>
    <div class="halo-glow"></div>

    <div class="worshipper w-left2">&#129494;</div>
    <div class="worshipper w-left">&#129494;</div>
    <div class="worshipper w-right">&#129494;</div>
    <div class="worshipper w-right2">&#129494;</div>

    <div class="candle-wrap c-l2"><div class="flame"></div><div class="candle-body"></div></div>
    <div class="candle-wrap c-l1"><div class="flame"></div><div class="candle-body" style="height:70px"></div></div>
    <div class="candle-wrap c-r1"><div class="flame"></div><div class="candle-body" style="height:70px"></div></div>
    <div class="candle-wrap c-r2"><div class="flame"></div><div class="candle-body"></div></div>

    <div class="prayer pr-l1">WE ARE NOT WORTHY</div>
    <div class="prayer pr-l2">&#10022; GET BLESSINGS &#10022;</div>
    <div class="prayer pr-r1">THE GOD PUGGU</div>
    <div class="prayer pr-r2">&#10022; ALL HAIL &#10022;</div>

    <div class="picture-frame">
      <div class="halo-ring"></div>
      <span class="corner-bl">&#10022;</span>
      <span class="corner-br">&#10022;</span>
      <div class="picture-inner">
        <img src="PUGGUA.jpg" style="width:100%;height:100%;object-fit:cover;position:relative;z-index:2;">
      </div>
    </div>
    <div class="altar-base"></div>

  </div>
</div>

<div class="ticker">
  <span class="ticker-inner">
    &#10022; &nbsp; GLORY TO THE PUGGU &nbsp; &#10022; &nbsp; MAY THEIR LIGHT SHINE ETERNAL &nbsp; &#10022; &nbsp; PUGGU THE GOD OF PUGGISM &nbsp; &#10022; &nbsp; THE ONE ABOVE ALL &nbsp; &#10022; &nbsp; THE LEGEND WALKS AMONG US &nbsp; &#10022; &nbsp; ALL KINGDOMS BOW &nbsp; &#10022; &nbsp; GET BLESSED BY PUGGU &nbsp; &#10022; &nbsp;
  </span>
</div>

<script>
// Star field
const sc = document.getElementById('stars');
const sx = sc.getContext('2d');
sc.width = window.innerWidth; sc.height = window.innerHeight;
const stars = Array.from({length:200}, () => ({
  x: Math.random()*sc.width, y: Math.random()*sc.height,
  r: Math.random()*1.5+0.3, a: Math.random(), sp: Math.random()*0.008+0.003
}));
function drawStars() {
  sx.clearRect(0,0,sc.width,sc.height);
  stars.forEach(s => {
    s.a += s.sp;
    if(s.a>1||s.a<0) s.sp=-s.sp;
    sx.beginPath(); sx.arc(s.x,s.y,s.r,0,Math.PI*2);
    sx.fillStyle=`rgba(255,220,120,${s.a*0.9})`; sx.fill();
  });
  requestAnimationFrame(drawStars);
}
drawStars();

// Ray lines
const raysEl = document.getElementById('rays');
for(let i=0;i<24;i++){
  const r=document.createElement('div');
  r.className='ray';
  r.style.transform=`rotate(${i*15}deg)`;
  r.style.opacity=i%2===0?'0.6':'0.3';
  r.style.height=i%3===0?'5px':'2px';
  raysEl.appendChild(r);
}

// Gold particles
const pc = document.getElementById('particles');
const px = pc.getContext('2d');
pc.width=window.innerWidth; pc.height=window.innerHeight;
const parts = Array.from({length:60}, ()=>({
  x: Math.random()*pc.width, y: pc.height+Math.random()*200,
  vy: -(Math.random()*0.6+0.2), vx: (Math.random()-0.5)*0.4,
  r: Math.random()*2.5+0.5, a: Math.random()
}));
function drawParts(){
  px.clearRect(0,0,pc.width,pc.height);
  parts.forEach(p=>{
    p.y+=p.vy; p.x+=p.vx; p.a-=0.003;
    if(p.y<-10||p.a<=0){ p.y=pc.height+10; p.x=Math.random()*pc.width; p.a=Math.random()*0.7+0.3; }
    px.beginPath(); px.arc(p.x,p.y,p.r,0,Math.PI*2);
    px.fillStyle=`rgba(255,210,60,${p.a})`; px.fill();
  });
  requestAnimationFrame(drawParts);
}
drawParts();

window.addEventListener('resize',()=>{
  sc.width=pc.width=window.innerWidth;
  sc.height=pc.height=window.innerHeight;
});

// Audio
const audio = new Audio('hail.mp3');
audio.loop=true; audio.volume=0.4;
audio.play().catch(()=>{
  const toast=document.createElement('div');
  toast.textContent='&#128276; Click anywhere to hear the hymn';
  toast.style.cssText=`position:fixed;bottom:50px;left:50%;transform:translateX(-50%);
    background:rgba(20,10,0,0.95);color:#f5d96e;font-family:'Cinzel',serif;font-size:16px;
    padding:12px 28px;border-radius:4px;border:1px solid #7a5800;z-index:9999;letter-spacing:2px;
    box-shadow:0 0 20px rgba(255,180,0,0.3);`;
  document.body.appendChild(toast);
  const unlock=()=>{ audio.play(); toast.remove(); document.removeEventListener('click',unlock); };
  document.addEventListener('click',unlock);
});

// Divine sparks
function spawnSpark(){
  const el=document.createElement('div');
  const items=['\u2736','\u2605','\u2727','\u2B50','\uD83C\uDF1F','\uD83D\uDC51','\u2728'];
  el.textContent=items[Math.floor(Math.random()*items.length)];
  const vw=window.innerWidth, vh=window.innerHeight;
  el.style.cssText=`position:fixed;left:${vw/2-60+Math.random()*120}px;top:${vh/2-40+Math.random()*80}px;
    font-size:${14+Math.random()*18}px;color:#f5d96e;pointer-events:none;z-index:100;opacity:1;
    text-shadow:0 0 12px rgba(255,200,60,0.9);`;
  document.body.appendChild(el);
  const angle=Math.random()*Math.PI*2, dist=120+Math.random()*180;
  const tx=Math.cos(angle)*dist, ty=Math.sin(angle)*dist-60;
  let start=null;
  function step(ts){
    if(!start) start=ts;
    const p=Math.min((ts-start)/1400,1);
    el.style.transform=`translate(${tx*p}px,${ty*p}px)`;
    el.style.opacity=1-p;
    if(p<1) requestAnimationFrame(step); else el.remove();
  }
  requestAnimationFrame(step);
}
setInterval(spawnSpark,500);
</script>
</body>
</html>
