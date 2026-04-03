<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>MediHome — Family Medicine Manager</title>
<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;500;600;700;800;900&family=Sora:wght@300;400;600;700&display=swap" rel="stylesheet">
<style>
:root {
  --teal: #0D9488;
  --teal-light: #CCFBF1;
  --teal-dark: #0F766E;
  --blue: #3B82F6;
  --blue-light: #DBEAFE;
  --orange: #F97316;
  --orange-light: #FFEDD5;
  --red: #EF4444;
  --red-light: #FEE2E2;
  --green: #22C55E;
  --green-light: #DCFCE7;
  --yellow: #EAB308;
  --yellow-light: #FEF9C3;
  --bg: #F0FDFA;
  --surface: #FFFFFF;
  --surface2: #F8FFFE;
  --border: #CCFBF1;
  --border2: #E5E7EB;
  --text: #134E4A;
  --text2: #6B7280;
  --radius: 18px;
  --radius-sm: 10px;
  --shadow: 0 4px 24px rgba(13,148,136,0.10);
  --shadow-lg: 0 8px 40px rgba(13,148,136,0.18);
}

* { margin: 0; padding: 0; box-sizing: border-box; }

body {
  font-family: 'Nunito', sans-serif;
  background: var(--bg);
  color: var(--text);
  min-height: 100vh;
  overflow-x: hidden;
}

/* ===== SIDEBAR ===== */
.layout { display: flex; min-height: 100vh; }

