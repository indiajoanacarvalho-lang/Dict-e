<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Ma dictée pas à pas — CM1</title>
  <style>
    :root {
      --bg: #f6f8f5;
      --surface: #ffffff;
      --surface-soft: #eef3ee;
      --ink: #1e2d26;
      --muted: #55685f;
      --primary: #2d6a4f;
      --primary-hover: #22543d;
      --primary-soft: #d8f3dc;
      --accent: #3b6e8c;
      --accent-soft: #e0f0f8;
      --warn: #b45309;
      --warn-soft: #fef3c7;
      --ok: #1b6b3a;
      --ok-soft: #dcfce7;
      --err: #b91c1c;
      --err-soft: #fee2e2;
      --border: #d5e0d8;
      --radius: 16px;
      --shadow: 0 6px 20px rgba(24, 42, 33, 0.06);
      --font-size-base: 19px;
      --line-height-base: 1.7;
      --letter-spacing-base: 0px;
      --word-spacing-base: 0px;
    }

    body.dys-mode {
      --font-size-base: 21px;
      --line-height-base: 2.15;
      --letter-spacing-base: 0.04em;
      --word-spacing-base: 0.14em;
    }

    * { box-sizing: border-box; }

    body {
      margin: 0;
      font-family: "Trebuchet MS", "Segoe UI", Arial, sans-serif;
      font-size: var(--font-size-base);
      line-height: var(--line-height-base);
      letter-spacing: var(--letter-spacing-base);
      word-spacing: var(--word-spacing-base);
      background: var(--bg);
      color: var(--ink);
      min-height: 100vh;
    }

    header.topbar {
      background: var(--surface);
      border-bottom: 1px solid var(--border);
      padding: 14px 20px;
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
      position: sticky;
      top: 0;
      z-index: 20;
    }

    .brand {
      display: flex;
      align-items: center;
      gap: 12px;
      cursor: pointer;
    }

    .brand-badge {
      width: 44px;
      height: 44px;
      border-radius: 12px;
      background: var(--primary-soft);
      color: var(--primary);
      display: grid;
      place-items: center;
      font-weight: 700;
      font-size: 20px;
    }

    .brand h1 {
      margin: 0;
      font-size: 21px;
      line-height: 1.2;
    }

    .brand small {
      display: block;
      font-size: 13px;
      color: var(--muted);
    }

    .topbar-actions {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      align-items: center;
    }

    button, select, input[type="text"], input[type="password"], textarea {
      font-family: inherit;
      font-size: 17px;
    }

    button {
      border: 1px solid var(--border);
      background: var(--surface);
      color: var(--ink);
      padding: 11px 16px;
      border-radius: 12px;
      cursor: pointer;
      font-weight: 600;
      min-height: 46px;
      transition: transform 0.1s ease, background 0.15s ease, border-color 0.15s ease;
    }

    button:hover:not(:disabled) {
      background: var(--surface-soft);
    }

    button:active:not(:disabled) {
      transform: scale(0.98);
    }

    button:disabled {
      opacity: 0.45;
      cursor: not-allowed;
    }

    button.btn-primary {
      background: var(--primary);
      color: #fff;
      border-color: var(--primary);
    }

    button.btn-primary:hover:not(:disabled) {
      background: var(--primary-hover);
    }

    button.btn-soft {
      background: var(--accent-soft);
      color: var(--accent);
      border-color: #b7d7e8;
    }

    button.btn-warn {
      background: var(--warn-soft);
      color: var(--warn);
      border-color: #f5d08a;
    }

    button.btn-active {
      background: var(--primary-soft);
      border-color: var(--primary);
      color: var(--primary);
    }

    main.container {
      max-width: 920px;
      margin: 24px auto 56px;
      padding: 0 18px;
    }

    .card {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      padding: 24px;
      box-shadow: var(--shadow);
      margin-bottom: 20px;
    }

    .grid-2 {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 16px;
    }

    .field {
      margin-bottom: 16px;
    }

    .field label {
      display: block;
      font-weight: 700;
      margin-bottom: 6px;
    }

    input[type="text"], input[type="password"], select, textarea {
      width: 100%;
      padding: 12px 14px;
      border: 1.5px solid var(--border);
      border-radius: 12px;
      background: #fff;
      color: var(--ink);
    }

    textarea {
      min-height: 110px;
      resize: vertical;
    }

    input:focus, select:focus, textarea:focus {
      outline: 3px solid var(--primary-soft);
      border-color: var(--primary);
    }

    .level-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
      gap: 12px;
      margin-top: 8px;
    }

    .level-option {
      border: 2px solid var(--border);
      border-radius: 14px;
      padding: 14px;
      background: #fff;
      text-align: left;
      display: flex;
      flex-direction: column;
      gap: 4px;
      min-height: unset;
    }

    .level-option.selected {
      border-color: var(--primary);
      background: var(--primary-soft);
    }

    .level-option.locked {
      opacity: 0.5;
      background: #f3f5f4;
    }

    .level-num {
      font-size: 13px;
      font-weight: 700;
      text-transform: uppercase;
      color: var(--primary);
    }

    .level-title {
      font-weight: 700;
      font-size: 17px;
    }

    .level-desc {
      font-size: 14px;
      color: var(--muted);
      line-height: 1.4;
    }

    .progress-wrap {
      margin-bottom: 16px;
    }

    .progress-meta {
      display: flex;
      justify-content: space-between;
      font-size: 15px;
      color: var(--muted);
      margin-bottom: 6px;
      font-weight: 600;
    }

    .progress-bar {
      height: 12px;
      background: var(--surface-soft);
      border-radius: 999px;
      overflow: hidden;
      border: 1px solid var(--border);
    }

    .progress-fill {
      height: 100%;
      background: var(--primary);
      transition: width 0.3s ease;
    }

    .audio-bar {
      background: var(--surface-soft);
      border: 1px solid var(--border);
      border-radius: 14px;
      padding: 14px;
      margin-bottom: 18px;
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      align-items: center;
    }

    .segments-row {
      width: 100%;
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-top: 6px;
    }

    .segment-btn {
      padding: 8px 12px;
      min-height: 38px;
      font-size: 15px;
      background: #fff;
    }

    .spoken-preview {
      margin-top: 8px;
      font-size: 16px;
      color: var(--accent);
      font-weight: 600;
      min-height: 24px;
    }

    .zone-box {
      background: #fafcfb;
      border: 1.5px dashed #b7c9be;
      border-radius: 14px;
      padding: 16px;
      min-height: 82px;
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      align-items: center;
      margin-bottom: 14px;
    }

    .chip {
      background: #fff;
      border: 2px solid #9db7a8;
      border-radius: 12px;
      padding: 10px 14px;
      font-weight: 600;
      cursor: grab;
      user-select: none;
      touch-action: manipulation;
    }

    .chip:hover {
      border-color: var(--primary);
      background: var(--primary-soft);
    }

    .chip.in-answer {
      background: var(--accent-soft);
      border-color: var(--accent);
    }

    .chip.used {
      opacity: 0.35;
    }

    /* Texte naturel sans cases pour les niveaux 3 et 4 */
    .fluent-passage {
      font-size: calc(var(--font-size-base) + 2px);
      line-height: 2.15;
      padding: 18px 20px;
      background: #fcfdfb;
      border: 1px solid var(--border);
      border-radius: 14px;
      margin: 14px 0 18px;
    }

    .fluent-word {
      display: inline;
      padding: 2px 3px;
      border-radius: 5px;
      cursor: pointer;
      transition: background 0.15s ease;
    }

    .fluent-word:hover {
      background: #e6f0eb;
    }

    .fluent-word.selected-word {
      background: var(--accent-soft);
      text-decoration: underline wavy var(--accent);
      text-underline-offset: 5px;
    }

    .fluent-word.corrected-word {
      background: var(--primary-soft);
      border-bottom: 2px solid var(--primary);
      font-weight: 700;
    }

    .correction-editor {
      background: var(--surface-soft);
      border: 1px solid var(--border);
      border-radius: 14px;
      padding: 16px;
      margin-bottom: 16px;
    }

    .correction-list {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-top: 10px;
    }

    .correction-tag {
      background: #fff;
      border: 1px solid var(--border);
      border-radius: 999px;
      padding: 6px 12px;
      font-size: 15px;
      display: inline-flex;
      align-items: center;
      gap: 8px;
    }

    .correction-tag button {
      min-height: unset;
      padding: 2px 7px;
      font-size: 13px;
      border-radius: 999px;
    }

    .feedback {
      border-radius: 14px;
      padding: 16px 18px;
      margin-top: 16px;
      border: 1.5px solid transparent;
    }

    .feedback.ok {
      background: var(--ok-soft);
      border-color: #86efac;
      color: var(--ok);
    }

    .feedback.err {
      background: var(--err-soft);
      border-color: #fca5a5;
      color: var(--err);
    }

    .feedback.hint {
      background: var(--warn-soft);
      border-color: #fcd34d;
      color: #78350f;
    }

    .step-tabs {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin: 14px 0;
    }

    .step-tab.done {
      background: var(--ok-soft);
      border-color: #86efac;
      color: var(--ok);
    }

    .accent-bar {
      display: flex;
      flex-wrap: wrap;
      gap: 6px;
      margin-top: 8px;
    }

    .accent-btn {
      min-height: 38px;
      padding: 6px 11px;
      font-size: 16px;
      background: var(--surface-soft);
    }

    .action-row {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-top: 16px;
      align-items: center;
    }

    .celebrate {
      animation: popIn 0.35s ease;
    }

    @keyframes popIn {
      0% { transform: scale(0.96); opacity: 0.6; }
      100% { transform: scale(1); opacity: 1; }
    }

    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 10px;
      font-size: 15px;
    }

    th, td {
      border-bottom: 1px solid var(--border);
      padding: 10px 8px;
      text-align: left;
    }

    th {
      background: var(--surface-soft);
    }

    .hidden { display: none !important; }
  </style>
