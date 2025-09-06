<!doctype html>
<html lang="it">
<head>
<meta charset="utf-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1"/>
<title>Pomodoro Pro</title>
<link rel="icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><circle cx='50' cy='50' r='46' fill='%23e11d48'/><text x='50' y='62' font-size='54' text-anchor='middle' fill='white' font-family='monospace'>🍅</text></svg>">
<style>
:root{
  --bg:#0f1117; --card:#151923; --ink:#e6e8ee; --muted:#a9b0c0; --accent:#7dd3fc; --accent2:#22d3ee; --ok:#22c55e; --warn:#f59e0b; --bad:#ef4444;
}
*{box-sizing:border-box}
html,body{height:100%}
body{margin:0;background:radial-gradient(1200px 800px at 100% -10%,rgba(125,211,252,.08),transparent 60%),radial-gradient(1000px 800px at -20% 120%,rgba(34,197,94,.06),transparent 50%),var(--bg);color:var(--ink);font:14px/1.4 system-ui,-apple-system,Segoe UI,Roboto,Ubuntu,Arial}
.container{max-width:880px;margin:24px auto;padding:16px}
.card{background:linear-gradient(180deg,rgba(255,255,255,.06),rgba(255,255,255,.03));border:1px solid rgba(255,255,255,.08);box-shadow:0 10px 30px rgba(0,0,0,.35), inset 0 1px 0 rgba(255,255,255,.04);border-radius:18px;padding:18px;backdrop-filter:blur(10px)}
.row{display:flex;gap:16px;align-items:center}
.space{flex:1}
.h1{font-size:22px;font-weight:700;letter-spacing:.2px}
.badge{font-size:12px;color:var(--muted);border:1px dashed rgba(255,255,255,.18);padding:4px 8px;border-radius:999px}
.timer{display:flex;align-items:center;gap:18px;margin:14px 0}
.time{font-size:68px;font-weight:800;letter-spacing:-2px}
.mode{color:var(--muted);font-weight:600}
.btn{appearance:none;border:1px solid rgba(255,255,255,.18);background:rgba(255,255,255,.04);color:var(--ink);border-radius:12px;padding:10px 14px;font-weight:600;cursor:pointer}
.btn:hover{border-color:rgba(255,255,255,.28)}
.btn.primary{border-color:transparent;background:linear-gradient(180deg,var(--accent),var(--accent2));color:#0b1220}
.btn.ghost{background:transparent}
.grid{display:grid;grid-template-columns:repeat(3,1fr);gap:12px}
.cell{border:1px solid rgba(255,255,255,.09);background:rgba(255,255,255,.04);border-radius:14px;padding:12px}
.cell b{display:block;color:var(--muted);font-size:12px;margin-bottom:6px}
.input, select{width:100%;padding:10px 12px;border-radius:10px;border:1px solid rgba(255,255,255,.18);background:rgba(255,255,255,.04);color:var(--ink)}
.switch{display:inline-flex;align-items:center;gap:8px}
.switch input{width:44px;height:24px;-webkit-appearance:none;appearance:none;background:#333;border-radius:12px;position:relative;outline:none;border:1px solid rgba(255,255,255,.18)}
.switch input:checked{background:#0ea5e9}
.switch input::after{content:"";position:absolute;top:2px;left:2px;width:18px;height:18px;background:#fff;border-radius:50%;transition:.2s}
.switch input:checked::after{left:24px}
.small{font-size:12px;color:var(--muted)}
hr{border:0;border-top:1px dashed rgba(255,255,255,.15);margin:12px 0}
.footer{display:flex;gap:10px;align-items:center;justify-content:space-between;color:var(--muted)}
.kbd{border:1px solid rgba(255,255,255,.2);padding:2px 6px;border-radius:6px;background:rgba(255,255,255,.06)}
.progress{height:8px;background:rgba(255,255,255,.08);border-radius:999px;overflow:hidden}
.progress>div{height:100%;width:0;background:linear-gradient(90deg,#34d399,#60a5fa);}
.spotify{width:100%;height:152px;border:0;border-radius:14px;}
.compact .timer .time{font-size:40px}
.compact .grid{grid-template-columns:repeat(2,1fr)}
</style>
</head>
<body>
<div class="container">
  <div class="card" id="app">
    <div class="row">
      <div class="h1">Pomodoro Pro</div>
      <span class="badge" id="status">Pronto</span>
      <div class="space"></div>
      <button class="btn ghost" id="compactBtn">Compatta</button>
    </div>

    <div class="progress" aria-label="progress"><div id="bar"></div></div>

    <div class="timer">
      <div>
        <div class="time" id="clock">25:00</div>
        <div class="mode" id="mode">Pomodoro</div>
      </div>
      <div class="space"></div>
      <div class="row">
        <button class="btn primary" id="start">Start (Space)</button>
        <button class="btn" id="pause">Pausa</button>
        <button class="btn" id="reset">Reset</button>
        <button class="btn" id="skip">Skip</button>
      </div>
    </div>

    <div class="grid" style="margin-top:10px">
      <div class="cell"><b>Durate (min)</b>
        <div class="row">
          <input id="pomo" class="input" type="number" min="1" value="25" title="Pomodoro"/>
          <input id="short" class="input" type="number" min="1" value="5" title="Pausa breve"/>
          <input id="long" class="input" type="number" min="1" value="15" title="Pausa lunga"/>
        </div>
      </div>
      <div class="cell"><b>Cicli</b>
        <div class="row">
          <label class="switch"><input id="autoNext" type="checkbox" checked><span class="small">Auto-next</span></label>
          <label class="switch"><input id="autoBreak" type="checkbox" checked><span class="small">Auto-break</span></label>
          <label class="switch"><input id="longEvery" type="checkbox" checked><span class="small">Lunga ogni 4</span></label>
        </div>
        <div class="small" id="cycles">Ciclo 1 di 4</div>
      </div>
      <div class="cell"><b>Suoni & Notifiche</b>
        <div class="row">
          <label class="switch"><input id="bell" type="checkbox" checked><span class="small">Campanella</span></label>
          <label class="switch"><input id="notify" type="checkbox" checked><span class="small">Notifiche</span></label>
          <label class="switch"><input id="titleflash" type="checkbox" checked><span class="small">Lampeggia titolo</span></label>
        </div>
        <div class="row" style="margin-top:8px">
          <input id="vol" class="input" type="range" min="0" max="1" step="0.01" value="0.5"> <span class="small" id="voltxt">Vol 50%</span>
        </div>
      </div>
      <div class="cell"><b>Tema</b>
        <select id="theme" class="input">
          <option value="dark">Dark (default)</option>
          <option value="light">Light</option>
          <option value="ocean">Ocean</option>
          <option value="forest">Forest</option>
        </select>
        <div class="small" style="margin-top:6px">Scorciatoie: <span class="kbd">Space</span> Start/Pausa • <span class="kbd">R</span> Reset • <span class="kbd">N</span> Skip</div>
      </div>
      <div class="cell" style="grid-column:span 2"><b>Spotify (incolla link playlist/album/track)</b>
        <input id="spotifyUrl" class="input" placeholder="https://open.spotify.com/playlist/..."/>
        <div style="margin-top:8px">
          <iframe id="spotify" class="spotify" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>
          <div class="small">Devi essere loggato su Spotify nel browser. Puoi mettere in shuffle/loop dall’iframe.</div>
        </div>
      </div>
      <div class="cell"><b>Export/Import</b>
        <div class="row">
          <button class="btn" id="export">Esporta</button>
          <button class="btn" id="import">Importa</button>
        </div>
        <div class="small">Salva/riprendi le impostazioni. Tutto è anche in <code>localStorage</code>.</div>
      </div>
    </div>

    <hr/>
    <div class="footer">
      <div class="small" id="next">Prossimo: Pausa breve</div>
      <div class="small">Made for Daniele • Pomodoro Pro</div>
    </div>
  </div>
</div>

<audio id="ding" preload="auto">
  <source src="data:audio/mp3;base64,//uQZAAAAAAAAAAAAAAAAAAAAAAAWGluZwAAAA8AAAACAAACcQCAAAACAAACcQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA" type="audio/mpeg">
</audio>
<script>
(function(){
  const qs = id=>document.getElementById(id);
  const el = {
    clock:qs('clock'), mode:qs('mode'), status:qs('status'),
    start:qs('start'), pause:qs('pause'), reset:qs('reset'), skip:qs('skip'),
    pomo:qs('pomo'), short:qs('short'), long:qs('long'),
    autoNext:qs('autoNext'), autoBreak:qs('autoBreak'), longEvery:qs('longEvery'),
    bell:qs('bell'), notify:qs('notify'), titleflash:qs('titleflash'), vol:qs('vol'), voltxt:qs('voltxt'),
    theme:qs('theme'), cycles:qs('cycles'), next:qs('next'), bar:qs('bar'),
    compactBtn:qs('compactBtn'),
    spotifyUrl:qs('spotifyUrl'), spotify:qs('spotify'),
    exportBtn:qs('export'), importBtn:qs('import'), ding:qs('ding'), app:qs('app')
  };

  // Load saved settings
  const saved = JSON.parse(localStorage.getItem('pomo_pro_v1')||'{}');
  const assign=(k,def)=>{ if(saved[k]!==undefined){ if(el[k].type==='checkbox') el[k].checked = !!saved[k]; else el[k].value = saved[k]; } else if(def!=null){ if(el[k].type==='checkbox') el[k].checked=!!def; else el[k].value=def; } };
  ['pomo','short','long','autoNext','autoBreak','longEvery','bell','notify','titleflash','vol','theme','spotifyUrl'].forEach(k=>assign(k));
  if(saved.compact) document.body.classList.add('compact');
  if(saved.spotifyUrl) setSpotify(saved.spotifyUrl);
  el.voltxt.textContent = `Vol ${Math.round((+el.vol.value)*100)}%`;

  // Query params override
  const qp = new URLSearchParams(location.search);
  ['pomo','short','long'].forEach(k=>{ if(qp.get(k)) el[k].value = +qp.get(k); });

  let total = (+el.pomo.value)*60, left=total, mode='pomo', running=false, cycles=1, targetCycle=4, interval=null;

  function fmt(sec){ const m=Math.floor(sec/60).toString().padStart(2,'0'); const s=Math.floor(sec%60).toString().padStart(2,'0'); return `${m}:${s}`; }
  function title(t){ document.title = `🍅 ${t}`; }
  function setBar(){ el.bar.style.width = `${100*(1-left/total)}%`; }
  function save(){ const obj={}; ['pomo','short','long','autoNext','autoBreak','longEvery','bell','notify','titleflash','vol','theme','spotifyUrl'].forEach(k=>{ obj[k]= (el[k].type==='checkbox') ? el[k].checked : el[k].value;}); obj.compact=document.body.classList.contains('compact'); localStorage.setItem('pomo_pro_v1',JSON.stringify(obj)); }

  function switchTheme(name){
    const themes={
      dark:{bg:'#0f1117',grad1:'rgba(125,211,252,.08)',grad2:'rgba(34,197,94,.06)'},
      light:{bg:'#f5f7fb',grad1:'rgba(14,165,233,.18)',grad2:'rgba(34,197,94,.12)',ink:'#0b1220',muted:'#4b5563'},
      ocean:{bg:'#07131c',grad1:'rgba(56,189,248,.12)',grad2:'rgba(99,102,241,.08)'},
      forest:{bg:'#0b1210',grad1:'rgba(34,197,94,.12)',grad2:'rgba(250,204,21,.06)'}
    };
    const t=themes[name]||themes.dark; document.body.style.background=`radial-gradient(1200px 800px at 100% -10%,${t.grad1},transparent 60%),radial-gradient(1000px 800px at -20% 120%,${t.grad2},transparent 50%),${t.bg}`; if(t.ink){ document.documentElement.style.setProperty('--ink',t.ink); document.documentElement.style.setProperty('--muted',t.muted); }
  }
  switchTheme(el.theme.value);

  function setMode(m){
    mode=m; el.mode.textContent = (m==='pomo'?'Pomodoro': m==='short'?'Pausa breve':'Pausa lunga');
    total = (m==='pomo'? +el.pomo.value : m==='short'? +el.short.value : +el.long.value) * 60; left = total; setBar(); updateClock();
    el.status.textContent = 'Pronto';
    el.next.textContent = (m==='pomo'? 'Prossimo: Pausa breve' : 'Prossimo: Pomodoro');
  }
  function updateClock(){ el.clock.textContent = fmt(left); title(`${el.mode.textContent} ${fmt(left)}`); }

  function start(){ if(running) return; running=true; el.status.textContent='In corso'; const startAt=Date.now(); const startLeft=left; interval=setInterval(()=>{ const dt=Math.floor((Date.now()-startAt)/1000); left=startLeft-dt; if(left<=0){ left=0; setBar(); tickEnd(); } updateClock(); setBar(); },250); }
  function pause(){ running=false; el.status.textContent='In pausa'; clearInterval(interval); interval=null; }
  function reset(){ pause(); left=total; setBar(); updateClock(); el.status.textContent='Pronto'; }

  function ring(){ try{ el.ding.volume = +el.vol.value; el.ding.currentTime=0; el.ding.play(); }catch(_){} }
  function notify(msg){ if(!('Notification' in window)) return; if(Notification.permission==='granted'){ new Notification('Pomodoro Pro', { body: msg, icon: document.querySelector('link[rel="icon"]').href }); } else if(Notification.permission!=='denied'){ Notification.requestPermission(); } }
  let flashInt=null; function flashTitle(msg){ if(!el.titleflash.checked) return; let on=false; clearInterval(flashInt); flashInt=setInterval(()=>{ document.title = on? '🔔 '+msg : '🍅 '+msg; on=!on; }, 800); setTimeout(()=>{ clearInterval(flashInt); title(msg); }, 12000); }

  function nextPhase(){ if(mode==='pomo'){ // end of pomodoro
      if(el.longEvery.checked && cycles%4===0){ setMode('long'); } else { setMode('short'); }
    } else { // end of break
      if(mode==='long'){ cycles=1; } else { cycles++; }
      setMode('pomo');
    }
    el.cycles.textContent = `Ciclo ${mode==='pomo'?cycles:cycles-1} di 4`;
    if(el.autoNext.checked) start();
  }

  function tickEnd(){ pause(); if(el.bell.checked) ring(); if(el.notify.checked) notify(`${el.mode.textContent} finito`); flashTitle(`${el.mode.textContent} finito`); if(el.autoBreak.checked || mode!=='pomo'){ nextPhase(); } }

  // Spotify
  function setSpotify(url){ try{ const u=new URL(url); const path=u.pathname.split('/').filter(Boolean); const type=path[0]; const id=path[1]; if(!id) return; el.spotify.src = `https://open.spotify.com/embed/${type}/${id}`; }catch(e){} }

  // Events
  el.start.onclick=start; el.pause.onclick=pause; el.reset.onclick=reset; el.skip.onclick=()=>{ tickEnd(); };
  ['pomo','short','long','autoNext','autoBreak','longEvery','bell','notify','titleflash','vol','theme'].forEach(k=>{ el[k].addEventListener('input',()=>{ if(k==='vol') el.voltxt.textContent = `Vol ${Math.round((+el.vol.value)*100)}%`; if(k==='theme') switchTheme(el.theme.value); save(); }); });
  el.spotifyUrl.addEventListener('change',()=>{ setSpotify(el.spotifyUrl.value); save(); });
  el.compactBtn.onclick=()=>{ document.body.classList.toggle('compact'); el.compactBtn.textContent = document.body.classList.contains('compact')? 'Estesa' : 'Compatta'; save(); };

  el.exportBtn.onclick=()=>{ const data=localStorage.getItem('pomo_pro_v1')||'{}'; const blob=new Blob([data],{type:'application/json'}); const a=document.createElement('a'); a.href=URL.createObjectURL(blob); a.download='pomodoro-pro-settings.json'; a.click(); };
  el.importBtn.onclick=()=>{ const i=document.createElement('input'); i.type='file'; i.accept='application/json'; i.onchange=()=>{ const f=i.files[0]; if(!f) return; const fr=new FileReader(); fr.onload=()=>{ try{ localStorage.setItem('pomo_pro_v1', fr.result); location.reload(); }catch(e){ alert('File non valido'); } }; fr.readAsText(f); }; i.click(); };

  // Keyboard shortcuts
  window.addEventListener('keydown',e=>{ if(e.code==='Space'){ e.preventDefault(); running?pause():start(); } if(e.key==='r' || e.key==='R') reset(); if(e.key==='n' || e.key==='N') tickEnd(); });

  // init
  setMode('pomo'); updateClock(); setBar(); title('Pronto');
})();
</script>
</body>
</html>
