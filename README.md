<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>☭ USSR Economy Simulator ☭</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #111;
      color: #eee;
      margin: 0;
      padding: 20px;
    }

    h1 {
      text-align: center;
      margin-bottom: 10px;
    }

    .container {
      display: flex;
      flex-wrap: wrap;
      gap: 20px;
      justify-content: center;
    }

    .section {
      background: #1c1c1c;
      padding: 12px;
      border: 1px solid #444;
      border-radius: 6px;
      flex: 1 1 300px;
      max-width: 480px;
      box-sizing: border-box;
    }

    .section h2 {
      font-size: 1.1em;
      margin-top: 0;
      border-bottom: 1px solid #333;
      padding-bottom: 5px;
    }

    button, select, input {
      margin: 4px 0;
      padding: 6px 10px;
      background: #333;
      color: #eee;
      border: 1px solid #555;
      border-radius: 4px;
      cursor: pointer;
    }

    button:hover {
      background: #444;
    }

    .small-buttons button {
      font-size: 0.9em;
      padding: 4px 8px;
    }

    ul {
      list-style: none;
      padding: 0;
      margin: 0;
    }

    .row {
      display: flex;
      justify-content: space-between;
    }

    .quotaStatus.met { color: lightgreen; }
    .quotaStatus.not-met { color: red; }

    #warning {
      color: orange;
      font-weight: bold;
      display: none;
    }

    @media (max-width: 800px) {
      .container {
        flex-direction: column;
        align-items: center;
      }
    }
  </style>
</head>
<body>
  <h1>☭ USSR Economy Simulator ☭</h1>

  <div class="container">
    <!-- Game Controls -->
    <div class="section">
      <h2>🎮 Controls</h2>
      <button onclick="saveGame(true)">💾 Save</button>
      <button onclick="loadGame()">📂 Load</button>
      <button onclick="resetGame()">🧨 Reset</button>
      <p id="gameMessage" style="color: yellow;"></p>
    </div>

    <!-- Policy -->
    <div class="section">
      <h2>📜 Policy</h2>
      <select id="policySelect" onchange="selectPolicy()">
        <option value="none">-- Select Policy --</option>
        <option value="marxism">Marxism</option>
        <option value="stalinism">Stalinism</option>
        <option value="maoism">Maoism</option>
        <option value="anarcho">Anarcho-Communism</option>
        <option value="leninism">Leninism</option>
        <option value="trotskyism">Trotskyism</option>
        <option value="kronstadtism">Kronstadtism</option>
      </select>
      <p><strong>Current:</strong> <span id="currentPolicy">None</span></p>
      <p id="policyEffects" style="font-style: italic; font-size: 0.9em;"></p>
    </div>

    <!-- Time Skip -->
    <div class="section">
      <h2>⏳ Skip Time</h2>
      <div class="small-buttons">
        <button onclick="skipDays(1)">▶ 1 Day</button>
        <button onclick="skipDays(10)">⏩ 10 Days</button>
        <button onclick="skipDays(100)">⏭ 100</button>
        <button onclick="skipDays(365)">🗓 1 Year</button>
      </div>
      <div>
        <input type="number" id="customYearsSkip" value="1" min="1" />
        <button onclick="skipCustomYears()">📆 Custom Years</button>
      </div>
    </div>

    <!-- Stats -->
    <div class="section">
      <h2>📊 Stats</h2>
      <p>🧍‍♂️ Manpower: <span id="manpower">0</span></p>
      <p>👷 Workers: <span id="workers">0</span></p>
      <p>🏠 Population: <span id="population">0</span></p>
    </div>

    <!-- Hiring -->
    <div class="section">
      <h2>👷 Hire Worker</h2>
      <button onclick="hireWorker()">➕ Hire (Cost: <span id="workerCost">10</span>)</button>
    </div>

    <!-- Resource Management -->
    <div class="section">
      <h2>⚙️ Resource Workers</h2>
      <p>Unassigned: <span id="unassigned">0</span></p>
      <div class="small-buttons">
        <p>Steel: <span id="steel">0</span> (<span id="steelWorkers">0</span>)
          <button onclick="assignWorker('steel')">+1</button>
          <button onclick="unassignWorker('steel')">-1</button>
        </p>
        <p>Food: <span id="food">0</span> (<span id="foodWorkers">0</span>)
          <button onclick="assignWorker('food')">+1</button>
          <button onclick="unassignWorker('food')">-1</button>
        </p>
        <p>Oil: <span id="oil">0</span> (<span id="oilWorkers">0</span>)
          <button onclick="assignWorker('oil')">+1</button>
          <button onclick="unassignWorker('oil')">-1</button>
        </p>
      </div>
    </div>

    <!-- Quotas -->
    <div class="section">
      <h2>📋 Quota (Day <span id="dayCount">1</span>)</h2>
      <ul>
        <li>Steel: <span id="quotaSteel">0</span>/<span id="targetSteel">100</span></li>
        <li>Food: <span id="quotaFood">0</span>/<span id="targetFood">80</span></li>
        <li>Oil: <span id="quotaOil">0</span>/<span id="targetOil">50</span></li>
      </ul>
      <p id="quotaStatus" class="quotaStatus not-met">🚫 Not Met</p>
      <p id="warning"></p>
    </div>
  </div>

  <script>
    // 🔧 Paste your existing JavaScript logic here
  </script>
</body>
</html>
