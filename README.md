<!DOCTYPE html>
<!-- saved from url=(0049)file:///C:/Users/FENOMEN/Downloads/Map%20(1).html -->
<html lang="kk" data-theme="light"><head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8">

<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Шымкент — Қауіпсіздік мониторингі v7</title>
<link rel="stylesheet" href="./Шымкент — Қауіпсіздік мониторингі v7_files/leaflet.min.css">
<script src="./Шымкент — Қауіпсіздік мониторингі v7_files/leaflet.min.js.загружено"></script>
<link href="./Шымкент — Қауіпсіздік мониторингі v7_files/css2" rel="stylesheet">
<style>
:root {
  --bg-primary:#ffffff; --bg-secondary:#f8f9fb; --bg-tertiary:#f0f2f5;
  --text-primary:#1a2332; --text-secondary:#4a5568; --text-muted:#9aa5b4;
  --border:#e0e4ea; --border-light:#f4f6f8;
  --accent:#1565c0; --accent-dark:#0d47a1;
  --shadow:rgba(0,0,0,0.07); --shadow-md:rgba(0,0,0,0.12);
  --card-bg:#ffffff; --topbar-bg:#ffffff; --sidebar-bg:#ffffff;
  --input-bg:#f8f9fb; --chip-bg:#f8f9fb;
  --danger:#e53935; --warning:#fb8c00; --success:#2e7d32; --purple:#7b1fa2;
}
[data-theme="dark"] {
  --bg-primary:#1a1f2e; --bg-secondary:#141824; --bg-tertiary:#0f1219;
  --text-primary:#e8edf5; --text-secondary:#a0adb8; --text-muted:#5a6475;
  --border:#2a3245; --border-light:#1f2840;
  --shadow:rgba(0,0,0,0.3); --shadow-md:rgba(0,0,0,0.4);
  --card-bg:#1e2538; --topbar-bg:#141824; --sidebar-bg:#161b2a;
  --input-bg:#1a1f2e; --chip-bg:#1e2538;
}
* { margin:0; padding:0; box-sizing:border-box; }
body { font-family:'Rubik',sans-serif; background:var(--bg-tertiary); height:100vh; display:flex; flex-direction:column; overflow:hidden; color:var(--text-primary); transition:background .25s,color .25s; }

