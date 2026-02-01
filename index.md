<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>BNB Swap</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <link rel="stylesheet" href="style.css" />
</head>
<body>

  <div class="page">

    <!-- Header -->
    <header class="header">
      <h1>
        The First Integrated Platform for Swap, Farming<br />
        and Self-Governance on <span>BNB</span>
      </h1>
    </header>

    <!-- Swap Card -->
    <section class="swap-card">

      <div class="swap-title">
        <h2>Swap</h2>
        <div class="settings">⚙️</div>
      </div>

      <!-- FROM -->
      <div class="swap-box">
        <div class="box-header">
          <span>From</span>
          <span class="wallet-status">
            <span class="shield">🛡</span> Unknown
          </span>
        </div>

        <div class="box-body">
          <button class="token-btn">
            <img src="https://cryptologos.cc/logos/bnb-bnb-logo.png" />
            BNB
            <span class="arrow">▼</span>
          </button>

          <input type="text" placeholder="Enter an Amount" />
        </div>

        <div class="balance">Balance --</div>
      </div>

      <!-- SWITCH -->
      <div class="switch">
        ⬇️
      </div>

      <!-- TO -->
      <div class="swap-box">
        <div class="box-header">
          <span>To</span>
        </div>

        <div class="box-body">
          <button class="token-btn secondary">
            Select a token
          </button>

          <input type="text" placeholder="0" disabled />
        </div>

        <div class="balance">Balance --</div>
      </div>

      <!-- CONNECT -->
      <button class="connect-btn">
        Connect Wallet
      </button>

    </section>
  </div>

</body>
</html>
