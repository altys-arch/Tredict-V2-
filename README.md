<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Tredict Invictus Website</title>
  <style>
    /* Background gradasi animasi */
    body {
      margin: 0;
      font-family: 'Segoe UI', Tahoma, sans-serif;
      background: linear-gradient(-45deg, #0f172a, #1e293b, #2563eb, #9333ea);
      background-size: 400% 400%;
      animation: gradientMove 12s ease infinite;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      color: #fff;
      overflow: hidden;
    }

    @keyframes gradientMove {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }

    /* Container utama */
    .container {
      background: rgba(30, 41, 59, 0.9);
      backdrop-filter: blur(14px);
      padding: 30px;
      border-radius: 18px;
      width: 90%;
      max-width: 380px;
      box-shadow: 0 10px 40px rgba(0,0,0,0.6);
      text-align: center;
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%) scale(0.95);
      opacity: 0;
      pointer-events: none;
      transition: all 0.5s ease;
    }

    .container.active {
      opacity: 1;
      transform: translate(-50%, -50%) scale(1);
      pointer-events: auto;
    }

    /* Judul */
    .title {
      font-size: 22px;
      font-weight: bold;
      margin-bottom: 18px;
      color: #38bdf8;
      letter-spacing: 1px;
    }

    .info {
      font-size: 14px;
      margin: 8px 0;
      color: #e2e8f0;
    }

    /* Input */
    input {
      width: 100%;
      padding: 12px;
      margin: 8px 0;
      border: 1px solid #475569;
      border-radius: 10px;
      background: #334155;
      color: #fff;
      font-size: 14px;
      transition: 0.3s;
    }
    input:focus {
      outline: none;
      border-color: #38bdf8;
      background: #1e293b;
    }

    /* Button */
    .button {
      display: inline-block;
      margin: 8px 6px;
      padding: 10px 20px;
      background: linear-gradient(90deg, #3b82f6, #9333ea);
      color: #fff;
      border-radius: 10px;
      cursor: pointer;
      font-size: 14px;
      font-weight: 500;
      transition: all 0.3s ease;
    }
    .button:hover {
      opacity: 0.9;
      transform: translateY(-2px);
    }
    .button.clicked {
      background: #0c4a6e;
    }

    /* Link */
    .logout, .support {
      display: block;
      margin-top: 12px;
      cursor: pointer;
      font-size: 14px;
      text-decoration: underline;
      transition: 0.3s;
    }
    .logout { color: #f87171; }
    .support { color: #facc15; }
    .logout:hover, .support:hover { opacity: 0.8; }
  </style>
</head>
<body>
  <!-- Login Page -->
  <div class="container active" id="login-page">
    <div class="title">Login Tredict</div>
    <input type="text" id="username" placeholder="Username">
    <input type="password" id="password" placeholder="Password">
    <div>
      <span class="button" onclick="login()">Login</span>
    </div>
  </div>

  <!-- Main Page -->
  <div class="container" id="main-page">
    <div class="title">Tredict Invictus</div>
    <div class="info">welcome,user!</div>
    <div class="info">@aldannn</div>
    <label for="target-input" class="info">Target:</label>
    <input type="text" id="target-input" placeholder="Masukkan nomor target...">
    <div>
      <span class="button" onclick="handleClick(this, 'Crash Android')">Crash Android</span>
      <span class="button" onclick="handleClick(this, 'Crash iPhone')">Crash iPhone</span>
      <span class="button" onclick="handleClick(this, 'Delay Invisible')">Delay Invisible</span>
    </div>
    <div class="info">Status: Server Aktif</div>
    <div class="info">Info: Selamat datang, vands</div>
    <div class="info">© Tredict Invictus</div>
    <span class="support" onclick="goSupport()">Support</span>
    <span class="logout" onclick="logout()">Logout</span>
  </div>

  <!-- Result Page -->
  <div class="container" id="result-page">
    <div class="title">Tredict Invictus Website</div>
    <div class="info">indev</div>
    <div class="info">@wongasorr</div>
    <div class="info" id="result-target">Target: </div>
    <div class="info" id="result-info">Info: </div>
    <div class="info" id="result-time">Waktu: </div>
    <div class="info">© Tredict Invictus</div>
    <span class="support" onclick="goSupport()">Support</span>
    <span class="logout" onclick="logout()">Logout</span>
    <span class="button" onclick="goMain()">Kembali</span>
  </div>

  <!-- Support Page -->
  <div class="container" id="support-page">
    <div class="title">Support</div>
    <div class="info">Support this web >:)</div>
    <span class="button" onclick="goMain()">Kembali</span>
    <span class="logout" onclick="logout()">Logout</span>
  </div>

  <script>
    function showPage(pageId) {
      document.querySelectorAll(".container").forEach(c => c.classList.remove("active"));
      document.getElementById(pageId).classList.add("active");
    }

    function login() {
      const user = document.getElementById('username').value.trim();
      const pass = document.getElementById('password').value.trim();

      if ((user === "vands" && pass === "pintulog") || (user === "" && pass === "")) {
        showPage('main-page');
      } else {
        alert("Username atau Password salah!");
      }
    }

    function logout() {
      document.getElementById('username').value = "";
      document.getElementById('password').value = "";
      showPage('login-page');
    }

    function goSupport() {
      showPage('support-page');
    }

    function goMain() {
      showPage('main-page');
    }

    function handleClick(button, action) {
      button.classList.add('clicked');
      const target = document.getElementById('target-input').value || 'Tidak ada nomor';

      let message = 'Berhasil Mengirim ';
      if (action === 'Crash Android' || action === 'Crash iPhone') {
        message += 'CRASH FORCECLOSE';
      } else if (action === 'Delay Invisible') {
        message += 'DELAY INVISIBLE';
      }

      const now = new Date();
      const timeStr = now.toLocaleString('id-ID');

      document.getElementById('result-target').textContent = `Target: ${target}`;
      document.getElementById('result-info').textContent = `Info: ${message}`;
      document.getElementById('result-time').textContent = `Waktu: ${timeStr}`;

      showPage('result-page');
    }
  </script>
</body>
</html>