/* ============ TOPBAR ============ */
#topbar {
  background:var(--topbar-bg); border-bottom:1px solid var(--border); padding:0 14px; height:52px;
  display:flex; align-items:center; justify-content:space-between; gap:8px;
  flex-shrink:0; box-shadow:0 2px 8px var(--shadow); z-index:100; transition:background .25s,border-color .25s;
}
.logo { display:flex; align-items:center; gap:10px; font-weight:800; font-size:15px; color:var(--text-primary); white-space:nowrap; }
.logo-badge {
  background:linear-gradient(135deg,#1565c0,#0d47a1); color:#fff;
  font-size:11px; font-weight:700; padding:4px 10px; border-radius:20px;
  display:flex; align-items:center; gap:5px;
}
.logo-pulse { width:7px; height:7px; border-radius:50%; background:#4fc3f7; animation:logoPulse 2s infinite; }
@keyframes logoPulse { 0%,100%{opacity:1;box-shadow:0 0 0 0 rgba(79,195,247,.4)} 50%{opacity:.8;box-shadow:0 0 0 5px rgba(79,195,247,0)} }
.topbar-stats { display:flex; gap:4px; flex:1; justify-content:center; overflow:hidden; }
.ts-chip { display:flex; align-items:center; gap:5px; background:var(--chip-bg); border:1px solid var(--border); border-radius:7px; padding:4px 9px; font-size:11px; color:var(--text-secondary); white-space:nowrap; transition:background .25s; }
.ts-chip .dot { width:7px; height:7px; border-radius:50%; flex-shrink:0; }
.ts-chip strong { font-weight:700; color:var(--text-primary); font-size:12px; font-family:'JetBrains Mono',monospace; }
.topbar-right { display:flex; align-items:center; gap:5px; flex-shrink:0; }
#clock { font-size:11px; color:var(--text-muted); font-weight:500; font-family:'JetBrains Mono',monospace; min-width:155px; text-align:right; }

/* ============ BUTTONS ============ */
.theme-btn { background:var(--chip-bg); border:1px solid var(--border); border-radius:18px; padding:5px 11px; font-size:11px; font-weight:600; color:var(--text-primary); cursor:pointer; display:flex; align-items:center; gap:5px; transition:all .2s; font-family:'Rubik',sans-serif; }
.theme-btn:hover { border-color:var(--accent); color:var(--accent); }
.add-btn { background:linear-gradient(135deg,#e53935,#b71c1c); color:#fff; border:none; border-radius:7px; padding:6px 11px; font-size:11px; font-weight:700; cursor:pointer; font-family:'Rubik',sans-serif; display:flex; align-items:center; gap:4px; transition:all .2s; }
.add-btn:hover { transform:translateY(-1px); box-shadow:0 4px 12px rgba(229,57,53,.4); }
.place-btn { background:linear-gradient(135deg,#2e7d32,#1b5e20); color:#fff; border:none; border-radius:7px; padding:6px 11px; font-size:11px; font-weight:700; cursor:pointer; font-family:'Rubik',sans-serif; display:flex; align-items:center; gap:4px; transition:all .2s; }
.place-btn:hover { transform:translateY(-1px); box-shadow:0 4px 12px rgba(46,125,50,.4); }
.place-btn.active { background:linear-gradient(135deg,#f57f17,#e65100); box-shadow:0 0 0 3px rgba(245,127,23,.3); }
.bld-btn { background:linear-gradient(135deg,#6a1b9a,#4a148c); color:#fff; border:none; border-radius:7px; padding:6px 11px; font-size:11px; font-weight:700; cursor:pointer; font-family:'Rubik',sans-serif; display:flex; align-items:center; gap:4px; transition:all .2s; }
.bld-btn:hover { transform:translateY(-1px); box-shadow:0 4px 12px rgba(106,27,154,.4); }
.bld-btn.active { background:linear-gradient(135deg,#f57f17,#e65100); box-shadow:0 0 0 3px rgba(245,127,23,.3); }
/* NEW: camera button */
.cam-btn { background:linear-gradient(135deg,#0277bd,#01579b); color:#fff; border:none; border-radius:7px; padding:6px 11px; font-size:11px; font-weight:700; cursor:pointer; font-family:'Rubik',sans-serif; display:flex; align-items:center; gap:4px; transition:all .2s; }
.cam-btn:hover { transform:translateY(-1px); box-shadow:0 4px 12px rgba(2,119,189,.4); }
.cam-btn.active { background:linear-gradient(135deg,#f57f17,#e65100); box-shadow:0 0 0 3px rgba(245,127,23,.3); }
.heatmap-btn { background:var(--chip-bg); border:1px solid var(--border); border-radius:7px; padding:6px 11px; font-size:11px; font-weight:700; cursor:pointer; font-family:'Rubik',sans-serif; color:var(--text-secondary); display:flex; align-items:center; gap:4px; transition:all .2s; }
.heatmap-btn:hover { border-color:#fb8c00; color:#fb8c00; }
.heatmap-btn.active { background:linear-gradient(135deg,#f57f17,#e65100); border-color:transparent; color:#fff; }
.auto-btn { background:var(--chip-bg); border:1px solid var(--border); border-radius:7px; padding:6px 11px; font-size:11px; font-weight:700; cursor:pointer; font-family:'Rubik',sans-serif; color:var(--text-secondary); display:flex; align-items:center; gap:4px; transition:all .2s; }
.auto-btn.active { background:linear-gradient(135deg,#2e7d32,#1b5e20); border-color:transparent; color:#fff; }

/* ============ MAIN LAYOUT ============ */
#main { display:flex; flex:1; overflow:hidden; }

/* ============ SIDEBAR ============ */
#sidebar { width:272px; flex-shrink:0; background:var(--sidebar-bg); border-right:1px solid var(--border); display:flex; flex-direction:column; overflow:hidden; z-index:50; box-shadow:2px 0 8px var(--shadow); transition:background .25s,border-color .25s; }
.sidebar-scroll { flex:1; overflow-y:auto; padding-bottom:16px; }
.sidebar-scroll::-webkit-scrollbar { width:3px; }
.sidebar-scroll::-webkit-scrollbar-thumb { background:var(--border); border-radius:2px; }
.s-section { padding:11px 13px; border-bottom:1px solid var(--border-light); }
.s-title { font-size:9px; font-weight:700; letter-spacing:1.8px; color:var(--text-muted); text-transform:uppercase; margin-bottom:8px; }
.search-box { width:100%; padding:7px 11px; background:var(--input-bg); border:1.5px solid var(--border); border-radius:7px; font-family:'Rubik',sans-serif; font-size:12px; color:var(--text-primary); outline:none; transition:border-color .2s,background .25s; }
.search-box:focus { border-color:var(--accent); }
.search-box::placeholder { color:var(--text-muted); }
select { width:100%; padding:7px 11px; background:var(--input-bg); border:1.5px solid var(--border); border-radius:7px; font-family:'Rubik',sans-serif; font-size:12px; color:var(--text-primary); cursor:pointer; outline:none; appearance:none; background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='12' viewBox='0 0 24 24' fill='none' stroke='%238a96a3' stroke-width='2'%3E%3Cpath d='M6 9l6 6 6-6'/%3E%3C/svg%3E"); background-repeat:no-repeat; background-position:right 11px center; transition:border-color .2s,background .25s; }
select:focus { border-color:var(--accent); }
.btn-show { width:100%; padding:8px; margin-top:7px; background:linear-gradient(135deg,#1565c0,#0d47a1); color:#fff; border:none; border-radius:7px; font-family:'Rubik',sans-serif; font-size:12px; font-weight:600; cursor:pointer; transition:all .2s; box-shadow:0 2px 8px rgba(21,101,192,0.25); }
.btn-show:hover { transform:translateY(-1px); box-shadow:0 4px 14px rgba(21,101,192,0.35); }
.btn-reset { width:100%; padding:6px; margin-top:5px; background:var(--card-bg); color:var(--text-muted); border:1.5px solid var(--border); border-radius:7px; font-family:'Rubik',sans-serif; font-size:11px; font-weight:600; cursor:pointer; transition:all .2s; }
.btn-reset:hover { border-color:#e53935; color:#e53935; }
.layer-row { display:flex; align-items:center; gap:8px; padding:5px 0; cursor:pointer; border-radius:5px; transition:background .12s; }
.layer-row:hover { background:var(--bg-secondary); padding-left:4px; }
.layer-row input[type=checkbox] { width:14px; height:14px; cursor:pointer; accent-color:#1565c0; flex-shrink:0; }
.layer-icon { font-size:12px; flex-shrink:0; }
.layer-label { font-size:11px; color:var(--text-secondary); flex:1; }
.layer-count { font-size:9px; font-weight:700; color:#fff; padding:1px 6px; border-radius:9px; }
.stat-item { margin-bottom:7px; }
.stat-row { display:flex; justify-content:space-between; align-items:center; margin-bottom:3px; }
.stat-name { font-size:11px; color:var(--text-secondary); }
.stat-val { font-size:11px; font-weight:700; font-family:'JetBrains Mono',monospace; }
.stat-bar-bg { height:3px; background:var(--bg-tertiary); border-radius:3px; overflow:hidden; }
.stat-bar-fill { height:100%; border-radius:3px; transition:width 0.6s ease; }
.unit-row { display:flex; align-items:center; gap:8px; padding:5px 0; border-bottom:1px solid var(--border-light); }
.unit-info { flex:1; }
.unit-name { font-weight:600; color:var(--text-primary); font-size:11px; }
.unit-street { font-size:9px; color:var(--text-muted); margin-top:1px; }
.badge { font-size:9px; font-weight:600; padding:2px 6px; border-radius:9px; }
.badge-patrol { background:#e8f5e9; color:#2e7d32; }

/* ============ MAP ============ */
#map { flex:1; transition:filter .25s; }
[data-theme="dark"] #map { filter:brightness(0.85) invert(1) hue-rotate(180deg); }
[data-theme="dark"] .leaflet-tile { filter:invert(1) hue-rotate(180deg) brightness(1.2) saturate(0.9); }
#map.mode-incident { cursor:crosshair !important; }
#map.mode-incident .leaflet-interactive { cursor:crosshair !important; }
#map.mode-building { cursor:cell !important; }
#map.mode-building .leaflet-interactive { cursor:cell !important; }
#map.mode-camera { cursor:crosshair !important; }
#map.mode-camera .leaflet-interactive { cursor:crosshair !important; }

/* ============ MAP OVERLAYS ============ */
#osm-loader { position:absolute; top:10px; right:10px; z-index:700; background:var(--card-bg); border:1.5px solid var(--border); border-radius:10px; padding:7px 13px; font-size:11px; font-weight:600; color:var(--text-secondary); box-shadow:0 4px 16px var(--shadow-md); display:flex; align-items:center; gap:7px; transition:opacity .4s; }
#osm-loader.hidden { opacity:0; pointer-events:none; }
.osm-spin { width:13px; height:13px; border:2px solid var(--border); border-top-color:#1565c0; border-radius:50%; animation:spin .8s linear infinite; flex-shrink:0; }
@keyframes spin { to { transform:rotate(360deg); } }
#mode-banner { position:absolute; top:10px; left:50%; transform:translateX(-50%); z-index:600; border-radius:14px; padding:9px 18px; font-size:12px; font-weight:700; color:#fff; box-shadow:0 4px 20px rgba(0,0,0,.3); display:none; align-items:center; gap:9px; white-space:nowrap; animation:bannerIn .3s ease; }
#mode-banner.show { display:flex; }
#mode-banner.inc-mode { background:linear-gradient(135deg,#e53935,#b71c1c); }
#mode-banner.bld-mode { background:linear-gradient(135deg,#6a1b9a,#4a148c); }
#mode-banner.cam-mode { background:linear-gradient(135deg,#0277bd,#01579b); }
.mode-pulse { width:9px; height:9px; border-radius:50%; background:#fff; animation:modePulse 1s infinite; }
@keyframes modePulse { 0%,100%{opacity:1;transform:scale(1)} 50%{opacity:.5;transform:scale(1.4)} }
.mode-cancel-btn { background:rgba(255,255,255,0.2); border:1px solid rgba(255,255,255,0.4); border-radius:10px; padding:3px 9px; font-size:10px; font-weight:700; color:#fff; cursor:pointer; font-family:'Rubik',sans-serif; transition:background .15s; }
.mode-cancel-btn:hover { background:rgba(255,255,255,0.35); }
#focus-banner { position:absolute; bottom:14px; left:50%; transform:translateX(-50%); z-index:500; background:var(--card-bg); border:1.5px solid var(--border); border-radius:20px; padding:7px 16px; font-size:11px; font-weight:600; color:var(--text-primary); box-shadow:0 4px 16px var(--shadow-md); display:none; align-items:center; gap:9px; white-space:nowrap; }
#focus-banner.show { display:flex; animation:bannerIn .3s ease; }
@keyframes bannerIn { from{opacity:0;transform:translateX(-50%) translateY(-8px)} to{opacity:1;transform:translateX(-50%) translateY(0)} }
#focus-banner .fb-dot { width:9px; height:9px; border-radius:50%; flex-shrink:0; }
#focus-banner .fb-close { background:var(--bg-secondary); border:none; border-radius:50%; width:18px; height:18px; cursor:pointer; font-size:10px; display:flex; align-items:center; justify-content:center; color:var(--text-secondary); transition:background .15s; flex-shrink:0; }
#focus-banner .fb-close:hover { background:#e53935; color:#fff; }
#empty-hint { position:absolute; top:50%; left:50%; transform:translate(-50%,-50%); z-index:400; background:var(--card-bg); border:1.5px solid var(--border); border-radius:14px; padding:18px 24px; text-align:center; box-shadow:0 8px 32px var(--shadow-md); pointer-events:none; animation:hintFade 1s ease 1s both; }
@keyframes hintFade { from{opacity:0;transform:translate(-50%,-55%)} to{opacity:1;transform:translate(-50%,-50%)} }
#empty-hint.hidden { display:none; }
#empty-hint .hint-icon { font-size:32px; margin-bottom:7px; }
#empty-hint .hint-title { font-size:14px; font-weight:700; color:var(--text-primary); margin-bottom:5px; }
#empty-hint .hint-sub { font-size:11px; color:var(--text-muted); line-height:1.6; }
#heatmap-legend { position:absolute; bottom:50px; right:10px; z-index:500; background:var(--card-bg); border:1.5px solid var(--border); border-radius:10px; padding:10px 13px; font-size:10px; color:var(--text-secondary); box-shadow:0 4px 14px var(--shadow-md); display:none; }
#heatmap-legend.show { display:block; }
#heatmap-legend .hl-title { font-weight:700; color:var(--text-primary); margin-bottom:7px; font-size:11px; }
.hl-bar { height:10px; width:150px; border-radius:5px; background:linear-gradient(to right,rgba(0,0,255,.3),rgba(0,255,0,.5),rgba(255,255,0,.7),rgba(255,0,0,.9)); margin:4px 0; }
.hl-labels { display:flex; justify-content:space-between; font-size:9px; color:var(--text-muted); }

/* ============ RIGHT PANEL ============ */
#panel-right { width:268px; flex-shrink:0; background:var(--sidebar-bg); border-left:1px solid var(--border); display:flex; flex-direction:column; overflow:hidden; z-index:50; box-shadow:-2px 0 8px var(--shadow); transition:background .25s,border-color .25s; }
.panel-tabs { display:flex; border-bottom:1px solid var(--border); flex-shrink:0; }
.tab-btn { flex:1; padding:10px 2px; font-size:10px; font-weight:600; color:var(--text-muted); background:none; border:none; border-bottom:2px solid transparent; cursor:pointer; transition:all .2s; font-family:'Rubik',sans-serif; }
.tab-btn.active { color:var(--accent); border-bottom-color:var(--accent); }
.tab-content { display:none; flex:1; overflow-y:auto; flex-direction:column; }
.tab-content.active { display:flex; }
.tab-content::-webkit-scrollbar { width:3px; }
.tab-content::-webkit-scrollbar-thumb { background:var(--border); border-radius:2px; }
#district-card { margin:11px; border-radius:11px; padding:13px; color:#fff; display:none; background:linear-gradient(135deg,#1565c0,#0d47a1); animation:cardIn .3s cubic-bezier(.4,0,.2,1); }
@keyframes cardIn { from{opacity:0;transform:translateY(-8px)} to{opacity:1;transform:translateY(0)} }
#district-card.show { display:block; }
#dc-name { font-size:13px; font-weight:700; margin-bottom:9px; }
.dc-grid { display:grid; grid-template-columns:1fr 1fr; gap:5px; margin-bottom:9px; }
.dc-item { background:rgba(255,255,255,0.13); border-radius:7px; padding:6px 9px; }
.dc-val { font-size:18px; font-weight:800; font-family:'JetBrains Mono',monospace; }
.dc-lbl { font-size:8px; opacity:.72; letter-spacing:1px; margin-top:2px; }

/* Incident feed */
.inc-item { padding:7px 12px; border-bottom:1px solid var(--border-light); border-left:3px solid transparent; cursor:pointer; transition:background .12s; animation:fadeSlide .3s ease; position:relative; }
.inc-item:hover { background:var(--bg-secondary); }
.inc-item:hover .inc-delete { display:flex; }
.inc-delete { display:none; position:absolute; right:7px; top:50%; transform:translateY(-50%); background:#fce4ec; border:none; border-radius:5px; padding:2px 6px; color:#c62828; font-size:9px; font-weight:700; cursor:pointer; transition:background .15s; }
.inc-delete:hover { background:#e53935; color:#fff; }
@keyframes fadeSlide { from{opacity:0;transform:translateX(-5px)} to{opacity:1;transform:translateX(0)} }
.inc-item.sev-high { border-left-color:#e53935; }
.inc-item.sev-med  { border-left-color:#fb8c00; }
.inc-item.sev-low  { border-left-color:#fdd835; }
.inc-type { font-size:9px; font-weight:700; letter-spacing:1px; text-transform:uppercase; }
.inc-type.high { color:#e53935; } .inc-type.med { color:#fb8c00; } .inc-type.low { color:#f9a825; }
.inc-loc { font-size:10px; color:var(--text-secondary); margin:2px 0; }
.inc-time { font-size:9px; color:var(--text-muted); font-family:'JetBrains Mono',monospace; }
.inc-district { font-size:8px; font-weight:600; padding:1px 5px; border-radius:7px; display:inline-block; margin-top:2px; }
.inc-auto-badge { font-size:8px; background:#e8f5e9; color:#2e7d32; padding:1px 4px; border-radius:4px; margin-left:4px; }

/* Buildings */
.bld-item { padding:8px 12px; border-bottom:1px solid var(--border-light); cursor:pointer; transition:background .12s; display:flex; align-items:center; gap:9px; position:relative; }
.bld-item:hover { background:var(--bg-secondary); }
.bld-item:hover .bld-delete { display:flex; }
.bld-delete { display:none; position:absolute; right:7px; top:50%; transform:translateY(-50%); background:#fce4ec; border:none; border-radius:5px; padding:2px 6px; color:#c62828; font-size:9px; font-weight:700; cursor:pointer; }
.bld-delete:hover { background:#e53935; color:#fff; }
.bld-emoji { font-size:18px; flex-shrink:0; }
.bld-info { flex:1; }
.bld-name { font-size:11px; font-weight:600; color:var(--text-primary); }
.bld-type { font-size:9px; color:var(--text-muted); margin-top:1px; }
.bld-district-badge { font-size:8px; font-weight:600; padding:1px 5px; border-radius:7px; color:#fff; margin-top:3px; display:inline-block; }

/* Charts */
.chart-title { font-size:9px; font-weight:700; letter-spacing:1px; color:var(--text-muted); text-transform:uppercase; margin-bottom:8px; }
.hour-chart { display:flex; align-items:flex-end; gap:2px; height:48px; padding:0 12px; margin-top:7px; }
.h-bar-w { flex:1; display:flex; flex-direction:column; align-items:center; gap:2px; }
.h-bar { width:100%; border-radius:2px 2px 0 0; transition:height .4s; }
.h-lbl { font-size:6px; color:var(--text-muted); }
.mini-chart { padding:11px 13px 0; }
.chart-bars { display:flex; align-items:flex-end; gap:3px; height:50px; }
.chart-bar-wrap { flex:1; display:flex; flex-direction:column; align-items:center; gap:3px; }
.chart-bar { width:100%; border-radius:3px 3px 0 0; transition:height .5s ease; }
.chart-lbl { font-size:8px; color:var(--text-muted); }

/* Popups */
.leaflet-popup-content-wrapper { border-radius:9px !important; box-shadow:0 4px 20px var(--shadow-md) !important; border:1px solid var(--border) !important; padding:0 !important; background:var(--card-bg) !important; }
.leaflet-popup-content { margin:0 !important; padding:0 !important; }
.popup-inner { padding:9px 11px; font-family:'Rubik',sans-serif; min-width:150px; background:var(--card-bg); border-radius:9px; }
.popup-title { font-size:12px; font-weight:700; color:var(--text-primary); margin-bottom:4px; }
.popup-row { font-size:10px; color:var(--text-secondary); margin-bottom:2px; }
.popup-delete-btn { width:100%; margin-top:7px; padding:5px; background:#fce4ec; border:none; border-radius:5px; color:#c62828; font-size:10px; font-weight:700; cursor:pointer; font-family:'Rubik',sans-serif; transition:background .15s; }
.popup-delete-btn:hover { background:#e53935; color:#fff; }
.leaflet-popup-tip-container { display:none; }

/* ============ MODALS ============ */
#modal-overlay, #bld-modal-overlay, #analytics-overlay, #cam-modal-overlay {
  position:fixed; inset:0; background:rgba(0,0,0,0.55); z-index:2000;
  display:none; align-items:center; justify-content:center; backdrop-filter:blur(2px);
}
#modal-overlay.show, #bld-modal-overlay.show, #analytics-overlay.show, #cam-modal-overlay.show { display:flex; }
#modal, #bld-modal, #cam-modal { background:var(--card-bg); border:1px solid var(--border); border-radius:14px; padding:22px; width:410px; max-width:95vw; box-shadow:0 16px 48px rgba(0,0,0,.25); animation:modalIn .25s cubic-bezier(.4,0,.2,1); }
#analytics-modal { background:var(--card-bg); border:1px solid var(--border); border-radius:14px; padding:24px; width:600px; max-width:95vw; max-height:85vh; overflow-y:auto; box-shadow:0 16px 48px rgba(0,0,0,.25); animation:modalIn .25s cubic-bezier(.4,0,.2,1); }
@keyframes modalIn { from{opacity:0;transform:scale(.95)} to{opacity:1;transform:scale(1)} }
.modal-title { font-size:15px; font-weight:700; color:var(--text-primary); margin-bottom:14px; display:flex; justify-content:space-between; align-items:center; }
.modal-close { background:none; border:none; font-size:17px; color:var(--text-muted); cursor:pointer; padding:0 4px; }
.modal-close:hover { color:#e53935; }
.form-group { margin-bottom:11px; }
.form-label { font-size:9px; font-weight:700; color:var(--text-muted); letter-spacing:1.2px; text-transform:uppercase; margin-bottom:4px; display:block; }
.form-input { width:100%; padding:8px 11px; background:var(--input-bg); border:1.5px solid var(--border); border-radius:7px; font-family:'Rubik',sans-serif; font-size:12px; color:var(--text-primary); outline:none; transition:border-color .2s; }
.form-input:focus { border-color:var(--accent); }
.form-row { display:grid; grid-template-columns:1fr 1fr; gap:9px; }
.sev-btns { display:flex; gap:7px; }
.sev-btn { flex:1; padding:6px; border-radius:7px; border:1.5px solid var(--border); font-size:10px; font-weight:700; cursor:pointer; background:var(--input-bg); color:var(--text-muted); transition:all .2s; font-family:'Rubik',sans-serif; }
.sev-btn.active-high { border-color:#e53935; background:#fce4ec; color:#c62828; }
.sev-btn.active-med  { border-color:#fb8c00; background:#fff3e0; color:#e65100; }
.sev-btn.active-low  { border-color:#fdd835; background:#fffde7; color:#f57f17; }
.modal-actions { display:flex; gap:7px; margin-top:14px; }
.btn-save { flex:1; padding:9px; background:linear-gradient(135deg,#1565c0,#0d47a1); color:#fff; border:none; border-radius:7px; font-family:'Rubik',sans-serif; font-size:12px; font-weight:700; cursor:pointer; transition:all .2s; }
.btn-save:hover { opacity:.9; }
.btn-cancel { padding:9px 14px; background:var(--bg-secondary); color:var(--text-secondary); border:1.5px solid var(--border); border-radius:7px; font-family:'Rubik',sans-serif; font-size:12px; cursor:pointer; transition:all .2s; }
.coords-display { background:var(--bg-secondary); border:1px solid var(--border); border-radius:7px; padding:7px 11px; font-size:10px; color:var(--text-secondary); font-family:'JetBrains Mono',monospace; display:flex; align-items:center; gap:7px; }
.coords-dot { width:7px; height:7px; border-radius:50%; background:#2e7d32; flex-shrink:0; }
.emoji-grid { display:grid; grid-template-columns:repeat(8,1fr); gap:3px; margin-top:7px; }
.emoji-option { font-size:18px; padding:5px; border-radius:7px; cursor:pointer; text-align:center; border:2px solid transparent; transition:all .15px; background:var(--bg-secondary); }
.emoji-option:hover { background:var(--bg-tertiary); transform:scale(1.1); }
.emoji-option.selected { border-color:var(--accent); background:#e8f2fd; }
[data-theme="dark"] .emoji-option.selected { background:#1a2a3e; }
.pop-overlay { margin-top:9px; background:rgba(255,255,255,0.15); border-radius:7px; padding:7px 9px; }
.pop-overlay-title { font-size:8px; opacity:.75; letter-spacing:1px; text-transform:uppercase; margin-bottom:3px; }
.pop-overlay-val { font-size:17px; font-weight:800; font-family:'JetBrains Mono',monospace; }
.pop-overlay-row { display:flex; justify-content:space-between; font-size:9px; opacity:.8; margin-top:3px; }
.export-btn { width:100%; padding:7px; margin-top:5px; background:var(--card-bg); color:#2e7d32; border:1.5px solid #2e7d32; border-radius:7px; font-family:'Rubik',sans-serif; font-size:11px; font-weight:600; cursor:pointer; transition:all .2s; }
.export-btn:hover { background:#e8f5e9; }
.analytics-btn { width:100%; padding:7px; margin-top:5px; background:var(--card-bg); color:#1565c0; border:1.5px solid #1565c0; border-radius:7px; font-family:'Rubik',sans-serif; font-size:11px; font-weight:600; cursor:pointer; transition:all .2s; }
.analytics-btn:hover { background:#e8f0fc; }
.db-status { display:flex; align-items:center; gap:5px; font-size:10px; color:var(--text-muted); padding:5px 0; }
.db-dot { width:5px; height:5px; border-radius:50%; background:#2e7d32; animation:pulse 2s infinite; }
@keyframes pulse { 0%,100%{opacity:1} 50%{opacity:.4} }
.filter-chips { display:flex; gap:3px; flex-wrap:wrap; margin-top:6px; }
.filter-chip { font-size:9px; font-weight:600; padding:2px 7px; border-radius:10px; cursor:pointer; border:1px solid var(--border); background:var(--bg-secondary); color:var(--text-muted); transition:all .15s; }
.filter-chip.active { border-color:var(--accent); background:#e8f2fd; color:var(--accent); }
[data-theme="dark"] .filter-chip.active { background:#1a2a3e; }

/* Toast */
#toast { position:fixed; bottom:18px; left:50%; transform:translateX(-50%) translateY(90px); background:var(--card-bg); border:1px solid var(--border); border-left:4px solid #e53935; border-radius:9px; padding:9px 14px; z-index:9999; box-shadow:0 8px 24px var(--shadow-md); min-width:240px; transition:transform .35s cubic-bezier(.4,0,.2,1); display:flex; align-items:center; gap:9px; }
#toast.show { transform:translateX(-50%) translateY(0); }
#toast-type { font-size:9px; font-weight:700; color:#e53935; letter-spacing:1px; }
#toast-loc { font-size:11px; color:var(--text-secondary); margin-top:2px; }

.car-label { background:var(--card-bg); border:2px solid #7b1fa2; border-radius:10px; padding:2px 6px; font-size:9px; font-weight:700; color:#7b1fa2; white-space:nowrap; box-shadow:0 2px 6px var(--shadow); }
.osm-badge { display:inline-flex; align-items:center; gap:3px; font-size:8px; background:#e8f5e9; color:#2e7d32; border:1px solid #a5d6a7; border-radius:7px; padding:2px 6px; font-weight:600; }

/* Analytics modal */
.analytics-grid { display:grid; grid-template-columns:1fr 1fr; gap:12px; margin-bottom:16px; }
.analytics-card { background:var(--bg-secondary); border:1px solid var(--border); border-radius:10px; padding:14px; }
.analytics-card .ac-val { font-size:26px; font-weight:800; font-family:'JetBrains Mono',monospace; }
.analytics-card .ac-lbl { font-size:10px; color:var(--text-muted); margin-top:3px; }
.analytics-card .ac-trend { font-size:10px; margin-top:5px; font-weight:600; }
.trend-up { color:#e53935; } .trend-down { color:#2e7d32; }
.analytics-section-title { font-size:11px; font-weight:700; letter-spacing:1px; text-transform:uppercase; color:var(--text-muted); margin-bottom:10px; }
.a-bar-row { display:flex; align-items:center; gap:9px; margin-bottom:8px; }
.a-bar-label { font-size:11px; color:var(--text-secondary); width:90px; flex-shrink:0; text-align:right; }
.a-bar-bg { flex:1; height:6px; background:var(--bg-tertiary); border-radius:3px; overflow:hidden; }
.a-bar-fill { height:100%; border-radius:3px; }
.a-bar-val { font-size:10px; font-weight:700; font-family:'JetBrains Mono',monospace; width:35px; }
#radar-canvas { display:block; margin:0 auto; }
</style>
</head>
<body class="">

<!-- INCIDENT MODAL -->
<div id="modal-overlay">
  <div id="modal">
    <div class="modal-title">🚨 Оқиға қосу <button class="modal-close" onclick="closeModal()">✕</button></div>
    <div id="modal-coords-display" class="coords-display" style="margin-bottom:11px;display:none">
      <div class="coords-dot"></div><span id="modal-coords-text">—</span>
    </div>
    <div class="form-group">
      <label class="form-label">Оқиға түрі (бап)</label>
      <select class="form-input" id="m-type">
        <option value="ст.190">ст.190 — Алаяқтық</option>
        <option value="ст.188">ст.188 — Ұрлық</option>
        <option value="ст.109-1">ст.109-1 — Денсаулыққа зиян</option>
        <option value="ст.296">ст.296 — Бұзақылық</option>
        <option value="ст.108-1">ст.108-1 — Зорлық</option>
        <option value="ст.345">ст.345 — Лауазымды тұлғаға қарсылық</option>
        <option value="ст.107">ст.107 — Қасақана дене жарақаты</option>
        <option value="ст.293">ст.293 — Тонау</option>
        <option value="ст.139">ст.139 — Кісі өлтіру</option>
        <option value="ст.297">ст.297 — Тәртіп бұзу</option>
        <option value="ст.191">ст.191 — Алаяқтық (ауыр)</option>
        <option value="ст.194">ст.194 — Жымқыру</option>
        <option value="ст.187">ст.187 — Меншікке зиян</option>
        <option value="ст.287">ст.287 — Нашақорлық</option>
        <option value="ст.367">ст.367 — Жалған жалалау</option>
        <option value="ст.385">ст.385 — Пара беру</option>
        <option value="ст.195">ст.195 — Иелену</option>
        <option value="ст.189">ст.189 — Ұрлық (ауыр)</option>
        <option value="ЖКО">ЖКО — Жол-көлік оқиғасы</option>
        <option value="ҰРЛЫҚ">ҰРЛЫҚ</option>
        <option value="ТОНАУ">ТОНАУ</option>
        <option value="ЗОРЛЫҚ">ЗОРЛЫҚ</option>
        <option value="АЛАЯҚТЫҚ">АЛАЯҚТЫҚ</option>
        <option value="НАШАҚОРЛЫҚ">НАШАҚОРЛЫҚ</option>
        <option value="БҰЗАҚЫЛЫҚ">БҰЗАҚЫЛЫҚ</option>
        <option value="ШАБУЫЛ">ШАБУЫЛ</option>
        <option value="КІСІ ӨЛТІРУ">КІСІ ӨЛТІРУ</option>
      </select>
    </div>
    <div class="form-group">
      <label class="form-label">Мекенжай</label>
      <input type="text" class="form-input" id="m-loc" placeholder="Мысалы: Тәуелсіздік к-сі, 45">
    </div>
    <div class="form-row">
      <div class="form-group">
        <label class="form-label">Аудан</label>
        <select class="form-input" id="m-district">
          <option value="alfarabi">Аль-Фараби</option>
          <option value="abay">Абай</option>
          <option value="karatau">Қаратау</option>
          <option value="enbekshi">Еңбекшілер</option>
          <option value="turan">Туран</option>
        </select>
      </div>
      <div class="form-group">
        <label class="form-label">Уақыт</label>
        <input type="time" class="form-input" id="m-time">
      </div>
    </div>
    <div class="form-group">
      <label class="form-label">Маңыздылық</label>
      <div class="sev-btns">
        <button class="sev-btn active-high" id="sev-high" onclick="setSev(&#39;high&#39;)">🔴 Жоғары</button>
        <button class="sev-btn" id="sev-med" onclick="setSev(&#39;med&#39;)">🟡 Орта</button>
        <button class="sev-btn" id="sev-low" onclick="setSev(&#39;low&#39;)">🟢 Төмен</button>
      </div>
    </div>
    <div class="form-group">
      <label class="form-label">Сипаттама</label>
      <input type="text" class="form-input" id="m-desc" placeholder="Қысқаша сипаттама...">
    </div>
    <div class="modal-actions">
      <button class="btn-cancel" onclick="closeModal()">Бас тарту</button>
      <button class="btn-save" onclick="saveIncident()">💾 Сақтау</button>
    </div>
  </div>
</div>

<!-- BUILDING MODAL -->
<div id="bld-modal-overlay" class="">
  <div id="bld-modal">
    <div class="modal-title">🏢 Ғимарат қосу <button class="modal-close" onclick="closeBldModal()">✕</button></div>
    <div id="bld-coords-display" class="coords-display" style="margin-bottom: 11px; display: flex;">
      <div class="coords-dot" style="background:#6a1b9a"></div><span id="bld-coords-text">42.34064, 69.62522 · Аль-Фараби ауданы</span>
    </div>
    <div class="form-group">
      <label class="form-label">Атауы</label>
      <input type="text" class="form-input" id="b-name" placeholder="Мысалы: Центральный рынок...">
    </div>
    <div class="form-row">
      <div class="form-group">
        <label class="form-label">Нысан түрі</label>
        <select class="form-input" id="b-type">
          <option>Мектеп</option><option>Аурухана</option><option>Базар</option>
          <option>Мекеме</option><option>Банк</option><option>Мешіт</option>
          <option>Мейрамхана</option><option>Қонақ үй</option><option>Зауыт</option>
          <option>Тұрғын үй</option><option>Спорт</option><option>Басқа</option>
        </select>
      </div>
      <div class="form-group">
        <label class="form-label">Аудан</label>
        <select class="form-input" id="b-district">
          <option value="alfarabi">Аль-Фараби</option>
          <option value="abay">Абай</option>
          <option value="karatau">Қаратау</option>
          <option value="enbekshi">Еңбекшілер</option>
          <option value="turan">Туран</option>
        </select>
      </div>
    </div>
    <div class="form-group">
      <label class="form-label">Белгіше</label>
      <div class="emoji-grid" id="emoji-grid"><div class="emoji-option">🏫</div><div class="emoji-option">🏥</div><div class="emoji-option">🛒</div><div class="emoji-option selected">🏛</div><div class="emoji-option">🏦</div><div class="emoji-option">🕌</div><div class="emoji-option">🍽️</div><div class="emoji-option">🏨</div><div class="emoji-option">🏭</div><div class="emoji-option">🏠</div><div class="emoji-option">🏋️</div><div class="emoji-option">🏟️</div><div class="emoji-option">🎭</div><div class="emoji-option">🎓</div><div class="emoji-option">💒</div><div class="emoji-option">🚒</div><div class="emoji-option">🚓</div><div class="emoji-option">🏗️</div><div class="emoji-option">🌳</div><div class="emoji-option">🏪</div></div>
    </div>
    <div class="form-group">
      <label class="form-label">Сипаттама</label>
      <input type="text" class="form-input" id="b-desc" placeholder="Қосымша ақпарат...">
    </div>
    <div class="modal-actions">
      <button class="btn-cancel" onclick="closeBldModal()">Бас тарту</button>
      <button class="btn-save" style="background:linear-gradient(135deg,#6a1b9a,#4a148c)" onclick="saveBuilding()">💾 Сақтау</button>
    </div>
  </div>
</div>

<!-- CAMERA MODAL -->
<div id="cam-modal-overlay">
  <div id="cam-modal">
    <div class="modal-title">📷 Камера қосу <button class="modal-close" onclick="closeCamModal()">✕</button></div>
    <div id="cam-coords-display" class="coords-display" style="margin-bottom:11px;display:none">
      <div class="coords-dot" style="background:#0277bd"></div><span id="cam-coords-text">—</span>
    </div>
    <div class="form-group">
      <label class="form-label">Камера атауы / №</label>
      <input type="text" class="form-input" id="cam-name" placeholder="Мысалы: Камера #43 немесе Базар камерасы">
    </div>
    <div class="form-row">
      <div class="form-group">
        <label class="form-label">Аудан</label>
        <select class="form-input" id="cam-district">
          <option value="alfarabi">Аль-Фараби</option>
          <option value="abay">Абай</option>
          <option value="karatau">Қаратау</option>
          <option value="enbekshi">Еңбекшілер</option>
          <option value="turan">Туран</option>
        </select>
      </div>
      <div class="form-group">
        <label class="form-label">Сапа</label>
        <select class="form-input" id="cam-quality">
          <option value="HD">HD</option>
          <option value="Full HD">Full HD</option>
          <option value="4K">4K</option>
          <option value="SD">SD</option>
        </select>
      </div>
    </div>
    <div class="form-group">
      <label class="form-label">Мекенжай</label>
      <input type="text" class="form-input" id="cam-loc" placeholder="Мысалы: Тәуелсіздік к-сі, 45">
    </div>
    <div class="form-group">
      <label class="form-label">Күй</label>
      <div class="sev-btns">
        <button class="sev-btn active-low" id="cam-status-ok" onclick="setCamStatus(&#39;ok&#39;)">🟢 Жұмыс жасайды</button>
        <button class="sev-btn" id="cam-status-repair" onclick="setCamStatus(&#39;repair&#39;)">🟡 Жөндеуде</button>
        <button class="sev-btn" id="cam-status-off" onclick="setCamStatus(&#39;off&#39;)">🔴 Сөндірілген</button>
      </div>
    </div>
    <div class="modal-actions">
      <button class="btn-cancel" onclick="closeCamModal()">Бас тарту</button>
      <button class="btn-save" style="background:linear-gradient(135deg,#0277bd,#01579b)" onclick="saveCamera()">💾 Сақтау</button>
    </div>
  </div>
</div>

<!-- ANALYTICS MODAL -->
<div id="analytics-overlay">
  <div id="analytics-modal">
    <div class="modal-title">📊 Қала статистикасы — Шымкент 2024 <button class="modal-close" onclick="closeAnalytics()">✕</button></div>
    <div class="analytics-grid">
      <div class="analytics-card"><div class="ac-val" style="color:#e53935">1431</div><div class="ac-lbl">Жалпы тіркелген іс (2024)</div><div class="ac-trend trend-up">▲ +4.2% өткен жылдан</div></div>
      <div class="analytics-card"><div class="ac-val" style="color:#fb8c00">799</div><div class="ac-lbl">ст.190 Алаяқтық — ең жиі</div><div class="ac-trend trend-up">▲ 55.8% үлесі</div></div>
      <div class="analytics-card"><div class="ac-val" style="color:#1565c0">68%</div><div class="ac-lbl">Ашылу коэффициенті</div><div class="ac-trend trend-down">▼ +2.1% өсім</div></div>
      <div class="analytics-card"><div class="ac-val" style="color:#7b1fa2">1 274 296</div><div class="ac-lbl">Халық саны</div><div class="ac-trend trend-up">▲ Өсімде</div></div>
    </div>
    <div style="margin-bottom:16px">
      <div class="analytics-section-title">Аудандар бойынша — барлық баптар</div>
      <div id="analytics-bars"></div>
    </div>
    <div style="margin-bottom:16px">
      <div class="analytics-section-title">Жетекші баптар рейтингі</div>
      <div id="analytics-top-crimes"></div>
    </div>
    <div>
      <div class="analytics-section-title">Аудан профилі (радар)</div>
      <canvas id="radar-canvas" width="400" height="220"></canvas>
    </div>
  </div>
</div>

<!-- TOPBAR -->
<div id="topbar">
  <div class="logo">
    <div class="logo-badge"><div class="logo-pulse"></div>🛡 ШҚМ</div>
    <span style="font-size:13px">Шымкент мониторингі</span>
    <span style="font-size:9px;color:var(--text-muted);font-weight:400">v7.0</span>
  </div>
  <div class="topbar-stats">
    <div class="ts-chip"><div class="dot" style="background:#e53935"></div>Тіркелді: <strong id="stat-total">283</strong></div>
    <div class="ts-chip"><div class="dot" style="background:#fb8c00"></div>ст.190: <strong>799</strong></div>
    <div class="ts-chip"><div class="dot" style="background:#8e24aa"></div>ст.188: <strong>393</strong></div>
    <div class="ts-chip"><div class="dot" style="background:#2e7d32"></div>ст.109-1: <strong>239</strong></div>
    <div class="ts-chip"><div class="dot" style="background:#1565c0"></div>Патруль: <strong>10</strong></div>
    <div class="ts-chip"><div class="dot" style="background:#00897b"></div>Халық: <strong>1.27М</strong></div>
  </div>
  <div class="topbar-right">
    <button class="auto-btn active" id="auto-btn" onclick="toggleAutoIncidents()">🟢 Авто</button>
    <button class="heatmap-btn" id="heatmap-btn" onclick="toggleHeatmap()">🌡 Жылу</button>
    <button class="cam-btn" id="place-cam-btn" onclick="toggleCameraMode()">📷 Камера</button>
    <button class="place-btn" id="place-inc-btn" onclick="toggleIncidentMode()">📍 Белгілеу</button>
    <button class="bld-btn" id="place-bld-btn" onclick="toggleBuildingMode()">🏢 Ғимарат</button>
    <button class="add-btn" onclick="openManualModal()">＋ Оқиға</button>
    <button class="theme-btn" id="theme-toggle" onclick="toggleTheme()">🌙 Қараңғы</button>
    <div id="clock">15:08:26 · 06.05.2026</div>
  </div>
</div>

<div id="main">
<div id="sidebar">
  <div class="sidebar-scroll">
    <div class="s-section">
      <div class="s-title">Іздеу</div>
      <input type="text" class="search-box" id="search-input" placeholder="🔍 Мекенжай немесе бап..." oninput="filterIncidents(this.value)">
      <div class="filter-chips" id="filter-chips">
        <span class="filter-chip" onclick="toggleFilter(&#39;ЖКО&#39;,this)">ЖКО</span>
        <span class="filter-chip" onclick="toggleFilter(&#39;ст.190&#39;,this)">ст.190</span>
        <span class="filter-chip" onclick="toggleFilter(&#39;ст.188&#39;,this)">ст.188</span>
        <span class="filter-chip" onclick="toggleFilter(&#39;ст.109-1&#39;,this)">ст.109-1</span>
        <span class="filter-chip" onclick="toggleFilter(&#39;ст.296&#39;,this)">ст.296</span>
        <span class="filter-chip" onclick="toggleFilter(&#39;ст.139&#39;,this)">ст.139</span>
        <span class="filter-chip" onclick="toggleFilter(&#39;ҰРЛЫҚ&#39;,this)">Ұрлық</span>
        <span class="filter-chip" onclick="toggleFilter(&#39;ТОНАУ&#39;,this)">Тонау</span>
      </div>
    </div>

    <div class="s-section">
      <div class="s-title">Аймақты таңдау</div>
      <select id="region-select" onchange="selectDistrict(this.value)">
        <option value="">— Барлық аудандар —</option>
        <option value="abay">Абай ауданы</option>
        <option value="alfarabi">Аль-Фараби ауданы</option>
        <option value="enbekshi">Еңбекшілер ауданы</option>
        <option value="karatau">Қаратау ауданы</option>
        <option value="turan">Туран ауданы</option>
      </select>
      <button class="btn-show" onclick="zoomToSelected()">⊕ Картада көрсету</button>
      <button class="btn-reset" onclick="resetFocus()">✕ Барлығын көрсету</button>
      <div style="margin-top:7px;font-size:9px;color:var(--text-muted);display:flex;align-items:center;gap:4px">
        <span class="osm-badge">🗺 OpenStreetMap</span> нақты шекаралар
      </div>
    </div>

    <div class="s-section">
      <div class="s-title">Қабаттар</div>
      <div class="layer-row" onclick="toggleLayer(&#39;crimes&#39;)"><input type="checkbox" id="l-crimes" checked=""><span class="layer-icon">⚠️</span><span class="layer-label">Тіркелген оқиғалар</span><span class="layer-count" style="background:#e53935" id="lc-crimes">283</span></div>
      <div class="layer-row" onclick="toggleLayer(&#39;dtp&#39;)"><input type="checkbox" id="l-dtp" checked=""><span class="layer-icon">💥</span><span class="layer-label">ЖКО нүктелері</span><span class="layer-count" style="background:#fb8c00">25</span></div>
      <div class="layer-row" onclick="toggleLayer(&#39;police&#39;)"><input type="checkbox" id="l-police" checked=""><span class="layer-icon">🚔</span><span class="layer-label">Патруль</span><span class="layer-count" style="background:#7b1fa2">10</span></div>
      <div class="layer-row" onclick="toggleLayer(&#39;posts&#39;)"><input type="checkbox" id="l-posts" checked=""><span class="layer-icon">🏛</span><span class="layer-label">Учаскелік пункттер</span><span class="layer-count" style="background:#2e7d32">12</span></div>
      <div class="layer-row" onclick="toggleLayer(&#39;cameras&#39;)"><input type="checkbox" id="l-cameras" checked=""><span class="layer-icon">📷</span><span class="layer-label">Бейнебақылау</span><span class="layer-count" style="background:#1565c0" id="lc-cameras">42</span></div>
      <div class="layer-row" onclick="toggleLayer(&#39;hospitals&#39;)"><input type="checkbox" id="l-hospitals" checked=""><span class="layer-icon">🏥</span><span class="layer-label">Аурухана / СМП</span><span class="layer-count" style="background:#00897b">9</span></div>
      <div class="layer-row" onclick="toggleLayer(&#39;schools&#39;)"><input type="checkbox" id="l-schools" checked=""><span class="layer-icon">🏫</span><span class="layer-label">Мектептер</span><span class="layer-count" style="background:#f57f17">14</span></div>
      <div class="layer-row" onclick="toggleLayer(&#39;bazaars&#39;)"><input type="checkbox" id="l-bazaars" checked=""><span class="layer-icon">🛒</span><span class="layer-label">Базарлар / ТЦ</span><span class="layer-count" style="background:#6d4c41">8</span></div>
      <div class="layer-row" onclick="toggleLayer(&#39;userBuildings&#39;)"><input type="checkbox" id="l-userBuildings" checked=""><span class="layer-icon">🏢</span><span class="layer-label">Менің ғимараттарым</span><span class="layer-count" style="background:#6a1b9a" id="lc-buildings">21</span></div>
    </div>

    <div class="s-section">
      <div class="s-title">Шымкент статистика 2024</div>
      <div class="stat-item"><div class="stat-row"><span class="stat-name">ст.190 Алаяқтық</span><span class="stat-val" style="color:#fb8c00">799</span></div><div class="stat-bar-bg"><div class="stat-bar-fill" style="width:100%;background:#fb8c00"></div></div></div>
      <div class="stat-item"><div class="stat-row"><span class="stat-name">ст.188 Ұрлық</span><span class="stat-val" style="color:#e53935">393</span></div><div class="stat-bar-bg"><div class="stat-bar-fill" style="width:49%;background:#e53935"></div></div></div>
      <div class="stat-item"><div class="stat-row"><span class="stat-name">ст.109-1 Денсаулыққа зиян</span><span class="stat-val" style="color:#f9a825">239</span></div><div class="stat-bar-bg"><div class="stat-bar-fill" style="width:30%;background:#f9a825"></div></div></div>
      <div class="stat-item"><div class="stat-row"><span class="stat-name">ст.296 Бұзақылық</span><span class="stat-val" style="color:#8e24aa">130</span></div><div class="stat-bar-bg"><div class="stat-bar-fill" style="width:16%;background:#8e24aa"></div></div></div>
      <div class="stat-item"><div class="stat-row"><span class="stat-name">ст.108-1 Зорлық</span><span class="stat-val" style="color:#0288d1">99</span></div><div class="stat-bar-bg"><div class="stat-bar-fill" style="width:12%;background:#0288d1"></div></div></div>
      <div class="stat-item"><div class="stat-row"><span class="stat-name">ст.345 Қарсылық</span><span class="stat-val" style="color:#6d4c41">59</span></div><div class="stat-bar-bg"><div class="stat-bar-fill" style="width:7%;background:#6d4c41"></div></div></div>
      <div class="stat-item"><div class="stat-row"><span class="stat-name">ст.107 Дене жарақаты</span><span class="stat-val" style="color:#c62828">56</span></div><div class="stat-bar-bg"><div class="stat-bar-fill" style="width:7%;background:#c62828"></div></div></div>
      <div class="stat-item"><div class="stat-row"><span class="stat-name">ст.293 Тонау</span><span class="stat-val" style="color:#e65100">37</span></div><div class="stat-bar-bg"><div class="stat-bar-fill" style="width:5%;background:#e65100"></div></div></div>
      <div class="stat-item"><div class="stat-row"><span class="stat-name">ст.139 Кісі өлтіру</span><span class="stat-val" style="color:#b71c1c">36</span></div><div class="stat-bar-bg"><div class="stat-bar-fill" style="width:5%;background:#b71c1c"></div></div></div>
    </div>

    <div class="s-section">
      <div class="s-title">Деректер базасы</div>
      <div class="db-status"><div class="db-dot"></div>localStorage — белсенді</div>
      <div id="db-info" style="font-size:10px;color:var(--text-muted);margin-top:3px">Оқиғалар: <b style="color:var(--text-primary)">283</b> (қол: 0, авто: 283)<br>Ғимараттар: <b style="color:#6a1b9a">21</b> · Камералар: <b style="color:#0277bd">42</b></div>
      <button class="analytics-btn" onclick="openAnalytics()">📊 Толық аналитика</button>
      <button class="export-btn" onclick="exportCSV()">📤 CSV жүктеп алу</button>
      <button class="btn-reset" style="margin-top:4px" onclick="clearDB()">🗑 Базаны тазалау</button>
    </div>

    <div class="s-section">
      <div class="s-title">Патруль бірліктері</div>
      <div id="units-list"><div class="unit-row"><div style="font-size:14px">🚔</div><div class="unit-info"><div class="unit-name">ПМ-001</div><div class="unit-street">Абай даңғылы — Солтүстік</div></div><div class="badge badge-patrol">ПАТРУЛЬ</div></div><div class="unit-row"><div style="font-size:14px">🚔</div><div class="unit-info"><div class="unit-name">ПМ-002</div><div class="unit-street">Абай — Манкент диагональ</div></div><div class="badge badge-patrol">ПАТРУЛЬ</div></div><div class="unit-row"><div style="font-size:14px">🚔</div><div class="unit-info"><div class="unit-name">ПМ-003</div><div class="unit-street">Аль-Фараби — Орталық</div></div><div class="badge badge-patrol">ПАТРУЛЬ</div></div><div class="unit-row"><div style="font-size:14px">🚔</div><div class="unit-info"><div class="unit-name">ПМ-004</div><div class="unit-street">Каратаевская — Батыс</div></div><div class="badge badge-patrol">ПАТРУЛЬ</div></div><div class="unit-row"><div style="font-size:14px">🚔</div><div class="unit-info"><div class="unit-name">ПМ-005</div><div class="unit-street">Еңбекшілер — Солтүстік</div></div><div class="badge badge-patrol">ПАТРУЛЬ</div></div><div class="unit-row"><div style="font-size:14px">🚔</div><div class="unit-info"><div class="unit-name">ПМ-006</div><div class="unit-street">Туран — Аль-Фараби шекарасы</div></div><div class="badge badge-patrol">ПАТРУЛЬ</div></div><div class="unit-row"><div style="font-size:14px">🚔</div><div class="unit-info"><div class="unit-name">ПМ-007</div><div class="unit-street">Еңбекшілер — Оңтүстік</div></div><div class="badge badge-patrol">ПАТРУЛЬ</div></div><div class="unit-row"><div style="font-size:14px">🚔</div><div class="unit-info"><div class="unit-name">ПМ-008</div><div class="unit-street">Абай — Солтүстік-шығыс</div></div><div class="badge badge-patrol">ПАТРУЛЬ</div></div><div class="unit-row"><div style="font-size:14px">🚔</div><div class="unit-info"><div class="unit-name">ПМ-009</div><div class="unit-street">Аль-Фараби — Оңтүстік-батыс</div></div><div class="badge badge-patrol">ПАТРУЛЬ</div></div><div class="unit-row"><div style="font-size:14px">🚔</div><div class="unit-info"><div class="unit-name">ПМ-010</div><div class="unit-street">Аль-Фараби — Оңтүстік маршрут</div></div><div class="badge badge-patrol">ПАТРУЛЬ</div></div></div>
    </div>
  </div>
</div>

<div style="flex:1;position:relative;">
  <div id="map" style="width: 100%; height: 100%; position: relative;" class="leaflet-container leaflet-touch leaflet-fade-anim leaflet-grab leaflet-touch-drag leaflet-touch-zoom" tabindex="0"><div class="leaflet-pane leaflet-map-pane" style="transform: translate3d(-2488px, 183px, 0px);"><div class="leaflet-pane leaflet-tile-pane"><div class="leaflet-layer " style="z-index: 1; opacity: 1;"><div class="leaflet-tile-container leaflet-zoom-animated" style="z-index: 16; transform: translate3d(1614px, 84px, 0px) scale(0.25);"></div><div class="leaflet-tile-container leaflet-zoom-animated" style="z-index: 18; transform: translate3d(0px, 0px, 0px) scale(1);"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3030.png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(2930px, -144px, 0px); opacity: 1;"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3030(1).png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(3186px, -144px, 0px); opacity: 1;"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3031.png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(2930px, 112px, 0px); opacity: 1;"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3031(1).png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(3186px, 112px, 0px); opacity: 1;"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3029.png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(2930px, -400px, 0px); opacity: 1;"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3029(1).png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(3186px, -400px, 0px); opacity: 1;"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3030(2).png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(2674px, -144px, 0px); opacity: 1;"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3030(3).png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(3442px, -144px, 0px); opacity: 1;"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3031(2).png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(2674px, 112px, 0px); opacity: 1;"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3031(3).png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(3442px, 112px, 0px); opacity: 1;"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3032.png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(2930px, 368px, 0px); opacity: 1;"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3032(1).png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(3186px, 368px, 0px); opacity: 1;"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3029(2).png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(2674px, -400px, 0px); opacity: 1;"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3029(3).png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(3442px, -400px, 0px); opacity: 1;"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3032(2).png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(2674px, 368px, 0px); opacity: 1;"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3032(3).png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(3442px, 368px, 0px); opacity: 1;"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3030(4).png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(2418px, -144px, 0px); opacity: 1;"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3030(5).png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(3698px, -144px, 0px); opacity: 1;"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3031(4).png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(2418px, 112px, 0px); opacity: 1;"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3031(5).png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(3698px, 112px, 0px); opacity: 1;"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3029(4).png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(2418px, -400px, 0px); opacity: 1;"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3029(5).png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(3698px, -400px, 0px); opacity: 1;"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3032(4).png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(2418px, 368px, 0px); opacity: 1;"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3032(5).png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(3698px, 368px, 0px); opacity: 1;"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3033.png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(2930px, 624px, 0px); opacity: 1;"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3033(1).png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(3186px, 624px, 0px); opacity: 1;"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3033(2).png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(2674px, 624px, 0px); opacity: 1;"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3033(3).png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(3442px, 624px, 0px); opacity: 1;"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3033(4).png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(2418px, 624px, 0px); opacity: 1;"><img alt="" src="./Шымкент — Қауіпсіздік мониторингі v7_files/3033(5).png" class="leaflet-tile leaflet-tile-loaded" style="width: 256px; height: 256px; transform: translate3d(3698px, 624px, 0px); opacity: 1;"></div></div></div><div class="leaflet-pane leaflet-overlay-pane"><svg pointer-events="none" class="leaflet-zoom-animated" width="1602" height="1057" viewBox="2355 -271 1602 1057" style="transform: translate3d(2355px, -271px, 0px);"><g><path class="leaflet-interactive" stroke="#7b1fa2" stroke-opacity="0.35" stroke-width="3" stroke-linecap="round" stroke-linejoin="round" stroke-dasharray="6,5" fill="none" d="M3289 -266L3201 -61L3184 -37L3003 -92L2893 -37L3003 -92L3184 -37L3201 -61"></path><path class="leaflet-interactive" stroke="#7b1fa2" stroke-opacity="0.35" stroke-width="3" stroke-linecap="round" stroke-linejoin="round" stroke-dasharray="6,5" fill="none" d="M3178 -37L3364 18L3411 128L3364 18"></path><path class="leaflet-interactive" stroke="#7b1fa2" stroke-opacity="0.35" stroke-width="3" stroke-linecap="round" stroke-linejoin="round" stroke-dasharray="6,5" fill="none" d="M3364 262L3411 128L3364 18L3190 -37L3364 18L3411 128"></path><path class="leaflet-interactive" stroke="#7b1fa2" stroke-opacity="0.35" stroke-width="3" stroke-linecap="round" stroke-linejoin="round" stroke-dasharray="6,5" fill="none" d="M2747 -69L2782 -29L2817 26L2875 49L2817 26L2782 -29"></path><path class="leaflet-interactive" stroke="#7b1fa2" stroke-opacity="0.35" stroke-width="3" stroke-linecap="round" stroke-linejoin="round" stroke-dasharray="6,5" fill="none" d="M3108 176L3195 207L3230 105L3137 81L3120 136L3091 168L3108 176"></path><path class="leaflet-interactive" stroke="#7b1fa2" stroke-opacity="0.35" stroke-width="3" stroke-linecap="round" stroke-linejoin="round" stroke-dasharray="6,5" fill="none" d="M3090 -271L3027 -85"></path><path class="leaflet-interactive" stroke="#7b1fa2" stroke-opacity="0.35" stroke-width="3" stroke-linecap="round" stroke-linejoin="round" stroke-dasharray="6,5" fill="none" d="M3061 160L3009 26L2945 -53L3009 26"></path><path class="leaflet-interactive" stroke="#7b1fa2" stroke-opacity="0.35" stroke-width="3" stroke-linecap="round" stroke-linejoin="round" stroke-dasharray="6,5" fill="none" d="M0 0"></path><path class="leaflet-interactive" stroke="#7b1fa2" stroke-opacity="0.35" stroke-width="3" stroke-linecap="round" stroke-linejoin="round" stroke-dasharray="6,5" fill="none" d="M2985 531L3009 489L2977 471L2940 455L2922 486L2936 504L2943 508L2967 511L2985 531L2967 511L2943 508L2936 504L2922 486L2940 455L2977 471L3009 489"></path><path class="leaflet-interactive" stroke="#7b1fa2" stroke-opacity="0.35" stroke-width="3" stroke-linecap="round" stroke-linejoin="round" stroke-dasharray="6,5" fill="none" d="M2984 539L2910 745L2921 766L2970 786M2970 786L2921 766L2910 745"></path><path class="leaflet-interactive" stroke="#00838f" stroke-opacity="1" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" fill="#00838f" fill-opacity="0.1" fill-rule="evenodd" d="M2718 98L2685 118L2652 74L2609 44L2588 25L2557 18L2546 13L2455 -6L2440 -7L2429 -14L2429 -34L2362 -47L2353 -54L2353 789L2777 789L2797 727L2927 402L2994 254L3024 177L3059 155L3072 135z"></path><path class="leaflet-interactive" stroke="#1565c0" stroke-opacity="1" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" fill="#1565c0" fill-opacity="0.1" fill-rule="evenodd" d="M3240 -152L3291 -266L3291 -273L2353 -273L2353 -60L2379 -41L2473 -4L2560 34L2607 46L2667 100L2766 151L2892 8L2938 -62L2998 -98L3047 -140L3139 -176L3236 -145L3240 -152z"></path><path class="leaflet-interactive" stroke="#7b1fa2" stroke-opacity="1" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" fill="#7b1fa2" fill-opacity="0.1" fill-rule="evenodd" d="M3238 -145L3289 -273L3960 -273L3960 444L3902 460L3850 467L3854 342L3853 231L3812 195L3805 106L3790 85L3778 36L3712 -46L3649 -55L3425 47L3435 27L3400 -37L3388 -46L3328 -48L3287 -61L3306 -122L3238 -146z"></path><path class="leaflet-interactive" stroke="#e53935" stroke-opacity="1" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" fill="#e53935" fill-opacity="0.1" fill-rule="evenodd" d="M3095 61L3233 104L3287 -61L3392 -46L3400 -37L3435 27L3424 47L3329 87L3315 194L3285 289L3205 316L3152 397L3087 442L3066 495L3091 520L3102 575L3099 669L3083 757L3085 790L2776 790L2797 727L2927 402L2994 254L3072 136z"></path><path class="leaflet-interactive" stroke="#2e7d32" stroke-opacity="1" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" fill="#2e7d32" fill-opacity="0.1" fill-rule="evenodd" d="M3960 789L3960 441L3850 467L3853 231L3812 195L3805 106L3761 16L3623 -44L3328 85L3246 277L3229 302L3191 329L3062 469L3067 496L3095 520L3102 575L3099 669L3078 789z"></path></g></svg></div><div class="leaflet-pane leaflet-shadow-pane"></div><div class="leaflet-pane leaflet-marker-pane"><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(3058px, 184px, 0px); z-index: 184;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(3085px, 159px, 0px); z-index: 159;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(3021px, 203px, 0px); z-index: 203;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(2986px, 247px, 0px); z-index: 247;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(3108px, 136px, 0px); z-index: 136;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(3161px, 97px, 0px); z-index: 97;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(3061px, 42px, 0px); z-index: 42;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(2945px, 168px, 0px); z-index: 168;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(3038px, 231px, 0px); z-index: 231;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(3102px, -6px, 0px); z-index: -6;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(3102px, 278px, 0px); z-index: 278;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(3061px, 333px, 0px); z-index: 333;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(2898px, 81px, 0px); z-index: 81;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(2828px, -61px, 0px); z-index: -61;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(3248px, 18px, 0px); z-index: 18;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(3190px, 199px, 0px); z-index: 199;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(3131px, 262px, 0px); z-index: 262;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(2986px, 136px, 0px); z-index: 136;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(3102px, 183px, 0px); z-index: 183;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(2986px, -14px, 0px); z-index: -14;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(3032px, 112px, 0px); z-index: 112;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(3009px, 168px, 0px); z-index: 168;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(3190px, 65px, 0px); z-index: 65;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(3015px, 380px, 0px); z-index: 380;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(2957px, -116px, 0px); z-index: -116;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(2840px, -195px, 0px); z-index: -195;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(3131px, -61px, 0px); z-index: -61;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(2945px, 246px, 0px); z-index: 246;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(3161px, 152px, 0px); z-index: 152;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(3003px, 49px, 0px); z-index: 49;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(3085px, 191px, 0px); z-index: 191;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(2951px, -6px, 0px); z-index: -6;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(3044px, -140px, 0px); z-index: -140;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(3190px, 278px, 0px); z-index: 278;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(2665px, -258px, 0px); z-index: -258;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(2753px, -353px, 0px); z-index: -353;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(2957px, 325px, 0px); z-index: 325;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(3056px, 128px, 0px); z-index: 128;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(2992px, 223px, 0px); z-index: 223;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(3091px, 26px, 0px); z-index: 26;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(2887px, -69px, 0px); z-index: -69;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -7px; margin-top: -7px; width: 14px; height: 14px; transform: translate3d(3201px, 105px, 0px); z-index: 105;"><div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(2957px, 42px, 0px); z-index: 42;"><div style="background:#fff;border:2px solid #2e7d32;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(2898px, -329px, 0px); z-index: -329;"><div style="background:#fff;border:2px solid #2e7d32;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3073px, 239px, 0px); z-index: 239;"><div style="background:#fff;border:2px solid #2e7d32;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3161px, 333px, 0px); z-index: 333;"><div style="background:#fff;border:2px solid #2e7d32;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3306px, -234px, 0px); z-index: -234;"><div style="background:#fff;border:2px solid #2e7d32;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3248px, -431px, 0px); z-index: -431;"><div style="background:#fff;border:2px solid #2e7d32;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(2549px, -155px, 0px); z-index: -155;"><div style="background:#fff;border:2px solid #2e7d32;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(2374px, 42px, 0px); z-index: 42;"><div style="background:#fff;border:2px solid #2e7d32;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(2782px, 176px, 0px); z-index: 176;"><div style="background:#fff;border:2px solid #2e7d32;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(2724px, 278px, 0px); z-index: 278;"><div style="background:#fff;border:2px solid #2e7d32;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(2840px, -510px, 0px); z-index: -510;"><div style="background:#fff;border:2px solid #2e7d32;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3027px, 184px, 0px); z-index: 184;"><div style="background:#fff;border:2px solid #2e7d32;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9.5px; margin-top: -9.5px; width: 19px; height: 19px; transform: translate3d(3102px, 176px, 0px); z-index: 176;"><div style="background:#fff;border:2px solid #00897b;border-radius:4px;width:17px;height:17px;display:flex;align-items:center;justify-content:center;font-size:10px">🏥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9.5px; margin-top: -9.5px; width: 19px; height: 19px; transform: translate3d(3027px, 278px, 0px); z-index: 278;"><div style="background:#fff;border:2px solid #00897b;border-radius:4px;width:17px;height:17px;display:flex;align-items:center;justify-content:center;font-size:10px">🏥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9.5px; margin-top: -9.5px; width: 19px; height: 19px; transform: translate3d(3131px, 65px, 0px); z-index: 65;"><div style="background:#fff;border:2px solid #00897b;border-radius:4px;width:17px;height:17px;display:flex;align-items:center;justify-content:center;font-size:10px">🏥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9.5px; margin-top: -9.5px; width: 19px; height: 19px; transform: translate3d(3015px, -37px, 0px); z-index: -37;"><div style="background:#fff;border:2px solid #00897b;border-radius:4px;width:17px;height:17px;display:flex;align-items:center;justify-content:center;font-size:10px">🏥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9.5px; margin-top: -9.5px; width: 19px; height: 19px; transform: translate3d(3102px, 357px, 0px); z-index: 357;"><div style="background:#fff;border:2px solid #00897b;border-radius:4px;width:17px;height:17px;display:flex;align-items:center;justify-content:center;font-size:10px">🏥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9.5px; margin-top: -9.5px; width: 19px; height: 19px; transform: translate3d(3190px, -155px, 0px); z-index: -155;"><div style="background:#fff;border:2px solid #00897b;border-radius:4px;width:17px;height:17px;display:flex;align-items:center;justify-content:center;font-size:10px">🏥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9.5px; margin-top: -9.5px; width: 19px; height: 19px; transform: translate3d(2927px, 199px, 0px); z-index: 199;"><div style="background:#fff;border:2px solid #00897b;border-radius:4px;width:17px;height:17px;display:flex;align-items:center;justify-content:center;font-size:10px">🏥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9.5px; margin-top: -9.5px; width: 19px; height: 19px; transform: translate3d(2665px, -313px, 0px); z-index: -313;"><div style="background:#fff;border:2px solid #00897b;border-radius:4px;width:17px;height:17px;display:flex;align-items:center;justify-content:center;font-size:10px">🏥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9.5px; margin-top: -9.5px; width: 19px; height: 19px; transform: translate3d(3219px, 262px, 0px); z-index: 262;"><div style="background:#fff;border:2px solid #00897b;border-radius:4px;width:17px;height:17px;display:flex;align-items:center;justify-content:center;font-size:10px">🏥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3061px, 144px, 0px); z-index: 144;"><div style="background:#fff;border:2px solid #f57f17;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🏫</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3161px, 81px, 0px); z-index: 81;"><div style="background:#fff;border:2px solid #f57f17;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🏫</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3003px, 207px, 0px); z-index: 207;"><div style="background:#fff;border:2px solid #f57f17;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🏫</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(2992px, -6px, 0px); z-index: -6;"><div style="background:#fff;border:2px solid #f57f17;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🏫</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3102px, 254px, 0px); z-index: 254;"><div style="background:#fff;border:2px solid #f57f17;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🏫</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3161px, -77px, 0px); z-index: -77;"><div style="background:#fff;border:2px solid #f57f17;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🏫</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(2782px, -195px, 0px); z-index: -195;"><div style="background:#fff;border:2px solid #f57f17;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🏫</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(2840px, 120px, 0px); z-index: 120;"><div style="background:#fff;border:2px solid #f57f17;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🏫</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(2957px, 278px, 0px); z-index: 278;"><div style="background:#fff;border:2px solid #f57f17;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🏫</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3015px, -274px, 0px); z-index: -274;"><div style="background:#fff;border:2px solid #f57f17;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🏫</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3190px, 176px, 0px); z-index: 176;"><div style="background:#fff;border:2px solid #f57f17;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🏫</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3044px, 357px, 0px); z-index: 357;"><div style="background:#fff;border:2px solid #f57f17;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🏫</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(2898px, -116px, 0px); z-index: -116;"><div style="background:#fff;border:2px solid #f57f17;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🏫</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(2811px, -392px, 0px); z-index: -392;"><div style="background:#fff;border:2px solid #f57f17;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🏫</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3056px, 176px, 0px); z-index: 176;"><div style="background:#fff;border:2px solid #6d4c41;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🛒</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3091px, 120px, 0px); z-index: 120;"><div style="background:#fff;border:2px solid #6d4c41;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🛒</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3027px, 223px, 0px); z-index: 223;"><div style="background:#fff;border:2px solid #6d4c41;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🛒</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3120px, 18px, 0px); z-index: 18;"><div style="background:#fff;border:2px solid #6d4c41;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🛒</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(2957px, -77px, 0px); z-index: -77;"><div style="background:#fff;border:2px solid #6d4c41;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🛒</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3161px, 278px, 0px); z-index: 278;"><div style="background:#fff;border:2px solid #6d4c41;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🛒</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3003px, 89px, 0px); z-index: 89;"><div style="background:#fff;border:2px solid #6d4c41;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🛒</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3056px, 254px, 0px); z-index: 254;"><div style="background:#fff;border:2px solid #6d4c41;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🛒</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3058px, 184px, 0px); z-index: 184;"><div style="background:#fff;border:2px solid #fb8c00;border-radius:50%;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">💥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3161px, 97px, 0px); z-index: 97;"><div style="background:#fff;border:2px solid #fb8c00;border-radius:50%;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">💥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3102px, 278px, 0px); z-index: 278;"><div style="background:#fff;border:2px solid #fb8c00;border-radius:50%;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">💥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3102px, -6px, 0px); z-index: -6;"><div style="background:#fff;border:2px solid #fb8c00;border-radius:50%;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">💥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3108px, 136px, 0px); z-index: 136;"><div style="background:#fff;border:2px solid #fb8c00;border-radius:50%;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">💥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(2986px, 247px, 0px); z-index: 247;"><div style="background:#fff;border:2px solid #fb8c00;border-radius:50%;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">💥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3248px, 18px, 0px); z-index: 18;"><div style="background:#fff;border:2px solid #fb8c00;border-radius:50%;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">💥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3190px, 199px, 0px); z-index: 199;"><div style="background:#fff;border:2px solid #fb8c00;border-radius:50%;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">💥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3131px, 262px, 0px); z-index: 262;"><div style="background:#fff;border:2px solid #fb8c00;border-radius:50%;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">💥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(2828px, -61px, 0px); z-index: -61;"><div style="background:#fff;border:2px solid #fb8c00;border-radius:50%;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">💥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3015px, 380px, 0px); z-index: 380;"><div style="background:#fff;border:2px solid #fb8c00;border-radius:50%;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">💥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(2957px, -116px, 0px); z-index: -116;"><div style="background:#fff;border:2px solid #fb8c00;border-radius:50%;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">💥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(2840px, -195px, 0px); z-index: -195;"><div style="background:#fff;border:2px solid #fb8c00;border-radius:50%;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">💥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(2665px, -313px, 0px); z-index: -313;"><div style="background:#fff;border:2px solid #fb8c00;border-radius:50%;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">💥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(2898px, 81px, 0px); z-index: 81;"><div style="background:#fff;border:2px solid #fb8c00;border-radius:50%;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">💥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(2945px, 168px, 0px); z-index: 168;"><div style="background:#fff;border:2px solid #fb8c00;border-radius:50%;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">💥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3038px, 231px, 0px); z-index: 231;"><div style="background:#fff;border:2px solid #fb8c00;border-radius:50%;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">💥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(2986px, 160px, 0px); z-index: 160;"><div style="background:#fff;border:2px solid #fb8c00;border-radius:50%;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">💥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(2986px, -14px, 0px); z-index: -14;"><div style="background:#fff;border:2px solid #fb8c00;border-radius:50%;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">💥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(2665px, -258px, 0px); z-index: -258;"><div style="background:#fff;border:2px solid #fb8c00;border-radius:50%;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">💥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(2887px, -69px, 0px); z-index: -69;"><div style="background:#fff;border:2px solid #fb8c00;border-radius:50%;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">💥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(2782px, -550px, 0px); z-index: -550;"><div style="background:#fff;border:2px solid #fb8c00;border-radius:50%;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">💥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(2753px, -353px, 0px); z-index: -353;"><div style="background:#fff;border:2px solid #fb8c00;border-radius:50%;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">💥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3201px, 112px, 0px); z-index: 112;"><div style="background:#fff;border:2px solid #fb8c00;border-radius:50%;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">💥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -9px; margin-top: -9px; width: 18px; height: 18px; transform: translate3d(3102px, 183px, 0px); z-index: 183;"><div style="background:#fff;border:2px solid #fb8c00;border-radius:50%;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">💥</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -40px; margin-top: -11px; width: 80px; height: 22px; transform: translate3d(3200px, -59px, 0px); z-index: 941;"><div class="car-label">🚔 ПМ-001</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -40px; margin-top: -11px; width: 80px; height: 22px; transform: translate3d(3344px, 12px, 0px); z-index: 1012;"><div class="car-label">🚔 ПМ-002</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -40px; margin-top: -11px; width: 80px; height: 22px; transform: translate3d(3271px, -11px, 0px); z-index: 989;"><div class="car-label">🚔 ПМ-003</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -40px; margin-top: -11px; width: 80px; height: 22px; transform: translate3d(2831px, 32px, 0px); z-index: 1032;"><div class="car-label">🚔 ПМ-004</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -40px; margin-top: -11px; width: 80px; height: 22px; transform: translate3d(3213px, 157px, 0px); z-index: 1157;"><div class="car-label">🚔 ПМ-005</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -40px; margin-top: -11px; width: 80px; height: 22px; transform: translate3d(3040px, -125px, 0px); z-index: 875;"><div class="car-label">🚔 ПМ-006</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -40px; margin-top: -11px; width: 80px; height: 22px; transform: translate3d(2957px, -38px, 0px); z-index: 962;"><div class="car-label">🚔 ПМ-007</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -40px; margin-top: -11px; width: 80px; height: 22px; transform: translate3d(2870px, -460px, 0px); z-index: 540;"><div class="car-label">🚔 ПМ-008</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -40px; margin-top: -11px; width: 80px; height: 22px; transform: translate3d(2978px, 524px, 0px); z-index: 1524;"><div class="car-label">🚔 ПМ-009</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -40px; margin-top: -11px; width: 80px; height: 22px; transform: translate3d(2915px, 754px, 0px); z-index: 1754;"><div class="car-label">🚔 ПМ-010</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4229px, -103px, 0px); z-index: -103;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2286px, 747px, 0px); z-index: 747;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2544px, -535px, 0px); z-index: -535;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4249px, -260px, 0px); z-index: -260;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3960px, 603px, 0px); z-index: 603;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2198px, 646px, 0px); z-index: 646;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4031px, 677px, 0px); z-index: 677;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4212px, -240px, 0px); z-index: -240;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4190px, -83px, 0px); z-index: -83;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3943px, 655px, 0px); z-index: 655;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4047px, 641px, 0px); z-index: 641;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3133px, 907px, 0px); z-index: 907;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4045px, 627px, 0px); z-index: 627;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3010px, 910px, 0px); z-index: 910;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4058px, 657px, 0px); z-index: 657;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3944px, 748px, 0px); z-index: 748;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4066px, 681px, 0px); z-index: 681;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3016px, 938px, 0px); z-index: 938;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3995px, 693px, 0px); z-index: 693;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2545px, -407px, 0px); z-index: -407;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2559px, -373px, 0px); z-index: -373;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2492px, -505px, 0px); z-index: -505;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2466px, -385px, 0px); z-index: -385;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2246px, 690px, 0px); z-index: 690;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2196px, 760px, 0px); z-index: 760;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4232px, -226px, 0px); z-index: -226;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2976px, 752px, 0px); z-index: 752;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3082px, 877px, 0px); z-index: 877;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2441px, -510px, 0px); z-index: -510;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2505px, -409px, 0px); z-index: -409;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3077px, 764px, 0px); z-index: 764;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4142px, -223px, 0px); z-index: -223;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4034px, 605px, 0px); z-index: 605;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4157px, -184px, 0px); z-index: -184;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4155px, -278px, 0px); z-index: -278;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3032px, 736px, 0px); z-index: 736;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4058px, 673px, 0px); z-index: 673;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4022px, 705px, 0px); z-index: 705;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3082px, 782px, 0px); z-index: 782;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2204px, 776px, 0px); z-index: 776;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3123px, 860px, 0px); z-index: 860;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4165px, -183px, 0px); z-index: -183;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4124px, -203px, 0px); z-index: -203;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3039px, 753px, 0px); z-index: 753;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2495px, -367px, 0px); z-index: -367;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4222px, -166px, 0px); z-index: -166;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3911px, 627px, 0px); z-index: 627;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2219px, 677px, 0px); z-index: 677;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2291px, 819px, 0px); z-index: 819;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4179px, -188px, 0px); z-index: -188;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4222px, -131px, 0px); z-index: -131;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3129px, 892px, 0px); z-index: 892;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2478px, -427px, 0px); z-index: -427;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3095px, 827px, 0px); z-index: 827;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4063px, 616px, 0px); z-index: 616;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3049px, 892px, 0px); z-index: 892;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2181px, 731px, 0px); z-index: 731;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -15px; margin-top: -15px; width: 30px; height: 30px; transform: translate3d(3244px, 147px, 0px); z-index: 147;"><div style="background:#fff;border:2.5px solid #e53935;border-radius:7px;width:28px;height:28px;display:flex;align-items:center;justify-content:center;font-size:16px;box-shadow:0 2px 8px rgba(0,0,0,.2)" class="">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated" tabindex="0" role="button" style="margin-left: -100px; margin-top: -22px; width: 200px; height: 44px; transform: translate3d(2235px, 701px, 0px); z-index: 701;"><div style="text-align:center;pointer-events:none;user-select:none"><div style="font-family:&#39;Rubik&#39;,sans-serif;font-size:11px;font-weight:700;color:#00838f;text-shadow:0 0 5px #fff,0 1px 3px rgba(255,255,255,.95);letter-spacing:.5px;white-space:nowrap">ТУРАН АУДАНЫ</div><div style="font-family:&#39;JetBrains Mono&#39;,sans-serif;font-size:9px;color:#444;text-shadow:0 1px 3px rgba(255,255,255,.95);white-space:nowrap;margin-top:1px">👥 136&nbsp;000 · 🔍 320 іс</div></div></div><div class="leaflet-marker-icon leaflet-zoom-animated" tabindex="0" role="button" style="margin-left: -100px; margin-top: -22px; width: 200px; height: 44px; transform: translate3d(2514px, -472px, 0px); z-index: -472;"><div style="text-align:center;pointer-events:none;user-select:none"><div style="font-family:&#39;Rubik&#39;,sans-serif;font-size:11px;font-weight:700;color:#1565c0;text-shadow:0 0 5px #fff,0 1px 3px rgba(255,255,255,.95);letter-spacing:.5px;white-space:nowrap">АБАЙ АУДАНЫ</div><div style="font-family:&#39;JetBrains Mono&#39;,sans-serif;font-size:9px;color:#444;text-shadow:0 1px 3px rgba(255,255,255,.95);white-space:nowrap;margin-top:1px">👥 345&nbsp;761 · 🔍 511 іс</div></div></div><div class="leaflet-marker-icon leaflet-zoom-animated" tabindex="0" role="button" style="margin-left: -100px; margin-top: -22px; width: 200px; height: 44px; transform: translate3d(4166px, -185px, 0px); z-index: -185;"><div style="text-align:center;pointer-events:none;user-select:none"><div style="font-family:&#39;Rubik&#39;,sans-serif;font-size:11px;font-weight:700;color:#7b1fa2;text-shadow:0 0 5px #fff,0 1px 3px rgba(255,255,255,.95);letter-spacing:.5px;white-space:nowrap">ҚАРАТАУ АУДАНЫ</div><div style="font-family:&#39;JetBrains Mono&#39;,sans-serif;font-size:9px;color:#444;text-shadow:0 1px 3px rgba(255,255,255,.95);white-space:nowrap;margin-top:1px">👥 386&nbsp;000 · 🔍 356 іс</div></div></div><div class="leaflet-marker-icon leaflet-zoom-animated" tabindex="0" role="button" style="margin-left: -100px; margin-top: -22px; width: 200px; height: 44px; transform: translate3d(3060px, 824px, 0px); z-index: 824;"><div style="text-align:center;pointer-events:none;user-select:none"><div style="font-family:&#39;Rubik&#39;,sans-serif;font-size:11px;font-weight:700;color:#e53935;text-shadow:0 0 5px #fff,0 1px 3px rgba(255,255,255,.95);letter-spacing:.5px;white-space:nowrap">АЛЬ-ФАРАБИ АУДАНЫ</div><div style="font-family:&#39;JetBrains Mono&#39;,sans-serif;font-size:9px;color:#444;text-shadow:0 1px 3px rgba(255,255,255,.95);white-space:nowrap;margin-top:1px">👥 201&nbsp;573 · 🔍 402 іс</div></div></div><div class="leaflet-marker-icon leaflet-zoom-animated" tabindex="0" role="button" style="margin-left: -100px; margin-top: -22px; width: 200px; height: 44px; transform: translate3d(3998px, 641px, 0px); z-index: 641;"><div style="text-align:center;pointer-events:none;user-select:none"><div style="font-family:&#39;Rubik&#39;,sans-serif;font-size:11px;font-weight:700;color:#2e7d32;text-shadow:0 0 5px #fff,0 1px 3px rgba(255,255,255,.95);letter-spacing:.5px;white-space:nowrap">ЕҢБЕКШІЛЕР АУДАНЫ</div><div style="font-family:&#39;JetBrains Mono&#39;,sans-serif;font-size:9px;color:#444;text-shadow:0 1px 3px rgba(255,255,255,.95);white-space:nowrap;margin-top:1px">👥 204&nbsp;962 · 🔍 236 іс</div></div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4237px, -74px, 0px); z-index: -74;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3989px, 661px, 0px); z-index: 661;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3922px, 526px, 0px); z-index: 526;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2528px, -450px, 0px); z-index: -450;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3076px, 786px, 0px); z-index: 786;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4204px, -186px, 0px); z-index: -186;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4010px, 530px, 0px); z-index: 530;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2158px, 784px, 0px); z-index: 784;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2192px, 641px, 0px); z-index: 641;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4086px, -143px, 0px); z-index: -143;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3049px, 923px, 0px); z-index: 923;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2436px, -577px, 0px); z-index: -577;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2298px, 634px, 0px); z-index: 634;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3118px, 932px, 0px); z-index: 932;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -15px; margin-top: -15px; width: 30px; height: 30px; transform: translate3d(3160px, 196px, 0px); z-index: 196;"><div style="background:#fff;border:2.5px solid #e53935;border-radius:7px;width:28px;height:28px;display:flex;align-items:center;justify-content:center;font-size:16px;box-shadow:0 2px 8px rgba(0,0,0,.2)" class="">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3953px, 706px, 0px); z-index: 706;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2191px, 592px, 0px); z-index: 592;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2249px, 652px, 0px); z-index: 652;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2250px, 773px, 0px); z-index: 773;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2495px, -437px, 0px); z-index: -437;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3075px, 910px, 0px); z-index: 910;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -15px; margin-top: -15px; width: 30px; height: 30px; transform: translate3d(3126px, 227px, 0px); z-index: 227;"><div style="background:#fff;border:2.5px solid #e53935;border-radius:7px;width:28px;height:28px;display:flex;align-items:center;justify-content:center;font-size:16px;box-shadow:0 2px 8px rgba(0,0,0,.2)">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3989px, 631px, 0px); z-index: 631;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4119px, -252px, 0px); z-index: -252;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4115px, -181px, 0px); z-index: -181;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4027px, 671px, 0px); z-index: 671;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2265px, 807px, 0px); z-index: 807;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4143px, -129px, 0px); z-index: -129;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4246px, -236px, 0px); z-index: -236;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4170px, -100px, 0px); z-index: -100;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4173px, -175px, 0px); z-index: -175;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3928px, 559px, 0px); z-index: 559;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4162px, -225px, 0px); z-index: -225;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4079px, -155px, 0px); z-index: -155;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2581px, -396px, 0px); z-index: -396;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4194px, -149px, 0px); z-index: -149;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -15px; margin-top: -15px; width: 30px; height: 30px; transform: translate3d(3083px, 191px, 0px); z-index: 191;"><div style="background:#fff;border:2.5px solid #e53935;border-radius:7px;width:28px;height:28px;display:flex;align-items:center;justify-content:center;font-size:16px;box-shadow:0 2px 8px rgba(0,0,0,.2)">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4167px, -92px, 0px); z-index: -92;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4208px, -292px, 0px); z-index: -292;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2445px, -521px, 0px); z-index: -521;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4179px, -299px, 0px); z-index: -299;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2999px, 725px, 0px); z-index: 725;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4137px, -73px, 0px); z-index: -73;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3056px, 776px, 0px); z-index: 776;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2227px, 590px, 0px); z-index: 590;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2989px, 881px, 0px); z-index: 881;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3119px, 868px, 0px); z-index: 868;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4087px, -175px, 0px); z-index: -175;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2241px, 618px, 0px); z-index: 618;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3002px, 902px, 0px); z-index: 902;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4073px, 664px, 0px); z-index: 664;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4079px, 561px, 0px); z-index: 561;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4147px, -211px, 0px); z-index: -211;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4200px, -82px, 0px); z-index: -82;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2267px, 770px, 0px); z-index: 770;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3033px, 751px, 0px); z-index: 751;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2219px, 700px, 0px); z-index: 700;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2488px, -399px, 0px); z-index: -399;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -15px; margin-top: -15px; width: 30px; height: 30px; transform: translate3d(3071px, 170px, 0px); z-index: 170;"><div style="background:#fff;border:2.5px solid #e53935;border-radius:7px;width:28px;height:28px;display:flex;align-items:center;justify-content:center;font-size:16px;box-shadow:0 2px 8px rgba(0,0,0,.2)">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3081px, 817px, 0px); z-index: 817;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2306px, 729px, 0px); z-index: 729;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3001px, 738px, 0px); z-index: 738;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4152px, -123px, 0px); z-index: -123;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4239px, -71px, 0px); z-index: -71;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3131px, 724px, 0px); z-index: 724;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3126px, 868px, 0px); z-index: 868;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2522px, -568px, 0px); z-index: -568;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2513px, -470px, 0px); z-index: -470;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4153px, -159px, 0px); z-index: -159;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -15px; margin-top: -15px; width: 30px; height: 30px; transform: translate3d(3047px, 177px, 0px); z-index: 177;"><div style="background:#fff;border:2.5px solid #e53935;border-radius:7px;width:28px;height:28px;display:flex;align-items:center;justify-content:center;font-size:16px;box-shadow:0 2px 8px rgba(0,0,0,.2)">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2254px, 667px, 0px); z-index: 667;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2565px, -561px, 0px); z-index: -561;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2555px, -471px, 0px); z-index: -471;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2583px, -388px, 0px); z-index: -388;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4240px, -77px, 0px); z-index: -77;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2433px, -560px, 0px); z-index: -560;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4076px, 538px, 0px); z-index: 538;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3972px, 561px, 0px); z-index: 561;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4121px, -141px, 0px); z-index: -141;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2992px, 708px, 0px); z-index: 708;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3004px, 814px, 0px); z-index: 814;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4194px, -127px, 0px); z-index: -127;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3069px, 888px, 0px); z-index: 888;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2217px, 624px, 0px); z-index: 624;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4051px, 726px, 0px); z-index: 726;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3080px, 893px, 0px); z-index: 893;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2988px, 723px, 0px); z-index: 723;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4106px, -200px, 0px); z-index: -200;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4199px, -273px, 0px); z-index: -273;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -15px; margin-top: -15px; width: 30px; height: 30px; transform: translate3d(3193px, 278px, 0px); z-index: 278;"><div style="background:#fff;border:2.5px solid #e53935;border-radius:7px;width:28px;height:28px;display:flex;align-items:center;justify-content:center;font-size:16px;box-shadow:0 2px 8px rgba(0,0,0,.2)" class="">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4032px, 593px, 0px); z-index: 593;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4079px, 605px, 0px); z-index: 605;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4137px, -171px, 0px); z-index: -171;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2522px, -377px, 0px); z-index: -377;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3997px, 594px, 0px); z-index: 594;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2578px, -416px, 0px); z-index: -416;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2989px, 789px, 0px); z-index: 789;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2494px, -577px, 0px); z-index: -577;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -15px; margin-top: -15px; width: 30px; height: 30px; transform: translate3d(3114px, 302px, 0px); z-index: 302;"><div style="background:#fff;border:2.5px solid #e53935;border-radius:7px;width:28px;height:28px;display:flex;align-items:center;justify-content:center;font-size:16px;box-shadow:0 2px 8px rgba(0,0,0,.2)">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3106px, 706px, 0px); z-index: 706;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2489px, -477px, 0px); z-index: -477;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2537px, -385px, 0px); z-index: -385;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -15px; margin-top: -15px; width: 30px; height: 30px; transform: translate3d(3178px, 335px, 0px); z-index: 335;"><div style="background:#fff;border:2.5px solid #e53935;border-radius:7px;width:28px;height:28px;display:flex;align-items:center;justify-content:center;font-size:16px;box-shadow:0 2px 8px rgba(0,0,0,.2)">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2524px, -569px, 0px); z-index: -569;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2311px, 599px, 0px); z-index: 599;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4123px, -234px, 0px); z-index: -234;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2214px, 611px, 0px); z-index: 611;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2315px, 762px, 0px); z-index: 762;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2536px, -442px, 0px); z-index: -442;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2297px, 799px, 0px); z-index: 799;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3127px, 904px, 0px); z-index: 904;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2537px, -520px, 0px); z-index: -520;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4099px, -68px, 0px); z-index: -68;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3086px, 929px, 0px); z-index: 929;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4151px, -236px, 0px); z-index: -236;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2451px, -513px, 0px); z-index: -513;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2578px, -523px, 0px); z-index: -523;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3078px, 835px, 0px); z-index: 835;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2552px, -379px, 0px); z-index: -379;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3946px, 629px, 0px); z-index: 629;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4005px, 736px, 0px); z-index: 736;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4239px, -194px, 0px); z-index: -194;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2272px, 665px, 0px); z-index: 665;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2278px, 739px, 0px); z-index: 739;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4158px, -279px, 0px); z-index: -279;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3034px, 759px, 0px); z-index: 759;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -15px; margin-top: -15px; width: 30px; height: 30px; transform: translate3d(3366px, -23px, 0px); z-index: -23;"><div style="background:#fff;border:2.5px solid #e53935;border-radius:7px;width:28px;height:28px;display:flex;align-items:center;justify-content:center;font-size:16px;box-shadow:0 2px 8px rgba(0,0,0,.2)">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2284px, 595px, 0px); z-index: 595;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3141px, 939px, 0px); z-index: 939;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4177px, -77px, 0px); z-index: -77;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4007px, 678px, 0px); z-index: 678;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2477px, -469px, 0px); z-index: -469;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -15px; margin-top: -15px; width: 30px; height: 30px; transform: translate3d(3338px, 29px, 0px); z-index: 29;"><div style="background:#fff;border:2.5px solid #e53935;border-radius:7px;width:28px;height:28px;display:flex;align-items:center;justify-content:center;font-size:16px;box-shadow:0 2px 8px rgba(0,0,0,.2)" class="">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4106px, -250px, 0px); z-index: -250;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3956px, 727px, 0px); z-index: 727;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2156px, 739px, 0px); z-index: 739;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4103px, -192px, 0px); z-index: -192;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -15px; margin-top: -15px; width: 30px; height: 30px; transform: translate3d(3360px, 52px, 0px); z-index: 52;"><div style="background:#fff;border:2.5px solid #e53935;border-radius:7px;width:28px;height:28px;display:flex;align-items:center;justify-content:center;font-size:16px;box-shadow:0 2px 8px rgba(0,0,0,.2)">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3975px, 636px, 0px); z-index: 636;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4250px, -156px, 0px); z-index: -156;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2987px, 727px, 0px); z-index: 727;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4088px, -212px, 0px); z-index: -212;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2524px, -576px, 0px); z-index: -576;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3146px, 796px, 0px); z-index: 796;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2545px, -519px, 0px); z-index: -519;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3091px, 798px, 0px); z-index: 798;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2176px, 616px, 0px); z-index: 616;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2312px, 789px, 0px); z-index: 789;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3962px, 631px, 0px); z-index: 631;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2435px, -534px, 0px); z-index: -534;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2979px, 934px, 0px); z-index: 934;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2477px, -499px, 0px); z-index: -499;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4185px, -256px, 0px); z-index: -256;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3125px, 779px, 0px); z-index: 779;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4219px, -133px, 0px); z-index: -133;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2220px, 756px, 0px); z-index: 756;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4152px, -150px, 0px); z-index: -150;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3014px, 928px, 0px); z-index: 928;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3982px, 654px, 0px); z-index: 654;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4165px, -231px, 0px); z-index: -231;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2237px, 747px, 0px); z-index: 747;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2440px, -461px, 0px); z-index: -461;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3916px, 621px, 0px); z-index: 621;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3961px, 566px, 0px); z-index: 566;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2244px, 681px, 0px); z-index: 681;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3928px, 706px, 0px); z-index: 706;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2498px, -539px, 0px); z-index: -539;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4096px, -204px, 0px); z-index: -204;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2179px, 793px, 0px); z-index: 793;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -15px; margin-top: -15px; width: 30px; height: 30px; transform: translate3d(3054px, 283px, 0px); z-index: 283;"><div style="background:#fff;border:2.5px solid #e53935;border-radius:7px;width:28px;height:28px;display:flex;align-items:center;justify-content:center;font-size:16px;box-shadow:0 2px 8px rgba(0,0,0,.2)">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4156px, -225px, 0px); z-index: -225;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3074px, 846px, 0px); z-index: 846;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4251px, -131px, 0px); z-index: -131;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2493px, -378px, 0px); z-index: -378;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -15px; margin-top: -15px; width: 30px; height: 30px; transform: translate3d(3012px, 282px, 0px); z-index: 282;"><div style="background:#fff;border:2.5px solid #e53935;border-radius:7px;width:28px;height:28px;display:flex;align-items:center;justify-content:center;font-size:16px;box-shadow:0 2px 8px rgba(0,0,0,.2)">🏢</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2224px, 678px, 0px); z-index: 678;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2236px, 684px, 0px); z-index: 684;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3081px, 800px, 0px); z-index: 800;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4092px, -163px, 0px); z-index: -163;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -15px; margin-top: -15px; width: 30px; height: 30px; transform: translate3d(3028px, 315px, 0px); z-index: 315;"><div style="background:#fff;border:2.5px solid #e53935;border-radius:7px;width:28px;height:28px;display:flex;align-items:center;justify-content:center;font-size:16px;box-shadow:0 2px 8px rgba(0,0,0,.2)">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4067px, 706px, 0px); z-index: 706;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2163px, 799px, 0px); z-index: 799;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -15px; margin-top: -15px; width: 30px; height: 30px; transform: translate3d(2979px, 350px, 0px); z-index: 350;"><div style="background:#fff;border:2.5px solid #e53935;border-radius:7px;width:28px;height:28px;display:flex;align-items:center;justify-content:center;font-size:16px;box-shadow:0 2px 8px rgba(0,0,0,.2)">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3945px, 584px, 0px); z-index: 584;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3076px, 867px, 0px); z-index: 867;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4196px, -252px, 0px); z-index: -252;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2297px, 589px, 0px); z-index: 589;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2490px, -557px, 0px); z-index: -557;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2451px, -566px, 0px); z-index: -566;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2493px, -560px, 0px); z-index: -560;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -15px; margin-top: -15px; width: 30px; height: 30px; transform: translate3d(2985px, 479px, 0px); z-index: 479;"><div style="background:#fff;border:2.5px solid #e53935;border-radius:7px;width:28px;height:28px;display:flex;align-items:center;justify-content:center;font-size:16px;box-shadow:0 2px 8px rgba(0,0,0,.2)">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3122px, 742px, 0px); z-index: 742;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4068px, 759px, 0px); z-index: 759;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3921px, 531px, 0px); z-index: 531;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2304px, 799px, 0px); z-index: 799;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4060px, 689px, 0px); z-index: 689;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2478px, -508px, 0px); z-index: -508;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -15px; margin-top: -15px; width: 30px; height: 30px; transform: translate3d(3116px, 325px, 0px); z-index: 325;"><div style="background:#fff;border:2.5px solid #e53935;border-radius:7px;width:28px;height:28px;display:flex;align-items:center;justify-content:center;font-size:16px;box-shadow:0 2px 8px rgba(0,0,0,.2)">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2427px, -405px, 0px); z-index: -405;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2260px, 787px, 0px); z-index: 787;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3125px, 918px, 0px); z-index: 918;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3128px, 782px, 0px); z-index: 782;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3073px, 745px, 0px); z-index: 745;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3977px, 704px, 0px); z-index: 704;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4252px, -174px, 0px); z-index: -174;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3113px, 884px, 0px); z-index: 884;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2587px, -581px, 0px); z-index: -581;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2166px, 672px, 0px); z-index: 672;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2260px, 764px, 0px); z-index: 764;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2203px, 792px, 0px); z-index: 792;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4237px, -239px, 0px); z-index: -239;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3944px, 690px, 0px); z-index: 690;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3982px, 740px, 0px); z-index: 740;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3125px, 799px, 0px); z-index: 799;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -15px; margin-top: -15px; width: 30px; height: 30px; transform: translate3d(3351px, -23px, 0px); z-index: -23;"><div style="background:#fff;border:2.5px solid #e53935;border-radius:7px;width:28px;height:28px;display:flex;align-items:center;justify-content:center;font-size:16px;box-shadow:0 2px 8px rgba(0,0,0,.2)">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2298px, 680px, 0px); z-index: 680;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4077px, 624px, 0px); z-index: 624;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2277px, 586px, 0px); z-index: 586;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4217px, -244px, 0px); z-index: -244;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2226px, 590px, 0px); z-index: 590;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2198px, 785px, 0px); z-index: 785;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3069px, 725px, 0px); z-index: 725;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -15px; margin-top: -15px; width: 30px; height: 30px; transform: translate3d(3401px, 35px, 0px); z-index: 35;"><div style="background:#fff;border:2.5px solid #e53935;border-radius:7px;width:28px;height:28px;display:flex;align-items:center;justify-content:center;font-size:16px;box-shadow:0 2px 8px rgba(0,0,0,.2)">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2197px, 811px, 0px); z-index: 811;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2547px, -426px, 0px); z-index: -426;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3915px, 553px, 0px); z-index: 553;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -15px; margin-top: -15px; width: 30px; height: 30px; transform: translate3d(3278px, -3px, 0px); z-index: -3;"><div style="background:#fff;border:2.5px solid #e53935;border-radius:7px;width:28px;height:28px;display:flex;align-items:center;justify-content:center;font-size:16px;box-shadow:0 2px 8px rgba(0,0,0,.2)">🏛</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3925px, 752px, 0px); z-index: 752;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2233px, 616px, 0px); z-index: 616;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3136px, 871px, 0px); z-index: 871;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2485px, -436px, 0px); z-index: -436;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2300px, 785px, 0px); z-index: 785;"><div style="background:#fff;border:3px solid #fdd835;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(2438px, -543px, 0px); z-index: -543;"><div style="background:#fff;border:3px solid #e53935;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(4150px, -122px, 0px); z-index: -122;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div><div class="leaflet-marker-icon leaflet-zoom-animated leaflet-interactive" tabindex="0" role="button" style="margin-left: -12px; margin-top: -12px; width: 24px; height: 24px; transform: translate3d(3998px, 644px, 0px); z-index: 644;"><div style="background:#fff;border:3px solid #fb8c00;border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div></div></div><div class="leaflet-pane leaflet-tooltip-pane"></div><div class="leaflet-pane leaflet-popup-pane"></div><div class="leaflet-proxy leaflet-zoom-animated" style="transform: translate3d(1.45405e+06px, 776082px, 0px) scale(4096);"></div></div><div class="leaflet-control-container"><div class="leaflet-top leaflet-left"><div class="leaflet-control-zoom leaflet-bar leaflet-control"><a class="leaflet-control-zoom-in" href="file:///C:/Users/FENOMEN/Downloads/Map%20(1).html#" title="Zoom in" role="button" aria-label="Zoom in" aria-disabled="false"><span aria-hidden="true">+</span></a><a class="leaflet-control-zoom-out" href="file:///C:/Users/FENOMEN/Downloads/Map%20(1).html#" title="Zoom out" role="button" aria-label="Zoom out" aria-disabled="false"><span aria-hidden="true">−</span></a></div></div><div class="leaflet-top leaflet-right"></div><div class="leaflet-bottom leaflet-left"></div><div class="leaflet-bottom leaflet-right"><div class="leaflet-control-attribution leaflet-control"><a href="https://leafletjs.com/" title="A JavaScript library for interactive maps"><svg aria-hidden="true" xmlns="http://www.w3.org/2000/svg" width="12" height="8" viewBox="0 0 12 8" class="leaflet-attribution-flag"><path fill="#4C7BE1" d="M0 0h12v4H0z"></path><path fill="#FFD500" d="M0 4h12v3H0z"></path><path fill="#E0BC00" d="M0 7h12v1H0z"></path></svg> Leaflet</a> <span aria-hidden="true">|</span> © OpenStreetMap &amp; CartoDB</div></div></div></div>
  <div id="osm-loader" class="hidden"><div class="osm-spin"></div><span id="osm-loader-text">⚠️ Резервтік шекаралар</span></div>
  <div id="mode-banner" class="bld-mode">
    <div class="mode-pulse"></div>
    <span id="mode-banner-text">🏢 Картадағы орынды басыңыз — ғимарат белгілеу үшін</span>
    <button class="mode-cancel-btn" onclick="cancelMode()">✕ Бас тарту</button>
  </div>
  <div id="focus-banner">
    <div class="fb-dot" id="fb-dot"></div>
    <span id="fb-name">Аудан</span>
    <span style="color:var(--text-muted);font-weight:400">·</span>
    <span id="fb-stats" style="color:var(--text-secondary);font-weight:400;font-size:10px"></span>
    <button class="fb-close" onclick="resetFocus()">✕</button>
  </div>
  <div id="empty-hint" class="hidden">
    <div class="hint-icon">📍</div>
    <div class="hint-title">Карта бос</div>
    <div class="hint-sub">Оқиға белгілеу үшін:<br><strong>📍 Белгілеу</strong> батырмасын басып,<br>картадағы орынды таңдаңыз<br><br>немесе <strong>🤖 Авто</strong> режимін қосыңыз</div>
  </div>
  <div id="heatmap-legend">
    <div class="hl-title">🌡 Қылмыс тығыздығы</div>
    <div class="hl-bar"></div>
    <div class="hl-labels"><span>Төмен</span><span>Орта</span><span>Жоғары</span></div>
  </div>
</div>

<div id="panel-right">
  <div class="panel-tabs">
    <button class="tab-btn active" onclick="switchTab(&#39;feed&#39;,this)">Оқиғалар</button>
    <button class="tab-btn" onclick="switchTab(&#39;buildings&#39;,this)">Ғимараттар</button>
    <button class="tab-btn" onclick="switchTab(&#39;stats&#39;,this)">Статистика</button>
    <button class="tab-btn" onclick="switchTab(&#39;district&#39;,this)">Аудан</button>
  </div>
  <div class="tab-content active" id="tab-feed"><div id="incident-feed">
    <div class="inc-item sev-med" onclick="map.setView([42.25854714394999,69.7487310138566],17)" style="cursor:pointer">
      <div class="inc-type med">ст.296<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Ленгер жолы</div>
      <div class="inc-time">🕐 15:08<span class="inc-district" style="background:#2e7d3222;color:#2e7d32">Еңбекшілер ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778062093100_b8vl&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.355700229913644,69.77488131374443],17)" style="cursor:pointer">
      <div class="inc-type med">БҰЗАҚЫЛЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Момышұлы к-сі</div>
      <div class="inc-time">🕐 15:08<span class="inc-district" style="background:#7b1fa222;color:#7b1fa2">Қаратау ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778062082001_uvf8&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-high" onclick="map.setView([42.409119177476896,69.48090834271274],17)" style="cursor:pointer">
      <div class="inc-type high">ст.109-1<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Зоопарк маңы</div>
      <div class="inc-time">🕐 15:07<span class="inc-district" style="background:#1565c022;color:#1565c0">Абай ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778062069450_9jj6&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-low" onclick="map.setView([42.240580417391996,69.45720995861758],17)" style="cursor:pointer">
      <div class="inc-type low">ЖКО<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Рысқұлов к-сі</div>
      <div class="inc-time">🕐 15:07<span class="inc-district" style="background:#00838f22;color:#00838f">Туран ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778062044191_ptxj&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.39559691261153,69.48907708159274],17)" style="cursor:pointer">
      <div class="inc-type med">БҰЗАҚЫЛЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Таскешу жолы</div>
      <div class="inc-time">🕐 15:07<span class="inc-district" style="background:#1565c022;color:#1565c0">Абай ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778062030200_idwx&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-high" onclick="map.setView([42.22965497253127,69.60084148020925],17)" style="cursor:pointer">
      <div class="inc-type high">ст.108-1<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Рысқұлов к-сі</div>
      <div class="inc-time">🕐 15:06<span class="inc-district" style="background:#e5393522;color:#e53935">Аль-Фараби ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778062015201_v4vk&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-high" onclick="map.setView([42.262014819772226,69.44580227412222],17)" style="cursor:pointer">
      <div class="inc-type high">ст.108-1<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 3 мкр</div>
      <div class="inc-time">🕐 15:06<span class="inc-district" style="background:#00838f22;color:#00838f">Туран ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778062004192_y3wg&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.24475673995293,69.73617485965576],17)" style="cursor:pointer">
      <div class="inc-type med">ст.293<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Карасу жолы</div>
      <div class="inc-time">🕐 15:06<span class="inc-district" style="background:#2e7d3222;color:#2e7d32">Еңбекшілер ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061991201_4hdz&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.270104221483734,69.73449674735672],17)" style="cursor:pointer">
      <div class="inc-type med">ст.109-1<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Манкент тас жолы</div>
      <div class="inc-time">🕐 15:06<span class="inc-district" style="background:#2e7d3222;color:#2e7d32">Еңбекшілер ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061979972_xfqw&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.39432590605536,69.4996680040233],17)" style="cursor:pointer">
      <div class="inc-type med">ст.296<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Манкент тас жолы</div>
      <div class="inc-time">🕐 15:06<span class="inc-district" style="background:#1565c022;color:#1565c0">Абай ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061965889_rfq0&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-low" onclick="map.setView([42.23730667111501,69.4395579517257],17)" style="cursor:pointer">
      <div class="inc-type low">ст.293<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Рысқұлов к-сі</div>
      <div class="inc-time">🕐 15:05<span class="inc-district" style="background:#00838f22;color:#00838f">Туран ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061951197_wo5n&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.24817633150328,69.58926456858289],17)" style="cursor:pointer">
      <div class="inc-type med">ст.296<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Ордабасы базары маңы</div>
      <div class="inc-time">🕐 15:05<span class="inc-district" style="background:#e5393522;color:#e53935">Аль-Фараби ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061935826_pvk6&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-low" onclick="map.setView([42.240606030429454,69.43983186757798],17)" style="cursor:pointer">
      <div class="inc-type low">ст.108-1<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Рысқұлов к-сі</div>
      <div class="inc-time">🕐 15:05<span class="inc-district" style="background:#00838f22;color:#00838f">Туран ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061923423_yjrk&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.265387949613135,69.44458252362497],17)" style="cursor:pointer">
      <div class="inc-type med">АЛАЯҚТЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Рысқұлов к-сі</div>
      <div class="inc-time">🕐 15:05<span class="inc-district" style="background:#00838f22;color:#00838f">Туран ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061909192_5sd3&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-low" onclick="map.setView([42.37128337251988,69.7864189977986],17)" style="cursor:pointer">
      <div class="inc-type low">ст.293<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Байтерек батыс</div>
      <div class="inc-time">🕐 15:04<span class="inc-district" style="background:#7b1fa222;color:#7b1fa2">Қаратау ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061897180_jbgf&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-low" onclick="map.setView([42.2659041511405,69.45337069296062],17)" style="cursor:pointer">
      <div class="inc-type low">БҰЗАҚЫЛЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Желтоқсан к-сі</div>
      <div class="inc-time">🕐 15:04<span class="inc-district" style="background:#00838f22;color:#00838f">Туран ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061885195_xo14&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-low" onclick="map.setView([42.261099889079766,69.76228164542637],17)" style="cursor:pointer">
      <div class="inc-type low">ҰРЛЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Самал мкр</div>
      <div class="inc-time">🕐 15:04<span class="inc-district" style="background:#2e7d3222;color:#2e7d32">Еңбекшілер ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061873189_2kt1&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.25395217200253,69.45694083305835],17)" style="cursor:pointer">
      <div class="inc-type med">ст.109-1<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 3 мкр</div>
      <div class="inc-time">🕐 15:04<span class="inc-district" style="background:#00838f22;color:#00838f">Туран ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061862187_ak0v&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.23887516370021,69.59890106313381],17)" style="cursor:pointer">
      <div class="inc-type med">ст.108-1<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Ордабасы базары маңы</div>
      <div class="inc-time">🕐 15:04<span class="inc-district" style="background:#e5393522;color:#e53935">Аль-Фараби ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061847139_8pog&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-high" onclick="map.setView([42.24636415653487,69.7459561895442],17)" style="cursor:pointer">
      <div class="inc-type high">АЛАЯҚТЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Ленгер жолы</div>
      <div class="inc-time">🕐 15:03<span class="inc-district" style="background:#2e7d3222;color:#2e7d32">Еңбекшілер ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061834230_b4t1&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-high" onclick="map.setView([42.252707834787984,69.73954043675337],17)" style="cursor:pointer">
      <div class="inc-type high">ст.190<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Манкент тас жолы</div>
      <div class="inc-time">🕐 15:03<span class="inc-district" style="background:#2e7d3222;color:#2e7d32">Еңбекшілер ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061824186_o7pr&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.37060165066074,69.78979495344184],17)" style="cursor:pointer">
      <div class="inc-type med">ЖКО<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Байтерек батыс</div>
      <div class="inc-time">🕐 15:03<span class="inc-district" style="background:#7b1fa222;color:#7b1fa2">Қаратау ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061814192_0q5n&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.239718833677216,69.44067888056342],17)" style="cursor:pointer">
      <div class="inc-type med">БҰЗАҚЫЛЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Рысқұлов к-сі</div>
      <div class="inc-time">🕐 15:03<span class="inc-district" style="background:#00838f22;color:#00838f">Туран ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061802196_mf26&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.24327539335041,69.4503983917716],17)" style="cursor:pointer">
      <div class="inc-type med">ст.108-1<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Желтоқсан к-сі</div>
      <div class="inc-time">🕐 15:03<span class="inc-district" style="background:#00838f22;color:#00838f">Туран ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061787195_pakj&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.25491151862631,69.4342298642293],17)" style="cursor:pointer">
      <div class="inc-type med">ст.188<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Желтоқсан к-сі</div>
      <div class="inc-time">🕐 15:02<span class="inc-district" style="background:#00838f22;color:#00838f">Туран ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061777201_0wba&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-high" onclick="map.setView([42.41391042645466,69.506635163673],17)" style="cursor:pointer">
      <div class="inc-type high">ст.293<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Манкент тас жолы</div>
      <div class="inc-time">🕐 15:02<span class="inc-district" style="background:#1565c022;color:#1565c0">Абай ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061762198_o9xg&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-high" onclick="map.setView([42.2280388788367,69.59678444958864],17)" style="cursor:pointer">
      <div class="inc-type high">БҰЗАҚЫЛЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Ордабасы базары маңы</div>
      <div class="inc-time">🕐 15:02<span class="inc-district" style="background:#e5393522;color:#e53935">Аль-Фараби ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061750192_xawt&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-low" onclick="map.setView([42.36237963654469,69.79233089248635],17)" style="cursor:pointer">
      <div class="inc-type low">ст.188<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Каратаевская к-сі</div>
      <div class="inc-time">🕐 15:02<span class="inc-district" style="background:#7b1fa222;color:#7b1fa2">Қаратау ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061737192_wbfa&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-low" onclick="map.setView([42.250911965841425,69.74521088799654],17)" style="cursor:pointer">
      <div class="inc-type low">ст.188<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Манкент тас жолы</div>
      <div class="inc-time">🕐 15:02<span class="inc-district" style="background:#2e7d3222;color:#2e7d32">Еңбекшілер ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061723807_vsfm&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-high" onclick="map.setView([42.245722226847896,69.58989462729429],17)" style="cursor:pointer">
      <div class="inc-type high">БҰЗАҚЫЛЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Ордабасы базары маңы</div>
      <div class="inc-time">🕐 15:01<span class="inc-district" style="background:#e5393522;color:#e53935">Аль-Фараби ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061711291_h5hq&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-high" onclick="map.setView([42.24099912867797,69.5994817220056],17)" style="cursor:pointer">
      <div class="inc-type high">ст.296<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Тәуелсіздік даңғылы</div>
      <div class="inc-time">🕐 15:01<span class="inc-district" style="background:#e5393522;color:#e53935">Аль-Фараби ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061700478_874d&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.223640038163985,69.59895215416131],17)" style="cursor:pointer">
      <div class="inc-type med">ст.108-1<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Рысқұлов к-сі</div>
      <div class="inc-time">🕐 15:01<span class="inc-district" style="background:#e5393522;color:#e53935">Аль-Фараби ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061688284_fzpr&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-low" onclick="map.setView([42.24036730390485,69.45042224697447],17)" style="cursor:pointer">
      <div class="inc-type low">ТОНАУ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Рысқұлов к-сі</div>
      <div class="inc-time">🕐 15:01<span class="inc-district" style="background:#00838f22;color:#00838f">Туран ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061673548_cuxw&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.39166848540247,69.4790160003448],17)" style="cursor:pointer">
      <div class="inc-type med">ст.190<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Таскешу жолы</div>
      <div class="inc-time">🕐 15:01<span class="inc-district" style="background:#1565c022;color:#1565c0">Абай ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061660777_hd2y&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.40470359203495,69.4877655906664],17)" style="cursor:pointer">
      <div class="inc-type med">ҰРЛЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Манкент тас жолы</div>
      <div class="inc-time">🕐 15:00<span class="inc-district" style="background:#1565c022;color:#1565c0">Абай ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061647828_fxtg&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.25275282125844,69.75941542996156],17)" style="cursor:pointer">
      <div class="inc-type med">ст.109-1<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Карасу жолы</div>
      <div class="inc-time">🕐 15:00<span class="inc-district" style="background:#2e7d3222;color:#2e7d32">Еңбекшілер ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061638199_8qmc&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.238767657706504,69.45790002268868],17)" style="cursor:pointer">
      <div class="inc-type med">ст.190<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Рысқұлов к-сі</div>
      <div class="inc-time">🕐 15:00<span class="inc-district" style="background:#00838f22;color:#00838f">Туран ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061622986_a5cc&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-low" onclick="map.setView([42.27280792230081,69.73555896927348],17)" style="cursor:pointer">
      <div class="inc-type low">АЛАЯҚТЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Манкент тас жолы</div>
      <div class="inc-time">🕐 15:00<span class="inc-district" style="background:#2e7d3222;color:#2e7d32">Еңбекшілер ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061608189_w4if&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-low" onclick="map.setView([42.24387420096159,69.76080678932784],17)" style="cursor:pointer">
      <div class="inc-type low">АЛАЯҚТЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Ленгер жолы</div>
      <div class="inc-time">🕐 14:59<span class="inc-district" style="background:#2e7d3222;color:#2e7d32">Еңбекшілер ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061595195_ky2w&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-high" onclick="map.setView([42.24608565971983,69.5983451890398],17)" style="cursor:pointer">
      <div class="inc-type high">АЛАЯҚТЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Байтерек к-сі</div>
      <div class="inc-time">🕐 14:59<span class="inc-district" style="background:#e5393522;color:#e53935">Аль-Фараби ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061583950_zsed&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-high" onclick="map.setView([42.41130404744341,69.49038556312824],17)" style="cursor:pointer">
      <div class="inc-type high">ст.108-1<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Абай даңғылы</div>
      <div class="inc-time">🕐 14:59<span class="inc-district" style="background:#1565c022;color:#1565c0">Абай ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061572110_ldd5&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-low" onclick="map.setView([42.41206125463747,69.4832292597571],17)" style="cursor:pointer">
      <div class="inc-type low">ст.296<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Таскешу жолы</div>
      <div class="inc-time">🕐 14:59<span class="inc-district" style="background:#1565c022;color:#1565c0">Абай ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061560458_o6rv&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.41096895298197,69.48987935438359],17)" style="cursor:pointer">
      <div class="inc-type med">ҰРЛЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Абай даңғылы</div>
      <div class="inc-time">🕐 14:59<span class="inc-district" style="background:#1565c022;color:#1565c0">Абай ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061546199_pgga&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-high" onclick="map.setView([42.265535273055626,69.45669756796104],17)" style="cursor:pointer">
      <div class="inc-type high">ст.296<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 3 мкр</div>
      <div class="inc-time">🕐 14:58<span class="inc-district" style="background:#00838f22;color:#00838f">Туран ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061534470_kuex&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-low" onclick="map.setView([42.372281279478244,69.78267402128942],17)" style="cursor:pointer">
      <div class="inc-type low">БҰЗАҚЫЛЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Аэропорт жолы</div>
      <div class="inc-time">🕐 14:58<span class="inc-district" style="background:#7b1fa222;color:#7b1fa2">Қаратау ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061523851_5due&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.23015714253815,69.59044701264787],17)" style="cursor:pointer">
      <div class="inc-type med">ст.109-1<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Байтерек к-сі</div>
      <div class="inc-time">🕐 14:58<span class="inc-district" style="background:#e5393522;color:#e53935">Аль-Фараби ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061512192_g3nn&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-low" onclick="map.setView([42.26610563831749,69.73974751836484],17)" style="cursor:pointer">
      <div class="inc-type low">ҰРЛЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Самал мкр</div>
      <div class="inc-time">🕐 14:58<span class="inc-district" style="background:#2e7d3222;color:#2e7d32">Еңбекшілер ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061501972_fl35&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-low" onclick="map.setView([42.238862333330296,69.43378541716176],17)" style="cursor:pointer">
      <div class="inc-type low">ст.293<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 3 мкр</div>
      <div class="inc-time">🕐 14:58<span class="inc-district" style="background:#00838f22;color:#00838f">Туран ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061489192_okg1&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-low" onclick="map.setView([42.250621347920955,69.76062267710431],17)" style="cursor:pointer">
      <div class="inc-type low">АЛАЯҚТЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Самал мкр</div>
      <div class="inc-time">🕐 14:57<span class="inc-district" style="background:#2e7d3222;color:#2e7d32">Еңбекшілер ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061474817_96or&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.360916281654106,69.76491241406985],17)" style="cursor:pointer">
      <div class="inc-type med">БҰЗАҚЫЛЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Аэропорт жолы</div>
      <div class="inc-time">🕐 14:57<span class="inc-district" style="background:#7b1fa222;color:#7b1fa2">Қаратау ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061460310_32lz&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.23873389509352,69.59138913866579],17)" style="cursor:pointer">
      <div class="inc-type med">ст.296<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Тәуелсіздік даңғылы</div>
      <div class="inc-time">🕐 14:57<span class="inc-district" style="background:#e5393522;color:#e53935">Аль-Фараби ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061450484_eboe&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-high" onclick="map.setView([42.25338331762287,69.44632308750685],17)" style="cursor:pointer">
      <div class="inc-type high">ст.296<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Рысқұлов к-сі</div>
      <div class="inc-time">🕐 14:57<span class="inc-district" style="background:#00838f22;color:#00838f">Туран ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061440198_4z2w&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-high" onclick="map.setView([42.25415604318114,69.44420774415815],17)" style="cursor:pointer">
      <div class="inc-type high">ст.190<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 9 мкр</div>
      <div class="inc-time">🕐 14:57<span class="inc-district" style="background:#00838f22;color:#00838f">Туран ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061425188_movk&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.3882744168963,69.49039451783335],17)" style="cursor:pointer">
      <div class="inc-type med">АЛАЯҚТЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Абай даңғылы</div>
      <div class="inc-time">🕐 14:56<span class="inc-district" style="background:#1565c022;color:#1565c0">Абай ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061409991_jmu2&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-high" onclick="map.setView([42.356849065539365,69.79215020209965],17)" style="cursor:pointer">
      <div class="inc-type high">ст.190<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Каратаевская к-сі</div>
      <div class="inc-time">🕐 14:56<span class="inc-district" style="background:#7b1fa222;color:#7b1fa2">Қаратау ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061400027_62lz&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-high" onclick="map.setView([42.232879874879146,69.59012051061463],17)" style="cursor:pointer">
      <div class="inc-type high">АЛАЯҚТЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Рысқұлов к-сі</div>
      <div class="inc-time">🕐 14:56<span class="inc-district" style="background:#e5393522;color:#e53935">Аль-Фараби ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061385199_9uke&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.368846164588966,69.77586561169782],17)" style="cursor:pointer">
      <div class="inc-type med">АЛАЯҚТЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Аэропорт жолы</div>
      <div class="inc-time">🕐 14:56<span class="inc-district" style="background:#7b1fa222;color:#7b1fa2">Қаратау ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061370879_0ete&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-high" onclick="map.setView([42.23958449849911,69.43653533283626],17)" style="cursor:pointer">
      <div class="inc-type high">ст.188<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Рысқұлов к-сі</div>
      <div class="inc-time">🕐 14:56<span class="inc-district" style="background:#00838f22;color:#00838f">Туран ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061361595_337m&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-high" onclick="map.setView([42.366097075638756,69.76557157352308],17)" style="cursor:pointer">
      <div class="inc-type high">ст.109-1<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Каратаевская к-сі</div>
      <div class="inc-time">🕐 14:55<span class="inc-district" style="background:#7b1fa222;color:#7b1fa2">Қаратау ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061351025_000a&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.40859443370333,69.49119391161179],17)" style="cursor:pointer">
      <div class="inc-type med">ст.108-1<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Таскешу жолы</div>
      <div class="inc-time">🕐 14:55<span class="inc-district" style="background:#1565c022;color:#1565c0">Абай ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061336187_nsij&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.25064945833576,69.73678605657108],17)" style="cursor:pointer">
      <div class="inc-type med">ЖКО<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Манкент тас жолы</div>
      <div class="inc-time">🕐 14:55<span class="inc-district" style="background:#2e7d3222;color:#2e7d32">Еңбекшілер ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061324227_zm4q&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-high" onclick="map.setView([42.253854489880936,69.44769122197505],17)" style="cursor:pointer">
      <div class="inc-type high">ст.109-1<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Рысқұлов к-сі</div>
      <div class="inc-time">🕐 14:55<span class="inc-district" style="background:#00838f22;color:#00838f">Туран ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061311068_nobd&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.26844861495788,69.7423713930552],17)" style="cursor:pointer">
      <div class="inc-type med">ст.188<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Ленгер жолы</div>
      <div class="inc-time">🕐 14:54<span class="inc-district" style="background:#2e7d3222;color:#2e7d32">Еңбекшілер ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061298929_lftr&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-low" onclick="map.setView([42.26147465239361,69.73471542443528],17)" style="cursor:pointer">
      <div class="inc-type low">АЛАЯҚТЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Самал мкр</div>
      <div class="inc-time">🕐 14:54<span class="inc-district" style="background:#2e7d3222;color:#2e7d32">Еңбекшілер ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061284201_p39h&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-high" onclick="map.setView([42.39877983556894,69.48123803745648],17)" style="cursor:pointer">
      <div class="inc-type high">ҰРЛЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Зоопарк маңы</div>
      <div class="inc-time">🕐 14:54<span class="inc-district" style="background:#1565c022;color:#1565c0">Абай ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061270033_y6fj&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.2453988036098,69.44645050646783],17)" style="cursor:pointer">
      <div class="inc-type med">ст.108-1<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Рысқұлов к-сі</div>
      <div class="inc-time">🕐 14:54<span class="inc-district" style="background:#00838f22;color:#00838f">Туран ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061257194_km7l&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.36953769150695,69.77746388324292],17)" style="cursor:pointer">
      <div class="inc-type med">ст.190<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Аэропорт жолы</div>
      <div class="inc-time">🕐 14:54<span class="inc-district" style="background:#7b1fa222;color:#7b1fa2">Қаратау ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061242198_5s2k&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.2572017979644,69.74607816031332],17)" style="cursor:pointer">
      <div class="inc-type med">ЖКО<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Ленгер жолы</div>
      <div class="inc-time">🕐 14:53<span class="inc-district" style="background:#2e7d3222;color:#2e7d32">Еңбекшілер ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061231201_11wl&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.222411578598845,69.57979292476047],17)" style="cursor:pointer">
      <div class="inc-type med">ст.296<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Рысқұлов к-сі</div>
      <div class="inc-time">🕐 14:53<span class="inc-district" style="background:#e5393522;color:#e53935">Аль-Фараби ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061221194_ije1&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-high" onclick="map.setView([42.35927625064132,69.77519111798624],17)" style="cursor:pointer">
      <div class="inc-type high">ст.296<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Момышұлы к-сі</div>
      <div class="inc-time">🕐 14:53<span class="inc-district" style="background:#7b1fa222;color:#7b1fa2">Қаратау ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061207192_aihf&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-low" onclick="map.setView([42.244285092971786,69.44351215364709],17)" style="cursor:pointer">
      <div class="inc-type low">ТОНАУ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 9 мкр</div>
      <div class="inc-time">🕐 14:53<span class="inc-district" style="background:#00838f22;color:#00838f">Туран ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061197643_wa3t&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-low" onclick="map.setView([42.35718134103861,69.78673092649476],17)" style="cursor:pointer">
      <div class="inc-type low">ст.109-1<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Аэропорт жолы</div>
      <div class="inc-time">🕐 14:53<span class="inc-district" style="background:#7b1fa222;color:#7b1fa2">Қаратау ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061184649_0ihe&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.24134348021646,69.59889764242968],17)" style="cursor:pointer">
      <div class="inc-type med">ТОНАУ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Тәуелсіздік даңғылы</div>
      <div class="inc-time">🕐 14:52<span class="inc-district" style="background:#e5393522;color:#e53935">Аль-Фараби ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061173200_f7as&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.37279695414448,69.78087715000693],17)" style="cursor:pointer">
      <div class="inc-type med">ст.109-1<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Каратаевская к-сі</div>
      <div class="inc-time">🕐 14:52<span class="inc-district" style="background:#7b1fa222;color:#7b1fa2">Қаратау ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061159018_57m9&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.40354756211912,69.48771830505491],17)" style="cursor:pointer">
      <div class="inc-type med">ст.188<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Таскешу жолы</div>
      <div class="inc-time">🕐 14:52<span class="inc-district" style="background:#1565c022;color:#1565c0">Абай ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061148296_lsur&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-low" onclick="map.setView([42.22165191154589,69.57388510216508],17)" style="cursor:pointer">
      <div class="inc-type low">ЖКО<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Рысқұлов к-сі</div>
      <div class="inc-time">🕐 14:52<span class="inc-district" style="background:#e5393522;color:#e53935">Аль-Фараби ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061134073_i27f&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.40803817184022,69.48042029727482],17)" style="cursor:pointer">
      <div class="inc-type med">АЛАЯҚТЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Абай даңғылы</div>
      <div class="inc-time">🕐 14:52<span class="inc-district" style="background:#1565c022;color:#1565c0">Абай ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061124202_ei6k&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.26019194435496,69.74260435906277],17)" style="cursor:pointer">
      <div class="inc-type med">ст.293<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Ленгер жолы</div>
      <div class="inc-time">🕐 14:51<span class="inc-district" style="background:#2e7d3222;color:#2e7d32">Еңбекшілер ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061108489_4f9g&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-low" onclick="map.setView([42.24008528541171,69.45935793017799],17)" style="cursor:pointer">
      <div class="inc-type low">БҰЗАҚЫЛЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Рысқұлов к-сі</div>
      <div class="inc-time">🕐 14:51<span class="inc-district" style="background:#00838f22;color:#00838f">Туран ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061096122_vutm&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-low" onclick="map.setView([42.26209532238479,69.43592028725423],17)" style="cursor:pointer">
      <div class="inc-type low">ст.108-1<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Рысқұлов к-сі</div>
      <div class="inc-time">🕐 14:51<span class="inc-district" style="background:#00838f22;color:#00838f">Туран ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061081195_rh3b&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-low" onclick="map.setView([42.2388988592115,69.59303446693063],17)" style="cursor:pointer">
      <div class="inc-type low">ҰРЛЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Тәуелсіздік даңғылы</div>
      <div class="inc-time">🕐 14:51<span class="inc-district" style="background:#e5393522;color:#e53935">Аль-Фараби ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061068197_6dd8&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.40610196461563,69.4993356481235],17)" style="cursor:pointer">
      <div class="inc-type med">АЛАЯҚТЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Манкент тас жолы</div>
      <div class="inc-time">🕐 14:50<span class="inc-district" style="background:#1565c022;color:#1565c0">Абай ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061056137_na1u&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.239235387572954,69.60247474882327],17)" style="cursor:pointer">
      <div class="inc-type med">ҰРЛЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Ордабасы базары маңы</div>
      <div class="inc-time">🕐 14:50<span class="inc-district" style="background:#e5393522;color:#e53935">Аль-Фараби ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061042900_p8g2&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-high" onclick="map.setView([42.4132929542275,69.49581843037731],17)" style="cursor:pointer">
      <div class="inc-type high">ҰРЛЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Таскешу жолы</div>
      <div class="inc-time">🕐 14:50<span class="inc-district" style="background:#1565c022;color:#1565c0">Абай ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061031874_hex3&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.367121590340794,69.76427749110083],17)" style="cursor:pointer">
      <div class="inc-type med">ст.293<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Аэропорт жолы</div>
      <div class="inc-time">🕐 14:50<span class="inc-district" style="background:#7b1fa222;color:#7b1fa2">Қаратау ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061022200_82ox&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.24793251823834,69.57517308681763],17)" style="cursor:pointer">
      <div class="inc-type med">ст.296<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Рысқұлов к-сі</div>
      <div class="inc-time">🕐 14:50<span class="inc-district" style="background:#e5393522;color:#e53935">Аль-Фараби ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778061008194_5pxx&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.360025284076265,69.79204875391281],17)" style="cursor:pointer">
      <div class="inc-type med">АЛАЯҚТЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Каратаевская к-сі</div>
      <div class="inc-time">🕐 14:49<span class="inc-district" style="background:#7b1fa222;color:#7b1fa2">Қаратау ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778060994197_rbda&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-low" onclick="map.setView([42.25952513069033,69.74478284437072],17)" style="cursor:pointer">
      <div class="inc-type low">ҰРЛЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Манкент тас жолы</div>
      <div class="inc-time">🕐 14:49<span class="inc-district" style="background:#2e7d3222;color:#2e7d32">Еңбекшілер ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778060983906_5mc1&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.364683567418965,69.76675659550301],17)" style="cursor:pointer">
      <div class="inc-type med">ТОНАУ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Байтерек батыс</div>
      <div class="inc-time">🕐 14:49<span class="inc-district" style="background:#7b1fa222;color:#7b1fa2">Қаратау ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778060974201_ae99&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-low" onclick="map.setView([42.246384620249685,69.43256817139124],17)" style="cursor:pointer">
      <div class="inc-type low">АЛАЯҚТЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Рысқұлов к-сі</div>
      <div class="inc-time">🕐 14:49<span class="inc-district" style="background:#00838f22;color:#00838f">Туран ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778060964196_3fe3&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-low" onclick="map.setView([42.247986782217936,69.74155677398666],17)" style="cursor:pointer">
      <div class="inc-type low">ст.108-1<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Самал мкр</div>
      <div class="inc-time">🕐 14:49<span class="inc-district" style="background:#2e7d3222;color:#2e7d32">Еңбекшілер ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778060952187_v7l4&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.371948161374476,69.76729182187353],17)" style="cursor:pointer">
      <div class="inc-type med">ст.109-1<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Байтерек батыс</div>
      <div class="inc-time">🕐 14:49<span class="inc-district" style="background:#7b1fa222;color:#7b1fa2">Қаратау ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778060942196_mija&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-low" onclick="map.setView([42.39969885153867,69.48767998687912],17)" style="cursor:pointer">
      <div class="inc-type low">ст.188<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Абай даңғылы</div>
      <div class="inc-time">🕐 14:48<span class="inc-district" style="background:#1565c022;color:#1565c0">Абай ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778060928642_twc1&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.25419764235073,69.75024660476036],17)" style="cursor:pointer">
      <div class="inc-type med">ст.109-1<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Самал мкр</div>
      <div class="inc-time">🕐 14:48<span class="inc-district" style="background:#2e7d3222;color:#2e7d32">Еңбекшілер ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778060917195_9idp&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-high" onclick="map.setView([42.349995088535614,69.77952698537345],17)" style="cursor:pointer">
      <div class="inc-type high">ҰРЛЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Аэропорт жолы</div>
      <div class="inc-time">🕐 14:48<span class="inc-district" style="background:#7b1fa222;color:#7b1fa2">Қаратау ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778060902200_t3v2&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-high" onclick="map.setView([42.220982702228405,69.60168599047208],17)" style="cursor:pointer">
      <div class="inc-type high">ст.109-1<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Рысқұлов к-сі</div>
      <div class="inc-time">🕐 14:48<span class="inc-district" style="background:#e5393522;color:#e53935">Аль-Фараби ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778060888199_9ldw&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-low" onclick="map.setView([42.264728882001855,69.45454999866311],17)" style="cursor:pointer">
      <div class="inc-type low">ЖКО<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Желтоқсан к-сі</div>
      <div class="inc-time">🕐 14:47<span class="inc-district" style="background:#00838f22;color:#00838f">Туран ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778060876201_2cpg&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.24389899687161,69.58332762480303],17)" style="cursor:pointer">
      <div class="inc-type med">БҰЗАҚЫЛЫҚ<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Байтерек к-сі</div>
      <div class="inc-time">🕐 14:47<span class="inc-district" style="background:#e5393522;color:#e53935">Аль-Фараби ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778060865200_mpvv&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-low" onclick="map.setView([42.375674449767345,69.77626214587337],17)" style="cursor:pointer">
      <div class="inc-type low">ЖКО<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 Момышұлы к-сі</div>
      <div class="inc-time">🕐 14:47<span class="inc-district" style="background:#7b1fa222;color:#7b1fa2">Қаратау ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778060855294_jqli&#39;,this)">🗑</button>
    </div>
    <div class="inc-item sev-med" onclick="map.setView([42.24637451789284,69.45349437744287],17)" style="cursor:pointer">
      <div class="inc-type med">ст.190<span class="inc-auto-badge">авто</span></div>
      <div class="inc-loc">📍 3 мкр</div>
      <div class="inc-time">🕐 14:47<span class="inc-district" style="background:#00838f22;color:#00838f">Туран ауданы</span></div>
      <button class="inc-delete" onclick="event.stopPropagation();deleteIncident(&#39;inc_1778060844187_976r&#39;,this)">🗑</button>
    </div></div></div>
  <div class="tab-content" id="tab-buildings">
    <div style="padding:9px 12px;border-bottom:1px solid var(--border-light);">
      <div style="font-size:10px;color:var(--text-muted)">Жоғарыдағы <strong style="color:#6a1b9a">🏢 Ғимарат</strong> батырмасын басып, картада нысанды белгілеңіз</div>
    </div>
    <div id="buildings-feed"><div class="bld-item" onclick="map.setView([42.34063994662327,69.62521612644197],16)"><div class="bld-emoji">🏛</div><div class="bld-info"><div class="bld-name">Участковый пункт полиции Енбекшинского РОВД УВД г. Шымкента  №18</div><div class="bld-type">Басқа</div><span class="bld-district-badge" style="background:#e53935">Аль-Фараби</span></div><button class="bld-delete" onclick="event.stopPropagation();deleteBuilding(&#39;bld_1778061985868&#39;,this)">🗑</button></div><div class="bld-item" onclick="map.setView([42.33588161229564,69.64632511138917],16)"><div class="bld-emoji">🏛</div><div class="bld-info"><div class="bld-name">Участковый пункт полиции Аль-Фарабийского района ОП УВД г. Шымкента  №14</div><div class="bld-type">Басқа</div><span class="bld-district-badge" style="background:#e53935">Аль-Фараби</span></div><button class="bld-delete" onclick="event.stopPropagation();deleteBuilding(&#39;bld_1778061939908&#39;,this)">🗑</button></div><div class="bld-item" onclick="map.setView([42.34315775285915,69.63769912719728],16)"><div class="bld-emoji">🏛</div><div class="bld-info"><div class="bld-name">Участковый пункт полиции Каратауского района ОП УВД г. Шымкента  №51</div><div class="bld-type">Басқа</div><span class="bld-district-badge" style="background:#e53935">Аль-Фараби</span></div><button class="bld-delete" onclick="event.stopPropagation();deleteBuilding(&#39;bld_1778061853191&#39;,this)">🗑</button></div><div class="bld-item" onclick="map.setView([42.29907166843843,69.59733724594118],16)"><div class="bld-emoji">🏛</div><div class="bld-info"><div class="bld-name">Участковый пункт полиции Аль-Фарабийского района ОП УВД г. Шымкента  №26</div><div class="bld-type">Басқа</div><span class="bld-district-badge" style="background:#e53935">Аль-Фараби</span></div><button class="bld-delete" onclick="event.stopPropagation();deleteBuilding(&#39;bld_1778061657154&#39;,this)">🗑</button></div><div class="bld-item" onclick="map.setView([42.27946000049741,69.57479596138002],16)"><div class="bld-emoji">🏛</div><div class="bld-info"><div class="bld-name">Участковый пункт полиции Аль-Фарабийского района ОП УВД г. Шымкента  №31</div><div class="bld-type">Басқа</div><span class="bld-district-badge" style="background:#e53935">Аль-Фараби</span></div><button class="bld-delete" onclick="event.stopPropagation();deleteBuilding(&#39;bld_1778061583706&#39;,this)">🗑</button></div><div class="bld-item" onclick="map.setView([42.29582596621327,69.57388401031496],16)"><div class="bld-emoji">🏛</div><div class="bld-info"><div class="bld-name">Участковый пункт полиции Аль-Фарабийского района ОП УВД г. Шымкента  №27</div><div class="bld-type">Басқа</div><span class="bld-district-badge" style="background:#e53935">Аль-Фараби</span></div><button class="bld-delete" onclick="event.stopPropagation();deleteBuilding(&#39;bld_1778061500359&#39;,this)">🗑</button></div><div class="bld-item" onclick="map.setView([42.3002857878897,69.58218812942506],16)"><div class="bld-emoji">🏛</div><div class="bld-info"><div class="bld-name">Участковый пункт полиции Аль-Фарабийского района ОП УВД г. Шымкента  №24</div><div class="bld-type">Басқа</div><span class="bld-district-badge" style="background:#e53935">Аль-Фараби</span></div><button class="bld-delete" onclick="event.stopPropagation();deleteBuilding(&#39;bld_1778061462429&#39;,this)">🗑</button></div><div class="bld-item" onclick="map.setView([42.30450724977516,69.57948446273805],16)"><div class="bld-emoji">🏢</div><div class="bld-info"><div class="bld-name">Участковый пункт полиции Аль-Фарабийского района ОП УВД г. Шымкента  №32</div><div class="bld-type">Басқа</div><span class="bld-district-badge" style="background:#e53935">Аль-Фараби</span></div><button class="bld-delete" onclick="event.stopPropagation();deleteBuilding(&#39;bld_1778061410998&#39;,this)">🗑</button></div><div class="bld-item" onclick="map.setView([42.30436442298425,69.5867693424225],16)"><div class="bld-emoji">🏛</div><div class="bld-info"><div class="bld-name">Участковый пункт полиции Аль-Фарабийского района ОП УВД г. Шымкента  №29</div><div class="bld-type">Басқа</div><span class="bld-district-badge" style="background:#e53935">Аль-Фараби</span></div><button class="bld-delete" onclick="event.stopPropagation();deleteBuilding(&#39;bld_1778061370244&#39;,this)">🗑</button></div><div class="bld-item" onclick="map.setView([42.333700588729386,69.63924407958986],16)"><div class="bld-emoji">🏛</div><div class="bld-info"><div class="bld-name">Участковый пункт полиции Аль-Фарабийского района ОП УВД г. Шымкента  №16</div><div class="bld-type">Басқа</div><span class="bld-district-badge" style="background:#e53935">Аль-Фараби</span></div><button class="bld-delete" onclick="event.stopPropagation();deleteBuilding(&#39;bld_1778060980952&#39;,this)">🗑</button></div><div class="bld-item" onclick="map.setView([42.33664296998421,69.63543534278871],16)"><div class="bld-emoji">🏛</div><div class="bld-info"><div class="bld-name">Участковый пункт полиции Аль-Фарабийского района ОП УВД г. Шымкента  №17</div><div class="bld-type">Басқа</div><span class="bld-district-badge" style="background:#e53935">Аль-Фараби</span></div><button class="bld-delete" onclick="event.stopPropagation();deleteBuilding(&#39;bld_1778060929859&#39;,this)">🗑</button></div><div class="bld-item" onclick="map.setView([42.34315378788923,69.64023649692537],16)"><div class="bld-emoji">🏛</div><div class="bld-info"><div class="bld-name">Участковый пункт полиции Аль-Фарабийского района ОП УВД г. Шымкента  №19</div><div class="bld-type">Басқа</div><span class="bld-district-badge" style="background:#e53935">Аль-Фараби</span></div><button class="bld-delete" onclick="event.stopPropagation();deleteBuilding(&#39;bld_1778060870975&#39;,this)">🗑</button></div><div class="bld-item" onclick="map.setView([42.29769881236193,69.60800170898439],16)"><div class="bld-emoji">🏛</div><div class="bld-info"><div class="bld-name">Линейный отдел внутренних дел на станции Шымкент  Отделения полиции</div><div class="bld-type">Басқа</div><span class="bld-district-badge" style="background:#e53935">Аль-Фараби</span></div><button class="bld-delete" onclick="event.stopPropagation();deleteBuilding(&#39;bld_1778060588976&#39;,this)">🗑</button></div><div class="bld-item" onclick="map.setView([42.30196012336955,69.59700465202333],16)"><div class="bld-emoji">🏛</div><div class="bld-info"><div class="bld-name">Участковый пункт полиции Аль-Фарабийского района ОП УВД г. Шымкента  №33</div><div class="bld-type">Басқа</div><span class="bld-district-badge" style="background:#e53935">Аль-Фараби</span></div><button class="bld-delete" onclick="event.stopPropagation();deleteBuilding(&#39;bld_1778060541592&#39;,this)">🗑</button></div><div class="bld-item" onclick="map.setView([42.30500714099169,69.6106141805649],16)"><div class="bld-emoji">🏛</div><div class="bld-info"><div class="bld-name">Участковый пункт полиции Аль-Фарабийского района ОП УВД г. Шымкента  №30</div><div class="bld-type">Басқа</div><span class="bld-district-badge" style="background:#e53935">Аль-Фараби</span></div><button class="bld-delete" onclick="event.stopPropagation();deleteBuilding(&#39;bld_1778060448390&#39;,this)">🗑</button></div><div class="bld-item" onclick="map.setView([42.31783632382953,69.58547115325929],16)"><div class="bld-emoji">🏛</div><div class="bld-info"><div class="bld-name">Участковый пункт полиции Аль-Фарабийского района ОП УВД г. Шымкента  №25</div><div class="bld-type">Басқа</div><span class="bld-district-badge" style="background:#e53935">Аль-Фараби</span></div><button class="bld-delete" onclick="event.stopPropagation();deleteBuilding(&#39;bld_1778060229465&#39;,this)">🗑</button></div><div class="bld-item" onclick="map.setView([42.31866929723672,69.58965539932252],16)"><div class="bld-emoji">🏛</div><div class="bld-info"><div class="bld-name">Участковый пункт полиции Аль-Фарабийского района ОП УВД г. Шымкента</div><div class="bld-type">Басқа</div><span class="bld-district-badge" style="background:#e53935">Аль-Фараби</span></div><button class="bld-delete" onclick="event.stopPropagation();deleteBuilding(&#39;bld_1778060119379&#39;,this)">🗑</button></div><div class="bld-item" onclick="map.setView([42.316035476968054,69.59171533584596],16)"><div class="bld-emoji">🏛</div><div class="bld-info"><div class="bld-name">Участковый пункт полиции Аль-Фарабийского района ОП УВД г. Шымкента</div><div class="bld-type">Басқа</div><span class="bld-district-badge" style="background:#e53935">Аль-Фараби</span></div><button class="bld-delete" onclick="event.stopPropagation();deleteBuilding(&#39;bld_1778059850033&#39;,this)">🗑</button></div><div class="bld-item" onclick="map.setView([42.31145776199981,69.59903240203859],16)"><div class="bld-emoji">🏛</div><div class="bld-info"><div class="bld-name">Участковый пункт полиции Аль-Фарабийского района ОП УВД г. Шымкента</div><div class="bld-type">Басқа</div><span class="bld-district-badge" style="background:#e53935">Аль-Фараби</span></div><button class="bld-delete" onclick="event.stopPropagation();deleteBuilding(&#39;bld_1778059675068&#39;,this)">🗑</button></div><div class="bld-item" onclick="map.setView([42.31542460531425,69.60496544837953],16)"><div class="bld-emoji">🏛</div><div class="bld-info"><div class="bld-name">Управление специализированной службы охраны</div><div class="bld-type">Басқа</div><span class="bld-district-badge" style="background:#e53935">Аль-Фараби</span></div><button class="bld-delete" onclick="event.stopPropagation();deleteBuilding(&#39;bld_1778059594223&#39;,this)">🗑</button></div><div class="bld-item" onclick="map.setView([42.321612381634196,69.61929380893709],16)"><div class="bld-emoji">🏛</div><div class="bld-info"><div class="bld-name">Опорный Пункт Полиций</div><div class="bld-type">Басқа</div><span class="bld-district-badge" style="background:#e53935">Аль-Фараби</span></div><button class="bld-delete" onclick="event.stopPropagation();deleteBuilding(&#39;bld_1778059393232&#39;,this)">🗑</button></div></div>
  </div>
  <div class="tab-content" id="tab-stats">
    <div class="mini-chart">
      <div class="chart-title">7 күн — ЖКО</div>
      <div class="chart-bars" id="chart-dtp"></div>
    </div>
    <div class="mini-chart" style="margin-top:10px">
      <div class="chart-title">7 күн — Қылмыс</div>
      <div class="chart-bars" id="chart-crime"></div>
    </div>
    <div style="padding:11px 12px">
      <div class="chart-title" style="margin-bottom:7px">Тіркелген оқиғалар (сағат бойынша)</div>
      <div class="hour-chart" id="chart-hours"><div class="h-bar-w"><div class="h-bar" style="height:0px;background:#1565c0;opacity:.75"></div><div class="h-lbl">0</div></div><div class="h-bar-w"><div class="h-bar" style="height:0px;background:#1565c0;opacity:.75"></div><div class="h-lbl"></div></div><div class="h-bar-w"><div class="h-bar" style="height:0px;background:#1565c0;opacity:.75"></div><div class="h-lbl"></div></div><div class="h-bar-w"><div class="h-bar" style="height:0px;background:#1565c0;opacity:.75"></div><div class="h-lbl"></div></div><div class="h-bar-w"><div class="h-bar" style="height:0px;background:#1565c0;opacity:.75"></div><div class="h-lbl">4</div></div><div class="h-bar-w"><div class="h-bar" style="height:0px;background:#1565c0;opacity:.75"></div><div class="h-lbl"></div></div><div class="h-bar-w"><div class="h-bar" style="height:0px;background:#1565c0;opacity:.75"></div><div class="h-lbl"></div></div><div class="h-bar-w"><div class="h-bar" style="height:0px;background:#1565c0;opacity:.75"></div><div class="h-lbl"></div></div><div class="h-bar-w"><div class="h-bar" style="height:0px;background:#1565c0;opacity:.75"></div><div class="h-lbl">8</div></div><div class="h-bar-w"><div class="h-bar" style="height:0px;background:#1565c0;opacity:.75"></div><div class="h-lbl"></div></div><div class="h-bar-w"><div class="h-bar" style="height:0px;background:#1565c0;opacity:.75"></div><div class="h-lbl"></div></div><div class="h-bar-w"><div class="h-bar" style="height:0px;background:#1565c0;opacity:.75"></div><div class="h-lbl"></div></div><div class="h-bar-w"><div class="h-bar" style="height:0px;background:#1565c0;opacity:.75"></div><div class="h-lbl">12</div></div><div class="h-bar-w"><div class="h-bar" style="height:0px;background:#1565c0;opacity:.75"></div><div class="h-lbl"></div></div><div class="h-bar-w"><div class="h-bar" style="height:44px;background:#e53935;opacity:.75"></div><div class="h-lbl"></div></div><div class="h-bar-w"><div class="h-bar" style="height:6.8244897959183675px;background:#1565c0;opacity:.75"></div><div class="h-lbl"></div></div><div class="h-bar-w"><div class="h-bar" style="height:0px;background:#1565c0;opacity:.75"></div><div class="h-lbl">16</div></div><div class="h-bar-w"><div class="h-bar" style="height:0px;background:#1565c0;opacity:.75"></div><div class="h-lbl"></div></div><div class="h-bar-w"><div class="h-bar" style="height:0px;background:#1565c0;opacity:.75"></div><div class="h-lbl"></div></div><div class="h-bar-w"><div class="h-bar" style="height:0px;background:#1565c0;opacity:.75"></div><div class="h-lbl"></div></div><div class="h-bar-w"><div class="h-bar" style="height:0px;background:#1565c0;opacity:.75"></div><div class="h-lbl">20</div></div><div class="h-bar-w"><div class="h-bar" style="height:0px;background:#1565c0;opacity:.75"></div><div class="h-lbl"></div></div><div class="h-bar-w"><div class="h-bar" style="height:0px;background:#1565c0;opacity:.75"></div><div class="h-lbl"></div></div><div class="h-bar-w"><div class="h-bar" style="height:0px;background:#1565c0;opacity:.75"></div><div class="h-lbl"></div></div></div>
    </div>
    <div style="padding:11px 12px">
      <div class="chart-title" style="margin-bottom:7px">Аудан бойынша — ст.190</div>
      <div id="district-st190"><div style="margin-bottom:6px"><div style="display:flex;justify-content:space-between;margin-bottom:2px"><span style="font-size:10px;color:var(--text-secondary)">Абай</span><span style="font-size:10px;font-weight:700;color:#1565c0;font-family:&#39;JetBrains Mono&#39;,monospace">204</span></div><div style="height:4px;background:var(--bg-tertiary);border-radius:3px"><div style="height:100%;width:100%;background:#1565c0;border-radius:3px;transition:width .6s"></div></div></div><div style="margin-bottom:6px"><div style="display:flex;justify-content:space-between;margin-bottom:2px"><span style="font-size:10px;color:var(--text-secondary)">Аль-Фараби</span><span style="font-size:10px;font-weight:700;color:#e53935;font-family:&#39;JetBrains Mono&#39;,monospace">170</span></div><div style="height:4px;background:var(--bg-tertiary);border-radius:3px"><div style="height:100%;width:83%;background:#e53935;border-radius:3px;transition:width .6s"></div></div></div><div style="margin-bottom:6px"><div style="display:flex;justify-content:space-between;margin-bottom:2px"><span style="font-size:10px;color:var(--text-secondary)">Қаратау</span><span style="font-size:10px;font-weight:700;color:#7b1fa2;font-family:&#39;JetBrains Mono&#39;,monospace">160</span></div><div style="height:4px;background:var(--bg-tertiary);border-radius:3px"><div style="height:100%;width:78%;background:#7b1fa2;border-radius:3px;transition:width .6s"></div></div></div><div style="margin-bottom:6px"><div style="display:flex;justify-content:space-between;margin-bottom:2px"><span style="font-size:10px;color:var(--text-secondary)">Туран</span><span style="font-size:10px;font-weight:700;color:#00838f;font-family:&#39;JetBrains Mono&#39;,monospace">147</span></div><div style="height:4px;background:var(--bg-tertiary);border-radius:3px"><div style="height:100%;width:72%;background:#00838f;border-radius:3px;transition:width .6s"></div></div></div><div style="margin-bottom:6px"><div style="display:flex;justify-content:space-between;margin-bottom:2px"><span style="font-size:10px;color:var(--text-secondary)">Еңбекшілер</span><span style="font-size:10px;font-weight:700;color:#2e7d32;font-family:&#39;JetBrains Mono&#39;,monospace">118</span></div><div style="height:4px;background:var(--bg-tertiary);border-radius:3px"><div style="height:100%;width:58%;background:#2e7d32;border-radius:3px;transition:width .6s"></div></div></div></div>
    </div>
    <div style="padding:11px 12px">
      <div class="chart-title" style="margin-bottom:7px">Аудан бойынша — ст.188</div>
      <div id="district-st188"><div style="margin-bottom:6px"><div style="display:flex;justify-content:space-between;margin-bottom:2px"><span style="font-size:10px;color:var(--text-secondary)">Абай</span><span style="font-size:10px;font-weight:700;color:#1565c0;font-family:&#39;JetBrains Mono&#39;,monospace">120</span></div><div style="height:4px;background:var(--bg-tertiary);border-radius:3px"><div style="height:100%;width:100%;background:#1565c0;border-radius:3px;transition:width .6s"></div></div></div><div style="margin-bottom:6px"><div style="display:flex;justify-content:space-between;margin-bottom:2px"><span style="font-size:10px;color:var(--text-secondary)">Аль-Фараби</span><span style="font-size:10px;font-weight:700;color:#e53935;font-family:&#39;JetBrains Mono&#39;,monospace">102</span></div><div style="height:4px;background:var(--bg-tertiary);border-radius:3px"><div style="height:100%;width:85%;background:#e53935;border-radius:3px;transition:width .6s"></div></div></div><div style="margin-bottom:6px"><div style="display:flex;justify-content:space-between;margin-bottom:2px"><span style="font-size:10px;color:var(--text-secondary)">Қаратау</span><span style="font-size:10px;font-weight:700;color:#7b1fa2;font-family:&#39;JetBrains Mono&#39;,monospace">80</span></div><div style="height:4px;background:var(--bg-tertiary);border-radius:3px"><div style="height:100%;width:67%;background:#7b1fa2;border-radius:3px;transition:width .6s"></div></div></div><div style="margin-bottom:6px"><div style="display:flex;justify-content:space-between;margin-bottom:2px"><span style="font-size:10px;color:var(--text-secondary)">Туран</span><span style="font-size:10px;font-weight:700;color:#00838f;font-family:&#39;JetBrains Mono&#39;,monospace">48</span></div><div style="height:4px;background:var(--bg-tertiary);border-radius:3px"><div style="height:100%;width:40%;background:#00838f;border-radius:3px;transition:width .6s"></div></div></div><div style="margin-bottom:6px"><div style="display:flex;justify-content:space-between;margin-bottom:2px"><span style="font-size:10px;color:var(--text-secondary)">Еңбекшілер</span><span style="font-size:10px;font-weight:700;color:#2e7d32;font-family:&#39;JetBrains Mono&#39;,monospace">43</span></div><div style="height:4px;background:var(--bg-tertiary);border-radius:3px"><div style="height:100%;width:36%;background:#2e7d32;border-radius:3px;transition:width .6s"></div></div></div></div>
    </div>
    <div style="padding:11px 12px">
      <div class="chart-title" style="margin-bottom:7px">Аудандар рейтингі (барлық қылмыс)</div>
      <div id="district-ranking"><div style="margin-bottom:7px"><div style="display:flex;justify-content:space-between;margin-bottom:2px"><span style="font-size:10px;color:var(--text-secondary)">Абай</span><span style="font-size:10px;font-weight:700;color:#1565c0;font-family:&#39;JetBrains Mono&#39;,monospace">511</span></div><div style="height:4px;background:var(--bg-tertiary);border-radius:3px"><div style="height:100%;width:100%;background:#1565c0;border-radius:3px;transition:width .6s"></div></div></div><div style="margin-bottom:7px"><div style="display:flex;justify-content:space-between;margin-bottom:2px"><span style="font-size:10px;color:var(--text-secondary)">Аль-Фараби</span><span style="font-size:10px;font-weight:700;color:#e53935;font-family:&#39;JetBrains Mono&#39;,monospace">402</span></div><div style="height:4px;background:var(--bg-tertiary);border-radius:3px"><div style="height:100%;width:79%;background:#e53935;border-radius:3px;transition:width .6s"></div></div></div><div style="margin-bottom:7px"><div style="display:flex;justify-content:space-between;margin-bottom:2px"><span style="font-size:10px;color:var(--text-secondary)">Қаратау</span><span style="font-size:10px;font-weight:700;color:#7b1fa2;font-family:&#39;JetBrains Mono&#39;,monospace">356</span></div><div style="height:4px;background:var(--bg-tertiary);border-radius:3px"><div style="height:100%;width:70%;background:#7b1fa2;border-radius:3px;transition:width .6s"></div></div></div><div style="margin-bottom:7px"><div style="display:flex;justify-content:space-between;margin-bottom:2px"><span style="font-size:10px;color:var(--text-secondary)">Туран</span><span style="font-size:10px;font-weight:700;color:#00838f;font-family:&#39;JetBrains Mono&#39;,monospace">320</span></div><div style="height:4px;background:var(--bg-tertiary);border-radius:3px"><div style="height:100%;width:63%;background:#00838f;border-radius:3px;transition:width .6s"></div></div></div><div style="margin-bottom:7px"><div style="display:flex;justify-content:space-between;margin-bottom:2px"><span style="font-size:10px;color:var(--text-secondary)">Еңбекшілер</span><span style="font-size:10px;font-weight:700;color:#2e7d32;font-family:&#39;JetBrains Mono&#39;,monospace">236</span></div><div style="height:4px;background:var(--bg-tertiary);border-radius:3px"><div style="height:100%;width:46%;background:#2e7d32;border-radius:3px;transition:width .6s"></div></div></div></div>
    </div>
  </div>
  <div class="tab-content" id="tab-district">
    <div id="district-card">
      <div id="dc-name">—</div>
      <div class="dc-grid">
        <div class="dc-item"><div class="dc-val" id="dc-st190">—</div><div class="dc-lbl">СТ.190</div></div>
        <div class="dc-item"><div class="dc-val" id="dc-st188">—</div><div class="dc-lbl">СТ.188</div></div>
        <div class="dc-item"><div class="dc-val" id="dc-st1091">—</div><div class="dc-lbl">СТ.109-1</div></div>
        <div class="dc-item"><div class="dc-val" id="dc-total">—</div><div class="dc-lbl">БАРЛЫҒЫ</div></div>
      </div>
      <div id="dc-streets"></div>
    </div>
    <div id="district-hint" style="padding:11px 13px;font-size:11px;color:var(--text-muted)">Картадан аудан шекарасын басыңыз немесе сол жақтан таңдаңыз.</div>
  </div>
