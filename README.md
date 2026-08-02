<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="robots" content="noindex, nofollow">
<title>Panel · Corazón para Ganar</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.min.js"></script>
<style>
:root{
  --marino:#0a1f38; --marino-d:#061527; --marino-l:#12304f;
  --oro:#c9a227; --oro-h:#e0b62e; --oro-soft:rgba(201,162,39,.10);
  --blanco:#ffffff;
  --fondo:#f4f6f9;
  --borde:#e6eaf0;
  --txt:#0d2137; --txt2:#5b6b7d; --txt3:#93a1b0;
  --err:#c0392b; --err-bg:#fdf0ee;
}
*{box-sizing:border-box;margin:0;padding:0}
body{background:var(--fondo);color:var(--txt);font-family:'Inter',sans-serif;-webkit-font-smoothing:antialiased}

.layout{display:flex;min-height:100vh}

/* ---------- SIDEBAR MARINO ---------- */
.sidebar{
  width:248px;flex-shrink:0;position:fixed;top:0;bottom:0;left:0;
  background:linear-gradient(170deg,var(--marino) 0%,var(--marino-d) 100%);
  display:flex;flex-direction:column;padding:26px 0;z-index:50;
}
.brand{padding:0 24px 26px;border-bottom:1px solid rgba(255,255,255,.08)}
.brand .esc{width:34px;height:34px;border-radius:8px;background:var(--oro);display:flex;align-items:center;
  justify-content:center;font-family:'Bebas Neue';font-size:1.3rem;color:var(--marino);margin-bottom:11px}
