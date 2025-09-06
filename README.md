<!doctype html>
<html lang="it">
<head>
<meta charset="utf-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1"/>
<title>Pomodoro Pro</title>
<style>
:root {
  --bg: #f5f7fb; /* chiaro */
  --ink: #1c1c1e; /* testo scuro */
  --muted: #4a5568;
  --card: #ffffff; /* box */
  --card2: #f9fbfd;
  --line: rgba(0, 0, 0, .08);
  --grad1: rgba(59,130,246,.08);
  --grad2: rgba(34,197,94,.05);
}
*{box-sizing:border-box}
html,body{height:100%}
body{margin:0;background:radial-gradient(1200px 800px at 100% -10%,var(--grad1),transparent 60%),radial-gradient(1000px 800px at -20% 120%,var(--grad2),transparent 50%),var(--bg);color:var(--ink);font:14px/1.45 system-ui,-apple-system,Segoe UI,Roboto,Ubuntu,Arial}
.container{max-width:880px;margin:24px auto;padding:0 14px}
.app{background:var(--card);border:1px solid var(--line);border-radius:18px;box-shadow:0 8px 20px rgba(0,0,0,.08);overflow:hidden}
.header{display:flex;gap:10px;align-items:center;justify-content:space-between;padding:14px 16px;border-bottom:1px solid var(--line);background:linear-gradient(180deg,rgba(255,255,255,.7),rgba(255,255,255,.3))}
.h1{font-size:18px;font-weight:800;letter-spacing:.2px;color:#1c1c1e}
.badge{font-size:12px;color:var(--muted);border:1px dashed var(--line);padding:4px 8px;border-radius:999px;background:#f3f7fb}
.btn{appearance:none;border:1px solid var(--line);background:rgba(255,255,255,.9);color:#1c1c1e;border-radius:10px;padding:8px 12px;font-weight:600;cursor:pointer;transition:.15s}
.btn:hover{background:#eaf2ff}
.btn.primary{border-color:transparent;background:linear-gradient(180deg,#60a5fa,#22d3ee);color:#fff}
.timerWrap{display:flex;gap:16px;align-items:center;padding:16px}
.time{font-size:72px;font-weight:900;letter-spacing:-2px;line-height:1}
.mode{color:var(--muted);font-weight:600;margin-top:4px}
.controls{display:flex;gap:10px;margin-left:auto}
.progress{height:8px;background:rgba(0,0,0,.06);border-radius:999px;overflow:hidden;margin:0 16px}
.progress>div{height:100%;width:0;background:linear-gradient(90deg,#34d399,#60a5fa)}
.grid{display:grid;grid-template-columns:repeat(12,1fr);gap:12px;padding:16px}
.card{grid-column:span 4;background:var(--card2);border:1px solid var(--line);border-radius:14px;padding:12px;box-shadow:0 2px 4px rgba(0,0,0,.04)}
.card b{display:block;color:var(--muted);font-size:12px;margin-bottom:8px;letter-spacing:.2px}
.card--wide{grid-column:span 12}
.card--half{grid-column:span 6}
.row{display:flex;gap:10px;align-items:center}
.input, select{width:100%;padding:10px 12px;border-radius:10px;border:1px solid var(--line);background:#fff;color:#1c1c1e;box-shadow:0 1px 2px rgba(0,0,0,.04)}
.input:focus,select:focus{outline:2px solid #60a5fa}
.switch{display:inline-flex;align-items:center;gap:8px}
.switch input{width:44px;height:24px;-webkit-appearance:none;appearance:none;background:#d1d5db;border-radius:12px;border:1px solid var(--line);position:relative;outline:none}
.switch input:checked{background:#0ea5e9}
.switch input::after{content:"";position:absolute;top:2px;left:2px;width:18px;height:18px;background:#fff;border-radius:50%;transition:.2s}
.switch input:checked::after{left:24px}
.small{font-size:12px;color:var(--muted)}
.kbd{border:1px solid var(--line);padding:2px 6px;border-radius:6px;background:#fff}
.spotify{width:100%;height:152px;border:0;border-radius:10px;box-shadow:0 2px 6px rgba(0,0,0,.1)}
.footer{display:flex;align-items:center;justify-content:space-between;padding:12px 16px;border-top:1px dashed var(--line);color:var(--muted)}
.compact .time{font-size:42px}
@media (max-width:820px){.timerWrap{flex-wrap:wrap}.controls{margin-left:0}.card,.card--half,.card--wide{grid-column:span 12}}
</style>
</head>
<body>
<div class="container">
  <div class="app" id="app">
    <div class="header">
      <div class="row"><div class="h1">Pomodoro Pro</div><span class="badge" id="status">Pronto</span></div>
      <div class="right"><button class="btn" id="compactBtn">Compatta</button></div>
    </div>

    <div class="progress"><div id="bar"></div></div>

    <div class="timerWrap">
      <div>
        <div class="time" id="clock">25:00</div>
        <div class="mode" id="mode">Pomodoro</div>
      </div>
      <div class="controls">
        <button class="btn primary" id="start">Start (Space)</button>
        <button class="btn" id="pause">Pausa</button>
        <button class="btn" id="reset">Reset</button>
        <button class="btn" id="skip">Skip</button>
      </div>
    </div>

    <div class="grid">
      <div class="card card--half">
        <b>Durate (min)</b>
        <div class="row">
          <input id="pomo" class="input" type="number" min="1" value="25" title="Pomodoro"/>
          <input id="short" class="input" type="number" min="1" value="5" title="Pausa breve"/>
          <input id="long" class="input" type="number" min="1" value="15" title="Pausa lunga"/>
        </div>
      </div>

      <div class="card card--half">
        <b>Cicli</b>
        <div class="row" style="flex-wrap:wrap">
          <label class="switch"><input id="autoNext" type="checkbox" checked><span class="small">Auto‑next</span></label>
          <label class="switch"><input id="autoBreak" type="checkbox" checked><span class="small">Auto‑break</span></label>
          <label class="switch"><input id="longEvery" type="checkbox" checked><span class="small">Lunga ogni 4</span></label>
        </div>
        <div class="small" id="cycles" style="margin-top:6px">Ciclo 1 di 4</div>
      </div>

      <div class="card">
        <b>Suoni & Notifiche</b>
        <div class="row" style="flex-wrap:wrap">
          <label class="switch"><input id="bell" type="checkbox" checked><span class="small">Campanella</span></label>
          <label class="switch"><input id="notify" type="checkbox" checked><span class="small">Notifiche</span></label>
          <label class="switch"><input id="titleflash" type="checkbox" checked><span class="small">Lampeggia titolo</span></label>
          <label class="switch"><input id="uiSounds" type="checkbox" checked><span class="small">Suoni UI</span></label>
        </div>
        <div class="row" style="margin-top:8px"><input id="vol" class="input" type="range" min="0" max="1" step="0.01" value="0.5"> <span class="small" id="voltxt">Vol 50%</span></div>
      </div>

      <div class="card">
        <b>Tema</b>
        <select id="theme" class="input">
          <option value="light">Light (default)</option>
          <option value="dark">Dark</option>
          <option value="ocean">Ocean</option>
          <option value="forest">Forest</option>
        </select>
        <div class="small" style="margin-top:6px">Scorciatoie: <span class="kbd">Space</span> Start/Pausa • <span class="kbd">R</span> Reset • <span class="kbd">N</span> Skip</div>
      </div>

      <div class="card card--wide">
        <b>Spotify (incolla link playlist/album/track)</b>
        <input id="spotifyUrl" class="input" placeholder="https://open.spotify.com/playlist/..."/>
        <div style="margin-top:8px">
          <iframe id="spotify" class="spotify" allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture" loading="lazy"></iframe>
          <div class="small">Devi essere loggato su Spotify nel browser. Puoi mettere in shuffle/loop dall’iframe.</div>
        </div>
      </div>

      <div class="card">
        <b>Export/Import</b>
        <div class="row"><button class="btn" id="export">Esporta</button><button class="btn" id="import">Importa</button></div>
        <div class="small" style="margin-top:6px">Salva/riprendi le impostazioni (anche in <code>localStorage</code>).</div>
      </div>
    </div>

    <div class="footer"><div class="small" id="next">Prossimo: Pausa breve</div><div class="small">Made for Daniele • Pomodoro Pro</div></div>
  </div>
</div>

<audio id="ding" preload="auto"><source src="data:audio/mp3;base64,//uQZAAAAAAAAAAAAAAAAAAAAAAAWGluZwAAAA8AAAACAAACcQCAAAACAAACcQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA" type="audio/mpeg"></audio>
<script>
(function(){
  const qs = id=>document.getElementById(id);
  const el = {clock:qs('clock'), mode:qs('mode'), status:qs('status'), start:qs('start'), pause:qs('pause'), reset:qs('reset'), skip:qs('skip'), pomo:qs('pomo'), short:qs('short'), long:qs('long'), autoNext:qs('autoNext'), autoBreak:qs('autoBreak'), longEvery:qs('longEvery'), bell:qs('bell'), notify:qs('notify'), titleflash:qs('titleflash'), uiSounds:qs('uiSounds'), vol:qs('vol'), voltxt:qs('voltxt'), theme:qs('theme'), cycles:qs('cycles'), next:qs('next'), bar:qs('bar'), compactBtn:qs('compactBtn'), spotifyUrl:qs('spotifyUrl'), spotify:qs('spotify'), exportBtn:qs('export'), importBtn:qs('import'), ding:qs('ding'), app:qs('app') };

  // WebAudio per suoni UI (click/whoosh)
  let AC; function uiSound(freq=700, dur=0.04){ if(!el.uiSounds.checked) return; try{ AC = AC || new (window.AudioContext||window.webkitAudioContext)(); const o=AC.createOscillator(); const g=AC.createGain(); o.frequency.value=freq; const v=(+el.vol.value)*0.5; g.gain.setValueAtTime(v, AC.currentTime); g.gain.exponentialRampToValueAtTime(0.0001, AC.currentTime+dur); o.connect(g).connect(AC.destination); o.start(); o.stop(AC.currentTime+dur); }catch(e){} }

  // saved settings
  const saved = JSON.parse(localStorage.getItem('pomo_pro_v3')||'{}');
  const assign=(k)=>{ if(saved[k]!==undefined){ if(el[k]?.type==='checkbox') el[k].checked=!!saved[k]; else if(el[k]) el[k].value=saved[k]; } };
  ['pomo','short','long','autoNext','autoBreak','longEvery','bell','notify','titleflash','uiSounds','vol','theme','spotifyUrl','compact'].forEach(k=>assign(k));
  if(saved.compact) document.body.classList.add('compact');
  if(saved.spotifyUrl) setSpotify(saved.spotifyUrl);
  el.voltxt.textContent = `Vol ${Math.round((+el.vol.value)*100)}%`;

  // query params
  const qp = new URLSearchParams(location.search);
  if(qp.get('compact')==='1') document.body.classList.add('compact');
  ['pomo','short','long'].forEach(k=>{ if(qp.get(k)) el[k].value = +qp.get(k); });

  let total=(+el.pomo.value)*60, left=total, mode='pomo', running=false, cycles=1, interval=null;
  const fmt=s=>`${String(Math.floor(s/60)).padStart(2,'0')}:${String(Math.floor(s%60)).padStart(2,'0')}`;
  const title=t=>document.title=`🍅 ${t}`;
  const setBar=()=>el.bar.style.width=`${100*(1-left/total)}%`;
  const save=()=>{ const o={}; ['pomo','short','long','autoNext','autoBreak','longEvery','bell','notify','titleflash','uiSounds','vol','theme','spotifyUrl'].forEach(k=>o[k]= el[k]?.type==='checkbox'? el[k].checked : el[k]?.value); o.compact=document.body.classList.contains('compact'); localStorage.setItem('pomo_pro_v3',JSON.stringify(o)); };

  function switchTheme(name){ const t={light:['#f5f7fb','rgba(59,130,246,.08)','rgba(34,197,94,.05)'], dark:['#0b0f14','rgba(59,130,246,.12)','rgba(34,197,94,.08)'], ocean:['#07131c','rgba(56,189,248,.12)','rgba(99,102,241,.08)'], forest:['#0b1210','rgba(34,197,94,.12)','rgba(250,204,21,.06)'] }[name]||['#f5f7fb','rgba(59,130,246,.08)','rgba(34,197,94,.05)']; document.body.style.background=`radial-gradient(1200px 800px at 100% -10%,${t[1]},transparent 60%),radial-gradient(1000px 800px at -20% 120%,${t[2]},transparent 50%),${t[0]}`; }
  switchTheme(el.theme.value);

  function setMode(m){ mode=m; el.mode.textContent=(m==='pomo'?'Pomodoro':m==='short'?'Pausa breve':'Pausa lunga'); total=(m==='pomo'?+el.pomo.value:m==='short'?+el.short.value:+el.long.value)*60; left=total; setBar(); updateClock(); el.status.textContent='Pronto'; el.next.textContent=(m==='pomo'?'Prossimo: Pausa breve':'Prossimo: Pomodoro'); }
  function updateClock(){ el.clock.textContent=fmt(left); title(`${el.mode.textContent} ${fmt(left)}`); }
  function start(){ if(running) return; running=true; el.status.textContent='In corso'; uiSound(900,0.05); const t0=Date.now(), l0=left; interval=setInterval(()=>{ const dt=((Date.now()-t0)/1000)|0; left=l0-dt; if(left<=0){ left=0; setBar(); endPhase(); } updateClock(); setBar(); },250); }
  function pause(){ if(!running) { uiSound(500,0.04); return; } running=false; clearInterval(interval); interval=null; el.status.textContent='In pausa'; uiSound(500,0.04); }
  function reset(){ pause(); left=total; setBar(); updateClock(); el.status.textContent='Pronto'; uiSound(300,0.05); }
  function ring(){ try{ el.ding.volume=+el.vol.value; el.ding.currentTime=0; el.ding.play(); }catch(_){} }
  function notify(msg){ if(!('Notification' in window)) return; if(Notification.permission==='granted'){ new Notification('Pomodoro Pro',{body:msg}); } else if(Notification.permission!=='denied'){ Notification.requestPermission(); } }
  let flash=null; function flashTitle(msg){ if(!el.titleflash.checked) return; clearInterval(flash); let on=false; flash=setInterval(()=>{ document.title=on? '🔔 '+msg : '🍅 '+msg; on=!on; },800); setTimeout(()=>{ clearInterval(flash); title(msg); },12000); }
  function nextPhase(){ if(mode==='pomo'){ if(el.longEvery.checked && (cycles%4===0)){ setMode('long'); } else { setMode('short'); } } else { if(mode==='long'){ cycles=1; } else { cycles++; } setMode('pomo'); } el.cycles.textContent=`Ciclo ${mode==='pomo'?cycles:cycles-1} di 4`; if(el.autoNext.checked) start(); }
  function endPhase(){ pause(); if(el.bell.checked) ring(); if(el.notify.checked) notify(`${el.mode.textContent} finito`); flashTitle(`${el.mode.textContent} finito`); if(el.autoBreak.checked || mode!=='pomo') nextPhase(); }
  function setSpotify(url){ try{ const u=new URL(url); const [type,id]=u.pathname.split('/').filter(Boolean); if(!id) return; el.spotify.src=`https://open.spotify.com/embed/${type}/${id}`; }catch(e){} }

  // events
  el.start.onclick=()=>{ start(); };
  el.pause.onclick=()=>{ pause(); };
  el.reset.onclick=()=>{ reset(); };
  el.skip.onclick=()=>{ uiSound(650,0.04); endPhase(); };
  ['pomo','short','long','autoNext','autoBreak','longEvery','bell','notify','titleflash','uiSounds','vol','theme'].forEach(k=>el[k].addEventListener('input',()=>{ if(k==='vol') el.voltxt.textContent=`Vol ${Math.round((+el.vol.value)*100)}%`; if(k==='theme') switchTheme(el.theme.value); if(['pomo','short','long'].includes(k)) uiSound(700,0.03); save(); }));
  el.spotifyUrl.addEventListener('change',()=>{ setSpotify(el.spotifyUrl.value); save(); uiSound(750,0.04); });
  el.compactBtn.onclick=()=>{ document.body.classList.toggle('compact'); el.compactBtn.textContent=document.body.classList.contains('compact')?'Estesa':'Compatta'; save(); uiSound(600,0.04); };
  el.exportBtn.onclick=()=>{ const data=localStorage.getItem('pomo_pro_v3')||'{}'; const blob=new Blob([data],{type:'application/json'}); const a=document.createElement('a'); a.href=URL.createObjectURL(blob); a.download='pomodoro-pro-settings.json'; a.click(); uiSound(820,0.05); };
  el.importBtn.onclick=()=>{ const i=document.createElement('input'); i.type='file'; i.accept='application/json'; i.onchange=()=>{ const f=i.files[0]; if(!f) return; const fr=new FileReader(); fr.onload=()=>{ try{ localStorage.setItem('pomo_pro_v3',fr.result); location.reload(); }catch(e){ alert('File non valido'); } }; fr.readAsText(f); }; i.click(); uiSound(400,0.04); };
  window.addEventListener('keydown',e=>{ if(e.code==='Space'){ e.preventDefault(); (running? pause:start)(); } if(e.key==='r'||e.key==='R'){ reset(); } if(e.key==='n'||e.key==='N'){ uiSound(650,0.04); endPhase(); } });

  // init
  function applyThemeFromSelect(){ switchTheme(el.theme.value); }
  applyThemeFromSelect();
  setMode('pomo'); updateClock(); setBar(); title('Pronto');
})();
</script>
</body>
</html>