</div>
</div>

<div id="toast" class="" style="border-left-color: rgb(229, 57, 53);">
  <div style="font-size:16px">🚨</div>
  <div><div id="toast-type" style="color: rgb(229, 57, 53);">ЖАҢА ОҚИҒА</div><div id="toast-loc">ст.109-1 — Зоопарк маңы</div></div>
</div>

<script>
// ============ DISTRICT DATA ============
const districtData = {
  alfarabi: {
    name:'Аль-Фараби ауданы', osmName:'Аль-Фарабийский район',
    color:'#e53935',
    pop:201573, area:144, density:1400, popMale:97000, popFemale:105000,
    st190:170, st188:102, st1091:28, st296:25, st1081:16, st107:15, st287:10, st139:7, st187:7, st293:6, st367:6, st345:5, st385:5,
    total:402, patrol:3, crimes:62, dtp:31, murder:5,
    streets:['Тәуелсіздік даңғылы','Байтерек к-сі','Рысқұлов к-сі','Ордабасы базары маңы']
  },
  abay: {
    name:'Абай ауданы', osmName:'Абайский район',
    color:'#1565c0',
    pop:345761, area:497, density:696, popMale:168000, popFemale:178000,
    st190:204, st188:120, st1091:71, st296:28, st1081:31, st107:15, st191:14, st297:10, st345:10, st194:8,
    total:511, patrol:2, crimes:78, dtp:23, murder:3,
    streets:['Абай даңғылы','Таскешу жолы','Манкент тас жолы','Байтерек (солтүстік)']
  },
  turan: {
    name:'Туран ауданы', osmName:'Туранский район',
    color:'#00838f',
    pop:136000, area:68, density:2000, popMale:65000, popFemale:71000,
    st190:147, st188:48, st296:44, st1091:32, st1081:16, st107:12, st345:11, st297:10,
    total:320, patrol:1, crimes:45, dtp:18, murder:2,
    streets:['Желтоқсан к-сі','Рысқұлов к-сі','Тәуелсіздік (батыс)','9 мкр']
  },
  karatau: {
    name:'Қаратау ауданы', osmName:'Каратауский район',
    color:'#7b1fa2',
    pop:386000, area:323, density:1195, popMale:189000, popFemale:197000,
    st190:160, st188:80, st1091:65, st296:22, st1081:20, st107:9,
    total:356, patrol:1, crimes:52, dtp:16, murder:2,
    streets:['Каратаевская к-сі','Байтерек (батыс)','Аэропорт жолы','Момышұлы к-сі']
  },
  enbekshi: {
    name:'Еңбекшілер ауданы', osmName:'Енбекшинский район',
    color:'#2e7d32',
    pop:204962, area:207, density:990, popMale:99000, popFemale:106000,
    st190:118, st188:43, st1091:43, st296:11, st1081:16, st107:5,
    total:236, patrol:1, crimes:55, dtp:19, murder:2,
    streets:['Манкент тас жолы','Карасу жолы','Ленгер жолы','Самал мкр']
  }
};

