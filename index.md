
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Swap — Demo UI</title>

  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700;800&display=swap" rel="stylesheet">

  <style>
    :root{
      --bg-top:#3b2aa8;
      --bg-bottom:#1e0b3a;
      --card:#12061a;
      --panel:#24132b;
      --muted:#9b7fb4;
      --accent1:#7e3bff;
      --accent2:#b14dff;
      --button-grad: linear-gradient(90deg,var(--accent1),var(--accent2));
      --glass: rgba(255,255,255,0.03);
      --border: rgba(255,255,255,0.06);
      --white: #ffffff;
    }

    *{box-sizing:border-box}
    html,body{height:100%;margin:0}
    body{
      font-family:Inter,system-ui,-apple-system,Segoe UI,Roboto,"Helvetica Neue",Arial;
      background: linear-gradient(180deg,var(--bg-top) 0%, #4b2fb1 20%, var(--bg-bottom) 100%);
      color:var(--white);
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
      display:flex;
      align-items:flex-start;
      justify-content:center;
      padding:48px 18px;
    }

    /* subtle top hero text (like image) */
    .hero{
      width:100%;
      max-width:420px;
      margin:0 auto 18px;
      text-align:left;
    }
    .hero h2{
      margin:0 0 12px;
      font-weight:700;
      font-size:20px;
      line-height:1.15;
      color:rgba(255,255,255,0.98);
    }

    /* main card */
    .card{
      width:100%;
      max-width:420px;
      background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
      border-radius:16px;
      padding:18px;
      border:1px solid var(--border);
      box-shadow: 0 12px 40px rgba(8,5,12,0.6), inset 0 1px 0 rgba(255,255,255,0.02);
    }

    .card .title{
      font-size:22px;
      font-weight:800;
      margin:6px 8px 18px;
      color:var(--white);
    }

    .panel{
      background: linear-gradient(180deg, rgba(255,255,255,0.01), rgba(0,0,0,0.02));
      border-radius:12px;
      padding:14px;
      border:1px solid rgba(255,255,255,0.03);
      margin:8px;
    }

    .from-to{
      display:flex;
      gap:12px;
      flex-direction:column;
    }

    .row{
      background: rgba(0,0,0,0.25);
      border-radius:10px;
      padding:14px;
      border:1px solid rgba(255,255,255,0.03);
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:12px;
      min-height:72px;
      position:relative;
    }

    .label{
      font-size:13px;
      color:var(--muted);
      margin-bottom:6px;
    }

    .left-block{
      display:flex;
      gap:12px;
      align-items:center;
      min-width:0;
    }

    /* token button */
    .token-btn{
      display:inline-flex;
      gap:8px;
      align-items:center;
      padding:8px 12px;
      background: linear-gradient(90deg, rgba(0,0,0,0.25), rgba(255,255,255,0.02));
      border-radius:999px;
      border:1px solid rgba(255,255,255,0.04);
      cursor:pointer;
      min-width:92px;
    }
    .token-icon{
      width:20px;
      height:20px;
      display:inline-flex;
      align-items:center;
      justify-content:center;
      border-radius:6px;
      background: #f0c419;
      box-shadow: 0 1px 0 rgba(255,255,255,0.12) inset;
      flex-shrink:0;
    }
    .token-name{ font-weight:700; color:var(--white); font-size:14px; }

    .amount{
      color:rgba(255,255,255,0.65);
      font-size:18px;
      text-align:right;
      min-width:120px;
      word-break:break-all;
    }

    .amount.placeholder { color: rgba(255,255,255,0.20); font-size:18px; }

    /* center arrow circle */
    .swap-arrow{
      width:52px;
      height:52px;
      border-radius:50%;
      background: linear-gradient(180deg, rgba(0,0,0,0.25), rgba(0,0,0,0.14));
      border:1px solid rgba(255,255,255,0.04);
      display:flex;
      align-items:center;
      justify-content:center;
      margin:12px auto;
      box-shadow:0 6px 18px rgba(0,0,0,0.45);
    }
    .swap-arrow svg{ width:20px; height:20px; opacity:0.9; color:var(--white); }

    /* Select token button (purple pill) */
    .select-token{
      background: var(--button-grad);
      padding:12px 20px;
      border-radius:999px;
      font-weight:700;
      color:var(--white);
      border: none;
      box-shadow: 0 8px 24px rgba(125,54,255,0.18);
      cursor:pointer;
      font-size:15px;
      display:inline-block;
    }

    /* big Connect Wallet button */
    .connect{
      display:block;
      width: calc(100% - 32px);
      margin:18px auto 6px;
      padding:16px;
      border-radius:999px;
      background: var(--button-grad);
      color:var(--white);
      font-weight:800;
      text-align:center;
      border: none;
      font-size:18px;
      box-shadow: 0 14px 36px rgba(125,54,255,0.2);
      cursor:pointer;
    }

    /* right small info column in each row */
    .right-info{
      text-align:right;
      min-width:80px;
    }
    .small-muted{ font-size:12px; color:var(--muted) }

    /* Unknown badge top-right */
    .badge{
      position:absolute;
      right:14px;
      top:14px;
      display:inline-flex;
      gap:8px;
      align-items:center;
      padding:6px 10px;
      border-radius:999px;
      background: rgba(255,255,255,0.03);
      border:1px solid rgba(255,255,255,0.02);
      font-size:13px;
      color:var(--muted);
      backdrop-filter: blur(4px);
    }

    /* token selector area for lower panel */
    .select-area{ display:flex; align-items:center; gap:14px; justify-content:flex-start; flex-wrap:wrap; }

    /* subtle footer inside card */
    .card-footer{
      font-size:12px;
      color:var(--muted);
      margin:8px 12px 0;
      text-align:center;
    }

    /* responsive */
    @media (max-width:420px){
      .card{ padding:12px }
      .label{ font-size:12px }
      .amount { font-size:16px; min-width:90px }
      .select-token{ padding:10px 14px; font-size:14px }
      .connect{ font-size:16px; padding:14px }
    }
  </style>
</head>
<body>
  <div class="hero">
    <h2>The First Integrated Platform for Swap, Farming and Self‑Governance on BNB</h2>
  </div>

  <div class="card" role="region" aria-label="Swap panel">
    <div class="title">Swap</div>

    <div class="panel from-to" aria-hidden="false">
      <!-- From -->
      <div style="position:relative" class="row" id="fromRow">
        <div style="display:flex;flex-direction:column;min-width:0">
          <div class="label">From</div>
          <div style="display:flex;align-items:center;gap:10px;min-width:0">
            <button class="token-btn" id="fromTokenBtn" title="Choose token">
              <span class="token-icon" aria-hidden="true">
                <!-- simple BNB-like diamond -->
                <svg width="14" height="14" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M12 2L15.5 5.5L12 9L8.5 5.5L12 2Z" fill="#F3BA2F"/>
                  <path d="M12 15L15.5 11.5L12 8L8.5 11.5L12 15Z" fill="#F3BA2F"/>
                  <path d="M12 22L15.5 18.5L12 15L8.5 18.5L12 22Z" fill="#F3BA2F" opacity="0"/>
                </svg>
              </span>
              <span class="token-name">BNB</span>
            </button>

            <div class="amount placeholder" id="fromAmount">Enter an Amount</div>
          </div>
        </div>

        <div class="right-info">
          <div class="small-muted">Balance --</div>
        </div>

        <div class="badge" aria-hidden="true">
          <!-- shield icon -->
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" style="opacity:0.9" xmlns="http://www.w3.org/2000/svg">
            <path d="M12 2L20 5V11C20 16 16 21 12 22C8 21 4 16 4 11V5L12 2Z" fill="#2b2b3a"/>
            <circle cx="12" cy="11" r="3" fill="#5b6bff"/>
          </svg>
          <span style="opacity:0.9">Unknown</span>
        </div>
      </div>

      <!-- arrow -->
      <div class="swap-arrow" aria-hidden="true" title="Swap direction">
        <svg viewBox="0 0 24 24" fill="none" width="20" height="20" xmlns="http://www.w3.org/2000/svg">
          <path d="M12 5v10" stroke="rgba(255,255,255,0.9)" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
          <path d="M8 11l4 4 4-4" stroke="rgba(255,255,255,0.9)" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </div>

      <!-- To -->
      <div style="position:relative" class="row" id="toRow">
        <div style="display:flex;flex-direction:column;min-width:0">
          <div class="label">To</div>
          <div class="select-area">
            <button class="select-token" id="selectTokenBtn">Select a token</button>
          </div>
        </div>

        <div class="right-info">
          <div class="small-muted">Balance --</div>
          <div style="font-size:18px; color:rgba(255,255,255,0.85); margin-top:6px">0</div>
        </div>
      </div>
    </div>

    <button class="connect" id="connectBtn">Connect Wallet</button>

    <div class="card-footer"> Click "Select a token" to pick a sample token.</div>
  </div>

  <script>
    // Small interactive behavior: picking a token from a tiny menu,
    // and showing sample values (purely visual; not connected to chain).
    (function(){
      const selectBtn = document.getElementById('selectTokenBtn');
      const fromAmount = document.getElementById('fromAmount');
      const fromTokenBtn = document.getElementById('fromTokenBtn');

      const tokens = [
        { symbol:'PLAYBNB', name:'Play BNB', color:'#A15BFF' },
        { symbol:'USDT', name:'Tether', color:'#22C55E' },
        { symbol:'CAKE', name:'Pancake', color:'#FFB86B' }
      ];

      function buildMenu(){
        const menu = document.createElement('div');
        menu.style.position = 'absolute';
        menu.style.left = '50%';
        menu.style.top = '50%';
        menu.style.transform = 'translate(-50%,-50%)';
        menu.style.background = 'linear-gradient(180deg, rgba(0,0,0,0.85), rgba(0,0,0,0.8))';
        menu.style.padding = '12px';
        menu.style.borderRadius = '10px';
        menu.style.border = '1px solid rgba(255,255,255,0.06)';
        menu.style.boxShadow = '0 8px 30px rgba(0,0,0,0.8)';
        menu.style.zIndex = 9999;
        menu.id = 'tokenMenu';

        tokens.forEach(t => {
          const item = document.createElement('button');
          item.textContent = t.name + ' (' + t.symbol + ')';
          item.style.display = 'block';
          item.style.width = '260px';
          item.style.textAlign = 'left';
          item.style.padding = '10px';
          item.style.margin = '6px 0';
          item.style.background = 'transparent';
          item.style.color = 'white';
          item.style.border = '1px solid rgba(255,255,255,0.03)';
          item.style.borderRadius = '8px';
          item.style.cursor = 'pointer';
          item.onclick = () => {
            selectBtn.textContent = t.name + ' • ' + t.symbol;
            selectBtn.style.background = 'linear-gradient(90deg, '+ (t.color || '#7e3bff') +', rgba(160,90,255,0.9))';
            document.body.removeChild(menu);
            // show a sample from-amount placeholder cleared
            fromAmount.classList.remove('placeholder');
            fromAmount.textContent = '0.00';
          };
          menu.appendChild(item);
        });

        const cancel = document.createElement('button');
        cancel.textContent = 'Cancel';
        cancel.style.display = 'block';
        cancel.style.width = '260px';
        cancel.style.marginTop = '8px';
        cancel.style.padding = '10px';
        cancel.style.background = 'transparent';
        cancel.style.color = 'var(--muted)';
        cancel.style.border = '1px solid rgba(255,255,255,0.02)';
        cancel.style.borderRadius = '8px';
        cancel.onclick = () => { if(document.getElementById('tokenMenu')) document.body.removeChild(menu); };
        menu.appendChild(cancel);

        // place menu in center of viewport
        document.body.appendChild(menu);
      }

      selectBtn.addEventListener('click', buildMenu);

      // simple handler to toggle placeholder text in from amount when clicking token
      fromTokenBtn.addEventListener('click', ()=>{
        fromAmount.classList.remove('placeholder');
        fromAmount.textContent = '0.00';
      });

      // Connect Wallet button (visual only)
      document.getElementById('connectBtn').addEventListener('click', ()=>{
        alert(' Connect Wallet is not implemented here.');
      });
    })();
  </script>
</body>
</html>
