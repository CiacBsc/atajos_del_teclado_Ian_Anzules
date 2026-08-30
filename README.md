<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Atajos del teclado - Juego para practicar</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Baloo+2:wght@500;600;700&family=Nunito:wght@400;600;700;800&display=swap" rel="stylesheet">
<style>
  :root{
    --paper:#FBF8F1; --line:#E7E0CC; --margin:#E8AFAE;
    --ink:#3A342E; --ink-soft:#756B5E; --card:#FFFFFF;
    --purple:#8E7FEA; --purple-d:#5A4BC4;
    --green:#4FAE7C; --green-d:#2E7C54;
    --blue:#5B99DA; --blue-d:#33689E;
    --amber:#EFA84B; --amber-d:#B87A1D;
    --pink:#E97AA5; --pink-d:#B84A78;
    --yellow:#EFCB4E; --yellow-d:#A98A0C;
    --teal:#46B7AC; --teal-d:#277F76;
    --coral:#EE7C61; --coral-d:#C24E32;
    --ok:#3F9E6C; --bad:#DD6259;
  }
  *{box-sizing:border-box;}
  html,body{margin:0;padding:0;}
  body{
    font-family:'Nunito',-apple-system,'Segoe UI',sans-serif;
    color:var(--ink);
    background-color:var(--paper);
    background-image:repeating-linear-gradient(to bottom, transparent 0 33px, var(--line) 33px 34px);
    min-height:100vh;
    display:flex;
    justify-content:center;
    padding:22px 14px 60px;
  }
  #app{width:100%;max-width:460px;}
  h1,h2,h3{font-family:'Baloo 2',sans-serif;font-weight:700;margin:0;}
  .icon{width:1em;height:1em;stroke:currentColor;fill:none;stroke-width:2;stroke-linecap:round;stroke-linejoin:round;}
  button{font-family:inherit;cursor:pointer;}
  button:focus-visible, a:focus-visible{outline:3px solid var(--ink);outline-offset:2px;}
  @media (prefers-reduced-motion: reduce){*{animation-duration:.01ms !important;transition-duration:.01ms !important;}}

  /* header */
  .top{display:flex;align-items:center;gap:10px;margin-bottom:18px;}
  .top-icon{width:40px;height:40px;border-radius:12px;background:var(--purple);color:#fff;display:flex;align-items:center;justify-content:center;flex-shrink:0;}
  .top-icon .icon{width:22px;height:22px;}
  .top h1{font-size:21px;color:var(--ink);}
  .top p{margin:2px 0 0;font-size:13px;color:var(--ink-soft);}

  /* card sheet */
  .sheet{background:var(--card);border-radius:18px;border:1.5px solid var(--line);padding:22px 18px;position:relative;overflow:hidden;}
  .sheet::before{content:"";position:absolute;left:34px;top:0;bottom:0;width:2px;background:var(--margin);opacity:.55;}
  .sheet-inner{position:relative;padding-left:14px;}

  /* menu screen */
  .menu-title{font-size:15px;color:var(--ink-soft);margin:0 0 14px;}
  .level-card{display:flex;align-items:center;gap:14px;width:100%;background:#fff;border:2px solid var(--line);border-radius:16px;padding:14px 16px;margin-bottom:12px;text-align:left;transition:transform .12s, border-color .12s;}
  .level-card:active{transform:scale(.97);}
  .level-card .lc-icon{width:52px;height:52px;border-radius:14px;display:flex;align-items:center;justify-content:center;flex-shrink:0;}
  .level-card .lc-icon .icon{width:28px;height:28px;color:#fff;}
  .level-card h3{font-size:17px;}
  .level-card p{margin:3px 0 0;font-size:13px;color:var(--ink-soft);}
  .lvl1 .lc-icon{background:var(--blue);} .lvl1{border-color:var(--blue);}
  .lvl2 .lc-icon{background:var(--teal);} .lvl2{border-color:var(--teal);}

  /* game header */
  .game-top{display:flex;align-items:center;gap:10px;margin-bottom:14px;}
  .back-btn{background:none;border:none;color:var(--ink-soft);display:flex;align-items:center;padding:6px;border-radius:10px;}
  .back-btn .icon{width:22px;height:22px;}
  .back-btn:hover{background:var(--paper);}
  .progress-label{font-size:13px;color:var(--ink-soft);font-weight:700;margin-bottom:4px;}
  .dots{display:flex;gap:5px;flex:1;flex-wrap:wrap;}
  .dot{width:9px;height:9px;border-radius:50%;background:var(--line);}
  .dot.done{background:var(--ok);}
  .dot.current{background:var(--amber);}

  /* question */
  .q-icon-wrap{width:64px;height:64px;border-radius:16px;display:flex;align-items:center;justify-content:center;margin:4px auto 14px;}
  .q-icon-wrap .icon{width:34px;height:34px;color:#fff;}
  .q-prompt{font-size:19px;text-align:center;line-height:1.4;margin:0 0 20px;font-weight:600;}
  .options{display:flex;flex-direction:column;gap:12px;}
  .opt{display:flex;align-items:center;justify-content:center;gap:12px;background:#fff;border:2.5px solid var(--line);border-radius:16px;padding:12px 14px;transition:transform .1s, border-color .1s, background .15s;}
  .opt .opt-icon{width:38px;height:38px;border-radius:11px;display:flex;align-items:center;justify-content:center;flex-shrink:0;}
  .opt .opt-icon .icon{width:20px;height:20px;color:#fff;}
  .opt-keys{display:flex;align-items:center;gap:5px;}
  .key{border:2px solid var(--ink);border-radius:8px;padding:5px 9px;font-weight:700;font-size:15px;background:#fff;line-height:1;}
  .plus{font-weight:700;color:var(--ink-soft);}
  .opt:active{transform:scale(.97);}
  .opt.correct{border-color:var(--ok);background:#EAF6EF;animation:pop .35s;}
  .opt.wrong{border-color:var(--bad);background:#FCECEA;animation:shake .35s;}
  .opt.hint{border-color:var(--ok);background:#EAF6EF;}
  .opt:disabled{opacity:.55;}
  @keyframes pop{0%{transform:scale(1);}40%{transform:scale(1.04);}100%{transform:scale(1);}}
  @keyframes shake{0%,100%{transform:translateX(0);}25%{transform:translateX(-6px);}75%{transform:translateX(6px);}}

  .feedback{min-height:26px;text-align:center;font-weight:700;font-size:15px;margin-top:14px;}
  .feedback.ok{color:var(--ok);}
  .feedback.bad{color:var(--bad);}

  /* mascot */
  .mascot{width:56px;height:56px;margin:0 auto 8px;transition:transform .3s;}
  .mascot.bounce{animation:bounce .5s;}
  @keyframes bounce{0%,100%{transform:translateY(0) rotate(0);}30%{transform:translateY(-8px) rotate(-4deg);}60%{transform:translateY(0) rotate(4deg);}}

  /* complete screen */
  .complete{text-align:center;padding:10px 0 4px;}
  .complete .mascot{width:78px;height:78px;}
  .complete h2{font-size:22px;margin:10px 0 4px;}
  .complete p{color:var(--ink-soft);font-size:15px;margin:0 0 20px;}
  .stars-row{display:flex;justify-content:center;gap:6px;margin-bottom:18px;}
  .stars-row .icon{width:26px;height:26px;}
  .btn-row{display:flex;flex-direction:column;gap:10px;}
  .btn{border:none;border-radius:14px;padding:14px;font-family:'Baloo 2',sans-serif;font-weight:600;font-size:16px;display:flex;align-items:center;justify-content:center;gap:8px;}
  .btn .icon{width:19px;height:19px;}
  .btn-primary{background:var(--ink);color:#fff;}
  .btn-secondary{background:#fff;border:2px solid var(--line);color:var(--ink);}
  .btn:active{transform:scale(.98);}

  .tip{display:flex;gap:10px;align-items:flex-start;background:#FDF6E9;border-radius:14px;padding:12px 14px;margin-top:16px;font-size:13px;color:var(--ink-soft);line-height:1.5;}
  .tip .icon{width:18px;height:18px;color:var(--amber-d);flex-shrink:0;margin-top:1px;}
</style>
</head>
<body>
<div id="app"></div>

<svg style="display:none" aria-hidden="true">
  <symbol id="i-copy" viewBox="0 0 24 24"><rect x="9" y="9" width="11" height="11" rx="2"/><path d="M5 15V5a2 2 0 0 1 2-2h10"/></symbol>
  <symbol id="i-paste" viewBox="0 0 24 24"><rect x="6" y="4" width="12" height="16" rx="2"/><path d="M9 4V3a1 1 0 0 1 1-1h4a1 1 0 0 1 1 1v1"/><path d="M9 12h6M9 16h6"/></symbol>
  <symbol id="i-cut" viewBox="0 0 24 24"><circle cx="6" cy="6" r="2.5"/><circle cx="6" cy="18" r="2.5"/><path d="M8.3 7.6 20 19M8.3 16.4 20 5"/></symbol>
  <symbol id="i-undo" viewBox="0 0 24 24"><path d="M4 10h9a5 5 0 0 1 0 10h-2"/><path d="M8 5 3 10l5 5"/></symbol>
  <symbol id="i-redo" viewBox="0 0 24 24"><path d="M20 10h-9a5 5 0 0 0 0 10h2"/><path d="M16 5l5 5-5 5"/></symbol>
  <symbol id="i-print" viewBox="0 0 24 24"><rect x="6" y="9" width="12" height="7" rx="1"/><path d="M8 9V4h8v5"/><path d="M8 16v4h8v-4"/></symbol>
  <symbol id="i-folder" viewBox="0 0 24 24"><path d="M3 8l1.4 10.2A2 2 0 0 0 6.4 20h11.2a2 2 0 0 0 2-1.8L21 8H3z"/><path d="M3 8V6a2 2 0 0 1 2-2h3.5l2 2H19a2 2 0 0 1 2 2v0"/></symbol>
  <symbol id="i-search" viewBox="0 0 24 24"><circle cx="10.5" cy="10.5" r="6"/><path d="M15 15l5.5 5.5"/></symbol>
  <symbol id="i-newdoc" viewBox="0 0 24 24"><path d="M13 3H7a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h10a2 2 0 0 0 2-2V8z"/><path d="M13 3v5h5"/><path d="M12 12.5v5M9.5 15h5"/></symbol>
  <symbol id="i-save" viewBox="0 0 24 24"><path d="M5 4h11l3 3v13a1 1 0 0 1-1 1H5a1 1 0 0 1-1-1V5a1 1 0 0 1 1-1z"/><path d="M8 4v6h7V4"/><rect x="8" y="14" width="7.5" height="6"/></symbol>
  <symbol id="i-tabnew" viewBox="0 0 24 24"><path d="M4 6.5a2 2 0 0 1 2-2h4.5l2 2H18a2 2 0 0 1 2 2v9a2 2 0 0 1-2 2H6a2 2 0 0 1-2-2z"/><path d="M12 11v5M9.5 13.5h5"/></symbol>
  <symbol id="i-tabclose" viewBox="0 0 24 24"><path d="M4 6.5a2 2 0 0 1 2-2h4.5l2 2H18a2 2 0 0 1 2 2v9a2 2 0 0 1-2 2H6a2 2 0 0 1-2-2z"/><path d="M10 11.3l4 4M14 11.3l-4 4"/></symbol>
  <symbol id="i-reload" viewBox="0 0 24 24"><path d="M20 12a8 8 0 1 1-3.1-6.3"/><path d="M20 4v5.5h-5.5"/></symbol>
  <symbol id="i-history" viewBox="0 0 24 24"><circle cx="12" cy="13" r="7.2"/><path d="M12 9.3V13l2.6 1.6"/><path d="M9 3.6A8 8 0 0 0 5 7.2"/></symbol>
  <symbol id="i-download" viewBox="0 0 24 24"><path d="M12 4v11.5"/><path d="M8 11.5l4 4 4-4"/><path d="M5 19.5h14"/></symbol>
  <symbol id="i-switch" viewBox="0 0 24 24"><path d="M4 8.5h13"/><path d="M14 4.5l4 4-4 4"/><path d="M20 15.5H7"/><path d="M10 11.5l-4 4 4 4"/></symbol>
  <symbol id="i-power" viewBox="0 0 24 24"><path d="M12 3v8.5"/><path d="M6.3 6.6a8 8 0 1 0 11.4 0"/></symbol>
  <symbol id="i-back" viewBox="0 0 24 24"><path d="M19 12H6M11 6l-6 6 6 6"/></symbol>
  <symbol id="i-star" viewBox="0 0 24 24"><path d="M12 2.5l2.9 6 6.6.7-4.9 4.5 1.3 6.5-5.9-3.3-5.9 3.3 1.3-6.5-4.9-4.5 6.6-.7z" fill="currentColor" stroke="none"/></symbol>
  <symbol id="i-replay" viewBox="0 0 24 24"><path d="M4 12a8 8 0 1 1 2.9 6.1"/><path d="M4 20v-5.5h5.5"/></symbol>
  <symbol id="i-grid" viewBox="0 0 24 24"><rect x="3.5" y="3.5" width="7" height="7" rx="1.5"/><rect x="13.5" y="3.5" width="7" height="7" rx="1.5"/><rect x="3.5" y="13.5" width="7" height="7" rx="1.5"/><rect x="13.5" y="13.5" width="7" height="7" rx="1.5"/></symbol>
  <symbol id="i-bulb" viewBox="0 0 24 24"><path d="M9 18h6M10 21h4"/><path d="M12 3a6 6 0 0 0-3.5 10.9c.6.4 1 1.1 1 1.9v.2h5v-.2c0-.8.4-1.5 1-1.9A6 6 0 0 0 12 3z"/></symbol>
  <symbol id="i-laptop" viewBox="0 0 24 24"><rect x="4" y="4" width="16" height="11" rx="1.5"/><circle cx="9.5" cy="9" r="1" fill="currentColor" stroke="none"/><circle cx="14.5" cy="9" r="1" fill="currentColor" stroke="none"/><path d="M9.5 11.8a3 3 0 0 0 5 0"/><path d="M2 18.5h20l-1.5 2H3.5z"/></symbol>
</svg>

<script>
const COLORS = {
  purple:['var(--purple)','var(--purple-d)'], green:['var(--green)','var(--green-d)'],
  blue:['var(--blue)','var(--blue-d)'], amber:['var(--amber)','var(--amber-d)'],
  pink:['var(--pink)','var(--pink-d)'], yellow:['var(--yellow)','var(--yellow-d)'],
  teal:['var(--teal)','var(--teal-d)'], coral:['var(--coral)','var(--coral-d)']
};

const LEVELS = {
  1: {
    name:'Trabajar en la compu', icon:'i-newdoc', color:'blue',
    desc:'Copiar, guardar, imprimir y más',
    items:[
      {combo:'Ctrl + C', action:'copiar', icon:'i-copy', color:'purple', prompt:'Quiero copiar este dibujo'},
      {combo:'Ctrl + V', action:'pegar', icon:'i-paste', color:'green', prompt:'Ya copié algo, quiero pegarlo aquí'},
      {combo:'Ctrl + X', action:'cortar', icon:'i-cut', color:'blue', prompt:'Quiero cortar esta parte del texto'},
      {combo:'Ctrl + Z', action:'deshacer', icon:'i-undo', color:'pink', prompt:'¡Uy, me equivoqué! Quiero deshacerlo'},
      {combo:'Ctrl + Y', action:'rehacer', icon:'i-redo', color:'yellow', prompt:'Ahora quiero rehacer lo que deshice'},
      {combo:'Ctrl + P', action:'imprimir', icon:'i-print', color:'amber', prompt:'Terminé mi dibujo, quiero imprimirlo'},
      {combo:'Ctrl + O', action:'abrir documento', icon:'i-folder', color:'teal', prompt:'Quiero abrir un documento guardado'},
      {combo:'Ctrl + U', action:'nuevo documento', icon:'i-newdoc', color:'green', prompt:'Quiero empezar un documento nuevo'},
      {combo:'Ctrl + G', action:'guardar', icon:'i-save', color:'blue', prompt:'Terminé mi trabajo, quiero guardarlo'},
      {combo:'Ctrl + B', action:'buscar', icon:'i-search', color:'coral', prompt:'Quiero buscar una palabra en mi documento'},
      {combo:'Ctrl + F', action:'buscar', icon:'i-search', color:'purple', prompt:'Quiero buscar una palabra en la página'}
    ]
  },
  2:{
    name:'Internet', icon:'i-tabnew', color:'teal',
    desc:'Pestañas, buscar páginas y más',
    items:[
      {combo:'Ctrl + T', action:'nueva pestaña', icon:'i-tabnew', color:'teal', prompt:'Cual es el atajo para ABRIR UNA PESTAÑA NUEVA'},
      {combo:'Ctrl + W', action:'cerrar pestaña', icon:'i-tabclose', color:'coral', prompt:'Cual es el atajo para CERRAR PESTAÑA'},
      {combo:'Ctrl + R', action:'recargar página', icon:'i-reload', color:'blue', prompt:'Cual es el atajo para RECARGAR LA PAGINA'},
      {combo:'Ctrl + H', action:'ver historial', icon:'i-history', color:'purple', prompt:'Cual es el atajo para VER EL HISTORIAL'},
      {combo:'Ctrl + J', action:'ver descargas', icon:'i-download', color:'green', prompt:'Cual es el atajo para VER MIS DESCARGAS'},
      {combo:'Ctrl + Tab', action:'cambiar de pestaña', icon:'i-switch', color:'amber', prompt:'Cual es el atajo para CAMBIAR ENTRE PESTAÑAS'},
      {combo:'Alt + F4', action:'cerrar el programa', icon:'i-power', color:'pink', prompt:'Cual es el atajo para CERRAR VENTANA'}
    ]
  }
};

const OK_MSGS = ['¡Muy bien!','¡Genial!','¡Excelente!','¡Lo lograste!','¡Perfecto!','¡Así es!'];

let state = { screen:'menu' };
const app = document.getElementById('app');

function shuffle(arr){
  const a = arr.slice();
  for(let i=a.length-1;i>0;i--){
    const j = Math.floor(Math.random()*(i+1));
    [a[i],a[j]] = [a[j],a[i]];
  }
  return a;
}

function icon(id, cls){ return '<svg class="icon '+(cls||'')+'"><use href="#'+id+'"/></svg>'; }

function keysHtml(combo){
  return combo.split(' + ').map(function(k){return '<span class="key">'+k+'</span>';}).join('<span class="plus">+</span>');
}

function mascot(cls){
  return '<div class="mascot '+(cls||'')+'" style="color:var(--blue-d)">'+icon('i-laptop')+'</div>';
}

/* ---------- audio (very light, best-effort) ---------- */
let actx = null;
function tone(freq, start, dur, type){
  try{
    if(!actx) actx = new (window.AudioContext||window.webkitAudioContext)();
    const o = actx.createOscillator(); const g = actx.createGain();
    o.type = type||'sine'; o.frequency.value = freq;
    o.connect(g); g.connect(actx.destination);
    const t0 = actx.currentTime+start;
    g.gain.setValueAtTime(0.0001, t0);
    g.gain.exponentialRampToValueAtTime(0.09, t0+0.02);
    g.gain.exponentialRampToValueAtTime(0.0001, t0+dur);
    o.start(t0); o.stop(t0+dur+0.02);
  }catch(e){}
}
function soundOk(){ tone(523,0,.14); tone(784,.11,.18); }
function soundBad(){ tone(220,0,.18,'sine'); }

/* ---------- render: menu ---------- */
function renderMenu(){
  let html = '';
  html += '<div class="top"><div class="top-icon">'+icon('i-laptop')+'</div>';
  html += '<div><h1>Atajos del teclado</h1><p>Elige qué quieres practicar</p></div></div>';
  html += '<div class="sheet"><div class="sheet-inner">';
  html += '<p class="menu-title">Toca un nivel para empezar</p>';
  [1,2].forEach(function(n){
    const lvl = LEVELS[n];
    html += '<button class="level-card lvl'+n+'" data-level="'+n+'">';
    html += '<div class="lc-icon">'+icon(lvl.icon)+'</div>';
    html += '<div><h3>'+lvl.name+'</h3><p>'+lvl.desc+'</p></div></button>';
  });
  html += '</div></div>';
  html += '<div class="tip">'+icon('i-bulb')+'<span>By CIAC Desing - Cesar Anzules * For Ian Anzules.</span></div>';
  app.innerHTML = html;
  app.querySelectorAll('.level-card').forEach(function(btn){
    btn.addEventListener('click', function(){ startLevel(parseInt(btn.dataset.level,10)); });
  });
}

/* ---------- render: game ---------- */
function startLevel(n){
  const items = shuffle(LEVELS[n].items);
  state = {
    screen:'game', level:n, items:items, index:0,
    correctFirstTry:0, wrongCount:0
  };
  renderGame();
}

function buildOptions(levelItems, correct){
  const pool = levelItems.filter(function(i){ return i.action !== correct.action; });
  const distractors = shuffle(pool).slice(0,2);
  return shuffle([correct].concat(distractors));
}

function renderGame(){
  const lvl = LEVELS[state.level];
  const q = state.items[state.index];
  const options = buildOptions(lvl.items, q);
  state.options = options;
  state.wrongThisQ = 0;

  let dots = '';
  state.items.forEach(function(it, i){
    let cls = 'dot';
    if(i < state.index) cls += ' done';
    else if(i === state.index) cls += ' current';
    dots += '<span class="'+cls+'"></span>';
  });

  let html = '';
  html += '<div class="game-top"><button class="back-btn" id="backBtn" aria-label="Volver al menú">'+icon('i-back')+'</button>';
  html += '<div style="flex:1"><p class="progress-label">'+lvl.name+' · '+(state.index+1)+' de '+state.items.length+'</p><div class="dots">'+dots+'</div></div></div>';
  html += '<div class="sheet"><div class="sheet-inner">';
  html += mascot();
  const qc = COLORS[q.color];
  html += '<div class="q-icon-wrap" style="background:'+qc[0]+'">'+icon(q.icon)+'</div>';
  html += '<p class="q-prompt">'+q.prompt+'</p>';
  html += '<div class="options">';
  options.forEach(function(opt){
    const c = COLORS[opt.color];
    html += '<button class="opt" data-combo="'+opt.combo+'" style="--oc:'+c[0]+'">';
    html += '<span class="opt-keys">'+keysHtml(opt.combo)+'</span></button>';
  });
  html += '</div>';
  html += '<p class="feedback" id="feedback"></p>';
  html += '</div></div>';
  app.innerHTML = html;

  document.getElementById('backBtn').addEventListener('click', function(){ state.screen='menu'; renderMenu(); });
  app.querySelectorAll('.opt').forEach(function(btn){
    btn.addEventListener('click', function(){ answer(btn, q); });
  });
}

function answer(btn, q){
  if(btn.disabled) return;
  const chosen = btn.dataset.combo;
  const feedback = document.getElementById('feedback');
  const allOpts = app.querySelectorAll('.opt');

  if(chosen === q.combo){
    allOpts.forEach(function(b){ b.disabled = true; });
    btn.classList.add('correct');
    feedback.textContent = OK_MSGS[Math.floor(Math.random()*OK_MSGS.length)];
    feedback.className = 'feedback ok';
    document.querySelector('.mascot').classList.add('bounce');
    soundOk();
    if(state.wrongThisQ === 0) state.correctFirstTry++;
    setTimeout(nextQuestion, 950);
  } else {
    btn.classList.add('wrong');
    btn.disabled = true;
    state.wrongCount++;
    state.wrongThisQ++;
    soundBad();
    setTimeout(function(){ btn.classList.remove('wrong'); }, 400);
    if(state.wrongThisQ >= 2){
      feedback.textContent = 'Esta es la correcta, tócala:';
      feedback.className = 'feedback bad';
      allOpts.forEach(function(b){
        if(b.dataset.combo === q.combo) b.classList.add('hint');
      });
    } else {
      feedback.textContent = 'Casi... ¡inténtalo otra vez!';
      feedback.className = 'feedback bad';
    }
  }
}

function nextQuestion(){
  if(state.index < state.items.length - 1){
    state.index++;
    renderGame();
  } else {
    renderComplete();
  }
}

function renderComplete(){
  const lvl = LEVELS[state.level];
  const total = state.items.length;
  let stars = '';
  for(let i=0;i<3;i++){
    const filled = state.correctFirstTry >= Math.ceil(total*((i+1)/3));
    stars += '<span style="color:'+(filled?'var(--amber)':'var(--line)')+'">'+icon('i-star')+'</span>';
  }
  let html = '<div class="sheet"><div class="sheet-inner complete">';
  html += mascot('bounce');
  html += '<h2>¡Terminaste '+lvl.name+'! 🎉</h2>';
  html += '<p>Acertó '+state.correctFirstTry+' de '+total+' a la primera</p>';
  html += '<div class="stars-row">'+stars+'</div>';
  html += '<div class="btn-row">';
  html += '<button class="btn btn-primary" id="replayBtn">'+icon('i-replay')+' Jugar de nuevo</button>';
  html += '<button class="btn btn-secondary" id="menuBtn">'+icon('i-grid')+' Elegir otro nivel</button>';
  html += '</div></div></div>';
  app.innerHTML = html;
  document.getElementById('replayBtn').addEventListener('click', function(){ startLevel(state.level); });
  document.getElementById('menuBtn').addEventListener('click', renderMenu);
}

renderMenu();
</script>
</body>
</html>