// ============ DB ============
const DB = {
  INCIDENTS_KEY:'shymkent_incidents_v7',
  BUILDINGS_KEY:'shymkent_buildings_v7',
  CAMERAS_KEY:'shymkent_cameras_v7',
  SETTINGS_KEY:'shymkent_settings_v7',
  load(key,fb=[]){try{const r=localStorage.getItem(key);return r?JSON.parse(r):fb;}catch{return fb;}},
  save(key,data){try{localStorage.setItem(key,JSON.stringify(data));return true;}catch{return false;}},
  getIncidents(){return this.load(this.INCIDENTS_KEY,[]);},
  addIncident(inc){
    const list=this.getIncidents();
    inc.id='inc_'+Date.now()+'_'+Math.random().toString(36).slice(2,6);
    inc.created=new Date().toISOString(); inc.source=inc.source||'manual';
    list.unshift(inc); if(list.length>500)list.splice(500);
    this.save(this.INCIDENTS_KEY,list); return inc;
  },
  removeIncident(id){this.save(this.INCIDENTS_KEY,this.getIncidents().filter(i=>i.id!==id));},
  getBuildings(){return this.load(this.BUILDINGS_KEY,[]);},
  addBuilding(b){
    const list=this.getBuildings();
    b.id='bld_'+Date.now(); b.created=new Date().toISOString();
    list.unshift(b); this.save(this.BUILDINGS_KEY,list); return b;
  },
  removeBuilding(id){this.save(this.BUILDINGS_KEY,this.getBuildings().filter(b=>b.id!==id));},
  getCameras(){return this.load(this.CAMERAS_KEY,[]);},
  addCamera(cam){
    const list=this.getCameras();
    cam.id='cam_'+Date.now(); cam.created=new Date().toISOString();
    list.unshift(cam); this.save(this.CAMERAS_KEY,list); return cam;
  },
  removeCamera(id){this.save(this.CAMERAS_KEY,this.getCameras().filter(c=>c.id!==id));},
  getSettings(){return this.load(this.SETTINGS_KEY,{theme:'light',autoMode:false});},
  saveSetting(k,v){const s=this.getSettings();s[k]=v;this.save(this.SETTINGS_KEY,s);},
  clearIncidents(){this.save(this.INCIDENTS_KEY,[]);},
  getStats(){
    const incs=this.getIncidents(); const byHour=new Array(24).fill(0);
    incs.forEach(i=>{const h=new Date(i.created).getHours();byHour[h]++;});
    return{byHour,total:incs.length};
  },
  updateDBInfo(){
    const incs=this.getIncidents(); const blds=this.getBuildings(); const cams=this.getCameras();
    const manual=incs.filter(i=>i.source==='manual').length;
    const auto=incs.filter(i=>i.source==='auto').length;
    const el=document.getElementById('db-info');
    if(el)el.innerHTML=`Оқиғалар: <b style="color:var(--text-primary)">${incs.length}</b> (қол: ${manual}, авто: ${auto})<br>Ғимараттар: <b style="color:#6a1b9a">${blds.length}</b> · Камералар: <b style="color:#0277bd">${42+cams.length}</b>`;
    document.getElementById('stat-total').textContent=incs.length;
    document.getElementById('lc-crimes').textContent=incs.length;
    document.getElementById('lc-buildings').textContent=blds.length;
    // Update camera count badge
    const camCount = 42 + cams.length;
    document.getElementById('lc-cameras').textContent = camCount;
    const hint=document.getElementById('empty-hint');
    if(hint) hint.classList.toggle('hidden', incs.length>0);
  }
};

