<!DOCTYPE html>  
  
<html dir="rtl" lang="ar">  
<head>  
<meta charset="UTF-8">  
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">  
<meta name="apple-mobile-web-app-capable" content="yes">  
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">  
<meta name="apple-mobile-web-app-title" content="Dr.Tree">  
<meta name="theme-color" content="#1B4332">  
<title>🌳 Dr.Tree</title>  
<style>  
:root {  
  --gd:#1B4332; --gm:#2D6A4F; --gl:#52B788; --gp:#D8F3DC;  
  --gold:#D4AC0D; --goldl:#FFF9E6;  
  --or:#E07B39; --orl:#FEF0E7;  
  --red:#C0392B; --redl:#FADBD8;  
  --blue:#1A56DB; --bluel:#EBF5FF;  
  --bg:#EEF2EE; --white:#fff; --gray:#F7F7F7;  
  --border:#E5E7EB; --muted:#6B7280;  
}  
* { margin:0; padding:0; box-sizing:border-box; -webkit-tap-highlight-color:transparent; }  
body { font-family:Arial,sans-serif; background:var(--bg); direction:rtl; min-height:100vh; }  
input,select,textarea,button { font-family:Arial,sans-serif; font-size:15px; }  
  
/* Layout */  
#app { max-width:640px; margin:0 auto; padding:14px 12px 90px; }  
.header { background:var(–gd); padding:14px 16px; display:flex; align-items:center; justify-content:space-between; position:sticky; top:0; z-index:100; box-shadow:0 2px 10px rgba(0,0,0,.2); }  
.header-logo { color:#fff; font-weight:900; font-size:18px; }  
.header-logo span { color:var(–gl); }  
.header-badges { display:flex; gap:8px; align-items:center; }  
.badge-saved { background:#2D6A4F; color:var(–gl); border-radius:20px; padding:3px 10px; font-size:10px; font-weight:600; }  
.badge-overdue { background:var(–red); color:#fff; border-radius:20px; padding:3px 10px; font-size:11px; font-weight:700; animation:pulse 2s infinite; }  
@keyframes pulse { 0%,100%{opacity:1} 50%{opacity:.6} }  
  
/* Bottom nav */  
.bottom-nav { position:fixed; bottom:0; left:0; right:0; background:#fff; border-top:1px solid var(–border); display:flex; z-index:100; padding-bottom:env(safe-area-inset-bottom); }  
.nav-item { flex:1; padding:10px 4px 8px; text-align:center; cursor:pointer; border-top:3px solid transparent; }  
.nav-item.active { background:var(–gp); border-top-color:var(–gm); }  
.nav-item .nav-icon { font-size:20px; }  
.nav-item .nav-label { font-size:10px; font-weight:700; color:var(–muted); margin-top:2px; }  
.nav-item.active .nav-label { color:var(–gm); }  
  
/* Cards */  
.card { background:#fff; border-radius:14px; overflow:hidden; box-shadow:0 2px 10px rgba(0,0,0,.07); margin-bottom:14px; }  
.card-header { padding:13px 16px; display:flex; align-items:center; gap:8px; }  
.card-header h2 { color:#fff; font-weight:700; font-size:15px; }  
.card-header.between { justify-content:space-between; }  
  
/* KPIs */  
.kpis { display:grid; grid-template-columns:1fr 1fr; gap:10px; margin-bottom:14px; }  
.kpi { border-radius:12px; padding:14px; border-right:4px solid; box-shadow:0 1px 4px rgba(0,0,0,.06); }  
.kpi-label { font-size:10px; color:var(–muted); font-weight:700; margin-bottom:4px; text-transform:uppercase; letter-spacing:.5px; }  
.kpi-value { font-size:22px; font-weight:900; }  
  
/* Forms */  
.field { margin-bottom:12px; }  
.field label { display:block; font-size:11px; font-weight:700; color:var(–muted); margin-bottom:5px; text-transform:uppercase; letter-spacing:.5px; }  
input, select, textarea {  
width:100%; padding:11px 12px; border:1.5px solid var(–border); border-radius:8px;  
font-size:15px; direction:rtl; background:#fafafa; outline:none; box-sizing:border-box;  
-webkit-appearance:none; appearance:none; color:#111;  
}  
input:focus, select:focus, textarea:focus { border-color:var(–gl); background:#fff; }  
input.error { border-color:var(–red); background:var(–redl); }  
textarea { min-height:72px; resize:vertical; }  
.grid2 { display:grid; grid-template-columns:1fr 1fr; gap:12px; }  
  
/* Buttons */  
.btn { border:none; border-radius:10px; font-size:14px; font-weight:700; cursor:pointer; padding:12px 20px; display:inline-flex; align-items:center; gap:6px; }  
.btn-primary { background:var(–gd); color:#fff; width:100%; justify-content:center; }  
.btn-gold { background:var(–gold); color:var(–gd); width:100%; justify-content:center; }  
.btn-secondary { background:transparent; color:var(–muted); border:1.5px solid var(–border); }  
.btn-sm { padding:6px 12px; font-size:12px; border-radius:20px; }  
.btn-full { width:100%; padding:14px; font-size:15px; border-radius:12px; margin-bottom:10px; }  
  
/* Sections */  
.section-extras { background:var(–orl); border-radius:10px; padding:12px; margin-bottom:12px; }  
.section-extras h3 { font-size:12px; font-weight:700; color:var(–or); margin-bottom:10px; }  
.section-pay { background:var(–bluel); border-radius:10px; padding:12px; margin-bottom:16px; }  
.section-pay h3 { font-size:12px; font-weight:700; color:var(–blue); margin-bottom:10px; }  
  
/* Visit rows */  
.visit-row { padding:12px 16px; border-bottom:1px solid #F0F0F0; }  
.visit-row:last-child { border-bottom:none; }  
.visit-row.overdue { background:var(–redl); }  
.visit-row.even { background:var(–white); }  
.visit-row.odd { background:var(–gray); }  
.visit-top { display:flex; justify-content:space-between; align-items:flex-start; margin-bottom:4px; }  
.visit-name { font-weight:700; font-size:14px; }  
.visit-area { color:var(–muted); font-size:12px; margin-right:6px; }  
.visit-meta { font-size:12px; color:#666; margin-bottom:3px; }  
.visit-notes { font-size:11px; color:var(–blue); margin-bottom:3px; }  
.visit-extra { font-size:12px; color:var(–or); margin-top:4px; display:flex; gap:8px; align-items:center; flex-wrap:wrap; }  
.visit-actions { display:flex; gap:6px; align-items:center; }  
.btn-icon { background:none; border:none; font-size:16px; cursor:pointer; padding:2px 5px; }  
.type-tag { background:var(–gp); color:var(–gm); padding:2px 8px; border-radius:12px; font-size:11px; font-weight:700; }  
  
/* Badge */  
.badge { display:inline-block; padding:2px 9px; border-radius:20px; font-size:11px; font-weight:700; }  
.badge-sm { padding:1px 7px; font-size:10px; }  
.badge-paid { background:var(–gp); color:var(–gm); }  
.badge-partial { background:var(–goldl); color:var(–gold); }  
.badge-unpaid { background:var(–redl); color:var(–red); }  
.badge-done { background:var(–gp); color:var(–gm); }  
.badge-progress { background:var(–orl); color:var(–or); }  
.badge-pending { background:var(–goldl); color:var(–gold); }  
.badge-approved { background:var(–gp); color:var(–gm); }  
  
/* Alert */  
.alert-overdue { background:var(–redl); border:1px solid var(–red); border-radius:12px; padding:12px 16px; margin-bottom:14px; display:flex; align-items:center; gap:10px; }  
.alert-overdue .icon { font-size:24px; }  
.alert-overdue h3 { font-weight:700; font-size:14px; color:var(–red); }  
.alert-overdue p { font-size:12px; color:var(–muted); margin-top:2px; }  
  
/* Filters */  
.filters { padding:12px; }  
.filters input, .filters select { margin-bottom:10px; }  
  
/* Modal */  
.modal { display:none; position:fixed; inset:0; background:rgba(0,0,0,.5); z-index:200; align-items:flex-end; }  
.modal.open { display:flex; }  
.modal-box { background:#fff; border-radius:20px 20px 0 0; width:100%; max-height:92vh; overflow-y:auto; padding:20px 16px; padding-bottom:calc(20px + env(safe-area-inset-bottom)); }  
.modal-handle { width:40px; height:4px; background:#ddd; border-radius:4px; margin:0 auto 16px; }  
.modal-title { font-size:17px; font-weight:700; color:var(–gd); margin-bottom:16px; text-align:center; }  
.modal-footer { display:flex; gap:10px; margin-top:4px; }  
  
/* Invoice selectors */  
.inv-type-switcher { display:flex; gap:8px; margin-bottom:16px; background:#F0F4F1; padding:5px; border-radius:10px; }  
.inv-type-btn { flex:1; padding:10px; border-radius:8px; cursor:pointer; text-align:center; border:2px solid transparent; font-weight:700; font-size:14px; color:var(–muted); background:transparent; }  
.inv-type-btn.active { background:#fff; border-color:var(–gm); color:var(–gm); box-shadow:0 2px 6px rgba(0,0,0,.1); }  
.visit-selector { display:flex; flex-direction:column; gap:8px; margin-bottom:14px; }  
.visit-select-item { display:flex; align-items:center; gap:10px; padding:12px; border-radius:10px; border:2px solid var(–border); background:#FAFAFA; cursor:pointer; }  
.visit-select-item.selected { background:var(–gp); border-color:var(–gm); }  
.check { width:22px; height:22px; border-radius:6px; border:2px solid #ccc; background:#fff; display:flex; align-items:center; justify-content:center; flex-shrink:0; font-size:13px; color:#fff; font-weight:900; }  
.check.round { border-radius:50%; }  
.check.checked { background:var(–gm); border-color:var(–gm); }  
.inv-summary { background:var(–gp); border-radius:10px; padding:14px; margin-bottom:14px; }  
.inv-summary-row { display:flex; justify-content:space-between; font-size:13px; color:var(–gm); margin-bottom:6px; }  
.inv-summary-row.orange { color:var(–or); }  
.inv-summary-total { display:flex; justify-content:space-between; font-size:17px; color:var(–gd); font-weight:900; margin-top:8px; padding-top:8px; border-top:1px solid rgba(0,0,0,.1); }  
  
/* Toast */  
.toast { position:fixed; top:70px; left:50%; transform:translateX(-50%) translateY(-20px); background:var(–gd); color:#fff; padding:12px 24px; border-radius:30px; font-size:14px; font-weight:600; z-index:999; box-shadow:0 4px 16px rgba(0,0,0,.2); white-space:nowrap; opacity:0; transition:all .3s; pointer-events:none; }  
.toast.show { opacity:1; transform:translateX(-50%) translateY(0); }  
  
/* Empty */  
.empty { padding:48px 24px; text-align:center; color:var(–muted); }  
.empty .icon { font-size:48px; margin-bottom:12px; }  
  
/* Tabs */  
.tab { display:none; }  
.tab.active { display:block; }  
</style>  
  
<script type="module">  
  import { initializeApp } from "https://www.gstatic.com/firebasejs/10.12.0/firebase-app.js";  
  import { getDatabase, ref, set, onValue, push, remove, get } from "https://www.gstatic.com/firebasejs/10.12.0/firebase-database.js";  
  
  const firebaseConfig = { databaseURL: "https://drtree-abfe8-default-rtdb.asia-southeast1.firebasedatabase.app" };  
  const app = initializeApp(firebaseConfig);  
  const db = getDatabase(app);  
  
  window._fb = { db, ref, set, onValue, push, remove, get };  
  window._fbReady = true;  
  setTimeout(() => window.dispatchEvent(new Event('fb-ready')), 500);  
</script>  
  
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>  
  
<script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>  
  
</head>  
<body>  
  
<!-- Header -->  
  
<div class="header">  
  <div class="header-logo">🌳 <span>Dr.Tree</span></div>  
  <div class="header-badges">  
    <span id="badge-overdue" class="badge-overdue" style="display:none">⚠️ <span id="overdue-count">0</span> **متأخر**</span>  
    <span id="sync-badge" style="display:none;background:var(--blue);color:#fff;border-radius:20px;padding:3px 10px;font-size:10px;font-weight:600">🔄 **مزامنة**</span>  
    <span class="badge-saved">💾 **محفوظ**</span>  
  </div>  
</div>  
  
<!-- Toast -->  
  
<div class="toast" id="toast"></div>  
  
<!-- App -->  
  
<div id="app">  
  
  <!-- DASHBOARD TAB -->  
  
  <div id="tab-dashboard" class="tab active">  
    <div id="alert-overdue" class="alert-overdue" style="display:none">  
      <div class="icon">⚠️</div>  
      <div>  
        <h3 id="alert-overdue-text">**عميل** **متأخر** **في** **الدفع**</h3>  
        <p>**راجع** **السجل** **للتفاصيل**</p>  
      </div>  
    </div>  
    <div class="kpis">  
      <div class="kpi" style="background:var(--gp);border-color:var(--gl)">  
        <div class="kpi-label">**إجمالي** **الزيارات**</div>  
        <div class="kpi-value" id="kpi-total" style="color:var(--gm)">0</div>  
      </div>  
      <div class="kpi" style="background:var(--orl);border-color:var(--or)">  
        <div class="kpi-label">**مبالغ** **الإضافية**</div>  
        <div class="kpi-value" id="kpi-extras" style="color:var(--or)">0</div>  
      </div>  
      <div class="kpi" style="background:var(--goldl);border-color:var(--gold)">  
        <div class="kpi-label">**إضافية** **مكتملة**</div>  
        <div class="kpi-value" id="kpi-done" style="color:var(--gold)">0</div>  
      </div>  
      <div class="kpi" style="background:var(--redl);border-color:var(--red)">  
        <div class="kpi-label">**غير** **مدفوع**</div>  
        <div class="kpi-value" id="kpi-unpaid" style="color:var(--red)">0</div>  
      </div>  
    </div>  
  
```  
<button class="btn btn-primary btn-full" onclick="openAdd()">➕ **إضافة** **زيارة** **جديدة**</button>  
  
<!-- Upcoming visits -->  
<div id="upcoming-card" class="card" style="display:none">  
  <div class="card-header" style="background:var(--gm)">  
    <h2>📅 **المواعيد** **القادمة**</h2>  
  </div>  
  <div id="upcoming-list"></div>  
</div>  
  
<div class="card">  
  <div class="card-header between" style="background:var(--gd)">  
    <h2>📋 **آخر** **الزيارات**</h2>  
    <button class="btn btn-sm" style="background:var(--goldl);color:#8B6914;border:1px solid var(--gold)" onclick="exportCSV()">📥 Excel</button>  
  </div>  
  <div id="recent-list"></div>  
</div>  
```  
  
  </div>  
  
  <!-- LOG TAB -->  
  
  <div id="tab-log" class="tab">  
    <div class="card filters">  
      <input type="text" id="search-input" placeholder="🔍 **بحث** **عن** **عميل** **أو** **عمل**..." oninput="renderLog()">  
      <div class="grid2">  
        <select id="filter-client" onchange="renderLog()">  
          <option value="">**كل** **العملاء**</option>  
        </select>  
        <select id="filter-type" onchange="renderLog()">  
          <option value="">**كل** **الأنواع**</option>  
          <option>**قص** **وتشذيب**</option><option>**زراعة**</option><option>**صيانة**</option>  
          <option>**تنسيق**</option><option>**ري**</option><option>**تنظيف**</option>  
          <option>**تسميد**</option><option>**رش** **مبيد**</option><option>**أخرى**</option>  
        </select>  
      </div>  
      <div style="display:flex;gap:8px;align-items:center">  
        <select id="filter-pay" onchange="renderLog()" style="flex:1">  
          <option value="">**كل** **حالات** **الدفع**</option>  
          <option>**غير** **مدفوع**</option><option>**مدفوع** **جزئياً**</option><option>**مدفوع**</option>  
        </select>  
        <button class="btn btn-secondary btn-sm" onclick="clearFilters()">**مسح**</button>  
      </div>  
      <div>  
        <select id="filter-month" onchange="renderLog()" style="width:100%;padding:10px 12px;border:1.5px solid var(--border);border-radius:8px;font-size:14px;direction:rtl;background:#fafafa;outline:none;-webkit-appearance:none">  
          <option value="">**كل** **الأشهر**</option>  
        </select>  
      </div>  
    </div>  
  
```  
<div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:10px">  
  <span style="font-size:13px;color:var(--muted)" id="log-count">0 **زيارة**</span>  
  <div style="display:flex;gap:8px">  
    <button class="btn btn-primary btn-sm" onclick="openAdd()">➕ **إضافة**</button>  
    <button class="btn btn-sm" style="background:var(--goldl);color:#8B6914;border:1px solid var(--gold)" onclick="exportCSV()">📥 Excel</button>  
  </div>  
</div>  
<div class="card" id="log-list"></div>  
```  
  
  </div>  
  
  <!-- INVOICE TAB -->  
  
  <div id="tab-invoice" class="tab">  
    <div class="card">  
      <div class="card-header" style="background:var(--gm)">  
        <h2>🧾 **إعداد** **الفاتورة**</h2>  
      </div>  
      <div style="padding:16px">  
        <div class="inv-type-switcher">  
          <button class="inv-type-btn active" id="inv-monthly-btn" onclick="setInvType('monthly')">📅 **فاتورة** **شهرية**</button>  
          <button class="inv-type-btn" id="inv-single-btn" onclick="setInvType('single')">📄 **فاتورة** **زيارة**</button>  
        </div>  
  
```  
    <div class="field">  
      <label>**العميل**</label>  
      <select id="inv-client" onchange="onInvClientChange()">  
        <option value="">**اختر** **العميل**...</option>  
      </select>  
    </div>  
    <div class="field" id="inv-month-field" style="display:none">  
      <label>**شهر** **الفاتورة**</label>  
      <select id="inv-month" onchange="autoSelectMonthVisits()" style="width:100%;padding:11px 12px;border:1.5px solid var(--border);border-radius:8px;font-size:15px;direction:rtl;background:#fafafa;outline:none;-webkit-appearance:none">  
        <option value="">**اختر** **الشهر**...</option>  
      </select>  
    </div>  
    <div class="grid2">  
      <div class="field"><label>**رقم** **الفاتورة**</label><input type="text" id="inv-num" value="INV-001"></div>  
      <div class="field"><label id="inv-fee-label">**الباقة** **الشهرية** (QAR)</label><input type="number" id="inv-fee" value="500"></div>  
    </div>  
    <div class="grid2">  
      <div class="field"><label>**تاريخ** **الاستحقاق**</label><input type="date" id="inv-due"></div>  
      <div class="field">  
        <label>**حالة** **الدفع**</label>  
        <select id="inv-pay-status">  
          <option>**غير** **مدفوع**</option><option>**مدفوع** **جزئياً**</option><option>**مدفوع**</option>  
        </select>  
      </div>  
    </div>  
  
    <div id="inv-visits-section" style="display:none">  
      <div style="font-size:13px;font-weight:700;color:var(--gm);margin-bottom:8px" id="inv-visits-label">**اختر** **الزيارات**:</div>  
      <div class="visit-selector" id="inv-visits-list"></div>  
      <div class="inv-summary" id="inv-summary" style="display:none">  
        <div class="inv-summary-row" id="inv-sum-fee-row"><span id="inv-sum-fee-label">**الباقة** **الشهرية**</span><span id="inv-sum-fee">0 QAR</span></div>  
        <div class="inv-summary-row orange" id="inv-sum-ext-row" style="display:none"><span>**الأعمال** **الإضافية**</span><span id="inv-sum-ext">0 QAR</span></div>  
        <div class="inv-summary-total"><span>**الإجمالي**</span><span id="inv-sum-total">0 QAR</span></div>  
      </div>  
    </div>  
  </div>  
  <div style="padding:0 16px 16px" id="inv-buttons" style="display:none">  
    <button class="btn btn-primary btn-full" onclick="doPrint()">🖨 **طباعة** / **حفظ** PDF</button>  
    <button class="btn btn-gold btn-full" onclick="doExportHTML()">📄 **تصدير** **الفاتورة** **كملف**</button>  
    <button class="btn btn-full" style="background:#25D366;color:#fff;border:none" onclick="shareInvoiceWhatsApp()">💬 **مشاركة** **عبر** **واتساب**</button>  
  </div>  
</div>  
```  
  
  </div>  
  
</div>  
  
<!-- Bottom Nav -->  
  
  <!-- CLIENTS TAB -->  
  
  <div id="tab-clients" class="tab">  
    <button class="btn btn-primary btn-full" style="margin-bottom:14px;border-radius:12px;padding:14px;font-size:15px" onclick="openAddClient()">  
      👤 **إضافة** **عميل** **جديد**  
    </button>  
    <div class="card" id="clients-list-card">  
      <div class="card-header" style="background:var(--gd)">  
        <h2>👥 **قائمة** **العملاء**</h2>  
        <span id="clients-count" style="margin-right:auto;background:var(--gl);color:white;padding:2px 10px;border-radius:20px;font-size:11px;font-weight:700"></span>  
      </div>  
      <div id="clients-list-body"></div>  
    </div>  
  </div>  
  
  <!-- QUOTATION TAB -->  
  
  <div id="tab-quote" class="tab">  
    <div style="margin-bottom:14px">  
      <button class="btn btn-primary btn-full" style="border-radius:12px;padding:14px;font-size:15px" onclick="newQuote()">  
        📋 **كوتيشن** **جديد**  
      </button>  
    </div>  
  
```  
<!-- Quote Form -->  
<div class="card" id="quote-form-card" style="display:none">  
  <div class="card-header between" style="background:var(--gm)">  
    <h2>📋 **إعداد** **الكوتيشن**</h2>  
    <button onclick="document.getElementById('quote-form-card').style.display='none'" style="background:none;border:none;color:white;font-size:18px;cursor:pointer">×</button>  
  </div>  
  <div style="padding:16px">  
    <div class="grid2">  
      <div class="field"><label>**العميل**</label>  
        <select id="q-client" onchange="onQClientChange(this.value)" style="width:100%;padding:11px 12px;border:1.5px solid var(--border);border-radius:8px;font-size:15px;direction:rtl;background:#fafafa;outline:none;-webkit-appearance:none;margin-bottom:6px">  
          <option value="">**اختر** **العميل**...</option>  
          <option value="__new__">+ **إضافة** **عميل** **جديد**...</option>  
        </select>  
      <input type="text" id="q-new-client" placeholder="**اكتب** **اسم** **العميل** **الجديد**..." style="display:none;width:100%;padding:11px 12px;border:1.5px solid var(--gm);border-radius:8px;font-size:15px;direction:rtl;background:#fafafa;outline:none;box-sizing:border-box">  
      </div>  
      <div class="field"><label>**تاريخ** **الكوتيشن**</label><input type="date" id="q-date" style="width:100%;padding:11px 12px;border:1.5px solid var(--border);border-radius:8px;font-size:15px;direction:rtl;background:#fafafa;outline:none;box-sizing:border-box"></div>  
    </div>  
    <div class="field"><label>**وصف** **المشروع**</label><textarea id="q-desc" placeholder="**وصف** **الأعمال** **المطلوبة**..." style="width:100%;padding:11px 12px;border:1.5px solid var(--border);border-radius:8px;font-size:15px;direction:rtl;background:#fafafa;min-height:72px;resize:vertical;outline:none;box-sizing:border-box"></textarea></div>  
  
    <!-- Labor Section -->  
    <div style="background:#EBF5FF;border-radius:10px;padding:12px;margin-bottom:12px">  
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:10px">  
        <div style="font-size:12px;font-weight:700;color:#1A56DB">👷 **العمالة**</div>  
        <button onclick="addLaborRow()" style="background:#1A56DB;color:white;border:none;border-radius:8px;padding:4px 12px;font-size:12px;cursor:pointer">+ **إضافة**</button>  
      </div>  
      <div id="labor-rows"></div>  
    </div>  
  
    <!-- Plants Section -->  
    <div style="background:#EAF3DE;border-radius:10px;padding:12px;margin-bottom:12px">  
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:10px">  
        <div style="font-size:12px;font-weight:700;color:#3B6D11">🌳 **النباتات**</div>  
        <button onclick="addPlantRow()" style="background:#3B6D11;color:white;border:none;border-radius:8px;padding:4px 12px;font-size:12px;cursor:pointer">+ **إضافة**</button>  
      </div>  
      <datalist id="plants-datalist"></datalist>  
      <div id="plant-rows"></div>  
    </div>  
  
    <!-- Materials Section -->  
    <div style="background:var(--gp);border-radius:10px;padding:12px;margin-bottom:12px">  
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:10px">  
        <div style="font-size:12px;font-weight:700;color:var(--gm)">🪨 **المواد** **والمستلزمات**</div>  
        <button onclick="addMaterialRow()" style="background:var(--gm);color:white;border:none;border-radius:8px;padding:4px 12px;font-size:12px;cursor:pointer">+ **إضافة**</button>  
      </div>  
      <div id="material-rows"></div>  
    </div>  
  
    <!-- Other Section -->  
    <div style="background:var(--orl);border-radius:10px;padding:12px;margin-bottom:12px">  
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:10px">  
        <div style="font-size:12px;font-weight:700;color:var(--or)">⚙ **أجور** **أخرى**</div>  
        <button onclick="addOtherRow()" style="background:var(--or);color:white;border:none;border-radius:8px;padding:4px 12px;font-size:12px;cursor:pointer">+ **إضافة**</button>  
      </div>  
      <div id="other-rows"></div>  
    </div>  
  
    <!-- Summary -->  
    <div style="background:var(--gp);border-radius:10px;padding:14px;margin-bottom:4px" id="quote-summary">  
      <div style="display:flex;justify-content:space-between;font-size:13px;color:#1A56DB;margin-bottom:6px"><span>👷 **العمالة**</span><span id="qs-labor">0 QAR</span></div>  
      <div style="display:flex;justify-content:space-between;font-size:13px;color:#3B6D11;margin-bottom:6px"><span>🌳 **النباتات**</span><span id="qs-plant">0 QAR</span></div>  
      <div style="display:flex;justify-content:space-between;font-size:13px;color:var(--gm);margin-bottom:6px"><span>🪨 **المواد**</span><span id="qs-material">0 QAR</span></div>  
      <div style="display:flex;justify-content:space-between;font-size:13px;color:var(--or);margin-bottom:8px"><span>⚙ **أجور** **أخرى**</span><span id="qs-other">0 QAR</span></div>  
      <div style="height:1px;background:rgba(0,0,0,.1);margin-bottom:8px"></div>  
      <div style="display:flex;justify-content:space-between;font-size:17px;color:var(--gd);font-weight:900"><span>**الإجمالي**</span><span id="qs-total">0 QAR</span></div>  
    </div>  
  </div>  
  <div style="padding:0 16px 16px;display:flex;flex-direction:column;gap:10px">  
    <button class="btn btn-primary btn-full" style="padding:14px;font-size:15px" onclick="printQuote()">🖨 **طباعة** / **حفظ** PDF</button>  
    <button class="btn btn-full" style="background:#25D366;color:#fff;border:none;padding:12px;border-radius:10px;font-size:14px;font-weight:700;cursor:pointer" onclick="shareQuoteWhatsApp()">💬 **مشاركة** **عبر** **واتساب**</button>  
  </div>  
</div>  
  
<!-- Saved Quotes -->  
<div class="card">  
  <div class="card-header" style="background:var(--gd)">  
    <h2>📁 **الكوتيشنات** **المحفوظة**</h2>  
    <span id="quotes-count" style="margin-right:auto;background:var(--gl);color:white;padding:2px 10px;border-radius:20px;font-size:11px;font-weight:700"></span>  
  </div>  
  <div id="quotes-list"></div>  
</div>  
```  
  
  </div>  
  
<div class="bottom-nav">  
  <div class="nav-item active" id="nav-dashboard" onclick="switchTab('dashboard')">  
    <div class="nav-icon">🏠</div>  
    <div class="nav-label">**الرئيسية**</div>  
  </div>  
  <div class="nav-item" id="nav-log" onclick="switchTab('log')">  
    <div class="nav-icon">📋</div>  
    <div class="nav-label" id="nav-log-label">**السجل**</div>  
  </div>  
  <div class="nav-item" id="nav-clients" onclick="switchTab('clients')">  
    <div class="nav-icon">👥</div>  
    <div class="nav-label">**العملاء**</div>  
  </div>  
  <div class="nav-item" id="nav-quote" onclick="switchTab('quote')">  
    <div class="nav-icon">📋</div>  
    <div class="nav-label">**كوتيشن**</div>  
  </div>  
  <div class="nav-item" id="nav-invoice" onclick="switchTab('invoice')">  
    <div class="nav-icon">🧾</div>  
    <div class="nav-label">**الفواتير**</div>  
  </div>  
</div>  
  
<!-- Visit Modal -->  
  
<div class="modal" id="modal">  
  <div class="modal-box">  
    <div class="modal-handle"></div>  
    <div class="modal-title" id="modal-title">➕ **إضافة** **زيارة** **جديدة**</div>  
  
```  
<div class="field">  
  <label>**اسم** **العميل** *</label>  
  <select id="f-client-select" onchange="onClientSelect(this.value)" style="width:100%;padding:11px 12px;border:1.5px solid var(--border);border-radius:8px;font-size:15px;direction:rtl;background:var(--color-background-primary,#fafafa);outline:none;-webkit-appearance:none;margin-bottom:6px">  
    <option value="">**اختر** **عميل** **موجود**...</option>  
  </select>  
  <input type="text" id="f-client" list="clients-list" placeholder="**أو** **اكتب** **اسم** **جديد**..." oninput="autoFillArea(this.value)" style="width:100%;padding:11px 12px;border:1.5px solid var(--border);border-radius:8px;font-size:15px;direction:rtl;background:#fafafa;outline:none;box-sizing:border-box">  
  <datalist id="clients-list"></datalist>  
</div>  
<div class="grid2">  
  <div class="field"><label>**المنطقة**</label>  
    <select id="f-area-select" onchange="document.getElementById('f-area').value=this.value" style="width:100%;padding:11px 12px;border:1.5px solid var(--border);border-radius:8px;font-size:15px;direction:rtl;background:#fafafa;outline:none;-webkit-appearance:none;margin-bottom:6px">  
      <option value="">**اختر** **منطقة**...</option>  
    </select>  
    <input type="text" id="f-area" list="areas-list" placeholder="**أو** **اكتب** **منطقة** **جديدة**..." style="width:100%;padding:11px 12px;border:1.5px solid var(--border);border-radius:8px;font-size:15px;direction:rtl;background:#fafafa;outline:none;box-sizing:border-box">  
    <datalist id="areas-list"></datalist>  
  </div>  
  <div class="field"><label>**التاريخ** *</label><input type="date" id="f-date"></div>  
</div>  
<div class="field">  
  <label>**نوع** **العمل**</label>  
  <select id="f-type">  
    <option value="">**اختر**...</option>  
    <option>**قص** **وتشذيب**</option><option>**زراعة**</option><option>**صيانة**</option>  
    <option>**تنسيق**</option><option>**ري**</option><option>**تنظيف**</option>  
    <option>**تسميد**</option><option>**رش** **مبيد**</option><option>**أخرى**</option>  
  </select>  
</div>  
<div class="field"><label>**الأعمال** **المنجزة**</label><textarea id="f-work" placeholder="**وصف** **الأعمال**..."></textarea></div>  
<div class="field"><label>**ملاحظات**</label><textarea id="f-notes" placeholder="**أي** **ملاحظات**..." style="min-height:80px"></textarea></div>  
  
<div class="section-extras">  
  <h3>⚙ **الأعمال** **الإضافية**</h3>  
  <div class="field"><textarea id="f-extra" placeholder="**وصف** **الأعمال** **الإضافية**..." style="min-height:52px;background:#fff"></textarea></div>  
  <div class="grid2">  
    <div class="field"><label>**المبلغ** (QAR)</label><input type="number" id="f-extra-amount" placeholder="0" min="0" style="background:#fff"></div>  
    <div class="field">  
      <label>**الحالة**</label>  
      <select id="f-extra-status" style="background:#fff">  
        <option value="">**اختر**...</option>  
        <option>**قيد** **الموافقة**</option><option>**موافق** **عليه**</option><option>**قيد** **التنفيذ**</option><option>**مكتمل**</option>  
      </select>  
    </div>  
  </div>  
</div>  
  
<div class="section-pay">  
  <h3>💰 **الدفع**</h3>  
  <div class="grid2">  
    <div class="field">  
      <label>**حالة** **الدفع**</label>  
      <select id="f-pay-status" style="background:#fff" onchange="togglePaidAmount()">  
        <option>**غير** **مدفوع**</option><option>**مدفوع** **جزئياً**</option><option>**مدفوع**</option>  
      </select>  
    </div>  
    <div class="field"><label>**تاريخ** **الاستحقاق**</label><input type="date" id="f-due-date" style="background:#fff"></div>  
  </div>  
  <div class="field" id="paid-amount-field" style="display:none">  
    <label>**المبلغ** **المدفوع** (QAR)</label>  
    <input type="number" id="f-paid-amount" placeholder="0" min="0" style="background:#fff">  
  </div>  
</div>  
  
<div class="section-next" style="background:#F0F4F1;border-radius:10px;padding:12px;margin-bottom:16px">  
  <h3 style="font-size:12px;font-weight:700;color:var(--gm);margin-bottom:10px">📅 **الموعد** **القادم**</h3>  
  <div class="grid2">  
    <div class="field"><label>**تاريخ** **الزيارة** **القادمة**</label><input type="date" id="f-next-date" style="background:#fff"></div>  
    <div class="field"><label>**ملاحظة** **الموعد**</label><input type="text" id="f-next-note" placeholder="**مثال**: **قص** **العشب**" style="background:#fff"></div>  
  </div>  
</div>  
<div class="modal-footer">  
  <button class="btn btn-primary" style="flex:1" id="modal-save-btn" onclick="saveVisit()">✚ **أضف** **للسجل**</button>  
  <button class="btn btn-secondary" onclick="closeModal()">**إلغاء**</button>  
</div>  
```  
  
  </div>  
</div>  
  
<script>  
// **──** Colors **──**  
const GD='#1B4332',GM='#2D6A4F',GL='#52B788',GP='#D8F3DC',GOLD='#D4AC0D',GOLDL='#FFF9E6',OR='#E07B39',ORL='#FEF0E7',RED='#C0392B',REDL='#FADBD8',BLUE='#1A56DB';  
  
// **──** Data **──**  
const TODAY = new Date().toISOString().split('T')[0];  
let visits = [], nextId = 1, editId = null, invType = 'monthly', selectedVisits = [];  
  
function loadData() {  
  // Load from localStorage as fallback while Firebase loads  
  try { visits = JSON.parse(localStorage.getItem('dt_visits') || '[]'); } catch { visits = []; }  
  try { nextId = parseInt(localStorage.getItem('dt_nextid') || '1'); } catch { nextId = 1; }  
  renderAll();  
}  
  
function saveData() {  
  // Save to localStorage always (offline support)  
  try { localStorage.setItem('dt_visits', JSON.stringify(visits)); localStorage.setItem('dt_nextid', String(nextId)); } catch {}  
  // Save to Firebase if ready  
  if (window._fbReady) {  
    const { db, ref, set } = window._fb;  
    set(ref(db, 'visits'), visits).catch(e => console.log('Firebase save error:', e));  
    set(ref(db, 'nextId'), nextId).catch(e => console.log('Firebase save error:', e));  
  }  
}  
  
function initFirebase() {  
  if (!window._fbReady) {  
    window.addEventListener('fb-ready', () => initFirebase());  
    // Fallback: keep checking every 500ms  
    setTimeout(() => { if (!window._fbReady) return; initFirebase(); }, 2000);  
    return;  
  }  
  const { db, ref, onValue } = window._fb;  
  // Listen for realtime changes from Firebase  
  onValue(ref(db, 'visits'), (snapshot) => {  
    const data = snapshot.val();  
    if (data && Array.isArray(data)) {  
      visits = data;  
      // Update localStorage  
      try { localStorage.setItem('dt_visits', JSON.stringify(visits)); } catch {}  
      renderAll();  
      showSync();  
    }  
  });  
  onValue(ref(db, 'invoices'), (snapshot) => {  
    const data = snapshot.val();  
    if (data) {  
      try { localStorage.setItem('dt_invoices', JSON.stringify(data)); } catch {}  
    }  
  });  
  onValue(ref(db, 'quotes'), (snapshot) => {  
    const data = snapshot.val();  
    if (data && Array.isArray(data)) {  
      quotes = data;  
      try { localStorage.setItem('dt_quotes', JSON.stringify(quotes)); } catch {}  
      if (document.getElementById('tab-quote').classList.contains('active')) renderQuotes();  
    }  
  });  
  onValue(ref(db, 'plants_list'), (snapshot) => {  
    const data = snapshot.val();  
    if (data && Array.isArray(data)) {  
      savedPlants = data;  
      try { localStorage.setItem('dt_plants_list', JSON.stringify(savedPlants)); } catch {}  
    }  
  });  
  onValue(ref(db, 'clients'), (snapshot) => {  
    const data = snapshot.val();  
    if (data) {  
      clients_data = Array.isArray(data) ? data : Object.values(data);  
      try { localStorage.setItem('dt_clients', JSON.stringify(clients_data)); } catch {}  
      updateClientSelects();  
      if (document.getElementById('tab-clients').classList.contains('active')) renderClients();  
    }  
  });  
  onValue(ref(db, 'nextId'), (snapshot) => {  
    const data = snapshot.val();  
    if (data && data > nextId) {  
      nextId = data;  
      try { localStorage.setItem('dt_nextid', String(nextId)); } catch {}  
    }  
  });  
}  
  
function showSync() {  
  const badge = document.getElementById('sync-badge');  
  if (badge) { badge.style.display = 'inline-block'; setTimeout(() => badge.style.display = 'none', 2000); }  
}  
  
// **──** Helpers **──**  
function fmtDate(d) { if (!d) return '—'; const [y,m,day] = d.split('-'); return `${day}/${m}/${y}`; }  
function daysDiff(d) { if (!d) return null; return Math.floor((new Date() - new Date(d)) / 86400000); }  
function fmtQAR(n) { return (n||0).toLocaleString('en') + ' QAR'; }  
function badgeClass(s) {  
  if (s==='**مدفوع**') return 'badge-paid';  
  if (s==='**مدفوع** **جزئياً**') return 'badge-partial';  
  if (s==='**غير** **مدفوع**') return 'badge-unpaid';  
  if (s==='**مكتمل**'||s==='**موافق** **عليه**') return 'badge-done';  
  if (s==='**قيد** **التنفيذ**') return 'badge-progress';  
  if (s==='**قيد** **الموافقة**') return 'badge-pending';  
  return '';  
}  
function badge(s, small) { return s ? `<span class="badge ${small?'badge-sm':''} ${badgeClass(s)}">${s}</span>` : ''; }  
function getClients() {  
  const fromVisits = visits.map(v=>v.client).filter(Boolean);  
  const fromClients = clients_data.map(c=>c.name).filter(Boolean);  
  return [...new Set([...fromClients,...fromVisits])].sort();  
}  
function getAreas() {  
  const fromVisits = visits.map(v=>v.area).filter(Boolean);  
  const fromClients = clients_data.map(c=>c.area).filter(Boolean);  
  return [...new Set([...fromClients,...fromVisits])].sort();  
}  
function onClientSelect(name) {  
  if (!name) return;  
  document.getElementById('f-client').value = name;  
  autoFillArea(name);  
}  
  
function autoFillArea(clientName) {  
  if (!clientName) return;  
  // Find the most recent visit for this client  
  const match = visits.find(v => v.client === clientName && v.area);  
  if (match) {  
    const areaField = document.getElementById('f-area');  
    if (!areaField.value) areaField.value = match.area;  
  }  
}  
function showToast(msg) {  
  const t = document.getElementById('toast');  
  t.textContent = msg; t.classList.add('show');  
  setTimeout(() => t.classList.remove('show'), 2500);  
}  
  
// **──** Tab switching **──**  
function switchTab(tab) {  
  ['dashboard','log','clients','quote','invoice'].forEach(t => {  
    document.getElementById('tab-'+t).classList.toggle('active', t===tab);  
    document.getElementById('nav-'+t).classList.toggle('active', t===tab);  
  });  
  if (tab === 'log') renderLog();  
  if (tab === 'invoice') renderInvClients();  
  if (tab === 'quote') renderQuotes();  
  if (tab === 'clients') renderClients();  
}  
  
// **──** KPIs **──**  
function renderKPIs() {  
  const overdue = visits.filter(v => v.payStatus !== '**مدفوع**' && v.dueDate && daysDiff(v.dueDate) > 0);  
  document.getElementById('kpi-total').textContent = visits.length;  
  document.getElementById('kpi-extras').textContent = visits.reduce((s,v)=>s+(v.extraAmount||0),0).toLocaleString('en');  
  document.getElementById('kpi-done').textContent = visits.filter(v=>v.extraStatus==='**مكتمل**').length;  
  document.getElementById('kpi-unpaid').textContent = visits.filter(v=>v.payStatus==='**غير** **مدفوع**').length;  
  
  const hasOverdue = overdue.length > 0;  
  document.getElementById('badge-overdue').style.display = hasOverdue ? 'inline-block' : 'none';  
  document.getElementById('overdue-count').textContent = overdue.length;  
  const alertEl = document.getElementById('alert-overdue');  
  alertEl.style.display = hasOverdue ? 'flex' : 'none';  
  if (hasOverdue) document.getElementById('alert-overdue-text').textContent = `${overdue.length} **عميل** **متأخر** **في** **الدفع**`;  
  document.getElementById('nav-log-label').textContent = `**السجل** (${visits.length})`;  
}  
  
// **──** Visit row HTML **──**  
function visitRowHTML(v, i, showEdit=true) {  
  const overdue = v.payStatus !== '**مدفوع**' && v.dueDate && daysDiff(v.dueDate) > 0;  
  const cls = overdue ? 'overdue' : i%2===0 ? 'even' : 'odd';  
  return `  
  <div class="visit-row ${cls}">  
    <div class="visit-top">  
      <div><span class="visit-name">${v.client}</span><span class="visit-area">${v.area||''}</span></div>  
      <div class="visit-actions">  
        ${badge(v.payStatus||'**غير** **مدفوع**', true)}  
        <button class="btn-icon" style="color:var(--gm)" onclick="printVisitReport(${v.id})">📋</button>  
        <button class="btn-icon" style="color:#25D366" onclick="shareReportWhatsApp(${v.id})">💬</button>  
        ${showEdit ? `<button class="btn-icon" onclick="openEdit(${v.id})">✏️</button>` : ''}  
        <button class="btn-icon" style="color:#ddd" onclick="delVisit(${v.id})">🗑</button>  
      </div>  
    </div>  
    <div class="visit-meta">${fmtDate(v.date)} · <span class="type-tag">${v.type||'—'}</span></div>  
    <div class="visit-meta" style="color:#555;margin-top:2px">${v.work||'—'}</div>  
    ${v.notes ? `<div class="visit-notes">📝 ${v.notes}</div>` : ''}  
    ${overdue ? `<div style="font-size:11px;color:var(--red);font-weight:700;margin-top:2px">⚠️ **متأخر** ${daysDiff(v.dueDate)} **يوم** (**استحقاق**: ${fmtDate(v.dueDate)})</div>` : ''}  
    ${v.dueDate && !overdue ? `<div style="font-size:11px;color:var(--muted);margin-top:2px">**استحقاق**: ${fmtDate(v.dueDate)}</div>` : ''}  
    ${v.extra ? `<div class="visit-extra">⚙ ${v.extra} ${v.extraAmount>0?`<b>${v.extraAmount.toLocaleString('en')} QAR</b>`:''}${badge(v.extraStatus,true)}</div>` : ''}  
    ${v.nextDate ? `<div style="font-size:12px;color:var(--gm);margin-top:4px;font-weight:600">📅 **الموعد** **القادم**: ${fmtDate(v.nextDate)}${v.nextNote?' — '+v.nextNote:''}</div>` : ''}  
  </div>`;  
}  
  
// **──** Recent list **──**  
function renderRecent() {  
  const el = document.getElementById('recent-list');  
  if (!visits.length) { el.innerHTML = '<div class="empty"><div class="icon">🌿</div><p>**لا** **توجد** **زيارات** **بعد**</p></div>'; return; }  
  el.innerHTML = visits.slice(0,5).map((v,i) => visitRowHTML(v,i)).join('');  
}  
  
// **──** Log **──**  
function renderLog() {  
  const search = document.getElementById('search-input').value;  
  const fc = document.getElementById('filter-client').value;  
  const ft = document.getElementById('filter-type').value;  
  const fp = document.getElementById('filter-pay').value;  
  const fm = document.getElementById('filter-month').value;  
  const filtered = visits.filter(v => {  
    if (search && !v.client.includes(search) && !(v.area||'').includes(search) && !(v.type||'').includes(search) && !(v.work||'').includes(search)) return false;  
    if (fc && v.client !== fc) return false;  
    if (ft && v.type !== ft) return false;  
    if (fp && v.payStatus !== fp) return false;  
    if (fm && v.date) {  
      let vMonth = '';  
      if (v.date.includes('-')) {  
        vMonth = v.date.substring(0,7); // YYYY-MM-DD  
      } else if (v.date.includes('/')) {  
        const parts = v.date.split('/');  
        // DD/MM/YYYY → YYYY-MM  
        vMonth = parts[2] + '-' + parts[1].padStart(2,'0');  
      }  
      if (vMonth !== fm) return false;  
    }  
    return true;  
  });  
  document.getElementById('log-count').textContent = filtered.length + ' **زيارة**';  
  const el = document.getElementById('log-list');  
  if (!filtered.length) { el.innerHTML = '<div class="empty"><div class="icon">🌿</div><p>**لا** **توجد** **زيارات**</p></div>'; return; }  
  el.innerHTML = filtered.map((v,i) => visitRowHTML(v,i)).join('');  
}  
  
function clearFilters() {  
  document.getElementById('search-input').value = '';  
  document.getElementById('filter-client').value = '';  
  document.getElementById('filter-type').value = '';  
  document.getElementById('filter-pay').value = '';  
  document.getElementById('filter-month').value = '';  
  renderLog();  
}  
  
function updateClientSelects() {  
  const clients = getClients();  
  // datalist  
  document.getElementById('clients-list').innerHTML = clients.map(c=>`<option value="${c}">`).join('');  
  const csel = document.getElementById('f-client-select');  
  if (csel) {  
    const cv = csel.value;  
    csel.innerHTML = '<option value="">**اختر** **عميل** **موجود**...</option>' + clients.map(c=>`<option value="${c}"${c===cv?' selected':''}>${c}</option>`).join('');  
  }  
  const areas = getAreas();  
  const al = document.getElementById('areas-list');  
  if (al) al.innerHTML = areas.map(a=>`<option value="${a}">`).join('');  
  const asel = document.getElementById('f-area-select');  
  if (asel) {  
    const av = asel.value;  
    asel.innerHTML = '<option value="">**اختر** **منطقة**...</option>' + areas.map(a=>`<option value="${a}"${a===av?' selected':''}>${a}</option>`).join('');  
  }  
  // Build last 12 months  
  const monthSel = document.getElementById('filter-month');  
  if (monthSel) {  
    const arMonths = ['**يناير**','**فبراير**','**مارس**','**أبريل**','**مايو**','**يونيو**','**يوليو**','**أغسطس**','**سبتمبر**','**أكتوبر**','**نوفمبر**','**ديسمبر**'];  
    const now = new Date(); const cur = monthSel.value;  
    let opts = '<option value="">**كل** **الأشهر**</option>';  
    for (let i = 0; i < 12; i++) {  
      const d = new Date(now.getFullYear(), now.getMonth() - i, 1);  
      const val = d.getFullYear() + '-' + String(d.getMonth()+1).padStart(2,'0');  
      const label = arMonths[d.getMonth()] + ' ' + d.getFullYear();  
      opts += `<option value="${val}"${val===cur?' selected':''}>${label}</option>`;  
    }  
    monthSel.innerHTML = opts;  
  }  
  // filter-client  
  const fc = document.getElementById('filter-client');  
  const fv = fc.value;  
  fc.innerHTML = '<option value="">**كل** **العملاء**</option>' + clients.map(c=>`<option${c===fv?' selected':''}>${c}</option>`).join('');  
  // inv-client  
  const ic = document.getElementById('inv-client');  
  const iv = ic.value;  
  ic.innerHTML = '<option value="">**اختر** **العميل**...</option>' + clients.map(c=>`<option${c===iv?' selected':''}>${c}</option>`).join('');  
}  
  
// **──** Modal **──**  
function openAdd() {  
  editId = null;  
  document.getElementById('modal-title').textContent = '➕ **إضافة** **زيارة** **جديدة**';  
  document.getElementById('modal-save-btn').textContent = '✚ **أضف** **للسجل**';  
  document.getElementById('f-client').value = '';  
  const csel=document.getElementById('f-client-select');if(csel)csel.value='';  
  const asel=document.getElementById('f-area-select');if(asel)asel.value='';  
  document.getElementById('f-area').value = '';  
  document.getElementById('f-date').value = TODAY;  
  document.getElementById('f-type').value = '';  
  document.getElementById('f-work').value = '';  
  document.getElementById('f-notes').value = '';  
  document.getElementById('f-extra').value = '';  
  document.getElementById('f-extra-amount').value = '';  
  document.getElementById('f-extra-status').value = '';  
  document.getElementById('f-pay-status').value = '**غير** **مدفوع**';  
  document.getElementById('f-due-date').value = '';  
  document.getElementById('f-paid-amount').value = '';  
  document.getElementById('paid-amount-field').style.display = 'none';  
  document.getElementById('f-next-date').value = '';  
  document.getElementById('f-next-note').value = '';  
  document.getElementById('f-client').classList.remove('error');  
  document.getElementById('f-date').classList.remove('error');  
  document.getElementById('modal').classList.add('open');  
}  
  
function openEdit(id) {  
  const v = visits.find(x => x.id === id);  
  if (!v) return;  
  editId = id;  
  document.getElementById('modal-title').textContent = '✏️ **تعديل** **الزيارة**';  
  document.getElementById('modal-save-btn').textContent = '💾 **حفظ** **التعديل**';  
  document.getElementById('f-client').value = v.client||'';  
  const ces=document.getElementById('f-client-select');if(ces)ces.value=v.client||'';  
  document.getElementById('f-area').value = v.area||'';  
  const aes=document.getElementById('f-area-select');if(aes)aes.value=v.area||'';  
  document.getElementById('f-date').value = v.date||TODAY;  
  document.getElementById('f-type').value = v.type||'';  
  document.getElementById('f-work').value = v.work||'';  
  document.getElementById('f-notes').value = v.notes||'';  
  document.getElementById('f-extra').value = v.extra||'';  
  document.getElementById('f-extra-amount').value = v.extraAmount||'';  
  document.getElementById('f-extra-status').value = v.extraStatus||'';  
  document.getElementById('f-pay-status').value = v.payStatus||'**غير** **مدفوع**';  
  document.getElementById('f-due-date').value = v.dueDate||'';  
  document.getElementById('f-paid-amount').value = v.paidAmount||'';  
  document.getElementById('f-next-date').value = v.nextDate||'';  
  document.getElementById('f-next-note').value = v.nextNote||'';  
  document.getElementById('paid-amount-field').style.display = v.payStatus==='**مدفوع** **جزئياً**' ? 'block' : 'none';  
  document.getElementById('f-client').classList.remove('error');  
  document.getElementById('f-date').classList.remove('error');  
  document.getElementById('modal').classList.add('open');  
}  
  
function closeModal() { document.getElementById('modal').classList.remove('open'); }  
document.getElementById('modal').addEventListener('click', e => { if (e.target === e.currentTarget) closeModal(); });  
  
function togglePaidAmount() {  
  document.getElementById('paid-amount-field').style.display =  
    document.getElementById('f-pay-status').value === '**مدفوع** **جزئياً**' ? 'block' : 'none';  
}  
  
function saveVisit() {  
  const client = document.getElementById('f-client').value.trim();  
  const date = document.getElementById('f-date').value;  
  let ok = true;  
  document.getElementById('f-client').classList.toggle('error', !client);  
  document.getElementById('f-date').classList.toggle('error', !date);  
  if (!client || !date) return;  
  
  const data = {  
    id: editId || nextId,  
    client, date,  
    area: document.getElementById('f-area').value.trim(),  
    type: document.getElementById('f-type').value,  
    work: document.getElementById('f-work').value.trim(),  
    notes: document.getElementById('f-notes').value.trim(),  
    extra: document.getElementById('f-extra').value.trim(),  
    extraAmount: parseFloat(document.getElementById('f-extra-amount').value)||0,  
    extraStatus: document.getElementById('f-extra-status').value,  
    payStatus: document.getElementById('f-pay-status').value,  
    dueDate: document.getElementById('f-due-date').value,  
    paidAmount: parseFloat(document.getElementById('f-paid-amount').value)||0,  
    nextDate: document.getElementById('f-next-date').value,  
    nextNote: document.getElementById('f-next-note').value.trim(),  
  };  
  
  if (editId) {  
    visits = visits.map(v => v.id===editId ? data : v);  
    showToast('✅ **تم** **تعديل** **الزيارة**!');  
  } else {  
    visits.unshift(data);  
    nextId++;  
    showToast('✅ **تمت** **إضافة** **الزيارة** **وحُفظت**!');  
  }  
  saveData(); closeModal(); renderAll();  
  switchTab('log');  
}  
  
function delVisit(id) {  
  if (!confirm('**حذف** **هذه** **الزيارة؟**')) return;  
  visits = visits.filter(v => v.id !== id);  
  saveData(); renderAll();  
  showToast('🗑 **تم** **الحذف**');  
}  
  
// **──** Export CSV **──**  
function exportCSV() {  
  if (!visits.length) { alert('**لا** **توجد** **بيانات**'); return; }  
  const h = ['#','**العميل**','**المنطقة**','**التاريخ**','**نوع** **العمل**','**الأعمال** **المنجزة**','**ملاحظات**','**أعمال** **إضافية**','**مبلغ** **الإضافية**','**حالة** **الإضافية**','**حالة** **الدفع**','**تاريخ** **الاستحقاق**'];  
  const r = visits.map((v,i) => [visits.length-i,v.client,v.area,v.date,v.type,v.work,v.notes||'',v.extra||'',v.extraAmount||0,v.extraStatus||'',v.payStatus||'',v.dueDate||'']);  
  const csv = '\uFEFF' + [h,...r].map(row=>row.map(c=>`"${c}"`).join(',')).join('\n');  
  const a = document.createElement('a');  
  a.href = URL.createObjectURL(new Blob([csv],{type:'text/csv;charset=utf-8'}));  
  a.download = `**سجل**_**الزيارات**_${TODAY}.csv`; a.click();  
}  
  
// **──** Invoice **──**  
function setInvType(type) {  
  invType = type; selectedVisits = [];  
  document.getElementById('inv-monthly-btn').classList.toggle('active', type==='monthly');  
  document.getElementById('inv-single-btn').classList.toggle('active', type==='single');  
  document.getElementById('inv-fee-label').textContent = type==='monthly' ? '**الباقة** **الشهرية** (QAR)' : '**سعر** **الزيارة** (QAR)';  
  document.getElementById('inv-visits-label').textContent = type==='monthly' ? '**اختر** **الزيارات**:' : '**اختر** **زيارة** **واحدة**:';  
  renderInvVisits();  
}  
  
function renderInvClients() {  
  const clients = getClients();  
  const el = document.getElementById('inv-client');  
  const cv = el.value;  
  el.innerHTML = '<option value="">**اختر** **العميل**...</option>' + clients.map(c=>`<option${c===cv?' selected':''}>${c}</option>`).join('');  
}  
  
function buildInvMonthOptions() {  
  const arMonths = ['**يناير**','**فبراير**','**مارس**','**أبريل**','**مايو**','**يونيو**','**يوليو**','**أغسطس**','**سبتمبر**','**أكتوبر**','**نوفمبر**','**ديسمبر**'];  
  const now = new Date();  
  let opts = '<option value="">**اختر** **الشهر**...</option>';  
  for (let i = 0; i < 12; i++) {  
    const d = new Date(now.getFullYear(), now.getMonth() - i, 1);  
    const val = d.getFullYear() + '-' + String(d.getMonth()+1).padStart(2,'0');  
    opts += `<option value="${val}">${arMonths[d.getMonth()]} ${d.getFullYear()}</option>`;  
  }  
  return opts;  
}  
  
function autoSelectMonthVisits() {  
  const client = document.getElementById('inv-client').value;  
  const month = document.getElementById('inv-month').value;  
  if (!client || !month) return;  
  // Get client data for visits per month  
  const clientData = clients_data.find(c => c.name === client);  
  // Filter visits for this client and month  
  const monthVisits = visits.filter(v => {  
    if (v.client !== client) return false;  
    let vMonth = '';  
    if (v.date && v.date.includes('-')) vMonth = v.date.substring(0,7);  
    else if (v.date && v.date.includes('/')) {  
      const parts = v.date.split('/');  
      vMonth = parts[2] + '-' + parts[1].padStart(2,'0');  
    }  
    return vMonth === month;  
  });  
  // Auto-select all visits for this month  
  selectedVisits = monthVisits.map(v => v.id);  
  renderInvVisits();  
}  
  
function onInvClientChange() {  
  selectedVisits = [];  
  // Auto-generate invoice number for this client  
  const client = document.getElementById('inv-client').value;  
  if (client) {  
    // Show month selector  
    const monthField = document.getElementById('inv-month-field');  
    if (monthField) {  
      monthField.style.display = 'block';  
      document.getElementById('inv-month').innerHTML = buildInvMonthOptions();  
    }  
    // Fill monthly fee from client data  
    const clientData = clients_data.find(c => c.name === client);  
    if (clientData && clientData.monthly) {  
      document.getElementById('inv-fee').value = clientData.monthly;  
    }  
    // Count existing invoices for this client from localStorage  
    let clientInvCount = 0;  
    try {  
      const allInv = JSON.parse(localStorage.getItem('dt_invoices') || '{}');  
      clientInvCount = allInv[client] || 0;  
    } catch {}  
    const nextNum = String(clientInvCount + 1).padStart(3, '0');  
    // Create short client code from first letters  
    const arToEn = {'**ا**':'A','**أ**':'A','**إ**':'A','**آ**':'A','**ب**':'B','**ت**':'T','**ث**':'TH','**ج**':'J','**ح**':'H','**خ**':'KH','**د**':'D','**ذ**':'Z','**ر**':'R','**ز**':'Z','**س**':'S','**ش**':'SH','**ص**':'S','**ض**':'D','**ط**':'T','**ظ**':'Z','**ع**':'A','**غ**':'GH','**ف**':'F','**ق**':'Q','**ك**':'K','**ل**':'L','**م**':'M','**ن**':'N','**ه**':'H','**و**':'W','**ي**':'Y','**ى**':'Y','**ة**':'H','**ء**':'A'};  
    const code = client.split(' ').map(w => arToEn[w[0]] || w[0].toUpperCase()).join('').substring(0,3).toUpperCase();  
    document.getElementById('inv-num').value = `${code}-INV-${nextNum}`;  
  } else {  
    const mf = document.getElementById('inv-month-field');  
    if (mf) mf.style.display = 'none';  
  }  
  renderInvVisits();  
}  
  
function renderInvVisits() {  
  const client = document.getElementById('inv-client').value;  
  const section = document.getElementById('inv-visits-section');  
  if (!client) { section.style.display = 'none'; updateInvButtons(); return; }  
  section.style.display = 'block';  
  const cVisits = visits.filter(v => v.client === client);  
  const el = document.getElementById('inv-visits-list');  
  if (!cVisits.length) { el.innerHTML = '<div style="color:var(--muted);font-size:13px;padding:12px 0;text-align:center">**لا** **توجد** **زيارات** **لهذا** **العميل**</div>'; return; }  
  el.innerHTML = cVisits.map(v => {  
    const sel = selectedVisits.includes(v.id);  
    const isRound = invType === 'single';  
    return `<div class="visit-select-item ${sel?'selected':''}" onclick="toggleInvVisit(${v.id})">  
      <div class="check ${isRound?'round':''} ${sel?'checked':''}">✓</div>  
      <div style="flex:1">  
        <div style="font-weight:600;font-size:14px">${fmtDate(v.date)} — <span style="color:var(--gm)">${v.type}</span></div>  
        <div style="font-size:12px;color:#888">${v.work||'—'}</div>  
      </div>  
      ${v.extraAmount>0?`<div style="font-size:12px;color:var(--or);font-weight:700">${v.extraAmount.toLocaleString('en')} QAR</div>`:''}  
    </div>`;  
  }).join('');  
  updateInvSummary();  
  updateInvButtons();  
}  
  
function toggleInvVisit(id) {  
  if (invType === 'single') { selectedVisits = selectedVisits.includes(id) ? [] : [id]; }  
  else { selectedVisits = selectedVisits.includes(id) ? selectedVisits.filter(x=>x!==id) : [...selectedVisits,id]; }  
  renderInvVisits();  
}  
  
function updateInvSummary() {  
  const selData = visits.filter(v => selectedVisits.includes(v.id));  
  const fee = parseFloat(document.getElementById('inv-fee').value)||0;  
  const extTotal = selData.reduce((s,v)=>s+(v.extraAmount||0),0);  
  const total = invType==='monthly' ? fee+extTotal : selData.length===1 ? fee+(selData[0]?.extraAmount||0) : 0;  
  const summary = document.getElementById('inv-summary');  
  if (!selData.length) { summary.style.display='none'; return; }  
  summary.style.display = 'block';  
  if (invType==='monthly') {  
    document.getElementById('inv-sum-fee-label').textContent = `**الباقة** (${selData.length} **زيارات**)`;  
    document.getElementById('inv-sum-fee').textContent = fmtQAR(fee);  
    const extRow = document.getElementById('inv-sum-ext-row');  
    extRow.style.display = extTotal > 0 ? 'flex' : 'none';  
    document.getElementById('inv-sum-ext').textContent = fmtQAR(extTotal);  
  } else {  
    document.getElementById('inv-sum-fee-label').textContent = '**سعر** **الزيارة**';  
    document.getElementById('inv-sum-fee').textContent = fmtQAR(fee);  
    const extRow = document.getElementById('inv-sum-ext-row');  
    const ea = selData[0]?.extraAmount||0;  
    extRow.style.display = ea > 0 ? 'flex' : 'none';  
    document.getElementById('inv-sum-ext').textContent = fmtQAR(ea);  
  }  
  document.getElementById('inv-sum-total').textContent = fmtQAR(total);  
}  
  
function updateInvButtons() {  
  const canPrint = invType==='monthly' ? selectedVisits.length>0 : selectedVisits.length===1;  
  document.getElementById('inv-buttons').style.display = canPrint ? 'block' : 'none';  
}  
  
function buildInvoiceHTML(forPrint) {  
  const client = document.getElementById('inv-client').value;  
  const invNum = document.getElementById('inv-num').value;  
  const fee = parseFloat(document.getElementById('inv-fee').value)||0;  
  const due = document.getElementById('inv-due').value;  
  const payStatus = document.getElementById('inv-pay-status').value;  
  const selData = visits.filter(v => selectedVisits.includes(v.id));  
  const ext = selData.reduce((s,v)=>s+(v.extraAmount||0),0);  
  const total = invType==='monthly' ? fee+ext : fee+(selData[0]?.extraAmount||0);  
  const payBadge = payStatus==='**مدفوع**' ? `background:#D8F3DC;color:#2D6A4F` : `background:#FADBD8;color:#C0392B`;  
  
  const rows = invType==='monthly'  
    ? selData.map((v,i) => `<tr style="background:${i%2===0?'#fff':'#f7f7f7'}">  
        <td style="padding:8px 12px;text-align:center;border-bottom:1px solid #eee;color:${GM};font-weight:700">${i+1}</td>  
        <td style="padding:8px 12px;text-align:right;border-bottom:1px solid #eee;font-weight:600">**زيارة** ${i+1}</td>  
        <td style="padding:8px 12px;text-align:right;border-bottom:1px solid #eee;font-size:11px;color:#555">${v.work||'—'}</td>  
        <td style="padding:8px 12px;text-align:center;border-bottom:1px solid #eee;font-size:11px">${fmtDate(v.date)}</td>  
        <td style="padding:8px 12px;text-align:right;border-bottom:1px solid #eee;font-size:11px;color:${OR}">${v.extra||'—'}</td>  
        <td style="padding:8px 12px;text-align:center;border-bottom:1px solid #eee;font-weight:700;color:${v.extraAmount?OR:'#ccc'}">${v.extraAmount?v.extraAmount.toLocaleString('en')+' QAR':'—'}</td>  
      </tr>`).join('')  
    : `<tr>  
        <td style="padding:12px;text-align:center;color:${GM};font-weight:700">1</td>  
        <td style="padding:12px;text-align:right"><div style="font-weight:700">${selData[0]?.type||'—'}</div><div style="font-size:11px;color:#555;margin-top:3px">${selData[0]?.work||'—'}</div></td>  
        <td style="padding:12px;text-align:center;font-weight:900;color:${GM};font-size:14px">${fee.toLocaleString('en')} QAR</td>  
      </tr>${(selData[0]?.extraAmount||0)>0?`<tr style="background:#f7f7f7">  
        <td style="padding:12px;text-align:center;color:${OR};font-weight:700">2</td>  
        <td style="padding:12px;text-align:right"><div style="font-weight:700;color:${OR}">**أعمال** **إضافية**</div><div style="font-size:11px;color:#555">${selData[0]?.extra||''}</div></td>  
        <td style="padding:12px;text-align:center;font-weight:900;color:${OR};font-size:14px">${(selData[0]?.extraAmount||0).toLocaleString('en')} QAR</td>  
      </tr>`:''}`;  
  
  const printBtn = forPrint ? '' : `<button onclick="window.print()" style="display:block;width:200px;margin:20px auto;padding:12px;background:#1B4332;color:white;border:none;border-radius:10px;font-size:15px;font-weight:700;cursor:pointer;font-family:Arial">🖨 **طباعة** / PDF</button>`;  
  const payColor = payStatus==='**مدفوع**'?'#2D6A4F':payStatus==='**مدفوع** **جزئياً**'?'#D4AC0D':'#C0392B';  
  const payBg    = payStatus==='**مدفوع**'?'#D8F3DC':payStatus==='**مدفوع** **جزئياً**'?'#FFF9E6':'#FADBD8';  
  
  const visitRows = invType==='monthly'  
    ? selData.map((v,i)=>`  
      <tr>  
        <td style="padding:10px 16px;border-bottom:1px solid #f0f0f0;color:#1B4332;font-weight:700;font-size:13px;text-align:center">${i+1}</td>  
        <td style="padding:10px 16px;border-bottom:1px solid #f0f0f0;font-weight:600;font-size:13px">${fmtDate(v.date)}</td>  
        <td style="padding:10px 16px;border-bottom:1px solid #f0f0f0;font-size:12px;color:#555">${v.type||'—'}</td>  
        <td style="padding:10px 16px;border-bottom:1px solid #f0f0f0;font-size:12px;color:#555">${v.work||'—'}</td>  
        <td style="padding:10px 16px;border-bottom:1px solid #f0f0f0;font-size:12px;color:#E07B39">${v.extra||'—'}</td>  
        <td style="padding:10px 16px;border-bottom:1px solid #f0f0f0;font-weight:700;color:${v.extraAmount?'#E07B39':'#ccc'};text-align:left">${v.extraAmount?v.extraAmount.toLocaleString('en')+' QAR':'—'}</td>  
      </tr>`).join('')  
    : `<tr>  
        <td style="padding:12px 16px;color:#2D6A4F;font-weight:700;text-align:center">1</td>  
        <td style="padding:12px 16px;font-weight:600">${selData[0]?.type||'—'}</td>  
        <td style="padding:12px 16px;font-size:12px;color:#555" colspan="2">${selData[0]?.work||'—'}</td>  
        <td style="padding:12px 16px"></td>  
        <td style="padding:12px 16px;font-weight:700;color:#2D6A4F;text-align:left">${fee.toLocaleString('en')} QAR</td>  
      </tr>${(selData[0]?.extraAmount||0)>0?`<tr style="background:#FEF0E7">  
        <td style="padding:12px 16px;color:#E07B39;font-weight:700;text-align:center">2</td>  
        <td style="padding:12px 16px;font-weight:600;color:#E07B39">**أعمال** **إضافية**</td>  
        <td style="padding:12px 16px;font-size:12px;color:#555" colspan="2">${selData[0]?.extra||''}</td>  
        <td style="padding:12px 16px"></td>  
        <td style="padding:12px 16px;font-weight:700;color:#E07B39;text-align:left">${(selData[0]?.extraAmount||0).toLocaleString('en')} QAR</td>  
      </tr>`:''}`;  
  
  return `<!DOCTYPE html><html dir="rtl" lang="ar"><head><meta charset="UTF-8">  
  <title>**فاتورة** ${invNum}</title>  
  <style>  
    *{margin:0;padding:0;box-sizing:border-box}  
    body{font-family:Arial,sans-serif;direction:rtl;background:#f4f6f4;padding:${forPrint?'0':'24px'}}  
    .page{max-width:700px;margin:0 auto;background:white;${forPrint?'':'border-radius:16px;overflow:hidden;box-shadow:0 8px 32px rgba(0,0,0,.12)'}}  
    @media print{body{background:white;padding:0}.page{box-shadow:none;border-radius:0}button{display:none!important}@page{margin:10mm}body{-webkit-print-color-adjust:exact;print-color-adjust:exact}}  
  </style>  
  
  </head><body>  
  ${printBtn}  
  <div class="page">  
  
```  
<!-- Header -->  
<div style="background:#1B4332;padding:28px 32px;display:flex;justify-content:space-between;align-items:center">  
  <div>  
    <div style="color:white;font-size:26px;font-weight:900;letter-spacing:-0.5px">🌳 Dr.Tree</div>  
    <div style="color:#52B788;font-size:11px;letter-spacing:3px;margin-top:5px;text-transform:uppercase">Garden & Tree Services</div>  
    <div style="color:#6aaa87;font-size:10px;margin-top:3px">+974 XXXX XXXX · info@drtree.qa</div>  
  </div>  
  <div style="text-align:center">  
    <div style="background:#D4AC0D;color:#1B4332;padding:12px 20px;border-radius:10px;display:inline-block">  
      <div style="font-size:9px;font-weight:700;text-transform:uppercase;letter-spacing:1px;margin-bottom:4px">${invType==='monthly'?'**فاتورة** **شهرية**':'**فاتورة** **زيارة**'}</div>  
      <div style="font-size:22px;font-weight:900">${invNum}</div>  
      <div style="font-size:10px;color:#5a4200;margin-top:3px">${new Date().toLocaleDateString('ar-QA')}</div>  
    </div>  
  </div>  
</div>  
  
<!-- Accent bar -->  
<div style="height:4px;background:linear-gradient(to left,#52B788,#D4AC0D,#52B788)"></div>  
  
<!-- Client info -->  
<div style="display:flex;background:#f8faf8;border-bottom:1px solid #e8ede8">  
  <div style="flex:1.5;padding:18px 24px;border-left:1px solid #e8ede8">  
    <div style="font-size:9px;color:#999;font-weight:700;text-transform:uppercase;letter-spacing:1.5px;margin-bottom:6px">**مقدم** **إلى**</div>  
    <div style="font-size:18px;font-weight:700;color:#1B4332">${client}</div>  
  </div>  
  <div style="flex:1;padding:18px 24px;border-left:1px solid #e8ede8">  
    <div style="font-size:9px;color:#999;font-weight:700;text-transform:uppercase;letter-spacing:1.5px;margin-bottom:6px">**الاستحقاق**</div>  
    <div style="font-size:14px;font-weight:700;color:${due?'#C0392B':'#888'}">${due?fmtDate(due):'**عند** **الاستلام**'}</div>  
  </div>  
  <div style="flex:1;padding:18px 24px">  
    <div style="font-size:9px;color:#999;font-weight:700;text-transform:uppercase;letter-spacing:1.5px;margin-bottom:6px">**حالة** **الدفع**</div>  
    <div style="display:inline-block;padding:4px 12px;border-radius:20px;font-size:12px;font-weight:700;background:${payBg};color:${payColor}">${payStatus}</div>  
  </div>  
</div>  
  
<!-- Table header -->  
<div style="background:#2D6A4F;padding:10px 16px 10px 0">  
  <table style="width:100%;border-collapse:collapse;font-size:11px">  
    <tr>  
      <th style="color:white;padding:0 16px;text-align:center;width:5%">#</th>  
      <th style="color:white;padding:0 16px;text-align:right;width:13%">**التاريخ**</th>  
      <th style="color:white;padding:0 16px;text-align:right;width:14%">**نوع** **العمل**</th>  
      <th style="color:white;padding:0 16px;text-align:right">**الأعمال** **المنجزة**</th>  
      <th style="color:white;padding:0 16px;text-align:right">**الأعمال** **الإضافية**</th>  
      <th style="color:#D4AC0D;padding:0 16px;text-align:left;width:14%">**المبلغ**</th>  
    </tr>  
  </table>  
</div>  
  
<!-- Table rows -->  
<table style="width:100%;border-collapse:collapse;font-size:12px">  
  <tbody>${visitRows}</tbody>  
</table>  
  
<!-- Package row -->  
${invType==='monthly'?`  
<div style="background:#D8F3DC;padding:14px 24px;display:flex;justify-content:space-between;align-items:center;border-top:2px solid #52B788">  
  <span style="font-weight:700;color:#1B4332;font-size:13px">**الباقة** **الشهرية** **الثابتة** — ${selData.length} **زيارات**</span>  
  <span style="background:#FFF9E6;color:#D4AC0D;border:2px solid #D4AC0D;padding:5px 14px;border-radius:6px;font-weight:900;font-size:15px">${fee.toLocaleString('en')} QAR</span>  
</div>`:''}  
  
<!-- Totals -->  
<div style="padding:20px 24px;background:#fafafa;border-top:1px solid #eee">  
  ${invType==='monthly'?`  
  <div style="display:flex;justify-content:space-between;align-items:center;padding:6px 0;font-size:13px">  
    <span style="color:#555">**الباقة** **الشهرية**</span><span style="font-weight:700;color:#2D6A4F">QAR ${fee.toLocaleString('en')}</span>  
  </div>  
  <div style="display:flex;justify-content:space-between;align-items:center;padding:6px 0;font-size:13px">  
    <span style="color:#555">**الأعمال** **الإضافية**</span><span style="font-weight:700;color:#E07B39">QAR ${ext.toLocaleString('en')}</span>  
  </div>`:`  
  <div style="display:flex;justify-content:space-between;align-items:center;padding:6px 0;font-size:13px">  
    <span style="color:#555">**سعر** **الزيارة**</span><span style="font-weight:700;color:#2D6A4F">QAR ${fee.toLocaleString('en')}</span>  
  </div>  
  ${(selData[0]?.extraAmount||0)>0?`<div style="display:flex;justify-content:space-between;align-items:center;padding:6px 0;font-size:13px">  
    <span style="color:#555">**أعمال** **إضافية**</span><span style="font-weight:700;color:#E07B39">QAR ${(selData[0]?.extraAmount||0).toLocaleString('en')}</span>  
  </div>`:''}`}  
  <div style="height:1px;background:#e0e0e0;margin:12px 0"></div>  
  <div style="background:#1B4332;border-radius:10px;padding:14px 20px;display:flex;justify-content:space-between;align-items:center">  
    <span style="color:white;font-size:14px;font-weight:700">💰 **الإجمالي** **المستحق**</span>  
    <span style="color:#D4AC0D;font-size:20px;font-weight:900">QAR ${total.toLocaleString('en')}</span>  
  </div>  
</div>  
  
<!-- Footer -->  
<div style="background:#1B4332;padding:16px 24px;display:flex;justify-content:space-between;align-items:center">  
  <div style="color:#52B788;font-size:11px">Dr.Tree · +974 XXXX XXXX · info@drtree.qa</div>  
  <div style="color:#6aaa87;font-size:10px">**صادرة** **بتاريخ** ${new Date().toLocaleDateString('ar-QA')}</div>  
</div>  
```  
  
  </div>  
  </body></html>`;  
}  
  
function markVisitsPaid() {  
if (!selectedVisits.length) return;  
visits = visits.map(v => {  
if (selectedVisits.includes(v.id)) {  
return { …v, payStatus: ‘**مدفوع**’, paidAmount: v.extraAmount || 0 };  
}  
return v;  
});  
saveData();  
showToast(‘✅ **تم** **تحديث** **حالة** **الدفع** **للزيارات**’);  
renderAll();  
}  
  
function doPrint() {  
const html = buildInvoiceHTML(true);  
saveInvoiceNum();  
markVisitsPaid();  
const w = window.open(’’,’_blank’);  
w.document.write(html); w.document.close(); w.focus();  
setTimeout(() => { w.print(); w.close(); }, 400);  
}  
  
function saveInvoiceNum() {  
const client = document.getElementById(‘inv-client’).value;  
if (!client) return;  
try {  
const allInv = JSON.parse(localStorage.getItem(‘dt_invoices’) || ‘{}’);  
allInv[client] = (allInv[client] || 0) + 1;  
localStorage.setItem(‘dt_invoices’, JSON.stringify(allInv));  
if (window._fbReady) {  
const { db, ref, set } = window._fb;  
set(ref(db, ‘invoices’), allInv).catch(e => console.log(e));  
}  
} catch {}  
}  
  
function shareInvoiceWhatsApp() {  
const client = document.getElementById(‘inv-client’).value;  
const invNum = document.getElementById(‘inv-num’).value;  
const fee = parseFloat(document.getElementById(‘inv-fee’).value)||0;  
const selData = visits.filter(v => selectedVisits.includes(v.id));  
const ext = selData.reduce((s,v)=>s+(v.extraAmount||0),0);  
const total = invType===‘monthly’ ? fee+ext : fee+(selData[0]?.extraAmount||0);  
const due = document.getElementById(‘inv-due’).value;  
let msg = `🌳 *Dr.Tree — **فاتورة** **خدمات***\n\n`;  
msg += `**رقم** **الفاتورة**: *${invNum}*\n`;  
msg += `**العميل**: *${client}*\n`;  
msg += `**التاريخ**: ${new Date().toLocaleDateString('ar-QA')}\n\n`;  
msg += `📋 ***تفصيل** **الخدمات**:*\n`;  
if (invType === ‘monthly’) {  
selData.forEach((v,i) => {  
msg += `• **زيارة** ${i+1} — ${fmtDate(v.date)} (${v.type||'—'})\n`;  
if (v.extra && v.extraAmount > 0) msg += `  ⚙ ${v.extra}: ${v.extraAmount.toLocaleString('en')} QAR\n`;  
});  
msg += `\n• **الباقة** **الشهرية**: ${fee.toLocaleString('en')} QAR\n`;  
if (ext > 0) msg += `• **الأعمال** **الإضافية**: ${ext.toLocaleString('en')} QAR\n`;  
} else {  
const v = selData[0];  
msg += `• ${v?.type||'—'} — ${fmtDate(v?.date)}\n`;  
msg += `• **سعر** **الزيارة**: ${fee.toLocaleString('en')} QAR\n`;  
if ((v?.extraAmount||0) > 0) msg += `• **أعمال** **إضافية**: ${v.extraAmount.toLocaleString('en')} QAR\n`;  
}  
msg += `\n💰 ***الإجمالي** **المستحق**: ${total.toLocaleString('en')} QAR*`;  
if (due) msg += `\n📅 **تاريخ** **الاستحقاق**: ${fmtDate(due)}`;  
msg += `\n\n**شكراً** **لثقتكم** **بخدماتنا** 🌿`;  
window.open(‘https://wa.me/?text=’ + encodeURIComponent(msg), ‘_blank’);  
}  
  
function shareReportWhatsApp(id) {  
const v = visits.find(x => x.id === id);  
if (!v) return;  
let msg = `🌳 *Dr.Tree — **تقرير** **زيارة***\n\n`;  
msg += `👤 **العميل**: *${v.client}*`;  
if (v.area) msg += ` — ${v.area}`;  
msg += `\n📅 **التاريخ**: ${fmtDate(v.date)}\n`;  
msg += `🔧 **نوع** **العمل**: ${v.type||'—'}\n\n`;  
if (v.work) msg += `📋 ***الأعمال** **المنجزة**:*\n${v.work}\n\n`;  
if (v.notes) msg += `📝 ***ملاحظات**:*\n${v.notes}\n\n`;  
if (v.extra) {  
msg += `⚙ ***أعمال** **إضافية**:*\n${v.extra}`;  
if (v.extraAmount > 0) msg += ` — ${v.extraAmount.toLocaleString('en')} QAR`;  
if (v.extraStatus) msg += ` (${v.extraStatus})`;  
msg += `\n\n`;  
}  
if (v.nextDate) msg += `📅 **الموعد** **القادم**: ${fmtDate(v.nextDate)}${v.nextNote?' — '+v.nextNote:''}\n\n`;  
msg += `**شكراً** **لثقتكم** **بخدماتنا** 🌿`;  
window.open(‘https://wa.me/?text=’ + encodeURIComponent(msg), ‘_blank’);  
}  
  
function generatePDF(id) { if (typeof id === ‘number’) printVisitReport(id); }  
  
function doExportHTML() {  
const client = document.getElementById(‘inv-client’).value;  
const invNum = document.getElementById(‘inv-num’).value;  
const html = buildInvoiceHTML(false);  
const a = document.createElement(‘a’);  
a.href = URL.createObjectURL(new Blob([html],{type:‘text/html;charset=utf-8’}));  
saveInvoiceNum();  
markVisitsPaid();  
a.download = `**فاتورة**_${invNum}_${client}_${TODAY}.html`;  
a.click();  
showToast(‘📄 **تم** **تصدير** **الفاتورة**!’);  
}  
  
// **──** Upcoming visits **──**  
function renderUpcoming() {  
const upcoming = visits  
.filter(v => v.nextDate && v.nextDate >= TODAY)  
.sort((a,b) => a.nextDate.localeCompare(b.nextDate))  
.slice(0, 5);  
const card = document.getElementById(‘upcoming-card’);  
const list = document.getElementById(‘upcoming-list’);  
if (!upcoming.length) { card.style.display = ‘none’; return; }  
card.style.display = ‘block’;  
const today = new Date(); today.setHours(0,0,0,0);  
list.innerHTML = upcoming.map((v,i) => {  
const d = new Date(v.nextDate);  
const diff = Math.round((d - today) / 86400000);  
const isToday = diff === 0;  
const isTomorrow = diff === 1;  
const label = isToday ? ‘🔴 **اليوم**!’ : isTomorrow ? ‘🟡 **غداً**’ : `**بعد** ${diff} **يوم**`;  
const bg = isToday ? ‘var(–redl)’ : isTomorrow ? ‘var(–goldl)’ : i%2===0 ? ‘#fff’ : ‘var(–gray)’;  
return `<div style="padding:12px 16px;border-bottom:1px solid #F0F0F0;background:${bg};display:flex;align-items:center;gap:12px"> <div style="text-align:center;min-width:48px"> <div style="font-size:18px;font-weight:900;color:var(--gm)">${fmtDate(v.nextDate).split('/')[0]}</div> <div style="font-size:10px;color:var(--muted)">${fmtDate(v.nextDate).split('/').slice(1).join('/')}</div> </div> <div style="flex:1"> <div style="font-weight:700;font-size:14px">${v.client} <span style="color:var(--muted);font-size:12px;font-weight:400">— ${v.area||''}</span></div> <div style="font-size:12px;color:var(--muted);margin-top:2px">${v.nextNote || v.type || '—'}</div> </div> <div style="font-size:12px;font-weight:700;color:${isToday?'var(--red)':isTomorrow?'var(--gold)':'var(--gm)'}">${label}</div> </div>`;  
}).join(’’);  
}  
  
// **──** Visit Report **──**  
function printVisitReport(id) {  
const v = visits.find(x => x.id === id);  
if (!v) return;  
const GOLD=’#D4AC0D’,GOLDL=’#FFF9E6’,OR=’#E07B39’,RED=’#C0392B’,BLUE=’#1A56DB’,BLUEL=’#EBF5FF’;  
  
const payColor = v.payStatus===‘**مدفوع**’ ? GM : v.payStatus===‘**مدفوع** **جزئياً**’ ? GOLD : RED;  
const payBg    = v.payStatus===‘**مدفوع**’ ? GP   : v.payStatus===‘**مدفوع** **جزئياً**’ ? GOLDL : ‘#FADBD8’;  
  
const html = `<!DOCTYPE html><html dir="rtl" lang="ar"><head><meta charset="UTF-8">  
  
  <title>**تقرير** **زيارة** — ${v.client}</title>  
  <style>  
    *{margin:0;padding:0;box-sizing:border-box}  
    body{font-family:Arial,sans-serif;direction:rtl;background:#f0f4f0;padding:20px}  
    .page{max-width:640px;margin:0 auto;background:white;border-radius:12px;overflow:hidden;box-shadow:0 4px 20px rgba(0,0,0,.1)}  
    .print-btn{display:block;width:180px;margin:16px auto;padding:11px;background:${GD};color:white;border:none;border-radius:10px;font-size:14px;font-weight:700;cursor:pointer;font-family:Arial;text-align:center}  
    @media print{body{background:white;padding:0}.page{box-shadow:none;border-radius:0}.print-btn{display:none}@page{margin:12mm}body{-webkit-print-color-adjust:exact;print-color-adjust:exact}}  
  </style></head><body>  
  <button class="print-btn" onclick="window.print()">🖨 **طباعة** / PDF</button>  
  <div class="page">  
  
```  
<!-- Header -->  
<div style="background:${GD};padding:20px 24px;display:flex;justify-content:space-between;align-items:center">  
  <div>  
    <div style="color:white;font-size:19px;font-weight:900">🌳 Dr.Tree</div>  
    <div style="color:${GL};font-size:10px;letter-spacing:2px;margin-top:2px">GARDEN &amp; TREE SERVICES · QATAR</div>  
  </div>  
  <div style="background:${GOLD};color:${GD};padding:8px 14px;border-radius:8px;text-align:center">  
    <div style="font-size:9px;font-weight:700">**تقرير** **زيارة**</div>  
    <div style="font-size:15px;font-weight:900">#${v.id}</div>  
    <div style="font-size:9px;color:#555">${new Date().toLocaleDateString('ar-QA')}</div>  
  </div>  
</div>  
<div style="height:4px;background:linear-gradient(to left,${GL},${GOLD},${GL})"></div>  
  
<!-- Client Info -->  
<div style="display:flex;border-bottom:2px solid ${GP}">  
  <div style="flex:1;padding:14px 20px;border-left:1px solid #eee">  
    <div style="font-size:9px;color:#999;font-weight:700;text-transform:uppercase;letter-spacing:1px;margin-bottom:4px">**العميل**</div>  
    <div style="font-size:16px;font-weight:700;color:${GD}">${v.client}</div>  
    <div style="font-size:12px;color:#888;margin-top:2px">${v.area||''}</div>  
  </div>  
  <div style="flex:1;padding:14px 20px;border-left:1px solid #eee">  
    <div style="font-size:9px;color:#999;font-weight:700;text-transform:uppercase;letter-spacing:1px;margin-bottom:4px">**تاريخ** **الزيارة**</div>  
    <div style="font-size:14px;font-weight:700;color:#333">${fmtDate(v.date)}</div>  
  </div>  
  <div style="flex:1;padding:14px 20px">  
    <div style="font-size:9px;color:#999;font-weight:700;text-transform:uppercase;letter-spacing:1px;margin-bottom:4px">**نوع** **العمل**</div>  
    <div style="display:inline-block;background:${GP};color:${GM};padding:3px 10px;border-radius:12px;font-size:12px;font-weight:700">${v.type||'—'}</div>  
  </div>  
</div>  
  
<!-- Work Done -->  
<div style="background:${GM};padding:9px 20px;font-size:12px;font-weight:700;color:white">**الأعمال** **المنجزة**</div>  
<div style="padding:16px 20px;border-bottom:1px solid #eee">  
  <div style="font-size:13px;color:#333;line-height:1.7">${v.work||'—'}</div>  
  ${v.notes ? `<div style="margin-top:10px;padding:10px 14px;background:#EBF5FF;border-radius:8px;font-size:12px;color:${BLUE}">📝 ${v.notes}</div>` : ''}  
</div>  
  
<!-- Extra Work -->  
${v.extra ? `  
<div style="background:${OR};padding:9px 20px;font-size:12px;font-weight:700;color:white">**الأعمال** **الإضافية**</div>  
<div style="padding:16px 20px;border-bottom:1px solid #eee;background:#FEF0E7">  
  <div style="font-size:13px;color:#333;margin-bottom:8px">${v.extra}</div>  
  ${v.extraAmount>0 ? `<div style="font-size:15px;font-weight:700;color:${OR}">${v.extraAmount.toLocaleString('en')} QAR</div>` : ''}  
  ${v.extraStatus ? `<div style="display:inline-block;margin-top:6px;padding:3px 10px;border-radius:12px;font-size:11px;font-weight:700;background:${GP};color:${GM}">${v.extraStatus}</div>` : ''}  
</div>` : ''}  
  
<!-- Payment -->  
<div style="background:${BLUE};padding:9px 20px;font-size:12px;font-weight:700;color:white">**حالة** **الدفع**</div>  
<div style="padding:16px 20px;border-bottom:1px solid #eee;display:flex;gap:20px;align-items:center;flex-wrap:wrap">  
  <div style="display:inline-block;padding:6px 16px;border-radius:20px;font-size:13px;font-weight:700;background:${payBg};color:${payColor}">${v.payStatus||'**غير** **مدفوع**'}</div>  
  ${v.dueDate ? `<div style="font-size:12px;color:#666">**تاريخ** **الاستحقاق**: <b style="color:${RED}">${fmtDate(v.dueDate)}</b></div>` : ''}  
  ${v.paidAmount>0 ? `<div style="font-size:12px;color:#666">**المبلغ** **المدفوع**: <b style="color:${GM}">${v.paidAmount.toLocaleString('en')} QAR</b></div>` : ''}  
</div>  
  
<!-- Next Visit -->  
${v.nextDate ? `  
<div style="background:#2D6A4F;padding:9px 20px;font-size:12px;font-weight:700;color:white">**الموعد** **القادم**</div>  
<div style="padding:16px 20px;border-bottom:1px solid #eee;background:${GP}">  
  <div style="font-size:14px;font-weight:700;color:${GD}">${fmtDate(v.nextDate)}</div>  
  ${v.nextNote ? `<div style="font-size:12px;color:#555;margin-top:4px">${v.nextNote}</div>` : ''}  
</div>` : ''}  
  
<!-- Footer -->  
<div style="background:${GD};color:${GL};text-align:center;padding:11px;font-size:10px">  
  Dr.Tree | +974 XXXX XXXX | info@drtree.qa  
</div>  
```  
  
  </div>  
  </body></html>`;  
  
const w = window.open(’’,’_blank’);  
w.document.write(html); w.document.close(); w.focus();  
setTimeout(() => { w.print(); w.close(); }, 400);  
}  
  
// **──** Clients **──**  
let clients_data = [];  
function loadClients() {  
try { clients_data = JSON.parse(localStorage.getItem(‘dt_clients’) || ‘[]’); } catch { clients_data = []; }  
}  
function saveClients() {  
try { localStorage.setItem(‘dt_clients’, JSON.stringify(clients_data)); } catch {}  
if (window._fbReady) {  
const { db, ref, set } = window._fb;  
// Convert to object to avoid Firebase empty array issues  
const clientsObj = {};  
clients_data.forEach((c,i) => { clientsObj[‘c’+i] = c; });  
set(ref(db, ‘clients’), clients_data.length ? clients_data : null).catch(e => console.log(e));  
}  
}  
  
function openAddClient() {  
document.getElementById(‘client-modal-title’).textContent = ‘👤 **إضافة** **عميل** **جديد**’;  
document.getElementById(‘client-save-btn’).textContent = ‘✚ **إضافة**’;  
document.getElementById(‘cf-name’).value = ‘’;  
document.getElementById(‘cf-area’).value = ‘’;  
document.getElementById(‘cf-phone’).value = ‘’;  
document.getElementById(‘cf-monthly’).value = ‘’;  
document.getElementById(‘cf-visits-per-month’).value = ‘4’;  
document.getElementById(‘cf-notes’).value = ‘’;  
document.getElementById(‘cf-name’).classList.remove(‘error’);  
window._editClientId = null;  
document.getElementById(‘client-modal’).classList.add(‘open’);  
}  
  
function openEditClient(id) {  
const c = clients_data.find(x => x.id === id);  
if (!c) return;  
document.getElementById(‘client-modal-title’).textContent = ‘✏️ **تعديل** **العميل**’;  
document.getElementById(‘client-save-btn’).textContent = ‘💾 **حفظ**’;  
document.getElementById(‘cf-name’).value = c.name || ‘’;  
document.getElementById(‘cf-area’).value = c.area || ‘’;  
document.getElementById(‘cf-phone’).value = c.phone || ‘’;  
document.getElementById(‘cf-monthly’).value = c.monthly || ‘’;  
document.getElementById(‘cf-visits-per-month’).value = c.visitsPerMonth || ‘4’;  
document.getElementById(‘cf-notes’).value = c.notes || ‘’;  
window._editClientId = id;  
document.getElementById(‘client-modal’).classList.add(‘open’);  
}  
  
function saveClient() {  
const name = document.getElementById(‘cf-name’).value.trim();  
if (!name) { document.getElementById(‘cf-name’).classList.add(‘error’); return; }  
const data = {  
id: window._editClientId || Date.now(),  
name,  
area: document.getElementById(‘cf-area’).value.trim(),  
phone: document.getElementById(‘cf-phone’).value.trim(),  
monthly: parseFloat(document.getElementById(‘cf-monthly’).value) || 0,  
visitsPerMonth: parseInt(document.getElementById(‘cf-visits-per-month’).value) || 4,  
notes: document.getElementById(‘cf-notes’).value.trim(),  
};  
if (window._editClientId) {  
clients_data = clients_data.map(c => c.id === window._editClientId ? data : c);  
showToast(‘✅ **تم** **تعديل** **العميل**!’);  
} else {  
clients_data.unshift(data);  
showToast(‘✅ **تمت** **إضافة** **العميل**!’);  
}  
saveClients();  
document.getElementById(‘client-modal’).classList.remove(‘open’);  
renderClients();  
updateClientSelects();  
}  
  
function delClient(id) {  
if (!confirm(‘**حذف** **هذا** **العميل؟**’)) return;  
clients_data = clients_data.filter(c => c.id !== id);  
saveClients();  
renderClients();  
showToast(‘🗑 **تم** **الحذف**’);  
}  
  
function renderClients() {  
// Merge clients from clients_data + visits  
const visitClients = […new Set(visits.map(v => v.client).filter(Boolean))];  
const savedNames = clients_data.map(c => c.name);  
// Auto-add clients from visits not in clients_data  
visitClients.forEach(name => {  
if (!savedNames.includes(name)) {  
const lastVisit = visits.find(v => v.client === name);  
clients_data.push({ id: Date.now() + Math.random(), name, area: lastVisit?.area || ‘’, phone: ‘’, notes: ‘’ });  
}  
});  
  
const el = document.getElementById(‘clients-list-body’);  
const count = document.getElementById(‘clients-count’);  
count.textContent = clients_data.length + ’ **عميل**’;  
  
if (!clients_data.length) {  
el.innerHTML = ‘<div class="empty"><div class="icon">👥</div><p>**لا** **يوجد** **عملاء** **بعد**</p></div>’;  
return;  
}  
  
el.innerHTML = clients_data.map((c, i) => {  
const cVisits = visits.filter(v => v.client === c.name);  
const lastVisit = cVisits[0];  
const bg = i%2===0 ? ‘#fff’ : ‘var(–gray)’;  
return `<div style="padding:14px 16px;border-bottom:1px solid #F0F0F0;background:${bg}"> <div style="display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:6px"> <div> <div style="font-weight:700;font-size:15px">${c.name}</div> <div style="font-size:12px;color:var(--muted);margin-top:2px"> ${c.area ? '📍 '+c.area : ''} ${c.phone ? ' &nbsp;📞 '+c.phone : ''} ${c.monthly ? `<span style="background:var(--goldl);color:var(--gold);padding:1px 8px;border-radius:12px;font-size:11px;font-weight:700;margin-right:4px">💰 ${c.monthly.toLocaleString(‘en’)} QAR/**شهر**</span>`: ''} </div> </div> <div style="display:flex;gap:6px;align-items:center"> <span style="background:var(--gp);color:var(--gm);padding:2px 10px;border-radius:20px;font-size:11px;font-weight:700">${cVisits.length} **زيارة**</span> <button class="btn-icon" onclick="openEditClient(${c.id})">✏️</button> <button class="btn-icon" style="color:#ddd" onclick="delClient(${c.id})">🗑</button> </div> </div> ${c.notes ?`<div style="font-size:11px;color:var(--blue);margin-bottom:6px">📝 ${c.notes}</div>`: ''} ${lastVisit ?`<div style="font-size:11px;color:var(--muted)">**آخر** **زيارة**: ${fmtDate(lastVisit.date)} · ${lastVisit.type||’’}</div>`: ''} ${cVisits.length > 0 ?`<div style="margin-top:8px">  
<details>  
<summary style="font-size:12px;color:var(--gm);font-weight:600;cursor:pointer">**عرض** **السجل** (${cVisits.length} **زيارة**)</summary>  
<div style="margin-top:8px;padding-right:8px;border-right:3px solid var(--gp)">  
${cVisits.map(v => `<div style="padding:6px 0;border-bottom:1px solid #f0f0f0;font-size:12px"> <span style="color:var(--gm);font-weight:600">${fmtDate(v.date)}</span> ·  <span style="background:var(--gp);color:var(--gm);padding:1px 6px;border-radius:10px;font-size:10px">${v.type||''}</span> ${v.work ? `<div style="color:#666;margin-top:2px">${v.work}</div>`: ''} ${v.extra ?`<div style="color:var(--or);margin-top:2px">⚙ ${v.extra}${v.extraAmount?’ — ‘+v.extraAmount.toLocaleString(‘en’)+’ QAR’:’’}</div>` : ''} </div>`).join(’’)}  
</div>  
</details>  
</div>` : ''} </div>`;  
}).join(’’);  
}  
  
// **──** Quotation **──**  
let quotes = JSON.parse(localStorage.getItem(‘dt_quotes’)||’[]’);  
let laborItems = [], plantItems = [], materialItems = [], otherItems = [];  
let savedPlants = JSON.parse(localStorage.getItem(‘dt_plants_list’)||’[]’);  
  
function savePlantsList() {  
try { localStorage.setItem(‘dt_plants_list’, JSON.stringify(savedPlants)); } catch {}  
if (window._fbReady) {  
const { db, ref, set } = window._fb;  
set(ref(db, ‘plants_list’), savedPlants.length ? savedPlants : null).catch(e=>console.log(e));  
}  
}  
  
function addPlantToRegistry(name) {  
if (!name || savedPlants.includes(name)) return;  
savedPlants.push(name);  
savedPlants.sort();  
savePlantsList();  
}  
  
function saveQuotes() {  
localStorage.setItem(‘dt_quotes’, JSON.stringify(quotes));  
if (window._fbReady) {  
const { db, ref, set } = window._fb;  
set(ref(db, ‘quotes’), quotes).catch(e=>console.log(e));  
}  
}  
  
function onQClientChange(val) {  
const newInput = document.getElementById(‘q-new-client’);  
if (val === ‘**new**’) {  
newInput.style.display = ‘block’;  
newInput.focus();  
} else {  
newInput.style.display = ‘none’;  
}  
}  
  
function getQClient() {  
const sel = document.getElementById(‘q-client’).value;  
if (sel === ‘**new**’) return document.getElementById(‘q-new-client’).value.trim();  
return sel;  
}  
  
function newQuote() {  
laborItems=[{desc:’’,qty:1,unit:‘**يوم**’,price:0,note:’’}];  
plantItems=[{desc:’’,qty:1,unit:‘**شجرة**’,price:0,note:’’}];  
materialItems=[{desc:’’,qty:1,unit:‘**وحدة**’,price:0,note:’’}];  
otherItems=[];  
document.getElementById(‘q-client’).innerHTML=’<option value="">**اختر** **العميل**…</option>’+getClients().map(c=>`<option>${c}</option>`).join(’’)+’<option value="__new__">+ **إضافة** **عميل** **جديد**…</option>’;  
document.getElementById(‘q-new-client’).style.display=‘none’;  
document.getElementById(‘q-new-client’).value=’’;  
document.getElementById(‘q-date’).value=TODAY;  
document.getElementById(‘q-desc’).value=’’;  
renderLaborRows(); renderPlantRows(); renderMaterialRows(); renderOtherRows(); updateQuoteSummary();  
document.getElementById(‘quote-form-card’).style.display=‘block’;  
document.getElementById(‘quote-form-card’).scrollIntoView({behavior:‘smooth’});  
}  
  
function makeRow(item,idx,type,bg) {  
const units = type===‘labor’?[‘**يوم**’,‘**ساعة**’,‘**أسبوع**’,‘**شهر**’]:type===‘plant’?[‘**شجرة**’,‘**شجيرة**’,‘**مغطيات**’,‘**زهور** **موسمية**’,‘**وحدة**’]:[‘**وحدة**’,‘**متر**’,‘**م**²’,‘**كيس**’,‘**طن**’,‘**لتر**’];  
const sizes = [‘**صغير**’,‘**وسط**’,‘**كبير**’,‘**كبير** **جداً**’];  
const subtotal = ((item.qty||0)*(item.price||0)).toLocaleString(‘en’);  
const isPlant = type===‘plant’;  
const cols = isPlant ? ‘2fr 55px 90px 70px 70px 60px 1fr 26px’ : ‘2fr 55px 75px 75px 60px 1fr 26px’;  
return `<div style="background:white;padding:8px;border-radius:8px;margin-bottom:8px;display:grid;grid-template-columns:${cols};gap:6px;align-items:center"> ${type==='plant'?`<input placeholder="**اسم** **النبات**" list="plants-datalist" value="${item.desc}" oninput="updateItem('plant',${idx},'desc',this.value)" style="padding:7px 9px;border:1px solid #ddd;border-radius:6px;font-size:13px;direction:rtl;width:100%">`:`<input placeholder="**البند**" value="${item.desc}" oninput="updateItem('${type}',${idx},'desc',this.value)" style="padding:7px 9px;border:1px solid #ddd;border-radius:6px;font-size:13px;direction:rtl;width:100%">`} <input type="number" placeholder="**كمية**" value="${item.qty}" min="0" oninput="updateItem('${type}',${idx},'qty',this.value)" style="padding:7px 4px;border:1px solid #ddd;border-radius:6px;font-size:13px;width:100%;text-align:center"> <select onchange="updateItem('${type}',${idx},'unit',this.value)" style="padding:7px 4px;border:1px solid #ddd;border-radius:6px;font-size:12px;direction:rtl;width:100%"> ${units.map(u=>`<option${u===item.unit?’ selected’:’’}>${u}</option>`).join('')} </select> ${isPlant?`<select onchange="updateItem('${type}',${idx},'size',this.value)" style="padding:7px 4px;border:1px solid #ddd;border-radius:6px;font-size:12px;direction:rtl;width:100%">  
${sizes.map(s=>`<option${s===(item.size||'**وسط**')?' selected':''}>${s}</option>`).join(’’)}  
</select>`:’’}  
<input type="number" placeholder="**سعر**" value="${item.price}" min="0" oninput="updateItem('${type}',${idx},'price',this.value)" style="padding:7px 4px;border:1px solid #ddd;border-radius:6px;font-size:13px;width:100%;text-align:center">  
<span style="font-size:11px;color:#666;font-weight:700;text-align:center;white-space:nowrap">${subtotal}</span>  
<input placeholder="**ملاحظة**..." value="${item.note||''}" oninput="updateItem('${type}',${idx},'note',this.value)" style="padding:7px 9px;border:1px solid #eee;border-radius:6px;font-size:12px;direction:rtl;color:#888;width:100%">  
<button onclick="removeItem('${type}',${idx})" style="background:none;border:none;color:#ddd;cursor:pointer;font-size:16px">×</button>  
  
  </div>`;  
}  
  
function renderLaborRows(){ document.getElementById(‘labor-rows’).innerHTML=laborItems.map((item,i)=>makeRow(item,i,‘labor’)).join(’’); updateQuoteSummary(); }  
function renderPlantRows(){  
// Update datalist  
const dl = document.getElementById(‘plants-datalist’);  
if (dl) dl.innerHTML = savedPlants.map(p=>`<option value="${p}">`).join(’’);  
document.getElementById(‘plant-rows’).innerHTML=plantItems.map((item,i)=>makeRow(item,i,‘plant’)).join(’’);  
updateQuoteSummary();  
}  
function renderMaterialRows(){ document.getElementById(‘material-rows’).innerHTML=materialItems.map((item,i)=>makeRow(item,i,‘material’)).join(’’); updateQuoteSummary(); }  
function renderOtherRows(){ document.getElementById(‘other-rows’).innerHTML=otherItems.map((item,i)=>makeRow(item,i,‘other’)).join(’’); updateQuoteSummary(); }  
  
function addLaborRow(){ laborItems.push({desc:’’,qty:1,unit:‘**يوم**’,price:0,note:’’}); renderLaborRows(); }  
function addPlantRow(){ plantItems.push({desc:’’,qty:1,unit:‘**شجرة**’,price:0,note:’’}); renderPlantRows(); }  
function addMaterialRow(){ materialItems.push({desc:’’,qty:1,unit:‘**وحدة**’,price:0,note:’’}); renderMaterialRows(); }  
function addOtherRow(){ otherItems.push({desc:’’,qty:1,unit:‘**وحدة**’,price:0,note:’’}); renderOtherRows(); }  
  
function removeItem(type,idx){  
if(type===‘labor’) { laborItems.splice(idx,1); renderLaborRows(); }  
else if(type===‘plant’) { plantItems.splice(idx,1); renderPlantRows(); }  
else if(type===‘material’) { materialItems.splice(idx,1); renderMaterialRows(); }  
else { otherItems.splice(idx,1); renderOtherRows(); }  
}  
  
function updateItem(type,idx,field,val){  
const arr = type===‘labor’?laborItems:type===‘plant’?plantItems:type===‘material’?materialItems:otherItems;  
arr[idx][field] = field===‘qty’||field===‘price’ ? parseFloat(val)||0 : val;  
if(field===‘size’) arr[idx].size = val;  
// Only re-render if qty or price changed (to update subtotal) — skip for text fields to avoid keyboard dismiss  
if(field===‘qty’||field===‘price’) {  
// Update only the subtotal span without re-rendering the whole row  
const rows = document.getElementById(type+’-rows’);  
if(rows) {  
const spans = rows.querySelectorAll(‘span’);  
const subtotal = ((arr[idx].qty||0)*(arr[idx].price||0)).toLocaleString(‘en’);  
// Find the subtotal span for this row  
const rowDivs = rows.children;  
if(rowDivs[idx]) {  
const span = rowDivs[idx].querySelector(‘span’);  
if(span) span.textContent = subtotal;  
}  
}  
updateQuoteSummary();  
}  
// For select changes (unit, size) re-render is needed  
if(field===‘unit’||field===‘size’) {  
if(type===‘labor’) renderLaborRows();  
else if(type===‘plant’) renderPlantRows();  
else if(type===‘material’) renderMaterialRows();  
else renderOtherRows();  
}  
}  
  
function calcSection(items){ return items.reduce((s,i)=>s+(i.qty||0)*(i.price||0),0); }  
  
function updateQuoteSummary(){  
const l=calcSection(laborItems), p=calcSection(plantItems), m=calcSection(materialItems), o=calcSection(otherItems);  
const total=l+p+m+o;  
document.getElementById(‘qs-labor’).textContent=l.toLocaleString(‘en’)+’ QAR’;  
document.getElementById(‘qs-plant’).textContent=p.toLocaleString(‘en’)+’ QAR’;  
document.getElementById(‘qs-material’).textContent=m.toLocaleString(‘en’)+’ QAR’;  
document.getElementById(‘qs-other’).textContent=o.toLocaleString(‘en’)+’ QAR’;  
document.getElementById(‘qs-total’).textContent=total.toLocaleString(‘en’)+’ QAR’;  
}  
  
function printQuote(){  
const client=getQClient();  
if(!client){showToast(‘⚠️ **اختر** **العميل** **أو** **أدخل** **اسمه**’);return;}  
// Save new client if needed  
if(document.getElementById(‘q-client’).value===’**new**’ && client) {  
if(!clients_data.find(c=>c.name===client)) {  
clients_data.push({id:Date.now(),name:client,area:’’,phone:’’,monthly:0,visitsPerMonth:4,notes:’’});  
saveClients(); updateClientSelects();  
}  
}  
const date=document.getElementById(‘q-date’).value;  
const desc=document.getElementById(‘q-desc’).value;  
const l=calcSection(laborItems),p=calcSection(plantItems),m=calcSection(materialItems),o=calcSection(otherItems),total=l+p+m+o;  
const qNum=‘QT-’+String(quotes.length+1).padStart(3,‘0’);  
  
const tableRow=(item,i,isPlant)=>`<tr style="background:${i%2===0?'#fff':'#f7f7f7'}"> <td style="padding:8px 12px;border-bottom:1px solid #eee;font-size:12px">${item.desc||'—'}${item.note?`<div style="font-size:10px;color:#999;margin-top:2px">${item.note}</div>`:''}</td> ${isPlant?`<td style="padding:8px 12px;border-bottom:1px solid #eee;text-align:center;font-size:12px">${item.size||‘**وسط**’}</td>`:’’}  
<td style="padding:8px 12px;border-bottom:1px solid #eee;text-align:center;font-size:12px">${item.qty}</td>  
<td style="padding:8px 12px;border-bottom:1px solid #eee;text-align:center;font-size:12px">${item.unit}</td>  
<td style="padding:8px 12px;border-bottom:1px solid #eee;text-align:center;font-size:12px">${item.price.toLocaleString(‘en’)} QAR</td>  
<td style="padding:8px 12px;border-bottom:1px solid #eee;text-align:center;font-weight:700;font-size:12px;color:#1B4332">${(item.qty*item.price).toLocaleString(‘en’)} QAR</td>  
  
  </tr>`;  
  
const th=`background:#1B4332;color:white;padding:9px 12px;text-align:`;  
const sectionHeader=(label,color)=>`<tr><td colspan="5" style="padding:8px 12px;background:${color};color:white;font-weight:700;font-size:12px">${label}</td></tr>`;  
  
const html=`<!DOCTYPE html><html dir="rtl" lang="ar"><head><meta charset="UTF-8"><title>**كوتيشن** ${qNum}</title>  
  
  <style>*{margin:0;padding:0;box-sizing:border-box}body{font-family:Arial,sans-serif;direction:rtl;background:#f0f4f0;padding:20px}  
  .page{max-width:680px;margin:0 auto;background:white;border-radius:12px;overflow:hidden;box-shadow:0 4px 20px rgba(0,0,0,.1)}  
  .print-btn{display:block;width:180px;margin:16px auto;padding:11px;background:#1B4332;color:white;border:none;border-radius:10px;font-size:14px;font-weight:700;cursor:pointer;font-family:Arial;text-align:center}  
  @media print{body{background:white;padding:0}.page{box-shadow:none;border-radius:0}.print-btn{display:none}@page{margin:12mm}body{-webkit-print-color-adjust:exact;print-color-adjust:exact}}</style>  
  
  </head><body>  
  <button class="print-btn" onclick="window.print()">🖨 **طباعة** / PDF</button>  
  <div class="page">  
    <div style="background:#1B4332;padding:20px 26px;display:flex;justify-content:space-between;align-items:flex-start">  
      <div><div style="color:white;font-size:20px;font-weight:900">🌳 Dr.Tree</div>  
      <div style="color:#52B788;font-size:10px;letter-spacing:2px;margin-top:3px">GARDEN &amp; TREE SERVICES · QATAR</div>  
      <div style="color:#aaa;font-size:10px;margin-top:5px">+974 XXXX XXXX | info@drtree.qa</div></div>  
      <div style="background:#D4AC0D;color:#1B4332;padding:10px 16px;border-radius:8px;text-align:center">  
        <div style="font-size:9px;font-weight:700">**عرض** **سعر**</div>  
        <div style="font-size:18px;font-weight:900">${qNum}</div>  
        <div style="font-size:9px;color:#555">${fmtDate(date)}</div>  
      </div>  
    </div>  
    <div style="height:4px;background:linear-gradient(to left,#52B788,#D4AC0D,#52B788)"></div>  
    <div style="display:flex;border-bottom:2px solid #D8F3DC">  
      <div style="flex:1;padding:14px 20px;border-left:1px solid #eee">  
        <div style="font-size:9px;color:#999;font-weight:700;text-transform:uppercase;letter-spacing:1px;margin-bottom:4px">**مقدم** **إلى**</div>  
        <div style="font-size:15px;font-weight:700;color:#1B4332">${client||'—'}</div>  
      </div>  
      <div style="flex:1;padding:14px 20px">  
        <div style="font-size:9px;color:#999;font-weight:700;text-transform:uppercase;letter-spacing:1px;margin-bottom:4px">**وصف** **المشروع**</div>  
        <div style="font-size:12px;color:#555">${desc||'—'}</div>  
      </div>  
    </div>  
    <table style="width:100%;border-collapse:collapse">  
      <thead><tr>  
        <th style="${th}right;width:35%">**البند**</th>  
        <th style="${th}center;width:10%">**الكمية**</th>  
        <th style="${th}center;width:12%">**الوحدة**</th>  
        <th style="${th}center;width:10%">**سعر** **الوحدة**</th>  
        <th style="${th}center;width:13%">**الإجمالي**</th>  
      </tr></thead>  
      <tbody>  
        ${laborItems.length?sectionHeader('👷 **العمالة**','#1A56DB')+laborItems.map((item,i)=>tableRow(item,i,false)).join(''):''}  
        ${plantItems.length?sectionHeader('🌳 **النباتات**','#3B6D11')+plantItems.map((item,i)=>tableRow(item,i,true)).join(''):''}   
        ${materialItems.length?sectionHeader('🪨 **المواد** **والمستلزمات**','#2D6A4F')+materialItems.map((item,i)=>tableRow(item,i,false)).join(''):''}  
        ${otherItems.length?sectionHeader('⚙ **أجور** **أخرى**','#E07B39')+otherItems.map((item,i)=>tableRow(item,i,false)).join(''):''}   
      </tbody>  
    </table>  
    <div style="padding:16px 26px">  
      <table style="border-collapse:collapse;min-width:280px">  
        ${l>0?`<tr><td style="padding:6px 14px;color:#555;font-weight:600;font-size:12px">👷 **العمالة**</td><td style="padding:6px 14px;font-weight:700;font-size:12px;color:#1A56DB">${l.toLocaleString('en')} QAR</td></tr>`:''}  
        ${p>0?`<tr><td style="padding:6px 14px;color:#555;font-weight:600;font-size:12px">🌳 **النباتات**</td><td style="padding:6px 14px;font-weight:700;font-size:12px;color:#3B6D11">${p.toLocaleString('en')} QAR</td></tr>`:''}  
        ${m>0?`<tr><td style="padding:6px 14px;color:#555;font-weight:600;font-size:12px">🪨 **المواد**</td><td style="padding:6px 14px;font-weight:700;font-size:12px;color:#2D6A4F">${m.toLocaleString('en')} QAR</td></tr>`:''}  
        ${o>0?`<tr><td style="padding:6px 14px;color:#555;font-weight:600;font-size:12px">⚙ **أجور** **أخرى**</td><td style="padding:6px 14px;font-weight:700;font-size:12px;color:#E07B39">${o.toLocaleString('en')} QAR</td></tr>`:''}  
        <tr><td colspan="2" style="padding:4px"><hr style="border:1px solid #eee"></td></tr>  
        <tr style="background:#1B4332"><td style="padding:11px 14px;color:white;font-size:13px;font-weight:900">💰 **إجمالي** **عرض** **السعر**</td><td style="padding:11px 14px;color:#D4AC0D;font-size:16px;font-weight:900">${total.toLocaleString('en')} QAR</td></tr>  
      </table>  
    </div>  
    <div style="margin:0 26px 14px;padding:9px 14px;background:#FFF9E6;border:1px solid #D4AC0D;border-radius:6px;font-size:10px;color:#8B6914;font-weight:600;text-align:center">  
      **صادر** **بتاريخ** ${fmtDate(date)} | **هذا** **العرض** **ساري** **لمدة** 30 **يوماً**  
    </div>  
    <div style="background:#1B4332;color:#52B788;text-align:center;padding:11px;font-size:10px">Dr.Tree | +974 XXXX XXXX | info@drtree.qa</div>  
  </div></body></html>`;  
  
// Save quote  
// Save plant names to registry  
plantItems.forEach(p => { if(p.desc) addPlantToRegistry(p.desc); });  
quotes.unshift({id:Date.now(),qNum,client,date,desc,labor:laborItems,plant:plantItems,material:materialItems,other:otherItems,total});  
saveQuotes();  
renderQuotes();  
  
const w=window.open(’’,’_blank’);  
w.document.write(html);w.document.close();w.focus();  
setTimeout(()=>{w.print();w.close();},400);  
}  
  
function shareQuoteWhatsApp(){  
const client=getQClient();  
const date=document.getElementById(‘q-date’).value;  
const l=calcSection(laborItems),p=calcSection(plantItems),m=calcSection(materialItems),o=calcSection(otherItems),total=l+p+m+o;  
let msg=`🌳 *Dr.Tree — **عرض** **سعر***\n\n`;  
msg+=`**العميل**: *${client||'—'}*\n`;  
msg+=`**التاريخ**: ${fmtDate(date)}\n\n`;  
if(l>0) msg+=`👷 **العمالة**: ${l.toLocaleString('en')} QAR\n`;  
if(m>0) msg+=`🌱 **الزراعة** **والمواد**: ${m.toLocaleString('en')} QAR\n`;  
if(o>0) msg+=`⚙ **أجور** **أخرى**: ${o.toLocaleString('en')} QAR\n`;  
msg+=`\n💰 ***الإجمالي**: ${total.toLocaleString('en')} QAR*`;  
msg+=`\n\n**هذا** **العرض** **ساري** **لمدة** 30 **يوماً** 🌿`;  
window.open(‘https://wa.me/?text=’+encodeURIComponent(msg),’_blank’);  
}  
  
function renderQuotes(){  
const el=document.getElementById(‘quotes-list’);  
const count=document.getElementById(‘quotes-count’);  
count.textContent=quotes.length+’ **كوتيشن**’;  
if(!quotes.length){el.innerHTML=’<div class="empty"><div class="icon">📋</div><p>**لا** **توجد** **كوتيشنات** **بعد**</p></div>’;return;}  
el.innerHTML=quotes.map((q,i)=>` <div style="padding:12px 16px;border-bottom:1px solid #F0F0F0;background:${i%2===0?'white':'var(--gray)'}"> <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:4px"> <div> <span style="font-weight:700;font-size:14px">${q.client||'—'}</span> <span style="color:var(--muted);font-size:12px;margin-right:8px">${q.qNum}</span> </div> <div style="display:flex;gap:8px;align-items:center"> <span style="background:var(--goldl);color:var(--gold);padding:2px 10px;border-radius:20px;font-size:12px;font-weight:700">${q.total.toLocaleString('en')} QAR</span> <button class="btn-icon" style="color:#ddd" onclick="deleteQuote(${q.id})">🗑</button> </div> </div> <div style="font-size:11px;color:var(--muted)">${fmtDate(q.date)}${q.desc?' — '+q.desc:''}</div> </div>`).join(’’);  
}  
  
function deleteQuote(id){  
if(!confirm(‘**حذف** **هذا** **الكوتيشن؟**’))return;  
quotes=quotes.filter(q=>q.id!==id);  
saveQuotes();renderQuotes();  
}  
  
// **──** Render all **──**  
function renderAll() {  
renderKPIs();  
renderRecent();  
renderUpcoming();  
updateClientSelects();  
}  
  
// **──** Init **──**  
loadData();  
loadClients();  
renderAll();  
initFirebase();  
document.getElementById(‘f-date’).value = TODAY;  
</script>  
  
<!-- Client Modal -->  
  
<div class="modal" id="client-modal">  
  <div class="modal-box">  
    <div class="modal-handle"></div>  
    <div class="modal-title" id="client-modal-title">👤 **إضافة** **عميل** **جديد**</div>  
    <div class="field"><label>**اسم** **العميل** *</label><input type="text" id="cf-name" placeholder="**مثال**: **محمد** **العلي**"></div>  
    <div class="grid2">  
      <div class="field"><label>**المنطقة**</label><input type="text" id="cf-area" list="areas-list" placeholder="**الدحيل**"></div>  
      <div class="field"><label>**الجوال**</label><input type="tel" id="cf-phone" placeholder="+974 XXXX XXXX"></div>  
    </div>  
    <div class="field"><label>**مبلغ** **الباقة** **الشهرية** (QAR)</label><input type="number" id="cf-monthly" placeholder="500" min="0"></div>  
    <div class="field"><label>**عدد** **الزيارات** **الشهرية**</label>  
      <select id="cf-visits-per-month" style="width:100%;padding:11px 12px;border:1.5px solid var(--border);border-radius:8px;font-size:15px;direction:rtl;background:#fafafa;outline:none;-webkit-appearance:none">  
        <option value="4">4 **زيارات**</option>  
        <option value="2">2 **زيارات**</option>  
        <option value="1">**زيارة** **واحدة**</option>  
        <option value="8">8 **زيارات**</option>  
        <option value="0">**غير** **محدد**</option>  
      </select>  
    </div>  
    <div class="field"><label>**ملاحظات**</label><textarea id="cf-notes" placeholder="**أي** **ملاحظات**..." style="min-height:60px"></textarea></div>  
    <div class="modal-footer">  
      <button class="btn btn-primary" style="flex:1" id="client-save-btn" onclick="saveClient()">✚ **إضافة**</button>  
      <button class="btn btn-secondary" onclick="document.getElementById('client-modal').classList.remove('open')">**إلغاء**</button>  
    </div>  
  </div>  
</div>  
</body>  
</html>  
