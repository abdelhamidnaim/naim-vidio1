<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes" />
  <title>NAIM Vidio — تسجيل الدخول</title>
  <link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans+Arabic:wght@300;400;500;600;700&display=swap" rel="stylesheet" />
  <style>
    /* ===== RESET & BASE ===== */
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    :root {
      --blue: #1877F2;
      --blue-h: #166FE5;
      --bg: #F0F2F5;
      --card: #FFFFFF;
      --border: #CED0D4;
      --text: #050505;
      --muted: #65676B;
      --font: 'IBM Plex Sans Arabic', sans-serif;
      --radius: 8px;
    }
    html, body {
      height: 100%;
      background: var(--bg);
      color: var(--text);
      font-family: var(--font);
      overflow-x: hidden;
    }

    /* ===== FULL LENGTH LOGIN PAGE ===== */
    .login-full {
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      min-height: 100vh;
      width: 100%;
      padding: 16px 20px 32px 20px;
      background: var(--bg);
    }

    /* ===== TOP SECTION ===== */
    .top-section {
      display: flex;
      flex-direction: column;
      align-items: center;
      padding-top: 24px;
      padding-bottom: 56px;
    }

    /* Language Selector (centered, above logo) */
    .lang-top {
      width: 100%;
      display: flex;
      justify-content: center;
      margin-bottom: 28px;
    }
    .lang-btn {
      display: flex;
      align-items: center;
      gap: 6px;
      background: transparent;
      border: none;
      font-family: var(--font);
      font-size: 16px;
      color: var(--muted);
      cursor: pointer;
      padding: 8px 14px;
      border-radius: 6px;
      transition: background .15s;
      position: relative;
    }
    .lang-btn:hover { background: rgba(0,0,0,0.05); }
    .lang-btn svg { display: none; }
    .lang-btn .arrow { font-size: 12px; margin-right: 2px; }

    .lang-dropdown {
      position: absolute;
      top: calc(100% + 4px);
      left: 50%;
      transform: translateX(-50%);
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      box-shadow: 0 4px 12px rgba(0,0,0,.15);
      padding: 6px 0;
      min-width: 190px;
      display: none;
      flex-direction: column;
      z-index: 20;
    }
    .lang-dropdown.open { display: flex; }
    .lang-item {
      padding: 8px 16px;
      font-size: 14px;
      color: var(--text);
      cursor: pointer;
      display: flex;
      align-items: center;
      gap: 8px;
      transition: background .15s;
      font-family: var(--font);
      background: transparent;
      border: none;
      width: 100%;
      text-align: right;
    }
    .lang-item:hover { background: #F0F2F5; }
    .lang-item .check { opacity: 0; transition: opacity .2s; }
    .lang-item.active .check { opacity: 1; color: var(--blue); }
    .lang-item .label { flex: 1; }

    /* ===== LOGO ===== */
    .app-logo {
      width: 100px;
      height: 100px;
      border-radius: 50%;
      object-fit: cover;
      background: var(--blue);
      box-shadow: 0 2px 8px rgba(0,0,0,.15);
      margin-bottom: 10px;
      flex-shrink: 0;
      border: 4px solid var(--bg);
    }
    .app-logo-fallback {
      width: 100px;
      height: 100px;
      border-radius: 50%;
      background: var(--blue);
      color: #fff;
      font-size: 40px;
      font-weight: 700;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 2px 8px rgba(0,0,0,.15);
      margin-bottom: 10px;
      border: 4px solid var(--bg);
      flex-shrink: 0;
    }

    .app-name {
      font-size: 28px;
      font-weight: 700;
      color: var(--blue);
      margin-bottom: 6px;
      letter-spacing: -0.5px;
    }
    .app-desc {
      text-align: center;
      font-size: 15px;
      color: var(--muted);
      margin-bottom: 16px;
      line-height: 1.4;
      max-width: 90%;
    }

    /* ===== MIDDLE SECTION (BUTTONS) ===== */
    .middle-section {
      width: 100%;
      max-width: 420px;
      margin: 0 auto;
      display: flex;
      flex-direction: column;
      gap: 14px;
      padding-bottom: 16px;
    }

    .btn-social {
      width: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 12px;
      padding: 14px 16px;
      border: none;
      border-radius: 6px;
      font-family: var(--font);
      font-size: 16px;
      font-weight: 700;
      color: #fff;
      cursor: pointer;
      transition: filter .15s, transform .1s;
      position: relative;
    }
    .btn-social:disabled { opacity: 0.7; cursor: not-allowed; }
    .btn-social:not(:disabled):hover { filter: brightness(1.08); }
    .btn-social:not(:disabled):active { transform: scale(0.97); }

    .btn-fb { background: #1877F2; }
    .btn-ig { background: linear-gradient(135deg,#f09433 0%,#e6683c 25%,#dc2743 50%,#cc2366 75%,#bc1888 100%); }
    .btn-tt { background: #010101; }

    /* ===== STATUS CIRCLE (أقصى يسار الزر) ===== */
    .btn-social { padding-left: 46px; }
    .status-circle {
      width: 20px;
      height: 20px;
      border-radius: 50%;
      flex-shrink: 0;
      border: 2px solid rgba(255,255,255,0.6);
      position: absolute;
      left: 14px;
      top: 50%;
      transform: translateY(-50%);
      transition: all 0.3s ease;
      background: transparent;
      color: #fff;
      font-size: 0;
    }
    .status-circle.idle { border-color: rgba(255,255,255,0.4); background: transparent; }
    .status-circle.loading { border-color: transparent; border-top-color: #fff; animation: spin 0.8s linear infinite; background: transparent; }
    .status-circle.connected { background: #31A24C; border-color: #31A24C; color: #fff; animation: none; font-size: 11px; display: flex; align-items: center; justify-content: center; }
    @keyframes spin { 0% { transform:rotate(0deg); } 100% { transform:rotate(360deg); } }

    .connected-note {
      padding: 10px 14px;
      background: #E7F3FF;
      border-radius: 6px;
      font-size: 14px;
      color: var(--blue);
      margin-bottom: 4px;
      display: none;
      text-align: center;
      width: 100%;
    }

    .btn-start {
      width: 100%;
      padding: 14px;
      background: var(--blue);
      border: none;
      border-radius: 6px;
      color: #fff;
      font-family: var(--font);
      font-size: 17px;
      font-weight: 700;
      cursor: pointer;
      transition: background .15s;
    }
    .btn-start:hover { background: var(--blue-h); }
    .btn-start:active { transform: scale(0.98); }

    /* ===== BOTTOM SECTION (FOOTER) ===== */
    .bottom-section {
      width: 100%;
      padding-top: 14px;
      margin-top: 24px;
      border-top: 1px solid var(--border);
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 6px;
    }
    .footer-links {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 6px 14px;
      font-size: 11px;
      color: var(--muted);
    }
    .footer-links a {
      color: var(--muted);
      text-decoration: none;
      transition: color .15s;
    }
    .footer-links a:hover { color: var(--blue); text-decoration: underline; }
    .footer-lang {
      font-size: 11px;
      color: var(--muted);
      cursor: pointer;
      background: transparent;
      border: none;
      font-family: var(--font);
      display: flex;
      align-items: center;
      gap: 5px;
    }
    .footer-lang svg { width: 13px; height: 13px; }
    .footer-lang:hover { color: var(--blue); }
    .footer-copy {
      font-size: 10px;
      color: var(--muted);
    }

    /* ===== TOAST ===== */
    .toast {
      position: fixed;
      bottom: 24px;
      left: 50%;
      transform: translateX(-50%) translateY(80px);
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 6px;
      padding: 11px 18px;
      font-size: 14px;
      box-shadow: 0 4px 12px rgba(0,0,0,.12);
      z-index: 999;
      transition: transform .3s cubic-bezier(.34,1.56,.64,1);
      display: flex;
      align-items: center;
      gap: 8px;
      white-space: nowrap;
    }
    .toast.show { transform: translateX(-50%) translateY(0); }

    /* ===== RESPONSIVE ===== */
    @media (max-width: 480px) {
      .login-full { padding: 12px 16px; }
      .app-logo, .app-logo-fallback { width: 90px; height: 90px; font-size: 36px; }
      .app-name { font-size: 24px; }
      .app-desc { font-size: 14px; }
      .btn-social { font-size: 15px; padding: 13px 14px; }
      .lang-btn { font-size: 13px; }
    }
    @media (max-width: 380px) {
      .app-logo, .app-logo-fallback { width: 80px; height: 80px; font-size: 32px; }
      .app-name { font-size: 22px; }
      .app-desc { font-size: 13px; }
      .btn-social { font-size: 14px; padding: 12px 12px; }
    }

    /* ===== PAGE 2 (APP) - Styles ===== */
    #pageApp {
      display: none;
      flex-direction: column;
      height: 100vh;
      background: var(--bg);
      width: 100%;
    }
    .app-nav {
      background: var(--card);
      border-bottom: 1px solid var(--border);
      padding: 0 16px;
      height: 56px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-shrink: 0;
      position: sticky;
      top: 0;
      z-index: 100;
    }
    .app-nav-left { display: flex; align-items: center; gap: 10px; }
    .back-btn {
      display: flex;
      align-items: center;
      justify-content: center;
      width: 38px;
      height: 38px;
      background: var(--blue);
      border: none;
      border-radius: 50%;
      cursor: pointer;
      flex-shrink: 0;
      transition: background .15s, transform .1s;
    }
    .back-btn:hover { background: var(--blue-h); }
    .back-btn:active { transform: scale(0.93); }
    .back-btn svg { width: 20px; height: 20px; fill: #fff; }

    .app-body {
      flex: 1;
      overflow-y: auto;
      padding: 16px 12px;
    }
    .app-grid {
      display: grid;
      grid-template-columns: 1fr;
      gap: 16px;
      max-width: 1080px;
      margin: 0 auto;
    }
    .card {
      background: var(--card);
      border-radius: 8px;
      box-shadow: 0 2px 4px rgba(0,0,0,0.08);
      border: 1px solid var(--border);
      padding: 16px;
    }
    .card-title {
      font-size: 14px;
      font-weight: 700;
      margin-bottom: 12px;
      display: flex;
      align-items: center;
      gap: 8px;
    }
    .card-title::after { content: ''; flex: 1; height: 1px; background: var(--border); }

    .dropzone {
      border: 2px dashed var(--border);
      border-radius: 8px;
      padding: clamp(24px, 6vw, 40px) 16px;
      text-align: center;
      cursor: pointer;
      transition: .2s;
      margin-bottom: 14px;
    }
    .dropzone:hover, .dropzone.over { border-color: var(--blue); background: #F7F8FA; }
    .dz-icon { font-size: clamp(32px, 8vw, 48px); margin-bottom: 8px; }
    .dz-title { font-size: clamp(15px, 4vw, 18px); font-weight: 600; margin-bottom: 5px; }
    .dz-sub { font-size: clamp(12px, 3vw, 14px); color: var(--muted); margin-bottom: 10px; }
    .dz-fmts { display: flex; gap: 6px; justify-content: center; flex-wrap: wrap; }
    .fmt { padding: 2px 9px; border-radius: 10px; background: #F0F2F5; border: 1px solid var(--border); font-size: 11px; color: var(--muted); }

    .counter-bar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 10px;
      opacity: 0;
      transform: translateY(4px);
      transition: .3s;
      flex-wrap: wrap;
      gap: 8px;
    }
    .counter-bar.show { opacity: 1; transform: none; }
    .cb-count { background: #F0F2F5; padding: 2px 10px; border-radius: 10px; font-size: 12px; color: var(--muted); }
    .btn-add { border: 1px solid var(--border); background: var(--card); padding: 6px 14px; border-radius: 6px; font-size: 12px; font-family: var(--font); cursor: pointer; }

    .video-list { display: flex; flex-direction: column; gap: 10px; }
    .vcard {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 8px;
      padding: 10px;
      display: grid;
      grid-template-columns: 46px 1fr auto;
      gap: 8px;
      align-items: start;
    }
    .vthumb { width: 46px; height: 46px; border-radius: 6px; background: #F0F2F5; border: 1px solid var(--border); overflow: hidden; position: relative; flex-shrink: 0; }
    .vthumb video { width: 100%; height: 100%; object-fit: cover; }
    .vplay { position: absolute; inset: 0; display: flex; align-items: center; justify-content: center; background: rgba(0,0,0,.3); color: #fff; font-size: 11px; }
    .vname { font-weight: 600; font-size: clamp(12px, 3vw, 14px); white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
    .vmeta { font-size: 11px; color: var(--muted); margin-bottom: 5px; }
    .card-stages { display: flex; gap: 3px; flex-wrap: wrap; }
    .cs { padding: 2px 7px; border-radius: 10px; font-size: 10px; border: 1px solid var(--border); background: #F0F2F5; color: var(--muted); }
    .cs-run { background: #E7F3FF; border-color: var(--blue); color: var(--blue); }
    .cs-ok { background: #E6F7E6; border-color: #31A24C; color: #31A24C; }
    .cs-dot { display: inline-block; width: 5px; height: 5px; border-radius: 50%; background: var(--blue); animation: pulse .8s infinite; }
    .vright { display: flex; flex-direction: column; align-items: flex-end; gap: 5px; }
    .vscore { font-weight: 600; font-size: 11px; padding: 2px 7px; border-radius: 10px; border: 1px solid var(--border); }
    .vhi { background: #E6F7E6; border-color: #31A24C; color: #31A24C; }
    .vmd { background: #FFF8E6; border-color: #F7B928; color: #c97d00; }
    .vlo { background: #FFE6E6; border-color: #E74C3C; color: #E74C3C; }
    .vdel { width: 28px; height: 28px; border-radius: 50%; border: 1px solid var(--border); background: transparent; color: var(--muted); cursor: pointer; display: flex; align-items: center; justify-content: center; font-size: 11px; }
    .vdel:hover { background: #FFE6E6; border-color: #E74C3C; color: #E74C3C; }

    .right-sidebar { display: flex; flex-direction: column; gap: 14px; }

    .state-card { display: none; }
    .state-card.show { display: block; }
    .sc-top { display: flex; align-items: center; gap: 10px; margin-bottom: 8px; }
    .sc-pulse { width: 9px; height: 9px; border-radius: 50%; background: var(--blue); animation: pulse .9s infinite; }
    .sc-pulse.done { background: #31A24C; animation: none; }
    .sc-title { font-weight: 600; font-size: clamp(14px, 3.5vw, 16px); }
    .sc-sub { font-size: clamp(12px, 3vw, 14px); color: var(--muted); }
    .prog-bar { height: 5px; background: #F0F2F5; border-radius: 4px; overflow: hidden; margin: 8px 0; }
    .prog-fill { height: 100%; background: var(--blue); border-radius: 4px; width: 0%; transition: width .55s ease; }
    .stage-pills { display: flex; gap: 4px; flex-wrap: wrap; }
    .sp { padding: 2px 7px; border-radius: 10px; font-size: 10px; border: 1px solid var(--border); background: #F0F2F5; color: var(--muted); }
    .sp-r { background: #E7F3FF; border-color: var(--blue); color: var(--blue); }
    .idle-hint { padding: 10px 0; font-size: clamp(13px, 3vw, 15px); color: var(--muted); text-align: center; }

    .success-banner { background: #E6F7E6; border: 1px solid #31A24C; border-radius: 8px; padding: 14px; display: none; }
    .success-banner.show { display: block; }
    .sb-head { font-weight: 700; font-size: clamp(14px, 3.5vw, 16px); display: flex; align-items: center; gap: 6px; margin-bottom: 10px; }
    .pub-grid { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 6px; margin-bottom: 10px; }
    .pub-cell { background: var(--card); border: 1px solid var(--border); border-radius: 6px; padding: 8px; text-align: center; }
    .pub-ico { font-size: 15px; }
    .pub-name { font-weight: 600; font-size: 11px; }
    .pub-time { font-size: 11px; color: var(--muted); }
    .btn-reset { width: 100%; padding: 10px; background: var(--blue); border: none; border-radius: 6px; color: #fff; font-weight: 600; font-size: 13px; font-family: var(--font); cursor: pointer; }

    .cal-empty { text-align: center; padding: 14px 0; color: var(--muted); font-size: 13px; }
    .cal-day { background: var(--card); border: 1px solid var(--border); border-radius: 6px; overflow: hidden; margin-bottom: 6px; }
    .cal-day-header { padding: 6px 10px; background: #F0F2F5; font-weight: 600; font-size: 12px; border-bottom: 1px solid var(--border); }
    .cal-entries { padding: 5px; display: flex; flex-direction: column; gap: 3px; }
    .cal-row { display: flex; align-items: center; gap: 7px; padding: 4px 7px; border-radius: 5px; font-size: 12px; }
    .plat-dot { width: 7px; height: 7px; border-radius: 50%; flex-shrink: 0; }
    .pd-fb { background: var(--blue); } .pd-ig { background: #E1306C; } .pd-tt { background: #010101; }
    .cal-name { flex: 1; color: var(--muted); white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
    .cal-time { font-weight: 600; color: var(--blue); background: #E7F3FF; padding: 0 7px; border-radius: 10px; font-size: 11px; flex-shrink: 0; }

    .q-card { display: flex; align-items: center; gap: 12px; }
    .q-ring { position: relative; width: clamp(44px, 12vw, 56px); height: clamp(44px, 12vw, 56px); flex-shrink: 0; }
    .q-ring svg { width: 100%; height: 100%; transform: rotate(-90deg); }
    .q-ring circle { fill: none; stroke-width: 6; stroke-linecap: round; }
    .qr-bg { stroke: var(--border); } .qr-fill { stroke: var(--blue); stroke-dasharray: 138; stroke-dashoffset: 138; transition: stroke-dashoffset 1s ease; }
    .q-num { position: absolute; inset: 0; display: flex; align-items: center; justify-content: center; font-weight: 700; font-size: clamp(11px, 3vw, 14px); }
    .q-text strong { display: block; font-weight: 600; font-size: clamp(13px, 3.2vw, 15px); }
    .q-text span { font-size: clamp(11px, 2.8vw, 13px); color: var(--muted); }

    .learn-feed { display: flex; flex-direction: column; gap: 5px; }
    .lf-item { display: flex; gap: 8px; padding: 7px 10px; background: var(--card); border: 1px solid var(--border); border-radius: 6px; font-size: 12px; align-items: flex-start; }
    .lf-text { color: var(--muted); line-height: 1.5; }
    .lf-text strong { color: var(--text); }

    @keyframes pulse { 0%,100%{opacity:1} 50%{opacity:.3} }

    @media (min-width: 600px) {
      .app-grid { grid-template-columns: 1fr 310px; }
      .app-body { padding: 20px 24px; }
    }
    @media (max-width: 599px) {
      .app-nav { padding: 0 12px; height: 50px; }
      .back-btn { font-size: 13px; }
      .app-body { padding: 12px 8px; }
      .vcard { grid-template-columns: 40px 1fr auto; }
      .vthumb { width: 40px; height: 40px; }
    }
  </style>
</head>
<body>

  <!-- ==========================================================
  CONFIGURATION (Logo & Name)
  ========================================================== -->
  <script>
    window.APP_CONFIG = {
      name: "NAIM Vidio",
      logo: "assets/logo.png" // غيّر هذا الرابط إلى شعارك
    };
  </script>

  <!-- ==========================================================
  PAGE 1 – FULL SCREEN LOGIN
  ========================================================== -->
  <div class="login-full" id="pageStart">

    <!-- TOP SECTION -->
    <div class="top-section">
      <!-- Language (top right) -->
      <div class="lang-top">
        <button class="lang-btn" id="langBtn" aria-label="اختيار اللغة">
          <svg viewBox="0 0 24 24"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-1 17.93c-3.95-.49-7-3.85-7-7.93 0-.62.08-1.21.21-1.79L9 15v1c0 1.1.9 2 2 2v1.93zm6.9-2.54c-.26-.81-1-1.39-1.9-1.39h-1v-3c0-.55-.45-1-1-1H8v-2h2c.55 0 1-.45 1-1V7h2c1.1 0 2-.9 2-2v-.41c2.93 1.19 5 4.06 5 7.41 0 2.08-.8 3.97-2.1 5.39z"/></svg>
          <span id="currentLangLabel">العربية</span>
          <span class="arrow">▼</span>
        </button>
        <div class="lang-dropdown" id="langDropdown">
          <button class="lang-item active" data-lang="ar" data-label="العربية">
            <span class="check">✓</span>
            <span class="label">العربية</span>
          </button>
          <button class="lang-item" data-lang="fr" data-label="Français (France)">
            <span class="check">✓</span>
            <span class="label">Français (France)</span>
          </button>
          <button class="lang-item" data-lang="en" data-label="English (US)">
            <span class="check">✓</span>
            <span class="label">English (US)</span>
          </button>
        </div>
      </div>

      <!-- Logo (dynamique) -->
      <img src="assets/logo.png" alt="Logo" class="app-logo" id="appLogo"
           onerror="this.style.display='none'; document.getElementById('logoFallback').style.display='flex';" />
      <div class="app-logo-fallback" id="logoFallback" style="display:none;">ن</div>

      <!-- App Name -->
      <div class="app-name" id="appName">NAIM Vidio</div>

      <!-- Description -->
      <div class="app-desc" id="appDesc">ارفع فيديوهاتك واترك الذكاء الاصطناعي يتولى النشر تلقائياً</div>
    </div>

    <!-- MIDDLE SECTION (Buttons) -->
    <div class="middle-section">
      <!-- Facebook -->
      <button class="btn-social btn-fb" id="btn-facebook" onclick="handleOAuth('facebook',this)">
        <svg width="22" height="22" viewBox="0 0 24 24" fill="white" style="flex-shrink:0"><path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/></svg>
        <span id="fbLabel">الدخول عبر Facebook</span>
        <span class="status-circle idle" id="sc-facebook"></span>
      </button>

      <!-- Instagram -->
      <button class="btn-social btn-ig" id="btn-instagram" onclick="handleOAuth('instagram',this)">
        <svg width="22" height="22" viewBox="0 0 24 24" fill="white" style="flex-shrink:0"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/></svg>
        <span id="igLabel">الدخول عبر Instagram</span>
        <span class="status-circle idle" id="sc-instagram"></span>
      </button>

      <!-- TikTok -->
      <button class="btn-social btn-tt" id="btn-tiktok" onclick="handleOAuth('tiktok',this)">
        <svg width="22" height="22" viewBox="0 0 24 24" fill="white" style="flex-shrink:0"><path d="M19.59 6.69a4.83 4.83 0 01-3.77-4.25V2h-3.45v13.67a2.89 2.89 0 01-2.88 2.5 2.89 2.89 0 01-2.89-2.89 2.89 2.89 0 012.89-2.89c.28 0 .54.04.79.1V9.01a6.27 6.27 0 00-.79-.05 6.34 6.34 0 00-6.34 6.34 6.34 6.34 0 006.34 6.34 6.34 6.34 0 006.33-6.34V8.69a8.22 8.22 0 004.8 1.54V6.78a4.85 4.85 0 01-1.03-.09z"/></svg>
        <span id="ttLabel">الدخول عبر TikTok</span>
        <span class="status-circle idle" id="sc-tiktok"></span>
      </button>

      <div class="connected-note" id="connectedNote"></div>
      <button class="btn-start" id="startBtn" style="display:none" onclick="startApp()">ابدأ الآن ←</button>
    </div>

    <!-- BOTTOM SECTION (Footer) -->
    <div class="bottom-section">
      <div class="footer-links">
        <a href="#" id="termsLink">شروط الاستخدام</a>
        <a href="#" id="privacyLink">سياسة الخصوصية</a>
        <span id="copyright">© 2026 NAIM Vidio</span>
      </div>
      <button class="footer-lang" id="footerLangBtn" aria-label="اختيار اللغة">
        <svg viewBox="0 0 24 24" width="16" height="16" fill="currentColor"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-1 17.93c-3.95-.49-7-3.85-7-7.93 0-.62.08-1.21.21-1.79L9 15v1c0 1.1.9 2 2 2v1.93zm6.9-2.54c-.26-.81-1-1.39-1.9-1.39h-1v-3c0-.55-.45-1-1-1H8v-2h2c.55 0 1-.45 1-1V7h2c1.1 0 2-.9 2-2v-.41c2.93 1.19 5 4.06 5 7.41 0 2.08-.8 3.97-2.1 5.39z"/></svg>
        <span id="footerLangLabel">العربية</span>
      </button>
    </div>
  </div>

  <!-- ==========================================================
  PAGE 2 – APP (سيتم إنشاؤها بواسطة JavaScript)
  ========================================================== -->
  <div id="pageApp"></div>

  <!-- ==========================================================
  TOAST
  ========================================================== -->
  <div class="toast" id="toast"><span id="toastIcon">✓</span><span id="toastText"></span></div>

  <script>
    // ============================================================
    // 0. APP CONFIG
    // ============================================================
    const APP_CONFIG = window.APP_CONFIG || { name: "NAIM Vidio", logo: "assets/logo.png" };

    // ============================================================
    // 1. TRANSLATIONS (i18n)
    // ============================================================
    const translations = {
      ar: {
        appName: APP_CONFIG.name,
        appDesc: 'ارفع فيديوهاتك واترك الذكاء الاصطناعي يتولى النشر تلقائياً',
        fbLabel: 'الدخول عبر Facebook',
        igLabel: 'الدخول عبر Instagram',
        ttLabel: 'الدخول عبر TikTok',
        startBtn: 'ابدأ الآن ←',
        terms: 'شروط الاستخدام',
        privacy: 'سياسة الخصوصية',
        copyright: `© 2026 ${APP_CONFIG.name}`,
        langLabel: 'العربية',
        connectedNote: (list) => `✅ متصل بـ: ${list.join('، ')}`,
        toastConnected: (p) => `تم ربط ${p} ✓`,
        toastWelcome: `مرحباً بك في ${APP_CONFIG.name} 🚀`,
        toastLang: (lang) => `تم تغيير اللغة إلى: ${lang}`,
        toastReset: 'تم التهيئة من جديد 🔄',
        uploadTitle: 'ارفع وانسَ',
        uploadDesc: 'النظام يحلّل، يعدّل، يكتب الوصف والهاشتاغات، ويختار أفضل وقت للنشر تلقائياً.',
        dropTitle: 'اسحب فيديوهاتك هنا',
        dropSub: 'أو انقر للاختيار — فيديو واحد أو عشرين دفعةً',
        videoCount: 'الفيديوهات المُرفوعة',
        addBtn: '+ إضافة',
        idleHint: 'ارفع فيديوهاتك — النظام يبدأ تلقائياً',
        publishDone: '🎉 تم النشر على جميع المنصات',
        resetBtn: '🔄 ارفع مجموعة جديدة',
        calendarTitle: '📅 تقويم النشر',
        calendarEmpty: 'سيظهر التقويم بعد الرفع',
        qualityTitle: '⭐ جودة المحتوى',
        noVideo: 'لا يوجد فيديو بعد',
        uploadHint: 'ارفع فيديو لرؤية التوقعات',
        learnTitle: '🧠 ما تعلّمه النظام',
        learnEmpty: 'يبدأ التعلم بعد أول نشر',
        navBack: 'رجوع',
        // Stage labels (مستخدمة في الكود)
        stageAnalyze: 'تحليل',
        stageMusic: 'موسيقى',
        stageEdit: 'مونتاج',
        stageCaption: 'وصف',
        stageHashtag: 'هاشتاغات',
        stageSchedule: 'جدولة',
        stagePublish: 'نشر',
        videoUnit: 'فيديو',
        toastProcessingWait: 'جاري المعالجة، انتظر',
        toastNoVideoFound: 'لم يتم العثور على فيديوهات',
        toastUploadedCount: (n) => `تم رفع ${n} فيديو`,
        toastNoDeleteProcessing: 'لا يمكن الحذف أثناء المعالجة',
        toastDeleted: 'تم الحذف',
        toastVideoReady: (name) => `تم تجهيز ${name} ✅`,
        toastAllPublished: 'تم نشر جميع الفيديوهات! 🎉',
        toastWaitFinish: 'انتظر حتى الانتهاء',
        processingLabel: (done, total) => `معالجة ${done}/${total}`,
        doneLabel: (name) => `تم: ${name}`,
        videoOfLabel: (done, total) => `الفيديو ${done}/${total}`,
        qualityAvgLabel: (avg) => `متوسط الجودة ${avg}%`,
        qualityBasedOn: (n) => `بناءً على ${n} فيديو`,
        publishDoneSub: 'كل الفيديوهات نُشرت تلقائياً',
        days: ['اليوم', 'غداً', 'بعد غد', 'اليوم الرابع', 'اليوم الخامس'],
        insights: [
          { ico: '📈', text: '<strong>TikTok</strong> يُعطي أفضل تفاعل في الساعة 19:20 لجمهورك' },
          { ico: '💡', text: 'الفيديوهات <strong>أقل من 45 ثانية</strong> تحصل على 2× مشاهدات' },
          { ico: '🕐', text: '<strong>Instagram</strong> يتفاعل أكثر في آخر الأسبوع' },
          { ico: '🏷️', text: 'الهاشتاغات <strong>#عمل #مشروع</strong> أفضل أداءً لجمهورك' },
          { ico: '🎵', text: 'الموسيقى الهادئة رفعت نسبة <strong>إتمام المشاهدة 34%</strong>' },
        ],
      },
      fr: {
        appName: APP_CONFIG.name,
        appDesc: 'Téléchargez vos vidéos et laissez l\'IA publier automatiquement.',
        fbLabel: 'Connexion avec Facebook',
        igLabel: 'Connexion avec Instagram',
        ttLabel: 'Connexion avec TikTok',
        startBtn: 'Commencer maintenant ←',
        terms: "Conditions d'utilisation",
        privacy: 'Politique de confidentialité',
        copyright: `© 2026 ${APP_CONFIG.name}`,
        langLabel: 'Français (France)',
        connectedNote: (list) => `✅ Connecté à: ${list.join(', ')}`,
        toastConnected: (p) => `Connecté à ${p} ✓`,
        toastWelcome: `Bienvenue sur ${APP_CONFIG.name} 🚀`,
        toastLang: (lang) => `Langue changée en: ${lang}`,
        toastReset: 'Réinitialisation terminée 🔄',
        uploadTitle: 'Téléchargez et oubliez',
        uploadDesc: "Le système analyse, monte, rédige la description et les hashtags, et choisit le meilleur moment pour publier automatiquement.",
        dropTitle: 'Glissez vos vidéos ici',
        dropSub: 'Ou cliquez pour choisir — une ou vingt vidéos à la fois',
        videoCount: 'Vidéos téléchargées',
        addBtn: '+ Ajouter',
        idleHint: 'Téléchargez vos vidéos — le système démarre automatiquement',
        publishDone: '🎉 Publié sur toutes les plateformes',
        resetBtn: '🔄 Télécharger un nouveau lot',
        calendarTitle: '📅 Calendrier de publication',
        calendarEmpty: 'Le calendrier apparaîtra après le téléchargement',
        qualityTitle: '⭐ Qualité du contenu',
        noVideo: 'Aucune vidéo pour le moment',
        uploadHint: 'Téléchargez une vidéo pour voir les prévisions',
        learnTitle: '🧠 Ce que le système a appris',
        learnEmpty: "L'apprentissage commence après la première publication",
        navBack: 'Retour',
        stageAnalyze: 'Analyse',
        stageMusic: 'Musique',
        stageEdit: 'Montage',
        stageCaption: 'Description',
        stageHashtag: 'Hashtags',
        stageSchedule: 'Planification',
        stagePublish: 'Publication',
        videoUnit: 'vidéo',
        toastProcessingWait: 'Traitement en cours, veuillez patienter',
        toastNoVideoFound: 'Aucune vidéo trouvée',
        toastUploadedCount: (n) => `${n} vidéo(s) téléchargée(s)`,
        toastNoDeleteProcessing: 'Suppression impossible pendant le traitement',
        toastDeleted: 'Supprimé',
        toastVideoReady: (name) => `${name} prêt ✅`,
        toastAllPublished: 'Toutes les vidéos ont été publiées ! 🎉',
        toastWaitFinish: 'Veuillez attendre la fin',
        processingLabel: (done, total) => `Traitement ${done}/${total}`,
        doneLabel: (name) => `Terminé : ${name}`,
        videoOfLabel: (done, total) => `Vidéo ${done}/${total}`,
        qualityAvgLabel: (avg) => `Qualité moyenne ${avg}%`,
        qualityBasedOn: (n) => `Basé sur ${n} vidéo(s)`,
        publishDoneSub: 'Toutes les vidéos ont été publiées automatiquement',
        days: ['Aujourd\'hui', 'Demain', 'Après-demain', 'Jour 4', 'Jour 5'],
        insights: [
          { ico: '📈', text: '<strong>TikTok</strong> offre le meilleur engagement à 19h20 pour votre audience' },
          { ico: '💡', text: 'Les vidéos de <strong>moins de 45 secondes</strong> obtiennent 2× plus de vues' },
          { ico: '🕐', text: '<strong>Instagram</strong> est plus actif en fin de semaine' },
          { ico: '🏷️', text: 'Les hashtags <strong>#travail #projet</strong> performent le mieux pour votre audience' },
          { ico: '🎵', text: 'La musique calme a augmenté le <strong>taux de visionnage complet de 34%</strong>' },
        ],
      },
      en: {
        appName: APP_CONFIG.name,
        appDesc: 'Upload your videos and let AI handle publishing automatically.',
        fbLabel: 'Continue with Facebook',
        igLabel: 'Continue with Instagram',
        ttLabel: 'Continue with TikTok',
        startBtn: 'Start now ←',
        terms: 'Terms of Service',
        privacy: 'Privacy Policy',
        copyright: `© 2026 ${APP_CONFIG.name}`,
        langLabel: 'English (US)',
        connectedNote: (list) => `✅ Connected to: ${list.join(', ')}`,
        toastConnected: (p) => `Connected to ${p} ✓`,
        toastWelcome: `Welcome to ${APP_CONFIG.name} 🚀`,
        toastLang: (lang) => `Language changed to: ${lang}`,
        toastReset: 'Reset complete 🔄',
        uploadTitle: 'Upload & Forget',
        uploadDesc: 'The system analyzes, edits, writes captions and hashtags, and selects the best time to publish automatically.',
        dropTitle: 'Drag your videos here',
        dropSub: 'Or click to choose — one or twenty videos at once',
        videoCount: 'Uploaded videos',
        addBtn: '+ Add',
        idleHint: 'Upload your videos — the system starts automatically',
        publishDone: '🎉 Published on all platforms',
        resetBtn: '🔄 Upload a new batch',
        calendarTitle: '📅 Publishing Calendar',
        calendarEmpty: 'The calendar will appear after uploading',
        qualityTitle: '⭐ Content Quality',
        noVideo: 'No video yet',
        uploadHint: 'Upload a video to see predictions',
        learnTitle: '🧠 What the system learned',
        learnEmpty: 'Learning starts after the first publication',
        navBack: 'Back',
        stageAnalyze: 'Analyze',
        stageMusic: 'Music',
        stageEdit: 'Edit',
        stageCaption: 'Caption',
        stageHashtag: 'Hashtags',
        stageSchedule: 'Schedule',
        stagePublish: 'Publish',
        videoUnit: 'video',
        toastProcessingWait: 'Processing in progress, please wait',
        toastNoVideoFound: 'No videos found',
        toastUploadedCount: (n) => `${n} video(s) uploaded`,
        toastNoDeleteProcessing: 'Cannot delete while processing',
        toastDeleted: 'Deleted',
        toastVideoReady: (name) => `${name} ready ✅`,
        toastAllPublished: 'All videos have been published! 🎉',
        toastWaitFinish: 'Please wait until it finishes',
        processingLabel: (done, total) => `Processing ${done}/${total}`,
        doneLabel: (name) => `Done: ${name}`,
        videoOfLabel: (done, total) => `Video ${done}/${total}`,
        qualityAvgLabel: (avg) => `Average quality ${avg}%`,
        qualityBasedOn: (n) => `Based on ${n} video(s)`,
        publishDoneSub: 'All videos were published automatically',
        days: ['Today', 'Tomorrow', 'Day after tomorrow', 'Day 4', 'Day 5'],
        insights: [
          { ico: '📈', text: '<strong>TikTok</strong> gives the best engagement at 7:20 PM for your audience' },
          { ico: '💡', text: 'Videos <strong>under 45 seconds</strong> get 2× more views' },
          { ico: '🕐', text: '<strong>Instagram</strong> engages more at the end of the week' },
          { ico: '🏷️', text: 'Hashtags <strong>#work #project</strong> perform best for your audience' },
          { ico: '🎵', text: 'Calm music increased the <strong>full watch rate by 34%</strong>' },
        ],
      }
    };

    // ============================================================
    // 2. LANGUAGE LOGIC
    // ============================================================
    let currentLang = localStorage.getItem('naim_lang') || 'ar';
    let currentTranslations = translations[currentLang] || translations.ar;

    function applyLanguage(lang) {
      currentLang = lang;
      currentTranslations = translations[lang] || translations.ar;
      localStorage.setItem('naim_lang', lang);

      const isRTL = lang === 'ar';
      document.documentElement.dir = isRTL ? 'rtl' : 'ltr';
      document.documentElement.lang = lang;
      document.body.dir = isRTL ? 'rtl' : 'ltr';
      document.body.style.direction = isRTL ? 'rtl' : 'ltr';

      // تحديث النصوص (الصفحة الرئيسية)
      document.getElementById('appName').textContent = currentTranslations.appName;
      document.getElementById('appDesc').textContent = currentTranslations.appDesc;
      document.getElementById('fbLabel').textContent = currentTranslations.fbLabel;
      document.getElementById('igLabel').textContent = currentTranslations.igLabel;
      document.getElementById('ttLabel').textContent = currentTranslations.ttLabel;
      const startBtn = document.getElementById('startBtn');
      if (startBtn.style.display !== 'none') startBtn.textContent = currentTranslations.startBtn;
      document.getElementById('termsLink').textContent = currentTranslations.terms;
      document.getElementById('privacyLink').textContent = currentTranslations.privacy;
      document.getElementById('copyright').textContent = currentTranslations.copyright;
      document.getElementById('currentLangLabel').textContent = currentTranslations.langLabel;
      document.getElementById('footerLangLabel').textContent = currentTranslations.langLabel;

      // تحديث القائمة المنسدلة
      document.querySelectorAll('.lang-item').forEach(item => {
        item.classList.toggle('active', item.dataset.lang === lang);
      });

      // تحديث الفول باك للشعار
      const fallback = document.getElementById('logoFallback');
      if (fallback.style.display !== 'none') {
        fallback.textContent = APP_CONFIG.name.charAt(0);
      }

      // تحديث الصفحة الثانية إن كانت ظاهرة
      const pageApp = document.getElementById('pageApp');
      if (pageApp.style.display !== 'none') {
        updateAppTranslations();
      }
    }

    // ============================================================
    // 3. LANGUAGE SELECTOR EVENTS
    // ============================================================
    (function initLang() {
      const btn = document.getElementById('langBtn');
      const dropdown = document.getElementById('langDropdown');
      const items = dropdown.querySelectorAll('.lang-item');
      const footerBtn = document.getElementById('footerLangBtn');

      applyLanguage(currentLang);

      function toggleDropdown(e) {
        e.stopPropagation();
        dropdown.classList.toggle('open');
      }

      btn.addEventListener('click', toggleDropdown);
      footerBtn.addEventListener('click', function(e) {
        e.preventDefault();
        dropdown.classList.toggle('open');
      });

      document.addEventListener('click', function(e) {
        if (!dropdown.contains(e.target) && e.target !== btn && e.target !== footerBtn) {
          dropdown.classList.remove('open');
        }
      });

      items.forEach(item => {
        item.addEventListener('click', function() {
          const lang = this.dataset.lang;
          applyLanguage(lang);
          dropdown.classList.remove('open');
          const label = this.querySelector('.label').textContent;
          showToast(currentTranslations.toastLang(label), '🌐');
        });
      });
    })();

    // ============================================================
    // 4. OAUTH SIMULATION
    // ============================================================
    const connected = { facebook: false, instagram: false, tiktok: false };
    const platformLabels = { facebook: 'Facebook', instagram: 'Instagram', tiktok: 'TikTok' };
    const OAUTH_URLS = {
      facebook: 'https://www.facebook.com/v18.0/dialog/oauth?client_id=YOUR_FB_APP_ID&redirect_uri=YOUR_REDIRECT_URI&scope=pages_manage_posts,instagram_basic&response_type=code',
      instagram: 'https://api.instagram.com/oauth/authorize?client_id=YOUR_IG_APP_ID&redirect_uri=YOUR_REDIRECT_URI&scope=user_profile,user_media&response_type=code',
      tiktok: 'https://www.tiktok.com/v2/auth/authorize?client_key=YOUR_TT_CLIENT_KEY&redirect_uri=YOUR_REDIRECT_URI&scope=user.info.basic,video.upload&response_type=code',
    };

    function handleOAuth(platform, btn) {
      if (connected[platform]) return;
      btn.disabled = true;
      const circle = document.getElementById('sc-' + platform);
      if (circle) {
        circle.className = 'status-circle loading';
        circle.textContent = '';
      }

      const url = OAUTH_URLS[platform];
      const popup = window.open(url, 'oauth_' + platform, 'width=600,height=700,scrollbars=yes,resizable=yes,top=100,left=200');

      setTimeout(() => {
        if (!popup || popup.closed) onOAuthSuccess(platform);
      }, 3000);

      const checkClosed = setInterval(() => {
        if (!popup || popup.closed) {
          clearInterval(checkClosed);
          if (!connected[platform]) {
            btn.disabled = false;
            const circle = document.getElementById('sc-' + platform);
            if (circle) {
              circle.className = 'status-circle idle';
              circle.textContent = '';
            }
          }
        }
      }, 500);
    }

    function onOAuthSuccess(platform) {
      connected[platform] = true;
      const btn = document.getElementById('btn-' + platform);
      if (btn) btn.disabled = false;
      const circle = document.getElementById('sc-' + platform);
      if (circle) {
        circle.className = 'status-circle connected';
        circle.textContent = '✓';
      }
      showToast(currentTranslations.toastConnected(platformLabels[platform]), '✓');

      const list = Object.entries(connected).filter(([, v]) => v).map(([k]) => platformLabels[k]);
      const note = document.getElementById('connectedNote');
      const sbtn = document.getElementById('startBtn');
      if (note) {
        note.style.display = 'block';
        note.textContent = currentTranslations.connectedNote(list);
      }
      if (sbtn) {
        sbtn.style.display = 'block';
        sbtn.textContent = currentTranslations.startBtn;
      }
    }

    // ============================================================
    // 5. APP NAVIGATION
    // ============================================================
    function goToPage(i) {
      if (i === 1) {
        document.getElementById('pageStart').style.display = 'none';
        document.getElementById('pageApp').style.display = 'flex';
        // إنشاء محتوى الصفحة الثانية إذا لم يكن موجوداً
        if (!document.getElementById('pageApp').innerHTML.trim()) {
          buildAppPage();
        }
        updateAppTranslations();
      } else {
        document.getElementById('pageApp').style.display = 'none';
        document.getElementById('pageStart').style.display = 'flex';
        resetAll();
      }
    }

    function startApp() {
      goToPage(1);
      showToast(currentTranslations.toastWelcome, '🚀');
    }

    function logout() {
      goToPage(0);
    }

    // ============================================================
    // 6. TOAST HELPER
    // ============================================================
    let toastTimer;
    function showToast(msg, icon = '✓') {
      const toast = document.getElementById('toast');
      document.getElementById('toastIcon').textContent = icon;
      document.getElementById('toastText').textContent = msg;
      toast.classList.add('show');
      clearTimeout(toastTimer);
      toastTimer = setTimeout(() => toast.classList.remove('show'), 3500);
    }

    // ============================================================
    // 7. BUILD APP PAGE (PAGE 2)
    // ============================================================
    function buildAppPage() {
      const appHTML = `
        <nav class="app-nav">
          <div class="app-nav-left">
            <div style="display:flex; align-items:center; gap:6px; font-size:clamp(18px, 4vw, 22px); font-weight:700; color:var(--blue);">
              <div style="width:34px; height:34px; background:var(--blue); border-radius:50%; display:flex; align-items:center; justify-content:center; color:#fff; font-weight:700; font-size:15px;">${APP_CONFIG.name.charAt(0)}</div>
              <span id="navAppName">${APP_CONFIG.name}</span>
            </div>
          </div>
          <button class="back-btn" onclick="logout()" aria-label="رجوع">
            <svg viewBox="0 0 24 24"><path d="M20 11H7.83l5.59-5.59L12 4l-8 8 8 8 1.41-1.41L7.83 13H20v-2z"/></svg>
          </button>
        </nav>
        <div class="app-body">
          <div class="app-grid">
            <!-- COLONNE GAUCHE -->
            <div>
              <div class="card">
                <h2 style="font-size:clamp(18px, 5vw, 24px); font-weight:700; margin-bottom:4px;" id="uploadTitle">ارفع وانسَ</h2>
                <p style="font-size:clamp(13px, 3.2vw, 15px); color:var(--muted); margin-bottom:14px;" id="uploadDesc">النظام يحلّل، يعدّل، يكتب الوصف والهاشتاغات، ويختار أفضل وقت للنشر تلقائياً.</p>
                <div class="dropzone" id="dz"
                     onclick="document.getElementById('fi').click()"
                     ondragover="event.preventDefault();this.classList.add('over')"
                     ondragleave="this.classList.remove('over')"
                     ondrop="onDrop(event)">
                  <div class="dz-icon">🎬</div>
                  <div class="dz-title" id="dropTitle">اسحب فيديوهاتك هنا</div>
                  <div class="dz-sub" id="dropSub">أو انقر للاختيار — فيديو واحد أو عشرين دفعةً</div>
                  <div class="dz-fmts">
                    <span class="fmt">MP4</span><span class="fmt">MOV</span>
                    <span class="fmt">AVI</span><span class="fmt">WEBM</span><span class="fmt">MKV</span>
                  </div>
                </div>
                <input type="file" id="fi" multiple accept="video/*" onchange="onFiles(this.files)" style="display:none">
                <div class="counter-bar" id="cbar">
                  <span style="font-size:clamp(14px, 3.5vw, 16px); font-weight:600;" id="videoCountLabel">الفيديوهات المُرفوعة</span>
                  <div style="display:flex; gap:8px; align-items:center; flex-wrap:wrap;">
                    <span class="cb-count" id="cnum">0 فيديو</span>
                    <button class="btn-add" onclick="document.getElementById('fi').click()" id="addBtn">+ إضافة</button>
                  </div>
                </div>
                <div class="video-list" id="vlist"></div>
              </div>
            </div>
            <!-- COLONNE DROITE -->
            <div class="right-sidebar">
              <div class="card state-card" id="state-card">
                <div class="sc-top">
                  <div class="sc-pulse" id="sc-pulse"></div>
                  <div>
                    <div class="sc-title" id="sc-title">في الانتظار</div>
                    <div class="sc-sub" id="sc-sub">ارفع فيديوهاتك للبدء</div>
                  </div>
                </div>
                <div class="prog-bar"><div class="prog-fill" id="pfill"></div></div>
                <div class="stage-pills" id="spills"></div>
              </div>
              <div class="idle-hint" id="idle-hint">ارفع فيديوهاتك — النظام يبدأ تلقائياً</div>

              <div class="success-banner" id="sb">
                <div class="sb-head" id="publishDone">🎉 تم النشر على جميع المنصات</div>
                <div class="pub-grid">
                  <div class="pub-cell"><div class="pub-ico">📘</div><div class="pub-name" style="color:var(--blue);">Facebook</div><div class="pub-time" id="pt-fb">—</div></div>
                  <div class="pub-cell"><div class="pub-ico">📸</div><div class="pub-name" style="color:#E1306C;">Instagram</div><div class="pub-time" id="pt-ig">—</div></div>
                  <div class="pub-cell"><div class="pub-ico">🎵</div><div class="pub-name">TikTok</div><div class="pub-time" id="pt-tt">—</div></div>
                </div>
                <button class="btn-reset" onclick="resetAll()" id="resetBtn">🔄 ارفع مجموعة جديدة</button>
              </div>

              <div class="card">
                <div class="card-title" id="calendarTitle">📅 تقويم النشر</div>
                <div id="calendar"><div class="cal-empty" id="calendarEmpty">سيظهر التقويم بعد الرفع</div></div>
              </div>

              <div class="card">
                <div class="card-title" id="qualityTitle">⭐ جودة المحتوى</div>
                <div class="q-card">
                  <div class="q-ring">
                    <svg viewBox="0 0 50 50">
                      <circle class="qr-bg" cx="25" cy="25" r="22"/>
                      <circle class="qr-fill" id="qfill" cx="25" cy="25" r="22"/>
                    </svg>
                    <div class="q-num" id="qnum">—</div>
                  </div>
                  <div class="q-text">
                    <strong id="qtitle">لا يوجد فيديو بعد</strong>
                    <span id="qsub">ارفع فيديو لرؤية التوقعات</span>
                  </div>
                </div>
              </div>

              <div class="card">
                <div class="card-title" id="learnTitle">🧠 ما تعلّمه النظام</div>
                <div class="learn-feed" id="lfeed">
                  <div style="text-align:center;padding:10px 0;font-size:12px;color:var(--muted);" id="learnEmpty">يبدأ التعلم بعد أول نشر</div>
                </div>
              </div>
            </div>
          </div>
        </div>
      `;
      document.getElementById('pageApp').innerHTML = appHTML;
    }

    // ============================================================
    // 8. UPDATE APP TRANSLATIONS
    // ============================================================
    function updateAppTranslations() {
      const t = currentTranslations;
      const el = (id) => document.getElementById(id);
      if (el('uploadTitle')) el('uploadTitle').textContent = t.uploadTitle;
      if (el('uploadDesc')) el('uploadDesc').textContent = t.uploadDesc;
      if (el('dropTitle')) el('dropTitle').textContent = t.dropTitle;
      if (el('dropSub')) el('dropSub').textContent = t.dropSub;
      if (el('videoCountLabel')) el('videoCountLabel').textContent = t.videoCount;
      if (el('addBtn')) el('addBtn').textContent = t.addBtn;
      if (el('idle-hint')) el('idle-hint').textContent = t.idleHint;
      if (el('publishDone')) el('publishDone').textContent = t.publishDone;
      if (el('resetBtn')) el('resetBtn').textContent = t.resetBtn;
      if (el('calendarTitle')) el('calendarTitle').textContent = t.calendarTitle;
      if (el('calendarEmpty')) el('calendarEmpty').textContent = t.calendarEmpty;
      if (el('qualityTitle')) el('qualityTitle').textContent = t.qualityTitle;
      if (el('qtitle')) el('qtitle').textContent = t.noVideo;
      if (el('qsub')) el('qsub').textContent = t.uploadHint;
      if (el('learnTitle')) el('learnTitle').textContent = t.learnTitle;
      if (el('learnEmpty')) el('learnEmpty').textContent = t.learnEmpty;
      if (el('navBackLabel')) el('navBackLabel').textContent = t.navBack;
      if (el('navAppName')) el('navAppName').textContent = t.appName;
    }

    // ============================================================
    // 9. APP LOGIC (VIDEO UPLOAD, PROCESSING)
    // ============================================================
    let videos = [], processing = false, allPublished = false, curIdx = 0, timers = [], vcnt = 0;
    const STAGES = [
      { key: 'analyze', icon: '🔍', dur: 2200 },
      { key: 'music', icon: '🎵', dur: 1800 },
      { key: 'edit', icon: '✂️', dur: 2600 },
      { key: 'caption', icon: '✍️', dur: 1600 },
      { key: 'hashtag', icon: '#️⃣', dur: 1200 },
      { key: 'schedule', icon: '📅', dur: 1400 },
      { key: 'publish', icon: '📤', dur: 1800 },
    ];
    function stageLabel(key) {
      const k = 'stage' + key.charAt(0).toUpperCase() + key.slice(1);
      return currentTranslations[k] || key;
    }
    const TIMESETS = [{ fb: '18:40', ig: '20:05', tt: '19:20' }, { fb: '17:55', ig: '19:30', tt: '18:45' }, { fb: '20:10', ig: '21:00', tt: '20:30' }, { fb: '12:30', ig: '13:15', tt: '12:00' }];
    const $ = id => document.getElementById(id);

    function onDrop(e) { e.preventDefault(); const dz = document.getElementById('dz'); if (dz) dz.classList.remove('over'); if (e.dataTransfer.files.length) addFiles(e.dataTransfer.files); }
    function onFiles(fl) { if (fl.length) addFiles(fl); }

    function addFiles(fl) {
      if (processing) { showToast(currentTranslations.toastProcessingWait, '⏳'); return; }
      let n = 0;
      for (const f of fl) {
        if (!f.type.startsWith('video/')) continue;
        videos.push({ id: ++vcnt, file: f, name: f.name, size: f.size, status: 'waiting', stages: {}, score: 0, times: { fb: null, ig: null, tt: null }, published: { fb: false, ig: false, tt: false }, publishTime: { fb: null, ig: null, tt: null } });
        n++;
      }
      if (!n) { showToast(currentTranslations.toastNoVideoFound, '⚠️'); return; }
      showToast(currentTranslations.toastUploadedCount(n), '📤');
      render();
      updateCtr();
      const stateCard = document.getElementById('state-card');
      if (stateCard) stateCard.classList.add('show');
      const idleHint = document.getElementById('idle-hint');
      if (idleHint) idleHint.style.display = 'none';
      if (!processing) startProc();
    }

    function render() {
      const vl = document.getElementById('vlist');
      if (!vl) return;
      if (!videos.length) { vl.innerHTML = ''; return; }
      let h = '';
      for (const v of videos) {
        let sh = '';
        for (const sk of STAGES) {
          const st = v.stages[sk.key];
          let cls = '', dot = '';
          if (st === 'running') { cls = 'cs-run'; dot = '<span class="cs-dot"></span>'; } else if (st === 'done') cls = 'cs-ok';
          sh += `<span class="cs ${cls}">${dot}${stageLabel(sk.key)}</span>`;
        }
        const sc = v.score >= 70 ? 'vhi' : v.score >= 40 ? 'vmd' : 'vlo';
        h += `<div class="vcard">
          <div class="vthumb"><video src="${URL.createObjectURL(v.file)}" muted></video><div class="vplay">▶</div></div>
          <div><div class="vname">${esc(v.name)}</div><div class="vmeta">${fmt(v.size)}</div><div class="card-stages">${sh}</div></div>
          <div class="vright"><div class="vscore ${sc}">${v.score ? v.score + '%' : '—'}</div><button class="vdel" onclick="removeVideo(${v.id})">✕</button></div>
        </div>`;
      }
      vl.innerHTML = h;
      vl.querySelectorAll('.vthumb video').forEach(v => {
        v.addEventListener('mouseenter', () => v.play().catch(() => {}));
        v.addEventListener('mouseleave', () => { v.pause(); v.currentTime = 0; });
      });
    }

    function esc(s) { const d = document.createElement('div'); d.textContent = s; return d.innerHTML; }
    function fmt(b) { if (b < 1024) return b + 'B'; if (b < 1048576) return (b / 1024).toFixed(1) + 'KB'; return (b / 1048576).toFixed(1) + 'MB'; }

    function removeVideo(id) {
      if (processing) { showToast(currentTranslations.toastNoDeleteProcessing, '⛔'); return; }
      videos = videos.filter(v => v.id !== id);
      render();
      updateCtr();
      if (!videos.length) {
        const stateCard = document.getElementById('state-card');
        if (stateCard) stateCard.classList.remove('show');
        const idleHint = document.getElementById('idle-hint');
        if (idleHint) idleHint.style.display = 'block';
        resetQ();
        const sb = document.getElementById('sb');
        if (sb) sb.classList.remove('show');
        const calendar = document.getElementById('calendar');
        if (calendar) calendar.innerHTML = `<div class="cal-empty">${currentTranslations.calendarEmpty}</div>`;
        const lfeed = document.getElementById('lfeed');
        if (lfeed) lfeed.innerHTML = `<div style="text-align:center;padding:10px 0;font-size:12px;color:var(--muted);">${currentTranslations.learnEmpty}</div>`;
      }
      showToast(currentTranslations.toastDeleted, '🗑️');
    }

    function updateCtr() { const n = videos.length; const cnum = document.getElementById('cnum'); if (cnum) cnum.textContent = n + ' ' + currentTranslations.videoUnit; const cbar = document.getElementById('cbar'); if (cbar) cbar.classList.toggle('show', n > 0); }

    function startProc() {
      if (processing || !videos.length) return;
      allPublished = false;
      const sb = document.getElementById('sb');
      if (sb) sb.classList.remove('show');
      for (const v of videos) { v.status = 'waiting'; v.stages = {}; v.score = 0; v.published = { fb: false, ig: false, tt: false }; v.publishTime = { fb: null, ig: null, tt: null }; v.times = { fb: null, ig: null, tt: null }; }
      render();
      processing = true;
      curIdx = 0;
      nextVideo();
    }

    function nextVideo() {
      if (curIdx >= videos.length) { finishAll(); return; }
      const v = videos[curIdx];
      v.status = 'processing';
      v.score = Math.floor(Math.random() * 40) + 55;
      const ts = TIMESETS[Math.floor(Math.random() * TIMESETS.length)];
      v.times = { ...ts };
      let si = 0;

      function runStage() {
        if (si >= STAGES.length) {
          v.status = 'done';
          const now = new Date();
          const pad = n => String(n).padStart(2, '0');
          const t = `${pad(now.getHours())}:${pad(now.getMinutes())}`;
          v.publishTime = { fb: t, ig: t, tt: t };
          v.published = { fb: true, ig: true, tt: true };
          render();
          const done = videos.filter(x => x.status === 'done').length;
          setState('processing', currentTranslations.processingLabel(done, videos.length), currentTranslations.doneLabel(v.name), (done / videos.length) * 100, Object.keys(v.stages));
          showToast(currentTranslations.toastVideoReady(v.name));
          curIdx++;
          setTimeout(nextVideo, 600);
          return;
        }
        const sk = STAGES[si];
        v.stages[sk.key] = 'running';
        render();
        const done = videos.filter(x => x.status === 'done').length;
        setState('processing', stageLabel(sk.key) + ' ' + sk.icon, currentTranslations.videoOfLabel(done + 1, videos.length), ((done + (si / STAGES.length)) / videos.length) * 100, Object.keys(v.stages));
        setTimeout(() => { v.stages[sk.key] = 'done'; render(); si++; runStage(); }, sk.dur + Math.random() * 800);
      }
      runStage();
    }

    function setState(status, title, sub, prog, stages = []) {
      const stateCard = document.getElementById('state-card');
      if (stateCard) stateCard.classList.add('show');
      const pulse = document.getElementById('sc-pulse');
      if (pulse) pulse.className = 'sc-pulse' + (status === 'done' ? ' done' : '');
      const scTitle = document.getElementById('sc-title');
      if (scTitle) scTitle.textContent = title;
      const scSub = document.getElementById('sc-sub');
      if (scSub) scSub.textContent = sub;
      const pfill = document.getElementById('pfill');
      if (pfill) pfill.style.width = Math.min(100, prog) + '%';
      const spills = document.getElementById('spills');
      if (spills) spills.innerHTML = STAGES.map(sk => `<span class="sp ${stages.includes(sk.key) ? 'sp-r' : ''}">${sk.icon} ${stageLabel(sk.key)}</span>`).join('');
      const idleHint = document.getElementById('idle-hint');
      if (idleHint) idleHint.style.display = 'none';
    }

    function finishAll() {
      processing = false;
      allPublished = true;
      setState('done', currentTranslations.publishDone, currentTranslations.publishDoneSub, 100, STAGES.map(s => s.key));
      const sb = document.getElementById('sb');
      if (sb) sb.classList.add('show');
      const v = videos[0];
      const ptFb = document.getElementById('pt-fb');
      if (ptFb) ptFb.textContent = v.publishTime.fb || '—';
      const ptIg = document.getElementById('pt-ig');
      if (ptIg) ptIg.textContent = v.publishTime.ig || '—';
      const ptTt = document.getElementById('pt-tt');
      if (ptTt) ptTt.textContent = v.publishTime.tt || '—';
      buildCal();
      updateQ();
      buildFeed();
      showToast(currentTranslations.toastAllPublished);
    }

    function buildCal() {
      const cal = document.getElementById('calendar');
      if (!cal) return;
      if (!videos.length) { cal.innerHTML = `<div class="cal-empty">${currentTranslations.calendarEmpty}</div>`; return; }
      const gr = {};
      for (let i = 0; i < videos.length; i++) { const v = videos[i]; if (!v.times.fb) continue; const d = Math.floor(i / 3) % 5; if (!gr[d]) gr[d] = []; gr[d].push(v); }
      const keys = Object.keys(gr).sort((a, b) => a - b);
      if (!keys.length) { cal.innerHTML = `<div class="cal-empty">${currentTranslations.calendarEmpty}</div>`; return; }
      const days = currentTranslations.days || [];
      cal.innerHTML = keys.map(dk => `<div class="cal-day"><div class="cal-day-header">${days[parseInt(dk)] || ('+' + (parseInt(dk)+1))}</div><div class="cal-entries">${gr[dk].map(v => ['fb','ig','tt'].filter(p=>v.times[p]).map(p=>`<div class="cal-row"><span class="plat-dot pd-${p}"></span><span class="cal-name">${esc(v.name)}</span><span class="cal-time">${v.times[p]}</span></div>`).join('')).join('')}</div></div>`).join('');
    }

    function updateQ() {
      if (!videos.length) { resetQ(); return; }
      const avg = Math.round(videos.reduce((s, v) => s + v.score, 0) / videos.length);
      const c = 2 * Math.PI * 22;
      const qfill = document.getElementById('qfill');
      if (qfill) { qfill.style.strokeDasharray = c; qfill.style.strokeDashoffset = c - (avg / 100) * c; }
      const qnum = document.getElementById('qnum');
      if (qnum) qnum.textContent = avg + '%';
      const qtitle = document.getElementById('qtitle');
      if (qtitle) qtitle.textContent = currentTranslations.qualityAvgLabel(avg);
      const qsub = document.getElementById('qsub');
      if (qsub) qsub.textContent = currentTranslations.qualityBasedOn(videos.length);
    }

    function resetQ() {
      const qfill = document.getElementById('qfill');
      if (qfill) qfill.style.strokeDashoffset = 138;
      const qnum = document.getElementById('qnum');
      if (qnum) qnum.textContent = '—';
      const qtitle = document.getElementById('qtitle');
      if (qtitle) qtitle.textContent = currentTranslations.noVideo;
      const qsub = document.getElementById('qsub');
      if (qsub) qsub.textContent = currentTranslations.uploadHint;
    }

    function buildFeed() {
      const lfeed = document.getElementById('lfeed');
      if (!lfeed) return;
      if (!allPublished || !videos.length) { lfeed.innerHTML = `<div style="text-align:center;padding:10px 0;font-size:12px;color:var(--muted);">${currentTranslations.learnEmpty}</div>`; return; }
      const insights = currentTranslations.insights || [];
      lfeed.innerHTML = [...insights].sort(() => Math.random() - .5).slice(0, 4).map(i => `<div class="lf-item"><span>${i.ico}</span><div class="lf-text">${i.text}</div></div>`).join('');
    }

    function resetAll() {
      if (processing) { showToast(currentTranslations.toastWaitFinish, '⏳'); return; }
      timers.forEach(clearTimeout);
      timers = [];
      videos = [];
      processing = false;
      allPublished = false;
      curIdx = 0;
      render();
      updateCtr();
      const stateCard = document.getElementById('state-card');
      if (stateCard) stateCard.classList.remove('show');
      const idleHint = document.getElementById('idle-hint');
      if (idleHint) idleHint.style.display = 'block';
      const pfill = document.getElementById('pfill');
      if (pfill) pfill.style.width = '0%';
      const spills = document.getElementById('spills');
      if (spills) spills.innerHTML = '';
      const sb = document.getElementById('sb');
      if (sb) sb.classList.remove('show');
      const calendar = document.getElementById('calendar');
      if (calendar) calendar.innerHTML = `<div class="cal-empty">${currentTranslations.calendarEmpty}</div>`;
      resetQ();
      const lfeed = document.getElementById('lfeed');
      if (lfeed) lfeed.innerHTML = `<div style="text-align:center;padding:10px 0;font-size:12px;color:var(--muted);">${currentTranslations.learnEmpty}</div>`;
      showToast(currentTranslations.toastReset, '🔄');
    }

    // ============================================================
    // 10. EXPOSE GLOBALS
    // ============================================================
    window.startApp = startApp;
    window.logout = logout;
    window.goHome = logout;
    window.handleOAuth = handleOAuth;
    window.onDrop = onDrop;
    window.onFiles = onFiles;
    window.removeVideo = removeVideo;
    window.resetAll = resetAll;
    window.showToast = showToast;
    window.onOAuthSuccess = onOAuthSuccess;

    console.log('✅ NAIM Vidio - Full screen style Facebook avec status circles réparées');
  </script>
</body>
</html>