// ============ THEME ============
function applyTheme(t){
  document.documentElement.setAttribute('data-theme',t);
  document.getElementById('theme-toggle').textContent=t==='dark'?'☀️ Жарық':'🌙 Қараңғы';
  DB.saveSetting('theme',t);
}
function toggleTheme(){const cur=document.documentElement.getAttribute('data-theme')||'light';applyTheme(cur==='dark'?'light':'dark');}
const savedSettings=DB.getSettings();
applyTheme(savedSettings.theme||'light');

// ============ MAP ============
const map=L.map('map',{zoomControl:true}).setView([42.30,69.59],12);
L.tileLayer('https://{s}.basemaps.cartocdn.com/light_all/{z}/{x}/{y}{r}.png',{attribution:'&copy; OpenStreetMap & CartoDB'}).addTo(map);

// ============ DISTRICT POLYGONS ============
const districtPolygons={};
let activeDistrict=null;

async function loadOSMBoundaries(){
  const loader=document.getElementById('osm-loader');
  const loaderText=document.getElementById('osm-loader-text');
  const query=`[out:json][timeout:30];(relation["boundary"="administrative"]["admin_level"~"^(7|8|9)$"]["name"~"район"]["name"~"(Абайский|Аль-Фараби|Каратаус|Енбекшин|Туранский)"](41.5,68.8,42.8,70.5););out geom;`.trim();
  try{
    loaderText.textContent='Overpass API сұрауы...';
    const response=await fetch('https://overpass-api.de/api/interpreter',{method:'POST',headers:{'Content-Type':'application/x-www-form-urlencoded'},body:'data='+encodeURIComponent(query)});
    if(!response.ok)throw new Error('Network error');
    const data=await response.json();
    if(!data.elements||data.elements.length===0)throw new Error('No data');
    let matched=0;
    data.elements.forEach(el=>{
      if(el.type!=='relation'||!el.members)return;
      const name=el.tags?.name||'';
      let districtId=null;
      if(name.includes('Абайский'))districtId='abay';
      else if(name.includes('Аль-Фараби')||name.includes('Аль-Фарабийский'))districtId='alfarabi';
      else if(name.includes('Каратаус')||name.includes('Каратауский'))districtId='karatau';
      else if(name.includes('Енбекши')||name.includes('Енбекшинский'))districtId='enbekshi';
      else if(name.includes('Туранский')||name.includes('Туран'))districtId='turan';
      if(!districtId)return;
      const coords=buildPolygonFromRelation(el);
      if(coords&&coords.length>3){addDistrictPolygon(districtId,coords,name);matched++;}
    });
    if(matched>0){loaderText.textContent=`✅ ${matched} аудан жүктелді`;setTimeout(()=>loader.classList.add('hidden'),2500);}
    else throw new Error('No match');
  }catch(err){
    loaderText.textContent='⚠️ Резервтік шекаралар';
    loadFallbackBoundaries();
    setTimeout(()=>loader.classList.add('hidden'),2500);
  }
}