</head>
<body>
  <header class="topbar">
    <div class="brand" onclick="goHome()">
      <div class="brand-badge">M</div>
      <div>
        <h1>Ma dictée pas à pas</h1>
        <small>Orthographe &amp; production écrite — CM1</small>
      </div>
    </div>
    <div class="topbar-actions">
      <button id="btnDys" type="button" onclick="toggleDys()">Texte aéré</button>
      <button id="btnHome" type="button" onclick="goHome()">Accueil élève</button>
      <button id="btnTeacher" type="button" onclick="openTeacherGate()">Espace enseignant</button>
    </div>
  </header>

  <main class="container">
    <!-- ACCUEIL ÉLÈVE -->
    <section id="viewHome" class="card">
      <h2>Bienvenue ! Préparons ta dictée</h2>
      <p style="color:var(--muted); margin-top:0;">Travaille à ton rythme, sans stress. Tu peux écouter les phrases autant de fois que tu veux.</p>

      <div class="grid-2">
        <div class="field">
          <label for="studentName">Ton prénom ou pseudo</label>
          <input id="studentName" type="text" placeholder="Ex. : Léo, Chloé, Élève 3..." maxlength="30" />
        </div>
        <div class="field">
          <label for="dictationSelect">Choisis la dictée</label>
          <select id="dictationSelect" onchange="renderLevelSelector()"></select>
        </div>
      </div>

      <div class="field">
        <label>Choisis ton niveau</label>
        <div id="levelSelector" class="level-grid"></div>
      </div>

      <div class="action-row">
        <button id="btnStart" class="btn-primary" type="button" onclick="startExercise()">Commencer</button>
      </div>
    </section>

    <!-- ESPACE EXERCICE ÉLÈVE -->
    <section id="viewExercise" class="card hidden"></section>

    <!-- CONNEXION ENSEIGNANT -->
    <section id="viewTeacherLogin" class="card hidden">
      <h2>Espace enseignant</h2>
      <p style="color:var(--muted);">Saisissez le code d'accès enseignant pour gérer les dictées, ajuster les 6 niveaux et consulter le suivi.</p>
      <div class="field" style="max-width:320px;">
        <label for="teacherCodeInput">Code d'accès (par défaut : 1234)</label>
        <input id="teacherCodeInput" type="password" value="1234" />
      </div>
      <div class="action-row">
        <button class="btn-primary" type="button" onclick="verifyTeacherCode()">Accéder</button>
        <button type="button" onclick="goHome()">Retour</button>
      </div>
      <div id="teacherLoginMsg"></div>
    </section>

    <!-- ESPACE ENSEIGNANT -->
    <section id="viewTeacher" class="card hidden"></section>
  </main>

  <script>
    const STORAGE_KEY = "ma_dictee_pas_a_pas_v1";
    const DEFAULT_CODE = "1234";

    const LEVEL_META = [
      { id: 1, title: "Je reconstruis les phrases", desc: "Remets les groupes de mots dans l'ordre." },
      { id: 2, title: "Je remets les mots dans l'ordre", desc: "Reconstruis la phrase mot par mot." },
      { id: 3, title: "Je trouve et corrige les erreurs", desc: "Repère les mots à corriger et écris la bonne forme." },
      { id: 4, title: "Je relis et corrige seul", desc: "Relis un court texte et corrige les erreurs." },
      { id: 5, title: "Je réalise la dictée", desc: "Écoute par segments, écris puis relis en 4 étapes." },
      { id: 6, title: "Je transfère mes connaissances", desc: "Transforme une phrase juste selon la consigne." }
    ];

    const ENCOURAGEMENTS = [
      "Bravo, tu progresses !",
      "Super travail, continue comme ça !",
      "Très bien ! Tu prends confiance.",
      "Belle réussite !"
    ];

    const GENTLE_PROMPTS = [
      "Encore un petit effort !",
      "Tu peux y arriver ! Regarde bien.",
      "Ce n'est pas grave, on essaie ensemble."
    ];

    // Mémoire sécurisée avec repli en mémoire vive
    const memoryFallback = {};
    function readStore() {
      try {
        const raw = window.localStorage.getItem(STORAGE_KEY);
        if (raw) return JSON.parse(raw);
      } catch (e) {}
      return memoryFallback.data ? JSON.parse(JSON.stringify(memoryFallback.data)) : null;
    }

    function writeStore(data) {
      memoryFallback.data = JSON.parse(JSON.stringify(data));
      try {
        window.localStorage.setItem(STORAGE_KEY, JSON.stringify(data));
      } catch (e) {}
    }

    function createInitialData() {
      return {
        teacherCode: DEFAULT_CODE,
        dictations: [
          {
            id: "dic_foret",
            title: "La promenade dans la forêt",
            text: "Les petits oiseaux chantent dans le jardin. Le matin, la rosée brille sur les feuilles. Les enfants préparent leur cartable et partent à l'école.",
            enabledLevels: [1, 2, 3, 4, 5, 6],
            level3Items: [
              {
                sentence: "Les petits oiseaux chantent dans le jardin.",
                errors: [
                  {
                    wrong: "chantent",
                    expected: "chantent",
                    displayWrong: "chante",
                    category: "accord sujet-verbe",
                    hint1: "Regarde qui fait l'action : c'est « Les petits oiseaux » (au pluriel).",
                    hint2: "Le verbe chanter est au pluriel : il se termine par -ent.",
                    explanation: "Le sujet « Les petits oiseaux » est au pluriel : on écrit « chantent »."
                  }
                ]
              },
              {
                sentence: "Le matin, la rosée brille sur les feuilles.",
                errors: [
                  {
                    wrong: "brille",
                    expected: "brille",
                    displayWrong: "brillent",
                    category: "accord sujet-verbe",
                    hint1: "Quel est le sujet du verbe briller ?",
                    hint2: "« La rosée » est singulier : le verbe se termine par -e.",
                    explanation: "Le sujet est « la rosée » (singulier) : on écrit « brille »."
                  },
                  {
                    wrong: "feuilles",
                    expected: "feuilles",
                    displayWrong: "feuille",
                    category: "accord dans le groupe nominal",
                    hint1: "Regarde le déterminant « les » avant le nom.",
                    hint2: "« les » indique le pluriel : il faut un -s à la fin du nom.",
                    explanation: "Avec le déterminant pluriel « les », le nom prend un -s : « feuilles »."
                  }
                ]
              }
            ],
            level4Items: [
              {
                text: "Les petits oiseaux chante dans le jardin. Le matin, la rosée brille sur les feuille.",
                errors: [
                  {
                    displayWrong: "chante",
                    expected: "chantent",
                    category: "accord sujet-verbe",
                    hint: "Vérifie l'accord du verbe avec « Les petits oiseaux »."
                  },
                  {
                    displayWrong: "feuille",
                    expected: "feuilles",
                    category: "accord dans le groupe nominal",
                    hint: "Regarde le déterminant « les » devant ce nom."
                  }
                ]
              }
            ],
            level6Items: [
              {
                sourceSentence: "Les petits oiseaux chantent dans le jardin.",
                instruction: "Transforme cette phrase au singulier : remplace « Les petits oiseaux » par « Le petit oiseau ».",
                expectedSentence: "Le petit oiseau chante dans le jardin.",
                explanation: "Au singulier, « petit » perd son -s et le verbe « chante » se termine par -e."
              },
              {
                sourceSentence: "Le matin, la rosée brille sur les feuilles.",
                instruction: "Transforme cette phrase en remplaçant « les feuilles » par « la feuille ».",
                expectedSentence: "Le matin, la rosée brille sur la feuille.",
                explanation: "Le déterminant « la » est au singulier, donc « feuille » ne prend pas de -s."
              }
            ]
          },
          {
            id: "dic_ecole",
            title: "À l'école et à la maison",
            text: "Paul et Léa rangent leurs livres. Il est à la bibliothèque et elle est à la maison. Ils aiment lire des histoires.",
            enabledLevels: [1, 2, 3, 4, 5, 6],
            level3Items: [
              {
                sentence: "Paul et Léa rangent leurs livres.",
                errors: [
                  {
                    displayWrong: "est",
                    expected: "et",
                    category: "homophone et / est",
                    hint1: "Essaie de remplacer ce mot par « et puis ».",
                    hint2: "Ici, on relie deux prénoms : Paul et Léa.",
                    explanation: "On écrit « et » (conjunction) car on peut dire « Paul et puis Léa »."
                  }
                ]
              }
            ],
            level4Items: [
              {
                text: "Paul et Léa range leurs livres. Ils aiment lire des histoire.",
                errors: [
                  {
                    displayWrong: "range",
                    expected: "rangent",
                    category: "accord sujet-verbe",
                    hint: "Quel est le sujet de ce verbe ? Paul et Léa font l'action."
                  },
                  {
                    displayWrong: "histoire",
                    expected: "histoires",
                    category: "accord dans le groupe nominal",
                    hint: "Regarde le déterminant « des » avant le nom."
                  }
                ]
              }
            ],
            level6Items: [
              {
                sourceSentence: "Paul et Léa rangent leurs livres.",
                instruction: "Transforme cette phrase au singulier en commençant par « Paul range ».",
                expectedSentence: "Paul range son livre.",
                explanation: "Avec un seul sujet « Paul », le verbe s'écrit « range » et « leurs livres » devient « son livre »."
              }
            ]
          }
        ],
        results: []
      };
    }

    let state = {
      appData: readStore() || createInitialData(),
      studentName: "",
      currentDictationId: null,
      currentLevel: 1,
      itemIndex: 0,
      dysMode: false,
      // État d'exercice courant
      ex: {}
    };

    if (!readStore()) {
      writeStore(state.appData);
    }
    state.currentDictationId = state.appData.dictations[0]?.id || null;

    function toggleDys() {
      state.dysMode = !state.dysMode;
      document.body.classList.toggle("dys-mode", state.dysMode);
      document.getElementById("btnDys").classList.toggle("btn-active", state.dysMode);
    }

    function showView(id) {
      ["viewHome", "viewExercise", "viewTeacherLogin", "viewTeacher"].forEach((v) => {
        document.getElementById(v).classList.toggle("hidden", v !== id);
      });
    }

    function goHome() {
      stopSpeech();
      renderHome();
      showView("viewHome");
    }

    function getCurrentDictation() {
      return state.appData.dictations.find((d) => d.id === state.currentDictationId) || state.appData.dictations[0];
    }

    function renderHome() {
      const sel = document.getElementById("dictationSelect");
      sel.innerHTML = state.appData.dictations
        .map((d) => `<option value="${escapeAttr(d.id)}" ${d.id === state.currentDictationId ? "selected" : ""}>${escapeHtml(d.title)}</option>`)
        .join("");
      document.getElementById("studentName").value = state.studentName;
      renderLevelSelector();
    }

    function renderLevelSelector() {
      const id = document.getElementById("dictationSelect").value;
      state.currentDictationId = id;
      const dic = getCurrentDictation();
      const enabled = dic ? dic.enabledLevels : [1, 2, 3, 4, 5, 6];
      if (!enabled.includes(state.currentLevel) && enabled.length) {
        state.currentLevel = enabled[0];
      }

      const container = document.getElementById("levelSelector");
      container.innerHTML = LEVEL_META.map((lvl) => {
        const isEnabled = enabled.includes(lvl.id);
        const isSelected = isEnabled && state.currentLevel === lvl.id;
        return `
          <button type="button"
            class="level-option ${isSelected ? "selected" : ""} ${!isEnabled ? "locked" : ""}"
            ${!isEnabled ? "disabled" : ""}
            onclick="selectLevel(${lvl.id})">
            <span class="level-num">Niveau ${lvl.id} ${!isEnabled ? "— Masqué" : ""}</span>
            <span class="level-title">${escapeHtml(lvl.title)}</span>
            <span class="level-desc">${escapeHtml(lvl.desc)}</span>
          </button>
        `;
      }).join("");
    }

    function selectLevel(lvl) {
      state.currentLevel = lvl;
      renderLevelSelector();
    }

    // Synthèse vocale française
    function stopSpeech() {
      if ("speechSynthesis" in window) {
        window.speechSynthesis.cancel();
      }
      const el = document.getElementById("spokenPreview");
      if (el) el.textContent = "";
    }

    function speakText(text, rate = 1.0, highlightLabel = "") {
      const preview = document.getElementById("spokenPreview");
      if (preview) preview.textContent = highlightLabel || text;
      if (!("speechSynthesis" in window)) return;
      window.speechSynthesis.cancel();
      const utter = new SpeechSynthesisUtterance(text);
      utter.lang = "fr-FR";
      utter.rate = rate;
      const voices = window.speechSynthesis.getVoices();
      const frVoice = voices.find((v) => v.lang && v.lang.toLowerCase().startsWith("fr"));
      if (frVoice) utter.voice = frVoice;
      window.speechSynthesis.speak(utter);
    }

    function speakWordByWord(sentence) {
      const words = sentence.split(/\s+/).filter(Boolean);
      const preview = document.getElementById("spokenPreview");
      if (!("speechSynthesis" in window)) {
        if (preview) preview.textContent = words.join(" · ");
        return;
      }
      window.speechSynthesis.cancel();
      words.forEach((w, idx) => {
        const clean = w.replace(/^[,.;:!?«»"']+|[,.;:!?«»"']+$/g, "") || w;
        const utter = new SpeechSynthesisUtterance(clean);
        utter.lang = "fr-FR";
        utter.rate = 0.85;
        const voices = window.speechSynthesis.getVoices();
        const frVoice = voices.find((v) => v.lang && v.lang.toLowerCase().startsWith("fr"));
        if (frVoice) utter.voice = frVoice;
        utter.onstart = () => {
          if (preview) {
            preview.innerHTML = words
              .map((tok, i) => i === idx ? `<mark style="background:#d8f3dc;padding:2px 5px;border-radius:6px;">${escapeHtml(tok)}</mark>` : escapeHtml(tok))
              .join(" ");
          }
        };
        window.speechSynthesis.speak(utter);
      });
    }

    function renderAudioBar(text, allowSegments = false) {
      const segments = text
        .split(/[,;]+/)
        .map((s) => s.trim())
        .filter(Boolean);
      return `
        <div class="audio-bar">
          <button type="button" class="btn-soft" onclick="speakText(${JSON.stringify(text)}, 1.0)">Écouter la phrase</button>
          <button type="button" class="btn-soft" onclick="speakText(${JSON.stringify(text)}, 0.68)">Lecture lente</button>
          <button type="button" class="btn-soft" onclick="speakWordByWord(${JSON.stringify(text)})">Mot par mot</button>
          <button type="button" onclick="stopSpeech()">Stop</button>
          ${allowSegments && segments.length > 1 ? `
            <div class="segments-row">
              <span style="font-size:14px;color:var(--muted);align-self:center;">Segments :</span>
              ${segments.map((seg, i) => `
                <button type="button" class="segment-btn" onclick="speakText(${JSON.stringify(seg)}, 0.85, 'Segment ${i + 1} : ' + ${JSON.stringify(seg)})">
                  Segment ${i + 1}
                </button>
              `).join("")}
            </div>
          ` : ""}
          <div id="spokenPreview" class="spoken-preview"></div>
        </div>
      `;
    }

    // Découpage intelligent sans modifier la dictée originale
    function splitSentences(text) {
      return text
        .match(/[^.!?]+[.!?]+/g)
        ?.map((s) => s.trim())
        .filter(Boolean) || [text.trim()];
    }

    function splitChunks(sentence) {
      const clean = sentence.trim();
      const punct = clean.slice(-1);
      const body = /[.!?]/.test(punct) ? clean.slice(0, -1).trim() : clean;
      const parts = body.split(",").map((p) => p.trim()).filter(Boolean);
      if (parts.length > 1) {
        parts[parts.length - 1] = parts[parts.length - 1] + (/[.!?]/.test(punct) ? punct : "");
        return parts;
      }
      const words = body.split(/\s+/);
      if (words.length <= 4) return [clean];
      const chunks = [];
      for (let i = 0; i < words.length; i += 2) {
        let piece = words.slice(i, i + 2).join(" ");
        if (i + 2 >= words.length && /[.!?]/.test(punct)) {
          piece += punct;
        }
        chunks.push(piece);
      }
      return chunks;
    }

    function shuffleArray(arr) {
      const copy = arr.slice();
      for (let i = copy.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [copy[i], copy[j]] = [copy[j], copy[i]];
      }
      return copy;
    }

    function startExercise() {
      const nameInput = document.getElementById("studentName").value.trim();
      state.studentName = nameInput || "Élève";
      state.currentDictationId = document.getElementById("dictationSelect").value;
      state.itemIndex = 0;
      initItemState();
      showView("viewExercise");
      renderExercise();
    }

    function getItemsForLevel(dic, lvl) {
      const sentences = splitSentences(dic.text);
      if (lvl === 1 || lvl === 2) return sentences;
      if (lvl === 3) return dic.level3Items && dic.level3Items.length ? dic.level3Items : [{ sentence: sentences[0], errors: [] }];
      if (lvl === 4) return dic.level4Items && dic.level4Items.length ? dic.level4Items : [{ text: sentences.slice(0, 2).join(" "), errors: [] }];
      if (lvl === 5) return sentences;
      if (lvl === 6) return dic.level6Items && dic.level6Items.length ? dic.level6Items : [{ sourceSentence: sentences[0], instruction: "Réécris cette phrase correctement.", expectedSentence: sentences[0], explanation: "Phrase de référence." }];
      return sentences;
    }

    function initItemState() {
      const dic = getCurrentDictation();
      const items = getItemsForLevel(dic, state.currentLevel);
      const item = items[state.itemIndex];
      const lvl = state.currentLevel;

      if (lvl === 1) {
        const target = splitChunks(item);
        let pool = shuffleArray(target.map((txt, idx) => ({ id: "c" + idx, text: txt })));
        if (pool.map((p) => p.text).join(" ") === target.join(" ") && pool.length > 1) {
          pool = pool.reverse();
        }
        state.ex = { target, pool, chosenIds: [], attempts: 0, hintLevel: 0, feedback: null, solved: false };
      } else if (lvl === 2) {
        const targetTokens = item.match(/\S+/g) || [];
        let pool = shuffleArray(targetTokens.map((tok, idx) => ({ id: "w" + idx, text: tok })));
        if (pool.map((p) => p.text).join(" ") === targetTokens.join(" ") && pool.length > 1) {
          pool = pool.reverse();
        }
        state.ex = { targetTokens, pool, chosenIds: [], attempts: 0, hintLevel: 0, feedback: null, solved: false };
      } else if (lvl === 3) {
        const tokens = item.match(/\S+/g) || [];
        state.ex = {
          tokens,
          errors: item.errors || [],
          selectedTokenIdx: null,
          corrections: {}, // tokenIdx -> mot saisi
          attempts: 0,
          hintStage: 0, // 0: aucun, 1: nature, 2: position/mot
          feedback: null,
          solved: false
        };
      } else if (lvl === 4) {
        const tokens = (item.text || "").match(/\S+/g) || [];
        state.ex = {
          tokens,
          errors: item.errors || [],
          selectedTokenIdx: null,
          corrections: {},
          attempts: 0,
          showHint: false,
          feedback: null,
          solved: false
        };
      } else if (lvl === 5) {
        state.ex = {
          targetSentence: item,
          draft: "",
          reviewStep: 1, // 1..4
          checkedSteps: [false, false, false, false],
          validated: false,
          feedback: null
        };
      } else if (lvl === 6) {
        state.ex = {
          item,
          answer: "",
          attempts: 0,
          feedback: null,
          solved: false
        };
      }
    }

    function recordResult(success, errorLabel) {
      const dic = getCurrentDictation();
      state.appData.results.push({
        id: "r_" + Date.now() + "_" + Math.random().toString(36).slice(2, 6),
        date: new Date().toLocaleDateString("fr-FR"),
        student: state.studentName,
        dictationTitle: dic.title,
        level: state.currentLevel,
        success: Boolean(success),
        errorTopic: success ? null : (errorLabel || `Niveau ${state.currentLevel}`)
      });
      writeStore(state.appData);
    }

    function renderExercise() {
      const dic = getCurrentDictation();
      const items = getItemsForLevel(dic, state.currentLevel);
      const lvlMeta = LEVEL_META.find((l) => l.id === state.currentLevel);
      const pct = Math.round(((state.itemIndex + (state.ex.solved || state.ex.validated ? 1 : 0)) / items.length) * 100);
      const box = document.getElementById("viewExercise");

      let bodyHtml = "";
      if (state.currentLevel === 1) bodyHtml = renderLevel1(items[state.itemIndex]);
      else if (state.currentLevel === 2) bodyHtml = renderLevel2(items[state.itemIndex]);
      else if (state.currentLevel === 3) bodyHtml = renderLevel3();
      else if (state.currentLevel === 4) bodyHtml = renderLevel4();
      else if (state.currentLevel === 5) bodyHtml = renderLevel5();
      else if (state.currentLevel === 6) bodyHtml = renderLevel6();

      const hasNext = state.itemIndex + 1 < items.length;
      const canAdvance = state.ex.solved || state.ex.validated;

      box.innerHTML = `
        <div style="display:flex;justify-content:space-between;flex-wrap:wrap;gap:8px;align-items:center;margin-bottom:8px;">
          <div>
            <span class="level-num">Niveau ${state.currentLevel} — ${escapeHtml(lvlMeta.title)}</span>
            <h2 style="margin:2px 0 0;">${escapeHtml(dic.title)}</h2>
          </div>
          <span style="font-size:15px;color:var(--muted);font-weight:600;">Élève : ${escapeHtml(state.studentName)}</span>
        </div>

        <div class="progress-wrap">
          <div class="progress-meta">
            <span>Élément ${state.itemIndex + 1} sur ${items.length}</span>
            <span>${pct}%</span>
          </div>
          <div class="progress-bar"><div class="progress-fill" style="width:${pct}%;"></div></div>
        </div>

        ${bodyHtml}

        ${state.ex.feedback ? `
          <div class="feedback ${state.ex.feedback.type} celebrate">
            <strong>${escapeHtml(state.ex.feedback.title)}</strong>
            <div style="margin-top:6px;">${state.ex.feedback.html}</div>
          </div>
        ` : ""}

        <div class="action-row">
          ${canAdvance && hasNext ? `<button class="btn-primary" type="button" onclick="nextItem()">Phrase suivante</button>` : ""}
          ${canAdvance && !hasNext ? `<button class="btn-primary" type="button" onclick="goHome()">Terminer et retourner à l'accueil</button>` : ""}
        </div>
      `;
    }

    function nextItem() {
      stopSpeech();
      state.itemIndex += 1;
      initItemState();
      renderExercise();
    }

    // NIVEAU 1
    function renderLevel1(sentence) {
      const chosen = state.ex.chosenIds.map((id) => state.ex.pool.find((p) => p.id === id)).filter(Boolean);
      return `
        <p><strong>Consigne :</strong> Écoute la phrase puis remets les groupes de mots dans l'ordre (par clic ou glisser-déposer).</p>
        ${renderAudioBar(sentence, false)}
        <div class="zone-box" ondragover="event.preventDefault()" ondrop="onDropChip1(event)">
          ${chosen.length ? chosen.map((c) => `
            <button type="button" class="chip in-answer" draggable="true" ondragstart="onDragStartChip(event, '${c.id}')" onclick="removeChip1('${c.id}')">${escapeHtml(c.text)}</button>
          `).join("") : `<span style="color:var(--muted);">Clique sur des étiquettes ci-dessous pour construire la phrase...</span>`}
        </div>
        <div class="zone-box" style="border-style:solid;background:#fff;">
          ${state.ex.pool.map((c) => {
            const used = state.ex.chosenIds.includes(c.id);
            return `<button type="button" class="chip ${used ? "used" : ""}" ${used ? "disabled" : ""} draggable="true" ondragstart="onDragStartChip(event, '${c.id}')" onclick="addChip1('${c.id}')">${escapeHtml(c.text)}</button>`;
          }).join("")}
        </div>
        <div class="action-row">
          <button type="button" class="btn-primary" onclick="checkLevel1()">Vérifier</button>
          <button type="button" class="btn-warn" onclick="hintLevel1()">Indice</button>
          <button type="button" onclick="resetLevel1()">Recommencer</button>
        </div>
      `;
    }

    function onDragStartChip(ev, id) {
      ev.dataTransfer.setData("text/plain", id);
    }

    function onDropChip1(ev) {
      ev.preventDefault();
      const id = ev.dataTransfer.getData("text/plain");
      if (id && !state.ex.chosenIds.includes(id)) {
        state.ex.chosenIds.push(id);
        renderExercise();
      }
    }

    function addChip1(id) {
      if (!state.ex.chosenIds.includes(id)) {
        state.ex.chosenIds.push(id);
        renderExercise();
      }
    }

    function removeChip1(id) {
      state.ex.chosenIds = state.ex.chosenIds.filter((x) => x !== id);
      renderExercise();
    }

    function resetLevel1() {
      state.ex.chosenIds = [];
      state.ex.feedback = null;
      renderExercise();
    }

    function hintLevel1() {
      state.ex.hintLevel += 1;
      const first = state.ex.target[0];
      const msg = state.ex.hintLevel === 1
        ? `Le premier groupe de mots commence par : <strong>${escapeHtml(first)}</strong>.`
        : `La phrase complète attendue est : <strong>${escapeHtml(state.ex.target.join(" "))}</strong>.`;
      state.ex.feedback = { type: "hint", title: "Indice", html: msg };
      renderExercise();
    }

    function checkLevel1() {
      const built = state.ex.chosenIds.map((id) => state.ex.pool.find((p) => p.id === id)?.text || "").join(" ");
      const expected = state.ex.target.join(" ");
      state.ex.attempts += 1;
      if (built === expected) {
        state.ex.solved = true;
        const praise = ENCOURAGEMENTS[state.ex.attempts % ENCOURAGEMENTS.length];
        state.ex.feedback = { type: "ok", title: praise, html: `Tu as bien reconstruit la phrase : <strong>${escapeHtml(expected)}</strong>.` };
        recordResult(true, null);
      } else {
        const gentle = GENTLE_PROMPTS[state.ex.attempts % GENTLE_PROMPTS.length];
        state.ex.feedback = {
          type: "err",
          title: gentle,
          html: `Ta phrase : « ${escapeHtml(built || "(vide)")} ». Demande un indice ou clique sur Recommencer.`
        };
        recordResult(false, "Ordre des groupes de mots");
      }
      renderExercise();
    }

    // NIVEAU 2
    function renderLevel2(sentence) {
      const chosen = state.ex.chosenIds.map((id) => state.ex.pool.find((p) => p.id === id)).filter(Boolean);
      return `
        <p><strong>Consigne :</strong> Remets chaque mot à sa place en respectant la majuscule et la ponctuation.</p>
        ${renderAudioBar(sentence, false)}
        <div class="zone-box" ondragover="event.preventDefault()" ondrop="onDropChip2(event)">
          ${chosen.length ? chosen.map((c) => `
            <button type="button" class="chip in-answer" draggable="true" ondragstart="onDragStartChip(event, '${c.id}')" onclick="removeChip2('${c.id}')">${escapeHtml(c.text)}</button>
          `).join("") : `<span style="color:var(--muted);">Clique sur les mots dans l'ordre de la phrase...</span>`}
        </div>
        <div class="zone-box" style="border-style:solid;background:#fff;">
          ${state.ex.pool.map((c) => {
            const used = state.ex.chosenIds.includes(c.id);
            return `<button type="button" class="chip ${used ? "used" : ""}" ${used ? "disabled" : ""} draggable="true" ondragstart="onDragStartChip(event, '${c.id}')" onclick="addChip2('${c.id}')">${escapeHtml(c.text)}</button>`;
          }).join("")}
        </div>
        <div class="action-row">
          <button type="button" class="btn-primary" onclick="checkLevel2()">Vérifier</button>
          <button type="button" class="btn-warn" onclick="hintLevel2()">Indice</button>
          <button type="button" onclick="resetLevel2()">Recommencer</button>
        </div>
      `;
    }

    function onDropChip2(ev) {
      ev.preventDefault();
      const id = ev.dataTransfer.getData("text/plain");
      if (id && !state.ex.chosenIds.includes(id)) {
        state.ex.chosenIds.push(id);
        renderExercise();
      }
    }

    function addChip2(id) {
      if (!state.ex.chosenIds.includes(id)) {
        state.ex.chosenIds.push(id);
        renderExercise();
      }
    }

    function removeChip2(id) {
      state.ex.chosenIds = state.ex.chosenIds.filter((x) => x !== id);
      renderExercise();
    }

    function resetLevel2() {
      state.ex.chosenIds = [];
      state.ex.feedback = null;
      renderExercise();
    }

    function hintLevel2() {
      state.ex.hintLevel += 1;
      const nextWord = state.ex.targetTokens[state.ex.chosenIds.length] || state.ex.targetTokens[0];
      state.ex.feedback = {
        type: "hint",
        title: "Indice",
        html: state.ex.hintLevel === 1
          ? `Le mot suivant attendu est : <strong>${escapeHtml(nextWord)}</strong>.`
          : `Regarde bien la majuscule au début et le point à la fin.`
      };
      renderExercise();
    }

    function checkLevel2() {
      const built = state.ex.chosenIds.map((id) => state.ex.pool.find((p) => p.id === id)?.text || "").join(" ");
      const expected = state.ex.targetTokens.join(" ");
      state.ex.attempts += 1;
      if (built === expected) {
        state.ex.solved = true;
        state.ex.feedback = { type: "ok", title: ENCOURAGEMENTS[0], html: `Phrase exacte : <strong>${escapeHtml(expected)}</strong>.` };
        recordResult(true, null);
      } else {
        state.ex.feedback = { type: "err", title: GENTLE_PROMPTS[0], html: `Essai actuel : « ${escapeHtml(built || "(vide)")} ».` };
        recordResult(false, "Ordre des mots / ponctuation");
      }
      renderExercise();
    }

    // NIVEAU 3 : Texte continu sans cases, indices gradués, saisie libre de la correction
    function renderLevel3() {
      const selIdx = state.ex.selectedTokenIdx;
      const selWord = selIdx !== null ? state.ex.tokens[selIdx] : "";
      const selCorrection = selIdx !== null ? (state.ex.corrections[selIdx] || "") : "";
      const entries = Object.entries(state.ex.corrections);

      return `
        <p><strong>Consigne :</strong> Lis la phrase. Clique sur un mot qui te semble mal écrit, puis écris sa correction. Au début, l'erreur n'est pas signalée.</p>
        <div class="fluent-passage">
          ${state.ex.tokens.map((tok, idx) => {
            const isSel = idx === selIdx;
            const hasCorr = Object.prototype.hasOwnProperty.call(state.ex.corrections, idx);
            const shown = hasCorr ? state.ex.corrections[idx] : tok;
            return `<span class="fluent-word ${isSel ? "selected-word" : ""} ${hasCorr ? "corrected-word" : ""}" onclick="selectWord3(${idx})">${escapeHtml(shown)}</span> `;
          }).join("")}
        </div>

        ${selIdx !== null ? `
          <div class="correction-editor">
            <div>Mot sélectionné : <strong>${escapeHtml(selWord)}</strong></div>
            <div style="display:flex;flex-wrap:wrap;gap:10px;margin-top:10px;align-items:center;">
              <input id="corrInput3" type="text" style="max-width:260px;" value="${escapeAttr(selCorrection)}" placeholder="Écris la correction..." />
              <button type="button" class="btn-soft" onclick="saveCorrection3()">Enregistrer ce mot</button>
              <button type="button" onclick="removeCorrection3(${selIdx})">Annuler ce mot</button>
            </div>
            ${renderAccentButtons("corrInput3")}
          </div>
        ` : `<p style="font-size:15px;color:var(--muted);">Clique sur un mot dans la phrase ci-dessus pour le corriger.</p>`}

        ${entries.length ? `
          <div class="correction-list">
            ${entries.map(([idx, val]) => `<span class="correction-tag">Mot n°${Number(idx) + 1} → <strong>${escapeHtml(val)}</strong> <button type="button" onclick="removeCorrection3(${idx})">×</button></span>`).join("")}
          </div>
        ` : ""}

        <div class="action-row">
          <button type="button" class="btn-primary" onclick="checkLevel3()">Vérifier</button>
          <button type="button" class="btn-warn" onclick="hintLevel3()">Indice gradué</button>
          <button type="button" onclick="resetLevel3()">Recommencer</button>
        </div>
      `;
    }

    function selectWord3(idx) {
      state.ex.selectedTokenIdx = idx;
      renderExercise();
      const inp = document.getElementById("corrInput3");
      if (inp) inp.focus();
    }

    function saveCorrection3() {
      const inp = document.getElementById("corrInput3");
      if (!inp || state.ex.selectedTokenIdx === null) return;
      const val = inp.value.trim();
      if (!val) return;
      state.ex.corrections[state.ex.selectedTokenIdx] = val;
      renderExercise();
    }

    function removeCorrection3(idx) {
      delete state.ex.corrections[idx];
      renderExercise();
    }

    function resetLevel3() {
      state.ex.corrections = {};
      state.ex.selectedTokenIdx = null;
      state.ex.feedback = null;
      renderExercise();
    }

    function hintLevel3() {
      state.ex.hintStage += 1;
      const errList = state.ex.errors;
      if (!errList.length) {
        state.ex.feedback = { type: "hint", title: "Indice", html: "Relis calmement chaque mot et vérifie les accords." };
        renderExercise();
        return;
      }
      const targetErr = errList[Math.min(state.ex.hintStage - 1, errList.length - 1)];
      if (state.ex.hintStage === 1) {
        state.ex.feedback = {
          type: "hint",
          title: "Indice 1 — Notion à vérifier",
          html: `L'erreur porte sur : <strong>${escapeHtml(targetErr.category)}</strong>. ${escapeHtml(targetErr.hint1 || "")}`
        };
      } else {
        state.ex.feedback = {
          type: "hint",
          title: "Indice 2 — Piste précise",
          html: `${escapeHtml(targetErr.hint2 || targetErr.hint1 || "Observe bien la terminaison ou l'orthographe du mot.")}`
        };
      }
      renderExercise();
    }

    function checkLevel3() {
      const inp = document.getElementById("corrInput3");
      if (inp && inp.value.trim() && state.ex.selectedTokenIdx !== null) {
        state.ex.corrections[state.ex.selectedTokenIdx] = inp.value.trim();
      }
      state.ex.attempts += 1;
      const expectedWrongs = state.ex.errors.map((e) => e.expected.toLowerCase());
      const userVals = Object.values(state.ex.corrections).map((v) => v.toLowerCase());
      const allFound = expectedWrongs.every((exp) => userVals.includes(exp)) && expectedWrongs.length > 0;

      if (allFound) {
        state.ex.solved = true;
        const explanations = state.ex.errors.map((e) => `<li><strong>${escapeHtml(e.displayWrong)} → ${escapeHtml(e.expected)} :</strong> ${escapeHtml(e.explanation)}</li>`).join("");
        state.ex.feedback = {
          type: "ok",
          title: ENCOURAGEMENTS[0],
          html: `<ul style="margin:4px 0 0 18px;">${explanations}</ul>`
        };
        recordResult(true, null);
      } else {
        const explanations = state.ex.errors.map((e) => `<li><strong>${escapeHtml(e.expected)}</strong> (${escapeHtml(e.category)}) : ${escapeHtml(e.explanation)}</li>`).join("");
        state.ex.feedback = {
          type: "err",
          title: GENTLE_PROMPTS[state.ex.attempts % GENTLE_PROMPTS.length],
          html: `Tu n'as pas encore corrigé toutes les erreurs prévues. Demande un indice ou essaie encore.<br><details style="margin-top:8px;"><summary>Voir l'explication après essai</summary><ul style="margin:6px 0 0 18px;">${explanations}</ul></details>`
        };
        recordResult(false, state.ex.errors[0]?.category || "Correction orthographique");
      }
      renderExercise();
    }

    // NIVEAU 4 : Relecture d'un court texte sans cases, bilan du nombre d'erreurs trouvées, indice ciblé, 2e tentative
    function renderLevel4() {
      const selIdx = state.ex.selectedTokenIdx;
      const selWord = selIdx !== null ? state.ex.tokens[selIdx] : "";
      const selCorr = selIdx !== null ? (state.ex.corrections[selIdx] || "") : "";
      const entries = Object.entries(state.ex.corrections);

      return `
        <p><strong>Consigne :</strong> Relis ce court texte et corrige les mots incorrects (${state.ex.errors.length} erreur(s) à repérer). Aucun mot n'est souligné au départ.</p>
        <div class="fluent-passage">
          ${state.ex.tokens.map((tok, idx) => {
            const isSel = idx === selIdx;
            const hasCorr = Object.prototype.hasOwnProperty.call(state.ex.corrections, idx);
            const shown = hasCorr ? state.ex.corrections[idx] : tok;
            return `<span class="fluent-word ${isSel ? "selected-word" : ""} ${hasCorr ? "corrected-word" : ""}" onclick="selectWord4(${idx})">${escapeHtml(shown)}</span> `;
          }).join("")}
        </div>

        ${selIdx !== null ? `
          <div class="correction-editor">
            <div>Mot sélectionné : <strong>${escapeHtml(selWord)}</strong></div>
            <div style="display:flex;flex-wrap:wrap;gap:10px;margin-top:10px;align-items:center;">
              <input id="corrInput4" type="text" style="max-width:260px;" value="${escapeAttr(selCorr)}" placeholder="Écris la correction..." />
              <button type="button" class="btn-soft" onclick="saveCorrection4()">Valider ce mot</button>
              <button type="button" onclick="removeCorrection4(${selIdx})">Retirer</button>
            </div>
            ${renderAccentButtons("corrInput4")}
          </div>
        ` : `<p style="font-size:15px;color:var(--muted);">Clique sur un mot du texte pour proposer ta correction.</p>`}

        ${entries.length ? `
          <div class="correction-list">
            ${entries.map(([idx, val]) => `<span class="correction-tag">Mot n°${Number(idx) + 1} → <strong>${escapeHtml(val)}</strong> <button type="button" onclick="removeCorrection4(${idx})">×</button></span>`).join("")}
          </div>
        ` : ""}

        <div class="action-row">
          <button type="button" class="btn-primary" onclick="checkLevel4()">Vérifier ma relecture</button>
          ${state.ex.attempts >= 1 && !state.ex.solved ? `<button type="button" class="btn-warn" onclick="hintLevel4()">Indice ciblé</button>` : ""}
          <button type="button" onclick="resetLevel4()">Recommencer</button>
        </div>
      `;
    }

    function selectWord4(idx) {
      state.ex.selectedTokenIdx = idx;
      renderExercise();
      const inp = document.getElementById("corrInput4");
      if (inp) inp.focus();
    }

    function saveCorrection4() {
      const inp = document.getElementById("corrInput4");
      if (!inp || state.ex.selectedTokenIdx === null) return;
      const val = inp.value.trim();
      if (!val) return;
      state.ex.corrections[state.ex.selectedTokenIdx] = val;
      renderExercise();
    }

    function removeCorrection4(idx) {
      delete state.ex.corrections[idx];
      renderExercise();
    }

    function resetLevel4() {
      state.ex.corrections = {};
      state.ex.selectedTokenIdx = null;
      state.ex.attempts = 0;
      state.ex.feedback = null;
      state.ex.solved = false;
      renderExercise();
    }

    function hintLevel4() {
      const hints = state.ex.errors.map((e) => `<li><strong>${escapeHtml(e.category)} :</strong> ${escapeHtml(e.hint)}</li>`).join("");
      state.ex.feedback = {
        type: "hint",
        title: "Indices ciblés pour ta nouvelle tentative",
        html: `<ul style="margin:4px 0 0 18px;">${hints}</ul>`
      };
      renderExercise();
    }

    function checkLevel4() {
      const inp = document.getElementById("corrInput4");
      if (inp && inp.value.trim() && state.ex.selectedTokenIdx !== null) {
        state.ex.corrections[state.ex.selectedTokenIdx] = inp.value.trim();
      }
      state.ex.attempts += 1;
      const expected = state.ex.errors.map((e) => e.expected.toLowerCase());
      const userVals = Object.values(state.ex.corrections).map((v) => v.toLowerCase());
      const foundCount = expected.filter((exp) => userVals.includes(exp)).length;
      const total = expected.length;

      if (foundCount === total && total > 0) {
        state.ex.solved = true;
        const details = state.ex.errors.map((e) => `<li><strong>${escapeHtml(e.displayWrong)} → ${escapeHtml(e.expected)}</strong> (${escapeHtml(e.category)})</li>`).join("");
        state.ex.feedback = {
          type: "ok",
          title: "Bravo ! Toutes les erreurs ont été trouvées et corrigées.",
          html: `<ul style="margin:4px 0 0 18px;">${details}</ul>`
        };
        recordResult(true, null);
      } else if (state.ex.attempts === 1) {
        // Après la 1re tentative : indiquer uniquement si toutes ont été trouvées ou s'il en reste, sans souligner
        const statusMsg = foundCount === 0
          ? `Aucune des ${total} erreurs n'a encore été trouvée. Tu peux cliquer sur « Indice ciblé » puis faire une seconde tentative.`
          : `Tu as trouvé ${foundCount} erreur(s) sur ${total} : il en reste encore. Clique sur « Indice ciblé » si tu veux une aide avant ta seconde tentative.`;
        state.ex.feedback = {
          type: "hint",
          title: "Bilan de ta 1re relecture",
          html: statusMsg
        };
      } else {
        // Après la 2e tentative ou plus : afficher la correction expliquée
        const details = state.ex.errors.map((e) => `<li><strong>${escapeHtml(e.displayWrong)} → ${escapeHtml(e.expected)}</strong> (${escapeHtml(e.category)}) : ${escapeHtml(e.hint)}</li>`).join("");
        state.ex.feedback = {
          type: "err",
          title: "Correction expliquée",
          html: `Tu as trouvé ${foundCount} sur ${total}. Voici les corrections attendues :<ul style="margin:6px 0 0 18px;">${details}</ul>`
        };
        recordResult(false, state.ex.errors[0]?.category || "Relecture");
      }
      renderExercise();
    }

    // NIVEAU 5 : Dictée audio par segments + relecture guidée en 4 étapes
    const REVIEW_STEPS = [
      "1. Je vérifie les majuscules et la ponctuation.",
      "2. Je vérifie les mots appris.",
      "3. Je vérifie les accords dans les groupes nominaux.",
      "4. Je vérifie les verbes et leur sujet."
    ];

    function renderLevel5() {
      const stepIdx = state.ex.reviewStep - 1;
      return `
        <p><strong>Consigne :</strong> Écoute la phrase segment par segment, écris-la, puis fais la relecture guidée en 4 étapes avant de valider.</p>
        ${renderAudioBar(state.ex.targetSentence, true)}
        <div class="field">
          <label for="dictationDraft5">Écris la phrase dictée</label>
          <input id="dictationDraft5" type="text" value="${escapeAttr(state.ex.draft)}" oninput="state.ex.draft = this.value" placeholder="Écris ici..." />
          ${renderAccentButtons("dictationDraft5")}
        </div>

        <div style="margin-top:16px;">
          <strong>Relecture guidée (4 étapes) :</strong>
          <div class="step-tabs">
            ${REVIEW_STEPS.map((label, i) => `
              <button type="button" class="step-tab ${state.ex.reviewStep === i + 1 ? "btn-active" : ""} ${state.ex.checkedSteps[i] ? "done" : ""}" onclick="setReviewStep5(${i + 1})">
                ${escapeHtml(label)}
              </button>
            `).join("")}
          </div>
          <div class="correction-editor">
            <div>${escapeHtml(REVIEW_STEPS[stepIdx])}</div>
            <div class="action-row" style="margin-top:10px;">
              <button type="button" class="btn-soft" onclick="markReviewStepDone5(${stepIdx})">J'ai vérifié cette étape</button>
            </div>
          </div>
        </div>

        <div class="action-row">
          <button type="button" class="btn-primary" onclick="checkLevel5()">Valider ma dictée</button>
        </div>
      `;
    }

    function setReviewStep5(s) {
      const inp = document.getElementById("dictationDraft5");
      if (inp) state.ex.draft = inp.value;
      state.ex.reviewStep = s;
      renderExercise();
    }

    function markReviewStepDone5(idx) {
      const inp = document.getElementById("dictationDraft5");
      if (inp) state.ex.draft = inp.value;
      state.ex.checkedSteps[idx] = true;
      if (idx + 1 < 4) state.ex.reviewStep = idx + 2;
      renderExercise();
    }

    function checkLevel5() {
      const inp = document.getElementById("dictationDraft5");
      if (inp) state.ex.draft = inp.value;
      const userNorm = state.ex.draft.trim().replace(/\s+/g, " ");
      const refNorm = state.ex.targetSentence.trim().replace(/\s+/g, " ");
      state.ex.validated = true;

      const userWords = userNorm.split(/\s+/).filter(Boolean);
      const refWords = refNorm.split(/\s+/).filter(Boolean);
      const diffs = [];
      const maxLen = Math.max(userWords.length, refWords.length);
      for (let i = 0; i < maxLen; i++) {
        if (userWords[i] !== refWords[i]) {
          diffs.push(`Mot ${i + 1} : tu as écrit « ${escapeHtml(userWords[i] || "—")} » au lieu de « ${escapeHtml(refWords[i] || "—")} ».`);
        }
      }

      if (userNorm === refNorm) {
        state.ex.feedback = { type: "ok", title: ENCOURAGEMENTS[0], html: `Ta dictée correspond exactement à la phrase de référence : <strong>${escapeHtml(refNorm)}</strong>.` };
        recordResult(true, null);
      } else {
        state.ex.feedback = {
          type: "err",
          title: "Comparaison avec la dictée de référence",
          html: `<div><strong>Référence :</strong> ${escapeHtml(refNorm)}</div><ul style="margin:6px 0 0 18px;">${diffs.map((d) => `<li>${d}</li>`).join("")}</ul>`
        };
        recordResult(false, "Dictée — comparaison avec référence");
      }
      renderExercise();
    }

    // NIVEAU 6 : Transformation d'une phrase juste (une transformation à la fois)
    function renderLevel6() {
      const it = state.ex.item;
      return `
        <p><strong>Phrase de référence :</strong> ${escapeHtml(it.sourceSentence)}</p>
        <p><strong>Transformation demandée :</strong> ${escapeHtml(it.instruction)}</p>
        <div class="field">
          <label for="transformInput6">Écris la nouvelle phrase transformée</label>
          <input id="transformInput6" type="text" value="${escapeAttr(state.ex.answer)}" oninput="state.ex.answer = this.value" placeholder="Écris la phrase transformée..." />
          ${renderAccentButtons("transformInput6")}
        </div>
        <div class="action-row">
          <button type="button" class="btn-primary" onclick="checkLevel6()">Vérifier la transformation</button>
        </div>
      `;
    }

    function checkLevel6() {
      const inp = document.getElementById("transformInput6");
      if (inp) state.ex.answer = inp.value;
      state.ex.attempts += 1;
      const userClean = state.ex.answer.trim().replace(/\s+/g, " ").toLowerCase();
      const expClean = state.ex.item.expectedSentence.trim().replace(/\s+/g, " ").toLowerCase();

      if (userClean === expClean) {
        state.ex.solved = true;
        state.ex.feedback = {
          type: "ok",
          title: ENCOURAGEMENTS[0],
          html: `Bravo ! Phrase attendue : <strong>${escapeHtml(state.ex.item.expectedSentence)}</strong>.<br>${escapeHtml(state.ex.item.explanation)}`
        };
        recordResult(true, null);
      } else {
        state.ex.feedback = {
          type: "err",
          title: GENTLE_PROMPTS[state.ex.attempts % GENTLE_PROMPTS.length],
          html: `Phrase attendue : <strong>${escapeHtml(state.ex.item.expectedSentence)}</strong>.<br>${escapeHtml(state.ex.item.explanation)}`
        };
        recordResult(false, "Transformation grammaticale");
      }
      renderExercise();
    }

    function renderAccentButtons(targetInputId) {
      const chars = ["é", "è", "ê", "à", "ç", "ù", "ô", "î"];
      return `
        <div class="accent-bar">
          ${chars.map((ch) => `<button type="button" class="accent-btn" onclick="insertAccent('${targetInputId}', '${ch}')">${ch}</button>`).join("")}
        </div>
      `;
    }

    function insertAccent(inputId, ch) {
      const inp = document.getElementById(inputId);
      if (!inp) return;
      const start = inp.selectionStart ?? inp.value.length;
      const end = inp.selectionEnd ?? inp.value.length;
      inp.value = inp.value.slice(0, start) + ch + inp.value.slice(end);
      inp.dispatchEvent(new Event("input"));
      inp.focus();
      inp.setSelectionRange(start + ch.length, start + ch.length);
    }

    // ESPACE ENSEIGNANT
    function openTeacherGate() {
      stopSpeech();
      document.getElementById("teacherLoginMsg").innerHTML = "";
      showView("viewTeacherLogin");
    }

    function verifyTeacherCode() {
      const code = document.getElementById("teacherCodeInput").value.trim();
      if (code === state.appData.teacherCode) {
        showView("viewTeacher");
        renderTeacherSpace();
      } else {
        document.getElementById("teacherLoginMsg").innerHTML = `<div class="feedback err">Code incorrect.</div>`;
      }
    }

    // Génération automatique respectant la dictée originale (sans modifier les mots de la dictée)
    function generateLevel3FromText(text) {
      const sentences = splitSentences(text);
      const out = [];
      sentences.slice(0, 3).forEach((s, idx) => {
        const words = s.split(/\s+/);
        const errs = [];
        const candIdx = words.findIndex((w) => /^(chantent|brillent|mangent|jouent|marchent|partent|rangent|aiment)$/i.test(w.replace(/[.!?]/g, "")));
        if (candIdx >= 0) {
          const raw = words[candIdx];
          const punct = raw.match(/[.!?]$/)?.[0] || "";
          const base = raw.replace(/[.!?]$/, "");
          const sing = base.replace(/ent$/i, "e");
          errs.push({
            displayWrong: sing,
            expected: base,
            category: "accord sujet-verbe",
            hint1: "Observe bien le sujet du verbe.",
            hint2: `Au pluriel avec -ent, on écrit « ${base} ».`,
            explanation: `Le verbe s'accorde avec son sujet : « ${base} »${punct ? " (" + punct + ")" : ""}.`
          });
        }
        if (idx > 0 && errs.length < 2) {
          const pluralCand = words.find((w) => /[a-zàâäéèêëîïôöùûüç]{3,}s[.!?]?$/i.test(w));
          if (pluralCand) {
            const cleanPlural = pluralCand.replace(/[.!?]$/, "");
            const singNoun = cleanPlural.replace(/s$/i, "");
            errs.push({
              displayWrong: singNoun,
              expected: cleanPlural,
              category: "accord dans le groupe nominal",
              hint1: "Regarde le déterminant devant le nom.",
              hint2: "Ajoute la marque du pluriel à la fin du nom.",
              explanation: `Le groupe nominal est au pluriel : on écrit « ${cleanPlural} ».`
            });
          }
        }
        if (!errs.length) {
          const firstWord = words[0]?.replace(/[^a-zA-ZÀ-ÿ]/g, "") || "mot";
          errs.push({
            displayWrong: firstWord.toLowerCase(),
            expected: firstWord,
            category: "majuscule / orthographe",
            hint1: "Vérifie la majuscule en début de phrase.",
            hint2: "Le premier mot d'une phrase prend une majuscule.",
            explanation: `En début de phrase, on met une majuscule : « ${firstWord} ».`
          });
        }
        out.push({ sentence: s, errors: errs.slice(0, idx === 0 ? 1 : 2) });
      });
      return out;
    }

    function generateLevel4FromText(text) {
      const sentences = splitSentences(text);
      const sample = sentences.slice(0, 2).join(" ");
      const words = sample.split(/\s+/);
      const errs = [];
      words.forEach((w) => {
        const clean = w.replace(/[,.;:!?]/g, "");
        if (/^(chantent|brillent|mangent|jouent|marchent|partent|rangent|aiment)$/i.test(clean) && errs.length < 2) {
          errs.push({
            displayWrong: clean.replace(/ent$/i, "e"),
            expected: clean,
            category: "accord sujet-verbe",
            hint: "Vérifie l'accord du verbe avec son sujet."
          });
        } else if (/[a-zàâäéèêëîïôöùûüç]{4,}s$/i.test(clean) && errs.length < 2) {
          errs.push({
            displayWrong: clean.replace(/s$/i, ""),
            expected: clean,
            category: "accord dans le groupe nominal",
            hint: "Regarde s'il y a plusieurs éléments dans le groupe nominal."
          });
        }
      });
      if (!errs.length && words.length) {
        const w0 = words[0].replace(/[,.;:!?]/g, "");
        errs.push({
          displayWrong: w0.toLowerCase(),
          expected: w0,
          category: "majuscule",
          hint: "Vérifie la majuscule initiale."
        });
      }
      return [{ text: sample, errors: errs.slice(0, 2) }];
    }

    function generateLevel6FromText(text) {
      const sentences = splitSentences(text);
      return sentences.slice(0, 2).map((s) => ({
        sourceSentence: s,
        instruction: "Réécris cette phrase en vérifiant l'orthographe et la ponctuation.",
        expectedSentence: s,
        explanation: "Phrase de référence conservée à l'identique."
      }));
    }

    function renderTeacherSpace() {
      const dic = getCurrentDictation();
      const enabled = dic.enabledLevels || [1, 2, 3, 4, 5, 6];
      const results = state.appData.results;

      // Agrégation suivi élèves
      const errorCounts = {};
      results.filter((r) => !r.success && r.errorTopic).forEach((r) => {
        errorCounts[r.errorTopic] = (errorCounts[r.errorTopic] || 0) + 1;
      });
      const topErrors = Object.entries(errorCounts).sort((a, b) => b[1] - a[1]);

      const studentMap = {};
      results.forEach((r) => {
        if (!studentMap[r.student]) {
          studentMap[r.student] = { name: r.student, total: 0, ok: 0, levels: new Set() };
        }
        studentMap[r.student].total += 1;
        if (r.success) studentMap[r.student].ok += 1;
        studentMap[r.student].levels.add(r.level);
      });

      document.getElementById("viewTeacher").innerHTML = `
        <h2>Espace enseignant</h2>

        <div class="field">
          <label for="teacherDictSelect">Dictée enregistrée à modifier</label>
          <select id="teacherDictSelect" onchange="switchTeacherDict(this.value)">
            ${state.appData.dictations.map((d) => `<option value="${escapeAttr(d.id)}" ${d.id === dic.id ? "selected" : ""}>${escapeHtml(d.title)}</option>`).join("")}
          </select>
        </div>

        <div class="field">
          <label for="tTitle">Titre de la dictée</label>
          <input id="tTitle" type="text" value="${escapeAttr(dic.title)}" />
        </div>

        <div class="field">
          <label for="tText">Texte de la dictée originale (conservé exactement)</label>
          <textarea id="tText">${escapeHtml(dic.text)}</textarea>
        </div>

        <div class="field">
          <label>Niveaux accessibles aux élèves</label>
          <div style="display:flex;flex-wrap:wrap;gap:12px;">
            ${LEVEL_META.map((l) => `
              <label style="display:inline-flex;align-items:center;gap:6px;font-weight:600;cursor:pointer;">
                <input type="checkbox" class="t-lvl-chk" value="${l.id}" ${enabled.includes(l.id) ? "checked" : ""} />
                Niveau ${l.id}
              </label>
            `).join("")}
          </div>
        </div>

        <div class="field">
          <label for="tLvl6Instruction">Consigne personnalisée du Niveau 6 (1re phrase)</label>
          <input id="tLvl6Instruction" type="text" value="${escapeAttr(dic.level6Items?.[0]?.instruction || "")}" />
        </div>

        <div class="action-row">
          <button type="button" class="btn-soft" onclick="autoGenerateCurrentDictation()">Générer automatiquement les niveaux</button>
          <button type="button" class="btn-primary" onclick="saveCurrentDictation()">Enregistrer la dictée</button>
          <button type="button" onclick="createNewDictation()">+ Nouvelle dictée</button>
        </div>

        <hr style="margin:28px 0;border:0;border-top:1px solid var(--border);" />

        <h3>Suivi des élèves (identifiants / pseudonymes uniquement)</h3>
        <p style="color:var(--muted);font-size:15px;">Difficultés les plus fréquentes : ${topErrors.length ? topErrors.map(([k, v]) => `<strong>${escapeHtml(k)}</strong> (${v})`).join(" · ") : "Aucune erreur enregistrée pour le moment."}</p>

        <table>
          <thead>
            <tr>
              <th>Élève</th>
              <th>Exercices réalisés</th>
              <th>Niveaux travaillés</th>
              <th>Taux de réussite</th>
            </tr>
          </thead>
          <tbody>
            ${Object.values(studentMap).length ? Object.values(studentMap).map((st) => {
              const rate = st.total ? Math.round((st.ok / st.total) * 100) : 0;
              return `
                <tr>
                  <td><strong>${escapeHtml(st.name)}</strong></td>
                  <td>${st.total}</td>
                  <td>Niveaux ${Array.from(st.levels).sort().join(", ")}</td>
                  <td>${rate}% (${st.ok}/${st.total})</td>
                </tr>
              `;
            }).join("") : `<tr><td colspan="4" style="color:var(--muted);">Aucun résultat enregistré pour l'instant.</td></tr>`}
          </tbody>
        </table>
      `;
    }

    function switchTeacherDict(id) {
      state.currentDictationId = id;
      renderTeacherSpace();
    }

    function collectTeacherForm() {
      const title = document.getElementById("tTitle").value.trim() || "Dictée sans titre";
      const text = document.getElementById("tText").value.trim();
      const enabledLevels = Array.from(document.querySelectorAll(".t-lvl-chk:checked")).map((el) => Number(el.value));
      const lvl6Inst = document.getElementById("tLvl6Instruction").value.trim();
      return { title, text, enabledLevels: enabledLevels.length ? enabledLevels : [1], lvl6Inst };
    }

    function autoGenerateCurrentDictation() {
      const dic = getCurrentDictation();
      const form = collectTeacherForm();
      dic.title = form.title;
      dic.text = form.text || dic.text;
      dic.enabledLevels = form.enabledLevels;
      dic.level3Items = generateLevel3FromText(dic.text);
      dic.level4Items = generateLevel4FromText(dic.text);
      dic.level6Items = generateLevel6FromText(dic.text);
      if (form.lvl6Inst && dic.level6Items[0]) {
        dic.level6Items[0].instruction = form.lvl6Inst;
      }
      writeStore(state.appData);
      renderTeacherSpace();
      alert("Exercices générés à partir de la dictée originale.");
    }

    function saveCurrentDictation() {
      const dic = getCurrentDictation();
      const form = collectTeacherForm();
      dic.title = form.title;
      if (form.text) dic.text = form.text;
      dic.enabledLevels = form.enabledLevels;
      if (!dic.level3Items || !dic.level3Items.length) dic.level3Items = generateLevel3FromText(dic.text);
      if (!dic.level4Items || !dic.level4Items.length) dic.level4Items = generateLevel4FromText(dic.text);
      if (!dic.level6Items || !dic.level6Items.length) dic.level6Items = generateLevel6FromText(dic.text);
      if (form.lvl6Inst && dic.level6Items[0]) {
        dic.level6Items[0].instruction = form.lvl6Inst;
      }
      writeStore(state.appData);
      alert("Dictée enregistrée.");
    }

    function createNewDictation() {
      const id = "dic_" + Date.now();
      const baseText = "Le chat dort sur le tapis. Les élèves écoutent attentivement.";
      const newDic = {
        id,
        title: "Nouvelle dictée CM1",
        text: baseText,
        enabledLevels: [1, 2, 3, 4, 5, 6],
        level3Items: generateLevel3FromText(baseText),
        level4Items: generateLevel4FromText(baseText),
        level6Items: generateLevel6FromText(baseText)
      };
      state.appData.dictations.push(newDic);
      state.currentDictationId = id;
      writeStore(state.appData);
      renderTeacherSpace();
    }

    function escapeHtml(str) {
      return String(str ?? "")
        .replace(/&/g, "&amp;")
        .replace(/</g, "&lt;")
        .replace(/>/g, "&gt;")
        .replace(/"/g, "&quot;");
    }

    function escapeAttr(str) {
      return escapeHtml(str).replace(/'/g, "&#39;");
    }

    // Initialisation
    renderHome();
  </script>
</body>
</html>