.brand h1{font-family:'Bebas Neue',sans-serif;font-size:1.42rem;letter-spacing:1.3px;color:#fff;line-height:1.05}
.brand h1 span{color:var(--oro)}
.brand .m{font-size:.68rem;color:rgba(255,255,255,.45);margin-top:5px;letter-spacing:.3px}

nav{padding:18px 14px;flex:1}
nav a{display:flex;align-items:center;gap:11px;padding:11px 14px;border-radius:9px;margin-bottom:3px;
  color:rgba(255,255,255,.62);text-decoration:none;font-size:.855rem;font-weight:500;transition:all .18s}
nav a:hover{background:rgba(255,255,255,.06);color:#fff}
nav a.on{background:var(--oro);color:var(--marino);font-weight:600}
nav a .ic{width:17px;height:17px;flex-shrink:0;opacity:.9}
nav .sep{font-size:.6rem;text-transform:uppercase;letter-spacing:1.2px;color:rgba(255,255,255,.28);
  padding:16px 14px 7px;font-weight:700}

.side-foot{padding:0 20px}
.side-card{background:rgba(255,255,255,.05);border:1px solid rgba(255,255,255,.09);border-radius:11px;padding:14px}
.side-card .l{font-size:.6rem;text-transform:uppercase;letter-spacing:1px;color:rgba(255,255,255,.4);font-weight:700}
.side-card .v{font-family:'Bebas Neue';font-size:1.5rem;color:var(--oro);letter-spacing:.5px;margin-top:3px}
.side-card .s{font-size:.72rem;color:rgba(255,255,255,.5);margin-top:2px}
.side-btn{width:100%;margin-top:11px;background:transparent;border:1px solid rgba(255,255,255,.22);color:rgba(255,255,255,.8);
  font-family:'Inter';font-size:.78rem;font-weight:600;padding:9px;border-radius:8px;cursor:pointer;transition:all .18s}
.side-btn:hover{background:var(--oro);border-color:var(--oro);color:var(--marino)}

/* ---------- CONTENIDO ---------- */
.main{margin-left:248px;flex:1;min-width:0}
.topbar{background:var(--blanco);border-bottom:1px solid var(--borde);padding:17px 32px;
  display:flex;justify-content:space-between;align-items:center;gap:16px;flex-wrap:wrap;
  position:sticky;top:0;z-index:40}
.topbar h2{font-family:'Bebas Neue',sans-serif;font-size:1.5rem;letter-spacing:1px;color:var(--txt)}
.topbar .d{font-size:.76rem;color:var(--txt3);margin-top:1px}
.pill{display:inline-flex;align-items:center;gap:7px;background:var(--marino);color:#fff;
  border-radius:100px;padding:8px 17px;font-size:.78rem;font-weight:500}
.pill .dot{width:7px;height:7px;border-radius:50%;background:#4ade80;box-shadow:0 0 0 3px rgba(74,222,128,.25)}
.pill b{color:var(--oro);font-weight:600}

.demo-bar{background:var(--oro);color:var(--marino);padding:10px 32px;font-size:.79rem;font-weight:600;display:none}
.content{padding:26px 32px 60px;max-width:1500px}

.sec{margin-bottom:34px;scroll-margin-top:82px}
.sec-h{display:flex;align-items:baseline;gap:12px;margin-bottom:5px}
.sec-h h3{font-family:'Bebas Neue',sans-serif;font-size:1.32rem;letter-spacing:1.1px;color:var(--txt)}
.niv{font-size:.58rem;background:var(--oro-soft);color:#8a6f14;padding:4px 9px;border-radius:100px;
  letter-spacing:.9px;font-weight:700;border:1px solid rgba(201,162,39,.25)}
.sec-d{font-size:.81rem;color:var(--txt3);margin-bottom:15px}

.grid{display:grid;gap:16px}
.g4{grid-template-columns:repeat(4,1fr)}
.g2{grid-template-columns:repeat(2,1fr)}
.g23{grid-template-columns:1.35fr 1fr}
@media(max-width:1150px){.g4{grid-template-columns:repeat(2,1fr)}.g23{grid-template-columns:1fr}}
@media(max-width:760px){.g4,.g2,.g23{grid-template-columns:1fr}}

.card{background:var(--blanco);border:1px solid var(--borde);border-radius:13px;padding:20px 22px;
  box-shadow:0 1px 2px rgba(13,33,55,.04);transition:box-shadow .2s}
.card:hover{box-shadow:0 6px 18px rgba(13,33,55,.07)}
.card.hero{border-top:3px solid var(--oro)}
.card.marino{background:linear-gradient(150deg,var(--marino) 0%,var(--marino-d) 100%);border-color:var(--marino)}
.card.marino .lbl{color:rgba(255,255,255,.5)}
.card.marino .val{color:#fff}
.card.marino .foot{color:rgba(255,255,255,.6)}

.lbl{font-size:.665rem;text-transform:uppercase;letter-spacing:1.05px;color:var(--txt3);font-weight:700}
.kpi .val{font-family:'Bebas Neue',sans-serif;font-size:2.9rem;line-height:1.03;margin-top:7px;letter-spacing:.5px}
.kpi .val.oro{color:var(--oro)}
.kpi .foot{font-size:.755rem;color:var(--txt2);margin-top:5px;line-height:1.4}

.bar-out{height:26px;background:#eef1f5;border-radius:100px;overflow:hidden;margin:13px 0 9px}
.bar-in{height:100%;background:linear-gradient(90deg,var(--oro),var(--oro-h));border-radius:100px;
  transition:width 1.2s cubic-bezier(.2,.8,.3,1);display:flex;align-items:center;justify-content:flex-end;
  padding-right:11px;font-size:.7rem;font-weight:700;color:var(--marino)}
.bar-meta{display:flex;justify-content:space-between;font-size:.78rem;color:var(--txt2)}
.bar-meta b{color:var(--txt)}

.chart-box{position:relative;height:262px}
.chart-box.tall{height:296px}

table{width:100%;border-collapse:collapse;font-size:.845rem}
th{text-align:left;font-size:.645rem;text-transform:uppercase;letter-spacing:1px;color:var(--txt3);
  padding:10px 11px;border-bottom:1.5px solid var(--borde);font-weight:700}
td{padding:11px;border-bottom:1px solid #f1f4f8;color:var(--txt2)}
tbody tr:hover{background:#fafbfd}
td.n{font-family:'Bebas Neue',sans-serif;font-size:1.18rem;color:var(--txt);letter-spacing:.4px}
td.id{color:var(--txt);font-weight:600}
td.tel{font-variant-numeric:tabular-nums;letter-spacing:.3px;color:var(--txt3)}
tr:last-child td{border-bottom:none}
.tag{display:inline-block;padding:3px 10px;border-radius:100px;font-size:.665rem;font-weight:700}
.t-open{background:#e7f7ed;color:#15803d}
.t-fin{background:#f1f4f8;color:var(--txt3)}
.up{color:#15803d}.down{color:var(--err)}

.note{font-size:.79rem;color:var(--txt2);margin-top:13px;line-height:1.62;padding-top:13px;border-top:1px solid #f1f4f8}
.note b{color:var(--txt)}
.alert{background:var(--err-bg);border:1px solid #f5d5cf;border-left:3px solid var(--err);color:#8c2d20;
  border-radius:11px;padding:16px 20px;font-size:.845rem;margin-top:18px}
.alert b{color:var(--err)}
.alert code{background:rgba(192,57,43,.09);padding:1px 6px;border-radius:4px;font-size:.94em}
.privado{display:inline-flex;align-items:center;gap:6px;background:#f1f4f8;color:var(--txt2);
  font-size:.68rem;font-weight:600;padding:4px 10px;border-radius:100px;margin-top:8px}

.dorm-list{max-height:250px;overflow-y:auto}
.dorm-list::-webkit-scrollbar{width:7px}
.dorm-list::-webkit-scrollbar-track{background:#f6f8fa}
.dorm-list::-webkit-scrollbar-thumb{background:#d5dce4;border-radius:10px}

.loading{display:flex;flex-direction:column;align-items:center;justify-content:center;height:100vh;color:var(--txt2);font-size:.9rem}
.spin{width:34px;height:34px;border:3px solid #e6eaf0;border-top-color:var(--oro);border-radius:50%;
  animation:sp .8s linear infinite;margin-bottom:16px}
@keyframes sp{to{transform:rotate(360deg)}}
#app{display:none}
.pie{text-align:center;font-size:.76rem;color:var(--txt3);padding-top:22px;border-top:1px solid var(--borde);margin-top:30px}

@media(max-width:900px){
  .sidebar{position:static;width:100%;height:auto;padding:18px 0}
  .sidebar nav,.side-foot{display:none}
  .main{margin-left:0}
  .content,.topbar{padding-left:18px;padding-right:18px}
}
</style>
</head>
<body>

<div id="load" class="loading"><div class="spin"></div>Cargando datos del sorteo…</div>

<div id="app">
<div class="layout">

  <aside class="sidebar">
    <div class="brand">
      <div class="esc">CPG</div>
      <h1>CORAZÓN<br><span>PARA GANAR</span></h1>
      <div class="m">Panel operativo · 2026</div>
    </div>
    <nav id="nav">
      <div class="sep">Seguimiento</div>
      <a href="#meta" class="on"><svg class="ic" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="9"/><circle cx="12" cy="12" r="4"/><circle cx="12" cy="12" r="1" fill="currentColor"/></svg>Meta 2026</a>
      <a href="#diag"><svg class="ic" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M3 3v18h18"/><path d="M7 15l4-5 3 3 5-7"/></svg>Diagnóstico</a>
      <a href="#activo"><svg class="ic" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="9"/><path d="M12 7v5l3 2"/></svg>Sorteo activo</a>
      <a href="#contexto"><svg class="ic" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="4" width="18" height="16" rx="2"/><path d="M3 10h18M9 10v10"/></svg>Contexto</a>
      <div class="sep">Acciones</div>
      <a href="#dormidos"><svg class="ic" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M17 21v-2a4 4 0 00-4-4H6a4 4 0 00-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M22 11h-6"/></svg>Reactivar dormidos</a>
      <a href="#alertas"><svg class="ic" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M10.3 3.9L1.8 18a2 2 0 001.7 3h17a2 2 0 001.7-3L13.7 3.9a2 2 0 00-3.4 0z"/><path d="M12 9v4M12 17h.01"/></svg>Calidad del dato</a>
    </nav>
    <div class="side-foot">
      <div class="side-card">
        <div class="l">Avance a la meta</div>
        <div class="v" id="s-avance">—</div>
        <div class="s" id="s-avance-f">—</div>
        <button class="side-btn" onclick="location.reload()">Actualizar datos</button>
      </div>
    </div>
  </aside>

  <div class="main">
    <div id="demo-bar" class="demo-bar">
      MODO DEMO · datos simulados. Al publicarlo en GitHub Pages se conecta solo a tus hojas reales.
    </div>

    <div class="topbar">
      <div>
        <h2>Camino a los 1,000 grones</h2>
        <div class="d" id="tb-fecha">—</div>
      </div>
      <div class="pill"><span class="dot"></span><span id="hdr-sorteo">—</span></div>
    </div>

    <div class="content">

      <section class="sec" id="meta">
        <div class="sec-h"><h3>Meta 2026</h3><span class="niv">NIVEL 1</span></div>
        <div class="sec-d">Lo único que decide si llegas a 1,000. Si solo miras cuatro números, son estos.</div>
        <div class="grid g4">
          <div class="card kpi hero"><div class="lbl">Grones únicos</div><div class="val oro" id="k-unicos">—</div><div class="foot">personas distintas, no participaciones</div></div>
          <div class="card kpi"><div class="lbl">Nuevos en sorteo activo</div><div class="val" id="k-nuevos">—</div><div class="foot" id="k-nuevos-f">—</div></div>
          <div class="card kpi"><div class="lbl">Faltan para 1,000</div><div class="val" id="k-faltan">—</div><div class="foot" id="k-ritmo">—</div></div>
          <div class="card kpi marino"><div class="lbl">Conversión del canal</div><div class="val" id="k-conv">—</div><div class="foot" id="k-conv-f">—</div></div>
        </div>
        <div class="card" style="margin-top:16px">
          <div class="bar-meta"><b id="p-pct">—</b><span id="p-eta">—</span></div>
          <div class="bar-out"><div class="bar-in" id="p-bar" style="width:0%"></div></div>
          <div class="bar-meta"><span id="p-txt">—</span><span>meta 1,000 · 31 dic 2026</span></div>
        </div>
      </section>

      <section class="sec" id="diag">
        <div class="sec-h"><h3>Diagnóstico</h3><span class="niv">NIVEL 2</span></div>
        <div class="sec-d">Por qué el número de arriba se mueve o se queda quieto.</div>
        <div class="grid g2">
          <div class="card"><div class="lbl">Nuevos vs. recurrentes por sorteo</div>
            <div class="chart-box" style="margin-top:14px"><canvas id="c-mix"></canvas></div>
            <div class="note">Solo la barra dorada mueve la meta. La gris es la misma gente volviendo.</div></div>
          <div class="card"><div class="lbl">Grones únicos acumulados</div>
            <div class="chart-box" style="margin-top:14px"><canvas id="c-acum"></canvas></div>
            <div class="note">La distancia contra la línea punteada es lo que falta por captar.</div></div>
        </div>
        <div class="card" style="margin-top:16px">
          <div class="lbl" style="margin-bottom:12px">Detalle por sorteo</div>
          <table><thead><tr>
            <th>Sorteo</th><th>Estado</th><th>Participaciones</th><th>Nuevos</th><th>Recurrentes</th><th>Retención</th><th>Base acum.</th>
          </tr></thead><tbody id="tbl-sorteos"></tbody></table>
          <div class="note" id="nota-ret"></div>
        </div>
        <div class="grid g23" style="margin-top:16px">
          <div class="card"><div class="lbl">Fuga: ¿en cuántos sorteos participó cada grone?</div>
            <div class="chart-box" style="margin-top:14px"><canvas id="c-leal"></canvas></div>
            <div class="note" id="nota-leal"></div></div>
          <div class="card" id="dormidos"><div class="lbl">Dormidos del sorteo activo</div>
            <div style="font-size:.79rem;color:var(--txt2);margin:9px 0 11px;line-height:1.5" id="dorm-resumen">—</div>
            <div class="dorm-list"><table><thead><tr><th>ID grone</th><th>Teléfono</th><th>Último</th></tr></thead><tbody id="tbl-dorm"></tbody></table></div>
            <div class="privado">
              <svg width="12" height="12" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><rect x="4" y="11" width="16" height="10" rx="2"/><path d="M8 11V7a4 4 0 018 0v4"/></svg>
              Teléfonos enmascarados · busca el ID en tu Sheet
            </div>
          </div>
        </div>
      </section>

      <section class="sec" id="activo">
        <div class="sec-h"><h3>Sorteo activo</h3><span class="niv">NIVEL 2</span></div>
        <div class="sec-d">Para reaccionar mientras el sorteo sigue abierto, no después.</div>
        <div class="grid g4">
          <div class="card kpi hero"><div class="lbl">Participaciones</div><div class="val oro" id="a-part">—</div><div class="foot" id="a-prem">—</div></div>
          <div class="card kpi"><div class="lbl">Días restantes</div><div class="val" id="a-dias">—</div><div class="foot" id="a-fecha">—</div></div>
          <div class="card kpi"><div class="lbl">Ritmo diario</div><div class="val" id="a-ritmo">—</div><div class="foot">participaciones por día</div></div>
          <div class="card kpi"><div class="lbl">vs. sorteo anterior</div><div class="val" id="a-vs">—</div><div class="foot" id="a-vs-f">mismo día del ciclo</div></div>
        </div>
        <div class="card" style="margin-top:16px">
          <div class="lbl">Curva acumulada por día del ciclo</div>
          <div class="chart-box tall" style="margin-top:14px"><canvas id="c-curva"></canvas></div>
        </div>
      </section>

      <section class="sec" id="contexto">
        <div class="sec-h"><h3>Contexto</h3><span class="niv">NIVEL 3</span></div>
        <div class="sec-d">Se revisa una vez al mes. Útil, pero no decide nada por sí solo.</div>
        <div class="grid g2">
          <div class="card"><div class="lbl">Participaciones por sorteo</div>
            <div class="chart-box" style="margin-top:14px"><canvas id="c-tot"></canvas></div>
            <div class="note">El dato que más se mira y menos informa: puede subir sin que la base crezca.</div></div>
          <div class="card"><div class="lbl" style="margin-bottom:12px">Premio vs. participación</div>
            <table><thead><tr><th>Sorteo</th><th>Premio</th><th>Particip.</th></tr></thead><tbody id="tbl-premios"></tbody></table>
            <div class="note">Con 4 sorteos aún no concluye nada. Hacia S08 te dirá qué camiseta jala más.</div></div>
        </div>
      </section>

      <div id="alertas"></div>
      <div class="pie" id="pie"></div>
    </div>
  </div>
</div>
</div>

<script>
/* ============================================================
   Panel CPG — lee Google Sheets. Si corre en file:// o falla
   el fetch, entra en MODO DEMO con datos simulados.
   Teléfonos enmascarados: el panel vive en un repo público.
   ============================================================ */
const BASE="https://docs.google.com/spreadsheets/d/e/2PACX-1vSVSgHlway102guhsuSOkbVIZyBLybfeCAJpAEAUYf4gp3ir25Av8LHp41PSAIc81TuWHnSgIu7jXuv/pub?single=true&output=csv";
const GID={sorteos:"98731452",hinchas:"1052193857",part:"396133425"};
const META=1000;
const CANAL_WA=466;            // <-- actualizar a mano cuando crezca el canal
const HOY=new Date();

const ORO="#c9a227",MARINO="#0a1f38",GRIS="#cfd8e3",TXT2="#5b6b7d",LINEA="#eef1f5";

/* ---------- utilidades ---------- */
function parseCSV(t){
  const rows=[];let row=[],f="",q=false;
  for(let i=0;i<t.length;i++){const c=t[i];
    if(q){ if(c==='"'){ if(t[i+1]==='"'){f+='"';i++;} else q=false; } else f+=c; }
    else { if(c==='"')q=true;
      else if(c===','){row.push(f);f="";}
      else if(c==='\n'){row.push(f);rows.push(row);row=[];f="";}
      else if(c!=='\r')f+=c; }
  }
  if(f!==""||row.length){row.push(f);rows.push(row);}
  return rows.filter(r=>r.some(x=>x.trim()!==""));
}
async function getCSV(gid){
  const r=await fetch(`${BASE}&gid=${gid}&_=${Date.now()}`);
  if(!r.ok)throw new Error("HTTP "+r.status);
  return parseCSV(await r.text());
}
function fecha(s){
  if(!s)return null;
  const p=s.trim().split(/\s+/)[0].split("/");
  if(p.length<3)return null;
  const d=new Date(+p[2],+p[1]-1,+p[0]);
  return isNaN(d)?null:d;
}
const MES={enero:0,febrero:1,marzo:2,abril:3,mayo:4,junio:5,julio:6,agosto:7,setiembre:8,septiembre:8,octubre:9,noviembre:10,diciembre:11};
function fechaLarga(s){
  if(!s)return null;
  const m=s.toLowerCase().match(/(\d{1,2})\s+de\s+([a-zé]+)(?:\s+de\s+(\d{4}))?/);
  return m?new Date(m[3]?+m[3]:2026,MES[m[2]]??0,+m[1]):null;
}
const dias=(a,b)=>Math.round((b-a)/86400000);
const fmt=n=>n.toLocaleString("es-PE");
/* enmascara el teléfono: 987654321 -> 9•• ••• 321 */
function mask(t){
  const s=String(t||"").replace(/\D/g,"");
  return s.length<4?"—":s[0]+"•• ••• "+s.slice(-3);
}

Chart.defaults.color=TXT2;
Chart.defaults.font.family="Inter";
Chart.defaults.font.size=11;
const EJE={grid:{color:LINEA},ticks:{color:TXT2},border:{display:false}};
const EJEX={grid:{display:false},ticks:{color:TXT2},border:{color:"#e6eaf0"}};
const LEG={position:"bottom",labels:{boxWidth:9,boxHeight:9,usePointStyle:true,pointStyle:"circle",padding:16,color:TXT2}};
const TIP={backgroundColor:MARINO,padding:11,cornerRadius:8,titleFont:{family:"Inter",size:12},
  bodyFont:{family:"Inter",size:12},boxPadding:4};

/* ---------- datos DEMO ---------- */
let seed=20260801;
const rnd=()=>{seed=(seed*1103515245+12345)&0x7fffffff;return seed/0x7fffffff;};
function demoData(){
  const sorteos=[
    {id:"S02",fecha:new Date(2026,4,24),gratuito:"La del Centenario",estado:"finalizado",n:198,ini:new Date(2026,3,28),fin:new Date(2026,4,23),recur:0},
    {id:"S03",fecha:new Date(2026,5,21),gratuito:"La Piel del 34",estado:"finalizado",n:226,ini:new Date(2026,5,1),fin:new Date(2026,5,20),recur:.60},
    {id:"S04",fecha:new Date(2026,6,26),gratuito:"La Piel del Centenario",estado:"finalizado",n:201,ini:new Date(2026,5,24),fin:new Date(2026,6,25),recur:.66},
    {id:"S05",fecha:new Date(2026,7,23),gratuito:"La Piel del 2004",estado:"abierto",n:42,ini:new Date(2026,6,29),fin:new Date(2026,7,1),recur:.81},
    {id:"S06",fecha:new Date(2026,8,20),gratuito:"pendiente",estado:"proximo",n:0}
  ];
  const parts=[],pool=[];let next=100;
  sorteos.filter(s=>s.n>0).forEach(s=>{
    const nRec=Math.round(s.n*s.recur),nNew=s.n-nRec,eleg=new Set();
    const mez=pool.slice().sort(()=>rnd()-.5);
    for(let i=0;i<nRec&&i<mez.length;i++)eleg.add(mez[i]);
    for(let i=0;i<nNew;i++){const g=String(next++);pool.push(g);eleg.add(g);}
    const span=Math.max(1,dias(s.ini,s.fin));
    [...eleg].forEach(g=>{
      const r=rnd(),off=r<.45?Math.floor(rnd()*span*.25):Math.floor(span*.5+rnd()*span*.5);
      const d=new Date(s.ini);d.setDate(d.getDate()+Math.min(off,span));
      parts.push({grone:g,sorteo:s.id,tel:"9"+String(10000000+(+g*7919)%89999999).slice(0,8),fecha:d,vip:false});
    });
  });
  return {sorteos,parts,tel:Object.fromEntries(parts.map(p=>[p.grone,p.tel]))};
}

/* ---------- render ---------- */
function render(sorteos,parts,tel,demo){
  if(demo)document.getElementById("demo-bar").style.display="block";

  const orden=sorteos.map(s=>s.id).filter(id=>parts.some(p=>p.sorteo===id));
  const activo=sorteos.find(s=>s.estado==="abierto")||sorteos.filter(s=>s.estado==="finalizado").pop();

  const vistos=new Set(),stats=[];
  orden.forEach((id,i)=>{
    const ps=parts.filter(p=>p.sorteo===id);
    const gr=new Set(ps.map(p=>p.grone).filter(Boolean));
    let nuevos=0;gr.forEach(g=>{if(!vistos.has(g))nuevos++;});
    const prev=i>0?new Set(parts.filter(p=>p.sorteo===orden[i-1]).map(p=>p.grone)):null;
    let vuelven=0;if(prev)prev.forEach(g=>{if(gr.has(g))vuelven++;});
    gr.forEach(g=>vistos.add(g));
    const so=sorteos.find(s=>s.id===id)||{};
    stats.push({id,total:ps.length,nuevos,recur:gr.size-nuevos,
      reten:prev&&prev.size?vuelven/prev.size:null,acum:vistos.size,
      estado:so.estado||"",premio:so.gratuito||"—"});
  });

  const totalUnicos=vistos.size,faltan=Math.max(0,META-totalUnicos),pct=Math.min(100,totalUnicos/META*100);
  const primera=parts.map(p=>p.fecha).filter(Boolean).sort((a,b)=>a-b)[0];
  const meses=primera?Math.max(1,dias(primera,HOY)/30.4):1;
  const nuevosMes=totalUnicos/meses,mesesFalta=nuevosMes>0?faltan/nuevosMes:null;
  let eta="—";
  if(mesesFalta&&isFinite(mesesFalta)){
    const d=new Date(HOY);d.setMonth(d.getMonth()+Math.ceil(mesesFalta));
    eta=d.toLocaleDateString("es-PE",{month:"long",year:"numeric"});
  }
  const idA=activo?activo.id:orden.at(-1);
  const sa=stats.find(s=>s.id===idA)||{total:0,nuevos:0,id:idA};

  document.getElementById("tb-fecha").textContent=
    HOY.toLocaleDateString("es-PE",{weekday:"long",day:"numeric",month:"long",year:"numeric"});
  if(activo)document.getElementById("hdr-sorteo").innerHTML=
    `<b>${activo.id}</b> · ${activo.gratuito} · ${activo.estado}`;
  document.getElementById("s-avance").textContent=pct.toFixed(1)+"%";
  document.getElementById("s-avance-f").textContent=`${fmt(totalUnicos)} de ${fmt(META)} grones`;

  document.getElementById("k-unicos").textContent=fmt(totalUnicos);
  document.getElementById("k-nuevos").textContent=fmt(sa.nuevos);
  document.getElementById("k-nuevos-f").textContent=`de ${fmt(sa.total)} participaciones en ${sa.id}`;
  document.getElementById("k-faltan").textContent=fmt(faltan);
  document.getElementById("k-ritmo").textContent=`captas ~${Math.round(nuevosMes)} grones nuevos/mes`;
  document.getElementById("k-conv").textContent=Math.round(totalUnicos/CANAL_WA*100)+"%";
  document.getElementById("k-conv-f").textContent=`${fmt(totalUnicos)} de ${CANAL_WA} del canal han participado`;
  document.getElementById("p-pct").textContent=pct.toFixed(1)+"% de la meta";
  document.getElementById("p-eta").textContent="Llegada estimada: "+eta;
  document.getElementById("p-txt").textContent=`${fmt(totalUnicos)} grones únicos`;
  setTimeout(()=>{const b=document.getElementById("p-bar");b.style.width=pct+"%";b.textContent=fmt(totalUnicos);},200);

  const cls={abierto:"t-open",finalizado:"t-fin",proximo:"t-fin"};
  document.getElementById("tbl-sorteos").innerHTML=stats.map(s=>`
    <tr><td class="id">${s.id}</td>
    <td><span class="tag ${cls[s.estado]||"t-fin"}">${s.estado||"—"}</span></td>
    <td class="n">${fmt(s.total)}</td>
    <td class="n" style="color:${ORO}">${fmt(s.nuevos)}</td>
    <td class="n">${fmt(s.recur)}</td>
    <td class="n">${s.reten===null?"—":Math.round(s.reten*100)+"%"}</td>
    <td class="n">${fmt(s.acum)}</td></tr>`).join("");
  const rp=stats.filter(s=>s.reten!==null);
  if(rp.length){
    const r=rp.reduce((a,b)=>a+b.reten,0)/rp.length;
    document.getElementById("nota-ret").innerHTML=
      `Retención promedio <b style="color:${ORO}">${Math.round(r*100)}%</b>: de cada 10 grones que participan, ${Math.round(r*10)} vuelven al siguiente sorteo. Las participaciones pueden subir sin que la base crezca — por eso la columna que importa es <b>Nuevos</b>.`;
  }

  new Chart(document.getElementById("c-mix"),{type:"bar",data:{labels:stats.map(s=>s.id),datasets:[
    {label:"Nuevos",data:stats.map(s=>s.nuevos),backgroundColor:ORO,borderRadius:6,barPercentage:.62},
    {label:"Recurrentes",data:stats.map(s=>s.recur),backgroundColor:GRIS,borderRadius:6,barPercentage:.62}]},
    options:{maintainAspectRatio:false,plugins:{legend:LEG,tooltip:TIP},
      scales:{x:{stacked:true,...EJEX},y:{stacked:true,...EJE,beginAtZero:true}}}});

  new Chart(document.getElementById("c-acum"),{type:"line",data:{labels:stats.map(s=>s.id),datasets:[
    {label:"Grones únicos",data:stats.map(s=>s.acum),borderColor:ORO,backgroundColor:"rgba(201,162,39,.13)",
     fill:true,tension:.32,pointRadius:4.5,pointBackgroundColor:"#fff",pointBorderColor:ORO,pointBorderWidth:2.5,borderWidth:2.5},
    {label:"Meta 1,000",data:stats.map(()=>META),borderColor:MARINO,borderDash:[6,5],pointRadius:0,borderWidth:1.5}]},
    options:{maintainAspectRatio:false,plugins:{legend:LEG,tooltip:TIP},
      scales:{x:EJEX,y:{...EJE,beginAtZero:true,suggestedMax:META*1.05}}}});

  const freq={};
  parts.forEach(p=>{if(p.grone)(freq[p.grone]=freq[p.grone]||new Set()).add(p.sorteo);});
  const dist={};Object.values(freq).forEach(s=>dist[s.size]=(dist[s.size]||0)+1);
  const ks=Object.keys(dist).map(Number).sort((a,b)=>a-b);
  new Chart(document.getElementById("c-leal"),{type:"bar",
    data:{labels:ks.map(k=>k+(k===1?" sorteo":" sorteos")),datasets:[{data:ks.map(k=>dist[k]),
      backgroundColor:ks.map(k=>k===1?"#e8a9a0":ORO),borderRadius:6,barPercentage:.6}]},
    options:{maintainAspectRatio:false,plugins:{legend:{display:false},tooltip:TIP},
      scales:{x:EJEX,y:{...EJE,beginAtZero:true}}}});
  const unaVez=dist[1]||0;
  document.getElementById("nota-leal").innerHTML=
    `<b style="color:var(--err)">${fmt(unaVez)} grones (${Math.round(unaVez/totalUnicos*100)}%)</b> participaron una sola vez y no volvieron. Ya te dieron su número: recuperarlos cuesta mucho menos que captar nuevos.`;

  const enActivo=new Set(parts.filter(p=>p.sorteo===idA).map(p=>p.grone));
  const ultimo={};parts.forEach(p=>{if(p.grone&&p.sorteo>(ultimo[p.grone]||""))ultimo[p.grone]=p.sorteo;});
  const dorm=Object.keys(freq).filter(g=>!enActivo.has(g)).sort((a,b)=>(ultimo[b]||"").localeCompare(ultimo[a]||""));
  document.getElementById("dorm-resumen").innerHTML=
    `<b style="color:${ORO};font-size:1.05rem">${fmt(dorm.length)}</b> grones registrados aún no participan en ${idA}. Lista lista para difusión.`;
  document.getElementById("tbl-dorm").innerHTML=dorm.slice(0,150).map(g=>
    `<tr><td class="id">${g}</td><td class="tel">${mask(tel[g])}</td><td>${ultimo[g]||"—"}</td></tr>`).join("")||
    `<tr><td colspan="3">Sin dormidos.</td></tr>`;

  document.getElementById("a-part").textContent=fmt(sa.total);
  document.getElementById("a-prem").textContent=activo?activo.gratuito:"—";
  if(activo&&activo.fecha){
    document.getElementById("a-dias").textContent=Math.max(0,dias(HOY,activo.fecha));
    document.getElementById("a-fecha").textContent="sorteo el "+activo.fecha.toLocaleDateString("es-PE",{day:"numeric",month:"long"});
  }
  function curva(id){
    const ps=parts.filter(p=>p.sorteo===id&&p.fecha).sort((a,b)=>a.fecha-b.fecha);
    if(!ps.length)return[];
    const d0=ps[0].fecha,out=[];let acc=0;
    const maxD=dias(d0,ps.at(-1).fecha);
    for(let d=0;d<=maxD;d++){acc+=ps.filter(p=>dias(d0,p.fecha)===d).length;out.push(acc);}
    return out;
  }
  const pa=parts.filter(p=>p.sorteo===idA&&p.fecha).sort((a,b)=>a.fecha-b.fecha);
  if(pa.length){
    const transc=Math.max(1,dias(pa[0].fecha,HOY)+1);
    document.getElementById("a-ritmo").textContent=(sa.total/transc).toFixed(1);
    const i=orden.indexOf(idA),idPrev=i>0?orden[i-1]:null;
    const cA=curva(idA),cP=idPrev?curva(idPrev):[];
    const labels=Array.from({length:Math.max(cA.length,cP.length)},(_,k)=>"Día "+(k+1));
    const ds=[{label:idA+" (activo)",data:cA,borderColor:ORO,backgroundColor:"rgba(201,162,39,.12)",
      fill:true,tension:.3,pointRadius:0,borderWidth:3}];
    if(cP.length)ds.push({label:idPrev,data:cP,borderColor:MARINO,borderDash:[5,4],tension:.3,pointRadius:0,borderWidth:2});
    new Chart(document.getElementById("c-curva"),{type:"line",data:{labels,datasets:ds},
      options:{maintainAspectRatio:false,interaction:{mode:"index",intersect:false},
        plugins:{legend:LEG,tooltip:TIP},scales:{x:EJEX,y:{...EJE,beginAtZero:true}}}});
    const d=cA.length-1,el=document.getElementById("a-vs");
    if(cP.length>d&&cP[d]>0){
      const diff=(cA[d]-cP[d])/cP[d]*100;
      el.textContent=(diff>=0?"+":"")+Math.round(diff)+"%";el.className="val "+(diff>=0?"up":"down");
      document.getElementById("a-vs-f").textContent=`${idPrev} iba en ${fmt(cP[d])} al día ${d+1}`;
    }else{el.textContent="—";document.getElementById("a-vs-f").textContent="sin comparable aún";}
  }

  new Chart(document.getElementById("c-tot"),{type:"bar",data:{labels:stats.map(s=>s.id),
    datasets:[{data:stats.map(s=>s.total),backgroundColor:MARINO,borderRadius:6,barPercentage:.55}]},
    options:{maintainAspectRatio:false,plugins:{legend:{display:false},tooltip:TIP},
      scales:{x:EJEX,y:{...EJE,beginAtZero:true}}}});
  document.getElementById("tbl-premios").innerHTML=stats.map(s=>
    `<tr><td class="id">${s.id}</td><td>${s.premio}</td><td class="n">${fmt(s.total)}</td></tr>`).join("");

  const al=[];
  if(!parts.some(p=>p.vip))al.push(`No hay <b>ninguna participación VIP</b> registrada. Las columnas <code>participa_vip</code>, <code>tipo_vip</code>, <code>nro_operación</code> y <code>monto_pagado</code> están vacías en las ${parts.length} filas.`);
  al.push(`Falta la columna <b>canal de origen</b> en Hinchas (WhatsApp / Instagram / Facebook / TikTok). Sin ella ningún panel te dice dónde invertir el esfuerzo.`);
  const sf=parts.filter(p=>!p.fecha).length;if(sf)al.push(`${sf} participaciones sin fecha válida — quedan fuera de las curvas de ritmo.`);
  document.getElementById("alertas").innerHTML=
    `<div class="alert"><b>Calidad del dato</b><ul style="margin:9px 0 0 18px;line-height:1.75">${al.map(x=>"<li>"+x+"</li>").join("")}</ul></div>`;

  document.getElementById("pie").textContent=
    `${fmt(parts.length)} participaciones · ${fmt(totalUnicos)} grones únicos · ${demo?"datos simulados":"actualizado "+new Date().toLocaleString("es-PE")}`;

  document.getElementById("load").style.display="none";
  document.getElementById("app").style.display="block";

  const links=[...document.querySelectorAll("#nav a")];
  const obs=new IntersectionObserver(es=>{
    es.forEach(e=>{if(e.isIntersecting)links.forEach(a=>a.classList.toggle("on",a.getAttribute("href")==="#"+e.target.id));});
  },{rootMargin:"-90px 0px -70% 0px"});
  document.querySelectorAll("section.sec").forEach(s=>obs.observe(s));
}

/* ---------- arranque ---------- */
(async function(){
  try{
    if(location.protocol==="file:")throw new Error("file://");
    const [rs,rp,rh]=await Promise.all([getCSV(GID.sorteos),getCSV(GID.part),getCSV(GID.hinchas)]);
    const sorteos=rs.slice(1).filter(r=>r[0]).map(r=>({id:r[0].trim(),fecha:fechaLarga(r[1]),
      gratuito:(r[2]||"").trim(),estado:(r[4]||"").trim().toLowerCase()})).sort((a,b)=>a.id.localeCompare(b.id));
    const parts=rp.slice(1).filter(r=>r[0]&&r[2]).map(r=>({grone:(r[1]||"").trim(),sorteo:(r[2]||"").trim(),
      tel:(r[3]||"").trim(),vip:((r[5]||"").trim().toUpperCase()==="SI"),fecha:fecha(r[10])}));
    const tel={};rh.slice(1).forEach(r=>{if(r[0])tel[r[0].trim()]=(r[1]||"").trim();});
    render(sorteos,parts,tel,false);
  }catch(e){
    const d=demoData();
    render(d.sorteos,d.parts,d.tel,true);
  }
})();
</script>
</body>
</html>
