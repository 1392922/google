# google
杳冥之無可言
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="Google 風格搜尋頁，包含救己會、壓力測試器、占卜和保防處">
  <meta name="keywords" content="搜尋, 救己會, 壓力測試器, 占卜, 保防處, Google">
  <title>Google 搜尋</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Product+Sans&family=Creepster&family=Roboto:wght@400;500;700&display=swap" rel="stylesheet">
  <style>
    :root {
      --primary-blue: #4285F4;
      --primary-red: #EA4335;
      --primary-yellow: #FBBC05;
      --primary-green: #34A853;
      --border-color: #dfe1e5;
      --button-bg: #f8f9fa;
      --shadow-color: rgba(32, 33, 36, 0.28);
      --dark-bg: #000;
      --dark-text: #ff0000;
      --dark-shadow: rgba(255, 0, 0, 0.5);
      --dark-border: #330000;
      --defense-bg: linear-gradient(to bottom, #00264d, #001f3f);
      --defense-text: #FFFFFF;
      --defense-accent: #ff3333;
      --defense-gray: #E0E0E0;
      --defense-nav-bg: #001a33;
    }

    * { box-sizing: border-box; margin: 0; padding: 0; }

    body {
      font-family: 'Roboto', Arial, sans-serif;
      background: #fff;
      color: #202124;
      min-height: 100vh;
      width: 100%;
      transition: background 0.3s, color 0.3s;
      position: relative;
      overflow-x: hidden;
    }

    section {
      width: 100%;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      padding: 1rem;
      align-items: center;
      justify-content: center;
      animation: fadeIn 0.5s ease-in-out;
    }

    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }

    .hidden { display: none !important; }

    #selfsave-view {
      position: relative;
      overflow: hidden;
      background: radial-gradient(ellipse at bottom, #1b2735 0%, #090a0f 100%);
      color: #fff;
    }
    #selfsave-view::before {
      content: "";
      position: absolute;
      width: 200%;
      height: 200%;
      top: -50%;
      left: -50%;
      background: transparent url('https://www.transparenttextures.com/patterns/stardust.png') repeat;
      animation: moveStars 100s linear infinite;
      opacity: 0.6;
      pointer-events: none;
    }
    @keyframes moveStars {
      from { transform: translate(0, 0); }
      to { transform: translate(1000px, 1000px); }
    }
    #selfsave-view .logo, #selfsave-view .search-box, #selfsave-view .buttons {
      position: relative;
      z-index: 10;
    }

    .logo {
      font-size: clamp(50px, 10vw, 80px);
      font-weight: bold;
      font-family: 'Product Sans', Arial, sans-serif;
      text-align: center;
      margin-bottom: 1.5rem;
    }

    .search-box {
      width: min(90%, 600px);
      display: flex;
      align-items: center;
      border: 1px solid var(--border-color);
      border-radius: 24px;
      padding: 0.75rem 1rem;
      transition: box-shadow 0.2s, transform 0.1s;
      margin: 0 auto;
    }

    .search-box:focus-within {
      box-shadow: 0 1px 6px var(--shadow-color);
      border-color: transparent;
    }

    .search-box input {
      flex: 1;
      border: none;
      font-size: 1rem;
      outline: none;
      background: transparent;
      color: inherit;
    }

    .buttons {
      margin-top: 1.5rem;
      display: flex;
      gap: 0.5rem;
      justify-content: center;
    }

    .buttons button {
      background: var(--button-bg);
      border: none;
      border-radius: 20px;
      padding: 0.75rem 1.5rem;
      cursor: pointer;
      font-size: 0.875rem;
      box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.2);
      transition: background 0.2s, transform 0.1s, box-shadow 0.2s;
      pointer-events: auto;
    }

    .buttons button:hover {
      background: #e8e8e8;
      transform: scale(1.05);
    }

    .buttons button:active {
      transform: scale(0.95);
      box-shadow: 0 0 2px rgba(0, 0, 0, 0.3);
    }

    #main-view .logo span:nth-child(1) { color: var(--primary-blue); }
    #main-view .logo span:nth-child(2) { color: var(--primary-red); }
    #main-view .logo span:nth-child(3) { color: var(--primary-yellow); }
    #main-view .logo span:nth-child(4) { color: var(--primary-blue); }
    #main-view .logo span:nth-child(5) { color: var(--primary-green); }
    #main-view .logo span:nth-child(6) { color: var(--primary-red); }

    #selfsave-view .logo {
      color: #fff;
      font-family: 'Product Sans', Arial, sans-serif;
    }
    #selfsave-view .logo span:nth-child(1) { color: var(--primary-red); }
    #selfsave-view .logo span:nth-child(2) { color: var(--primary-blue); }
    #selfsave-view .logo span:nth-child(3) { color: var(--primary-green); }
    #selfsave-view .search-box { border: 1px solid #fff; background: rgba(255, 255, 255, 0.1); }
    #selfsave-view .search-box input { color: #fff; }
    #selfsave-view .buttons button { background: #333; color: #fff; }
    #selfsave-view .buttons button:hover { background: #555; transform: scale(1.05); }
    #selfsave-view .buttons button:active { transform: scale(0.95); }

    #search-results-view { background: #fff; }
    #search-results-view .search-box { margin-top: 1rem; }
    #search-results-view .results-list {
      width: min(90%, 600px);
      margin: 1rem auto;
      padding: 0;
      list-style: none;
    }
    #search-results-view .result-item {
      margin-bottom: 1rem;
      padding: 0.5rem;
      cursor: pointer;
      transition: background 0.2s;
    }
    #search-results-view .result-item:hover {
      background: #f8f9fa;
    }
    #search-results-view .result-item h3 {
      color: var(--primary-blue);
      font-size: 1.1rem;
      margin-bottom: 0.25rem;
    }
    #search-results-view .result-item p {
      font-size: 0.875rem;
      color: #4d5156;
    }

    #ping-view, #divination-view {
      background: var(--dark-bg);
      color: var(--dark-text);
      font-family: 'Creepster', cursive;
      text-shadow: 0 0 10px var(--dark-shadow);
      animation: flicker 1.5s infinite alternate;
    }

    @keyframes flicker {
      0% { opacity: 0.8; }
      100% { opacity: 1; }
    }

    #ping-view .title, #divination-view .title {
      font-size: clamp(40px, 8vw, 60px);
      margin-bottom: 1rem;
      text-align: center;
    }

    #ping-view .subtitle {
      font-size: 0.875rem;
      margin-bottom: 2rem;
      opacity: 0.7;
      text-align: center;
    }

    #ping-view .search-box, #divination-view .search-box {
      border: 2px solid var(--dark-border);
      background: #111;
    }

    #ping-view .search-box:focus-within, #divination-view .search-box:focus-within {
      box-shadow: 0 0 15px var(--dark-shadow);
    }

    #ping-view .search-box input, #divination-view .search-box input {
      color: var(--dark-text);
      font-family: Arial, sans-serif;
    }

    #ping-view .buttons button, #divination-view .buttons button {
      background: #220000;
      border: 1px solid var(--dark-border);
      color: var(--dark-text);
      font-family: 'Creepster', cursive;
      padding: 0.75rem 1.5rem;
      transition: background 0.2s, transform 0.1s;
    }

    #ping-view .buttons button:hover, #divination-view .buttons button:hover {
      background: #440000;
      transform: scale(1.05);
    }

    #ping-view .buttons button:active, #divination-view .buttons button:active {
      transform: scale(0.95);
    }

    #results, #divination-results {
      margin-top: 2rem;
      width: min(90%, 600px);
      max-height: 400px;
      overflow-y: auto;
      background: #111;
      padding: 1rem;
      border: 1px solid var(--dark-border);
      border-radius: 8px;
      font-family: monospace;
      color: #ffcccc;
      text-shadow: none;
      margin: 0 auto;
    }

    .defense-view {
      background: var(--defense-bg);
      color: var(--defense-text);
      font-family: 'Roboto', Arial, sans-serif;
      text-shadow: none;
      animation: none;
      display: flex;
      flex-direction: column;
      position: relative;
    }

    .defense-header {
      background: var(--defense-nav-bg);
      padding: 1rem;
      text-align: center;
      border-bottom: 4px solid var(--defense-accent);
      width: 100%;
      position: fixed;
      top: 0;
      left: 0;
      z-index: 1000;
    }

    .defense-title {
      font-size: 1.75rem;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 2px;
      color: var(--defense-text);
    }

    .defense-badge {
      font-size: 0.875rem;
      color: var(--defense-gray);
      margin-top: 0.5rem;
      font-weight: 400;
    }

    .defense-nav {
      position: fixed;
      top: 80px;
      left: 0;
      width: 200px;
      background: var(--defense-nav-bg);
      height: calc(100vh - 80px);
      padding: 1rem;
      display: flex;
      flex-direction: column;
      gap: 0.5rem;
      border-right: 1px solid var(--defense-gray);
      transition: transform 0.3s ease;
      z-index: 900;
    }

    .defense-nav.mobile-hidden {
      transform: translateX(-100%);
    }

    .defense-nav.mobile-visible {
      transform: translateX(0);
    }

    .defense-nav button {
      background: transparent;
      border: 1px solid var(--defense-gray);
      color: var(--defense-text);
      padding: 0.75rem 1rem;
      border-radius: 4px;
      cursor: pointer;
      font-size: 0.875rem;
      text-align: left;
      transition: background 0.2s, transform 0.1s;
      pointer-events: auto;
    }

    .defense-nav button:hover {
      background: var(--defense-accent);
      transform: scale(1.03);
    }

    .defense-nav button:active {
      transform: scale(0.97);
    }

    .defense-content {
      max-width: 1000px;
      margin: 100px auto 2rem;
      padding: 1rem;
      background: rgba(255, 255, 255, 0.05);
      border-radius: 8px;
      border: 1px solid var(--defense-gray);
      flex: 1;
      margin-left: 220px;
      z-index: 10;
      pointer-events: auto;
    }

    .news-list, .exam-list, .announcement-list, .role-table {
      list-style: none;
      padding: 0;
    }

    .news-item, .exam-item, .announcement-item {
      background: #003366;
      margin-bottom: 1rem;
      padding: 1rem;
      border-left: 4px solid var(--defense-accent);
      cursor: pointer;
      transition: background 0.2s, transform 0.1s;
      pointer-events: auto;
    }

    .news-item:hover, .exam-item:hover, .announcement-item:hover {
      background: #004080;
      transform: scale(1.02);
    }

    .news-item:active, .exam-item:active, .announcement-item:active {
      transform: scale(0.98);
    }

    .role-table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 1rem;
    }

    .role-table th, .role-table td {
      border: 1px solid var(--defense-gray);
      padding: 0.5rem;
      text-align: left;
    }

    .role-table th {
      background: var(--defense-nav-bg);
      color: var(--defense-text);
      font-weight: 500;
    }

    .defense-footer {
      text-align: center;
      padding: 1rem;
      border-top: 1px solid var(--defense-gray);
      width: 100%;
      background: var(--defense-nav-bg);
      z-index: 10;
    }

    .nato-logo {
      position: absolute;
      top: 1rem;
      right: 1rem;
      width: 50px;
      height: 50px;
      background: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="white"><path d="M12 2a10 10 0 1 0 0 20 10 10 0 0 0 0-20zm0 18a8 8 0 1 1 0-16 8 8 0 0 1 0 16zm-1-12.5l1-1.732 1 1.732V10h2v1h-2v2.5l-1 1.732-1-1.732V11H9v-1h2V7.5z"/></svg>') no-repeat center;
      background-size: contain;
      opacity: 0.8;
      pointer-events: none;
    }

    .hamburger {
      display: none;
      position: fixed;
      top: 1rem;
      left: 1rem;
      background: var(--defense-nav-bg);
      border: 1px solid var(--defense-gray);
      color: var(--defense-text);
      font-size: 1.5rem;
      cursor: pointer;
      z-index: 1100;
      padding: 0.5rem 1rem;
      border-radius: 4px;
      transition: transform 0.1s;
    }

    .hamburger:hover {
      transform: scale(1.1);
    }

    .hamburger:active {
      transform: scale(0.9);
    }

    .back-button {
      position: fixed;
      top: 1rem;
      left: 1rem;
      background: var(--defense-nav-bg);
      border: 1px solid var(--defense-gray);
      color: var(--defense-text);
      padding: 0.5rem 1rem;
      border-radius: 4px;
      cursor: pointer;
      z-index: 1100;
      transition: transform 0.1s;
    }

    .back-button:hover {
      background: var(--defense-accent);
      transform: scale(1.1);
    }

    .back-button:active {
      transform: scale(0.9);
    }

    @media (max-width: 768px) {
      .defense-nav {
        transform: translateX(-100%);
        width: 200px;
        z-index: 1000;
      }
      .defense-nav.mobile-visible {
        transform: translateX(0);
      }
      .defense-content {
        margin-left: 0;
        margin-top: 80px;
      }
      .hamburger {
        display: block;
      }
      .back-button {
        left: 3rem;
      }
    }

    @media (max-width: 600px) {
      .search-box { width: 95%; }
      .buttons { flex-direction: column; align-items: center; }
      .buttons button { width: 60%; text-align: center; padding: 0.75rem; }
      .logo { font-size: clamp(40px, 8vw, 60px); }
      .results-list { width: 95%; }
      .defense-content { margin: 90px auto 2rem; padding: 0.75rem; }
      .news-item, .exam-item, .announcement-item { padding: 0.75rem; }
    }
  </style>
