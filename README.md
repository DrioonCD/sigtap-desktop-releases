<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SIGTAP Versionador — Mockup v2</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Manrope:wght@400;500;600;700;800&family=IBM+Plex+Mono:wght@400;500;600;700&display=swap');
 
:root{
  --bg: #F6F9FD;
  --bg-soft: #EEF4FC;
  --card: #FFFFFF;
  --ink: #16202C;
  --ink-soft: #64707D;
  --blue: #1D63E0;
  --blue-dark: #123F94;
  --blue-tint: #E7F0FD;
  --green: #1B8A4B;
  --green-tint: #DDF3E3;
  --amber: #C97A1A;
  --amber-tint: #FCEBD2;
  --violet: #6D4CF0;
  --teal: #0E9C93;
  --navy-bar: #12161F;
  --border: rgba(18,32,54,0.09);
  --shadow: 0 24px 55px -22px rgba(18,63,148,0.28);
  --shadow-lg: 0 34px 80px -24px rgba(18,63,148,0.38);
}
 
*{ box-sizing:border-box; margin:0; padding:0; }
html{ scroll-behavior:smooth; }
body{
  background: var(--bg);
  color: var(--ink);
  font-family: 'Manrope', sans-serif;
  line-height: 1.55;
  -webkit-font-smoothing: antialiased;
  overflow-x: hidden;
}
 
.wrap{ max-width: 1160px; margin:0 auto; padding: 0 32px; position: relative; z-index: 2;}
 
/* ambient blobs */
.blob{ position: fixed; border-radius: 50%; filter: blur(70px); opacity: 0.35; z-index: 0; pointer-events:none; }
.blob1{ width: 480px; height:480px; background: var(--blue-tint); top: -160px; right: -120px; }
.blob2{ width: 420px; height:420px; background: var(--green-tint); bottom: 10%; left: -160px; }
.blob3{ width: 360px; height:360px; background: var(--amber-tint); top: 60%; right: 8%; opacity:0.25; }
 