.sidebar {
  width: 76px;
  background: linear-gradient(180deg, #0F766E 0%, #0D9488 60%, #14B8A6 100%);
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px 0 28px;
  position: fixed;
  top: 0; left: 0; bottom: 0;
  z-index: 200;
  box-shadow: 4px 0 24px rgba(13,148,136,0.18);
  gap: 6px;
}

.sidebar-logo {
  width: 52px; height: 52px;
  background: white;
  border-radius: 16px;
  display: flex; align-items: center; justify-content: center;
  margin-bottom: 18px;
  box-shadow: 0 4px 16px rgba(0,0,0,0.12);
  flex-shrink: 0;
}

/* SVG LOGO */
.logo-svg { width: 38px; height: 38px; }

.nav-btn {
  width: 52px; height: 52px;
  border-radius: 14px;
  border: none;
  background: rgba(255,255,255,0.12);
  color: rgba(255,255,255,0.7);
  cursor: pointer;
  display: flex; flex-direction: column;
  align-items: center; justify-content: center;
  gap: 3px;
  font-size: 22px;
  transition: all 0.22s;
  position: relative;
}
.nav-btn .nav-label {
  font-size: 8px;
  font-family: 'Nunito', sans-serif;
  font-weight: 700;
  letter-spacing: 0.03em;
  color: rgba(255,255,255,0.6);
}
.nav-btn:hover { background: rgba(255,255,255,0.2); color: #fff; transform: scale(1.07); }
.nav-btn.active { background: white; color: var(--teal); box-shadow: 0 4px 14px rgba(0,0,0,0.15); }
.nav-btn.active .nav-label { color: var(--teal); }

.sidebar-spacer { flex: 1; }

/* ===== MAIN ===== */
.main {
  margin-left: 76px;
  flex: 1;
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

/* TOP BAR */
.topbar {
  background: white;
  border-bottom: 1.5px solid var(--border);
  padding: 0 32px;
  height: 64px;
  display: flex; align-items: center; justify-content: space-between;
  position: sticky; top: 0; z-index: 100;
  box-shadow: 0 2px 12px rgba(13,148,136,0.06);
}
.topbar-title {
  font-family: 'Sora', sans-serif;
  font-size: 20px;
  font-weight: 700;
  color: var(--text);
}
.topbar-sub { font-size: 13px; color: var(--text2); font-weight: 400; }
.topbar-right { display: flex; align-items: center; gap: 12px; }
.alert-badge {
  background: var(--red);
  color: white;
  border-radius: 20px;
  font-size: 12px;
  font-weight: 800;
  padding: 3px 9px;
  animation: pulse 2s infinite;
}
@keyframes pulse { 0%,100%{opacity:1} 50%{opacity:0.7} }

/* ===== CONTENT ===== */
.content { padding: 28px 32px; flex: 1; }

.page { display: none; animation: pageIn 0.35s cubic-bezier(0.22,1,0.36,1); }
.page.active { display: block; }
@keyframes pageIn { from{ opacity:0; transform:translateY(14px); } to{ opacity:1; transform:translateY(0); } }

/* ===== STAT CARDS ===== */
.stats-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 16px;
  margin-bottom: 24px;
}
.stat-card {
  background: white;
  border-radius: var(--radius);
  padding: 20px 22px;
  border: 1.5px solid var(--border);
  box-shadow: var(--shadow);
  display: flex; align-items: center; gap: 16px;
  transition: transform 0.2s, box-shadow 0.2s;
  cursor: default;
}
.stat-card:hover { transform: translateY(-3px); box-shadow: var(--shadow-lg); }
.stat-icon-wrap {
  width: 52px; height: 52px;
  border-radius: 14px;
  display: flex; align-items: center; justify-content: center;
  font-size: 26px;
  flex-shrink: 0;
}
.stat-val { font-size: 28px; font-weight: 900; line-height: 1; }
.stat-label { font-size: 12px; color: var(--text2); font-weight: 600; margin-top: 3px; text-transform: uppercase; letter-spacing: 0.04em; }

/* ===== SECTION TITLE ===== */
.section-header {
  display: flex; align-items: center; justify-content: space-between;
  margin-bottom: 16px;
}
.section-title {
  font-family: 'Sora', sans-serif;
  font-size: 17px;
  font-weight: 700;
  color: var(--text);
  display: flex; align-items: center; gap: 8px;
}

/* ===== BUTTONS ===== */
.btn {
  display: inline-flex; align-items: center; gap: 7px;
  padding: 10px 20px;
  border-radius: 10px;
  border: none;
  cursor: pointer;
  font-family: 'Nunito', sans-serif;
  font-size: 14px;
  font-weight: 700;
  transition: all 0.2s;
  text-decoration: none;
}
.btn-primary { background: linear-gradient(135deg,var(--teal),var(--teal-dark)); color: white; box-shadow: 0 3px 12px rgba(13,148,136,0.3); }
.btn-primary:hover { transform: translateY(-2px); box-shadow: 0 6px 20px rgba(13,148,136,0.35); }
.btn-outline { background: white; border: 1.5px solid var(--border2); color: var(--text); }
.btn-outline:hover { border-color: var(--teal); color: var(--teal); }
.btn-orange { background: linear-gradient(135deg,#F97316,#EA580C); color: white; box-shadow: 0 3px 12px rgba(249,115,22,0.3); }
.btn-orange:hover { transform: translateY(-2px); box-shadow: 0 6px 20px rgba(249,115,22,0.4); }
.btn-blue { background: linear-gradient(135deg,#3B82F6,#2563EB); color: white; box-shadow: 0 3px 12px rgba(59,130,246,0.3); }
.btn-blue:hover { transform: translateY(-2px); box-shadow: 0 6px 20px rgba(59,130,246,0.4); }
.btn-red { background: linear-gradient(135deg,#EF4444,#DC2626); color: white; }
.btn-sm { padding: 6px 14px; font-size: 13px; border-radius: 8px; }
.btn-xs { padding: 4px 10px; font-size: 12px; border-radius: 6px; }
.btn-icon { width: 36px; height: 36px; padding: 0; justify-content: center; border-radius: 9px; font-size: 16px; }

/* ===== CARDS ===== */
.card {
  background: white;
  border-radius: var(--radius);
  border: 1.5px solid var(--border);
  box-shadow: var(--shadow);
  padding: 22px 24px;
  margin-bottom: 18px;
}
.card-title {
  font-family: 'Sora', sans-serif;
  font-size: 16px;
  font-weight: 700;
  margin-bottom: 16px;
  display: flex; align-items: center; gap: 8px;
}

/* ===== TABLE ===== */
.table-wrap { overflow-x: auto; }
table { width: 100%; border-collapse: collapse; }
th {
  text-align: left;
  font-size: 11px;
  font-weight: 800;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: var(--text2);
  padding: 8px 14px;
  border-bottom: 2px solid var(--border);
}
td {
  padding: 13px 14px;
  font-size: 14px;
  border-bottom: 1px solid #F3FFFE;
  vertical-align: middle;
}
tr:last-child td { border-bottom: none; }
tr:hover td { background: #F0FDFA; }

/* ===== BADGES ===== */
.badge {
  display: inline-flex; align-items: center; gap: 4px;
  padding: 3px 10px;
  border-radius: 20px;
  font-size: 12px;
  font-weight: 700;
}
.badge-teal { background: var(--teal-light); color: var(--teal-dark); }
.badge-orange { background: var(--orange-light); color: #C2410C; }
.badge-red { background: var(--red-light); color: #B91C1C; }
.badge-green { background: var(--green-light); color: #15803D; }
.badge-blue { background: var(--blue-light); color: #1D4ED8; }
.badge-gray { background: #F3F4F6; color: var(--text2); }
.badge-yellow { background: var(--yellow-light); color: #92400E; }

/* ===== REMINDER ITEM ===== */
.reminder-item {
  display: flex; align-items: center; gap: 14px;
  padding: 14px 0;
  border-bottom: 1px solid #F0FDFA;
}
.reminder-item:last-child { border-bottom: none; }
.time-pill {
  background: linear-gradient(135deg,var(--teal),var(--teal-dark));
  color: white;
  border-radius: 10px;
  padding: 8px 13px;
  font-size: 13px;
  font-weight: 800;
  min-width: 72px;
  text-align: center;
  box-shadow: 0 2px 8px rgba(13,148,136,0.25);
  flex-shrink: 0;
}
.time-pill.done { background: #E5E7EB; color: var(--text2); box-shadow: none; }
.rem-info { flex: 1; }
.rem-name { font-weight: 700; font-size: 15px; }
.rem-meta { color: var(--text2); font-size: 13px; margin-top: 2px; }
.check-btn {
  width: 32px; height: 32px;
  border-radius: 50%;
  border: 2px solid var(--border2);
  background: none; cursor: pointer;
  display: flex; align-items: center; justify-content: center;
  font-size: 15px; transition: all 0.2s;
}
.check-btn.done { background: var(--green); border-color: var(--green); color: white; }
.check-btn:hover:not(.done) { border-color: var(--teal); }

/* ===== PHARMACY SECTION ===== */
.pharmacy-tabs {
  display: flex;
  background: #F0FDFA;
  border-radius: 12px;
  padding: 4px;
  gap: 4px;
  margin-bottom: 20px;
  border: 1.5px solid var(--border);
  width: fit-content;
}
.ph-tab {
  padding: 9px 22px;
  border-radius: 9px;
  border: none;
  cursor: pointer;
  font-family: 'Nunito', sans-serif;
  font-size: 14px;
  font-weight: 700;
  background: none;
  color: var(--text2);
  transition: all 0.2s;
  display: flex; align-items: center; gap: 7px;
}
.ph-tab.active { background: white; color: var(--teal); box-shadow: 0 2px 8px rgba(13,148,136,0.12); }

.pharmacy-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 16px;
}
.pharmacy-card {
  background: white;
  border-radius: var(--radius);
  border: 1.5px solid var(--border);
  padding: 18px 20px;
  box-shadow: var(--shadow);
  transition: all 0.22s;
}
.pharmacy-card:hover { transform: translateY(-3px); box-shadow: var(--shadow-lg); border-color: var(--teal); }
.ph-header { display: flex; align-items: flex-start; gap: 14px; margin-bottom: 12px; }
.ph-icon {
  width: 48px; height: 48px;
  border-radius: 13px;
  display: flex; align-items: center; justify-content: center;
  font-size: 24px;
  flex-shrink: 0;
}
.ph-name { font-weight: 800; font-size: 15px; }
.ph-dist { font-size: 12px; color: var(--text2); margin-top: 2px; }
.ph-rating { font-size: 12px; color: var(--yellow); font-weight: 700; }
.ph-meds { display: flex; flex-wrap: wrap; gap: 6px; margin-bottom: 12px; }
.ph-actions { display: flex; gap: 8px; }

/* Online pharmacy */
.online-pharmacy-card {
  background: linear-gradient(135deg, #EFF6FF, #DBEAFE);
  border: 1.5px solid #BFDBFE;
  border-radius: var(--radius);
  padding: 18px 20px;
  transition: all 0.22s;
}
.online-pharmacy-card:hover { transform: translateY(-3px); box-shadow: 0 8px 30px rgba(59,130,246,0.15); }

/* LOW STOCK ALERT PANEL */
.low-stock-alert {
  background: linear-gradient(135deg, #FFFBEB, #FEF3C7);
  border: 2px solid #FCD34D;
  border-radius: var(--radius);
  padding: 18px 22px;
  margin-bottom: 18px;
  display: flex; align-items: flex-start; gap: 14px;
}
.alert-icon { font-size: 28px; flex-shrink: 0; }
.alert-body { flex: 1; }
.alert-title { font-weight: 800; font-size: 15px; color: #92400E; margin-bottom: 4px; }
.alert-desc { font-size: 13px; color: #78350F; }
.alert-meds { display: flex; flex-wrap: wrap; gap: 6px; margin-top: 10px; }

/* MEMBER CARD */
.member-card {
  background: white;
  border: 1.5px solid var(--border);
  border-radius: var(--radius);
  padding: 20px;
  box-shadow: var(--shadow);
  transition: all 0.2s;
}
.member-card:hover { transform: translateY(-2px); box-shadow: var(--shadow-lg); }
.member-avatar {
  width: 48px; height: 48px; border-radius: 14px;
  display: flex; align-items: center; justify-content: center;
  font-size: 22px; font-weight: 900; color: white;
  flex-shrink: 0;
}
.members-grid { display: grid; grid-template-columns: repeat(3,1fr); gap: 16px; }

/* STOCK BAR */
.stock-bar-row { display: flex; align-items: center; gap: 10px; }
.stock-bar { flex: 1; height: 8px; border-radius: 8px; background: #F3F4F6; overflow: hidden; }
.stock-fill { height: 100%; border-radius: 8px; transition: width 0.7s cubic-bezier(0.22,1,0.36,1); }
.stock-pct { font-size: 12px; font-weight: 700; color: var(--text2); min-width: 38px; text-align: right; }

/* MODAL */
.overlay {
  display: none; position: fixed; inset: 0;
  background: rgba(13,78,74,0.35);
  z-index: 999; align-items: center; justify-content: center;
  backdrop-filter: blur(6px);
}
.overlay.open { display: flex; }
.modal {
  background: white;
  border-radius: 22px;
  padding: 32px;
  width: 500px; max-width: 96vw;
  box-shadow: 0 24px 64px rgba(13,148,136,0.2);
  animation: modalIn 0.32s cubic-bezier(0.34,1.56,0.64,1);
  max-height: 90vh; overflow-y: auto;
}
@keyframes modalIn { from{opacity:0;transform:scale(0.88)} to{opacity:1;transform:scale(1)} }
.modal-title { font-family:'Sora',sans-serif; font-size:20px; font-weight:700; margin-bottom:22px; display:flex;align-items:center;gap:10px; }
.modal-footer { display:flex;gap:10px;justify-content:flex-end;margin-top:22px; }

/* FORM */
.form-row { display:grid;grid-template-columns:1fr 1fr;gap:14px;margin-bottom:14px; }
.form-group { display:flex;flex-direction:column;gap:6px;margin-bottom:14px; }
.form-group:last-child{margin-bottom:0}
label { font-size:12px;font-weight:800;color:var(--text2);text-transform:uppercase;letter-spacing:0.05em; }
input,select,textarea {
  padding:11px 14px;
  border:1.5px solid var(--border2);
  border-radius:10px;
  font-family:'Nunito',sans-serif;
  font-size:14px; font-weight:600;
  color:var(--text);
  background:#FAFAFA;
  outline:none; transition:border 0.2s,background 0.2s;
}
input:focus,select:focus,textarea:focus { border-color:var(--teal); background:white; }

/* GRID 2 */
.grid2{display:grid;grid-template-columns:1fr 1fr;gap:18px;}

/* TOAST */
.toast {
  position:fixed; bottom:28px; right:28px;
  background: linear-gradient(135deg,var(--teal-dark),var(--teal));
  color:white; padding:13px 20px;
  border-radius:12px; font-size:14px; font-weight:700;
  z-index:9999; display:none;align-items:center;gap:9px;
  box-shadow:0 8px 28px rgba(13,148,136,0.3);
  animation:slideUp 0.3s ease;
}
@keyframes slideUp{from{transform:translateY(20px);opacity:0}to{transform:translateY(0);opacity:1}}
.toast.show{display:flex}

/* EMPTY */
.empty{text-align:center;padding:40px 20px;color:var(--text2);}
.empty-icon{font-size:48px;margin-bottom:12px}
.empty-text{font-size:15px;font-weight:600}

/* SEARCH */
.search-bar {
  display:flex;align-items:center;gap:10px;
  background:white;border:1.5px solid var(--border2);
  border-radius:10px;padding:9px 14px;
  font-family:'Nunito',sans-serif;font-size:14px;
  margin-bottom:16px; width:100%;
}
.search-bar input { border:none;background:none;outline:none;flex:1;font-size:14px;font-weight:600;color:var(--text); }

/* EXPIRY warning */
.expiry-warn { color: #C2410C; font-weight:700; }

/* ORDER MODAL special */
.order-medicine-list { display:flex;flex-direction:column;gap:10px;margin-bottom:16px; }
.order-med-row {
  display:flex;align-items:center;gap:12px;
  background:#F0FDFA;border-radius:10px;padding:12px 14px;
  border:1.5px solid var(--border);
}
.order-med-row input[type=number]{width:70px;padding:6px 10px;}
.order-platform {
  display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:16px;
}
.platform-btn {
  border:2px solid var(--border2);border-radius:12px;
  padding:14px;text-align:center;cursor:pointer;
  transition:all 0.2s;background:white;
}
.platform-btn:hover,.platform-btn.selected { border-color:var(--teal);background:var(--teal-light); }
.platform-name{font-weight:800;font-size:14px;margin-top:6px;}
.platform-eta{font-size:12px;color:var(--text2);}

/* DIRECTIONS button */
.dir-btn{
  display:inline-flex;align-items:center;gap:6px;
  padding:7px 14px;border-radius:8px;font-size:12px;font-weight:700;
  background:#EFF6FF;color:#1D4ED8;border:1.5px solid #BFDBFE;
  cursor:pointer;transition:all 0.2s;text-decoration:none;
}
.dir-btn:hover{background:#DBEAFE;}

/* CALL btn */
.call-btn{
  display:inline-flex;align-items:center;gap:6px;
  padding:7px 14px;border-radius:8px;font-size:12px;font-weight:700;
  background:#F0FDF4;color:#15803D;border:1.5px solid #BBF7D0;
  cursor:pointer;transition:all 0.2s;text-decoration:none;
}
.call-btn:hover{background:#DCFCE7;}

/* OPEN status */
.open-status{
  font-size:12px;font-weight:700;
  display:flex;align-items:center;gap:4px;
}
.open-dot{width:8px;height:8px;border-radius:50%;flex-shrink:0;}

/* ===== RESPONSIVE ===== */
@media(max-width:900px){
  .stats-grid{grid-template-columns:1fr 1fr;}
  .pharmacy-grid{grid-template-columns:1fr;}
  .members-grid{grid-template-columns:1fr 1fr;}
  .grid2{grid-template-columns:1fr;}
  .content{padding:18px 14px;}
  .topbar{padding:0 16px;}
}
@media(max-width:600px){
  .stats-grid{grid-template-columns:1fr 1fr;}
  .members-grid{grid-template-columns:1fr;}
  .form-row{grid-template-columns:1fr;}
}
</style>
</head>
<body>
<div class="layout">

<!-- SIDEBAR -->
<nav class="sidebar">
  <!-- APP LOGO (SVG) -->
  <div class="sidebar-logo">
    <svg class="logo-svg" viewBox="0 0 38 38" fill="none" xmlns="http://www.w3.org/2000/svg">
      <!-- House shape -->
      <path d="M19 5L4 16V34H34V16L19 5Z" fill="#0D9488" opacity="0.12"/>
      <path d="M19 5L4 16V34H34V16L19 5Z" stroke="#0D9488" stroke-width="2" stroke-linejoin="round"/>
      <!-- Cross/plus for medicine -->
      <rect x="15.5" y="19" width="7" height="2.5" rx="1.25" fill="#0D9488"/>
      <rect x="17.75" y="16.75" width="2.5" height="7" rx="1.25" fill="#0D9488"/>
      <!-- Small heart -->
      <path d="M19 13.5C19 13.5 16 11 14.5 12.5C13.2 13.8 14.5 15.5 19 17.5C23.5 15.5 24.8 13.8 23.5 12.5C22 11 19 13.5 19 13.5Z" fill="#EF4444" opacity="0.8"/>
    </svg>
  </div>

  <button class="nav-btn active" onclick="switchPage('dashboard',this)" title="Dashboard">
    🏠<span class="nav-label">HOME</span>
  </button>
  <button class="nav-btn" onclick="switchPage('medicines',this)" title="Medicines">
    💊<span class="nav-label">MEDS</span>
  </button>
  <button class="nav-btn" onclick="switchPage('reminders',this)" title="Reminders">
    🔔<span class="nav-label">ALERTS</span>
  </button>
  <button class="nav-btn" onclick="switchPage('pharmacy',this)" title="Find Pharmacy">
    🏥<span class="nav-label">PHARMA</span>
  </button>
  <button class="nav-btn" onclick="switchPage('inventory',this)" title="Inventory">
    📦<span class="nav-label">STOCK</span>
  </button>
  <button class="nav-btn" onclick="switchPage('members',this)" title="Family">
    👨‍👩‍👧<span class="nav-label">FAMILY</span>
  </button>
</nav>

<!-- MAIN -->
<div class="main">

  <!-- TOP BAR -->
  <div class="topbar">
    <div>
      <div class="topbar-title" id="topbar-title">Dashboard</div>
      <div class="topbar-sub" id="topbar-sub">Your family health at a glance</div>
    </div>
    <div class="topbar-right">
      <div class="alert-badge" id="low-stock-badge" style="display:none">⚠️ Low Stock</div>
      <button class="btn btn-primary btn-sm" id="topbar-action" onclick="openModal('modal-add-medicine')">+ Add Medicine</button>
    </div>
  </div>

  <!-- CONTENT -->
  <div class="content">

    <!-- ===== DASHBOARD ===== -->
    <div class="page active" id="page-dashboard">

      <!-- Low stock banner -->
      <div class="low-stock-alert" id="low-stock-banner" style="display:none">
        <div class="alert-icon">⚠️</div>
        <div class="alert-body">
          <div class="alert-title">Medicines Running Low — Order Now!</div>
          <div class="alert-desc">The following medicines need to be restocked. Find a nearby pharmacy or order online.</div>
          <div class="alert-meds" id="low-stock-meds-list"></div>
          <div style="display:flex;gap:10px;margin-top:12px;flex-wrap:wrap;">
            <button class="btn btn-orange btn-sm" onclick="switchPage('pharmacy',document.querySelectorAll('.nav-btn')[3]);setPhTab('online')">🛒 Order Online</button>
            <button class="btn btn-blue btn-sm" onclick="switchPage('pharmacy',document.querySelectorAll('.nav-btn')[3]);setPhTab('offline')">📍 Nearby Pharmacies</button>
          </div>
        </div>
      </div>

      <div class="stats-grid">
        <div class="stat-card">
          <div class="stat-icon-wrap" style="background:var(--teal-light)">💊</div>
          <div><div class="stat-val" style="color:var(--teal)" id="s-total">0</div><div class="stat-label">Total Medicines</div></div>
        </div>
        <div class="stat-card">
          <div class="stat-icon-wrap" style="background:var(--orange-light)">⚠️</div>
          <div><div class="stat-val" style="color:var(--orange)" id="s-low">0</div><div class="stat-label">Low Stock</div></div>
        </div>
        <div class="stat-card">
          <div class="stat-icon-wrap" style="background:var(--blue-light)">🔔</div>
          <div><div class="stat-val" style="color:var(--blue)" id="s-rem">0</div><div class="stat-label">Today's Doses</div></div>
        </div>
        <div class="stat-card">
          <div class="stat-icon-wrap" style="background:var(--green-light)">👨‍👩‍👧</div>
          <div><div class="stat-val" style="color:var(--green)" id="s-mem">0</div><div class="stat-label">Family Members</div></div>
        </div>
      </div>

      <div class="grid2">
        <div class="card">
          <div class="card-title">🔔 Today's Schedule</div>
          <div id="dash-reminders"></div>
        </div>
        <div class="card">
          <div class="card-title">📦 Stock Overview</div>
          <div id="dash-stock"></div>
        </div>
      </div>
    </div>

    <!-- ===== MEDICINES ===== -->
    <div class="page" id="page-medicines">
      <div class="section-header">
        <div class="section-title">💊 All Medicines</div>
        <button class="btn btn-primary" onclick="openModal('modal-add-medicine')">+ Add Medicine</button>
      </div>
      <div class="card" style="padding:0;overflow:hidden;">
        <div class="table-wrap">
          <table>
            <thead><tr>
              <th>Medicine</th><th>Type</th><th>Dosage</th><th>Member</th>
              <th>Expiry</th><th>Stock</th><th>Actions</th>
            </tr></thead>
            <tbody id="med-tbody"></tbody>
          </table>
        </div>
      </div>
    </div>

    <!-- ===== REMINDERS ===== -->
    <div class="page" id="page-reminders">
      <div class="section-header">
        <div class="section-title">🔔 Medication Reminders</div>
        <button class="btn btn-primary" onclick="openModal('modal-add-reminder')">+ Add Reminder</button>
      </div>
      <div class="card"><div id="rem-list"></div></div>
    </div>

    <!-- ===== PHARMACY ===== -->
    <div class="page" id="page-pharmacy">
      <div class="section-header">
        <div class="section-title">🏥 Find Pharmacy</div>
        <div id="ph-low-count"></div>
      </div>

      <!-- Tabs -->
      <div class="pharmacy-tabs">
        <button class="ph-tab active" id="tab-offline" onclick="setPhTab('offline')">📍 Nearby Pharmacies</button>
        <button class="ph-tab" id="tab-online" onclick="setPhTab('online')">🛒 Order Online</button>
      </div>

      <!-- OFFLINE -->
      <div id="ph-offline">
        <div style="background:linear-gradient(135deg,#F0FDFA,#CCFBF1);border:1.5px solid var(--border);border-radius:14px;padding:14px 18px;margin-bottom:18px;display:flex;align-items:center;gap:12px;">
          <span style="font-size:22px;">📍</span>
          <div>
            <div style="font-weight:800;font-size:14px;color:var(--teal-dark);">Showing pharmacies near you</div>
            <div style="font-size:12px;color:var(--text2);">Based on your location · Sorted by distance</div>
          </div>
          <button class="btn btn-outline btn-sm" style="margin-left:auto;" onclick="showToast('📍 Location refreshed!')">🔄 Refresh</button>
        </div>

        <div id="low-meds-for-pharmacy" style="margin-bottom:16px;"></div>

        <div class="pharmacy-grid" id="offline-pharmacies"></div>
      </div>

      <!-- ONLINE -->
      <div id="ph-online" style="display:none">
        <div style="background:linear-gradient(135deg,#EFF6FF,#DBEAFE);border:1.5px solid #BFDBFE;border-radius:14px;padding:14px 18px;margin-bottom:18px;display:flex;align-items:center;gap:12px;">
          <span style="font-size:22px;">🛒</span>
          <div>
            <div style="font-weight:800;font-size:14px;color:#1D4ED8;">Order medicines online & get home delivery</div>
            <div style="font-size:12px;color:var(--text2);">Fast delivery · Compare prices · Prescription upload</div>
          </div>
        </div>

        <div id="low-meds-for-online" style="margin-bottom:16px;"></div>

        <div class="pharmacy-grid" id="online-pharmacies"></div>
      </div>
    </div>

    <!-- ===== INVENTORY ===== -->
    <div class="page" id="page-inventory">
      <div class="section-header">
        <div class="section-title">📦 Stock Inventory</div>
      </div>
      <div class="card" style="padding:0;overflow:hidden;">
        <div class="table-wrap">
          <table>
            <thead><tr>
              <th>Medicine</th><th>Stock Level</th><th>Qty</th><th>Threshold</th><th>Status</th><th>Update</th>
            </tr></thead>
            <tbody id="inv-tbody"></tbody>
          </table>
        </div>
      </div>
    </div>

    <!-- ===== MEMBERS ===== -->
    <div class="page" id="page-members">
      <div class="section-header">
        <div class="section-title">👨‍👩‍👧 Family Members</div>
        <button class="btn btn-primary" onclick="openModal('modal-add-member')">+ Add Member</button>
      </div>
      <div class="members-grid" id="members-grid"></div>
    </div>

  </div><!-- /content -->
</div><!-- /main -->
</div><!-- /layout -->

<!-- ===== MODALS ===== -->

<!-- Add Medicine -->
<div class="overlay" id="modal-add-medicine">
  <div class="modal">
    <div class="modal-title">💊 Add Medicine</div>
    <div class="form-row">
      <div class="form-group"><label>Name *</label><input id="mn" placeholder="e.g. Paracetamol"></div>
      <div class="form-group"><label>Type</label>
        <select id="mt"><option>Tablet</option><option>Capsule</option><option>Syrup</option><option>Drops</option><option>Injection</option><option>Cream</option><option>Inhaler</option></select>
      </div>
    </div>
    <div class="form-row">
      <div class="form-group"><label>Dosage</label><input id="md" placeholder="e.g. 500mg"></div>
      <div class="form-group"><label>Quantity *</label><input id="mq" type="number" placeholder="30" min="0"></div>
    </div>
    <div class="form-row">
      <div class="form-group"><label>Min. Threshold</label><input id="mth" type="number" placeholder="5" min="0"></div>
      <div class="form-group"><label>Expiry Date</label><input id="me" type="date"></div>
    </div>
    <div class="form-group"><label>Assign to Member</label><select id="mm"><option value="">— Unassigned —</option></select></div>
    <div class="form-group"><label>Instructions</label><textarea id="mi" rows="2" placeholder="e.g. Take after meals"></textarea></div>
    <div class="modal-footer">
      <button class="btn btn-outline" onclick="closeModal('modal-add-medicine')">Cancel</button>
      <button class="btn btn-primary" onclick="addMedicine()">Add Medicine</button>
    </div>
  </div>
</div>

<!-- Add Reminder -->
<div class="overlay" id="modal-add-reminder">
  <div class="modal">
    <div class="modal-title">🔔 Add Reminder</div>
    <div class="form-group"><label>Medicine *</label><select id="rm"><option value="">— Select —</option></select></div>
    <div class="form-row">
      <div class="form-group"><label>Time *</label><input id="rt" type="time"></div>
      <div class="form-group"><label>Frequency</label>
        <select id="rf"><option>Daily</option><option>Twice daily</option><option>Three times daily</option><option>Weekly</option><option>As needed</option></select>
      </div>
    </div>
    <div class="form-group"><label>Notes</label><input id="rn" placeholder="e.g. With water"></div>
    <div class="modal-footer">
      <button class="btn btn-outline" onclick="closeModal('modal-add-reminder')">Cancel</button>
      <button class="btn btn-primary" onclick="addReminder()">Add Reminder</button>
    </div>
  </div>
</div>

<!-- Add Member -->
<div class="overlay" id="modal-add-member">
  <div class="modal">
    <div class="modal-title">👤 Add Family Member</div>
    <div class="form-row">
      <div class="form-group"><label>Name *</label><input id="emn" placeholder="e.g. Dad"></div>
      <div class="form-group"><label>Role</label>
        <select id="emr"><option>Parent</option><option>Child</option><option>Grandparent</option><option>Spouse</option><option>Other</option></select>
      </div>
    </div>
    <div class="form-row">
      <div class="form-group"><label>Age</label><input id="ema" type="number" placeholder="45" min="0"></div>
      <div class="form-group"><label>Blood Type</label>
        <select id="emb"><option value="">Unknown</option><option>A+</option><option>A-</option><option>B+</option><option>B-</option><option>AB+</option><option>AB-</option><option>O+</option><option>O-</option></select>
      </div>
    </div>
    <div class="form-group"><label>Allergies</label><input id="emal" placeholder="e.g. Penicillin (optional)"></div>
    <div class="modal-footer">
      <button class="btn btn-outline" onclick="closeModal('modal-add-member')">Cancel</button>
      <button class="btn btn-primary" onclick="addMember()">Add Member</button>
    </div>
  </div>
</div>

<!-- Update Stock -->
<div class="overlay" id="modal-stock">
  <div class="modal">
    <div class="modal-title">📦 Update Stock</div>
    <div class="form-group"><label>Medicine</label><input id="sk-name" readonly></div>
    <div class="form-row">
      <div class="form-group"><label>New Quantity</label><input id="sk-qty" type="number" min="0"></div>
      <div class="form-group"><label>Min. Threshold</label><input id="sk-thr" type="number" min="0"></div>
    </div>
    <div class="modal-footer">
      <button class="btn btn-outline" onclick="closeModal('modal-stock')">Cancel</button>
      <button class="btn btn-primary" onclick="saveStock()">Update Stock</button>
    </div>
  </div>
</div>

<!-- Order Online -->
<div class="overlay" id="modal-order">
  <div class="modal">
    <div class="modal-title">🛒 Order Medicines Online</div>
    <div style="font-size:13px;color:var(--text2);margin-bottom:14px;">Low-stock medicines selected automatically:</div>
    <div class="order-medicine-list" id="order-med-list"></div>
    <div style="font-weight:800;font-size:13px;margin-bottom:10px;color:var(--text2);">CHOOSE PLATFORM</div>
    <div class="order-platform" id="order-platforms">
      <div class="platform-btn selected" onclick="selectPlatform(this,'1mg')">
        <div style="font-size:26px">💊</div>
        <div class="platform-name">1mg</div>
        <div class="platform-eta">⚡ Delivery in 2–4 hrs</div>
      </div>
      <div class="platform-btn" onclick="selectPlatform(this,'PharmEasy')">
        <div style="font-size:26px">🏥</div>
        <div class="platform-name">PharmEasy</div>
        <div class="platform-eta">🚀 Delivery in 3–6 hrs</div>
      </div>
      <div class="platform-btn" onclick="selectPlatform(this,'Netmeds')">
        <div style="font-size:26px">💙</div>
        <div class="platform-name">Netmeds</div>
        <div class="platform-eta">📦 Delivery next day</div>
      </div>
      <div class="platform-btn" onclick="selectPlatform(this,'Apollo')">
        <div style="font-size:26px">⚕️</div>
        <div class="platform-name">Apollo Pharmacy</div>
        <div class="platform-eta">⚡ Same day available</div>
      </div>
    </div>
    <div class="modal-footer">
      <button class="btn btn-outline" onclick="closeModal('modal-order')">Cancel</button>
      <button class="btn btn-orange" onclick="placeOrder()">🛒 Proceed to Order</button>
    </div>
  </div>
</div>

<div class="toast" id="toast"></div>

<script>
// ===== STATE =====
let S = { medicines:[], reminders:[], members:[], _stockId:null, _platform:'1mg' };
const COLORS = ['#0D9488','#F97316','#3B82F6','#8B5CF6','#EC4899','#14B8A6'];

function load() {
  const s = localStorage.getItem('medihome2');
  if (s) S = {...S, ...JSON.parse(s)};
  else seedData();
}
function save() { localStorage.setItem('medihome2', JSON.stringify(S)); }

function seedData() {
  S.members = [
    {id:1,name:'Dad',role:'Parent',age:52,blood:'O+',allergies:'None'},
    {id:2,name:'Mom',role:'Parent',age:48,blood:'A+',allergies:'Aspirin'},
    {id:3,name:'Sarah',role:'Child',age:14,blood:'B+',allergies:'None'},
  ];
  S.medicines = [
    {id:1,name:'Paracetamol',type:'Tablet',dosage:'500mg',qty:24,threshold:5,expiry:'2026-12-01',memberId:'',instructions:'Take after meals'},
    {id:2,name:'Amoxicillin',type:'Capsule',dosage:'250mg',qty:3,threshold:5,expiry:'2025-08-15',memberId:1,instructions:'Complete full course'},
    {id:3,name:'Cetirizine',type:'Tablet',dosage:'10mg',qty:14,threshold:3,expiry:'2027-03-20',memberId:2,instructions:'Once at bedtime'},
    {id:4,name:'Vitamin C',type:'Tablet',dosage:'1000mg',qty:60,threshold:10,expiry:'2027-01-01',memberId:'',instructions:'With breakfast'},
    {id:5,name:'Ibuprofen Syrup',type:'Syrup',dosage:'5ml',qty:2,threshold:5,expiry:'2026-06-30',memberId:3,instructions:'With water'},
  ];
  S.reminders = [
    {id:1,medicineId:1,time:'08:00',freq:'Daily',notes:'After breakfast',done:false},
    {id:2,medicineId:3,time:'22:00',freq:'Daily',notes:'Before sleep',done:false},
    {id:3,medicineId:4,time:'07:30',freq:'Daily',notes:'With water',done:true},
    {id:4,medicineId:2,time:'12:00',freq:'Twice daily',notes:'',done:false},
  ];
  save();
}

// ===== PHARMACY DATA =====
const OFFLINE_PHARMACIES = [
  {name:'Apollo Pharmacy',dist:'0.3 km',rating:'4.8',open:true,hours:'Open · 24 Hours',emoji:'⚕️',color:'#EFF6FF',phone:'+91-98765-43210',mapsUrl:'https://maps.google.com/?q=Apollo+Pharmacy'},
  {name:'MedPlus Store',dist:'0.7 km',rating:'4.5',open:true,hours:'Open · Closes 10 PM',emoji:'💊',color:'#F0FDF4',phone:'+91-98765-11111',mapsUrl:'https://maps.google.com/?q=MedPlus+Pharmacy'},
  {name:'Guardian Pharmacy',dist:'1.1 km',rating:'4.3',open:false,hours:'Closed · Opens 9 AM',emoji:'🏥',color:'#FEF9C3',phone:'+91-98765-22222',mapsUrl:'https://maps.google.com/?q=Guardian+Pharmacy'},
  {name:'Wellness Forever',dist:'1.8 km',rating:'4.6',open:true,hours:'Open · Closes 11 PM',emoji:'🌿',color:'#F0FDFA',phone:'+91-98765-33333',mapsUrl:'https://maps.google.com/?q=Wellness+Forever+Pharmacy'},
];

const ONLINE_PLATFORMS = [
  {name:'1mg',emoji:'💊',tagline:'India\'s #1 online pharmacy',delivery:'2–4 hours',discount:'Upto 25% off',rating:'4.8',url:'https://1mg.com',color:'#EFF6FF'},
  {name:'PharmEasy',emoji:'🏥',tagline:'Medicines at your door',delivery:'3–6 hours',discount:'Flat 20% off',rating:'4.6',url:'https://pharmeasy.in',color:'#F0FDF4'},
  {name:'Netmeds',emoji:'💙',tagline:'India ki Pharmacy',delivery:'Next Day',discount:'15% cashback',rating:'4.5',url:'https://netmeds.com',color:'#EFF6FF'},
  {name:'Apollo Health',emoji:'⚕️',tagline:'Trusted healthcare partner',delivery:'Same day',discount:'18% off + free delivery',rating:'4.7',url:'https://apollopharmacy.in',color:'#ECFDF5'},
];

// ===== HELPERS =====
function getMem(id){return S.members.find(m=>m.id==id);}
function getMed(id){return S.medicines.find(m=>m.id==id);}
function getMemName(id){const m=getMem(id);return m?m.name:'—';}
function isLow(m){return m.qty<=(m.threshold||5);}
function isExpired(d){return d&&new Date(d)<new Date();}
function isExpiringSoon(d){if(!d)return false;const diff=(new Date(d)-new Date())/(1000*60*60*24);return diff>=0&&diff<=30;}
function lowMeds(){return S.medicines.filter(m=>isLow(m));}
const memberColor=(id)=>{const i=S.members.findIndex(m=>m.id==id);return COLORS[Math.max(0,i)%COLORS.length];};

// ===== NAVIGATION =====
const PAGE_META = {
  dashboard:{title:'Dashboard',sub:'Your family health at a glance',action:null},
  medicines:{title:'Medicines',sub:'All medicines in your home',action:()=>openModal('modal-add-medicine')},
  reminders:{title:'Reminders',sub:'Daily medication schedule',action:()=>openModal('modal-add-reminder')},
  pharmacy:{title:'Find Pharmacy',sub:'Nearby & online pharmacies for low-stock medicines',action:null},
  inventory:{title:'Inventory',sub:'Stock levels & alerts',action:null},
  members:{title:'Family Members',sub:'Manage profiles & assigned medicines',action:()=>openModal('modal-add-member')},
};

function switchPage(id, el) {
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.nav-btn').forEach(b=>b.classList.remove('active'));
  document.getElementById('page-'+id).classList.add('active');
  el.classList.add('active');
  const meta = PAGE_META[id];
  document.getElementById('topbar-title').textContent = meta.title;
  document.getElementById('topbar-sub').textContent = meta.sub;
  const btn = document.getElementById('topbar-action');
  if(meta.action){btn.style.display='';btn.onclick=meta.action;}else{btn.style.display='none';}
  renderAll();
}

// ===== RENDER =====
function renderAll(){
  renderStats();
  renderDash();
  renderMeds();
  renderReminders();
  renderPharmacy();
  renderInventory();
  renderMembers();
  renderLowStockBanner();
}

function renderStats(){
  document.getElementById('s-total').textContent = S.medicines.length;
  document.getElementById('s-low').textContent = lowMeds().length;
  document.getElementById('s-rem').textContent = S.reminders.length;
  document.getElementById('s-mem').textContent = S.members.length;
  const badge = document.getElementById('low-stock-badge');
  badge.style.display = lowMeds().length > 0 ? '' : 'none';
}

function renderLowStockBanner(){
  const lm = lowMeds();
  const banner = document.getElementById('low-stock-banner');
  const list = document.getElementById('low-stock-meds-list');
  if(lm.length>0){
    banner.style.display='flex';
    list.innerHTML = lm.map(m=>`<span class="badge badge-orange">⚠️ ${m.name} (${m.qty} left)</span>`).join('');
  } else {
    banner.style.display='none';
  }
}

function renderDash(){
  // Reminders
  const el = document.getElementById('dash-reminders');
  const sorted = [...S.reminders].sort((a,b)=>a.time.localeCompare(b.time));
  if(!sorted.length){el.innerHTML='<div class="empty"><div class="empty-icon">🔔</div><div class="empty-text">No reminders set</div></div>';return;}
  el.innerHTML = sorted.map(r=>{
    const m=getMed(r.medicineId);
    const name=m?m.name:'?';
    const mem=m?getMemName(m.memberId):'';
    return `<div class="reminder-item">
      <div class="time-pill${r.done?' done':''}">${r.time}</div>
      <div class="rem-info">
        <div class="rem-name">${name}</div>
        <div class="rem-meta">${r.freq}${r.notes?' · '+r.notes:''}${mem&&mem!=='—'?' · <b>'+mem+'</b>':''}</div>
      </div>
      <button class="check-btn${r.done?' done':''}" onclick="toggleDone(${r.id})">${r.done?'✓':''}</button>
    </div>`;
  }).join('');

  // Stock
  const se = document.getElementById('dash-stock');
  if(!S.medicines.length){se.innerHTML='<div class="empty"><div class="empty-icon">📦</div><div class="empty-text">No medicines</div></div>';return;}
  const sorted2 = [...S.medicines].sort((a,b)=>a.qty/(a.threshold||5)-b.qty/(b.threshold||5));
  se.innerHTML = sorted2.slice(0,5).map(m=>{
    const t=m.threshold||5;
    const max=Math.max(m.qty,t*4,30);
    const pct=Math.min(100,Math.round(m.qty/max*100));
    const col=isLow(m)?'var(--red)':pct<60?'var(--yellow)':'var(--green)';
    return `<div style="margin-bottom:12px;">
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:5px;">
        <span style="font-weight:700;font-size:14px;">${m.name}</span>
        ${isLow(m)?`<span class="badge badge-red">⚠️ Low</span>`:`<span style="font-size:12px;color:var(--text2);">${m.qty} units</span>`}
      </div>
      <div class="stock-bar-row">
        <div class="stock-bar"><div class="stock-fill" style="width:${pct}%;background:${col};"></div></div>
        <span class="stock-pct">${pct}%</span>
      </div>
    </div>`;
  }).join('');
}

function renderMeds(){
  const tb=document.getElementById('med-tbody');
  if(!S.medicines.length){tb.innerHTML='<tr><td colspan="7"><div class="empty"><div class="empty-icon">💊</div><div class="empty-text">No medicines added</div></div></td></tr>';return;}
  tb.innerHTML = S.medicines.map(m=>{
    const ex = isExpired(m.expiry)?'<span class="badge badge-red">Expired</span>':isExpiringSoon(m.expiry)?`<span class="badge badge-orange">Soon ${m.expiry}</span>`:m.expiry?`<span class="badge badge-teal">${m.expiry}</span>`:'—';
    const st = isLow(m)?`<span class="badge badge-red">⚠️ ${m.qty}</span>`:`<span class="badge badge-green">✓ ${m.qty}</span>`;
    const memId=m.memberId;const mc=getMem(memId);
    const memEl=memId?`<span style="display:inline-flex;align-items:center;gap:6px;"><span style="width:24px;height:24px;border-radius:8px;background:${memberColor(memId)};color:#fff;display:inline-flex;align-items:center;justify-content:center;font-size:11px;font-weight:800;">${mc?mc.name[0]:'?'}</span>${mc?mc.name:'?'}</span>`:`<span class="badge badge-gray">All</span>`;
    return `<tr>
      <td><div style="font-weight:700">${m.name}</div>${m.instructions?`<div style="font-size:11px;color:var(--text2);margin-top:2px;">${m.instructions}</div>`:''}</td>
      <td><span class="badge badge-teal">${m.type}</span></td>
      <td>${m.dosage||'—'}</td>
      <td>${memEl}</td>
      <td>${ex}</td>
      <td>${st}</td>
      <td style="display:flex;gap:6px;align-items:center;">
        ${isLow(m)?`<button class="btn btn-orange btn-xs" onclick="openOrderForMed(${m.id})">🛒 Order</button>`:''}
        <button class="btn btn-outline btn-xs" style="color:var(--red);border-color:var(--red-light);" onclick="deleteMed(${m.id})">✕</button>
      </td>
    </tr>`;
  }).join('');
}

function renderReminders(){
  const el=document.getElementById('rem-list');
  if(!S.reminders.length){el.innerHTML='<div class="empty"><div class="empty-icon">🔔</div><div class="empty-text">No reminders set</div></div>';return;}
  const sorted=[...S.reminders].sort((a,b)=>a.time.localeCompare(b.time));
  el.innerHTML=sorted.map(r=>{
    const m=getMed(r.medicineId);
    const name=m?`${m.name} (${m.dosage||m.type})`:'?';
    const mem=m?getMemName(m.memberId):'';
    return `<div class="reminder-item">
      <div class="time-pill${r.done?' done':''}">${r.time}</div>
      <div class="rem-info">
        <div class="rem-name">${name}</div>
        <div class="rem-meta">${r.freq}${r.notes?' · '+r.notes:''}${mem&&mem!=='—'?' · For <b>'+mem+'</b>':''}</div>
      </div>
      <button class="check-btn${r.done?' done':''}" onclick="toggleDone(${r.id})">${r.done?'✓':''}</button>
      <button class="btn btn-outline btn-icon" style="color:var(--red);border-color:var(--red-light);font-size:14px;" onclick="deleteRem(${r.id})">✕</button>
    </div>`;
  }).join('');
}

function renderPharmacy(){
  const lm=lowMeds();
  // Low meds chips for pharmacy page
  const lowHtml = lm.length>0
    ? `<div style="background:linear-gradient(135deg,#FFFBEB,#FEF3C7);border:1.5px solid #FCD34D;border-radius:12px;padding:13px 16px;display:flex;align-items:flex-start;gap:12px;margin-bottom:16px;">
        <span style="font-size:22px;">⚠️</span>
        <div>
          <div style="font-weight:800;font-size:14px;color:#92400E;">These medicines need restocking:</div>
          <div style="display:flex;flex-wrap:wrap;gap:6px;margin-top:8px;">
            ${lm.map(m=>`<span class="badge badge-orange">💊 ${m.name} — ${m.qty} left</span>`).join('')}
          </div>
        </div>
      </div>` : '';

  document.getElementById('low-meds-for-pharmacy').innerHTML = lowHtml;
  document.getElementById('low-meds-for-online').innerHTML = lowHtml;

  // Offline pharmacies
  document.getElementById('offline-pharmacies').innerHTML = OFFLINE_PHARMACIES.map(p=>`
    <div class="pharmacy-card">
      <div class="ph-header">
        <div class="ph-icon" style="background:${p.color};font-size:26px;">${p.emoji}</div>
        <div style="flex:1">
          <div class="ph-name">${p.name}</div>
          <div class="ph-dist">📍 ${p.dist} away</div>
          <div class="ph-rating">⭐ ${p.rating}</div>
        </div>
        <div class="open-status" style="flex-shrink:0">
          <div class="open-dot" style="background:${p.open?'var(--green)':'var(--red)'}"></div>
          <span style="font-size:11px;color:${p.open?'var(--green)':'var(--red)'};">${p.open?'Open':'Closed'}</span>
        </div>
      </div>
      <div style="font-size:12px;color:var(--text2);margin-bottom:10px;">🕐 ${p.hours}</div>
      ${lm.length>0?`<div style="font-size:12px;color:var(--text2);margin-bottom:10px;">Can supply: ${lm.map(m=>`<span class="badge badge-green" style="margin-right:4px;">${m.name}</span>`).join('')}</div>`:''}
      <div class="ph-actions">
        <a class="dir-btn" href="${p.mapsUrl}" target="_blank">🗺️ Directions</a>
        <a class="call-btn" href="tel:${p.phone}">📞 Call</a>
        ${p.open?`<button class="btn btn-primary btn-sm" onclick="showToast('📍 Navigating to ${p.name}...')">Navigate</button>`:''}
      </div>
    </div>`).join('');

  // Online pharmacies
  document.getElementById('online-pharmacies').innerHTML = ONLINE_PLATFORMS.map(p=>`
    <div class="online-pharmacy-card">
      <div class="ph-header">
        <div class="ph-icon" style="background:${p.color};font-size:26px;">${p.emoji}</div>
        <div style="flex:1">
          <div class="ph-name">${p.name}</div>
          <div class="ph-dist">${p.tagline}</div>
          <div class="ph-rating">⭐ ${p.rating}</div>
        </div>
      </div>
      <div style="display:flex;gap:8px;flex-wrap:wrap;margin-bottom:12px;">
        <span class="badge badge-blue">⚡ ${p.delivery}</span>
        <span class="badge badge-green">🎁 ${p.discount}</span>
      </div>
      ${lm.length>0?`<div style="font-size:12px;font-weight:700;color:var(--text2);margin-bottom:8px;">ORDER THESE:</div>
      <div style="display:flex;flex-wrap:wrap;gap:6px;margin-bottom:12px;">${lm.map(m=>`<span class="badge badge-orange">💊 ${m.name}</span>`).join('')}</div>`:''}
      <div class="ph-actions">
        <button class="btn btn-blue btn-sm" onclick="openOrderModal('${p.name}')">🛒 Order on ${p.name}</button>
        <a class="dir-btn" href="${p.url}" target="_blank">🌐 Visit</a>
      </div>
    </div>`).join('');
}

function renderInventory(){
  const tb=document.getElementById('inv-tbody');
  if(!S.medicines.length){tb.innerHTML='<tr><td colspan="6"><div class="empty"><div class="empty-icon">📦</div><div class="empty-text">No medicines</div></div></td></tr>';return;}
  tb.innerHTML = S.medicines.map(m=>{
    const t=m.threshold||5;
    const max=Math.max(m.qty,t*4,30);
    const pct=Math.min(100,Math.round(m.qty/max*100));
    const col=isLow(m)?'var(--red)':pct<60?'var(--yellow)':'var(--green)';
    const st=isExpired(m.expiry)?'<span class="badge badge-red">Expired</span>':isLow(m)?'<span class="badge badge-orange">⚠️ Low Stock</span>':'<span class="badge badge-green">✓ Good</span>';
    return `<tr>
      <td><b>${m.name}</b></td>
      <td style="min-width:160px;">
        <div class="stock-bar-row">
          <div class="stock-bar"><div class="stock-fill" style="width:${pct}%;background:${col}"></div></div>
          <span class="stock-pct">${pct}%</span>
        </div>
      </td>
      <td>${m.qty}</td>
      <td>${t}</td>
      <td>${st}</td>
      <td style="display:flex;gap:6px;">
        <button class="btn btn-outline btn-sm" onclick="openStock(${m.id})">✏️ Update</button>
        ${isLow(m)?`<button class="btn btn-orange btn-sm" onclick="openOrderForMed(${m.id})">🛒 Order</button>`:''}
      </td>
    </tr>`;
  }).join('');
}

function renderMembers(){
  const g=document.getElementById('members-grid');
  if(!S.members.length){g.innerHTML='<div class="empty" style="grid-column:1/-1"><div class="empty-icon">👨‍👩‍👧</div><div class="empty-text">No family members added</div></div>';return;}
  g.innerHTML=S.members.map((mem,i)=>{
    const meds=S.medicines.filter(m=>m.memberId==mem.id);
    const col=COLORS[i%COLORS.length];
    return `<div class="member-card">
      <div style="display:flex;align-items:center;gap:12px;margin-bottom:12px;">
        <div class="member-avatar" style="background:${col}">${mem.name[0]}</div>
        <div style="flex:1">
          <div style="font-weight:800;font-size:15px;">${mem.name}</div>
          <div style="font-size:12px;color:var(--text2);">${mem.role}${mem.age?' · '+mem.age+' yrs':''}${mem.blood?' · '+mem.blood:''}</div>
        </div>
        <button class="btn btn-outline btn-icon" style="color:var(--red);border-color:var(--red-light);font-size:13px;" onclick="deleteMem(${mem.id})">✕</button>
      </div>
      ${mem.allergies&&mem.allergies.toLowerCase()!=='none'?`<div style="background:var(--red-light);border-radius:8px;padding:8px 12px;font-size:12px;color:#B91C1C;font-weight:700;margin-bottom:10px;">⚠️ Allergy: ${mem.allergies}</div>`:''}
      <div style="font-size:11px;font-weight:800;color:var(--text2);margin-bottom:7px;text-transform:uppercase;letter-spacing:0.05em;">Medicines</div>
      <div style="display:flex;flex-wrap:wrap;gap:6px;">
        ${meds.length?meds.map(m=>`<span class="badge badge-teal">${m.name}</span>`).join(''):'<span class="badge badge-gray">None</span>'}
      </div>
    </div>`;
  }).join('');
}

// ===== PHARMACY TABS =====
function setPhTab(tab){
  document.getElementById('ph-offline').style.display=tab==='offline'?'':'none';
  document.getElementById('ph-online').style.display=tab==='online'?'':'none';
  document.getElementById('tab-offline').classList.toggle('active',tab==='offline');
  document.getElementById('tab-online').classList.toggle('active',tab==='online');
}

// ===== ORDER MODAL =====
function openOrderModal(platform){
  const lm=lowMeds();
  const list=document.getElementById('order-med-list');
  list.innerHTML=lm.length?lm.map(m=>`
    <div class="order-med-row">
      <div style="flex:1;font-weight:700;">${m.name} <span style="color:var(--text2);font-size:12px;">(${m.dosage||m.type})</span></div>
      <div style="font-size:12px;color:var(--red);font-weight:700;">Only ${m.qty} left</div>
      <input type="number" value="1" min="1" style="width:60px;font-size:13px;">
    </div>`).join('')
    :'<div style="color:var(--text2);font-size:14px;">No low-stock medicines. You can still browse and order.</div>';

  if(platform){
    document.querySelectorAll('.platform-btn').forEach(b=>b.classList.remove('selected'));
    document.querySelectorAll('.platform-btn').forEach(b=>{if(b.querySelector('.platform-name')?.textContent===platform)b.classList.add('selected');});
    S._platform=platform;
  }
  openModal('modal-order');
}

function openOrderForMed(id){
  const m=getMed(id);
  if(!m)return;
  openOrderModal(null);
}

function selectPlatform(el,name){
  document.querySelectorAll('.platform-btn').forEach(b=>b.classList.remove('selected'));
  el.classList.add('selected');
  S._platform=name;
}

function placeOrder(){
  closeModal('modal-order');
  showToast(`✅ Order placed on ${S._platform}! Delivery on the way.`);
}

// ===== ACTIONS =====
function addMedicine(){
  const name=document.getElementById('mn').value.trim();
  if(!name){showToast('Please enter medicine name');return;}
  S.medicines.push({
    id:Date.now(),name,type:document.getElementById('mt').value,
    dosage:document.getElementById('md').value,qty:parseInt(document.getElementById('mq').value)||0,
    threshold:parseInt(document.getElementById('mth').value)||5,
    expiry:document.getElementById('me').value,
    memberId:document.getElementById('mm').value,
    instructions:document.getElementById('mi').value
  });
  save();renderAll();closeModal('modal-add-medicine');
  showToast('✅ Medicine added!');
  ['mn','md','mq','mth','me','mi'].forEach(id=>document.getElementById(id).value='');
}

function deleteMed(id){
  if(!confirm('Delete this medicine?'))return;
  S.medicines=S.medicines.filter(m=>m.id!==id);
  S.reminders=S.reminders.filter(r=>r.medicineId!==id);
  save();renderAll();showToast('🗑 Medicine deleted');
}

function addReminder(){
  const medicineId=document.getElementById('rm').value;
  const time=document.getElementById('rt').value;
  if(!medicineId||!time){showToast('Select medicine and time');return;}
  S.reminders.push({id:Date.now(),medicineId:parseInt(medicineId),time,freq:document.getElementById('rf').value,notes:document.getElementById('rn').value,done:false});
  save();renderAll();closeModal('modal-add-reminder');showToast('✅ Reminder added!');
  document.getElementById('rt').value='';document.getElementById('rn').value='';
}

function deleteRem(id){S.reminders=S.reminders.filter(r=>r.id!==id);save();renderAll();showToast('🗑 Reminder removed');}
function toggleDone(id){const r=S.reminders.find(r=>r.id===id);if(r){r.done=!r.done;save();renderAll();}}

function addMember(){
  const name=document.getElementById('emn').value.trim();
  if(!name){showToast('Please enter name');return;}
  S.members.push({id:Date.now(),name,role:document.getElementById('emr').value,age:document.getElementById('ema').value,blood:document.getElementById('emb').value,allergies:document.getElementById('emal').value});
  save();renderAll();closeModal('modal-add-member');showToast('✅ Member added!');
  ['emn','ema','emal'].forEach(id=>document.getElementById(id).value='');
}

function deleteMem(id){
  if(!confirm('Delete member?'))return;
  S.members=S.members.filter(m=>m.id!==id);
  S.medicines.forEach(m=>{if(m.memberId==id)m.memberId='';});
  save();renderAll();showToast('🗑 Member deleted');
}

function openStock(id){
  S._stockId=id;const m=getMed(id);
  document.getElementById('sk-name').value=m.name;
  document.getElementById('sk-qty').value=m.qty;
  document.getElementById('sk-thr').value=m.threshold||5;
  openModal('modal-stock');
}

function saveStock(){
  const m=getMed(S._stockId);
  if(m){m.qty=parseInt(document.getElementById('sk-qty').value)||0;m.threshold=parseInt(document.getElementById('sk-thr').value)||5;save();renderAll();closeModal('modal-stock');showToast('📦 Stock updated!');}
}

// ===== MODAL =====
function openModal(id){
  if(id==='modal-add-medicine'){
    const sel=document.getElementById('mm');
    sel.innerHTML='<option value="">— Unassigned —</option>';
    S.members.forEach(m=>sel.innerHTML+=`<option value="${m.id}">${m.name}</option>`);
  }
  if(id==='modal-add-reminder'){
    const sel=document.getElementById('rm');
    sel.innerHTML='<option value="">— Select —</option>';
    S.medicines.forEach(m=>sel.innerHTML+=`<option value="${m.id}">${m.name} (${m.dosage||m.type})</option>`);
  }
  document.getElementById(id).classList.add('open');
}
function closeModal(id){document.getElementById(id).classList.remove('open');}
document.querySelectorAll('.overlay').forEach(o=>o.addEventListener('click',e=>{if(e.target===o)o.classList.remove('open');}));

// ===== TOAST =====
function showToast(msg){
  const t=document.getElementById('toast');
  t.textContent=msg;t.classList.add('show');
  setTimeout(()=>t.classList.remove('show'),2800);
}

// ===== INIT =====
load();
document.getElementById('topbar-action').style.display='';
renderAll();
</script>
</body>
</html>
