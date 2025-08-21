<!doctype html>
<html lang="nl">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Interactieve Bingo Kaart — A1 t/m T20</title>
<style>
:root{
--bg:#0f172a; /* slate-900 */
--panel:#111827; /* gray-900 */
--panel-2:#0b1220; /* darker */
--text:#e5e7eb; /* gray-200 */
--muted:#94a3b8; /* slate-400 */
--primary:#22d3ee; /* cyan-400 */
--accent:#a78bfa; /* violet-400 */
--marked:#10b98133; /* emerald-500 at 20% */
--ring:#22d3ee66;
--border:#1f2937; /* gray-800 */
}
* { box-sizing: border-box }
html, body { height: 100% }
body{
margin:0; font-family: ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, Helvetica, Arial, "Apple Color Emoji", "Segoe UI Emoji";
background: radial-gradient(1200px 800px at 10% -10%, #0b1220 0, var(--bg) 60%);
color:var(--text);
display:flex; flex-direction:column; gap:16px; align-items:center; padding:24px;
}
header{
width:100%; max-width:1200px; display:flex; flex-wrap:wrap; gap:12px; align-items:center; justify-content:space-between;
}
.title{ font-size:clamp(20px, 2.8vw, 32px); font-weight:800; letter-spacing:0.3px }
.subtitle{ color:var(--muted); font-size:clamp(12px,1.5vw,14px) }
.controls{ display:flex; gap:8px; flex-wrap:wrap; align-items:center }
button, input[type="text"], select{
background:linear-gradient(180deg, #0f1a2b, var(--panel));
color:var(--text); border:1px solid var(--border); border-radius:12px; padding:10px 14px; font-weight:600; cursor:pointer;
box-shadow: inset 0 0 0 1px #00000033, 0 2px 8px #00000055; outline:none;
}
button:hover{ border-color:#334155; transform: translateY(-1px) }
button:active{ transform: translateY(0) }
button.primary{ border-color:var(--ring) }
input[type="text"]{ cursor:text; min-width:160px }


.board-wrap{
width:100%; max-width:1200px; background:linear-gradient(180deg, var(--panel), var(--panel-2));
border:1px solid var(--border); border-radius:18px; padding:16px; box-shadow: 0 10px 30px #00000066;
}
.legend{ display:flex; gap:16px; align-items:center; margin:4px 2px 12px; color:var(--muted); font-size:14px }
.legend .dot{ width:14px; height:14px; border-radius:6px; display:inline-block; background:var(--marked); border:1px solid #134e4a }


.grid{ display:grid; grid-template-columns: repeat(20, minmax(40px, 1fr)); gap:8px }
.cell{
aspect-ratio: 1 / 1; border:1px solid var(--border); border-radius:12px; display:grid; place-items:center; user-select:none;
font-weight:700; font-size:clamp(12px, 1.4vw, 18px); letter-spacing:0.3px;
background:linear-gradient(180deg, #0e1726, #0b1424);
position:relative; overflow:hidden; transition: transform .06s ease, border-color .2s ease;
}
.cell::after{
content:""; position:absolute; inset:0; background: radial-gradient(200px 120px at -20% -20%, #22d3ee18, transparent 60%);
pointer-events:none;
}
.cell:hover{ border-color:#324456; transform: translateY(-1px) }
.cell.marked{ background:linear-gradient(180deg, #06291f, #0d1f1a); border-color:#134e4a; }
.cell.marked .label{ text-decoration: line-through; color:#c7f3e7 }
.cell .label{ position:relative; z-index:2 }


.footer{
display:flex; justify-content:space-between; align-items:center; color:var(--muted); margin-top:12px; font-size:14px;
}
.count{ font-weight:800; color:var(--primary) }


/* Small screens: tighter gaps */
@media (max-width: 640px){
.grid{ gap:6px }
}


/* Print-friendly */
@media print{
body{ background:white; color:black }
.board-wrap{ box-shadow:none; background:white; border-color:#ddd }
.cell{ background:white }
.cell.marked{ background:#c7f3e7 }
header, .legend, .controls{ filter: grayscale(1) }
}
</style>
</head>
<body>