function buildPolygonFromRelation(relation){
  const outerWays=relation.members.filter(m=>m.type==='way'&&m.role==='outer'&&m.geometry).map(m=>m.geometry.map(g=>[g.lat,g.lon]));
  if(outerWays.length===0)return null;
  let ring=[...outerWays[0]];
  const remaining=outerWays.slice(1);
  let changed=true;
  while(changed&&remaining.length>0){
    changed=false;
    for(let i=0;i<remaining.length;i++){
      const way=remaining[i];const lastPt=ring[ring.length-1];const firstPt=ring[0];
      if(dist(lastPt,way[0])<0.0001){ring=ring.concat(way.slice(1));remaining.splice(i,1);changed=true;break;}
      if(dist(lastPt,way[way.length-1])<0.0001){ring=ring.concat(way.slice(0,-1).reverse());remaining.splice(i,1);changed=true;break;}
      if(dist(firstPt,way[way.length-1])<0.0001){ring=way.concat(ring.slice(1));remaining.splice(i,1);changed=true;break;}
      if(dist(firstPt,way[0])<0.0001){ring=way.slice().reverse().concat(ring.slice(1));remaining.splice(i,1);changed=true;break;}
    }
  }
  if(remaining.length>0)remaining.forEach(w=>ring=ring.concat(w));
  return ring;
}
function dist(a,b){return Math.sqrt((a[0]-b[0])**2+(a[1]-b[1])**2);}

function addDistrictPolygon(id,coords,osmName){
  const d=districtData[id];
  if(districtPolygons[id]){map.removeLayer(districtPolygons[id]);if(districtPolygons[id]._label)map.removeLayer(districtPolygons[id]._label);}
  const poly=L.polygon(coords,{color:d.color,weight:2.5,fillColor:d.color,fillOpacity:0.10,smoothFactor:1}).addTo(map);
  const center=poly.getBounds().getCenter();
  const label=L.marker(center,{interactive:false,icon:L.divIcon({className:'',iconSize:[200,44],iconAnchor:[100,22],html:`<div style="text-align:center;pointer-events:none;user-select:none"><div style="font-family:'Rubik',sans-serif;font-size:11px;font-weight:700;color:${d.color};text-shadow:0 0 5px #fff,0 1px 3px rgba(255,255,255,.95);letter-spacing:.5px;white-space:nowrap">${d.name.toUpperCase()}</div><div style="font-family:'JetBrains Mono',sans-serif;font-size:9px;color:#444;text-shadow:0 1px 3px rgba(255,255,255,.95);white-space:nowrap;margin-top:1px">👥 ${d.pop.toLocaleString('ru-RU')} · 🔍 ${d.total} іс</div></div>`})}).addTo(map);
  poly._label=label;
  poly.on('click',()=>{if(mapMode)return;document.getElementById('region-select').value=id;focusDistrict(id);switchTab('district',document.querySelectorAll('.tab-btn')[3]);});
  poly.on('mouseover',function(){if(mapMode)return;this.setStyle({fillOpacity:0.25,weight:3.5});});
  poly.on('mouseout',function(){this.setStyle({fillOpacity:activeDistrict===id?0.22:0.10,weight:activeDistrict===id?3.5:2.5});});
  districtPolygons[id]=poly;
}

