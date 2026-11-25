<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Ma dictée pas à pas — Atelier CM1</title>
  <style>
    /* =========================================================================
       1. VARIABLES & DESIGN SYSTEM DOUX (100% AUTONOME, SANS CDN EXTERNE)
       ========================================================================= */
    :root {
      --bg-cream: #FAF8F5;
      --bg-sand: #F2EDE4;
      --bg-white: #FFFFFF;
      --text-main: #24303C;
      --text-muted: #5C6B77;
      --primary-slate: #3B6E8C;
      --primary-slate-dark: #2B536B;
      --primary-slate-light: #EBF3F8;
      --sage: #4A8B71;
      --sage-dark: #376B56;
      --sage-light: #E8F4EF;
      --sage-border: #B8DDD0;
      --amber: #D98A3C;
      --amber-dark: #B56E27;
      --amber-light: #FDF3E7;
      --amber-border: #F2CFA5;
      --coral: #D45D48;
      --coral-light: #FCECE9;
      --border-soft: #E2DBD0;
      --shadow-sm: 0 2px 6px rgba(36, 48, 60, 0.06);
      --shadow-md: 0 6px 18px rgba(36, 48, 60, 0.09);
      --radius-md: 14px;
      --radius-lg: 22px;
      --radius-xl: 28px;
      --font-sans: system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      -webkit-tap-highlight-color: transparent;
    }

    body {
      background-color: var(--bg-cream);
      color: var(--text-main);
      font-family: var(--font-sans);
      font-size: 17px;
      line-height: 1.55;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
    }

    /* Mode Accessibilité "Texte aéré" (Dyslexie / Troubles de la lecture) */
    body.dyslexic-mode {
      letter-spacing: 0.07em;
      word-spacing: 0.22em;
      line-height: 1.95;
      font-size: 18px;
    }

    button {
      font-family: inherit;
      cursor: pointer;
      border: none;
      background: none;
      color: inherit;
    }

    input, textarea, select {
      font-family: inherit;
      font-size: inherit;
      color: var(--text-main);
    }

    /* =========================================================================
       2. BARRE DE NAVIGATION SUPÉRIEURE
       ========================================================================= */
    .topbar {
      background: var(--bg-white);
      border-bottom: 2px solid var(--border-soft);
      position: sticky;
      top: 0;
      z-index: 30;
      box-shadow: var(--shadow-sm);
    }

    .topbar-inner {
      max-width: 1020px;
      margin: 0 auto;
      padding: 12px 18px;
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
    }

    .brand {
      display: flex;
      align-items: center;
      gap: 12px;
      text-align: left;
    }

    .brand-icon {
      width: 46px;
      height: 46px;
      border-radius: 15px;
      background: var(--sage);
      color: #fff;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-shrink: 0;
      box-shadow: 0 3px 0 var(--sage-dark);
    }

    .brand-title {
      font-size: 1.35rem;
      font-weight: 800;
      color: var(--text-main);
      line-height: 1.1;
    }

    .brand-title span {
      color: var(--sage);
    }

    .brand-sub {
      font-size: 0.8rem;
      color: var(--text-muted);
      font-weight: 600;
      margin-top: 2px;
    }

    .topbar-actions {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      gap: 10px;
    }

    .pill-btn {
      padding: 9px 14px;
      border-radius: 13px;
      font-weight: 700;
      font-size: 0.9rem;
      display: inline-flex;
      align-items: center;
      gap: 7px;
      transition: transform 0.1s ease, background-color 0.15s ease;
    }

    .pill-btn:active {
      transform: translateY(2px);
    }

    .btn-aere {
      background: var(--bg-sand);
      border: 2px solid var(--border-soft);
      color: var(--text-main);
    }

    .btn-aere.active {
      background: var(--sage-light);
      border-color: var(--sage);
      color: var(--sage-dark);
    }

    .student-chip {
      background: var(--primary-slate-light);
      border: 2px solid #C2DAE8;
      padding: 6px 12px;
      border-radius: 14px;
      display: inline-flex;
      align-items: center;
      gap: 8px;
      font-weight: 700;
      font-size: 0.92rem;
      color: var(--primary-slate-dark);
    }

    .student-avatar {
      width: 28px;
      height: 28px;
      border-radius: 50%;
      background: var(--primary-slate);
      color: #fff;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      font-weight: 800;
      font-size: 0.85rem;
    }

    .btn-teacher {
      background: var(--primary-slate);
      color: #fff;
      box-shadow: 0 3px 0 var(--primary-slate-dark);
    }

    .btn-teacher:hover {
      background: var(--primary-slate-dark);
    }

    /* =========================================================================
       3. CONTENEUR PRINCIPAL & CARTES
       ========================================================================= */
    .main-container {
      flex: 1;
      max-width: 1020px;
      width: 100%;
      margin: 0 auto;
      padding: 24px 18px 48px;
    }

    .card {
      background: var(--bg-white);
      border: 2px solid var(--border-soft);
      border-radius: var(--radius-lg);
      padding: 22px;
      box-shadow: var(--shadow-sm);
    }

    .section-heading {
      font-size: 1.15rem;
      font-weight: 800;
      margin: 22px 0 12px;
      display: flex;
      align-items: center;
      gap: 10px;
      color: var(--text-main);
    }

    .step-badge {
      width: 30px;
      height: 30px;
      border-radius: 50%;
      background: var(--primary-slate);
      color: #fff;
      font-size: 0.9rem;
      font-weight: 800;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      flex-shrink: 0;
    }

    /* Grilles adaptatives */
    .grid-2 {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 14px;
    }

    .grid-3 {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(270px, 1fr));
      gap: 14px;
    }

    /* =========================================================================
       4. GROS BOUTONS PÉDAGOGIQUES
       ========================================================================= */
    .btn-big {
      padding: 15px 26px;
      border-radius: 18px;
      font-weight: 800;
      font-size: 1.1rem;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      transition: transform 0.1s ease, filter 0.15s ease;
    }

    .btn-big:active:not(:disabled) {
      transform: translateY(3px);
    }

    .btn-big:disabled {
      opacity: 0.45;
      cursor: not-allowed;
    }

    .btn-sage {
      background: var(--sage);
      color: #fff;
      box-shadow: 0 4px 0 var(--sage-dark);
    }

    .btn-sage:hover:not(:disabled) {
      filter: brightness(1.05);
    }

    .btn-slate {
      background: var(--primary-slate);
      color: #fff;
      box-shadow: 0 4px 0 var(--primary-slate-dark);
    }

    .btn-amber {
      background: var(--amber-light);
      color: #7C4410;
      border: 2px solid var(--amber-border);
      box-shadow: 0 3px 0 var(--amber-border);
    }

    .btn-soft {
      background: var(--bg-sand);
      color: var(--text-main);
      border: 2px solid var(--border-soft);
    }

    /* =========================================================================
       5. SÉLECTION DICTÉES & NIVEAUX (ACCUEIL ÉLÈVE)
       ========================================================================= */
    .choice-card {
      background: var(--bg-white);
      border: 2px solid var(--border-soft);
      border-radius: var(--radius-lg);
      padding: 18px;
      text-align: left;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      gap: 10px;
      transition: all 0.15s ease;
    }

    .choice-card:hover {
      border-color: var(--primary-slate);
      transform: translateY(-2px);
    }

    .choice-card.selected {
      background: var(--sage-light);
      border-color: var(--sage);
      box-shadow: 0 0 0 3px rgba(74, 139, 113, 0.18);
    }

    .tag {
      display: inline-flex;
      align-items: center;
      gap: 5px;
      padding: 4px 10px;
      border-radius: 99px;
      font-size: 0.78rem;
      font-weight: 800;
      text-transform: uppercase;
      letter-spacing: 0.03em;
    }

    .tag-sage { background: var(--sage); color: #fff; }
    .tag-sand { background: var(--bg-sand); color: var(--text-muted); }
    .tag-amber { background: var(--amber-light); color: var(--amber-dark); border: 1px solid var(--amber-border); }

    /* =========================================================================
       6. ZONE D'EXERCICE : NIVEAUX 1 & 2 (ÉTIQUETTES)
       ========================================================================= */
    .audio-bar {
      background: var(--primary-slate-light);
      border: 2px solid #C2DAE8;
      border-radius: var(--radius-lg);
      padding: 16px;
      display: flex;
      flex-direction: column;
      gap: 12px;
    }

    .audio-buttons {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
    }

    .audio-btn {
      background: var(--bg-white);
      border: 2px solid #B5D2E3;
      color: var(--primary-slate-dark);
      padding: 10px 15px;
      border-radius: 14px;
      font-weight: 800;
      font-size: 0.95rem;
      display: inline-flex;
      align-items: center;
      gap: 8px;
      box-shadow: 0 2px 0 #B5D2E3;
    }

    .audio-btn:hover {
      background: #F6FAFD;
    }

    .audio-btn.playing {
      background: var(--primary-slate);
      color: #fff;
      border-color: var(--primary-slate-dark);
    }

    .drop-zone {
      min-height: 92px;
      padding: 16px;
      border-radius: var(--radius-md);
      border: 2px dashed var(--sage);
      background: var(--bg-cream);
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      gap: 10px;
      transition: background-color 0.15s ease;
    }

    .drop-zone.drag-over {
      background: var(--sage-light);
    }

    .pool-zone {
      min-height: 82px;
      padding: 16px;
      border-radius: var(--radius-md);
      background: var(--bg-sand);
      border: 2px solid var(--border-soft);
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      gap: 12px;
    }

    .word-tile {
      background: var(--bg-white);
      border: 2px solid #C7BEB0;
      border-radius: 14px;
      padding: 11px 17px;
      font-size: 1.2rem;
      font-weight: 800;
      color: var(--text-main);
      box-shadow: 0 3px 0 #C7BEB0;
      user-select: none;
      transition: transform 0.1s ease, background-color 0.15s ease;
    }

    .word-tile:hover {
      border-color: var(--primary-slate);
      background: #F8FBFD;
    }

    .word-tile.tile-ok {
      background: var(--sage-light);
      border-color: var(--sage);
      color: var(--sage-dark);
      box-shadow: 0 3px 0 var(--sage);
    }

    .word-tile.tile-warn {
      background: var(--amber-light);
      border-color: var(--amber);
      color: #7C4410;
      box-shadow: 0 3px 0 var(--amber);
    }

    /* =========================================================================
       7. NIVEAUX 3 & 4 : TEXTE FLUIDE CONTINU SANS CASES AUTOUR DES MOTS
       ========================================================================= */
    .fluent-text-box {
      background: var(--bg-cream);
      border: 2px solid var(--border-soft);
      border-radius: var(--radius-md);
      padding: 24px 26px;
      font-size: 1.45rem;
      line-height: 2.25;
      color: var(--text-main);
      font-weight: 600;
    }

    .clickable-word {
      display: inline;
      padding: 3px 5px;
      border-radius: 8px;
      cursor: pointer;
      transition: background-color 0.15s ease, color 0.15s ease;
    }

    .clickable-word:hover {
      background-color: #EAE3D5;
    }

    .clickable-word.is-editing {
      background-color: var(--primary-slate);
      color: #FFFFFF;
    }

    .clickable-word.has-correction {
      background-color: var(--primary-slate-light);
      color: var(--primary-slate-dark);
      text-decoration: underline;
      text-decoration-color: var(--primary-slate);
      text-decoration-thickness: 2px;
      text-underline-offset: 5px;
    }

    .clickable-word.is-validated-ok {
      background-color: var(--sage-light);
      color: var(--sage-dark);
      text-decoration: underline;
      text-decoration-color: var(--sage);
      text-decoration-thickness: 2px;
      text-underline-offset: 5px;
    }

    .clickable-word.is-validated-err {
      background-color: var(--amber-light);
      color: #7C4410;
      text-decoration: underline;
      text-decoration-color: var(--amber);
      text-decoration-thickness: 2px;
      text-underline-offset: 5px;
    }

    .clickable-word.hint-pulse {
      background-color: #FDE5C4;
      color: #7C4410;
    }

    .clickable-word.speaking-now {
      background-color: #FDE5C4;
      color: #1A2332;
    }

    .old-word-strike {
      text-decoration: line-through;
      opacity: 0.55;
      font-size: 0.82em;
      margin-right: 4px;
      font-weight: 400;
    }

    /* =========================================================================
       8. ZONES DE SAISIE, CLAVIER D'ACCENTS & RELECTURE GUIDÉE
       ========================================================================= */
    .text-input-large {
      width: 100%;
      padding: 15px 18px;
      border-radius: 16px;
      border: 2px solid var(--primary-slate);
      background: var(--bg-cream);
      font-size: 1.25rem;
      font-weight: 700;
      line-height: 1.6;
      outline: none;
    }

    .text-input-large:focus {
      background: var(--bg-white);
      box-shadow: 0 0 0 4px rgba(59, 110, 140, 0.16);
    }

    .accent-bar {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      gap: 6px;
      margin-top: 10px;
    }

    .accent-key {
      min-width: 38px;
      height: 38px;
      padding: 0 8px;
      border-radius: 10px;
      background: var(--bg-sand);
      border: 1px solid var(--border-soft);
      font-weight: 800;
      font-size: 1.05rem;
      display: inline-flex;
      align-items: center;
      justify-content: center;
    }

    .accent-key:hover {
      background: var(--primary-slate-light);
      border-color: var(--primary-slate);
    }

    /* Étapes de relecture guidée Niveau 5 */
    .review-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
      gap: 10px;
      margin-top: 12px;
    }

    .review-step-card {
      background: var(--bg-white);
      border: 2px solid var(--amber-border);
      border-radius: 15px;
      padding: 13px;
      text-align: left;
      transition: all 0.15s ease;
    }

    .review-step-card.active {
      border-color: var(--amber);
      background: #FFFDF9;
      box-shadow: 0 0 0 3px rgba(217, 138, 60, 0.18);
    }

    .review-step-card.checked {
      border-color: var(--sage);
      background: var(--sage-light);
    }

    /* =========================================================================
       9. BANNIÈRES DE FEEDBACK, MODALES & CONFETTIS CSS
       ========================================================================= */
    .feedback-banner {
      border-radius: var(--radius-lg);
      padding: 18px 20px;
      display: flex;
      align-items: flex-start;
      gap: 14px;
      margin-top: 18px;
      animation: popIn 0.25s ease;
    }

    .feedback-success {
      background: var(--sage-light);
      border: 2px solid var(--sage);
      color: #1F4536;
    }

    .feedback-retry {
      background: var(--amber-light);
      border: 2px solid var(--amber);
      color: #6E3B0C;
    }

    .toast-box {
      position: fixed;
      bottom: 20px;
      right: 20px;
      z-index: 60;
      display: flex;
      flex-direction: column;
      gap: 8px;
      max-width: 360px;
      pointer-events: none;
    }

    .toast-item {
      padding: 13px 18px;
      border-radius: 16px;
      color: #fff;
      font-weight: 800;
      font-size: 0.95rem;
      box-shadow: var(--shadow-md);
      animation: popIn 0.22s ease;
    }

    .modal-backdrop {
      position: fixed;
      inset: 0;
      background: rgba(36, 48, 60, 0.45);
      z-index: 50;
      display: none;
      align-items: center;
      justify-content: center;
      padding: 16px;
    }

    .modal-backdrop.open {
      display: flex;
    }

    .modal-panel {
      background: var(--bg-white);
      border-radius: var(--radius-xl);
      max-width: 440px;
      width: 100%;
      padding: 26px;
      box-shadow: var(--shadow-md);
      border: 2px solid var(--border-soft);
      animation: popIn 0.22s ease;
    }

    /* Tableau suivi enseignant */
    .table-wrap {
      overflow-x: auto;
      background: var(--bg-white);
      border: 2px solid var(--border-soft);
      border-radius: var(--radius-lg);
    }

    table {
      width: 100%;
      border-collapse: collapse;
      text-align: left;
    }

    th {
      background: var(--bg-sand);
      padding: 13px 16px;
      font-size: 0.8rem;
      text-transform: uppercase;
      color: var(--text-muted);
      border-bottom: 2px solid var(--border-soft);
    }

    td {
      padding: 14px 16px;
      border-bottom: 1px solid var(--border-soft);
      font-size: 0.95rem;
    }

    /* Barre de progression */
    .progress-track {
      width: 100%;
      height: 12px;
      background: var(--bg-sand);
      border-radius: 99px;
      overflow: hidden;
      margin-top: 12px;
    }

    .progress-fill {
      height: 100%;
      background: var(--sage);
      border-radius: 99px;
      transition: width 0.35s ease;
    }

    /* Animations douces */
    @keyframes popIn {
      from { opacity: 0; transform: scale(0.95) translateY(6px); }
      to { opacity: 1; transform: scale(1) translateY(0); }
    }

    .confetti-piece {
      position: fixed;
      width: 10px;
      height: 10px;
      border-radius: 3px;
      pointer-events: none;
      z-index: 70;
      animation: confettiFall 1.4s ease-out forwards;
    }

    @keyframes confettiFall {
      0% { transform: translateY(0) rotate(0deg); opacity: 1; }
      100% { transform: translateY(240px) rotate(540deg); opacity: 0; }
    }

    @media (max-width: 640px) {
      .fluent-text-box {
        font-size: 1.22rem;
        padding: 16px;
        line-height: 2.1;
      }
      .btn-big {
        width: 100%;
      }
    }
  </style>