</head>
<body>
  <section id="main-view">
    <header>
      <div class="logo" aria-label="Google 標誌">
        <span>G</span><span>o</span><span>o</span><span>g</span><span>l</span><span>e</span>
      </div>
    </header>
    <main>
      <form id="searchForm" class="search-box" role="search">
        <input type="search" id="searchInput" placeholder="在 Google 上搜尋..." aria-label="搜尋輸入框" required>
      </form>
      <div class="buttons">
        <button type="submit" form="searchForm">Google 搜尋</button>
        <button type="button" onclick="performDivination()">好手氣</button>
      </div>
    </main>
  </section>

  <section id="search-results-view" class="hidden">
    <button class="back-button" onclick="switchView('main')">← 返回</button>
    <header>
      <div class="logo" aria-label="Google 標誌">
        <span>G</span><span>o</span><span>o</span><span>g</span><span>l</span><span>e</span>
      </div>
    </header>
    <main>
      <form id="resultsSearchForm" class="search-box" role="search">
        <input type="search" id="resultsSearchInput" placeholder="在 Google 上搜尋..." aria-label="搜尋輸入框" required>
      </form>
      <div class="buttons">
        <button type="submit" form="resultsSearchForm">Google 搜尋</button>
      </div>
      <ul class="results-list" id="search-results-list"></ul>
    </main>
  </section>

  <section id="selfsave-view" class="hidden">
    <button class="back-button" onclick="switchView('main')">← 返回</button>
    <header>
      <div class="logo" aria-label="會己救標誌">
        <span>會</span><span>己</span><span>救</span>
      </div>
    </header>
    <main>
      <form id="selfsaveForm" class="search-box" role="search">
        <input type="search" id="selfsaveInput" placeholder="在會己救上搜尋..." aria-label="搜尋輸入框" required>
      </form>
      <div class="buttons">
        <button type="submit" form="selfsaveForm">搜尋</button>
      </div>
    </main>
  </section>

  <section id="ping-view" class="hidden">
    <button class="back-button" onclick="switchView('selfsave')">← 返回</button>
    <header>
      <div class="title" aria-label="壓力測試器">
        壓力測試器
      </div>
      <div class="subtitle">
        救己會製作
      </div>
    </header>
    <main>
      <form id="pingForm" class="search-box" role="search">
        <input type="text" id="targetInput" placeholder="輸入 IP 或網址..." aria-label="目標輸入框" required>
      </form>
      <div class="buttons">
        <button type="submit" form="pingForm">開始測試</button>
      </div>
      <div id="results"></div>
    </main>
  </section>

  <section id="divination-view" class="hidden">
    <button class="back-button" onclick="switchView('main')">← 返回</button>
    <header>
      <div class="title" aria-label="占卜大廳">
        神秘占卜大廳
      </div>
    </header>
    <main>
      <div class="buttons">
        <button onclick="performDivination()">進行占卜</button>
      </div>
      <div id="divination-results"></div>
    </main>
  </section>

  <section id="defense-main-view" class="hidden defense-view">
    <button class="hamburger" onclick="toggleNav()">☰</button>
    <button class="back-button" onclick="switchView('divination')">← 返回占卜</button>
    <header class="defense-header">
      <div class="defense-title">自救會保防處 - 國家安全防護中心</div>
      <div class="defense-badge">Official Website | Classification: Restricted</div>
    </header>
    <nav class="defense-nav mobile-hidden">
      <button onclick="switchDefenseView('news')">新聞處</button>
      <button onclick="switchDefenseView('intro')">介紹處</button>
      <button onclick="switchDefenseView('exam')">考核處</button>
      <button onclick="switchDefenseView('dispatch')">遣軍處</button>
      <button onclick="switchDefenseView('announcements')">公告處</button>
    </nav>
    <div class="nato-logo"></div>
    <main class="defense-content">
      <h2>歡迎進入自救會保防處</h2>
      <p>本處負責國家安全防護、危機應對與組織訓練。請選擇導航進入相關區域。</p>
    </main>
    <footer class="defense-footer">
      <p>&copy; 2025 自救會保防處 | 所有權利保留 | 機密資訊</p>
    </footer>
  </section>

  <section id="defense-news-view" class="hidden defense-view">
    <button class="hamburger" onclick="toggleNav()">☰</button>
    <button class="back-button" onclick="switchDefenseView('main')">← 返回</button>
    <header class="defense-header">
      <div class="defense-title">自救會保防處 - 新聞處</div>
      <div class="defense-badge">Official Website | Classification: Restricted</div>
    </header>
    <nav class="defense-nav mobile-hidden">
      <button onclick="switchDefenseView('news')">新聞處</button>
      <button onclick="switchDefenseView('intro')">介紹處</button>
      <button onclick="switchDefenseView('exam')">考核處</button>
      <button onclick="switchDefenseView('dispatch')">遣軍處</button>
      <button onclick="switchDefenseView('announcements')">公告處</button>
    </nav>
    <div class="nato-logo"></div>
    <main class="defense-content">
      <h2>最新新聞</h2>
      <ul class="news-list" id="news-list">
        <li class="news-item" data-news-key="2025-09-19">
          <h3>2025-09-19: 自救會防護演習成功</h3>
          <p>日期: 2025-09-19 | 簡述: 全員參與模擬危機應對，強化安全意識。</p>
        </li>
        <li class="news-item" data-news-key="2025-09-15A">
          <h3>2025-09-15: 新安全協議發布</h3>
          <p>日期: 2025-09-15 | 簡述: 更新防護指南，涵蓋網路與實體威脅。</p>
        </li>
        <li class="news-item" data-news-key="2025-09-15B">
          <h3>2025-09-15: 保防處飭告</h3>
          <p>日期: 2025-09-15 | 簡述: 全面提高戒備，確保情報安全。</p>
        </li>
      </ul>
    </main>
    <footer class="defense-footer">
      <p>&copy; 2025 自救會保防處 | 所有權利保留 | 機密資訊</p>
    </footer>
  </section>

  <section id="defense-news-detail-view" class="hidden defense-view">
    <button class="hamburger" onclick="toggleNav()">☰</button>
    <button class="back-button" onclick="switchDefenseView('news')">← 返回新聞處</button>
    <header class="defense-header">
      <div class="defense-title">自救會保防處 - 新聞詳情</div>
      <div class="defense-badge">Official Website | Classification: Restricted</div>
    </header>
    <nav class="defense-nav mobile-hidden">
      <button onclick="switchDefenseView('news')">新聞處</button>
      <button onclick="switchDefenseView('intro')">介紹處</button>
      <button onclick="switchDefenseView('exam')">考核處</button>
      <button onclick="switchDefenseView('dispatch')">遣軍處</button>
      <button onclick="switchDefenseView('announcements')">公告處</button>
    </nav>
    <div class="nato-logo"></div>
    <main class="defense-content" id="news-detail-content">
      <h2 id="news-title"></h2>
      <div id="news-content"></div>
    </main>
    <footer class="defense-footer">
      <p>&copy; 2025 自救會保防處 | 所有權利保留 | 機密資訊</p>
    </footer>
  </section>

  <section id="defense-intro-view" class="hidden defense-view">
    <button class="hamburger" onclick="toggleNav()">☰</button>
    <button class="back-button" onclick="switchDefenseView('main')">← 返回</button>
    <header class="defense-header">
      <div class="defense-title">自救會保防處 - 介紹處</div>
      <div class="defense-badge">Official Website | Classification: Restricted</div>
    </header>
    <nav class="defense-nav mobile-hidden">
      <button onclick="switchDefenseView('news')">新聞處</button>
      <button onclick="switchDefenseView('intro')">介紹處</button>
      <button onclick="switchDefenseView('exam')">考核處</button>
      <button onclick="switchDefenseView('dispatch')">遣軍處</button>
      <button onclick="switchDefenseView('announcements')">公告處</button>
    </nav>
    <div class="nato-logo"></div>
    <main class="defense-content">
      <h2>介紹處</h2>
      <p>自救會保防處成立於 2025 年，專責國家安全防護、危機預防與組織訓練。作為自救會的核心單位，我們致力於維護社會穩定，防範潛在威脅。成員來自各領域專家，共同構築防護網絡。核心使命：預防、應對、恢復。</p>
      <p>歡迎加入，共同守護未來。</p>
    </main>
    <footer class="defense-footer">
      <p>&copy; 2025 自救會保防處 | 所有權利保留 | 機密資訊</p>
    </footer>
  </section>

  <section id="defense-exam-view" class="hidden defense-view">
    <button class="hamburger" onclick="toggleNav()">☰</button>
    <button class="back-button" onclick="switchDefenseView('main')">← 返回</button>
    <header class="defense-header">
      <div class="defense-title">自救會保防處 - 考核處</div>
      <div class="defense-badge">Official Website | Classification: Restricted</div>
    </header>
    <nav class="defense-nav mobile-hidden">
      <button onclick="switchDefenseView('news')">新聞處</button>
      <button onclick="switchDefenseView('intro')">介紹處</button>
      <button onclick="switchDefenseView('exam')">考核處</button>
      <button onclick="switchDefenseView('dispatch')">遣軍處</button>
      <button onclick="switchDefenseView('announcements')">公告處</button>
    </nav>
    <div class="nato-logo"></div>
    <main class="defense-content">
      <h2>考核處</h2>
      <h3>公告考試日期</h3>
      <p>下次考試: 2025-10-15 (線上考核)</p>
      <p>考日概項: 涵蓋安全知識、危機應對，時長 2 小時，滿分 100 分。</p>
      <h3>考試檔案</h3>
      <ul class="exam-list">
        <li class="exam-item"><a href="#" download>安全知識 PDF 下載</a></li>
        <li class="exam-item"><a href="#" download>危機演習指南 PDF</a></li>
      </ul>
    </main>
    <footer class="defense-footer">
      <p>&copy; 2025 自救會保防處 | 所有權利保留 | 機密資訊</p>
    </footer>
  </section>

  <section id="defense-dispatch-view" class="hidden defense-view">
    <button class="hamburger" onclick="toggleNav()">☰</button>
    <button class="back-button" onclick="switchDefenseView('main')">← 返回</button>
    <header class="defense-header">
      <div class="defense-title">自救會保防處 - 遣軍處</div>
      <div class="defense-badge">Official Website | Classification: Restricted</div>
    </header>
    <nav class="defense-nav mobile-hidden">
      <button onclick="switchDefenseView('news')">新聞處</button>
      <button onclick="switchDefenseView('intro')">介紹處</button>
      <button onclick="switchDefenseView('exam')">考核處</button>
      <button onclick="switchDefenseView('dispatch')">遣軍處</button>
      <button onclick="switchDefenseView('announcements')">公告處</button>
    </nav>
    <div class="nato-logo"></div>
    <main class="defense-content">
      <h2>遣軍處</h2>
      <p>組織架構介紹與權利行使：</p>
      <table class="role-table">
        <thead>
          <tr>
            <th>職位</th>
            <th>介紹</th>
            <th>行使權利</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>管員</td>
            <td>負責日常巡邏與監控</td>
            <td>監控區域安全，報告異常</td>
          </tr>
          <tr>
            <td>社管員</td>
            <td>社區協調專員</td>
            <td>組織防護演習，社區聯絡</td>
          </tr>
          <tr>
            <td>社管長</td>
            <td>社群領導者</td>
            <td>決策地方防衛策略，資源調配</td>
          </tr>
          <tr>
            <td>團管員</td>
            <td>團體訓練官</td>
            <td>執行訓練計劃，成員評估</td>
          </tr>
          <tr>
            <td>團館長</td>
            <td>團體總管</td>
            <td>統籌資源分配，戰略執行</td>
          </tr>
          <tr>
            <td>副社長</td>
            <td>副總負責人</td>
            <td>協助決策、監督執行、危機應變</td>
          </tr>
          <tr>
            <td>社長</td>
            <td>最高領導</td>
            <td>最終決策、戰略規劃、組織領導</td>
          </tr>
        </tbody>
      </table>
    </main>
    <footer class="defense-footer">
      <p>&copy; 2025 自救會保防處 | 所有權利保留 | 機密資訊</p>
    </footer>
  </section>

  <section id="defense-announcements-view" class="hidden defense-view">
    <button class="hamburger" onclick="toggleNav()">☰</button>
    <button class="back-button" onclick="switchDefenseView('main')">← 返回</button>
    <header class="defense-header">
      <div class="defense-title">自救會保防處 - 公告處</div>
      <div class="defense-badge">Official Website | Classification: Restricted</div>
    </header>
    <nav class="defense-nav mobile-hidden">
      <button onclick="switchDefenseView('news')">新聞處</button>
      <button onclick="switchDefenseView('intro')">介紹處</button>
      <button onclick="switchDefenseView('exam')">考核處</button>
      <button onclick="switchDefenseView('dispatch')">遣軍處</button>
      <button onclick="switchDefenseView('announcements')">公告處</button>
    </nav>
    <div class="nato-logo"></div>
    <main class="defense-content">
      <h2>公告處</h2>
      <h3>澄清公告</h3>
      <ul class="announcement-list" id="clarification-list">
        <li class="announcement-item" data-announcement-id="1">
          <h3>2025-09-20: 關於近期謠言的澄清</h3>
          <p>日期: 2025-09-20 | 簡述: 針對不實網路傳言，保防處正式澄清並提供事實依據。</p>
        </li>
        <li class="announcement-item" data-announcement-id="2">
          <h3>2025-09-10: 訓練計劃誤解澄清</h3>
          <p>日期: 2025-09-10 | 簡述: 針對訓練計劃的誤解，保防處說明真實內容與目的。</p>
        </li>
      </ul>
      <h3>政策公告</h3>
      <ul class="announcement-list" id="policy-list">
        <li class="announcement-item" data-announcement-id="3">
          <h3>2025-09-18: 新安全政策發布</h3>
          <p>日期: 2025-09-18 | 簡述: 發布最新網路安全政策，強化資訊保護措施。</p>
        </li>
        <li class="announcement-item" data-announcement-id="4">
          <h3>2025-09-05: 危機應對政策更新</h3>
          <p>日期: 2025-09-05 | 簡述: 更新危機應對框架，提升應急效率。</p>
        </li>
      </ul>
    </main>
    <footer class="defense-footer">
      <p>&copy; 2025 自救會保防處 | 所有權利保留 | 機密資訊</p>
    </footer>
  </section>

  <section id="defense-announcement-detail-view" class="hidden defense-view">
    <button class="hamburger" onclick="toggleNav()">☰</button>
    <button class="back-button" onclick="switchDefenseView('announcements')">← 返回公告處</button>
    <header class="defense-header">
      <div class="defense-title">自救會保防處 - 公告詳情</div>
      <div class="defense-badge">Official Website | Classification: Restricted</div>
    </header>
    <nav class="defense-nav mobile-hidden">
      <button onclick="switchDefenseView('news')">新聞處</button>
      <button onclick="switchDefenseView('intro')">介紹處</button>
      <button onclick="switchDefenseView('exam')">考核處</button>
      <button onclick="switchDefenseView('dispatch')">遣軍處</button>
      <button onclick="switchDefenseView('announcements')">公告處</button>
    </nav>
    <div class="nato-logo"></div>
    <main class="defense-content" id="announcement-detail-content">
      <h2 id="announcement-title"></h2>
      <p id="announcement-date"></p>
      <p id="announcement-body"></p>
    </main>
    <footer class="defense-footer">
      <p>&copy; 2025 自救會保防處 | 所有權利保留 | 機密資訊</p>
    </footer>
  </section>

  <script>
    // 檢查是否允許 pushState
    function canUsePushState() {
      return window.location.origin !== 'null' && window.location.protocol !== 'about:';
    }

    // 安全執行 pushState
    function safePushState(state, title, url) {
      if (canUsePushState()) {
        try {
          history.pushState(state, title, url);
        } catch (e) {
          console.warn('pushState failed:', e.message);
        }
      }
    }

    // 占卜結果
    const divinationLevels = [
      { name: "小吉", meaning: "小有吉祥，宜謹慎行事，靜待時機。" },
      { name: "速喜", meaning: "喜事即將到來，行動迅速可獲益。" },
      { name: "大安", meaning: "大安大吉，萬事順遂，宜積極進取。" },
      { name: "流連", meaning: "流年多變，宜守不宜攻，化解糾紛。" },
      { name: "大羊", meaning: "阻礙重重，需堅韌面對，化解危機。" },
      { name: "慶雲", meaning: "大吉大利，慶賀雲集！天降祥瑞，萬事亨通。" }
    ];

    // 新聞數據
    const newsDetails = {
      "2025-09-19": {
        title: "自救會防護演習成功",
        date: "2025-09-19",
        content: `
          <p>2025年9月19日，自救會舉行了一場大規模防護演習。</p>
          <p>演習模擬了網路攻擊、基礎設施破壞以及資訊戰情境。</p>
          <p>參與人員展現了高度協同能力與安全意識，並成功完成所有測試。</p>
          <p>本次演習進一步鞏固了自救會在國防安全領域的防護能力。</p>
        `
      },
      "2025-09-15A": {
        title: "新安全協議發布",
        date: "2025-09-15",
        content: `
          <p>2025年9月15日，自救會保防處正式發布新一版安全協議。</p>
          <p>協議內容涵蓋網路威脅防禦、關鍵基礎設施保護以及組織安全規範。</p>
          <p>透過這份協議，自救會將全面升級資訊安全防護體系。</p>
        `
      },
      "2025-09-15B": {
        title: "保防處飭告",
        date: "2025-09-15",
        content: `
          <p>2025年9月15日，保防處對全體人員發出最新飭告。</p>
          <p>飭告強調：各單位需隨時保持高戒備，並持續演練應變機制。</p>
          <p>同時提醒所有人員注意內外部安全風險，嚴防情報外洩。</p>
        `
      }
    };

    // 公告數據
    const announcementData = [
      {
        id: 1,
        type: "clarification",
        title: "2025-09-20: 關於近期謠言的澄清",
        date: "2025-09-20",
        body: "針對近期網路流傳的不實謠言，保防處正式澄清：所有訓練計劃均符合安全規範，無任何違規行為。請成員以官方公告為準，切勿相信未經證實的資訊。"
      },
      {
        id: 2,
        type: "clarification",
        title: "2025-09-10: 訓練計劃誤解澄清",
        date: "2025-09-10",
        body: "針對外界對訓練計劃的誤解，保防處特此說明：訓練旨在提升危機應對能力，非軍事化行動。請參閱官方文件以了解詳情。"
      },
      {
        id: 3,
        type: "policy",
        title: "2025-09-18: 新安全政策發布",
        date: "2025-09-18",
        body: "保防處發布最新網路安全政策，要求所有成員採用多因素認證，並定期更新密碼。此政策將於 2025-10-01 生效。"
      },
      {
        id: 4,
        type: "policy",
        title: "2025-09-05: 危機應對政策更新",
        date: "2025-09-05",
        body: "更新危機應對框架，新增快速反應小組，提升應急效率。所有成員需參加相關培訓，詳情請見考核處。"
      }
    ];

    // 模擬搜尋結果
    function generateSearchResults(query) {
      const results = [
        { title: `關於 ${query} 的資訊`, url: `#`, description: `這是關於 ${query} 的模擬搜尋結果，提供相關資訊和概述。` },
        { title: `${query} 最新動態`, url: `#`, description: `探索與 ${query} 相關的最新更新和新聞。` },
        { title: `${query} 詳細介紹`, url: `#`, description: `深入了解 ${query} 的背景、功能和應用。` }
      ];
      return results;
    }

    // 顯示搜尋結果
    function showSearchResults(query) {
      const resultsList = document.getElementById('search-results-list');
      resultsList.innerHTML = '';
      const results = generateSearchResults(query);
      results.forEach(result => {
        const li = document.createElement('li');
        li.className = 'result-item';
        li.innerHTML = `
          <h3><a href="${result.url}">${result.title}</a></h3>
          <p>${result.description}</p>
        `;
        resultsList.appendChild(li);
      });
      document.getElementById('resultsSearchInput').value = query;
      switchView('search-results');
      safePushState({ view: 'search-results', query }, '', `/search?q=${encodeURIComponent(query)}`);
    }

    // 驗證 IP 或網址
    function isValidTarget(target) {
      const ipRegex = /^(?:[0-9]{1,3}\.){3}[0-9]{1,3}$/;
      const urlRegex = /^(https?:\/\/)?([\da-z.-]+)\.([a-z.]{2,6})([\/\w .-]*)*\/?$/;
      return ipRegex.test(target) || urlRegex.test(target);
    }

    // 模擬 ping
    function simulatePing(target, resultsDiv) {
      resultsDiv.innerHTML = '';
      const time = Math.floor(Math.random() * 100) + 10;
      const ttl = Math.floor(Math.random() * 10) + 54;
      const line = document.createElement('p');
      line.textContent = `64 bytes from ${target}: icmp_seq=1 ttl=${ttl} time=${time} ms`;
      resultsDiv.appendChild(line);
      resultsDiv.scrollTop = resultsDiv.scrollHeight;
    }

    // 進行占卜
    function performDivination() {
      const resultsDiv = document.getElementById('divination-results');
      resultsDiv.innerHTML = '';
      const level = divinationLevels[Math.floor(Math.random() * divinationLevels.length)];
      const p = document.createElement('p');
      p.innerHTML = `<strong>${level.name}</strong><br>${level.meaning}`;
      resultsDiv.appendChild(p);

      if (level.name === '慶雲') {
        const button = document.createElement('button');
        button.textContent = '進入自救會保防處';
        button.onclick = () => switchView('defense-main');
        button.style.marginTop = '1rem';
        button.style.padding = '0.75rem 1.5rem';
        button.style.background = '#ff3333';
        button.style.color = 'white';
        button.style.border = 'none';
        button.style.borderRadius = '4px';
        button.style.cursor = 'pointer';
        button.style.transition = 'transform 0.1s';
        button.addEventListener('mouseover', () => button.style.transform = 'scale(1.05)');
        button.addEventListener('mouseout', () => button.style.transform = 'scale(1)');
        button.addEventListener('mousedown', () => button.style.transform = 'scale(0.95)');
        button.addEventListener('mouseup', () => button.style.transform = 'scale(1)');
        resultsDiv.appendChild(button);
      }

      resultsDiv.scrollTop = resultsDiv.scrollHeight;
      switchView('divination');
    }

    // 顯示新聞詳情
    function showNewsDetail(key) {
      const news = newsDetails[key];
      if (!news) {
        console.error(`News key ${key} not found`);
        return;
      }

      document.getElementById('news-title').textContent = news.title;
      document.getElementById('news-content').innerHTML = news.content;
      switchDefenseView('news-detail');
      safePushState({ view: 'defense-news-detail', key }, '', `/defense/news/${key}`);
    }

    // 顯示公告詳情
    function showAnnouncementDetail(announcementId) {
      const announcement = announcementData.find(a => a.id === parseInt(announcementId));
      if (!announcement) {
        console.error(`Announcement ID ${announcementId} not found`);
        return;
      }

      document.getElementById('announcement-title').textContent = announcement.title;
      document.getElementById('announcement-date').textContent = `日期: ${announcement.date}`;
      document.getElementById('announcement-body').textContent = announcement.body;
      switchDefenseView('announcement-detail');
      safePushState({ view: 'defense-announcement-detail', announcementId }, '', `/defense/announcements/${announcementId}`);
    }

    // 切換導航顯示
    function toggleNav() {
      const nav = document.querySelector('.defense-nav');
      nav.classList.toggle('mobile-hidden');
      nav.classList.toggle('mobile-visible');
    }

    // 通用搜尋處理
    function handleSearch(e, currentView) {
      e.preventDefault();
      const input = e.target.querySelector('input');
      const query = input.value.trim().toLowerCase();
      if (!query) return;

      if (query === '聊天室' || query === '占卜') {
        switchDefenseView('news');
        return;
      }

      if (currentView === 'selfsave') {
        window.location.href = 'https://www.chatzy.com/99378426976932';
        return;
      }

      if (currentView === 'main' || currentView === 'search-results') {
        if (query === '救己會') {
          switchView('selfsave');
        } else {
          showSearchResults(query);
        }
      } else if (currentView === 'selfsave' && query === 'ping') {
        switchView('ping');
      }
    }

    // 切換視圖
    function switchView(view) {
      document.querySelectorAll('section').forEach(sec => sec.classList.add('hidden'));
      document.getElementById(`${view}-view`).classList.remove('hidden');

      if (view === 'selfsave') {
        document.body.style.background = 'radial-gradient(ellipse at bottom, #1b2735 0%, #090a0f 100%)';
        document.body.style.color = '#fff';
        document.body.style.fontFamily = 'Arial, sans-serif';
        document.body.style.textShadow = 'none';
        document.body.style.animation = 'none';
      } else if (view === 'ping' || view === 'divination') {
        document.body.style.background = 'var(--dark-bg)';
        document.body.style.color = 'var(--dark-text)';
        document.body.style.fontFamily = "'Creepster', cursive";
        document.body.style.textShadow = '0 0 10px var(--dark-shadow)';
        document.body.style.animation = 'flicker 1.5s infinite alternate';
      } else if (view.startsWith('defense-')) {
        document.body.style.background = 'var(--defense-bg)';
        document.body.style.color = 'var(--defense-text)';
        document.body.style.fontFamily = "'Roboto', Arial, sans-serif";
        document.body.style.textShadow = 'none';
        document.body.style.animation = 'none';
      } else {
        document.body.style.background = '#fff';
        document.body.style.color = '#202124';
        document.body.style.fontFamily = 'Arial, sans-serif';
        document.body.style.textShadow = 'none';
        document.body.style.animation = 'none';
      }

      safePushState({ view }, '', `/${view}`);
    }

    // 保防處子視圖切換
    function switchDefenseView(subview) {
      document.querySelectorAll('.defense-view').forEach(sec => sec.classList.add('hidden'));
      document.getElementById(`defense-${subview}-view`).classList.remove('hidden');
      const nav = document.querySelector('.defense-nav');
      if (window.innerWidth <= 768) {
        nav.classList.add('mobile-hidden');
        nav.classList.remove('mobile-visible');
      }
      safePushState({ view: `defense-${subview}` }, '', `/defense/${subview}`);
    }

    // 主頁事件
    document.getElementById('searchForm').addEventListener('submit', (e) => handleSearch(e, 'main'));

    // 搜尋結果頁事件
    document.getElementById('resultsSearchForm').addEventListener('submit', (e) => handleSearch(e, 'search-results'));

    // 救己會事件
    document.getElementById('selfsaveForm').addEventListener('submit', (e) => handleSearch(e, 'selfsave'));

    // ping 事件
    document.getElementById('pingForm').addEventListener('submit', (e) => {
      e.preventDefault();
      const target = document.getElementById('targetInput').value.trim();
      const resultsDiv = document.getElementById('results');

      if (!isValidTarget(target)) {
        resultsDiv.innerHTML = '<p style="color: #ff6666;">錯誤：請輸入有效的 IP 或網址</p>';
        return;
      }

      simulatePing(target, resultsDiv);
    });

    // 新聞列表點擊事件（使用事件委託）
    document.getElementById('defense-news-view').addEventListener('click', (e) => {
      const newsItem = e.target.closest('.news-item[data-news-key]');
      if (newsItem) {
        const key = newsItem.getAttribute('data-news-key');
        showNewsDetail(key);
      }
    });

    // 公告列表點擊事件（使用事件委託）
    document.getElementById('defense-announcements-view').addEventListener('click', (e) => {
      const announcementItem = e.target.closest('.announcement-item[data-announcement-id]');
      if (announcementItem) {
        const announcementId = announcementItem.getAttribute('data-announcement-id');
        showAnnouncementDetail(announcementId);
      }
    });

    // 為觸控設備添加觸控事件
    document.querySelectorAll('.buttons button, .defense-nav button, .news-item, .announcement-item, .back-button, .hamburger').forEach(element => {
      element.addEventListener('touchstart', () => {
        element.style.transform = 'scale(0.95)';
      });
      element.addEventListener('touchend', () => {
        element.style.transform = 'scale(1)';
      });
    });

    // 處理瀏覽器後退/前進
    window.addEventListener('popstate', (e) => {
      const state = e.state || {};
      const view = state.view || 'main';
      if (view.startsWith('defense-')) {
        if (view === 'defense-news-detail' && state.key) {
          showNewsDetail(state.key);
        } else if (view === 'defense-announcement-detail' && state.announcementId) {
          showAnnouncementDetail(state.announcementId);
        } else {
          switchDefenseView(view.replace('defense-', ''));
        }
      } else if (view === 'search-results' && state.query) {
        showSearchResults(state.query);
      } else {
        switchView(view);
      }
    });
  </script>
</body>
</html>