function loadFallbackBoundaries(){
  const fb={
    turan:[[42.32789,69.52900],[42.32534,69.52329],[42.33090,69.51763],[42.33466,69.51030],[42.33707,69.50679],[42.33795,69.50133],[42.33858,69.49953],[42.34031,69.48852],[42.34107,69.48396],[42.34116,69.48137],[42.34209,69.47942],[42.34462,69.47944],[42.34622,69.46801],[42.34803,69.46463],[42.35030,69.45931],[42.35257,69.45271],[42.35386,69.44843],[42.35629,69.44368],[42.35846,69.43616],[42.36088,69.43282],[42.36290,69.42829],[42.36375,69.42451],[42.36310,69.42124],[42.36200,69.41055],[42.36253,69.40519],[42.36109,69.40134],[42.36094,69.39849],[42.36272,69.39335],[42.36453,69.39175],[42.36965,69.37812],[42.36958,69.37068],[42.36928,69.36409],[42.37667,69.36580],[42.37768,69.35678],[42.37565,69.32612],[42.36361,69.30299],[42.35634,69.30232],[42.35534,69.31243],[42.35202,69.31474],[42.35384,69.31945],[42.33863,69.31114],[42.32224,69.30379],[42.31044,69.32318],[42.29077,69.34960],[42.24931,69.36595],[42.22894,69.34020],[42.22164,69.40136],[42.19708,69.41134],[42.16302,69.42859],[42.14619,69.47555],[42.12522,69.48563],[42.12487,69.49167],[42.13642,69.51783],[42.13677,69.53619],[42.14713,69.53265],[42.15681,69.53472],[42.17357,69.53217],[42.18167,69.53460],[42.19495,69.52336],[42.21731,69.52893],[42.24797,69.54261],[42.28926,69.56485],[42.30809,69.57649],[42.31784,69.58152],[42.32059,69.58764],[42.32309,69.58976]],
    abay:[[42.35954,69.61857],[42.37400,69.62736],[42.38842,69.62849],[42.41244,69.63413],[42.42193,69.63733],[42.43277,69.63529],[42.45176,69.63351],[42.45579,69.60863],[42.46469,69.56768],[42.47342,69.54170],[42.47834,69.53303],[42.47926,69.49755],[42.47843,69.46210],[42.47284,69.46257],[42.46906,69.45465],[42.46340,69.45107],[42.46065,69.45740],[42.45405,69.45839],[42.45157,69.46321],[42.44291,69.45818],[42.44048,69.44961],[42.43583,69.43498],[42.42351,69.44058],[42.41731,69.43408],[42.41716,69.42732],[42.41835,69.42002],[42.42052,69.41804],[42.41985,69.40928],[42.42060,69.40656],[42.42008,69.40255],[42.41715,69.39930],[42.41663,69.39470],[42.41447,69.39191],[42.41068,69.39083],[42.40590,69.38602],[42.39406,69.38844],[42.38311,69.38068],[42.37852,69.35108],[42.37452,69.35065],[42.37402,69.36505],[42.36953,69.36896],[42.36745,69.38296],[42.36535,69.38492],[42.36540,69.38911],[42.36149,69.39405],[42.36012,69.40024],[42.36196,69.40380],[42.36243,69.40860],[42.36285,69.41705],[42.36381,69.42497],[42.35845,69.43747],[42.35306,69.45349],[42.34870,69.46500],[42.34543,69.47076],[42.34079,69.48699],[42.33598,69.50197],[42.33445,69.51001],[42.32762,69.52022],[42.32110,69.53720],[42.33543,69.55421],[42.33928,69.55886],[42.34815,69.56685],[42.35267,69.57708],[42.35806,69.58555],[42.36254,69.60136],[42.35866,69.61801],[42.35962,69.61861]],
    karatau:[[42.35873,69.61824],[42.37912,69.62926],[42.41944,69.63700],[42.45188,69.63322],[42.44473,69.67670],[42.43940,69.71499],[42.42904,69.72128],[42.41791,69.72497],[42.40855,69.74349],[42.39602,69.76407],[42.39071,69.77834],[42.37112,69.78994],[42.36515,69.80060],[42.35537,69.81823],[42.34867,69.81628],[42.33957,69.82769],[42.33701,69.83041],[42.33445,69.84004],[42.33754,69.84763],[42.33412,69.86480],[42.32051,69.89136],[42.30003,69.91229],[42.29588,69.92184],[42.28528,69.93691],[42.27572,69.93028],[42.29061,69.90941],[42.29560,69.89567],[42.29846,69.86386],[42.29814,69.85677],[42.30132,69.84262],[42.30061,69.82000],[42.29977,69.81315],[42.29884,69.80892],[42.29113,69.78794],[42.29572,69.77169],[42.28655,69.75567],[42.28188,69.73220],[42.28095,69.72334],[42.29682,69.72410],[42.31091,69.72383],[42.31559,69.71682],[42.32681,69.71567],[42.32954,69.71304],[42.33569,69.71099],[42.33827,69.70808],[42.34609,69.69970],[42.34731,69.68887],[42.33436,69.65044],[42.33684,69.65208],[42.34493,69.64610],[42.34608,69.64406],[42.34640,69.63371],[42.34800,69.62666],[42.35580,69.63002],[42.35874,69.61824]],
    alfarabi:[[42.33256,69.59373],[42.32710,69.61737],[42.34797,69.62672],[42.34617,69.64481],[42.34493,69.64609],[42.33684,69.65208],[42.33426,69.65027],[42.32928,69.63392],[42.31562,69.63144],[42.30363,69.62643],[42.30018,69.61270],[42.28986,69.60346],[42.28412,69.59243],[42.27749,69.58885],[42.27431,69.59309],[42.26724,69.59503],[42.25527,69.59442],[42.24412,69.59161],[42.23070,69.59302],[42.22172,69.60819],[42.19316,69.63335],[42.16360,69.64747],[42.15393,69.65174],[42.13835,69.57755],[42.13112,69.55842],[42.12334,69.54120],[42.13668,69.53590],[42.14822,69.53283],[42.17839,69.53255],[42.19495,69.52336],[42.21731,69.52893],[42.24797,69.54261],[42.28926,69.56485],[42.30809,69.57649],[42.32085,69.58767],[42.32307,69.58977],[42.33256,69.59373]],
    enbekshi:[[42.23001,69.59690],[42.22435,69.63430],[42.19997,69.63564],[42.17187,69.69303],[42.22570,69.70971],[42.22976,69.72211],[42.23221,69.75899],[42.20979,69.75656],[42.19851,69.76223],[42.21401,69.78600],[42.20432,69.79436],[42.22016,69.82691],[42.24225,69.81156],[42.26641,69.82475],[42.26653,69.84476],[42.26819,69.86590],[42.27952,69.87509],[42.28749,69.88668],[42.29059,69.90941],[42.29570,69.89572],[42.29846,69.86386],[42.29977,69.81315],[42.29113,69.78794],[42.29572,69.77169],[42.28655,69.75567],[42.28095,69.72334],[42.31091,69.72383],[42.31559,69.71682],[42.32681,69.71567],[42.33826,69.70808],[42.34582,69.68436],[42.32944,69.63367],[42.30517,69.61965],[42.30191,69.61672],[42.29853,69.61029],[42.28412,69.59243],[42.28072,69.58814],[42.27735,69.58889],[42.27421,69.59381],[42.26724,69.59503],[42.25527,69.59442],[42.23683,69.58990],[42.22979,69.59699]]
  };
  Object.entries(fb).forEach(([id,coords])=>addDistrictPolygon(id,coords,districtData[id].osmName));
}

// ============ LAYERS ============
const layers={crimes:[],dtp:[],police:[],cameras:[],hospitals:[],schools:[],bazaars:[],posts:[],userBuildings:[]};
const layerVisible={crimes:true,dtp:true,police:true,cameras:true,hospitals:true,schools:true,bazaars:true,posts:true,userBuildings:true};

function mkIcon(html,s=22){return L.divIcon({className:'',iconSize:[s,s],iconAnchor:[s/2,s/2],html});}

function isPointInPolygon(point,polygon){
  let x=point[0],y=point[1],inside=false;
  for(let i=0,j=polygon.length-1;i<polygon.length;j=i++){
    const xi=polygon[i][0],yi=polygon[i][1],xj=polygon[j][0],yj=polygon[j][1];
    if(((yi>y)!=(yj>y))&&(x<(xj-xi)*(y-yi)/(yj-yi)+xi))inside=!inside;
  }
  return inside;
}

function getDistrictForPoint(lat,lng){
  for(const [id,poly] of Object.entries(districtPolygons)){
    if(poly.getBounds().contains([lat,lng])){
      const coords=poly.getLatLngs()[0].map(ll=>[ll.lat,ll.lng]);
      if(isPointInPolygon([lat,lng],coords))return id;
    }
  }
  return null;
}

// ============ PREDEFINED MARKERS ============
// Cameras
[[42.3169,69.5874],[42.3201,69.5920],[42.3145,69.5810],[42.3089,69.5750],[42.3230,69.5960],[42.3280,69.6050],[42.3350,69.5880],[42.3190,69.5680],[42.3110,69.5840],[42.3410,69.5950],[42.3050,69.5950],[42.2980,69.5880],[42.3300,69.5600],[42.3480,69.5480],[42.3380,69.6200],[42.3150,69.6100],[42.3070,69.6000],[42.3230,69.5750],[42.3170,69.5950],[42.3420,69.5750],[42.3260,69.5830],[42.3190,69.5790],[42.3320,69.6100],[42.2920,69.5800],[42.3550,69.5700],[42.3650,69.5500],[42.3480,69.6000],[42.3090,69.5680],[42.3210,69.6050],[42.3340,69.5780],[42.3160,69.5920],[42.3410,69.5690],[42.3580,69.5850],[42.3050,69.6100],[42.3730,69.5200],[42.3850,69.5350],[42.2990,69.5700],[42.3240,69.5870],[42.3120,69.5760],[42.3370,69.5930],[42.3490,69.5580],[42.3270,69.6120]].forEach(([lat,lng],i)=>{
  const m=L.marker([lat,lng],{icon:mkIcon(`<div style="width:10px;height:10px;background:#1565c0;border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(21,101,192,.6)"></div>`,14)}).bindPopup(`<div class="popup-inner"><div class="popup-title">📷 Камера #${i+1}</div><div class="popup-row">✅ HD · Жұмыс істеп тұр</div></div>`);
  m._district=null; m.addTo(map); layers.cameras.push(m);
});

// Posts (учаскелік)
[[42.3350,69.5700],[42.3820,69.5600],[42.3100,69.5900],[42.2980,69.6050],[42.3700,69.6300],[42.3950,69.6200],[42.3600,69.5000],[42.3350,69.4700],[42.3180,69.5400],[42.3050,69.5300],[42.4050,69.5500],[42.3169,69.5820]].forEach(([lat,lng],i)=>{
  const m=L.marker([lat,lng],{icon:mkIcon(`<div style="background:#fff;border:2px solid #2e7d32;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🏛</div>`,18)}).bindPopup(`<div class="popup-inner"><div class="popup-title">🏛 Учаскелік пункт #${i+1}</div></div>`);
  m._district=null; m.addTo(map); layers.posts.push(m);
});

// Hospitals
[[42.3180,69.5950,'Қалалық аурухана №1'],[42.3050,69.5820,'БСМП жедел жәрдем'],[42.3320,69.6000,'Балалар ауруханасы'],[42.3450,69.5800,'Абай ауданы клиникасы'],[42.2950,69.5950,'Аль-Фараби ДМЦ'],[42.3600,69.6100,'Манкент клиникасы'],[42.3150,69.5650,'БСМП орталығы'],[42.3800,69.5200,'Қаратау ауданы ауруханасы'],[42.3070,69.6150,'Самал медорталық']].forEach(([lat,lng,name])=>{
  const m=L.marker([lat,lng],{icon:mkIcon(`<div style="background:#fff;border:2px solid #00897b;border-radius:4px;width:17px;height:17px;display:flex;align-items:center;justify-content:center;font-size:10px">🏥</div>`,19)}).bindPopup(`<div class="popup-inner"><div class="popup-title" style="color:#00897b">🏥 ${name}</div></div>`);
  m._district=null; m.addTo(map); layers.hospitals.push(m);
});

// Schools
[[42.3220,69.5880,'№1'],[42.3300,69.6050,'№5'],[42.3140,69.5780,'№12'],[42.3410,69.5760,'№18'],[42.3080,69.5950,'№23'],[42.3500,69.6050,'№31'],[42.3650,69.5400,'№44'],[42.3250,69.5500,'№52'],[42.3050,69.5700,'№67'],[42.3750,69.5800,'№74'],[42.3180,69.6100,'№88'],[42.2950,69.5850,'№93'],[42.3550,69.5600,'№101'],[42.3900,69.5450,'Абай мектебі']].forEach(([lat,lng,name])=>{
  const m=L.marker([lat,lng],{icon:mkIcon(`<div style="background:#fff;border:2px solid #f57f17;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🏫</div>`,18)}).bindPopup(`<div class="popup-inner"><div class="popup-title" style="color:#f57f17">🏫 Мектеп ${name}</div></div>`);
  m._district=null; m.addTo(map); layers.schools.push(m);
});

// Bazaars
[[42.3180,69.5870,'Ордабасы'],[42.3250,69.5930,'Аль-Фараби'],[42.3120,69.5820,'Байтерек'],[42.3380,69.5980,'Манкент'],[42.3500,69.5700,'Қаратаев'],[42.3050,69.6050,'Самал ТЦ'],[42.3290,69.5780,'Центральный'],[42.3080,69.5870,'Жедел']].forEach(([lat,lng,name])=>{
  const m=L.marker([lat,lng],{icon:mkIcon(`<div style="background:#fff;border:2px solid #6d4c41;border-radius:4px;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">🛒</div>`,18)}).bindPopup(`<div class="popup-inner"><div class="popup-title" style="color:#6d4c41">🛒 ${name}</div></div>`);
  m._district=null; m.addTo(map); layers.bazaars.push(m);
});

// DTP
[[42.3169,69.5874,'Соқтығысу',1,'alfarabi'],[42.3280,69.6050,'Жаяу жүргіншіні басу',0,'alfarabi'],[42.3050,69.5950,'Аударылу',2,'alfarabi'],[42.3410,69.5950,'Соқтығысу',1,'abay'],[42.3230,69.5960,'Кері соқтығысу',0,'alfarabi'],[42.3089,69.5750,'Соқтығысу',1,'turan'],[42.3380,69.6200,'Жаяу жүргіншіні басу',1,'abay'],[42.3150,69.6100,'Аударылу',0,'alfarabi'],[42.3070,69.6000,'Соқтығысу',2,'alfarabi'],[42.3480,69.5480,'Соқтығысу',0,'turan'],[42.2920,69.5800,'Кері соқтығысу',1,'enbekshi'],[42.3550,69.5700,'Соқтығысу',0,'karatau'],[42.3650,69.5500,'Жаяу жүргіншіні басу',1,'karatau'],[42.3800,69.5200,'Аударылу',0,'karatau'],[42.3300,69.5600,'Соқтығысу',2,'karatau'],[42.3190,69.5680,'Кері соқтығысу',0,'turan'],[42.3110,69.5840,'Соқтығысу',1,'alfarabi'],[42.3200,69.5750,'Аударылу',0,'turan'],[42.3420,69.5750,'Жаяу жүргіншіні басу',1,'abay'],[42.3730,69.5200,'Соқтығысу',0,'abay'],[42.3490,69.5580,'Кері соқтығысу',2,'turan'],[42.4100,69.5400,'Соқтығысу',1,'abay'],[42.3850,69.5350,'Аударылу',0,'abay'],[42.3260,69.6120,'Жаяу жүргіншіні басу',1,'alfarabi'],[42.3170,69.5950,'Соқтығысу',0,'alfarabi']].forEach(([lat,lng,type,inj,district],i)=>{
  const m=L.marker([lat,lng],{icon:mkIcon(`<div style="background:#fff;border:2px solid #fb8c00;border-radius:50%;width:16px;height:16px;display:flex;align-items:center;justify-content:center;font-size:9px">💥</div>`,18)}).bindPopup(`<div class="popup-inner"><div class="popup-title" style="color:#fb8c00">ЖКО #${i+1}</div><div class="popup-row">Түрі: ${type}</div><div class="popup-row">Жарақат: ${inj} адам</div></div>`);
  m._district=district; m.addTo(map); layers.dtp.push(m);
});

// ============ PATROL CARS ============
const carRoutes=[
  {name:'ПМ-001',street:'Абай даңғылы — Солтүстік',district:'abay',path:[[42.374,69.627],[42.348,69.612],[42.345,69.609],[42.352,69.578],[42.345,69.559],[42.352,69.578],[42.345,69.609],[42.348,69.612]]},
  {name:'ПМ-002',street:'Абай — Манкент диагональ',district:'abay',path:[[42.345,69.608],[42.338,69.640],[42.324,69.648],[42.338,69.640]]},
  {name:'ПМ-003',street:'Аль-Фараби — Орталық',district:'alfarabi',path:[[42.307,69.640],[42.324,69.648],[42.338,69.640],[42.345,69.610],[42.338,69.640],[42.324,69.648]]},
  {name:'ПМ-004',street:'Каратаевская — Батыс',district:'karatau',path:[[42.349,69.534],[42.344,69.540],[42.337,69.546],[42.334,69.556],[42.337,69.546],[42.344,69.540]]},
  {name:'ПМ-005',street:'Еңбекшілер — Солтүстік',district:'enbekshi',path:[[42.318,69.596],[42.314,69.611],[42.327,69.617],[42.330,69.601],[42.323,69.598],[42.319,69.593],[42.318,69.596]]},
  {name:'ПМ-006',street:'Туран — Аль-Фараби шекарасы',district:'turan',path:[[42.379,69.595],[42.351,69.582]]},
  {name:'ПМ-007',street:'Еңбекшілер — Оңтүстік',district:'enbekshi',path:[[42.320,69.588],[42.337,69.579],[42.347,69.568],[42.337,69.579]]},
  {name:'ПМ-008',street:'Абай — Солтүстік-шығыс',district:'abay',path:[[42.405,69.550],[42.390,69.562],[42.375,69.575],[42.390,69.562]]},
  // ============ NEW PATROL ROUTES ============
  {
    name:'ПМ-009',
    street:'Аль-Фараби — Оңтүстік-батыс',
    district:'alfarabi',
    path:[
      [42.27290372090928,69.57487363729503],
      [42.27820525149744,69.5790369817754],
      [42.28042731729936,69.57341432067305],
      [42.28245885174663,69.56719076449109],
      [42.27852269426659,69.56405752586154],
      [42.27626881597641,69.56650402725721],
      [42.27576088861201,69.56766289633939],
      [42.27576088861201,69.56869300219016],
      [42.27534819461411,69.57178331974262],
      [42.272871973873855,69.57491655837217],
      [42.27534819461411,69.57178331974262],
      [42.27576088861201,69.56869300219016],
      [42.27576088861201,69.56766289633939],
      [42.27626881597641,69.56650402725721],
      [42.27852269426659,69.56405752586154],
      [42.28245885174663,69.56719076449109],
      [42.28042731729936,69.57341432067305],
      [42.27820525149744,69.5790369817754]
    ]
  },
  {
    name:'ПМ-010',
    street:'Аль-Фараби — Оңтүстік маршрут',
    district:'alfarabi',
    path:[
      [42.27185640265408,69.57462366103383],
      [42.24562746726982,69.56191902220714],
      [42.24302303094808,69.5638933917545],
      [42.24003732533844,69.57342187087453],
      [42.24302303094808,69.5638933917545],
      [42.24562746726982,69.56191902220714]
    ]
  }
];

const policeMarkers=carRoutes.map(route=>{
  const routeLine=L.polyline(route.path,{color:'#7b1fa2',weight:3,opacity:0.35,dashArray:'6,5',smoothFactor:1}).addTo(map);
  const m=L.marker(route.path[0],{icon:L.divIcon({className:'',iconSize:[80,22],iconAnchor:[40,11],html:`<div class="car-label">🚔 ${route.name}</div>`}),zIndexOffset:1000}).bindPopup(`<div class="popup-inner"><div class="popup-title" style="color:#7b1fa2">🚔 ${route.name}</div><div class="popup-row">📍 ${route.street}</div><div class="popup-row">🟢 Патруль</div></div>`);
  m._district=route.district; m.addTo(map); layers.police.push(m);
  m._routeLine=routeLine;
  return {marker:m,path:route.path,idx:0,progress:0,speed:0.003+Math.random()*0.001,routeLine,name:route.name,district:route.district};
});

function animateCars(){
  policeMarkers.forEach(car=>{
    car.progress+=car.speed;
    if(car.progress>=1){car.progress=0;car.idx=(car.idx+1)%(car.path.length-1);}
    const f=car.path[car.idx];const t=car.path[car.idx+1]||car.path[0];
    car.marker.setLatLng([f[0]+(t[0]-f[0])*car.progress,f[1]+(t[1]-f[1])*car.progress]);
  });
  requestAnimationFrame(animateCars);
}
animateCars();

// ============ HEATMAP ============
let heatmapActive=false;
let heatCircles=[];

function toggleHeatmap(){
  heatmapActive=!heatmapActive;
  const btn=document.getElementById('heatmap-btn');
  const legend=document.getElementById('heatmap-legend');
  if(heatmapActive){
    btn.classList.add('active');btn.innerHTML='🌡 Жылу ✓';
    legend.classList.add('show');renderHeatmap();
  }else{
    btn.classList.remove('active');btn.innerHTML='🌡 Жылу';
    legend.classList.remove('show');
    heatCircles.forEach(c=>map.removeLayer(c));heatCircles=[];
  }
}

function renderHeatmap(){
  heatCircles.forEach(c=>map.removeLayer(c));heatCircles=[];
  const hotspots=[
    {lat:42.318,lng:69.587,intensity:0.9},{lat:42.325,lng:69.593,intensity:0.8},{lat:42.308,lng:69.596,intensity:0.75},{lat:42.341,lng:69.595,intensity:0.7},{lat:42.355,lng:69.570,intensity:0.65},{lat:42.329,lng:69.604,intensity:0.6},{lat:42.315,lng:69.565,intensity:0.55},{lat:42.365,lng:69.550,intensity:0.5},{lat:42.295,lng:69.580,intensity:0.5},{lat:42.385,lng:69.535,intensity:0.45},{lat:42.307,lng:69.608,intensity:0.5},{lat:42.345,lng:69.609,intensity:0.45}
  ];
  hotspots.forEach(h=>{
    const intens=h.intensity;
    const r=intens>0.7?'255':intens>0.5?'255':'0';
    const g=intens>0.7?'0':intens>0.5?'165':'128';
    const c=L.circle([h.lat,h.lng],{radius:800+intens*600,color:'transparent',fillColor:`rgb(${r},${g},0)`,fillOpacity:intens*0.35}).addTo(map);
    heatCircles.push(c);
  });
}

// ============ AUTO INCIDENTS ============
let autoMode=savedSettings.autoMode||false;
let autoTimer=null;
const incTypesList=['ст.190','ст.188','ст.109-1','ст.296','ст.108-1','ст.293','ЖКО','ҰРЛЫҚ','ТОНАУ','БҰЗАҚЫЛЫҚ','АЛАЯҚТЫҚ'];
const incLocsByDistrict={
  alfarabi:['Тәуелсіздік даңғылы','Байтерек к-сі','Рысқұлов к-сі','Ордабасы базары маңы'],
  abay:['Абай даңғылы','Таскешу жолы','Манкент тас жолы','Зоопарк маңы'],
  karatau:['Каратаевская к-сі','Аэропорт жолы','Байтерек батыс','Момышұлы к-сі'],
  enbekshi:['Манкент тас жолы','Карасу жолы','Самал мкр','Ленгер жолы'],
  turan:['Желтоқсан к-сі','9 мкр','3 мкр','Рысқұлов к-сі']
};
const districtIds=['alfarabi','abay','karatau','enbekshi','turan'];

function toggleAutoIncidents(){
  autoMode=!autoMode;
  const btn=document.getElementById('auto-btn');
  btn.classList.toggle('active',autoMode);
  btn.innerHTML=autoMode?'🟢 Авто':'🤖 Авто';
  DB.saveSetting('autoMode',autoMode);
  if(autoMode) scheduleNextAuto();
  else if(autoTimer){clearTimeout(autoTimer);autoTimer=null;}
}

function scheduleNextAuto(){
  if(!autoMode)return;
  const delay=9000+Math.random()*6000;
  autoTimer=setTimeout(()=>{addAutoIncident();scheduleNextAuto();},delay);
}

function addAutoIncident(){
  const n=new Date(); const hh=n.getHours().toString().padStart(2,'0'); const mm=n.getMinutes().toString().padStart(2,'0');
  const type=incTypesList[Math.floor(Math.random()*incTypesList.length)];
  const did=districtIds[Math.floor(Math.random()*districtIds.length)];
  const loc=incLocsByDistrict[did][Math.floor(Math.random()*incLocsByDistrict[did].length)];
  const sev=['high','med','med','low'][Math.floor(Math.random()*4)];

  let lat,lng;
  if(districtPolygons[did]){
    const c=districtPolygons[did].getBounds().getCenter();
    lat=c.lat+(Math.random()-.5)*0.03; lng=c.lng+(Math.random()-.5)*0.03;
  } else { lat=42.30+(Math.random()-.5)*0.05; lng=69.59+(Math.random()-.5)*0.05; }

  const inc={type,loc,district:did,time:`${hh}:${mm}`,sev,desc:'Авто жазылым',lat,lng,source:'auto'};
  const saved=DB.addIncident(inc);

  const c=sev==='high'?'#e53935':sev==='med'?'#fb8c00':'#fdd835';
  const m=L.marker([lat,lng],{icon:mkIcon(`<div style="background:#fff;border:3px solid ${c};border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div>`,24)}).bindPopup(
    `<div class="popup-inner"><div class="popup-title" style="color:${c}">${type}</div><div class="popup-row">📍 ${loc}</div><div class="popup-row">⏰ ${hh}:${mm}</div><div class="popup-row" style="color:#2e7d32;font-size:9px">🤖 Авто жазылым</div><button class="popup-delete-btn" onclick="deleteIncident('${saved.id}',this)">🗑 Жою</button></div>`
  );
  m._incidentId=saved.id; m._district=did; m.addTo(map); layers.crimes.push(m);
  allIncidents.unshift({type,loc,time:`${hh}:${mm}`,sev,district:did,id:saved.id,lat,lng,source:'auto'});
  if(allIncidents.length>500)allIncidents.pop();
  DB.updateDBInfo(); renderFeed(activeDistrict); renderHourChart();
  if(sev==='high') showToast('ЖАҢА ОҚИҒА','#e53935',`${type} — ${loc}`);
}

// Restore auto mode
if(autoMode){
  document.getElementById('auto-btn').classList.add('active');
  document.getElementById('auto-btn').innerHTML='🟢 Авто';
  scheduleNextAuto();
}

// ============ MODE ============
let mapMode=null,pendingLat=null,pendingLng=null;

function toggleIncidentMode(){
  if(mapMode==='incident'){cancelMode();return;}
  cancelMode();mapMode='incident';
  document.getElementById('map').classList.add('mode-incident');
  document.getElementById('place-inc-btn').classList.add('active');
  document.getElementById('place-inc-btn').innerHTML='🔴 Картаны басыңыз...';
  showModeBanner('inc-mode','🚨 Картадағы орынды басыңыз — оқиғаны белгілеу үшін');
}
function toggleBuildingMode(){
  if(mapMode==='building'){cancelMode();return;}
  cancelMode();mapMode='building';
  document.getElementById('map').classList.add('mode-building');
  document.getElementById('place-bld-btn').classList.add('active');
  document.getElementById('place-bld-btn').innerHTML='🟣 Картаны басыңыз...';
  showModeBanner('bld-mode','🏢 Картадағы орынды басыңыз — ғимарат белгілеу үшін');
}
function toggleCameraMode(){
  if(mapMode==='camera'){cancelMode();return;}
  cancelMode();mapMode='camera';
  document.getElementById('map').classList.add('mode-camera');
  document.getElementById('place-cam-btn').classList.add('active');
  document.getElementById('place-cam-btn').innerHTML='🔵 Картаны басыңыз...';
  showModeBanner('cam-mode','📷 Картадағы орынды басыңыз — камера орнату үшін');
}
function cancelMode(){
  mapMode=null;
  document.getElementById('map').classList.remove('mode-incident','mode-building','mode-camera');
  document.getElementById('place-inc-btn').classList.remove('active');
  document.getElementById('place-inc-btn').innerHTML='📍 Белгілеу';
  document.getElementById('place-bld-btn').classList.remove('active');
  document.getElementById('place-bld-btn').innerHTML='🏢 Ғимарат';
  document.getElementById('place-cam-btn').classList.remove('active');
  document.getElementById('place-cam-btn').innerHTML='📷 Камера';
  document.getElementById('mode-banner').classList.remove('show');
}
function showModeBanner(cls,text){
  const b=document.getElementById('mode-banner');
  b.className='show '+cls;
  document.getElementById('mode-banner-text').textContent=text;
}

map.on('click',function(e){
  if(!mapMode)return;
  pendingLat=e.latlng.lat;pendingLng=e.latlng.lng;
  const det=getDistrictForPoint(pendingLat,pendingLng);
  if(mapMode==='incident'){cancelMode();openIncidentAtCoords(pendingLat,pendingLng,det);}
  else if(mapMode==='building'){cancelMode();openBuildingAtCoords(pendingLat,pendingLng,det);}
  else if(mapMode==='camera'){cancelMode();openCameraAtCoords(pendingLat,pendingLng,det);}
});

// ============ INCIDENT MODAL ============
let currentSev='high';

function openIncidentAtCoords(lat,lng,det){
  const n=new Date();
  document.getElementById('m-time').value=`${n.getHours().toString().padStart(2,'0')}:${n.getMinutes().toString().padStart(2,'0')}`;
  document.getElementById('modal-coords-display').style.display='flex';
  document.getElementById('modal-coords-text').textContent=`${lat.toFixed(5)}, ${lng.toFixed(5)}${det?' · '+districtData[det].name:''}`;
  if(det)document.getElementById('m-district').value=det;
  document.getElementById('m-loc').value='';document.getElementById('m-desc').value='';
  setSev('high');document.getElementById('modal-overlay').classList.add('show');
}
function openManualModal(){
  const n=new Date();
  document.getElementById('m-time').value=`${n.getHours().toString().padStart(2,'0')}:${n.getMinutes().toString().padStart(2,'0')}`;
  document.getElementById('modal-coords-display').style.display='none';
  pendingLat=null;pendingLng=null;
  document.getElementById('m-loc').value='';document.getElementById('m-desc').value='';
  setSev('high');document.getElementById('modal-overlay').classList.add('show');
}
function closeModal(){document.getElementById('modal-overlay').classList.remove('show');pendingLat=null;pendingLng=null;}
document.getElementById('modal-overlay').addEventListener('click',function(e){if(e.target===this)closeModal();});

function setSev(s){
  currentSev=s;
  ['high','med','low'].forEach(x=>{document.getElementById('sev-'+x).className='sev-btn'+(x===s?' active-'+x:'');});
}

function saveIncident(){
  const type=document.getElementById('m-type').value;
  const loc=document.getElementById('m-loc').value.trim()||'Мекенжай белгісіз';
  const district=document.getElementById('m-district').value;
  const time=document.getElementById('m-time').value;
  const desc=document.getElementById('m-desc').value.trim();
  const inc={type,loc,district,time,sev:currentSev,desc,lat:pendingLat,lng:pendingLng,source:'manual'};
  const saved=DB.addIncident(inc);

  let lat=pendingLat,lng=pendingLng;
  if(!lat||!lng){
    if(districtPolygons[district]){const c=districtPolygons[district].getBounds().getCenter();lat=c.lat+(Math.random()-.5)*0.02;lng=c.lng+(Math.random()-.5)*0.02;}
    else{lat=42.30;lng=69.59;}
  }

  const c=currentSev==='high'?'#e53935':currentSev==='med'?'#fb8c00':'#fdd835';
  const m=L.marker([lat,lng],{icon:mkIcon(`<div style="background:#fff;border:3px solid ${c};border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div>`,24)}).bindPopup(
    `<div class="popup-inner"><div class="popup-title" style="color:${c}">${type}</div><div class="popup-row">📍 ${loc}</div><div class="popup-row">⏰ ${time}</div>${desc?`<div class="popup-row">📝 ${desc}</div>`:''}<button class="popup-delete-btn" onclick="deleteIncident('${saved.id}',this)">🗑 Жою</button></div>`
  );
  m._incidentId=saved.id;m._district=district;m.addTo(map);layers.crimes.push(m);m.openPopup();
  allIncidents.unshift({type,loc,time,sev:currentSev,district,id:saved.id,lat,lng,source:'manual'});
  DB.updateDBInfo();renderFeed(activeDistrict);
  showToast('ЖАҢА ОҚИҒА','#e53935',`${type} — ${loc}`);
  closeModal();
}

function deleteIncident(id){
  DB.removeIncident(id);
  const idx=allIncidents.findIndex(i=>i.id===id);if(idx>-1)allIncidents.splice(idx,1);
  const mIdx=layers.crimes.findIndex(m=>m._incidentId===id);
  if(mIdx>-1){map.removeLayer(layers.crimes[mIdx]);layers.crimes.splice(mIdx,1);}
  DB.updateDBInfo();renderFeed(activeDistrict);
}

// ============ CAMERA MODAL ============
let currentCamStatus='ok';