</head>
<body>

  <!-- BARRE DE NAVIGATION -->
  <header class="topbar">
    <div class="topbar-inner">
      <button type="button" class="brand" onclick="navigateTo('home')">
        <div class="brand-icon" aria-hidden="true">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.4" stroke-linecap="round" stroke-linejoin="round">
            <path d="M2 3h6a4 4 0 0 1 4 4v14a3 3 0 0 0-3-3H2z"/>
            <path d="M22 3h-6a4 4 0 0 0-4 4v14a3 3 0 0 1 3-3h7z"/>
          </svg>
        </div>
        <div>
          <div class="brand-title">Ma dictée <span>pas à pas</span></div>
          <div class="brand-sub">Atelier d'orthographe progressif • CM1</div>
        </div>
      </button>

      <div class="topbar-actions">
        <button type="button" id="btn-dyslexic" class="pill-btn btn-aere" onclick="toggleDyslexicMode()" title="Aérer les lettres et les lignes">
          <svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.3">
            <polyline points="4 7 4 4 20 4 20 7"/><line x1="9" y1="20" x2="15" y2="20"/><line x1="12" y1="4" x2="12" y2="20"/>
          </svg>
          <span>Texte aéré</span>
        </button>

        <div id="student-badge-wrap" style="display:none;">
          <span class="student-chip">
            <span class="student-avatar" id="student-avatar">E</span>
            <span id="student-name-label">Élève</span>
            <button type="button" onclick="openStudentModal()" style="text-decoration:underline; font-size:0.8rem; margin-left:4px;">Changer</button>
          </span>
        </div>

        <button type="button" id="btn-teacher-toggle" class="pill-btn btn-teacher" onclick="handleTeacherButtonClick()">
          <svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.3">
            <path d="M22 10v6M2 10l10-5 10 5-10 5z"/><path d="M6 12v5c3 3 9 3 12 0v-5"/>
          </svg>
          <span id="btn-teacher-text">Espace Enseignant</span>
        </button>
      </div>
    </div>
  </header>

  <!-- CONTENEUR PRINCIPAL RENDU EN JS -->
  <main id="app-root" class="main-container"></main>

  <!-- NOTIFICATIONS BIENVEILLANTES -->
  <div id="toast-box" class="toast-box"></div>

  <!-- MODALE IDENTIFICATION ÉLÈVE -->
  <div id="modal-student" class="modal-backdrop">
    <div class="modal-panel">
      <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:12px;">
        <h2 style="font-size:1.3rem; font-weight:800;">Qui fait la dictée ?</h2>
        <button type="button" onclick="closeModal('modal-student')" style="font-size:1.4rem; padding:4px 10px;">✕</button>
      </div>
      <p style="color:var(--text-muted); font-size:0.95rem; margin-bottom:16px;">
        Écris ton prénom ou ton pseudonyme pour enregistrer tes progrès.
      </p>
      <form onsubmit="submitStudentName(event)">
        <label style="display:block; font-size:0.82rem; font-weight:800; text-transform:uppercase; color:var(--text-muted); margin-bottom:6px;">
          Ton prénom ou pseudo
        </label>
        <input type="text" id="input-student-name" required maxlength="24" placeholder="Ex : Léo, Maya, Sam..."
          class="text-input-large" style="margin-bottom:14px;" />

        <div id="known-students-area" style="display:none; margin-bottom:16px;">
          <div style="font-size:0.8rem; font-weight:800; color:var(--text-muted); margin-bottom:8px;">Ou clique sur ton prénom :</div>
          <div id="known-students-chips" style="display:flex; flex-wrap:wrap; gap:8px;"></div>
        </div>

        <button type="submit" class="btn-big btn-sage" style="width:100%;">
          C'est parti !
        </button>
      </form>
    </div>
  </div>

  <!-- MODALE PIN ENSEIGNANT -->
  <div id="modal-pin" class="modal-backdrop">
    <div class="modal-panel">
      <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:12px;">
        <h2 style="font-size:1.3rem; font-weight:800;">Accès Enseignant</h2>
        <button type="button" onclick="closeModal('modal-pin')" style="font-size:1.4rem; padding:4px 10px;">✕</button>
      </div>
      <p style="color:var(--text-muted); font-size:0.95rem; margin-bottom:10px;">
        Saisissez le code secret (code par défaut : <strong>1234</strong>).
      </p>
      <form onsubmit="submitTeacherPin(event)">
        <input type="password" id="input-pin" inputmode="numeric" maxlength="6" required placeholder="••••"
          class="text-input-large" style="text-align:center; letter-spacing:0.3em; margin-bottom:12px;" />
        <p id="pin-error" style="display:none; color:var(--coral); font-weight:800; font-size:0.9rem; text-align:center; margin-bottom:12px;">
          Code incorrect. Essayez 1234.
        </p>
        <button type="submit" class="btn-big btn-slate" style="width:100%;">
          Entrer dans l'espace enseignant
        </button>
      </form>
    </div>
  </div>

  <!-- MODALE CONFIRMATION SUPPRESSION -->
  <div id="modal-confirm" class="modal-backdrop">
    <div class="modal-panel">
      <h3 id="confirm-title" style="font-size:1.2rem; font-weight:800; margin-bottom:8px;">Confirmation</h3>
      <p id="confirm-msg" style="color:var(--text-muted); font-size:0.95rem; margin-bottom:20px;"></p>
      <div style="display:flex; gap:10px;">
        <button type="button" class="btn-big btn-soft" style="flex:1; font-size:1rem;" onclick="closeModal('modal-confirm')">Annuler</button>
        <button type="button" id="confirm-ok-btn" class="btn-big" style="flex:1; font-size:1rem; background:var(--coral); color:#fff;">Supprimer</button>
      </div>
    </div>
  </div>

  <script>
    /* =========================================================================
       1. STOCKAGE SÉCURISÉ (localStorage + repli automatique en mémoire vive)
       ========================================================================= */
    const memoryFallback = {};
    function safeGetStorage(key) {
      try {
        return window.localStorage.getItem(key);
      } catch (e) {
        return memoryFallback[key] || null;
      }
    }
    function safeSetStorage(key, val) {
      memoryFallback[key] = val;
      try {
        window.localStorage.setItem(key, val);
      } catch (e) {
        /* Mode navigation privée ou iframe restreinte : le repli mémoire prend le relais */
      }
    }

    const STORAGE_DICTATIONS = 'ma_dictee_cm1_dictations_v3';
    const STORAGE_RESULTS = 'ma_dictee_cm1_results_v3';
    const STORAGE_STUDENT = 'ma_dictee_cm1_student_v3';

    /* =========================================================================
       2. DEUX DICTÉES CM1 PRÉ-ENREGISTRÉES ET COMPLÈTES (6 NIVEAUX CHACUNE)
       ========================================================================= */
    const INITIAL_DICTATIONS = [
      {
        id: "dictee-oiseaux-jardin",
        title: "Les oiseaux du jardin",
        rawText: "Les petits oiseaux chantent dans le jardin. Le soleil brille et réchauffe les fleurs rouges. Un chat noir observe les moineaux avec attention.",
        enabledLevels: { 1: true, 2: true, 3: true, 4: true, 5: true, 6: true },
        sentences: [
          {
            text: "Les petits oiseaux chantent dans le jardin.",
            chunks: ["Les petits oiseaux", "chantent", "dans le jardin."],
            words: ["Les", "petits", "oiseaux", "chantent", "dans", "le", "jardin."],
            // Niveau 3 : 1 erreur ciblée sur la première phrase
            level3Errors: [
              {
                wordIndex: 1,
                wrongWord: "petit",
                correctWord: "petits",
                category: "Accord dans le groupe nominal",
                hintNature: "Observe l'accord de l'adjectif dans le groupe nominal « Les ... oiseaux ».",
                explanation: "On écrit « petits » avec un -s car le nom « oiseaux » est au pluriel."
              }
            ],
            // Niveau 6 : Une seule transformation grammaticale
            level6: {
              instruction: "Passe le groupe sujet au singulier : remplace « Les petits oiseaux » par « Le petit oiseau ».",
              targetSentence: "Le petit oiseau chante dans le jardin.",
              explanation: "Au singulier, « petit » et « oiseau » perdent la marque du pluriel, et le verbe « chantent » devient « chante » (-e avec il)."
            }
          },
          {
            text: "Le soleil brille et réchauffe les fleurs rouges.",
            chunks: ["Le soleil", "brille", "et réchauffe", "les fleurs rouges."],
            words: ["Le", "soleil", "brille", "et", "réchauffe", "les", "fleurs", "rouges."],
            // Niveau 3 : 2 erreurs ciblées
            level3Errors: [
              {
                wordIndex: 3,
                wrongWord: "est",
                correctWord: "et",
                category: "Homophone étudié (et / est)",
                hintNature: "Vérifie l'homophone : peux-tu dire « et puis » ?",
                explanation: "On écrit « et » (sans s) car on peut le remplacer par « et puis ». Ce n'est pas le verbe être."
              },
              {
                wordIndex: 7,
                wrongWord: "rouge.",
                correctWord: "rouges.",
                category: "Accord dans le groupe nominal",
                hintNature: "Regarde l'accord de l'adjectif de couleur avec « les fleurs ».",
                explanation: "L'adjectif « rouges » s'accorde au pluriel avec le nom féminin pluriel « les fleurs »."
              }
            ],
            level6: {
              instruction: "Remplace « les fleurs rouges » par « la fleur rouge ».",
              targetSentence: "Le soleil brille et réchauffe la fleur rouge.",
              explanation: "Avec le déterminant singulier « la », le nom « fleur » et l'adjectif « rouge » ne prennent pas de -s."
            }
          },
          {
            text: "Un chat noir observe les moineaux avec attention.",
            chunks: ["Un chat noir", "observe", "les moineaux", "avec attention."],
            words: ["Un", "chat", "noir", "observe", "les", "moineaux", "avec", "attention."],
            level3Errors: [
              {
                wordIndex: 3,
                wrongWord: "observent",
                correctWord: "observe",
                category: "Accord sujet-verbe",
                hintNature: "Cherche le sujet du verbe : qui est-ce qui observe ?",
                explanation: "Le sujet « Un chat noir » est au singulier (il), donc le verbe se termine par -e : « observe »."
              },
              {
                wordIndex: 5,
                wrongWord: "moineau",
                correctWord: "moineaux",
                category: "Pluriel des noms",
                hintNature: "Observe le déterminant « les » juste avant le nom d'oiseau.",
                explanation: "Après « les », le nom « moineau » est au pluriel et prend un -x car il se termine par -eau."
              }
            ],
            level6: {
              instruction: "Remplace « Un chat noir » par « Des chats noirs ».",
              targetSentence: "Des chats noirs observent les moineaux avec attention.",
              explanation: "Avec le sujet au pluriel « Des chats noirs » (ils), le verbe « observer » prend -ent : « observent »."
            }
          }
        ],
        // Niveau 4 : Paragraphe de relecture autonome (3 erreurs ciblées non soulignées)
        level4Paragraph: {
          words: [
            "Les", "petits", "oiseaux", "chante", "dans", "le", "jardin.",
            "Le", "soleil", "brille", "est", "réchauffe", "les", "fleurs", "rouge."
          ],
          errors: [
            {
              wordIndex: 3,
              wrongWord: "chante",
              correctWord: "chantent",
              category: "Accord sujet-verbe",
              explanation: "Le sujet « Les petits oiseaux » est au pluriel (ils), donc le verbe prend -ent."
            },
            {
              wordIndex: 10,
              wrongWord: "est",
              correctWord: "et",
              category: "Homophone grammatical",
              explanation: "On peut dire « et puis » : il faut écrire « et »."
            },
            {
              wordIndex: 14,
              wrongWord: "rouge.",
              correctWord: "rouges.",
              category: "Accord dans le groupe nominal",
              explanation: "« les fleurs » est au pluriel : l'adjectif « rouges » prend un -s."
            }
          ]
        }
      },
      {
        id: "dictee-promenade-foret",
        title: "Une promenade en forêt",
        rawText: "Hier, Léa a marché sur un sentier calme. Les grands arbres protègent les animaux sauvages. Ils sont heureux dans cette belle forêt.",
        enabledLevels: { 1: true, 2: true, 3: true, 4: true, 5: true, 6: true },
        sentences: [
          {
            text: "Hier, Léa a marché sur un sentier calme.",
            chunks: ["Hier,", "Léa a marché", "sur un sentier calme."],
            words: ["Hier,", "Léa", "a", "marché", "sur", "un", "sentier", "calme."],
            level3Errors: [
              {
                wordIndex: 2,
                wrongWord: "à",
                correctWord: "a",
                category: "Homophone étudié (a / à)",
                hintNature: "Vérifie l'homophone : peux-tu dire « avait » ?",
                explanation: "On peut dire « Léa avait marché » : c'est l'auxiliaire avoir « a » sans accent."
              }
            ],
            level6: {
              instruction: "Remplace « Léa » par « Léa et Tom ».",
              targetSentence: "Hier, Léa et Tom ont marché sur un sentier calme.",
              explanation: "Avec deux personnes (« Léa et Tom » = ils), le verbe avoir « a » devient « ont »."
            }
          },
          {
            text: "Les grands arbres protègent les animaux sauvages.",
            chunks: ["Les grands arbres", "protègent", "les animaux sauvages."],
            words: ["Les", "grands", "arbres", "protègent", "les", "animaux", "sauvages."],
            level3Errors: [
              {
                wordIndex: 1,
                wrongWord: "grand",
                correctWord: "grands",
                category: "Accord dans le groupe nominal",
                hintNature: "Vérifie l'accord dans le groupe nominal « Les ... arbres ».",
                explanation: "« arbres » est au pluriel, donc l'adjectif « grands » prend un -s."
              },
              {
                wordIndex: 3,
                wrongWord: "protège",
                correctWord: "protègent",
                category: "Accord sujet-verbe",
                hintNature: "Regarde la terminaison du verbe avec le sujet « Les grands arbres ».",
                explanation: "Le sujet « Les grands arbres » est au pluriel (ils), donc le verbe prend -ent."
              }
            ],
            level6: {
              instruction: "Remplace « Les grands arbres » par « Le grand arbre ».",
              targetSentence: "Le grand arbre protège les animaux sauvages.",
              explanation: "Au singulier, « grand » et « arbre » perdent le -s, et le verbe « protègent » devient « protège »."
            }
          },
          {
            text: "Ils sont heureux dans cette belle forêt.",
            chunks: ["Ils sont heureux", "dans", "cette belle forêt."],
            words: ["Ils", "sont", "heureux", "dans", "cette", "belle", "forêt."],
            level3Errors: [
              {
                wordIndex: 1,
                wrongWord: "son",
                correctWord: "sont",
                category: "Homophone étudié (son / sont)",
                hintNature: "Vérifie l'homophone juste après « Ils » (peux-tu dire « étaient » ?).",
                explanation: "On peut dire « Ils étaient heureux » : c'est le verbe être « sont »."
              },
              {
                wordIndex: 5,
                wrongWord: "bel",
                correctWord: "belle",
                category: "Accord dans le groupe nominal",
                hintNature: "Le nom « forêt » est féminin : observe l'adjectif devant lui.",
                explanation: "« forêt » est un nom féminin (« cette »), on écrit donc « belle »."
              }
            ],
            level6: {
              instruction: "Remplace « Ils » par « Il » (au singulier).",
              targetSentence: "Il est heureux dans cette belle forêt.",
              explanation: "Au singulier avec « Il », le verbe être « sont » devient « est ». « heureux » conserve son -x final."
            }
          }
        ],
        level4Paragraph: {
          words: [
            "Hier,", "Léa", "à", "marché", "sur", "un", "sentier", "calme.",
            "Les", "grand", "arbres", "protègent", "les", "animaux", "sauvage."
          ],
          errors: [
            {
              wordIndex: 2,
              wrongWord: "à",
              correctWord: "a",
              category: "Homophone (a / à)",
              explanation: "On peut dire « avait marché » : on écrit « a » sans accent."
            },
            {
              wordIndex: 9,
              wrongWord: "grand",
              correctWord: "grands",
              category: "Accord dans le groupe nominal",
              explanation: "« Les ... arbres » est au pluriel : il faut un -s à « grands »."
            },
            {
              wordIndex: 14,
              wrongWord: "sauvage.",
              correctWord: "sauvages.",
              category: "Accord dans le groupe nominal",
              explanation: "L'adjectif « sauvages » s'accorde avec « les animaux » (pluriel)."
            }
          ]
        }
      }
    ];

    /* =========================================================================
       3. ÉTAT GLOBAL DE L'APPLICATION
       ========================================================================= */
    const state = {
      view: 'home', // 'home' | 'exercise' | 'summary' | 'teacher'
      teacherTab: 'dictations', // 'dictations' | 'tracking'
      dyslexicMode: false,
      studentName: safeGetStorage(STORAGE_STUDENT) || '',
      dictations: [],
      results: [],
      selectedDictationId: 'dictee-oiseaux-jardin',
      selectedLevel: 1,
      exercise: {
        sentenceIndex: 0,
        score: 0,
        attempts: 0,
        errorsLog: [],
        verified: false,
        isCorrect: false,
        // Niveaux 1 & 2
        availableItems: [],
        placedItems: [],
        // Niveaux 3 & 4
        editingWordIdx: null,
        userCorrections: {},
        hintStep: 0,
        level4AttemptCount: 0,
        level4FoundCount: 0,
        level4ShowHints: false,
        level4Revealed: false,
        // Niveau 5
        dictationText: "",
        activeSegmentIndex: -1,
        guidedReviewStep: 0,
        reviewChecks: { 1: false, 2: false, 3: false, 4: false },
        wordComparison: [],
        // Niveau 6
        transformText: "",
        transformDiff: [],
        speakingWordIndex: -1
      },
      teacherDraft: null
    };

    function loadAppState() {
      const rawDicts = safeGetStorage(STORAGE_DICTATIONS);
      if (rawDicts) {
        try {
          const parsed = JSON.parse(rawDicts);
          state.dictations = (Array.isArray(parsed) && parsed.length > 0) ? parsed : JSON.parse(JSON.stringify(INITIAL_DICTATIONS));
        } catch (e) {
          state.dictations = JSON.parse(JSON.stringify(INITIAL_DICTATIONS));
        }
      } else {
        state.dictations = JSON.parse(JSON.stringify(INITIAL_DICTATIONS));
        safeSetStorage(STORAGE_DICTATIONS, JSON.stringify(state.dictations));
      }

      const rawRes = safeGetStorage(STORAGE_RESULTS);
      if (rawRes) {
        try {
          state.results = JSON.parse(rawRes) || [];
        } catch (e) {
          state.results = [];
        }
      }
      ensureValidSelection();
    }

    function persistDictations() {
      safeSetStorage(STORAGE_DICTATIONS, JSON.stringify(state.dictations));
    }

    function persistResults() {
      safeSetStorage(STORAGE_RESULTS, JSON.stringify(state.results));
    }

    function getSelectedDictation() {
      return state.dictations.find(d => d.id === state.selectedDictationId) || state.dictations[0];
    }

    function ensureValidSelection() {
      if (!state.dictations.some(d => d.id === state.selectedDictationId)) {
        state.selectedDictationId = state.dictations[0].id;
      }
      const d = getSelectedDictation();
      if (d && d.enabledLevels && !d.enabledLevels[state.selectedLevel]) {
        const firstActive = [1, 2, 3, 4, 5, 6].find(l => d.enabledLevels[l]);
        state.selectedLevel = firstActive || 1;
      }
    }

    /* =========================================================================
       4. SYNTHÈSE VOCALE FRANÇAISE (WEB SPEECH API)
       ========================================================================= */
    let frenchVoice = null;
    let wordSpeechTimer = null;

    function refreshVoices() {
      if (!('speechSynthesis' in window)) return;
      const voices = window.speechSynthesis.getVoices();
      frenchVoice = voices.find(v => v.lang === 'fr-FR' && (v.name.includes('Google') || v.name.includes('Amélie') || v.name.includes('Thomas') || v.name.includes('Audrey')))
                 || voices.find(v => v.lang && v.lang.toLowerCase().startsWith('fr'));
    }

    if ('speechSynthesis' in window) {
      refreshVoices();
      window.speechSynthesis.onvoiceschanged = refreshVoices;
    }

    function stopSpeech() {
      if ('speechSynthesis' in window) {
        window.speechSynthesis.cancel();
      }
      if (wordSpeechTimer) clearTimeout(wordSpeechTimer);
      state.exercise.speakingWordIndex = -1;
      state.exercise.activeSegmentIndex = -1;
    }

    function speakText(text, rate = 0.95, segIdx = -1) {
      if (!('speechSynthesis' in window)) {
        showToast("La lecture audio n'est pas disponible sur ce navigateur.", "amber");
        return;
      }
      stopSpeech();
      state.exercise.activeSegmentIndex = segIdx;
      if (segIdx >= 0) render();

      const utt = new SpeechSynthesisUtterance(text);
      utt.lang = 'fr-FR';
      if (frenchVoice) utt.voice = frenchVoice;
      utt.rate = rate;
      utt.onend = () => {
        state.exercise.activeSegmentIndex = -1;
        if (segIdx >= 0) render();
      };
      window.speechSynthesis.speak(utt);
    }

    function speakWordByWord(wordsArray) {
      if (!('speechSynthesis' in window)) return;
      stopSpeech();
      let idx = 0;

      function nextWord() {
        if (idx >= wordsArray.length) {
          state.exercise.speakingWordIndex = -1;
          render();
          return;
        }
        state.exercise.speakingWordIndex = idx;
        render();

        const clean = wordsArray[idx].replace(/[.,!?;:«»"]/g, '');
        const utt = new SpeechSynthesisUtterance(clean || wordsArray[idx]);
        utt.lang = 'fr-FR';
        if (frenchVoice) utt.voice = frenchVoice;
        utt.rate = 0.85;
        utt.onend = () => {
          idx++;
          wordSpeechTimer = setTimeout(nextWord, 420);
        };
        utt.onerror = () => {
          idx++;
          wordSpeechTimer = setTimeout(nextWord, 300);
        };
        window.speechSynthesis.speak(utt);
      }
      nextWord();
    }

    /* =========================================================================
       5. GÉNÉRATEUR PÉDAGOGIQUE AUTOMATIQUE (6 NIVEAUX, TEXTE EXACT CONSERVÉ)
       ========================================================================= */
    function splitSentencesExact(rawText) {
      const trimmed = rawText.trim();
      const matches = trimmed.match(/[^.!?]+[.!?]+(?:\s+|$)|[^.!?]+$/g);
      return matches ? matches.map(s => s.trim()).filter(Boolean) : [trimmed];
    }

    function generateTrapsForSentence(words) {
      const traps = [];
      words.forEach((word, wIdx) => {
        const m = word.match(/^([a-zA-ZÀ-ÿ'-]+)([.,!?;:]*)$/);
        const core = m ? m[1] : word;
        const punct = m ? m[2] : "";
        const lower = core.toLowerCase();

        if (lower === 'a' || lower === 'à') {
          traps.push({
            wordIndex: wIdx,
            wrongWord: (lower === 'a' ? (core === 'A' ? 'À' : 'à') : (core === 'À' ? 'A' : 'a')) + punct,
            correctWord: word,
            category: "Homophone (a / à)",
            hintNature: "Vérifie l'homophone : peux-tu dire « avait » ?",
            explanation: lower === 'a'
              ? "On peut dire « avait » : c'est le verbe avoir « a » sans accent."
              : "On ne peut pas dire « avait » : on écrit « à » avec un accent."
          });
        } else if (lower === 'et' || lower === 'est') {
          traps.push({
            wordIndex: wIdx,
            wrongWord: (lower === 'et' ? (core === 'Et' ? 'Est' : 'est') : (core === 'Est' ? 'Et' : 'et')) + punct,
            correctWord: word,
            category: "Homophone (et / est)",
            hintNature: "Vérifie l'homophone : peux-tu dire « et puis » ou « était » ?",
            explanation: lower === 'et'
              ? "On peut dire « et puis » : on écrit « et »."
              : "C'est le verbe être (on peut dire « était ») : on écrit « est »."
          });
        } else if (lower === 'son' || lower === 'sont') {
          traps.push({
            wordIndex: wIdx,
            wrongWord: (lower === 'son' ? (core === 'Son' ? 'Sont' : 'sont') : (core === 'Sont' ? 'Son' : 'son')) + punct,
            correctWord: word,
            category: "Homophone (son / sont)",
            hintNature: "Vérifie l'homophone : peux-tu dire « étaient » ?",
            explanation: lower === 'sont'
              ? "On peut dire « étaient » : c'est le verbe être « sont »."
              : "C'est le déterminant possessif (le sien) : on écrit « son »."
          });
        } else if (lower === 'on' || lower === 'ont') {
          traps.push({
            wordIndex: wIdx,
            wrongWord: (lower === 'on' ? (core === 'On' ? 'Ont' : 'ont') : (core === 'Ont' ? 'On' : 'on')) + punct,
            correctWord: word,
            category: "Homophone (on / ont)",
            hintNature: "Vérifie l'homophone : peux-tu dire « avaient » ?",
            explanation: lower === 'ont'
              ? "On peut dire « avaient » : c'est le verbe avoir « ont »."
              : "On peut remplacer par « il » : on écrit « on »."
          });
        } else if (lower.endsWith('ent') && lower.length > 4) {
          traps.push({
            wordIndex: wIdx,
            wrongWord: core.slice(0, -2) + punct,
            correctWord: word,
            category: "Accord sujet-verbe",
            hintNature: "Observe la terminaison du verbe : le sujet est au pluriel.",
            explanation: "Avec un sujet au pluriel (ils / elles), le verbe au présent prend -ent."
          });
        } else if (lower.endsWith('eaux') && lower.length > 4) {
          traps.push({
            wordIndex: wIdx,
            wrongWord: core.slice(0, -1) + punct,
            correctWord: word,
            category: "Pluriel des noms",
            hintNature: "Vérifie le pluriel d'un nom terminé par -eau.",
            explanation: "Les noms terminés par -eau prennent un -x au pluriel."
          });
        } else if (lower.endsWith('s') && lower.length > 3 && !['dans', 'mais', 'plus', 'très', 'sous', 'vers', 'sans', 'toujours', 'jamais', 'alors', 'ils', 'les', 'des', 'ces', 'ses', 'mes'].includes(lower)) {
          traps.push({
            wordIndex: wIdx,
            wrongWord: core.slice(0, -1) + punct,
            correctWord: word,
            category: "Accord dans le groupe nominal",
            hintNature: "Observe l'accord au pluriel dans un groupe nominal.",
            explanation: "Ce mot est au pluriel et doit prendre un -s."
          });
        }
      });

      if (traps.length === 0 && words.length >= 2) {
        const lastIdx = words.length - 1;
        const w = words[lastIdx];
        const m = w.match(/^([a-zA-ZÀ-ÿ'-]+)([.,!?;:]*)$/);
        const core = m ? m[1] : w;
        const punct = m ? m[2] : "";
        traps.push({
          wordIndex: lastIdx,
          wrongWord: (core.endsWith('s') ? core.slice(0, -1) : core + 's') + punct,
          correctWord: w,
          category: "Orthographe / accord",
          hintNature: "Observe attentivement la fin des mots de la phrase.",
          explanation: `La forme correcte attendue dans la dictée est « ${w} ».`
        });
      }
      return traps;
    }

    function buildDictationExercises(title, rawText, existingId = null, enabledLevels = null) {
      const sentenceStrings = splitSentencesExact(rawText);
      const determiners = new Set(['le', 'la', 'les', 'l’', "l'", 'un', 'une', 'des', 'du', 'au', 'aux', 'mon', 'ton', 'son', 'ma', 'ta', 'sa', 'mes', 'tes', 'ses', 'dans', 'sur', 'sous', 'avec', 'pour', 'par', 'sans', 'vers', 'chez']);

      const sentences = sentenceStrings.map((sStr, sIdx) => {
        const words = sStr.split(/\s+/).filter(Boolean);
        const chunks = [];
        let i = 0;
        while (i < words.length) {
          const lower = words[i].toLowerCase().replace(/[.,!?;:]/g, '');
          if (determiners.has(lower) && i + 1 < words.length) {
            if (i + 2 < words.length && words[i + 2].length <= 8 && !determiners.has(words[i + 2].toLowerCase())) {
              chunks.push(`${words[i]} ${words[i + 1]} ${words[i + 2]}`);
              i += 3;
            } else {
              chunks.push(`${words[i]} ${words[i + 1]}`);
              i += 2;
            }
          } else {
            chunks.push(words[i]);
            i += 1;
          }
        }
        if (chunks.length < 2 && words.length >= 2) {
          const mid = Math.ceil(words.length / 2);
          chunks.length = 0;
          chunks.push(words.slice(0, mid).join(' '), words.slice(mid).join(' '));
        }

        const detected = generateTrapsForSentence(words);
        const maxErr = sIdx === 0 ? 1 : Math.min(2, detected.length);
        const level3Errors = detected.slice(0, maxErr);

        let instruction = "Ajoute « Aujourd'hui, » tout au début de la phrase (attention à la majuscule).";
        let targetSentence = "Aujourd'hui, " + sStr.charAt(0).toLowerCase() + sStr.slice(1);
        let explanation = "Après « Aujourd'hui, », le mot suivant perd sa majuscule (sauf si c'est un nom propre).";

        if (words[0] === 'Les' || words[0] === 'Des') {
          instruction = `Remplace « ${words[0]} » par « ${words[0] === 'Les' ? 'Le' : 'Un'} » et fais les accords au singulier.`;
          explanation = "En passant au singulier, le déterminant, le nom, l'adjectif et le verbe s'accordent au singulier.";
        } else if (words[0] === 'Le' || words[0] === 'Un') {
          instruction = `Remplace « ${words[0]} » par « ${words[0] === 'Le' ? 'Les' : 'Des'} » et fais les accords au pluriel.`;
          explanation = "En passant au pluriel, pense aux marques du pluriel (-s ou -x aux noms/adjectifs, -ent aux verbes).";
        }

        return {
          text: sStr,
          chunks,
          words,
          level3Errors,
          level6: { instruction, targetSentence, explanation }
        };
      });

      // Paragraphe Niveau 4 (2 à 3 erreurs ciblées)
      const paraWords = [];
      const paraErrors = [];
      sentences.slice(0, Math.min(2, sentences.length)).forEach(s => {
        const offset = paraWords.length;
        paraWords.push(...s.words);
        s.level3Errors.forEach(err => {
          if (paraErrors.length < 3) {
            paraErrors.push({ ...err, wordIndex: offset + err.wordIndex });
          }
        });
      });

      return {
        id: existingId || ('dictee-' + Date.now()),
        title: title.trim() || "Dictée CM1",
        rawText: rawText.trim(),
        enabledLevels: enabledLevels || { 1: true, 2: true, 3: true, 4: true, 5: true, 6: true },
        sentences,
        level4Paragraph: { words: paraWords, errors: paraErrors }
      };
    }

    /* =========================================================================
       6. UTILITAIRES PÉDAGOGIQUES & ANIMATIONS DOUCES
       ========================================================================= */
    const SUCCESS_MESSAGES = [
      "Bravo, tu progresses !",
      "Super travail, continue comme ça !",
      "Génial ! Tu as réussi cette étape !",
      "Excellent ! Tu peux être fier de toi !"
    ];

    const RETRY_MESSAGES = [
      "Encore un petit effort, tu es tout près !",
      "Tu peux y arriver ! Utilise un indice si besoin.",
      "Ce n'est pas grave de se tromper, c'est comme ça qu'on apprend !"
    ];

    function shuffleArray(arr) {
      const copy = [...arr];
      for (let i = copy.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [copy[i], copy[j]] = [copy[j], copy[i]];
      }
      if (copy.length > 1 && copy.every((v, idx) => v === arr[idx])) {
        [copy[0], copy[1]] = [copy[1], copy[0]];
      }
      return copy;
    }

    function checkWordMatch(userInput, targetWord) {
      const m = targetWord.match(/^(.+?)([.,!?;:]*)$/);
      const coreTarget = m ? m[1] : targetWord;
      const punct = m ? m[2] : "";
      const cleanUser = userInput.trim().replace(/[.,!?;:]+$/, '');
      if (cleanUser === coreTarget) {
        return { isMatch: true, normalized: coreTarget + punct };
      }
      return { isMatch: false, normalized: userInput.trim() };
    }

    function showToast(text, tone = 'sage') {
      const box = document.getElementById('toast-box');
      if (!box) return;
      const el = document.createElement('div');
      el.className = 'toast-item';
      el.style.backgroundColor = tone === 'amber' ? '#D98A3C' : (tone === 'slate' ? '#3B6E8C' : '#4A8B71');
      el.textContent = text;
      box.appendChild(el);
      setTimeout(() => {
        el.style.opacity = '0';
        el.style.transition = 'opacity 0.25s ease';
        setTimeout(() => el.remove(), 250);
      }, 3200);
    }

    function launchGentleConfetti() {
      const colors = ['#4A8B71', '#3B6E8C', '#D98A3C', '#E8B84B'];
      for (let i = 0; i < 26; i++) {
        const dot = document.createElement('div');
        dot.className = 'confetti-piece';
        dot.style.left = (20 + Math.random() * 60) + 'vw';
        dot.style.top = (25 + Math.random() * 20) + 'vh';
        dot.style.backgroundColor = colors[i % colors.length];
        dot.style.animationDuration = (0.9 + Math.random() * 0.7) + 's';
        document.body.appendChild(dot);
        setTimeout(() => dot.remove(), 1700);
      }
    }

    function toggleDyslexicMode() {
      state.dyslexicMode = !state.dyslexicMode;
      document.body.classList.toggle('dyslexic-mode', state.dyslexicMode);
      const btn = document.getElementById('btn-dyslexic');
      if (btn) btn.classList.toggle('active', state.dyslexicMode);
    }

    function openModal(id) {
      const el = document.getElementById(id);
      if (el) el.classList.add('open');
    }

    function closeModal(id) {
      const el = document.getElementById(id);
      if (el) el.classList.remove('open');
    }

    /* =========================================================================
       7. NAVIGATION, IDENTITÉ ÉLÈVE & ACCÈS ENSEIGNANT
       ========================================================================= */
    function updateTopbarUI() {
      const wrap = document.getElementById('student-badge-wrap');
      if (state.studentName) {
        wrap.style.display = 'inline-flex';
        document.getElementById('student-name-label').textContent = state.studentName;
        document.getElementById('student-avatar').textContent = state.studentName.charAt(0).toUpperCase();
      } else {
        wrap.style.display = 'none';
      }

      const teacherText = document.getElementById('btn-teacher-text');
      if (teacherText) {
        teacherText.textContent = state.view === 'teacher' ? 'Retour Élève' : 'Espace Enseignant';
      }
    }

    function navigateTo(view) {
      stopSpeech();
      state.view = view;
      updateTopbarUI();
      render();
    }

    function openStudentModal() {
      const input = document.getElementById('input-student-name');
      input.value = state.studentName || '';
      const names = [...new Set(state.results.map(r => r.studentName).filter(Boolean))];
      const area = document.getElementById('known-students-area');
      const chips = document.getElementById('known-students-chips');

      if (names.length > 0) {
        area.style.display = 'block';
        chips.innerHTML = names.slice(0, 10).map(n => `
          <button type="button" class="pill-btn btn-soft" onclick="pickStudentName('${n.replace(/'/g, "\\'")}')">${n}</button>
        `).join('');
      } else {
        area.style.display = 'none';
      }
      openModal('modal-student');
      setTimeout(() => input.focus(), 60);
    }

    function pickStudentName(name) {
      state.studentName = name;
      safeSetStorage(STORAGE_STUDENT, name);
      closeModal('modal-student');
      updateTopbarUI();
      showToast(`Bonjour ${name} ! Prêt pour ta dictée ?`, 'sage');
      render();
    }

    function submitStudentName(e) {
      e.preventDefault();
      const val = document.getElementById('input-student-name').value.trim();
      if (!val) return;
      pickStudentName(val);
    }

    function handleTeacherButtonClick() {
      if (state.view === 'teacher') {
        navigateTo('home');
        return;
      }
      document.getElementById('input-pin').value = '';
      document.getElementById('pin-error').style.display = 'none';
      openModal('modal-pin');
      setTimeout(() => document.getElementById('input-pin').focus(), 60);
    }

    function submitTeacherPin(e) {
      e.preventDefault();
      const pin = document.getElementById('input-pin').value.trim();
      if (pin === '1234') {
        closeModal('modal-pin');
        navigateTo('teacher');
      } else {
        document.getElementById('pin-error').style.display = 'block';
      }
    }

    /* =========================================================================
       8. LOGIQUE DES 6 NIVEAUX D'EXERCICES
       ========================================================================= */
    function selectDictation(id) {
      state.selectedDictationId = id;
      ensureValidSelection();
      render();
    }

    function selectLevel(lvl) {
      state.selectedLevel = lvl;
      render();
    }

    function startExercise() {
      if (!state.studentName) {
        openStudentModal();
        return;
      }
      state.exercise = {
        sentenceIndex: 0,
        score: 0,
        attempts: 0,
        errorsLog: [],
        verified: false,
        isCorrect: false,
        availableItems: [],
        placedItems: [],
        editingWordIdx: null,
        userCorrections: {},
        hintStep: 0,
        level4AttemptCount: 0,
        level4FoundCount: 0,
        level4ShowHints: false,
        level4Revealed: false,
        dictationText: "",
        activeSegmentIndex: -1,
        guidedReviewStep: 0,
        reviewChecks: { 1: false, 2: false, 3: false, 4: false },
        wordComparison: [],
        transformText: "",
        transformDiff: [],
        speakingWordIndex: -1
      };
      setupCurrentStep();
      navigateTo('exercise');
    }

    function getTotalSteps() {
      const dict = getSelectedDictation();
      return state.selectedLevel === 4 ? 1 : dict.sentences.length;
    }

    function setupCurrentStep() {
      stopSpeech();
      const dict = getSelectedDictation();
      const sentence = dict.sentences[state.exercise.sentenceIndex];
      const lvl = state.selectedLevel;

      state.exercise.verified = false;
      state.exercise.isCorrect = false;
      state.exercise.editingWordIdx = null;
      state.exercise.userCorrections = {};
      state.exercise.hintStep = 0;
      state.exercise.level4AttemptCount = 0;
      state.exercise.level4FoundCount = 0;
      state.exercise.level4ShowHints = false;
      state.exercise.level4Revealed = false;
      state.exercise.dictationText = "";
      state.exercise.guidedReviewStep = 0;
      state.exercise.reviewChecks = { 1: false, 2: false, 3: false, 4: false };
      state.exercise.wordComparison = [];
      state.exercise.transformText = "";
      state.exercise.transformDiff = [];

      if (lvl === 1) {
        const items = sentence.chunks.map((text, idx) => ({ id: `c-${idx}-${Math.random()}`, text }));
        state.exercise.availableItems = shuffleArray(items);
        state.exercise.placedItems = [];
      } else if (lvl === 2) {
        const items = sentence.words.map((text, idx) => ({ id: `w-${idx}-${Math.random()}`, text }));
        state.exercise.availableItems = shuffleArray(items);
        state.exercise.placedItems = [];
      }
    }

    // --- Niveaux 1 & 2 : Clic ou Glisser-Déposer ---
    function placeItemById(id) {
      if (state.exercise.isCorrect) return;
      state.exercise.verified = false;
      const idx = state.exercise.availableItems.findIndex(x => x.id === id);
      if (idx >= 0) {
        const [item] = state.exercise.availableItems.splice(idx, 1);
        state.exercise.placedItems.push(item);
        render();
      }
    }

    function removeItemById(id) {
      if (state.exercise.isCorrect) return;
      state.exercise.verified = false;
      const idx = state.exercise.placedItems.findIndex(x => x.id === id);
      if (idx >= 0) {
        const [item] = state.exercise.placedItems.splice(idx, 1);
        state.exercise.availableItems.push(item);
        render();
      }
    }

    let dragState = { id: null, from: null };
    function onDragStart(e, id, from) {
      dragState = { id, from };
      if (e.dataTransfer) e.dataTransfer.setData('text/plain', id);
    }
    function onDragOver(e) {
      e.preventDefault();
      e.currentTarget.classList.add('drag-over');
    }
    function onDragLeave(e) {
      e.currentTarget.classList.remove('drag-over');
    }
    function onDropZone(e, target) {
      e.preventDefault();
      e.currentTarget.classList.remove('drag-over');
      if (!dragState.id) return;
      if (target === 'placed' && dragState.from === 'available') placeItemById(dragState.id);
      if (target === 'available' && dragState.from === 'placed') removeItemById(dragState.id);
      dragState = { id: null, from: null };
    }

    // --- Niveaux 3 & 4 : Clic sur mot dans le texte fluide ---
    function getLevel3Words(sentence) {
      const copy = [...sentence.words];
      (sentence.level3Errors || []).forEach(err => {
        if (err.wordIndex >= 0 && err.wordIndex < copy.length) {
          copy[err.wordIndex] = err.wrongWord;
        }
      });
      return copy;
    }

    function openWordEditor(wordIdx) {
      if (state.exercise.isCorrect || state.exercise.level4Revealed) return;
      state.exercise.editingWordIdx = wordIdx;
      state.exercise.verified = false;
      render();
      setTimeout(() => {
        const inp = document.getElementById('word-edit-input');
        if (inp) { inp.focus(); inp.select(); }
      }, 30);
    }

    function saveWordEdit(e) {
      if (e) e.preventDefault();
      const idx = state.exercise.editingWordIdx;
      if (idx === null) return;
      const inp = document.getElementById('word-edit-input');
      const val = inp ? inp.value.trim() : '';
      const dict = getSelectedDictation();
      const words = state.selectedLevel === 3
        ? getLevel3Words(dict.sentences[state.exercise.sentenceIndex])
        : dict.level4Paragraph.words;

      if (!val || val === words[idx]) {
        delete state.exercise.userCorrections[idx];
      } else {
        state.exercise.userCorrections[idx] = val;
      }
      state.exercise.editingWordIdx = null;
      state.exercise.verified = false;
      render();
    }

    function cancelWordEdit(wordIdx) {
      delete state.exercise.userCorrections[wordIdx];
      state.exercise.editingWordIdx = null;
      state.exercise.verified = false;
      render();
    }

    function insertAccentChar(char, inputId) {
      const el = document.getElementById(inputId);
      if (!el) return;
      const start = el.selectionStart ?? el.value.length;
      const end = el.selectionEnd ?? el.value.length;
      const updated = el.value.substring(0, start) + char + el.value.substring(end);
      el.value = updated;
      if (inputId === 'dictation-input') state.exercise.dictationText = updated;
      if (inputId === 'transform-input') state.exercise.transformText = updated;
      el.focus();
      el.setSelectionRange(start + 1, start + 1);
    }

    // --- Indices gradués ---
    function triggerHint() {
      const dict = getSelectedDictation();
      const sentence = dict.sentences[state.exercise.sentenceIndex];
      const lvl = state.selectedLevel;

      if (lvl === 1 || lvl === 2) {
        const expected = lvl === 1 ? sentence.chunks : sentence.words;
        let pos = 0;
        while (pos < state.exercise.placedItems.length && state.exercise.placedItems[pos].text === expected[pos]) {
          pos++;
        }
        if (pos < expected.length) {
          const needed = expected[pos];
          const removed = state.exercise.placedItems.splice(pos);
          state.exercise.availableItems.push(...removed);
          const foundIdx = state.exercise.availableItems.findIndex(x => x.text === needed);
          if (foundIdx >= 0) {
            const [item] = state.exercise.availableItems.splice(foundIdx, 1);
            state.exercise.placedItems.push(item);
          }
          showToast(`Indice : J'ai placé « ${needed} » au bon endroit !`, 'sage');
          render();
        }
      } else if (lvl === 3) {
        const errors = sentence.level3Errors || [];
        const remaining = errors.find(e => !checkWordMatch(state.exercise.userCorrections[e.wordIndex] || "", e.correctWord).isMatch) || errors[0];
        if (!remaining) return;
        if (state.exercise.hintStep === 0) {
          state.exercise.hintStep = 1;
          showToast(`Indice 1 : ${remaining.hintNature}`, 'amber');
        } else {
          state.exercise.hintStep = 2;
          showToast("Indice 2 : Le mot à corriger est surligné en orange dans le texte.", 'amber');
        }
        render();
      } else if (lvl === 4) {
        state.exercise.level4ShowHints = true;
        showToast("Les catégories des erreurs restantes s'affichent sous le texte.", 'amber');
        render();
      } else if (lvl === 5) {
        showToast(`Indice : La phrase commence par « ${sentence.words[0]} » et compte ${sentence.words.length} mots.`, 'sage');
      } else if (lvl === 6) {
        const debut = sentence.level6.targetSentence.split(/\s+/).slice(0, 2).join(' ');
        showToast(`Indice : La nouvelle phrase commence par « ${debut}... »`, 'sage');
      }
    }

    // --- Vérification selon le niveau ---
    function verifyCurrentExercise() {
      const dict = getSelectedDictation();
      const sentence = dict.sentences[state.exercise.sentenceIndex];
      const lvl = state.selectedLevel;
      state.exercise.attempts++;
      state.exercise.verified = true;

      let ok = false;

      if (lvl === 1) {
        ok = sentence.chunks.join(' ') === state.exercise.placedItems.map(x => x.text).join(' ');
        if (!ok) state.exercise.errorsLog.push("Ordre des groupes de mots");
      } else if (lvl === 2) {
        ok = sentence.words.join(' ') === state.exercise.placedItems.map(x => x.text).join(' ');
        if (!ok) state.exercise.errorsLog.push("Ordre des mots / ponctuation");
      } else if (lvl === 3) {
        const errors = sentence.level3Errors || [];
        let allGood = true;
        errors.forEach(err => {
          const usr = state.exercise.userCorrections[err.wordIndex] || "";
          const check = checkWordMatch(usr, err.correctWord);
          if (check.isMatch) {
            state.exercise.userCorrections[err.wordIndex] = check.normalized;
          } else {
            allGood = false;
            state.exercise.errorsLog.push(err.category);
          }
        });
        Object.keys(state.exercise.userCorrections).forEach(k => {
          if (!errors.some(e => e.wordIndex === Number(k))) allGood = false;
        });
        ok = allGood;
        if (!ok && state.exercise.hintStep === 0) state.exercise.hintStep = 1;
      } else if (lvl === 4) {
        const para = dict.level4Paragraph;
        const errors = para.errors || [];
        state.exercise.level4AttemptCount++;
        let found = 0;
        let falseAlarms = 0;

        errors.forEach(err => {
          const usr = state.exercise.userCorrections[err.wordIndex] || "";
          const check = checkWordMatch(usr, err.correctWord);
          if (check.isMatch) {
            state.exercise.userCorrections[err.wordIndex] = check.normalized;
            found++;
          } else {
            state.exercise.errorsLog.push(err.category);
          }
        });
        Object.keys(state.exercise.userCorrections).forEach(k => {
          if (!errors.some(e => e.wordIndex === Number(k))) falseAlarms++;
        });

        state.exercise.level4FoundCount = found;
        ok = (found === errors.length && falseAlarms === 0);
        if (!ok) state.exercise.level4ShowHints = true;
      } else if (lvl === 5) {
        const refWords = sentence.words;
        const usrWords = state.exercise.dictationText.trim().split(/\s+/).filter(Boolean);
        const maxLen = Math.max(refWords.length, usrWords.length);
        const comp = [];
        let allGood = (refWords.length === usrWords.length);

        for (let i = 0; i < maxLen; i++) {
          const rW = refWords[i] || "";
          const uW = usrWords[i] || "";
          const isMatch = rW === uW;
          if (!isMatch) {
            allGood = false;
            state.exercise.errorsLog.push("Dictée autonome (orthographe/accords)");
          }
          comp.push({ refWord: rW, userWord: uW, isOk: isMatch });
        }
        state.exercise.wordComparison = comp;
        ok = allGood;
      } else if (lvl === 6) {
        const target = sentence.level6.targetSentence.trim();
        const usr = state.exercise.transformText.trim().replace(/\s+([.,!?;:])/g, '$1');
        ok = (usr === target);

        const tWords = target.split(/\s+/);
        const uWords = usr.split(/\s+/).filter(Boolean);
        state.exercise.transformDiff = tWords.map((tw, idx) => ({
          expected: tw,
          actual: uWords[idx] || "",
          isOk: tw === (uWords[idx] || "")
        }));
        if (!ok) state.exercise.errorsLog.push("Transformation grammaticale");
      }

      state.exercise.isCorrect = ok;

      if (ok) {
        state.exercise.score++;
        showToast(SUCCESS_MESSAGES[Math.floor(Math.random() * SUCCESS_MESSAGES.length)], 'sage');
        launchGentleConfetti();
      } else {
        showToast(RETRY_MESSAGES[Math.floor(Math.random() * RETRY_MESSAGES.length)], 'amber');
      }
      render();
    }

    function nextStepOrSummary() {
      const total = getTotalSteps();
      if (state.exercise.sentenceIndex + 1 < total) {
        state.exercise.sentenceIndex++;
        setupCurrentStep();
        render();
      } else {
        const dict = getSelectedDictation();
        const rate = Math.min(100, Math.round((state.exercise.score / Math.max(1, total)) * 100));
        state.results.unshift({
          id: 'res-' + Date.now(),
          studentName: state.studentName || 'Élève',
          dictationId: dict.id,
          dictationTitle: dict.title,
          level: state.selectedLevel,
          score: state.exercise.score,
          maxScore: total,
          successRate: rate,
          errorTypes: [...new Set(state.exercise.errorsLog)],
          timestamp: Date.now()
        });
        persistResults();
        launchGentleConfetti();
        navigateTo('summary');
      }
    }

    /* =========================================================================
       9. ESPACE ENSEIGNANT (GÉNÉRATEUR 6 NIVEAUX + ÉDITEUR + SUIVI)
       ========================================================================= */
    function switchTeacherTab(tab) {
      state.teacherTab = tab;
      render();
    }

    function openNewDictationEditor() {
      state.teacherDraft = {
        id: null,
        title: "",
        rawText: "",
        enabledLevels: { 1: true, 2: true, 3: true, 4: true, 5: true, 6: true },
        sentences: null,
        level4Paragraph: null
      };
      render();
    }

    function openEditDictationEditor(id) {
      const found = state.dictations.find(d => d.id === id);
      if (!found) return;
      state.teacherDraft = JSON.parse(JSON.stringify(found));
      render();
    }

    function generateDraftFromForm() {
      const titleVal = document.getElementById('editor-title').value.trim();
      const textVal = document.getElementById('editor-raw').value.trim();
      if (!textVal) {
        showToast("Veuillez d'abord saisir ou coller le texte de la dictée.", "amber");
        return;
      }
      const existingId = state.teacherDraft ? state.teacherDraft.id : null;
      const levels = state.teacherDraft ? state.teacherDraft.enabledLevels : { 1: true, 2: true, 3: true, 4: true, 5: true, 6: true };
      state.teacherDraft = buildDictationExercises(titleVal || "Nouvelle dictée", textVal, existingId, levels);
      showToast("Les 6 niveaux ont été générés ! Vous pouvez les modifier ci-dessous.", "sage");
      render();
    }

    function saveTeacherDraft() {
      if (!state.teacherDraft || !state.teacherDraft.sentences) return;
      const titleInput = document.getElementById('editor-title');
      if (titleInput && titleInput.value.trim()) state.teacherDraft.title = titleInput.value.trim();
      if (!state.teacherDraft.id) state.teacherDraft.id = 'dictee-' + Date.now();
      if (![1, 2, 3, 4, 5, 6].some(l => state.teacherDraft.enabledLevels[l])) {
        state.teacherDraft.enabledLevels[1] = true;
      }

      const idx = state.dictations.findIndex(d => d.id === state.teacherDraft.id);
      if (idx >= 0) state.dictations[idx] = state.teacherDraft;
      else state.dictations.unshift(state.teacherDraft);

      persistDictations();
      state.selectedDictationId = state.teacherDraft.id;
      state.teacherDraft = null;
      showToast("Dictée enregistrée et disponible pour les élèves !", "sage");
      render();
    }

    function askDeleteDictation(id, title) {
      document.getElementById('confirm-title').textContent = "Supprimer cette dictée ?";
      document.getElementById('confirm-msg').textContent = `Voulez-vous supprimer « ${title} » de la bibliothèque ?`;
      document.getElementById('confirm-ok-btn').onclick = () => {
        state.dictations = state.dictations.filter(d => d.id !== id);
        if (state.dictations.length === 0) state.dictations = JSON.parse(JSON.stringify(INITIAL_DICTATIONS));
        persistDictations();
        ensureValidSelection();
        closeModal('modal-confirm');
        showToast("Dictée supprimée.", "slate");
        render();
      };
      openModal('modal-confirm');
    }

    /* =========================================================================
       10. RENDU DES VUES (ACCUEIL ÉLÈVE, 6 NIVEAUX, BILAN, ENSEIGNANT)
       ========================================================================= */
    function render() {
      const root = document.getElementById('app-root');
      if (!root) return;

      if (state.view === 'home') root.innerHTML = renderHomeView();
      else if (state.view === 'exercise') root.innerHTML = renderExerciseView();
      else if (state.view === 'summary') root.innerHTML = renderSummaryView();
      else if (state.view === 'teacher') root.innerHTML = renderTeacherView();
    }

    function renderHomeView() {
      const currentDict = getSelectedDictation();
      const levelsInfo = [
        { num: 1, title: "Je reconstruis les phrases", desc: "Remets les groupes de mots dans le bon ordre.", sub: "Étape 1 • Manipulation" },
        { num: 2, title: "Je remets les mots dans l'ordre", desc: "Place chaque mot, la majuscule et le point.", sub: "Étape 2 • Syntaxe" },
        { num: 3, title: "Je trouve et corrige les erreurs", desc: "Repère le mot mal écrit dans la phrase et corrige-le.", sub: "Étape 3 • Vigilance" },
        { num: 4, title: "Je relis et corrige seul", desc: "Relis un court texte et corrige les erreurs cachées.", sub: "Étape 4 • Relecture" },
        { num: 5, title: "Je réalise la dictée", desc: "Écoute par morceaux, écris et utilise la relecture guidée.", sub: "Étape 5 • Dictée" },
        { num: 6, title: "Je transfère mes connaissances", desc: "Transforme la phrase (pluriel, sujet, temps).", sub: "Étape 6 • Défi CM1" }
      ];

      const studentHistory = state.results.filter(r =>
        r.studentName.toLowerCase() === (state.studentName || '').toLowerCase() &&
        r.dictationId === currentDict.id
      );

      return `
        <div class="card" style="display:flex; flex-wrap:wrap; align-items:center; justify-content:space-between; gap:16px;">
          <div>
            <span class="tag tag-sage" style="margin-bottom:8px;">Parcours progressif en 6 niveaux</span>
            <h1 style="font-size:1.65rem; font-weight:800;">
              ${state.studentName ? `Bonjour <span style="color:var(--sage);">${state.studentName}</span> !` : 'Bienvenue dans ton atelier de dictée !'}
            </h1>
            <p style="color:var(--text-muted); margin-top:4px;">
              Choisis ta dictée, puis avance pas à pas à ton rythme.
            </p>
          </div>
          ${!state.studentName ? `
            <button type="button" class="btn-big btn-amber" onclick="openStudentModal()">
              Écrire mon prénom
            </button>
          ` : `
            <div style="background:var(--bg-sand); padding:12px 18px; border-radius:16px; border:2px solid var(--border-soft); text-align:center;">
              <div style="font-size:0.78rem; font-weight:800; text-transform:uppercase; color:var(--text-muted);">Exercices réussis</div>
              <div style="font-size:1.35rem; font-weight:800; color:var(--sage);">
                ${state.results.filter(r => r.studentName.toLowerCase() === state.studentName.toLowerCase()).length}
              </div>
            </div>
          `}
        </div>

        <h2 class="section-heading"><span class="step-badge">1</span> Choisis ta dictée</h2>
        <div class="grid-2">
          ${state.dictations.map(d => {
            const isSel = d.id === currentDict.id;
            return `
              <button type="button" class="choice-card ${isSel ? 'selected' : ''}" onclick="selectDictation('${d.id}')">
                <div>
                  <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:8px;">
                    <span class="tag ${isSel ? 'tag-sage' : 'tag-sand'}">${d.sentences.length} phrase${d.sentences.length > 1 ? 's' : ''}</span>
                    ${isSel ? '<strong style="color:var(--sage-dark);">✓ Choisie</strong>' : ''}
                  </div>
                  <div style="font-size:1.2rem; font-weight:800;">${d.title}</div>
                </div>
                <p style="font-size:0.9rem; color:var(--text-muted); font-style:italic;">« ${d.sentences[0]?.text || ''} »</p>
              </button>
            `;
          }).join('')}
        </div>

        <h2 class="section-heading"><span class="step-badge">2</span> Choisis ton niveau d'entraînement</h2>
        <div class="grid-3">
          ${levelsInfo.map(lvl => {
            const enabled = currentDict.enabledLevels ? currentDict.enabledLevels[lvl.num] : true;
            if (!enabled) return '';
            const isSel = state.selectedLevel === lvl.num;
            const done = studentHistory.some(r => r.level === lvl.num && r.successRate >= 70);

            return `
              <button type="button" class="choice-card ${isSel ? 'selected' : ''}" onclick="selectLevel(${lvl.num})">
                <div>
                  <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:8px;">
                    <span class="tag ${isSel ? 'tag-sage' : 'tag-sand'}">Niveau ${lvl.num}</span>
                    ${done ? '<span class="tag tag-amber">★ Réussi</span>' : ''}
                  </div>
                  <div style="font-size:1.1rem; font-weight:800; margin-bottom:4px;">${lvl.title}</div>
                  <p style="font-size:0.92rem; color:var(--text-muted);">${lvl.desc}</p>
                </div>
                <div style="font-size:0.78rem; font-weight:800; color:var(--text-muted); text-transform:uppercase;">${lvl.sub}</div>
              </button>
            `;
          }).join('')}
        </div>

        <div style="margin-top:28px; text-align:center;">
          <button type="button" class="btn-big btn-sage" style="font-size:1.25rem; padding:18px 38px;" onclick="startExercise()">
            ▶ Commencer le Niveau ${state.selectedLevel}
          </button>
        </div>
      `;
    }

    function renderExerciseView() {
      const dict = getSelectedDictation();
      const sIdx = state.exercise.sentenceIndex;
      const sentence = dict.sentences[sIdx];
      const lvl = state.selectedLevel;
      const totalSteps = getTotalSteps();
      const pct = Math.round(((sIdx + (state.exercise.isCorrect ? 1 : 0)) / totalSteps) * 100);

      const titles = {
        1: "Niveau 1 : Je reconstruis les phrases",
        2: "Niveau 2 : Je remets les mots dans l'ordre",
        3: "Niveau 3 : Je trouve et corrige les erreurs",
        4: "Niveau 4 : Je relis et corrige seul",
        5: "Niveau 5 : Je réalise la dictée",
        6: "Niveau 6 : Je transfère mes connaissances"
      };

      const instructions = {
        1: "Clique sur les étiquettes (ou glisse-les) pour remettre les morceaux de la phrase dans l'ordre.",
        2: "Remets tous les mots dans le bon ordre. Pense à la majuscule et au point !",
        3: `Il y a ${sentence.level3Errors.length} erreur${sentence.level3Errors.length > 1 ? 's' : ''} dans cette phrase. Clique directement sur le mot mal écrit pour le corriger !`,
        4: `Relis attentivement ce texte : ${dict.level4Paragraph.errors.length} erreurs s'y sont glissées. Clique sur chaque mot faux pour le corriger.`,
        5: "Écoute la phrase segment par segment, écris-la puis utilise la relecture guidée en 4 étapes.",
        6: "Lis la phrase modèle puis écris la nouvelle phrase en suivant la consigne."
      };

      const audioText = lvl === 4 ? dict.level4Paragraph.words.join(' ') : sentence.text;
      const audioWords = lvl === 4 ? dict.level4Paragraph.words : sentence.words;

      return `
        <div class="card" style="margin-bottom:18px;">
          <div style="display:flex; flex-wrap:wrap; align-items:center; justify-content:space-between; gap:10px;">
            <button type="button" class="pill-btn btn-soft" onclick="navigateTo('home')">← Changer de niveau</button>
            <div style="text-align:center;">
              <div style="font-size:0.8rem; font-weight:800; color:var(--sage); text-transform:uppercase;">${dict.title}</div>
              <h2 style="font-size:1.15rem; font-weight:800;">${titles[lvl]}</h2>
            </div>
            <span class="tag tag-amber">${lvl === 4 ? 'Texte complet' : `Phrase ${sIdx + 1} / ${totalSteps}`}</span>
          </div>
          <div class="progress-track"><div class="progress-fill" style="width:${pct}%;"></div></div>
        </div>

        ${lvl !== 6 ? `
          <div class="audio-bar" style="margin-bottom:18px;">
            <div style="display:flex; flex-wrap:wrap; align-items:center; justify-content:space-between; gap:10px;">
              <div>
                <div style="font-weight:800; color:var(--primary-slate-dark);">🔊 Dictée vocale</div>
                <div style="font-size:0.86rem; color:var(--text-muted);">Tu peux réécouter autant de fois que tu veux.</div>
              </div>
              <div class="audio-buttons">
                <button type="button" class="audio-btn" onclick="speakText('${audioText.replace(/'/g, "\\'")}', 0.95)">▶ Écouter la phrase</button>
                <button type="button" class="audio-btn" onclick="speakText('${audioText.replace(/'/g, "\\'")}', 0.62)">🐢 Écouter lentement</button>
                <button type="button" class="audio-btn" onclick="speakWordByWord(${JSON.stringify(audioWords).replace(/"/g, '&quot;')})">🔤 Mot par mot</button>
              </div>
            </div>
            ${lvl === 5 ? `
              <div style="border-top:1px solid #C2DAE8; padding-top:10px; display:flex; flex-wrap:wrap; align-items:center; gap:8px;">
                <span style="font-size:0.82rem; font-weight:800; color:var(--primary-slate-dark);">Segment par segment :</span>
                ${sentence.chunks.map((ch, cIdx) => `
                  <button type="button" class="audio-btn ${state.exercise.activeSegmentIndex === cIdx ? 'playing' : ''}"
                    onclick="speakText('${ch.replace(/'/g, "\\'")}', 0.85, ${cIdx})">
                    🎧 Morceau ${cIdx + 1}
                  </button>
                `).join('')}
              </div>
            ` : ''}
          </div>
        ` : ''}

        <p style="text-align:center; font-weight:800; font-size:1.08rem; margin-bottom:16px;">${instructions[lvl]}</p>

        <div class="card">
          ${(lvl === 1 || lvl === 2) ? renderLevel1Or2Body(sentence, lvl) : ''}
          ${lvl === 3 ? renderLevel3Body(sentence) : ''}
          ${lvl === 4 ? renderLevel4Body(dict.level4Paragraph) : ''}
          ${lvl === 5 ? renderLevel5Body(sentence) : ''}
          ${lvl === 6 ? renderLevel6Body(sentence) : ''}
        </div>

        ${state.exercise.verified ? renderFeedbackBanner(dict, sentence, lvl) : ''}

        <div style="display:flex; flex-wrap:wrap; align-items:center; justify-content:space-between; gap:12px; margin-top:20px;">
          <div style="display:flex; gap:10px;">
            <button type="button" class="btn-big btn-amber" style="font-size:1rem; padding:12px 18px;"
              ${(state.exercise.isCorrect || state.exercise.level4Revealed) ? 'disabled' : ''}
              onclick="triggerHint()">
              💡 Indice
            </button>
            <button type="button" class="btn-big btn-soft" style="font-size:1rem; padding:12px 18px;" onclick="setupCurrentStep(); render();">
              ↺ Recommencer
            </button>
          </div>

          ${renderPrimaryExerciseButton(lvl, sIdx, totalSteps)}
        </div>
      `;
    }

    function renderPrimaryExerciseButton(lvl, sIdx, totalSteps) {
      if (state.exercise.isCorrect || state.exercise.level4Revealed) {
        return `
          <button type="button" class="btn-big btn-sage" onclick="nextStepOrSummary()">
            ${sIdx + 1 < totalSteps ? 'Phrase suivante →' : 'Voir mon bilan ★'}
          </button>
        `;
      }
      if (lvl === 5 && state.exercise.guidedReviewStep === 0) {
        return `
          <button type="button" class="btn-big btn-slate" onclick="startGuidedReview()">
            🔍 Passer à la relecture guidée
          </button>
        `;
      }
      return `
        <button type="button" class="btn-big btn-slate" onclick="verifyCurrentExercise()">
          ✓ Vérifier
        </button>
      `;
    }

    function renderLevel1Or2Body(sentence, lvl) {
      const expected = lvl === 1 ? sentence.chunks : sentence.words;
      return `
        <div style="margin-bottom:20px;">
          <div style="font-size:0.82rem; font-weight:800; color:var(--text-muted); text-transform:uppercase; margin-bottom:8px;">
            Ta phrase (${state.exercise.placedItems.length} / ${expected.length}) — Clique sur une étiquette pour la retirer :
          </div>
          <div class="drop-zone" ondragover="onDragOver(event)" ondragleave="onDragLeave(event)" ondrop="onDropZone(event, 'placed')">
            ${state.exercise.placedItems.length === 0
              ? '<span style="color:var(--text-muted); font-style:italic;">Clique sur les étiquettes ci-dessous dans le bon ordre...</span>'
              : state.exercise.placedItems.map((item, idx) => {
                  let cls = 'word-tile';
                  if (state.exercise.verified) cls += (item.text === expected[idx]) ? ' tile-ok' : ' tile-warn';
                  return `
                    <button type="button" draggable="true" class="${cls}"
                      ondragstart="onDragStart(event, '${item.id}', 'placed')"
                      onclick="removeItemById('${item.id}')">${item.text}</button>
                  `;
                }).join('')
            }
          </div>
        </div>

        <div>
          <div style="font-size:0.82rem; font-weight:800; color:var(--text-muted); text-transform:uppercase; margin-bottom:8px;">
            Étiquettes à placer :
          </div>
          <div class="pool-zone" ondragover="onDragOver(event)" ondragleave="onDragLeave(event)" ondrop="onDropZone(event, 'available')">
            ${state.exercise.availableItems.map(item => `
              <button type="button" draggable="true" class="word-tile"
                ondragstart="onDragStart(event, '${item.id}', 'available')"
                onclick="placeItemById('${item.id}')">${item.text}</button>
            `).join('')}
          </div>
        </div>
      `;
    }

    /* NIVEAU 3 : Texte fluide naturel SANS CASES autour des mots */
    function renderLevel3Body(sentence) {
      const words = getLevel3Words(sentence);
      const errors = sentence.level3Errors || [];
      const accents = ['é', 'è', 'ê', 'ë', 'à', 'â', 'ç', 'ù', 'û', 'ô', 'î', 'ï'];

      return `
        <div class="fluent-text-box">
          ${words.map((w, idx) => {
            const fixed = state.exercise.userCorrections[idx];
            const isEd = state.exercise.editingWordIdx === idx;
            const errObj = errors.find(e => e.wordIndex === idx);
            const hint2 = (state.exercise.hintStep >= 2 && errObj && !fixed);

            let cls = 'clickable-word';
            if (isEd) cls += ' is-editing';
            else if (fixed) {
              if (state.exercise.verified && errObj) {
                cls += checkWordMatch(fixed, errObj.correctWord).isMatch ? ' is-validated-ok' : ' is-validated-err';
              } else {
                cls += ' has-correction';
              }
            } else if (hint2) {
              cls += ' hint-pulse';
            }

            const inner = fixed
              ? `<span class="old-word-strike">${w}</span><span>${fixed}</span>`
              : w;

            return `<span role="button" tabindex="0" class="${cls}" onclick="openWordEditor(${idx})" onkeydown="if(event.key==='Enter'||event.key===' '){event.preventDefault();openWordEditor(${idx});}">${inner}</span>${idx < words.length - 1 ? ' ' : ''}`;
          }).join('')}
        </div>

        ${state.exercise.hintStep >= 1 && !state.exercise.isCorrect ? `
          <div style="margin-top:14px; padding:14px; border-radius:14px; background:var(--amber-light); border:2px solid var(--amber-border); color:#6E3B0C; font-size:0.95rem;">
            <strong>💡 Indice :</strong> ${(errors.find(e => !checkWordMatch(state.exercise.userCorrections[e.wordIndex] || "", e.correctWord).isMatch) || errors[0]).hintNature}
          </div>
        ` : ''}

        ${state.exercise.editingWordIdx !== null ? renderWordCorrectionPanel(words[state.exercise.editingWordIdx], state.exercise.editingWordIdx, accents) : `
          <p style="text-align:center; font-size:0.86rem; color:var(--text-muted); margin-top:12px;">
            Clique directement sur un mot du texte pour écrire sa correction.
          </p>
        `}
      `;
    }

    /* NIVEAU 4 : Texte continu SANS CASES autour des mots */
    function renderLevel4Body(para) {
      const words = para.words || [];
      const errors = para.errors || [];
      const accents = ['é', 'è', 'ê', 'ë', 'à', 'â', 'ç', 'ù', 'û', 'ô', 'î', 'ï'];

      return `
        <div class="fluent-text-box">
          ${words.map((w, idx) => {
            const fixed = state.exercise.userCorrections[idx];
            const isEd = state.exercise.editingWordIdx === idx;
            const errObj = errors.find(e => e.wordIndex === idx);
            const speaking = state.exercise.speakingWordIndex === idx;

            let cls = 'clickable-word';
            if (speaking) cls += ' speaking-now';
            if (isEd) cls += ' is-editing';
            else if (state.exercise.level4Revealed && errObj) cls += ' is-validated-ok';
            else if (fixed) cls += state.exercise.isCorrect ? ' is-validated-ok' : ' has-correction';

            let inner = w;
            if (state.exercise.level4Revealed && errObj) {
              inner = `<span class="old-word-strike">${w}</span><span>${errObj.correctWord}</span>`;
            } else if (fixed) {
              inner = `<span class="old-word-strike">${w}</span><span>${fixed}</span>`;
            }

            return `<span role="button" tabindex="0" class="${cls}" onclick="openWordEditor(${idx})" onkeydown="if(event.key==='Enter'||event.key===' '){event.preventDefault();openWordEditor(${idx});}">${inner}</span>${idx < words.length - 1 ? ' ' : ''}`;
          }).join('')}
        </div>

        ${state.exercise.level4AttemptCount > 0 && !state.exercise.isCorrect && !state.exercise.level4Revealed ? `
          <div style="margin-top:16px; padding:16px; border-radius:16px; background:var(--amber-light); border:2px solid var(--amber); color:#6E3B0C;">
            <div style="font-weight:800; margin-bottom:6px;">
              Bilan de ta relecture : tu as trouvé <strong>${state.exercise.level4FoundCount} erreur${state.exercise.level4FoundCount > 1 ? 's' : ''} sur ${errors.length}</strong>.
              ${errors.length - state.exercise.level4FoundCount > 0 ? `Il en reste <strong>${errors.length - state.exercise.level4FoundCount}</strong> à corriger.` : `Attention, tu as modifié un mot qui était juste !`}
            </div>
            ${state.exercise.level4ShowHints ? `
              <div style="font-size:0.9rem; margin-top:8px;">
                <strong>Indices ciblés :</strong>
                ${errors.filter(e => !checkWordMatch(state.exercise.userCorrections[e.wordIndex] || "", e.correctWord).isMatch)
                  .map(e => `<span class="tag tag-amber" style="margin:4px 4px 0 0; background:#fff;">${e.category}</span>`).join('')}
              </div>
            ` : ''}
            ${state.exercise.level4AttemptCount >= 2 ? `
              <div style="margin-top:10px;">
                <button type="button" onclick="state.exercise.level4Revealed=true; render();" style="text-decoration:underline; font-weight:800; font-size:0.9rem;">
                  Afficher la correction expliquée
                </button>
              </div>
            ` : ''}
          </div>
        ` : ''}

        ${state.exercise.editingWordIdx !== null ? renderWordCorrectionPanel(words[state.exercise.editingWordIdx], state.exercise.editingWordIdx, accents) : ''}
      `;
    }

    function renderWordCorrectionPanel(originalWord, idx, accents) {
      const currentVal = state.exercise.userCorrections[idx] || originalWord;
      return `
        <form onsubmit="saveWordEdit(event)" style="margin-top:16px; padding:16px; border-radius:16px; background:var(--bg-sand); border:2px solid var(--primary-slate);">
          <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:8px;">
            <span style="font-weight:800;">Corriger le mot « <span style="color:var(--coral);">${originalWord}</span> » :</span>
            <button type="button" onclick="cancelWordEdit(${idx})" style="font-size:0.85rem; text-decoration:underline; color:var(--text-muted);">Annuler</button>
          </div>
          <div style="display:flex; flex-wrap:wrap; gap:10px;">
            <input type="text" id="word-edit-input" value="${currentVal.replace(/"/g, '&quot;')}"
              autocomplete="off" spellcheck="false" class="text-input-large" style="flex:1; min-width:180px;" />
            <button type="submit" class="btn-big btn-sage" style="font-size:1rem;">Valider ce mot</button>
          </div>
          <div class="accent-bar">
            <span style="font-size:0.8rem; font-weight:700; color:var(--text-muted);">Accents :</span>
            ${accents.map(ch => `
              <button type="button" class="accent-key" onmousedown="event.preventDefault(); insertAccentChar('${ch}', 'word-edit-input')">${ch}</button>
            `).join('')}
          </div>
        </form>
      `;
    }

    /* NIVEAU 5 : Dictée audio + Relecture guidée en 4 étapes */
    function startGuidedReview() {
      if (!state.exercise.dictationText.trim()) {
        showToast("Écris d'abord ta phrase avant de commencer la relecture guidée.", "amber");
        return;
      }
      state.exercise.guidedReviewStep = 1;
      state.exercise.reviewChecks[1] = true;
      render();
    }

    function renderLevel5Body(sentence) {
      const accents = ['é', 'è', 'ê', 'ë', 'à', 'â', 'ç', 'ù', 'û', 'ô', 'î', 'ï', 'É', 'À', 'Ç'];
      const steps = [
        { num: 1, title: "1. Majuscules et ponctuation", tip: "Vérifie la majuscule au début de la phrase (et aux noms propres) ainsi que le point à la fin." },
        { num: 2, title: "2. Mots appris et accents", tip: "Relis chaque mot lentement pour vérifier les lettres muettes et les accents." },
        { num: 3, title: "3. Accords dans les groupes nominaux", tip: "Après les, des, ces, ses... vérifie les -s ou -x aux noms et aux adjectifs." },
        { num: 4, title: "4. Verbes et leur sujet", tip: "Cherche le sujet de chaque verbe. Si le sujet est au pluriel (ils/elles), le verbe prend -ent." }
      ];

      return `
        <div>
          <label style="display:block; font-size:0.85rem; font-weight:800; color:var(--text-muted); text-transform:uppercase; margin-bottom:8px;">
            Écris la phrase dictée :
          </label>
          <textarea id="dictation-input" rows="3" class="text-input-large"
            oninput="state.exercise.dictationText=this.value; state.exercise.verified=false;"
            placeholder="Écoute les morceaux et écris la phrase ici...">${state.exercise.dictationText}</textarea>

          <div class="accent-bar">
            <span style="font-size:0.8rem; font-weight:700; color:var(--text-muted);">Accents :</span>
            ${accents.map(ch => `
              <button type="button" class="accent-key" onmousedown="event.preventDefault(); insertAccentChar('${ch}', 'dictation-input')">${ch}</button>
            `).join('')}
          </div>
        </div>

        ${state.exercise.guidedReviewStep > 0 && !state.exercise.isCorrect ? `
          <div style="margin-top:18px; padding:16px; border-radius:18px; background:var(--amber-light); border:2px solid var(--amber);">
            <div style="font-weight:800; color:#6E3B0C;">🔍 Relecture guidée en 4 étapes (clique sur chaque étape et corrige ton texte si besoin) :</div>
            <div class="review-grid">
              ${steps.map(st => {
                const isAct = state.exercise.guidedReviewStep === st.num;
                const isChk = state.exercise.reviewChecks[st.num];
                return `
                  <button type="button" class="review-step-card ${isAct ? 'active' : ''} ${isChk ? 'checked' : ''}"
                    onclick="state.exercise.guidedReviewStep=${st.num}; state.exercise.reviewChecks[${st.num}]=true; render();">
                    <div style="font-weight:800; font-size:0.95rem; margin-bottom:4px;">${isChk ? '✓ ' : ''}${st.title}</div>
                    <div style="font-size:0.84rem; color:var(--text-muted);">${st.tip}</div>
                  </button>
                `;
              }).join('')}
            </div>
          </div>
        ` : ''}

        ${state.exercise.verified && state.exercise.wordComparison.length > 0 ? `
          <div style="margin-top:16px; padding:14px; border-radius:14px; background:var(--bg-cream); border:2px solid var(--border-soft);">
            <div style="font-size:0.82rem; font-weight:800; color:var(--text-muted); text-transform:uppercase; margin-bottom:8px;">
              Comparaison mot à mot avec la dictée de référence :
            </div>
            <div style="display:flex; flex-wrap:wrap; gap:8px;">
              ${state.exercise.wordComparison.map(c => `
                <span class="tag ${c.isOk ? 'tag-sage' : 'tag-amber'}" style="font-size:0.95rem; text-transform:none; padding:6px 11px;">
                  ${c.isOk ? c.refWord : `<span style="text-decoration:line-through; margin-right:5px;">${c.userWord || '(oubli)'}</span> → ${c.refWord}`}
                </span>
              `).join('')}
            </div>
          </div>
        ` : ''}
      `;
    }

    /* NIVEAU 6 : Transformation grammaticale */
    function renderLevel6Body(sentence) {
      const accents = ['é', 'è', 'ê', 'ë', 'à', 'â', 'ç', 'ù', 'û', 'ô', 'î', 'ï', 'É', 'À', 'Ç'];
      return `
        <div style="padding:14px 18px; border-radius:14px; background:var(--primary-slate-light); border:2px solid #C2DAE8; margin-bottom:14px;">
          <div style="font-size:0.8rem; font-weight:800; color:var(--primary-slate-dark); text-transform:uppercase;">Phrase de départ :</div>
          <div style="font-size:1.25rem; font-weight:800; margin-top:4px;">« ${sentence.text} »</div>
        </div>

        <div style="padding:14px 18px; border-radius:14px; background:var(--amber-light); border:2px solid var(--amber); margin-bottom:16px;">
          <div style="font-size:0.8rem; font-weight:800; color:#7C4410; text-transform:uppercase;">Consigne de transformation :</div>
          <div style="font-size:1.1rem; font-weight:800; margin-top:4px;">${sentence.level6.instruction}</div>
        </div>

        <label style="display:block; font-size:0.85rem; font-weight:800; color:var(--text-muted); text-transform:uppercase; margin-bottom:8px;">
          Écris la phrase transformée :
        </label>
        <textarea id="transform-input" rows="2" class="text-input-large"
          oninput="state.exercise.transformText=this.value; state.exercise.verified=false;"
          placeholder="Écris ici la nouvelle phrase...">${state.exercise.transformText}</textarea>

        <div class="accent-bar">
          <span style="font-size:0.8rem; font-weight:700; color:var(--text-muted);">Accents :</span>
          ${accents.map(ch => `
            <button type="button" class="accent-key" onmousedown="event.preventDefault(); insertAccentChar('${ch}', 'transform-input')">${ch}</button>
          `).join('')}
        </div>
      `;
    }

    function renderFeedbackBanner(dict, sentence, lvl) {
      if (state.exercise.isCorrect || state.exercise.level4Revealed) {
        let details = "";
        if (lvl === 3) {
          details = `<ul style="margin-top:8px; padding-left:20px;">${(sentence.level3Errors || []).map(e => `<li><strong>${e.wrongWord} → ${e.correctWord}</strong> : ${e.explanation}</li>`).join('')}</ul>`;
        } else if (lvl === 4) {
          details = `<ul style="margin-top:8px; padding-left:20px;">${(dict.level4Paragraph.errors || []).map(e => `<li><strong>${e.wrongWord} → ${e.correctWord}</strong> : ${e.explanation}</li>`).join('')}</ul>`;
        } else if (lvl === 6) {
          details = `<p style="margin-top:8px;"><strong>Explication :</strong> ${sentence.level6.explanation}</p>`;
        }
        const ref = lvl === 4 ? dict.level4Paragraph.words.join(' ') : (lvl === 6 ? sentence.level6.targetSentence : sentence.text);
        return `
          <div class="feedback-banner feedback-success">
            <div style="font-size:1.8rem;">★</div>
            <div>
              <div style="font-weight:800; font-size:1.1rem;">${state.exercise.isCorrect ? 'Bravo ! Réponse exacte :' : 'Correction expliquée :'}</div>
              <div style="font-weight:700; margin-top:4px;">« ${ref} »</div>
              ${details}
            </div>
          </div>
        `;
      }

      return `
        <div class="feedback-banner feedback-retry">
          <div style="font-size:1.6rem;">💡</div>
          <div>
            <div style="font-weight:800; font-size:1.05rem;">Encore un petit effort !</div>
            <div style="margin-top:4px;">Observe les indications ci-dessus, utilise le bouton « Indice » si besoin et réessaie.</div>
          </div>
        </div>
      `;
    }

    function renderSummaryView() {
      const dict = getSelectedDictation();
      const latest = state.results[0] || { score: state.exercise.score, maxScore: getTotalSteps(), successRate: 100 };
      const nextLvl = [1, 2, 3, 4, 5, 6].find(l => l > state.selectedLevel && (dict.enabledLevels ? dict.enabledLevels[l] : true));

      return `
        <div class="card" style="max-width:560px; margin:0 auto; text-align:center; padding:34px 24px;">
          <div style="font-size:3.2rem; margin-bottom:10px;">🏆</div>
          <span class="tag tag-sage">Niveau ${state.selectedLevel} terminé</span>
          <h2 style="font-size:1.8rem; font-weight:800; margin:12px 0 6px;">Bravo ${state.studentName || ''} !</h2>
          <p style="color:var(--text-muted); margin-bottom:22px;">
            Tu as terminé le <strong>Niveau ${state.selectedLevel}</strong> de « ${dict.title} ».
          </p>

          <div style="display:grid; grid-template-columns:1fr 1fr; gap:14px; background:var(--bg-cream); padding:18px; border-radius:18px; border:2px solid var(--border-soft); margin-bottom:24px;">
            <div>
              <div style="font-size:0.78rem; font-weight:800; color:var(--text-muted); text-transform:uppercase;">Étapes réussies</div>
              <div style="font-size:1.6rem; font-weight:800; color:var(--sage);">${latest.score} / ${latest.maxScore}</div>
            </div>
            <div>
              <div style="font-size:0.78rem; font-weight:800; color:var(--text-muted); text-transform:uppercase;">Réussite</div>
              <div style="font-size:1.6rem; font-weight:800; color:var(--primary-slate);">${latest.successRate}%</div>
            </div>
          </div>

          <div style="display:flex; flex-wrap:wrap; gap:12px; justify-content:center;">
            <button type="button" class="btn-big btn-soft" onclick="navigateTo('home')">Retour à l'accueil</button>
            ${nextLvl ? `
              <button type="button" class="btn-big btn-sage" onclick="selectLevel(${nextLvl}); startExercise();">
                Passer au Niveau ${nextLvl} →
              </button>
            ` : ''}
          </div>
        </div>
      `;
    }

    /* =========================================================================
       11. VUE ENSEIGNANT (GESTION DES 6 NIVEAUX + SUIVI ÉLÈVES)
       ========================================================================= */
    function renderTeacherView() {
      return `
        <div class="card" style="display:flex; flex-wrap:wrap; align-items:center; justify-content:space-between; gap:14px; margin-bottom:20px;">
          <div>
            <h2 style="font-size:1.4rem; font-weight:800;">Espace Enseignant — CM1</h2>
            <p style="color:var(--text-muted); font-size:0.92rem;">Créez vos dictées sur 6 niveaux et consultez les progrès de vos élèves.</p>
          </div>
          <div style="display:flex; gap:8px; background:var(--bg-sand); padding:6px; border-radius:14px;">
            <button type="button" class="pill-btn" style="${state.teacherTab === 'dictations' ? 'background:#fff; box-shadow:var(--shadow-sm);' : ''}"
              onclick="switchTeacherTab('dictations')">Mes dictées & Générateur</button>
            <button type="button" class="pill-btn" style="${state.teacherTab === 'tracking' ? 'background:#fff; box-shadow:var(--shadow-sm);' : ''}"
              onclick="switchTeacherTab('tracking')">Suivi des élèves (${[...new Set(state.results.map(r => r.studentName))].length})</button>
          </div>
        </div>

        ${state.teacherTab === 'dictations' ? renderTeacherDictations() : renderTeacherTracking()}
      `;
    }

    function renderTeacherDictations() {
      if (state.teacherDraft) {
        const d = state.teacherDraft;
        return `
          <div class="card">
            <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:16px;">
              <h3 style="font-size:1.25rem; font-weight:800;">${d.id ? 'Modifier la dictée' : 'Nouvelle dictée (6 niveaux)'}</h3>
              <button type="button" class="pill-btn btn-soft" onclick="state.teacherDraft=null; render();">Annuler</button>
            </div>

            <div style="margin-bottom:14px;">
              <label style="display:block; font-size:0.82rem; font-weight:800; text-transform:uppercase; color:var(--text-muted); margin-bottom:6px;">Titre de la dictée</label>
              <input type="text" id="editor-title" value="${(d.title || '').replace(/"/g, '&quot;')}" placeholder="Ex : Le château fort" class="text-input-large" />
            </div>

            <div style="margin-bottom:14px;">
              <label style="display:block; font-size:0.82rem; font-weight:800; text-transform:uppercase; color:var(--text-muted); margin-bottom:6px;">
                Texte exact de la dictée (conservé mot pour mot sans aucune modification)
              </label>
              <textarea id="editor-raw" rows="4" class="text-input-large" placeholder="Collez ou saisissez ici votre dictée...">${d.rawText || ''}</textarea>
            </div>

            <div style="display:flex; flex-wrap:wrap; align-items:center; justify-content:space-between; gap:12px; margin-bottom:18px;">
              <button type="button" class="btn-big btn-slate" style="font-size:1rem;" onclick="generateDraftFromForm()">
                ✨ Générer automatiquement les 6 niveaux
              </button>

              <div style="display:flex; flex-wrap:wrap; align-items:center; gap:8px;">
                <span style="font-size:0.85rem; font-weight:800; color:var(--text-muted);">Niveaux ouverts :</span>
                ${[1, 2, 3, 4, 5, 6].map(l => `
                  <label style="display:inline-flex; align-items:center; gap:5px; padding:6px 10px; border-radius:10px; background:var(--bg-sand); font-weight:800; font-size:0.85rem; cursor:pointer;">
                    <input type="checkbox" ${d.enabledLevels[l] ? 'checked' : ''} onchange="state.teacherDraft.enabledLevels[${l}]=this.checked; render();" />
                    Niv. ${l}
                  </label>
                `).join('')}
              </div>
            </div>

            ${d.sentences ? `
              <div style="border-top:2px solid var(--border-soft); padding-top:18px; display:flex; flex-direction:column; gap:16px;">
                <h4 style="font-size:1.1rem; font-weight:800;">Ajuster les exercices générés :</h4>
                ${d.sentences.map((s, sIdx) => `
                  <div style="background:var(--bg-cream); border:2px solid var(--border-soft); border-radius:16px; padding:16px; display:flex; flex-direction:column; gap:10px;">
                    <div style="font-weight:800; color:var(--primary-slate-dark);">Phrase ${sIdx + 1} : « ${s.text} »</div>
                    <div>
                      <label style="font-size:0.78rem; font-weight:800; color:var(--text-muted);">Niveau 1 — Groupes de mots (séparés par « | ») :</label>
                      <input type="text" value="${s.chunks.join(' | ').replace(/"/g, '&quot;')}"
                        onchange="state.teacherDraft.sentences[${sIdx}].chunks=this.value.split('|').map(x=>x.trim()).filter(Boolean);"
                        style="width:100%; padding:8px 12px; border-radius:10px; border:1px solid var(--border-soft); margin-top:4px;" />
                    </div>
                    ${(s.level3Errors || []).map((err, eIdx) => `
                      <div style="display:grid; grid-template-columns:1fr 2fr; gap:10px; background:var(--amber-light); padding:10px; border-radius:12px;">
                        <div>
                          <label style="font-size:0.75rem; font-weight:800;">Niv. 3/4 Mot fautif affiché :</label>
                          <input type="text" value="${err.wrongWord.replace(/"/g, '&quot;')}"
                            onchange="state.teacherDraft.sentences[${sIdx}].level3Errors[${eIdx}].wrongWord=this.value;"
                            style="width:100%; padding:6px 10px; border-radius:8px; border:1px solid var(--amber-border); font-weight:800; color:var(--coral);" />
                        </div>
                        <div>
                          <label style="font-size:0.75rem; font-weight:800;">Explication (mot juste : ${err.correctWord}) :</label>
                          <input type="text" value="${err.explanation.replace(/"/g, '&quot;')}"
                            onchange="state.teacherDraft.sentences[${sIdx}].level3Errors[${eIdx}].explanation=this.value;"
                            style="width:100%; padding:6px 10px; border-radius:8px; border:1px solid var(--amber-border);" />
                        </div>
                      </div>
                    `).join('')}
                    <div>
                      <label style="font-size:0.78rem; font-weight:800; color:var(--text-muted);">Niveau 6 — Consigne & Phrase transformée attendue :</label>
                      <input type="text" value="${(s.level6?.instruction || '').replace(/"/g, '&quot;')}"
                        onchange="state.teacherDraft.sentences[${sIdx}].level6.instruction=this.value;"
                        style="width:100%; padding:7px 10px; border-radius:10px; border:1px solid var(--border-soft); margin-top:4px;" />
                      <input type="text" value="${(s.level6?.targetSentence || '').replace(/"/g, '&quot;')}"
                        onchange="state.teacherDraft.sentences[${sIdx}].level6.targetSentence=this.value;"
                        style="width:100%; padding:7px 10px; border-radius:10px; border:1px solid var(--sage-border); background:var(--sage-light); font-weight:700; margin-top:6px;" />
                    </div>
                  </div>
                `).join('')}

                <div style="text-align:right; margin-top:8px;">
                  <button type="button" class="btn-big btn-sage" onclick="saveTeacherDraft()">✓ Enregistrer la dictée</button>
                </div>
              </div>
            ` : ''}
          </div>
        `;
      }

      return `
        <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:16px;">
          <h3 style="font-size:1.15rem; font-weight:800;">Bibliothèque de dictées (${state.dictations.length})</h3>
          <button type="button" class="btn-big btn-sage" style="font-size:1rem; padding:12px 20px;" onclick="openNewDictationEditor()">
            + Nouvelle dictée
          </button>
        </div>

        <div class="grid-2">
          ${state.dictations.map(d => `
            <div class="card" style="display:flex; flex-direction:column; justify-content:space-between; gap:14px;">
              <div>
                <div style="display:flex; justify-content:space-between; align-items:flex-start; gap:8px;">
                  <h4 style="font-size:1.15rem; font-weight:800;">${d.title}</h4>
                  <span class="tag tag-sand">${d.sentences.length} phrase${d.sentences.length > 1 ? 's' : ''}</span>
                </div>
                <p style="background:var(--bg-cream); padding:12px; border-radius:12px; border:1px solid var(--border-soft); font-size:0.92rem; margin:10px 0;">
                  « ${d.rawText} »
                </p>
                <div style="display:flex; flex-wrap:wrap; gap:6px;">
                  ${[1, 2, 3, 4, 5, 6].map(l => {
                    const ok = d.enabledLevels ? d.enabledLevels[l] : true;
                    return `<span class="tag ${ok ? 'tag-sage' : 'tag-sand'}" style="${!ok ? 'text-decoration:line-through;' : ''}">Niv. ${l}</span>`;
                  }).join('')}
                </div>
              </div>
              <div style="display:flex; justify-content:flex-end; gap:8px; border-top:1px solid var(--border-soft); padding-top:10px;">
                <button type="button" class="pill-btn btn-soft" onclick="openEditDictationEditor('${d.id}')">Modifier</button>
                ${state.dictations.length > 1 ? `
                  <button type="button" class="pill-btn" style="background:var(--coral-light); color:var(--coral);" onclick="askDeleteDictation('${d.id}', '${d.title.replace(/'/g, "\\'")}')">Supprimer</button>
                ` : ''}
              </div>
            </div>
          `).join('')}
        </div>
      `;
    }

    function renderTeacherTracking() {
      if (state.results.length === 0) {
        return `
          <div class="card" style="text-align:center; padding:42px 20px;">
            <h3 style="font-size:1.2rem; font-weight:800; margin-bottom:6px;">Aucun résultat enregistré pour le moment</h3>
            <p style="color:var(--text-muted);">Les résultats apparaîtront ici dès qu'un élève terminera un niveau avec son prénom.</p>
          </div>
        `;
      }

      const grouped = {};
      state.results.forEach(r => {
        const key = r.studentName.trim();
        if (!grouped[key]) grouped[key] = { name: key, count: 0, levels: new Set(), sumRate: 0, errors: {} };
        grouped[key].count++;
        grouped[key].levels.add(r.level);
        grouped[key].sumRate += (r.successRate || 0);
        (r.errorTypes || []).forEach(err => {
          grouped[key].errors[err] = (grouped[key].errors[err] || 0) + 1;
        });
      });

      return `
        <div class="table-wrap">
          <table>
            <thead>
              <tr>
                <th>Élève (Pseudo)</th>
                <th>Parcours réalisés</th>
                <th>Niveaux travaillés</th>
                <th>Réussite moyenne</th>
                <th>Difficultés identifiées</th>
              </tr>
            </thead>
            <tbody>
              ${Object.values(grouped).map(st => {
                const avg = Math.round(st.sumRate / st.count);
                const errs = Object.entries(st.errors).sort((a, b) => b[1] - a[1]);
                return `
                  <tr>
                    <td style="font-weight:800;">${st.name}</td>
                    <td>${st.count} exercice${st.count > 1 ? 's' : ''}</td>
                    <td>
                      ${[...st.levels].sort().map(l => `<span class="tag tag-sage" style="margin-right:4px;">Niv. ${l}</span>`).join('')}
                    </td>
                    <td><span class="tag ${avg >= 75 ? 'tag-sage' : 'tag-amber'}">${avg}%</span></td>
                    <td>
                      ${errs.length > 0
                        ? errs.slice(0, 2).map(([name]) => `<span class="tag tag-amber" style="margin:2px 4px 2px 0;">${name}</span>`).join('')
                        : '<span style="color:var(--sage-dark); font-weight:700;">Aucune difficulté majeure</span>'}
                    </td>
                  </tr>
                `;
              }).join('')}
            </tbody>
          </table>
        </div>
      `;
    }

    /* =========================================================================
       12. INITIALISATION IMMÉDIATE AU CHARGEMENT
       ========================================================================= */
    loadAppState();
    updateTopbarUI();
    render();
  </script>
</body>
</html>
