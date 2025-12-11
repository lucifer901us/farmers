<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Farmers Village Hub</title>
  <style>
    body { font-family: Arial, sans-serif; background:#f5f5f5; margin:0; }
    header { background:#4a7c2d; color:#fff; padding:20px; text-align:center; }
    nav { background:#35581c; padding:10px; display:flex; gap:15px; justify-content:center; }
    nav a { color:white; text-decoration:none; font-weight:bold; }
    .page { display:none; padding:20px; max-width:900px; margin:auto; background:white; margin-top:20px; }
    .active { display:block; }
    table { width:100%; border-collapse:collapse; margin-top:10px; }
    table, th, td { border:1px solid #ccc; }
    th, td { padding:8px; }
    button { background:#4a7c2d; color:white; border:none; padding:8px 12px; cursor:pointer; margin-top:10px; border-radius:5px; }
    button:hover { background:#3b621f; }
  </style>
</head>
<body>
  <header>
    <h1>Farmers Village Hub</h1>
    <p>Essential tools for village farmers</p>
  </header>

  <nav>
    <a href="#" onclick="showPage('weather')">Weather</a>
    <a href="#" onclick="showPage('market')">Market Rates</a>
    <a href="#" onclick="showPage('tips')">Farming Tips</a>
    <a href="#" onclick="showPage('expenses')">Expense Tracker</a>
    <a href="#" onclick="showPage('contacts')">Essential Contacts</a>
  </nav>

  <!-- Weather Page -->
  <div id="weather" class="page active">
    <h2>Weather Forecast</h2>
    <p>Simple weather display (static demo).</p>
    <div id="weatherBox">Today: Sunny, 29°C — Good for field work.</div>
  </div>

  <!-- Market Rates Page -->
  <div id="market" class="page">
    <h2>Today's Market Rates</h2>
    <table>
      <tr><th>Crop</th><th>Price (per kg)</th></tr>
      <tr><td>Wheat</td><td>₹24</td></tr>
      <tr><td>Rice</td><td>₹32</td></tr>
      <tr><td>Pulses</td><td>₹70</td></tr>
      <tr><td>Tomato</td><td>₹18</td></tr>
    </table>
  </div>

  <!-- Tips Page -->
  <div id="tips" class="page">
    <h2>Farming Tips</h2>
    <p id="tipText">Click the button below for a helpful tip.</p>
    <button onclick="newTip()">Get Tip</button>
  </div>

  <!-- Expense Tracker Page -->
  <div id="expenses" class="page">
    <h2>Expense Tracker</h2>
    <input id="item" placeholder="Item" />
    <input id="cost" placeholder="Cost" type="number" />
    <button onclick="addExpense()">Add</button>
    <ul id="expenseList"></ul>
    <h3>Total: ₹<span id="total">0</span></h3>
  </div>

  <!-- Contacts Page -->
  <div id="contacts" class="page">
    <h2>Essential Contacts</h2>
    <ul>
      <li>Local Vet: 9876543210</li>
      <li>Agriculture Officer: 9822334455</li>
      <li>Seed Supplier: 9450011223</li>
      <li>Machine Repair: 9988776655</li>
    </ul>
  </div>

  <script>
    function showPage(page) {
      document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
      document.getElementById(page).classList.add('active');
    }

    const tips = [
      "Use drip irrigation to save water.",
      "Check soil moisture before watering.",
      "Store grains in dry, airtight containers.",
      "Grow legumes to improve soil nitrogen.",
      "Use organic pesticides for safer crops."
    ];
    function newTip() {
      document.getElementById('tipText').innerText = tips[Math.floor(Math.random() * tips.length)];
    }

    let total = 0;
    function addExpense() {
      const item = document.getElementById('item').value;
      const cost = Number(document.getElementById('cost').value);
      if (!item || !cost) return alert('Enter item and cost');

      const li = document.createElement('li');
      li.innerText = item + ' — ₹' + cost;
      document.getElementById('expenseList').appendChild(li);

      total += cost;
      document.getElementById('total').innerText = total;
      document.getElementById('item').value = '';
      document.getElementById('cost').value = '';
    }
  </script>
</body>
</html>