function openCameraAtCoords(lat,lng,det){
  pendingLat=lat;pendingLng=lng;
  document.getElementById('cam-coords-display').style.display='flex';
  document.getElementById('cam-coords-text').textContent=`${lat.toFixed(5)}, ${lng.toFixed(5)}${det?' · '+districtData[det].name:''}`;
  if(det)document.getElementById('cam-district').value=det;
  document.getElementById('cam-name').value='';
  document.getElementById('cam-loc').value='';
  currentCamStatus='ok';
  setCamStatus('ok');
  // Auto-number
  const total=42+DB.getCameras().length+1;
  document.getElementById('cam-name').placeholder=`Камера #${total}`;
  document.getElementById('cam-modal-overlay').classList.add('show');
}
function closeCamModal(){document.getElementById('cam-modal-overlay').classList.remove('show');pendingLat=null;pendingLng=null;}
document.getElementById('cam-modal-overlay').addEventListener('click',function(e){if(e.target===this)closeCamModal();});

function setCamStatus(s){
  currentCamStatus=s;
  const statuses=['ok','repair','off'];
  statuses.forEach(x=>{
    const btn=document.getElementById('cam-status-'+x);
    btn.className='sev-btn'+(x===s?x==='ok'?' active-low':x==='repair'?' active-med':' active-high':'');
  });
}

function saveCamera(){
  const name=document.getElementById('cam-name').value.trim()||(document.getElementById('cam-name').placeholder);
  const district=document.getElementById('cam-district').value;
  const quality=document.getElementById('cam-quality').value;
  const loc=document.getElementById('cam-loc').value.trim();
  const lat=pendingLat,lng=pendingLng;
  const cam=DB.addCamera({name,district,quality,loc,status:currentCamStatus,lat,lng});

  const statusColor=currentCamStatus==='ok'?'#1565c0':currentCamStatus==='repair'?'#fb8c00':'#e53935';
  const statusIcon=currentCamStatus==='ok'?'✅':currentCamStatus==='repair'?'🔧':'❌';
  const m=L.marker([lat,lng],{icon:mkIcon(`<div style="width:12px;height:12px;background:${statusColor};border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(0,0,0,.4)"></div>`,16)}).bindPopup(
    `<div class="popup-inner"><div class="popup-title" style="color:#1565c0">📷 ${name}</div><div class="popup-row">${statusIcon} ${quality} · ${currentCamStatus==='ok'?'Жұмыс істеп тұр':currentCamStatus==='repair'?'Жөндеуде':'Сөндірілген'}</div>${loc?`<div class="popup-row">📍 ${loc}</div>`:''}<div class="popup-row">🗺 ${districtData[district]?.name||district}</div><button class="popup-delete-btn" onclick="deleteCamera('${cam.id}',this)">🗑 Жою</button></div>`
  );
  m._cameraId=cam.id;m._district=district;m.addTo(map);layers.cameras.push(m);m.openPopup();
  DB.updateDBInfo();closeCamModal();
  showToast('КАМЕРА ҚОСЫЛДЫ','#0277bd',`📷 ${name}`);
}

function deleteCamera(id){
  DB.removeCamera(id);
  const mIdx=layers.cameras.findIndex(m=>m._cameraId===id);
  if(mIdx>-1){map.removeLayer(layers.cameras[mIdx]);layers.cameras.splice(mIdx,1);}
  DB.updateDBInfo();
}

// Load saved cameras from DB
function loadSavedCameras(){
  DB.getCameras().forEach(cam=>{
    if(!cam.lat||!cam.lng)return;
    const statusColor=cam.status==='ok'?'#1565c0':cam.status==='repair'?'#fb8c00':'#e53935';
    const statusIcon=cam.status==='ok'?'✅':cam.status==='repair'?'🔧':'❌';
    const m=L.marker([cam.lat,cam.lng],{icon:mkIcon(`<div style="width:12px;height:12px;background:${statusColor};border-radius:50%;border:2px solid #fff;box-shadow:0 1px 5px rgba(0,0,0,.4)"></div>`,16)}).bindPopup(
      `<div class="popup-inner"><div class="popup-title" style="color:#1565c0">📷 ${cam.name}</div><div class="popup-row">${statusIcon} ${cam.quality||'HD'} · ${cam.status==='ok'?'Жұмыс істеп тұр':cam.status==='repair'?'Жөндеуде':'Сөндірілген'}</div>${cam.loc?`<div class="popup-row">📍 ${cam.loc}</div>`:''}<button class="popup-delete-btn" onclick="deleteCamera('${cam.id}',this)">🗑 Жою</button></div>`
    );
    m._cameraId=cam.id;m._district=cam.district;m.addTo(map);layers.cameras.push(m);
  });
}

// ============ BUILDING MODAL ============
const buildingEmojis=['🏫','🏥','🛒','🏛','🏦','🕌','🍽️','🏨','🏭','🏠','🏋️','🏟️','🎭','🎓','💒','🚒','🚓','🏗️','🌳','🏪'];
let selectedEmoji='🏢';

function buildEmojiGrid(){
  const grid=document.getElementById('emoji-grid');grid.innerHTML='';
  buildingEmojis.forEach(e=>{
    const div=document.createElement('div');
    div.className='emoji-option'+(e===selectedEmoji?' selected':'');
    div.textContent=e;
    div.onclick=()=>{selectedEmoji=e;document.querySelectorAll('.emoji-option').forEach(el=>el.classList.remove('selected'));div.classList.add('selected');};
    grid.appendChild(div);
  });
}

function openBuildingAtCoords(lat,lng,det){
  pendingLat=lat;pendingLng=lng;
  document.getElementById('bld-coords-display').style.display='flex';
  document.getElementById('bld-coords-text').textContent=`${lat.toFixed(5)}, ${lng.toFixed(5)}${det?' · '+districtData[det].name:''}`;
  if(det)document.getElementById('b-district').value=det;
  document.getElementById('b-name').value='';document.getElementById('b-desc').value='';
  selectedEmoji='🏢';buildEmojiGrid();
  document.getElementById('bld-modal-overlay').classList.add('show');
}
function closeBldModal(){document.getElementById('bld-modal-overlay').classList.remove('show');pendingLat=null;pendingLng=null;}
document.getElementById('bld-modal-overlay').addEventListener('click',function(e){if(e.target===this)closeBldModal();});

function saveBuilding(){
  const name=document.getElementById('b-name').value.trim();
  if(!name){document.getElementById('b-name').focus();document.getElementById('b-name').style.borderColor='#e53935';return;}
  document.getElementById('b-name').style.borderColor='';
  const type=document.getElementById('b-type').value;
  const district=document.getElementById('b-district').value;
  const desc=document.getElementById('b-desc').value.trim();
  const lat=pendingLat,lng=pendingLng,emoji=selectedEmoji;
  const bld=DB.addBuilding({name,type,district,desc,lat,lng,emoji});
  const dColor=districtData[district]?.color||'#6a1b9a';
  const m=L.marker([lat,lng],{icon:mkIcon(`<div style="background:#fff;border:2.5px solid ${dColor};border-radius:7px;width:28px;height:28px;display:flex;align-items:center;justify-content:center;font-size:16px;box-shadow:0 2px 8px rgba(0,0,0,.2)">${emoji}</div>`,30)}).bindPopup(
    `<div class="popup-inner"><div class="popup-title">${emoji} ${name}</div><div class="popup-row">🏷 ${type}</div>${desc?`<div class="popup-row">📝 ${desc}</div>`:''}<div class="popup-row">📍 ${districtData[district]?.name||district}</div><button class="popup-delete-btn" style="background:#ede7f6;color:#4a148c" onclick="deleteBuilding('${bld.id}',this)">🗑 Жою</button></div>`
  );
  m._buildingId=bld.id;m._district=district;m.addTo(map);layers.userBuildings.push(m);m.openPopup();
  DB.updateDBInfo();renderBuildingsTab();closeBldModal();
  showToast('ҒИМАРАТ ҚОСЫЛДЫ','#6a1b9a',`${emoji} ${name}`);
}

function deleteBuilding(id){
  DB.removeBuilding(id);
  const mIdx=layers.userBuildings.findIndex(m=>m._buildingId===id);
  if(mIdx>-1){map.removeLayer(layers.userBuildings[mIdx]);layers.userBuildings.splice(mIdx,1);}
  DB.updateDBInfo();renderBuildingsTab();
}

function loadSavedBuildings(){
  DB.getBuildings().forEach(bld=>{
    if(!bld.lat||!bld.lng)return;
    const dColor=districtData[bld.district]?.color||'#6a1b9a';
    const emoji=bld.emoji||'🏢';
    const m=L.marker([bld.lat,bld.lng],{icon:mkIcon(`<div style="background:#fff;border:2.5px solid ${dColor};border-radius:7px;width:28px;height:28px;display:flex;align-items:center;justify-content:center;font-size:16px;box-shadow:0 2px 8px rgba(0,0,0,.2)">${emoji}</div>`,30)}).bindPopup(
      `<div class="popup-inner"><div class="popup-title">${emoji} ${bld.name}</div><div class="popup-row">🏷 ${bld.type}</div>${bld.desc?`<div class="popup-row">📝 ${bld.desc}</div>`:''}<div class="popup-row">📍 ${districtData[bld.district]?.name||bld.district}</div><button class="popup-delete-btn" style="background:#ede7f6;color:#4a148c" onclick="deleteBuilding('${bld.id}',this)">🗑 Жою</button></div>`
    );
    m._buildingId=bld.id;m._district=bld.district;m.addTo(map);layers.userBuildings.push(m);
  });
  renderBuildingsTab();
}

function renderBuildingsTab(){
  const blds=DB.getBuildings();
  const el=document.getElementById('buildings-feed');
  if(!blds.length){el.innerHTML=`<div style="padding:22px 14px;text-align:center;color:var(--text-muted);font-size:11px"><div style="font-size:30px;margin-bottom:7px">🏢</div>Ғимараттар жоқ</div>`;return;}
  el.innerHTML=blds.map(b=>`<div class="bld-item" onclick="map.setView([${b.lat},${b.lng}],16)"><div class="bld-emoji">${b.emoji||'🏢'}</div><div class="bld-info"><div class="bld-name">${b.name}</div><div class="bld-type">${b.type}</div><span class="bld-district-badge" style="background:${districtData[b.district]?.color||'#666'}">${districtData[b.district]?.name?.replace(' ауданы','')||b.district}</span></div><button class="bld-delete" onclick="event.stopPropagation();deleteBuilding('${b.id}',this)">🗑</button></div>`).join('');
}

// ============ LAYERS ============
function toggleLayer(name){
  layerVisible[name]=!layerVisible[name];
  document.getElementById('l-'+name).checked=layerVisible[name];
  layers[name].forEach(m=>{
    if(!layerVisible[name]){if(map.hasLayer(m))map.removeLayer(m);}
    else{if(!activeDistrict||m._district===activeDistrict||m._district===null)m.addTo(map);}
  });
}

// ============ DISTRICT FOCUS ============
function focusDistrict(id){
  activeDistrict=id;
  const d=districtData[id];
  Object.entries(districtPolygons).forEach(([k,p])=>{
    if(k===id){p.setStyle({fillOpacity:0.25,weight:4,color:d.color,fillColor:d.color});p.bringToFront();}
    else{p.setStyle({fillOpacity:0.03,weight:1,color:'#bbb',fillColor:'#bbb'});}
  });
  Object.keys(layers).forEach(ln=>{
    if(!layerVisible[ln])return;
    layers[ln].forEach(m=>{
      if(m._district===id||m._district===null){if(!map.hasLayer(m))m.addTo(map);}
      else{if(map.hasLayer(m))map.removeLayer(m);}
    });
  });
  if(districtPolygons[id])map.fitBounds(districtPolygons[id].getBounds(),{padding:[50,50]});
  document.getElementById('focus-banner').classList.add('show');
  document.getElementById('fb-dot').style.background=d.color;
  document.getElementById('fb-name').textContent=d.name;
  document.getElementById('fb-stats').textContent=`Халық: ${d.pop.toLocaleString('ru-RU')} · ст.190: ${d.st190} · ст.188: ${d.st188}`;
  document.getElementById('dc-name').textContent=d.name;
  document.getElementById('dc-st190').textContent=d.st190;
  document.getElementById('dc-st188').textContent=d.st188;
  document.getElementById('dc-st1091').textContent=d.st1091;
  document.getElementById('dc-total').textContent=d.total;
  document.getElementById('dc-streets').innerHTML=`
    <div class="pop-overlay">
      <div class="pop-overlay-title">👥 ХАЛЫҚ САНЫ</div>
      <div class="pop-overlay-val">${d.pop.toLocaleString('ru-RU')}</div>
      <div class="pop-overlay-row"><span>👨 ${d.popMale.toLocaleString('ru-RU')}</span><span>👩 ${d.popFemale.toLocaleString('ru-RU')}</span><span>📐 ${d.density}/км²</span></div>
    </div>
    <div style="margin-top:7px">
      <strong style="font-size:8px;opacity:.75;letter-spacing:1px;display:block;margin-bottom:4px">АУДАН БОЙЫНША БАПТАР</strong>
      ${[['ст.190',d.st190,'#fb8c00'],['ст.188',d.st188,'#e53935'],['ст.109-1',d.st1091,'#f9a825'],['ст.296',d.st296||0,'#8e24aa'],['ст.108-1',d.st1081||0,'#0288d1']].map(([k,v,c])=>`<div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:3px"><span style="font-size:9px;color:rgba(255,255,255,.8)">${k}</span><span style="font-size:10px;font-weight:700;color:#fff;font-family:'JetBrains Mono',monospace">${v}</span></div>`).join('')}
    </div>
    <div style="margin-top:7px;font-size:8px;opacity:.75;letter-spacing:1px;text-transform:uppercase;margin-bottom:3px">НЕГІЗГІ КӨШЕЛЕР</div>
    <div style="font-size:9px;opacity:.85">${d.streets.join(' · ')}</div>`;
  document.getElementById('district-card').style.background=`linear-gradient(135deg,${d.color}ee,${d.color}aa)`;
  document.getElementById('district-card').classList.add('show');
  document.getElementById('district-hint').style.display='none';
  policeMarkers.forEach(car=>{
    if(!car.routeLine)return;
    if(car.district===id){if(!map.hasLayer(car.routeLine))car.routeLine.addTo(map);}
    else{if(map.hasLayer(car.routeLine))map.removeLayer(car.routeLine);}
  });
  renderFeed(id);renderUnits(id);
}

function resetFocus(){
  activeDistrict=null;
  Object.entries(districtPolygons).forEach(([k,p])=>{const d=districtData[k];p.setStyle({fillOpacity:0.10,weight:2.5,color:d.color,fillColor:d.color});});
  Object.keys(layers).forEach(ln=>{if(!layerVisible[ln])return;layers[ln].forEach(m=>{if(!map.hasLayer(m))m.addTo(map);});});
  policeMarkers.forEach(car=>{if(car.routeLine&&!map.hasLayer(car.routeLine))car.routeLine.addTo(map);});
  document.getElementById('focus-banner').classList.remove('show');
  document.getElementById('district-card').classList.remove('show');
  document.getElementById('district-hint').style.display='block';
  document.getElementById('region-select').value='';
  map.setView([42.30,69.59],12);
  renderFeed(null);renderUnits(null);
}

// ============ FEED ============
const allIncidents=[];
DB.getIncidents().forEach(i=>{
  allIncidents.push({type:i.type,loc:i.loc,time:i.time||'—',sev:i.sev,district:i.district,id:i.id,lat:i.lat,lng:i.lng,source:i.source});
  if(i.lat&&i.lng){
    const c=i.sev==='high'?'#e53935':i.sev==='med'?'#fb8c00':'#fdd835';
    const m=L.marker([i.lat,i.lng],{icon:mkIcon(`<div style="background:#fff;border:3px solid ${c};border-radius:50%;width:22px;height:22px;display:flex;align-items:center;justify-content:center;font-size:12px;box-shadow:0 2px 8px rgba(0,0,0,.3)">📌</div>`,24)}).bindPopup(
      `<div class="popup-inner"><div class="popup-title" style="color:${c}">${i.type}</div><div class="popup-row">📍 ${i.loc}</div><div class="popup-row">⏰ ${i.time||'—'}</div>${i.source==='auto'?'<div class="popup-row" style="color:#2e7d32;font-size:9px">🤖 Авто</div>':''}<button class="popup-delete-btn" onclick="deleteIncident('${i.id}',this)">🗑 Жою</button></div>`
    );
    m._incidentId=i.id;m._district=i.district;m.addTo(map);layers.crimes.push(m);
  }
});

const districtColors={karatau:'#7b1fa2',abay:'#1565c0',turan:'#00838f',alfarabi:'#e53935',enbekshi:'#2e7d32'};
let activeFilters=new Set();

function toggleFilter(type,el){
  if(activeFilters.has(type)){activeFilters.delete(type);el.classList.remove('active');}
  else{activeFilters.add(type);el.classList.add('active');}
  renderFeed(activeDistrict);
}
function filterIncidents(query){renderFeed(activeDistrict,query);}

function renderFeed(districtId,query=''){
  let list=districtId?allIncidents.filter(i=>i.district===districtId):[...allIncidents];
  if(activeFilters.size>0)list=list.filter(i=>activeFilters.has(i.type));
  const q=(query||'').toLowerCase();
  if(q)list=list.filter(i=>i.loc.toLowerCase().includes(q)||i.type.toLowerCase().includes(q));
  if(!list.length){
    document.getElementById('incident-feed').innerHTML=`<div style="padding:28px 14px;text-align:center;color:var(--text-muted)"><div style="font-size:32px;margin-bottom:9px">📋</div><div style="font-size:12px;font-weight:600;margin-bottom:5px">Оқиғалар жоқ</div><div style="font-size:10px;line-height:1.6">📍 <strong>Белгілеу</strong> немесе<br>🤖 <strong>Авто</strong> режимін қосыңыз</div></div>`;
    return;
  }
  document.getElementById('incident-feed').innerHTML=list.slice(0,100).map(i=>`
    <div class="inc-item sev-${i.sev}" onclick="${i.lat?`map.setView([${i.lat},${i.lng}],17)`:''}" style="${i.lat?'cursor:pointer':''}">
      <div class="inc-type ${i.sev}">${i.type}${i.source==='auto'?'<span class="inc-auto-badge">авто</span>':''}</div>
      <div class="inc-loc">📍 ${i.loc}</div>
      <div class="inc-time">🕐 ${i.time}${!districtId&&districtColors[i.district]?`<span class="inc-district" style="background:${districtColors[i.district]}22;color:${districtColors[i.district]}">${districtData[i.district]?.name||''}</span>`:''}</div>
      ${i.id?`<button class="inc-delete" onclick="event.stopPropagation();deleteIncident('${i.id}',this)">🗑</button>`:''}
    </div>`).join('');
}

function renderUnits(districtId){
  const list=districtId?carRoutes.filter(r=>r.district===districtId):carRoutes;
  document.getElementById('units-list').innerHTML=list.map(u=>`<div class="unit-row"><div style="font-size:14px">🚔</div><div class="unit-info"><div class="unit-name">${u.name}</div><div class="unit-street">${u.street}</div></div><div class="badge badge-patrol">ПАТРУЛЬ</div></div>`).join('')||`<div style="padding:9px 0;font-size:10px;color:var(--text-muted)">Патруль жоқ</div>`;
}

// ============ STATS CHARTS ============
const days=['Дс','Сс','Ср','Бс','Жм','Сб','Жк'];
function renderWeekChart(id,data,color){
  const max=Math.max(...data);
  document.getElementById(id).innerHTML=data.map((v,i)=>`<div class="chart-bar-wrap"><div class="chart-bar" style="height:${(v/max)*46}px;background:${color};opacity:.8"></div><div class="chart-lbl">${days[i]}</div></div>`).join('');
}

function renderDistrictBar(elId,field){
  const dists=Object.entries(districtData).sort((a,b)=>b[1][field]-a[1][field]);
  const max=dists[0][1][field];
  document.getElementById(elId).innerHTML=dists.map(([id,d])=>`<div style="margin-bottom:6px"><div style="display:flex;justify-content:space-between;margin-bottom:2px"><span style="font-size:10px;color:var(--text-secondary)">${d.name.replace(' ауданы','')}</span><span style="font-size:10px;font-weight:700;color:${d.color};font-family:'JetBrains Mono',monospace">${d[field]}</span></div><div style="height:4px;background:var(--bg-tertiary);border-radius:3px"><div style="height:100%;width:${Math.round(d[field]/max*100)}%;background:${d.color};border-radius:3px;transition:width .6s"></div></div></div>`).join('');
}

function renderHourChart(){
  const h=DB.getStats().byHour;const max=Math.max(...h,1);
  document.getElementById('chart-hours').innerHTML=h.map((v,i)=>`<div class="h-bar-w"><div class="h-bar" style="height:${(v/max)*44}px;background:${v===Math.max(...h)?'#e53935':'#1565c0'};opacity:.75"></div><div class="h-lbl">${i%4===0?i:''}</div></div>`).join('');
}

function renderRanking(){
  const dists=Object.entries(districtData).sort((a,b)=>b[1].total-a[1].total);
  const max=dists[0][1].total;
  document.getElementById('district-ranking').innerHTML=dists.map(([id,d])=>`<div style="margin-bottom:7px"><div style="display:flex;justify-content:space-between;margin-bottom:2px"><span style="font-size:10px;color:var(--text-secondary)">${d.name.replace(' ауданы','')}</span><span style="font-size:10px;font-weight:700;color:${d.color};font-family:'JetBrains Mono',monospace">${d.total}</span></div><div style="height:4px;background:var(--bg-tertiary);border-radius:3px"><div style="height:100%;width:${Math.round(d.total/max*100)}%;background:${d.color};border-radius:3px;transition:width .6s"></div></div></div>`).join('');
}

// ============ ANALYTICS MODAL ============
function openAnalytics(){
  document.getElementById('analytics-overlay').classList.add('show');
  renderAnalyticsBars();renderAnalyticsTopCrimes();
  setTimeout(renderRadarChart,100);
}
function closeAnalytics(){document.getElementById('analytics-overlay').classList.remove('show');}
document.getElementById('analytics-overlay').addEventListener('click',function(e){if(e.target===this)closeAnalytics();});

function renderAnalyticsBars(){
  const dists=Object.entries(districtData).sort((a,b)=>b[1].total-a[1].total);
  const max=dists[0][1].total;
  document.getElementById('analytics-bars').innerHTML=dists.map(([id,d])=>`
    <div class="a-bar-row">
      <div class="a-bar-label" style="color:${d.color}">${d.name.replace(' ауданы','')}</div>
      <div class="a-bar-bg"><div class="a-bar-fill" style="width:${Math.round(d.total/max*100)}%;background:${d.color};height:100%"></div></div>
      <div class="a-bar-val" style="color:${d.color}">${d.total}</div>
    </div>`).join('');
}

function renderAnalyticsTopCrimes(){
  const crimes=[['ст.190 Алаяқтық',799,'#fb8c00'],['ст.188 Ұрлық',393,'#e53935'],['ст.109-1 Денсаулыққа зиян',239,'#f9a825'],['ст.296 Бұзақылық',130,'#8e24aa'],['ст.108-1 Зорлық',99,'#0288d1'],['ст.345 Қарсылық',59,'#6d4c41'],['ст.107 Дене жарақаты',56,'#c62828'],['ст.293 Тонау',37,'#e65100'],['ст.139 Кісі өлтіру',36,'#b71c1c']];
  const max=crimes[0][1];
  document.getElementById('analytics-top-crimes').innerHTML=crimes.map(([name,val,color])=>`
    <div class="a-bar-row">
      <div class="a-bar-label" style="color:${color};font-size:10px;width:130px">${name}</div>
      <div class="a-bar-bg"><div class="a-bar-fill" style="width:${Math.round(val/max*100)}%;background:${color};height:100%"></div></div>
      <div class="a-bar-val" style="color:${color}">${val}</div>
    </div>`).join('');
}

function renderRadarChart(){
  const canvas=document.getElementById('radar-canvas');if(!canvas)return;
  const ctx=canvas.getContext('2d');
  const W=400,H=220,cx=W/2,cy=H/2,R=80;
  ctx.clearRect(0,0,W,H);
  const districts=Object.values(districtData);
  const axes=[{label:'ст.190',key:'st190',max:204},{label:'ст.188',key:'st188',max:120},{label:'ст.109-1',key:'st1091',max:71},{label:'ст.296',key:'st296',max:44},{label:'ст.108-1',key:'st1081',max:31}];
  const N=axes.length;
  const isDark=document.documentElement.getAttribute('data-theme')==='dark';
  const gridColor=isDark?'rgba(255,255,255,0.1)':'rgba(0,0,0,0.1)';
  const textColor=isDark?'#a0adb8':'#4a5568';
  for(let r=0.25;r<=1;r+=0.25){
    ctx.beginPath();
    for(let i=0;i<=N;i++){const angle=(i/N)*Math.PI*2-Math.PI/2;const x=cx+Math.cos(angle)*R*r;const y=cy+Math.sin(angle)*R*r;if(i===0)ctx.moveTo(x,y);else ctx.lineTo(x,y);}
    ctx.closePath();ctx.strokeStyle=gridColor;ctx.lineWidth=1;ctx.stroke();
  }
  for(let i=0;i<N;i++){
    const angle=(i/N)*Math.PI*2-Math.PI/2;
    ctx.beginPath();ctx.moveTo(cx,cy);ctx.lineTo(cx+Math.cos(angle)*R,cy+Math.sin(angle)*R);
    ctx.strokeStyle=gridColor;ctx.lineWidth=1;ctx.stroke();
    ctx.fillStyle=textColor;ctx.font='bold 10px Rubik';ctx.textAlign='center';
    ctx.fillText(axes[i].label,cx+Math.cos(angle)*(R+18),cy+Math.sin(angle)*(R+18)+4);
  }
  districts.forEach(d=>{
    ctx.beginPath();
    axes.forEach((axis,i)=>{
      const val=(d[axis.key]||0)/axis.max;
      const angle=(i/N)*Math.PI*2-Math.PI/2;
      const x=cx+Math.cos(angle)*R*val;const y=cy+Math.sin(angle)*R*val;
      if(i===0)ctx.moveTo(x,y);else ctx.lineTo(x,y);
    });
    ctx.closePath();ctx.fillStyle=d.color+'44';ctx.fill();ctx.strokeStyle=d.color;ctx.lineWidth=1.5;ctx.stroke();
  });
  let lx=10;
  districts.forEach(d=>{
    ctx.fillStyle=d.color;ctx.fillRect(lx,H-18,10,10);
    ctx.fillStyle=textColor;ctx.font='9px Rubik';ctx.textAlign='left';
    ctx.fillText(d.name.replace(' ауданы',''),lx+13,H-10);
    lx+=ctx.measureText(d.name.replace(' ауданы','')).width+28;
  });
}

// ============ TOAST ============
function showToast(type,color,loc){
  document.getElementById('toast-type').textContent=type;
  document.getElementById('toast').style.borderLeftColor=color;
  document.getElementById('toast-type').style.color=color;
  document.getElementById('toast-loc').textContent=loc;
  const t=document.getElementById('toast');t.classList.add('show');setTimeout(()=>t.classList.remove('show'),4000);
}

// ============ EXPORT ============
function exportCSV(){
  const incs=DB.getIncidents();
  if(!incs.length){alert('База бос — алдымен оқиға қосыңыз');return;}
  const h='ID,Бап,Мекенжай,Аудан,Маңыздылық,Уақыт,Дата,Lat,Lng,Кез\n';
  const rows=incs.map(i=>`${i.id},"${i.type}","${i.loc}","${i.district}",${i.sev},${i.time||''},${(i.created||'').slice(0,10)},${i.lat||''},${i.lng||''},${i.source||'manual'}`).join('\n');
  const blob=new Blob(['\ufeff'+h+rows],{type:'text/csv;charset=utf-8'});
  const url=URL.createObjectURL(blob);
  const a=document.createElement('a');a.href=url;a.download='shymkent_v7_'+new Date().toISOString().slice(0,10)+'.csv';a.click();
  URL.revokeObjectURL(url);
}

function clearDB(){
  if(confirm('Барлық сақталған деректерді өшіру керек пе?')){
    DB.clearIncidents();
    while(allIncidents.length)allIncidents.pop();
    layers.crimes=layers.crimes.filter(m=>{if(m._incidentId){map.removeLayer(m);return false;}return true;});
    DB.updateDBInfo();renderFeed(activeDistrict);renderHourChart();
  }
}

function selectDistrict(id){if(!id){resetFocus();return;}focusDistrict(id);switchTab('district',document.querySelectorAll('.tab-btn')[3]);}
function zoomToSelected(){const id=document.getElementById('region-select').value;if(!id){resetFocus();return;}focusDistrict(id);}

function switchTab(name,btn){
  document.querySelectorAll('.tab-btn').forEach(b=>b.classList.remove('active'));
  document.querySelectorAll('.tab-content').forEach(c=>c.classList.remove('active'));
  if(btn)btn.classList.add('active');
  document.getElementById('tab-'+name).classList.add('active');
  if(name==='stats'){
    renderWeekChart('chart-dtp',[12,8,15,9,11,7,14],'#fb8c00');
    renderWeekChart('chart-crime',[28,22,35,18,31,25,38],'#e53935');
    renderHourChart();renderRanking();
    renderDistrictBar('district-st190','st190');renderDistrictBar('district-st188','st188');
  }
  if(name==='buildings')renderBuildingsTab();
}

function tick(){
  const n=new Date();
  document.getElementById('clock').textContent=`${n.getHours().toString().padStart(2,'0')}:${n.getMinutes().toString().padStart(2,'0')}:${n.getSeconds().toString().padStart(2,'0')} · ${n.toLocaleDateString('kk-KZ')}`;
}
setInterval(tick,1000);tick();

// ============ INIT ============
loadSavedCameras();
loadSavedBuildings();
renderFeed(null);
renderUnits(null);
DB.updateDBInfo();
loadOSMBoundaries();
renderDistrictBar('district-st190','st190');
renderDistrictBar('district-st188','st188');
renderHourChart();
renderRanking();
</script>

</body></html>
