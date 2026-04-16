# lilysecor21.github.io
Innovation Project
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>slow hour</title>
    <meta
      name="description"
      content="A beautiful screen-time reminder app with mini games, supportive break prompts, and anti-comparison affirmations."
    />
    <meta name="theme-color" content="#f4e4df" />
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link
      href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@500;600;700&family=DM+Sans:wght@400;500;700&display=swap"
      rel="stylesheet"
    />
    <style>
      :root {
        --bg: #fdf6f2;
        --bg-deep: #f4e4df;
        --surface: rgba(255, 251, 249, 0.8);
        --surface-strong: rgba(255, 248, 244, 0.96);
        --line: rgba(122, 90, 88, 0.16);
        --text: #3e2c34;
        --muted: #7d646b;
        --accent: #e98a7b;
        --accent-strong: #d95f77;
        --shadow: 0 24px 80px rgba(126, 78, 85, 0.14);
      }

      * {
        box-sizing: border-box;
      }

      html {
        min-height: 100%;
      }

      body {
        margin: 0;
        min-height: 100vh;
        font-family: "DM Sans", sans-serif;
        color: var(--text);
        background:
          radial-gradient(circle at top left, rgba(255, 214, 204, 0.9), transparent 28%),
          radial-gradient(circle at bottom right, rgba(231, 189, 166, 0.85), transparent 30%),
          linear-gradient(160deg, var(--bg), var(--bg-deep));
      }

      button,
      select,
      textarea {
        font: inherit;
      }

      .page-shell {
        position: relative;
        overflow: hidden;
        min-height: 100vh;
      }

      .ambient {
        position: absolute;
        border-radius: 999px;
        filter: blur(10px);
        opacity: 0.55;
      }

      .ambient-left {
        top: -5rem;
        left: -7rem;
        width: 22rem;
        height: 22rem;
        background: rgba(248, 205, 167, 0.45);
      }

      .ambient-right {
        right: -6rem;
        bottom: 8rem;
        width: 18rem;
        height: 18rem;
        background: rgba(221, 157, 176, 0.35);
      }

      .app {
        position: relative;
        z-index: 1;
        max-width: 1200px;
        margin: 0 auto;
        padding: 32px 20px 56px;
      }

      .panel {
        background: var(--surface);
        border: 1px solid var(--line);
        border-radius: 28px;
        backdrop-filter: blur(18px);
        box-shadow: var(--shadow);
      }

      .hero {
        padding: 32px;
        position: relative;
      }

      .eyebrow,
      .label,
      .stat-label,
      .prompt-title,
      .save-note {
        text-transform: uppercase;
        letter-spacing: 0.12em;
        font-size: 0.72rem;
        color: var(--muted);
      }

      .hero h1,
      .section-heading h2,
      .right-column h2 {
        margin: 10px 0 0;
        font-family: "Cormorant Garamond", serif;
        font-weight: 600;
        line-height: 0.98;
      }

      .hero h1 {
        max-width: 9ch;
        font-size: clamp(3.5rem, 7vw, 6.2rem);
      }

      .hero-copy {
        max-width: 560px;
        margin: 18px 0 28px;
        color: var(--muted);
        font-size: 1.05rem;
        line-height: 1.7;
      }

      .hero-grid,
      .prompt-grid,
      .dashboard {
        display: grid;
        gap: 18px;
      }

      .hero-grid {
        grid-template-columns: repeat(4, minmax(0, 1fr));
      }

      .stat-card,
      .prompt-card {
        background: var(--surface-strong);
        border: 1px solid rgba(122, 90, 88, 0.1);
        border-radius: 22px;
        padding: 18px;
      }

      .stat-card strong {
        display: block;
        margin: 10px 0 6px;
        font-size: 1.35rem;
      }

      .install-card {
        display: flex;
        flex-direction: column;
        align-items: start;
        gap: 10px;
      }

      .stat-note,
      .truth-list,
      .prompt-card p:last-child,
      .stacked,
      .message-card,
      textarea,
      small {
        color: var(--muted);
      }

      .dashboard {
        margin-top: 20px;
        grid-template-columns: 1.2fr 0.8fr;
        align-items: start;
      }

      .left-column,
      .right-column {
        display: grid;
        gap: 18px;
      }

      .timer-panel,
      .reminder-panel,
      .right-column .panel,
      .reflection-panel,
      .games-panel {
        padding: 24px;
      }

      .section-heading {
        display: flex;
        gap: 16px;
        justify-content: space-between;
        align-items: start;
        margin-bottom: 22px;
      }

      .pill-button,
      .secondary-button,
      .text-button,
      .ritual-chip,
      .game-tab,
      .tic-cell,
      .match-card {
        border: 0;
        cursor: pointer;
        transition: transform 180ms ease, box-shadow 180ms ease, background 180ms ease;
      }

      .pill-button,
      .secondary-button {
        border-radius: 999px;
        padding: 12px 16px;
      }

      .pill-button {
        background: rgba(233, 138, 123, 0.16);
        color: var(--accent-strong);
      }

      .pill-button.active {
        background: linear-gradient(135deg, rgba(233, 138, 123, 0.95), rgba(217, 95, 119, 0.95));
        color: white;
        box-shadow: 0 18px 35px rgba(217, 95, 119, 0.18);
      }

      .secondary-button {
        background: #fff7f5;
        color: var(--text);
        border: 1px solid rgba(122, 90, 88, 0.12);
      }

      .text-button {
        background: transparent;
        color: var(--accent-strong);
        padding: 8px 0;
      }

      .game-tabs {
        display: flex;
        gap: 10px;
        margin-bottom: 16px;
        flex-wrap: wrap;
      }

      .game-tab {
        padding: 11px 16px;
        border-radius: 999px;
        background: rgba(255, 255, 255, 0.72);
        color: var(--text);
        border: 1px solid rgba(122, 90, 88, 0.1);
      }

      .game-tab.active {
        background: rgba(233, 138, 123, 0.18);
        color: var(--accent-strong);
        box-shadow: 0 14px 28px rgba(217, 95, 119, 0.12);
      }

      .game-panels {
        display: grid;
      }

      .game-card {
        display: none;
        background: var(--surface-strong);
        border: 1px solid rgba(122, 90, 88, 0.1);
        border-radius: 22px;
        padding: 18px;
      }

      .game-card.active {
        display: block;
      }

      .game-heading {
        display: flex;
        justify-content: space-between;
        gap: 16px;
        align-items: start;
        margin-bottom: 16px;
      }

      .game-heading p:last-child {
        margin: 6px 0 0;
        color: var(--muted);
      }

      .tic-grid {
        display: grid;
        grid-template-columns: repeat(3, minmax(0, 1fr));
        gap: 10px;
      }

      .tic-cell {
        min-height: 88px;
        border-radius: 18px;
        background: rgba(255, 255, 255, 0.8);
        border: 1px solid rgba(122, 90, 88, 0.12);
        font-family: "Cormorant Garamond", serif;
        font-size: 2.4rem;
        color: var(--accent-strong);
      }

      .match-grid {
        display: grid;
        grid-template-columns: repeat(4, minmax(0, 1fr));
        gap: 10px;
      }

      .match-card {
        min-height: 78px;
        border-radius: 18px;
        background: linear-gradient(145deg, rgba(255, 244, 240, 0.98), rgba(245, 228, 223, 0.98));
        border: 1px solid rgba(122, 90, 88, 0.1);
        font-size: 1.8rem;
        color: transparent;
      }

      .match-card.revealed,
      .match-card.matched {
        color: var(--accent-strong);
        background: rgba(255, 255, 255, 0.86);
      }

      .match-card.matched {
        box-shadow: 0 14px 28px rgba(217, 95, 119, 0.12);
      }

      .timer-display {
        display: grid;
        grid-template-columns: 280px 1fr;
        gap: 28px;
        align-items: center;
      }

      .timer-ring {
        position: relative;
        width: 240px;
        height: 240px;
        margin: 0 auto;
      }

      .timer-ring svg {
        width: 100%;
        height: 100%;
        transform: rotate(-90deg);
      }

      .ring-track,
      .ring-progress {
        fill: none;
        stroke-width: 8;
      }

      .ring-track {
        stroke: rgba(122, 90, 88, 0.12);
      }

      .ring-progress {
        stroke: var(--accent-strong);
        stroke-linecap: round;
        stroke-dasharray: 326.73;
        stroke-dashoffset: 81.68;
      }

      .timer-copy {
        position: absolute;
        inset: 0;
        display: grid;
        place-content: center;
        text-align: center;
      }

      .timer-copy span {
        font-family: "Cormorant Garamond", serif;
        font-size: 3.4rem;
        color: var(--text);
      }

      .timer-controls {
        display: grid;
        gap: 14px;
      }

      .stacked {
        display: grid;
        gap: 8px;
        font-size: 0.95rem;
      }

      select,
      textarea {
        width: 100%;
        border: 1px solid rgba(122, 90, 88, 0.15);
        border-radius: 18px;
        background: rgba(255, 255, 255, 0.66);
        padding: 14px 16px;
        outline: none;
      }

      select:focus,
      textarea:focus {
        border-color: rgba(217, 95, 119, 0.55);
        box-shadow: 0 0 0 4px rgba(217, 95, 119, 0.12);
      }

      .message-card {
        margin: 0;
        background: linear-gradient(145deg, rgba(255, 249, 246, 0.96), rgba(250, 237, 231, 0.95));
        border-radius: 24px;
        padding: 24px;
        font-family: "Cormorant Garamond", serif;
        font-size: clamp(2rem, 4vw, 2.9rem);
        line-height: 1.06;
        color: var(--text);
      }

      .prompt-grid {
        margin-top: 16px;
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }

      .ritual-list {
        display: flex;
        flex-wrap: wrap;
        gap: 10px;
        margin-top: 18px;
      }

      .ritual-chip {
        padding: 12px 16px;
        border-radius: 999px;
        background: rgba(255, 255, 255, 0.68);
        border: 1px solid rgba(122, 90, 88, 0.1);
        color: var(--text);
      }

      .ritual-chip.selected,
      .game-tab:hover,
      .ritual-chip:hover,
      .tic-cell:hover,
      .match-card:hover,
      .pill-button:hover,
      .secondary-button:hover,
      .text-button:hover {
        transform: translateY(-1px);
      }

      .ritual-chip.selected {
        background: rgba(233, 138, 123, 0.18);
        color: var(--accent-strong);
        box-shadow: 0 14px 28px rgba(217, 95, 119, 0.12);
      }

      .truth-list {
        margin: 18px 0 0;
        padding-left: 18px;
        display: grid;
        gap: 10px;
        line-height: 1.65;
      }

      .save-note {
        margin: 10px 0 0;
      }

      .toast {
        position: fixed;
        left: 50%;
        bottom: 24px;
        transform: translateX(-50%) translateY(120%);
        background: rgba(62, 44, 52, 0.92);
        color: #fffaf7;
        padding: 14px 18px;
        border-radius: 999px;
        box-shadow: 0 18px 40px rgba(62, 44, 52, 0.28);
        transition: transform 220ms ease;
        z-index: 10;
      }

      .toast.show {
        transform: translateX(-50%) translateY(0);
      }

      @media (max-width: 980px) {
        .hero-grid {
          grid-template-columns: repeat(2, minmax(0, 1fr));
        }

        .dashboard {
          grid-template-columns: 1fr;
        }

        .timer-display {
          grid-template-columns: 1fr;
        }

        .timer-ring {
          width: 220px;
          height: 220px;
        }
      }

      @media (max-width: 720px) {
        .app {
          padding: 18px 14px 40px;
        }

        .hero,
        .timer-panel,
        .reminder-panel,
        .right-column .panel,
        .reflection-panel,
        .games-panel {
          padding: 20px;
        }

        .hero-grid,
        .prompt-grid {
          grid-template-columns: 1fr;
        }

        .section-heading,
        .game-heading {
          flex-direction: column;
        }

        .hero h1 {
          max-width: 10ch;
        }

        .match-grid {
          grid-template-columns: repeat(3, minmax(0, 1fr));
        }
      }

      @media (prefers-reduced-motion: no-preference) {
        .panel,
        .hero .stat-card,
        .message-card,
        .prompt-card {
          animation: rise 700ms ease both;
        }

        .hero .stat-card:nth-child(2) {
          animation-delay: 120ms;
        }

        .prompt-card:nth-child(2) {
          animation-delay: 120ms;
        }
      }

      @keyframes rise {
        from {
          opacity: 0;
          transform: translateY(18px);
        }

        to {
          opacity: 1;
          transform: translateY(0);
        }
      }
    </style>
  </head>
  <body>
    <div class="page-shell">
      <div class="ambient ambient-left"></div>
      <div class="ambient ambient-right"></div>

      <main class="app">
        <section class="hero panel">
          <div class="eyebrow">slow hour</div>
          <h1>You do not have to rush to be enough.</h1>
          <p class="hero-copy">
            A gentle break app for teen girls who need a softer place to land,
            a reset from comparison, and something lovely to do besides scroll.
          </p>

          <div class="hero-grid">
            <article class="stat-card">
              <span class="stat-label">Next reminder</span>
              <strong id="next-reminder">In 20 minutes</strong>
              <span class="stat-note">Customizable, calm, and never shaming.</span>
            </article>
            <article class="stat-card">
              <span class="stat-label">Opened today</span>
              <strong id="open-count">1 time</strong>
              <span class="stat-note">A little awareness, not guilt.</span>
            </article>
            <article class="stat-card">
              <span class="stat-label">Break ritual</span>
              <strong id="ritual-name">Breathe + reset</strong>
              <span class="stat-note">Tiny resets still change the day.</span>
            </article>
            <article class="stat-card install-card">
              <span class="stat-label">Install app</span>
              <strong>Single-file mode</strong>
              <button id="install-app" class="secondary-button" type="button">
                Open in browser
              </button>
            </article>
          </div>
        </section>

        <section class="dashboard">
          <div class="left-column">
            <section class="panel timer-panel">
              <div class="section-heading">
                <div>
                  <p class="label">Reminder timer</p>
                  <h2>Set the pace for your reset</h2>
                </div>
                <button id="toggle-reminders" class="pill-button active" type="button">
                  Reminders on
                </button>
              </div>

              <div class="timer-display">
                <div class="timer-ring">
                  <svg viewBox="0 0 120 120" aria-hidden="true">
                    <circle cx="60" cy="60" r="52" class="ring-track"></circle>
                    <circle
                      cx="60"
                      cy="60"
                      r="52"
                      class="ring-progress"
                      id="ring-progress"
                    ></circle>
                  </svg>
                  <div class="timer-copy">
                    <span id="minutes-left">20:00</span>
                    <small>until your next check-in</small>
                  </div>
                </div>

                <div class="timer-controls">
                  <label class="stacked" for="interval">
                    Reminder every
                    <select id="interval">
                      <option value="10">10 minutes</option>
                      <option value="20" selected>20 minutes</option>
                      <option value="30">30 minutes</option>
                      <option value="45">45 minutes</option>
                      <option value="60">60 minutes</option>
                    </select>
                  </label>

                  <label class="stacked" for="message-tone">
                    Reminder style
                    <select id="message-tone">
                      <option value="gentle" selected>Gentle</option>
                      <option value="grounding">Grounding</option>
                      <option value="confident">Confident</option>
                    </select>
                  </label>

                  <button id="reset-timer" class="secondary-button" type="button">
                    Reset timer
                  </button>
                </div>
              </div>
            </section>

            <section class="panel reminder-panel">
              <div class="section-heading">
                <div>
                  <p class="label">Current reminder</p>
                  <h2>What your mind might need right now</h2>
                </div>
                <button id="new-message" class="text-button" type="button">
                  New note
                </button>
              </div>

              <blockquote id="message-card" class="message-card">
                You are allowed to grow at your own gorgeous pace.
              </blockquote>

              <div class="prompt-grid">
                <article class="prompt-card">
                  <p class="prompt-title">Comparison reset</p>
                  <p id="comparison-reset">
                    Ask: do I actually want this, or do I just want to feel chosen?
                  </p>
                </article>
                <article class="prompt-card">
                  <p class="prompt-title">Micro-break idea</p>
                  <p id="break-idea">Put your phone down and relax your jaw and shoulders.</p>
                </article>
              </div>
            </section>

            <section class="panel games-panel">
              <div class="section-heading">
                <div>
                  <p class="label">Mini games</p>
                  <h2>Give your brain somewhere else to go</h2>
                </div>
              </div>

              <div class="game-tabs" id="game-tabs">
                <button class="game-tab active" data-game="tictactoe" type="button">
                  Tic-tac-toe
                </button>
                <button class="game-tab" data-game="match" type="button">
                  Match pairs
                </button>
              </div>

              <div class="game-panels">
                <section class="game-card active" id="game-tictactoe">
                  <div class="game-heading">
                    <div>
                      <p class="prompt-title">Tic-tac-toe</p>
                      <p id="ttt-status">You go first. Pick a square and take up space.</p>
                    </div>
                    <button id="ttt-reset" class="secondary-button" type="button">
                      Restart
                    </button>
                  </div>
                  <div class="tic-grid" id="tic-grid" aria-label="Tic tac toe board"></div>
                </section>

                <section class="game-card" id="game-match">
                  <div class="game-heading">
                    <div>
                      <p class="prompt-title">Match pairs</p>
                      <p id="match-status">Match all the icons. Slow is still winning.</p>
                    </div>
                    <button id="match-reset" class="secondary-button" type="button">
                      Shuffle
                    </button>
                  </div>
                  <div class="match-grid" id="match-grid" aria-label="Match pairs board"></div>
                </section>
              </div>
            </section>
          </div>

          <div class="right-column">
            <section class="panel">
              <p class="label">Quiet mode</p>
              <h2>Make your breaks sweeter</h2>
              <div class="ritual-list" id="ritual-list">
                <button class="ritual-chip selected" data-ritual="Breathe + reset" type="button">
                  Breathe + reset
                </button>
                <button class="ritual-chip" data-ritual="Water + face splash" type="button">
                  Water + face splash
                </button>
                <button class="ritual-chip" data-ritual="Music + stretch minute" type="button">
                  Music + stretch minute
                </button>
                <button class="ritual-chip" data-ritual="Write one true sentence" type="button">
                  Write one true sentence
                </button>
              </div>
            </section>

            <section class="panel reflection-panel">
              <p class="label">Reality check</p>
              <h2>Things feeds never show</h2>
              <ul class="truth-list">
                <li>Pretty is not proof that someone feels peaceful.</li>
                <li>Beauty trends change faster than your actual worth.</li>
                <li>Your real life gets better when you come back to it.</li>
              </ul>
            </section>

            <section class="panel">
              <p class="label">Daily note</p>
              <h2>Your offline life matters</h2>
              <label class="stacked" for="offline-plan">
                One thing you’ll do away from the screen
                <textarea
                  id="offline-plan"
                  rows="5"
                  placeholder="Take a shower, text a real friend, do my homework quietly, make tea, sketch, go outside..."
                ></textarea>
              </label>
              <p class="save-note" id="save-note">Saved on this device.</p>
            </section>
          </div>
        </section>
      </main>
    </div>

    <div id="toast" class="toast" role="status" aria-live="polite"></div>

    <script>
      const STORAGE_KEY = "slow-hour-single-file-settings";
      const CIRCLE_LENGTH = 326.73;

      const copyBank = {
        gentle: [
          "You are allowed to grow at your own gorgeous pace.",
          "Being gentle with yourself is still a kind of power.",
          "You do not need to keep auditioning for worthiness.",
          "Your real life is still the prettiest thing about you."
        ],
        grounding: [
          "What is real right now: your body, your room, your actual life.",
          "Comparison gets louder when you are tired. Try rest before self-criticism.",
          "Other girls shining does not make your light smaller.",
          "You can come back to yourself in one quiet minute."
        ],
        confident: [
          "Trends do not get to decide your value.",
          "Nobody on your feed is more worthy of softness than you are.",
          "You are not behind. You are allowed to be becoming.",
          "Your own energy is more magnetic than imitation."
        ]
      };

      const resetPrompts = [
        "Ask: do I actually want this, or do I just want to feel chosen?",
        "Notice the difference between inspiration and self-abandonment.",
        "Mute the urge to compare. Turn toward what you actually like.",
        "If this post vanished tomorrow, your worth would stay exactly the same."
      ];

      const breakIdeas = [
        "Put your phone down and unclench your jaw and shoulders.",
        "Stand by a window and let your eyes focus far away.",
        "Get water, wash your face, and reset your nervous system.",
        "Play one tiny game before deciding whether you even want to keep scrolling."
      ];

      const elements = {
        nextReminder: document.getElementById("next-reminder"),
        openCount: document.getElementById("open-count"),
        ritualName: document.getElementById("ritual-name"),
        installApp: document.getElementById("install-app"),
        toggleReminders: document.getElementById("toggle-reminders"),
        minutesLeft: document.getElementById("minutes-left"),
        interval: document.getElementById("interval"),
        tone: document.getElementById("message-tone"),
        resetTimer: document.getElementById("reset-timer"),
        messageCard: document.getElementById("message-card"),
        comparisonReset: document.getElementById("comparison-reset"),
        breakIdea: document.getElementById("break-idea"),
        newMessage: document.getElementById("new-message"),
        ringProgress: document.getElementById("ring-progress"),
        ritualList: document.getElementById("ritual-list"),
        offlinePlan: document.getElementById("offline-plan"),
        saveNote: document.getElementById("save-note"),
        toast: document.getElementById("toast"),
        gameTabs: document.getElementById("game-tabs"),
        ticGrid: document.getElementById("tic-grid"),
        tttStatus: document.getElementById("ttt-status"),
        tttReset: document.getElementById("ttt-reset"),
        matchGrid: document.getElementById("match-grid"),
        matchStatus: document.getElementById("match-status"),
        matchReset: document.getElementById("match-reset")
      };

      const defaultState = {
        intervalMinutes: 20,
        tone: "gentle",
        reminderEnabled: true,
        selectedRitual: "Breathe + reset",
        offlinePlan: "",
        deadline: Date.now() + 20 * 60 * 1000,
        lastOpenDate: "",
        dailyOpenCount: 0
      };

      const tttWinningLines = [
        [0, 1, 2],
        [3, 4, 5],
        [6, 7, 8],
        [0, 3, 6],
        [1, 4, 7],
        [2, 5, 8],
        [0, 4, 8],
        [2, 4, 6]
      ];

      const matchIcons = ["<3", ":)", "*", "!"];

      let state = loadState();
      let toastTimer;
      let activeGame = "tictactoe";
      let ticBoard = Array(9).fill("");
      let ticGameOver = false;
      let matchDeck = [];
      let revealedCards = [];
      let matchedIndices = new Set();
      let matchLock = false;

      trackDailyOpen();
      syncUI();
      bindEvents();
      startTicking();
      setupGames();

      function loadState() {
        try {
          const saved = JSON.parse(localStorage.getItem(STORAGE_KEY));
          if (!saved) {
            return { ...defaultState };
          }

          return {
            ...defaultState,
            ...saved,
            deadline:
              typeof saved.deadline === "number"
                ? saved.deadline
                : Date.now() + defaultState.intervalMinutes * 60 * 1000
          };
        } catch (error) {
          return { ...defaultState };
        }
      }

      function saveState() {
        localStorage.setItem(STORAGE_KEY, JSON.stringify(state));
      }

      function bindEvents() {
        elements.installApp.addEventListener("click", () => {
          showToast("This version is already a single downloadable HTML file.");
        });

        elements.toggleReminders.addEventListener("click", () => {
          state.reminderEnabled = !state.reminderEnabled;
          if (state.reminderEnabled) {
            state.deadline = Date.now() + state.intervalMinutes * 60 * 1000;
            showToast("Reminders are back on.");
          } else {
            showToast("Reminders paused for now.");
          }
          saveState();
          syncUI();
        });

        elements.interval.addEventListener("change", (event) => {
          state.intervalMinutes = Number(event.target.value);
          state.deadline = Date.now() + state.intervalMinutes * 60 * 1000;
          saveState();
          syncUI();
          showToast(`Break timer set to every ${state.intervalMinutes} minutes.`);
        });

        elements.tone.addEventListener("change", (event) => {
          state.tone = event.target.value;
          saveState();
          rotateMessage();
        });

        elements.resetTimer.addEventListener("click", () => {
          state.deadline = Date.now() + state.intervalMinutes * 60 * 1000;
          saveState();
          syncUI();
          showToast("Timer reset.");
        });

        elements.newMessage.addEventListener("click", () => {
          rotateMessage();
          showToast("A new note for you.");
        });

        elements.ritualList.addEventListener("click", (event) => {
          const button = event.target.closest(".ritual-chip");
          if (!button) {
            return;
          }
          state.selectedRitual = button.dataset.ritual;
          saveState();
          syncUI();
        });

        elements.offlinePlan.addEventListener("input", (event) => {
          state.offlinePlan = event.target.value;
          saveState();
          elements.saveNote.textContent = "Saved on this device.";
        });

        elements.gameTabs.addEventListener("click", (event) => {
          const button = event.target.closest(".game-tab");
          if (!button) {
            return;
          }
          activeGame = button.dataset.game;
          syncGameTabs();
        });

        elements.tttReset.addEventListener("click", resetTicTacToe);
        elements.matchReset.addEventListener("click", resetMatchGame);
      }

      function syncUI() {
        elements.interval.value = String(state.intervalMinutes);
        elements.tone.value = state.tone;
        elements.offlinePlan.value = state.offlinePlan;
        elements.openCount.textContent = `${state.dailyOpenCount} ${
          state.dailyOpenCount === 1 ? "time" : "times"
        }`;
        elements.ritualName.textContent = state.selectedRitual;
        elements.toggleReminders.textContent = state.reminderEnabled ? "Reminders on" : "Reminders off";
        elements.toggleReminders.classList.toggle("active", state.reminderEnabled);

        [...elements.ritualList.querySelectorAll(".ritual-chip")].forEach((chip) => {
          chip.classList.toggle("selected", chip.dataset.ritual === state.selectedRitual);
        });

        updateCountdown();
        if (!elements.messageCard.dataset.seeded) {
          rotateMessage();
          elements.messageCard.dataset.seeded = "true";
        }
      }

      function startTicking() {
        updateCountdown();
        window.setInterval(updateCountdown, 1000);
      }

      function updateCountdown() {
        if (!state.reminderEnabled) {
          elements.minutesLeft.textContent = "Paused";
          elements.nextReminder.textContent = "Paused";
          elements.ringProgress.style.strokeDashoffset = `${CIRCLE_LENGTH}`;
          return;
        }

        const remainingMs = state.deadline - Date.now();
        if (remainingMs <= 0) {
          triggerReminder();
          return;
        }

        const totalMs = state.intervalMinutes * 60 * 1000;
        const progress = Math.max(0, Math.min(1, remainingMs / totalMs));
        const remainingSeconds = Math.ceil(remainingMs / 1000);
        const minutes = Math.floor(remainingSeconds / 60);
        const seconds = remainingSeconds % 60;

        elements.minutesLeft.textContent = `${String(minutes).padStart(2, "0")}:${String(
          seconds
        ).padStart(2, "0")}`;
        elements.nextReminder.textContent = `In ${Math.ceil(remainingMs / 60000)} minute${
          Math.ceil(remainingMs / 60000) === 1 ? "" : "s"
        }`;
        elements.ringProgress.style.strokeDashoffset = `${CIRCLE_LENGTH * (1 - progress)}`;
      }

      function triggerReminder() {
        rotateMessage();
        state.deadline = Date.now() + state.intervalMinutes * 60 * 1000;
        saveState();
        syncUI();
        showToast("Break check-in: close the app you’re scrolling and come back to yourself.");
        maybeNotify();
      }

      function rotateMessage() {
        elements.messageCard.textContent = randomFrom(copyBank[state.tone]);
        elements.comparisonReset.textContent = randomFrom(resetPrompts);
        elements.breakIdea.textContent = randomFrom(breakIdeas);
      }

      function trackDailyOpen() {
        const today = new Date().toISOString().slice(0, 10);
        if (state.lastOpenDate !== today) {
          state.lastOpenDate = today;
          state.dailyOpenCount = 1;
        } else {
          state.dailyOpenCount += 1;
        }
        saveState();
      }

      function maybeNotify() {
        if (!("Notification" in window)) {
          return;
        }

        if (Notification.permission === "granted") {
          new Notification("slow hour", {
            body: "Time for a gentle break. Your life is not happening inside your feed."
          });
          return;
        }

        if (Notification.permission !== "denied") {
          Notification.requestPermission().then((permission) => {
            if (permission === "granted") {
              new Notification("slow hour", {
                body: "Time for a gentle break. Your life is not happening inside your feed."
              });
            }
          });
        }
      }

      function setupGames() {
        renderTicTacToe();
        resetMatchGame();
        syncGameTabs();
      }

      function syncGameTabs() {
        [...elements.gameTabs.querySelectorAll(".game-tab")].forEach((tab) => {
          tab.classList.toggle("active", tab.dataset.game === activeGame);
        });
        document.getElementById("game-tictactoe").classList.toggle("active", activeGame === "tictactoe");
        document.getElementById("game-match").classList.toggle("active", activeGame === "match");
      }

      function renderTicTacToe() {
        elements.ticGrid.innerHTML = "";
        ticBoard.forEach((value, index) => {
          const button = document.createElement("button");
          button.className = "tic-cell";
          button.type = "button";
          button.textContent = value;
          button.setAttribute("aria-label", `Tic tac toe square ${index + 1}`);
          button.addEventListener("click", () => playTicMove(index));
          elements.ticGrid.appendChild(button);
        });
      }

      function playTicMove(index) {
        if (ticBoard[index] || ticGameOver) {
          return;
        }

        ticBoard[index] = "X";
        renderTicTacToe();

        if (findWinner(ticBoard, "X")) {
          ticGameOver = true;
          elements.tttStatus.textContent = "You won. See? You are allowed to take up space.";
          return;
        }

        if (ticBoard.every(Boolean)) {
          ticGameOver = true;
          elements.tttStatus.textContent = "A tie counts. Rest is not wasted time.";
          return;
        }

        const move = chooseComputerMove();
        if (move !== -1) {
          ticBoard[move] = "O";
        }
        renderTicTacToe();

        if (findWinner(ticBoard, "O")) {
          ticGameOver = true;
          elements.tttStatus.textContent = "The board won this round. You can just press restart and begin again.";
          return;
        }

        if (ticBoard.every(Boolean)) {
          ticGameOver = true;
          elements.tttStatus.textContent = "A tie counts. Slow still counts.";
          return;
        }

        elements.tttStatus.textContent = "Your turn. Pick a square and stay here with yourself.";
      }

      function chooseComputerMove() {
        const empty = ticBoard
          .map((value, index) => ({ value, index }))
          .filter((cell) => !cell.value)
          .map((cell) => cell.index);

        if (!empty.length) {
          return -1;
        }

        if (ticBoard[4] === "") {
          return 4;
        }

        return empty[Math.floor(Math.random() * empty.length)];
      }

      function findWinner(board, player) {
        return tttWinningLines.some((line) => line.every((index) => board[index] === player));
      }

      function resetTicTacToe() {
        ticBoard = Array(9).fill("");
        ticGameOver = false;
        elements.tttStatus.textContent = "You go first. Pick a square and take up space.";
        renderTicTacToe();
      }

      function resetMatchGame() {
        matchDeck = [...matchIcons, ...matchIcons]
          .sort(() => Math.random() - 0.5)
          .map((icon, index) => ({ icon, id: `${icon}-${index}` }));
        revealedCards = [];
        matchedIndices = new Set();
        matchLock = false;
        elements.matchStatus.textContent = "Match all the icons. Slow is still winning.";
        renderMatchGame();
      }

      function renderMatchGame() {
        elements.matchGrid.innerHTML = "";

        matchDeck.forEach((card, index) => {
          const button = document.createElement("button");
          button.className = "match-card";
          button.type = "button";
          button.textContent = card.icon;
          button.setAttribute("aria-label", `Memory card ${index + 1}`);

          if (revealedCards.includes(index)) {
            button.classList.add("revealed");
          }

          if (matchedIndices.has(index)) {
            button.classList.add("matched");
            button.disabled = true;
          }

          if (!revealedCards.includes(index) && !matchedIndices.has(index)) {
            button.addEventListener("click", () => flipMatchCard(index));
          }

          elements.matchGrid.appendChild(button);
        });
      }

      function flipMatchCard(index) {
        if (matchLock || revealedCards.includes(index) || matchedIndices.has(index)) {
          return;
        }

        revealedCards.push(index);
        renderMatchGame();

        if (revealedCards.length < 2) {
          elements.matchStatus.textContent = "Nice. Pick one more.";
          return;
        }

        const [first, second] = revealedCards;
        const isMatch = matchDeck[first].icon === matchDeck[second].icon;

        if (isMatch) {
          matchedIndices.add(first);
          matchedIndices.add(second);
          revealedCards = [];
          renderMatchGame();

          if (matchedIndices.size === matchDeck.length) {
            elements.matchStatus.textContent =
              "You matched them all. Your brain deserved a softer assignment.";
            return;
          }

          elements.matchStatus.textContent = "Match made. Keep going, pretty mind.";
          return;
        }

        matchLock = true;
        elements.matchStatus.textContent = "Not a match. That is okay, try again.";

        window.setTimeout(() => {
          revealedCards = [];
          matchLock = false;
          renderMatchGame();
          elements.matchStatus.textContent = "Match all the icons. Slow is still winning.";
        }, 700);
      }

      function randomFrom(items) {
        return items[Math.floor(Math.random() * items.length)];
      }

      function showToast(message) {
        elements.toast.textContent = message;
        elements.toast.classList.add("show");
        window.clearTimeout(toastTimer);
        toastTimer = window.setTimeout(() => {
          elements.toast.classList.remove("show");
        }, 2600);
      }
    </script>
  </body>
</html>