/* ---------- TOP TAB BAR ---------- */
.tabbar{ position: sticky; top:0; z-index: 50; background: rgba(246,249,253,0.82); backdrop-filter: blur(10px); border-bottom: 1px solid var(--border); }
.tabbar .wrap{ display:flex; align-items:center; justify-content:space-between; height: 66px; }
.brand{ display:flex; align-items:center; gap:10px; font-weight:700; font-size:15px; }
.brand .mark{ width:26px; height:26px; border-radius:7px; background: var(--blue); display:flex; align-items:center; justify-content:center; color:#fff; font-size:15px; font-weight:800; box-shadow: 0 6px 14px -4px rgba(29,99,224,0.55); }
.tabs{ display:flex; gap: 30px; }
.tabs a{ font-size: 13.5px; font-weight:600; color: var(--ink-soft); text-decoration:none; transition: color .2s ease; }
.tabs a:hover{ color: var(--blue); }
@media (max-width: 720px){ .tabs{ display:none; } }
 
/* ---------- HERO ---------- */
.hero{ padding: 84px 0 60px; position:relative; }
.hero .wrap{ display:grid; grid-template-columns: 0.95fr 1.15fr; gap: 40px; align-items:center; }
@media (max-width: 980px){ .hero .wrap{ grid-template-columns: 1fr; } }
 
.eyebrow{ display:inline-flex; align-items:center; gap:8px; background: var(--blue-tint); color: var(--blue-dark);
  font-family:'IBM Plex Mono'; font-size: 11.5px; font-weight:600; letter-spacing:0.06em; text-transform:uppercase;
  padding: 7px 13px; border-radius: 100px; margin-bottom: 22px; }
.eyebrow .dot{ width:6px; height:6px; border-radius:50%; background: var(--green); animation: pulse 2s infinite; }
@keyframes pulse{ 0%,100%{ opacity:1; } 50%{ opacity:.35; } }
 
h1.title{ font-weight:800; font-size: clamp(34px, 4.4vw, 52px); line-height: 1.08; letter-spacing:-0.02em; color: var(--ink); margin-bottom: 18px; }
h1.title .accent{ color: var(--blue); }
 
.lede{ font-size: 17px; color: var(--ink-soft); max-width: 46ch; margin-bottom: 30px; }
.lede strong{ color: var(--ink); font-weight:700; }
 
.pill-row{ display:flex; gap:10px; flex-wrap:wrap; margin-bottom: 32px; }
.pill{ font-family:'IBM Plex Mono'; font-size:11.5px; font-weight:600; letter-spacing:0.03em; padding: 8px 13px; border-radius: 100px; }
.pill.blue{ background: var(--blue-tint); color: var(--blue-dark); }
.pill.green{ background: var(--green-tint); color: var(--green); }
.pill.violet{ background: #EFE9FE; color: var(--violet); }
 
.cta-row{ display:flex; gap:14px; align-items:center; flex-wrap:wrap; }
.btn-primary{ font-weight:700; font-size:14.5px; background: var(--blue); color:#fff; text-decoration:none;
  padding: 14px 24px; border-radius: 10px; box-shadow: var(--shadow); display:inline-flex; align-items:center; gap:9px;
  transition: transform .2s ease, box-shadow .2s ease; }
.btn-primary:hover{ transform: translateY(-2px); box-shadow: var(--shadow-lg); }
.btn-ghost{ font-weight:600; font-size:14px; color: var(--ink-soft); text-decoration:none; border-bottom: 1.5px solid var(--border); padding-bottom:2px; }
 
/* ---------- HERO PRODUCT MOCKUP (parallax) ---------- */
.stage{ position:relative; height: 460px; perspective: 1400px; }
.tilt{ position:absolute; inset:0; transform-style: preserve-3d; transition: transform .15s ease-out; }
 
.appwin{ position:absolute; top:10px; left:0; width: 92%; background: var(--card); border-radius: 14px;
  box-shadow: var(--shadow-lg); overflow:hidden; border: 1px solid var(--border); transform: translateZ(0); }
.win-bar{ background: var(--navy-bar); height: 34px; display:flex; align-items:center; justify-content:space-between; padding: 0 12px; }
.win-bar .l{ display:flex; align-items:center; gap:7px; color:#c9d3e0; font-size:11px; font-weight:600; }
.win-bar .l .sq{ width:14px; height:14px; border-radius:4px; background: var(--blue); }
.win-bar .r{ display:flex; gap:8px; }
.win-bar .r span{ width:9px; height:9px; border-radius:2px; border:1.4px solid #4b5566; }
.win-body{ display:flex; height: 300px; }
.win-side{ width: 30%; background: var(--card); border-right:1px solid var(--border); padding: 14px 12px; font-size:10px; }
.win-side .grp{ font-family:'IBM Plex Mono'; font-size:8.5px; color:#9aa4b1; letter-spacing:0.06em; margin: 10px 0 6px; }
.win-side .item{ padding:6px 8px; border-radius:6px; color: var(--ink-soft); font-weight:600; margin-bottom:3px; }
.win-side .item.active{ background: var(--blue-tint); color: var(--blue-dark); }
.win-main{ flex:1; background: var(--bg-soft); padding: 14px 16px; }
.win-search{ background:#fff; border:1px solid var(--border); border-radius:8px; height:28px; margin-bottom:12px; display:flex; align-items:center; padding:0 10px; gap:6px; color:#a7b0bc; font-size:10px; }
.win-grid{ display:grid; grid-template-columns: 1.3fr 1fr 1fr; gap:10px; }
.win-card{ background:#fff; border:1px solid var(--border); border-radius:10px; padding: 12px; }
.win-card.hi{ background: var(--blue-tint); grid-row: span 2; display:flex; flex-direction:column; justify-content:space-between; }
.win-card .num{ font-weight:800; font-size:20px; color: var(--ink); font-family:'IBM Plex Mono'; }
.win-card.hi .num{ font-size: 26px; }
.win-card .lbl{ font-size: 9.5px; color: var(--ink-soft); margin-top:2px; }
.win-card .mini-btn{ margin-top:8px; background: var(--blue); color:#fff; font-size:9.5px; font-weight:700; padding:6px 10px; border-radius:6px; display:inline-block; width:fit-content; }
.win-card .ic{ width:16px; height:16px; border-radius:5px; margin-bottom:6px; }
.win-card .ic.teal{ background: var(--teal); }
.win-card .ic.violet{ background: var(--violet); }
 
/* floating chips (parallax layers) */
.chip{ position:absolute; background: var(--card); border-radius: 12px; box-shadow: var(--shadow); border:1px solid var(--border);
  padding: 12px 16px; display:flex; align-items:center; gap:10px; transform: translateZ(60px); }
.chip .dotcol{ width:34px; height:34px; border-radius:9px; display:flex; align-items:center; justify-content:center; font-family:'IBM Plex Mono'; font-weight:700; font-size:11px; }
.chip .num{ font-family:'IBM Plex Mono'; font-weight:800; font-size: 17px; line-height:1; }
.chip .lbl{ font-size: 10.5px; color: var(--ink-soft); }
.chip1{ top: -6px; right: -14px; animation: floaty 5s ease-in-out infinite; }
.chip1 .dotcol{ background: var(--green-tint); color: var(--green); }
.chip2{ bottom: 26px; right: 24px; animation: floaty 6.5s ease-in-out infinite 0.6s; transform: translateZ(90px); }
.chip2 .dotcol{ background: #EFE9FE; color: var(--violet); }
.chip3{ bottom: -18px; left: 40%; animation: floaty 5.6s ease-in-out infinite 1.1s; transform: translateZ(40px); }
.chip3 .dotcol{ background: var(--amber-tint); color: var(--amber); }
@keyframes floaty{ 0%,100%{ transform: translateY(0) translateZ(60px);} 50%{ transform: translateY(-10px) translateZ(60px);} }
 
@media (max-width: 980px){ .stage{ height: 340px; } .appwin{ width:100%; } .chip{ display:none; } }
 
/* ---------- SECTIONS ---------- */
section{ padding: 66px 0; border-top: 1px solid var(--border); }
.sec-head{ display:flex; align-items:baseline; gap: 14px; margin-bottom: 32px; }
.sec-num{ font-family:'IBM Plex Mono'; font-size: 12.5px; color: var(--blue); font-weight:700; }
h2{ font-weight:800; font-size: 27px; color: var(--ink); letter-spacing:-0.01em; }
 
.reveal{ opacity:0; transform: translateY(26px); transition: opacity .7s cubic-bezier(.2,.7,.3,1), transform .7s cubic-bezier(.2,.7,.3,1); }
.reveal.in{ opacity:1; transform:none; }
 
/* about */
.about-grid{ display:grid; grid-template-columns: 1.3fr 0.7fr; gap: 46px; align-items:center; }
@media (max-width: 800px){ .about-grid{ grid-template-columns:1fr; } }
.about-grid p{ color: var(--ink-soft); font-size: 16px; max-width: 56ch; }
.about-grid p + p{ margin-top: 13px; }
.folder{ background: var(--card); border: 1px solid var(--border); border-radius: 14px; padding: 26px 24px; box-shadow: var(--shadow); }
.folder .tag-top{ display:inline-block; background: var(--blue-tint); color: var(--blue-dark); font-family:'IBM Plex Mono'; font-size:10.5px; font-weight:700; padding: 5px 11px; border-radius:100px; margin-bottom:14px; }
.folder .big{ font-weight:700; font-size: 20px; color: var(--ink); }
.folder .foot{ margin-top:16px; display:flex; align-items:center; gap:8px; }
.folder .foot .d{ width:7px; height:7px; border-radius:50%; background: var(--green); }
.folder .foot span{ font-size:11.5px; color: var(--ink-soft); font-family:'IBM Plex Mono'; }
 
/* download cards */
.punch-grid{ display:grid; grid-template-columns: 1fr 1fr; gap: 24px; }
@media (max-width: 780px){ .punch-grid{ grid-template-columns:1fr; } }
.punch{ background: var(--card); border: 1px solid var(--border); border-radius: 14px; box-shadow: var(--shadow);
  padding: 26px 26px 28px; transition: transform .25s cubic-bezier(.2,.8,.3,1), box-shadow .25s ease; }
.punch:hover{ transform: translateY(-6px); box-shadow: var(--shadow-lg); }
.filename{ font-family:'IBM Plex Mono'; font-weight:700; font-size: 14.5px; color: var(--blue-dark); word-break: break-word; }
.punch p.desc{ color: var(--ink-soft); font-size: 14.5px; margin: 12px 0 18px; }
.tag{ display:inline-block; font-family:'IBM Plex Mono'; font-size: 10.5px; font-weight:700; letter-spacing:0.03em; padding: 5px 10px; border-radius: 100px; }
.tag.recommend{ background: var(--green-tint); color: var(--green); }
.tag.manual{ background: var(--amber-tint); color: var(--amber); }
 
/* update flow */
.flow{ display:flex; align-items:center; gap: 20px; flex-wrap:wrap; margin-bottom: 26px; }
.mini-card{ background: var(--card); border:1px solid var(--border); border-radius:12px; padding: 16px 18px; width: 176px; box-shadow: var(--shadow); }
.mini-card .v{ font-family:'IBM Plex Mono'; font-weight:700; font-size:15px; }
.mini-card .lbl{ font-family:'IBM Plex Mono'; font-size:10px; font-weight:700; margin-top:8px; padding:4px 9px; border-radius:100px; display:inline-block; }
.mini-card.old .lbl{ color: var(--amber); background: var(--amber-tint); }
.mini-card.new .lbl{ color: var(--green); background: var(--green-tint); }
.arrow{ color: var(--ink-soft); font-size: 20px; }
.note-row{ display:flex; gap:12px; align-items:flex-start; background: var(--bg-soft); border-left: 3px solid var(--blue); padding: 14px 18px; border-radius: 0 10px 10px 0; }
.note-row p{ font-size: 14px; color: var(--ink-soft); }
.note-row .ic{ font-family:'IBM Plex Mono'; font-weight:700; color:var(--blue); }
 
/* memo */
.memo{ background: var(--card); border:1px solid var(--border); border-radius:14px; padding: 30px 34px; box-shadow: var(--shadow); }
.memo p{ font-size: 15.5px; color: var(--ink); max-width: 68ch; }
.memo mark{ background: var(--blue-tint); color: var(--blue-dark); padding: 0 4px; border-radius:4px; font-weight:600; }
.memo .memo-head{ font-family:'IBM Plex Mono'; font-size:11px; color: var(--ink-soft); font-weight:600; text-transform:uppercase; letter-spacing:0.05em; margin-bottom:14px; }
 
/* footer */
footer{ padding: 56px 0 66px; text-align:center; }
.plate{ display:inline-flex; align-items:center; gap:10px; background: var(--navy-bar); color: #E7EDF6;
  font-size:13px; font-weight:600; padding: 13px 26px; border-radius: 100px; box-shadow: var(--shadow); }
.plate b{ color: #79B4FF; }
footer .sub{ margin-top: 14px; font-family:'IBM Plex Mono'; font-size: 10.5px; color: var(--ink-soft); letter-spacing:0.05em; }
</style>
</head>
<body>
 
<div class="blob blob1"></div>
<div class="blob blob2"></div>
<div class="blob blob3"></div>
 
<nav class="tabbar">
  <div class="wrap">
    <div class="brand"><span class="mark">+</span> Consulta de dados SIGTAP</div>
    <div class="tabs">
      <a href="#sobre">Sobre</a>
      <a href="#baixar">Download</a>
      <a href="#atualiza">Atualizações</a>
      <a href="#projeto">O projeto</a>
    </div>
  </div>
</nav>
 
<header class="hero">
  <div class="wrap">
    <div>
      <div class="eyebrow"><span class="dot"></span> Versionador · Releases oficiais</div>
      <h1 class="title">A tabela SIGTAP,<br>direto no seu <span class="accent">Dashboard.</span></h1>
      <p class="lede">Consulte procedimentos, CIDs, CBOs e valores do SUS local e offline, com <strong>dados oficiais do DATASUS</strong> sempre atualizados.</p>
      <div class="pill-row">
        <div class="pill blue">Windows</div>
        <div class="pill green">Uso pessoal</div>
        <div class="pill violet">JogaeStudio</div>
      </div>
      <div class="cta-row">
        <a class="btn-primary" href="#baixar">↓ Baixar versão mais recente</a>
        <a class="btn-ghost" href="#sobre">como funciona</a>
      </div>
    </div>
 
    <div class="stage" id="stage">
      <div class="tilt" id="tilt">
        <div class="appwin">
          <div class="win-bar">
            <div class="l"><span class="sq"></span> Consulta de dados SIGTAP</div>
            <div class="r"><span></span><span></span><span></span></div>
          </div>
          <div class="win-body">
            <div class="win-side">
              <div class="item active">▤ Dashboard</div>
              <div class="item" style="color:#a7b0bc;">▥ Competências</div>
              <div class="grp">CONSULTAR</div>
              <div class="item" style="color:#a7b0bc;">⌕ Procedimentos</div>
              <div class="item" style="color:#a7b0bc;">◇ CIDs</div>
              <div class="item" style="color:#a7b0bc;">◈ Relações</div>
            </div>
            <div class="win-main">
              <div class="win-search">⌕ Buscar procedimento, código ou CID...</div>
              <div class="win-grid">
                <div class="win-card hi">
                  <div>
                    <div class="lbl" style="margin-bottom:6px;">COMPETÊNCIA 202608</div>
                    <div class="num" data-count="5023">0</div>
                    <div class="lbl">procedimentos na tabela unificada</div>
                  </div>
                  <div class="mini-btn">⌕ Explorar procedimentos</div>
                </div>
                <div class="win-card"><div class="ic teal"></div><div class="num" data-count="14242">0</div><div class="lbl">CIDs</div></div>
                <div class="win-card"><div class="ic violet"></div><div class="num" data-count="347">0</div><div class="lbl">Habilitações</div></div>
              </div>
            </div>
          </div>
        </div>
 
        <div class="chip chip1"><div class="dotcol">AB</div><div><div class="num" data-count="2719">0</div><div class="lbl">Ocupações CBO</div></div></div>
        <div class="chip chip2"><div class="dotcol">✓</div><div><div class="num">Offline</div><div class="lbl">acesso local</div></div></div>
        <div class="chip chip3"><div class="dotcol">MC</div><div><div class="num">Auto</div><div class="lbl">atualização</div></div></div>
      </div>
    </div>
  </div>
</header>
 
<section id="sobre">
  <div class="wrap">
    <div class="sec-head"><span class="sec-num">01</span><h2>Sobre este repositório</h2></div>
    <div class="about-grid reveal">
      <div>
        <p>Este repositório <strong>não contém código-fonte</strong> — ele existe só para hospedar as versões compiladas (releases) do aplicativo, permitindo que o próprio app verifique e baixe atualizações automaticamente.</p>
        <p>Se você chegou aqui procurando o código do projeto, ele vive num repositório separado e privado.</p>
      </div>
      <div class="folder">
        <div class="tag-top">Releases</div>
        <div class="big">Somente binários compilados (.exe)</div>
        <div class="foot"><span class="d"></span><span>SEM CÓDIGO-FONTE PÚBLICO</span></div>
      </div>
    </div>
  </div>
</section>
 
<section id="baixar">
  <div class="wrap">
    <div class="sec-head"><span class="sec-num">02</span><h2>Baixando o aplicativo</h2></div>
    <p class="reveal" style="color:var(--ink-soft); max-width:60ch; margin-bottom:28px;">Vá até a aba <strong>Releases</strong> deste repositório e baixe a versão mais recente. Nenhuma das opções exige conta ou cadastro público — o acesso é liberado individualmente pelo responsável pelo aplicativo.</p>
    <div class="punch-grid reveal">
      <div class="punch">
        <span class="tag recommend">recomendado</span>
        <div class="filename" style="margin-top:12px;">Consulta de dados SIGTAP - Instalador.exe</div>
        <p class="desc">Instalação normal no computador — cria atalho, abre mais rápido e <strong>atualiza sozinho</strong>.</p>
      </div>
      <div class="punch">
        <span class="tag manual">manual</span>
        <div class="filename" style="margin-top:12px;">Consulta de dados SIGTAP.exe</div>
        <p class="desc">Versão portable — não precisa instalar, roda de qualquer pasta, inclusive um pendrive. Atualização é manual.</p>
      </div>
    </div>
  </div>
</section>
 
<section id="atualiza">
  <div class="wrap">
    <div class="sec-head"><span class="sec-num">03</span><h2>Atualizações automáticas</h2></div>
    <div class="reveal">
      <div class="flow">
        <div class="mini-card old"><div class="v">v1.2.0</div><div class="lbl">desatualizado</div></div>
        <div class="arrow">→</div>
        <div class="mini-card new"><div class="v">v1.3.0</div><div class="lbl">atualizado</div></div>
        <div class="arrow">✓</div>
        <div style="font-size:13px; color:var(--ink-soft); max-width:220px;">verificação automática, um clique para instalar</div>
      </div>
      <div class="note-row">
        <span class="ic">i</span>
        <p>A versão <strong>portable</strong> não se autoatualiza — por natureza, ela não "vive" num lugar fixo. Para atualizar, baixe o .exe mais recente aqui e substitua o antigo.</p>
      </div>
    </div>
  </div>
</section>
 
<section id="projeto">
  <div class="wrap">
    <div class="sec-head"><span class="sec-num">04</span><h2>Sobre o projeto</h2></div>
    <div class="memo reveal">
      <div class="memo-head">Sobre o projeto</div>
      <p>Criado para facilitar o dia a dia de quem trabalha com <mark>faturamento</mark>, <mark>auditoria</mark> e <mark>gestão em saúde pública</mark>, consultando procedimentos, <mark>CIDs</mark>, <mark>CBOs</mark>, valores e regras de <mark>compatibilidade</mark> da tabela SIGTAP sem precisar estar online.</p>
    </div>
  </div>
</section>
 
<footer>
  <div class="plate">Criado por <b>Vitor Correa</b> — JogaeStudio</div>
  <div class="sub">SIGTAP VERSIONADOR · RELEASES OFICIAIS</div>
</footer>
 
<script>
/* reveal on scroll */
const els = document.querySelectorAll('.reveal');
const io = new IntersectionObserver((entries)=>{
  entries.forEach(e=>{ if(e.isIntersecting){ e.target.classList.add('in'); io.unobserve(e.target); } });
}, { threshold: 0.15 });
els.forEach(el=> io.observe(el));
 
/* smooth anchor nav */
document.querySelectorAll('a[href^="#"]').forEach(a=>{
  a.addEventListener('click', e=>{
    e.preventDefault();
    document.querySelector(a.getAttribute('href'))?.scrollIntoView({behavior:'smooth', block:'start'});
  });
});
 
/* mouse parallax tilt on hero stage */
const stage = document.getElementById('stage');
const tilt = document.getElementById('tilt');
if(stage && tilt){
  stage.addEventListener('mousemove', (e)=>{
    const r = stage.getBoundingClientRect();
    const px = (e.clientX - r.left) / r.width - 0.5;
    const py = (e.clientY - r.top) / r.height - 0.5;
    tilt.style.transform = `rotateY(${px*10}deg) rotateX(${-py*10}deg) translateZ(0)`;
  });
  stage.addEventListener('mouseleave', ()=>{ tilt.style.transform = 'rotateY(0deg) rotateX(0deg)'; });
}
 
/* scroll parallax on hero stage (drifts slower than page scroll) */
let ticking = false;
window.addEventListener('scroll', ()=>{
  if(!ticking){
    requestAnimationFrame(()=>{
      const y = window.scrollY;
      if(stage && y < 900){ stage.style.transform = `translateY(${y*0.12}px)`; }
      ticking = false;
    });
    ticking = true;
  }
});
 
/* count-up numbers when visible */
const counters = document.querySelectorAll('[data-count]');
const cio = new IntersectionObserver((entries)=>{
  entries.forEach(e=>{
    if(e.isIntersecting){
      const el = e.target;
      const target = parseInt(el.getAttribute('data-count'), 10);
      const start = performance.now();
      const dur = 1300;
      function tick(now){
        const p = Math.min((now-start)/dur, 1);
        const eased = 1 - Math.pow(1-p, 3);
        const val = Math.floor(eased * target);
        el.textContent = val.toLocaleString('pt-BR');
        if(p < 1) requestAnimationFrame(tick);
        else el.textContent = target.toLocaleString('pt-BR');
      }
      requestAnimationFrame(tick);
      cio.unobserve(el);
    }
  });
}, { threshold: 0.4 });
counters.forEach(el=> cio.observe(el));
</script>
 
</body>
</html>
