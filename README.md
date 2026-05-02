# Xauusd-calculator-<!DOCTYPE html>

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>XAUUSD Calculator</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  :root {
    --gold:      #C9A84C;
    --gold-bg:   rgba(201,168,76,0.08);
    --gold-bdr:  rgba(201,168,76,0.22);
    --green:     #2ECC7F;
    --green-bg:  rgba(46,204,127,0.08);
    --red:       #E8455A;
    --red-bg:    rgba(232,69,90,0.08);
    --blue:      #5B8FD4;
    --text:      #37352F;
    --text-2:    #6B6968;
    --text-3:    #9B9A97;
    --bg:        transparent;
    --card:      #FFFFFF;
    --card-bdr:  #E5E4E2;
    --input-bg:  #F7F6F3;
    --input-bdr: #D9D8D5;
    --row-alt:   #FAFAF9;
  }

@media (prefers-color-scheme: dark) {
:root {
–text:      #E8E2D4;
–text-2:    #9B9592;
–text-3:    #6B6562;
–card:      #1C1C1C;
–card-bdr:  #2E2E2E;
–input-bg:  #252525;
–input-bdr: #3A3A3A;
–row-alt:   #212121;
}
}

- { margin: 0; padding: 0; box-sizing: border-box; }

body {
background: var(–bg);
color: var(–text);
font-family: ‘JetBrains Mono’, ‘Courier New’, monospace;
font-size: 13px;
line-height: 1.5;
padding: 16px;
}

/* ── Title bar ── */
.title-bar {
display: flex;
align-items: center;
gap: 10px;
margin-bottom: 16px;
padding-bottom: 12px;
border-bottom: 1px solid var(–card-bdr);
}

.title-icon {
width: 28px; height: 28px;
background: var(–gold);
border-radius: 4px;
display: flex; align-items: center; justify-content: center;
font-size: 14px; flex-shrink: 0;
}

.title-text {
font-size: 14px;
font-weight: 600;
color: var(–text);
letter-spacing: 0.04em;
}

.title-sub {
font-size: 10px;
color: var(–text-3);
letter-spacing: 0.1em;
text-transform: uppercase;
margin-top: 1px;
}

/* ── Direction toggle ── */
.dir-toggle {
display: grid;
grid-template-columns: 1fr 1fr;
border: 1px solid var(–card-bdr);
border-radius: 6px;
overflow: hidden;
margin-bottom: 14px;
}

.dir-btn {
padding: 10px;
background: var(–input-bg);
border: none;
font-family: inherit;
font-size: 11px;
font-weight: 500;
letter-spacing: 0.12em;
text-transform: uppercase;
color: var(–text-3);
cursor: pointer;
transition: background 0.15s, color 0.15s;
}

.dir-btn:first-child { border-right: 1px solid var(–card-bdr); }

.dir-btn.buy  { background: var(–green-bg); color: var(–green); font-weight: 600; }
.dir-btn.sell { background: var(–red-bg);   color: var(–red);   font-weight: 600; }

/* ── Input grid ── */
.inputs {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 8px;
margin-bottom: 14px;
}

.field {
background: var(–card);
border: 1px solid var(–card-bdr);
border-radius: 6px;
padding: 10px 12px;
}

.field-label {
font-size: 9px;
letter-spacing: 0.18em;
text-transform: uppercase;
color: var(–text-3);
margin-bottom: 5px;
}

.field-row {
display: flex;
align-items: center;
gap: 6px;
}

.field input {
flex: 1;
background: var(–input-bg);
border: 1px solid var(–input-bdr);
border-radius: 4px;
color: var(–text);
font-family: inherit;
font-size: 14px;
font-weight: 500;
padding: 6px 9px;
outline: none;
width: 100%;
transition: border-color 0.15s;
-moz-appearance: textfield;
}
.field input::-webkit-outer-spin-button,
.field input::-webkit-inner-spin-button { -webkit-appearance: none; }
.field input:focus { border-color: var(–gold); }

.field-unit {
font-size: 9px;
color: var(–text-3);
letter-spacing: 0.1em;
white-space: nowrap;
flex-shrink: 0;
}

/* risk slider */
.slider-row {
margin-top: 6px;
display: flex;
align-items: center;
gap: 8px;
}

input[type=range] {
flex: 1;
-webkit-appearance: none;
height: 3px;
background: var(–input-bdr);
border-radius: 2px;
outline: none;
cursor: pointer;
}
input[type=range]::-webkit-slider-thumb {
-webkit-appearance: none;
width: 13px; height: 13px;
background: var(–gold);
border-radius: 50%;
cursor: pointer;
}

.slider-val {
font-size: 11px;
color: var(–gold);
font-weight: 600;
min-width: 36px;
text-align: right;
}

/* ── Results cards ── */
.results-top {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 8px;
margin-bottom: 8px;
}

.res-card {
background: var(–card);
border: 1px solid var(–card-bdr);
border-radius: 6px;
padding: 12px;
text-align: center;
}

.res-label {
font-size: 9px;
letter-spacing: 0.15em;
text-transform: uppercase;
color: var(–text-3);
margin-bottom: 5px;
}

.res-value {
font-size: 20px;
font-weight: 600;
line-height: 1;
}

.res-sub {
font-size: 9px;
color: var(–text-3);
margin-top: 3px;
}

.c-gold  { color: var(–gold); }
.c-green { color: var(–green); }
.c-red   { color: var(–red); }
.c-blue  { color: var(–blue); }

/* ── Stats strip ── */
.stats-strip {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 8px;
margin-bottom: 8px;
}

.stat-pill {
background: var(–card);
border: 1px solid var(–card-bdr);
border-radius: 6px;
padding: 8px 12px;
display: flex;
justify-content: space-between;
align-items: center;
}

.stat-key {
font-size: 9px;
letter-spacing: 0.1em;
text-transform: uppercase;
color: var(–text-3);
}

.stat-val {
font-size: 12px;
font-weight: 600;
}

/* ── Price levels ── */
.levels {
background: var(–card);
border: 1px solid var(–card-bdr);
border-radius: 6px;
padding: 12px;
margin-bottom: 8px;
}

.levels-hdr {
font-size: 9px;
letter-spacing: 0.18em;
text-transform: uppercase;
color: var(–text-3);
margin-bottom: 10px;
}

.level-row {
display: flex;
align-items: center;
gap: 10px;
padding: 6px 0;
}

.level-tag {
font-size: 9px;
font-weight: 600;
letter-spacing: 0.1em;
width: 38px;
text-align: center;
padding: 2px 6px;
border-radius: 3px;
flex-shrink: 0;
}

.tag-tp    { background: var(–green-bg); color: var(–green); }
.tag-entry { background: var(–gold-bg);  color: var(–gold);  }
.tag-sl    { background: var(–red-bg);   color: var(–red);   }

.level-price {
font-size: 14px;
font-weight: 500;
flex: 1;
}

.level-pnl {
font-size: 11px;
font-weight: 600;
min-width: 70px;
text-align: right;
}

.level-pips {
font-size: 9px;
color: var(–text-3);
min-width: 45px;
text-align: right;
}

/* pip bar between levels */
.pip-bar {
margin: 2px 0 2px 52px;
height: 3px;
background: var(–input-bg);
border-radius: 2px;
position: relative;
overflow: hidden;
}

.pip-fill {
position: absolute;
top: 0; bottom: 0;
border-radius: 2px;
transition: width 0.3s ease;
}

.pip-fill.tp { background: var(–green); left: 0; }
.pip-fill.sl { background: var(–red);   left: 0; }

/* ── Breakdown table ── */
.breakdown {
background: var(–card);
border: 1px solid var(–card-bdr);
border-radius: 6px;
overflow: hidden;
margin-bottom: 8px;
}

.breakdown-hdr {
padding: 8px 12px;
font-size: 9px;
letter-spacing: 0.18em;
text-transform: uppercase;
color: var(–text-3);
border-bottom: 1px solid var(–card-bdr);
background: var(–row-alt);
}

.bd-row {
display: flex;
justify-content: space-between;
align-items: center;
padding: 8px 12px;
border-bottom: 1px solid var(–card-bdr);
font-size: 12px;
}

.bd-row:last-child { border-bottom: none; }
.bd-row:nth-child(even) { background: var(–row-alt); }

.bd-key { color: var(–text-2); }
.bd-val { font-weight: 500; }

/* ── Risk warning ── */
.warn {
display: none;
background: var(–red-bg);
border: 1px solid rgba(232,69,90,0.3);
border-radius: 6px;
padding: 10px 12px;
font-size: 11px;
color: var(–red);
line-height: 1.6;
margin-bottom: 8px;
}
.warn.show { display: block; }

/* ── Reset ── */
.reset-btn {
width: 100%;
padding: 9px;
background: var(–input-bg);
border: 1px solid var(–card-bdr);
border-radius: 6px;
font-family: inherit;
font-size: 10px;
font-weight: 500;
letter-spacing: 0.15em;
text-transform: uppercase;
color: var(–text-3);
cursor: pointer;
transition: all 0.15s;
}

.reset-btn:hover {
border-color: var(–gold);
color: var(–gold);
}

/* value flash */
@keyframes flash {
0%   { opacity: 0.3; }
100% { opacity: 1; }
}
.flash { animation: flash 0.25s ease; }

/* responsive: single column on narrow */
@media (max-width: 480px) {
.inputs        { grid-template-columns: 1fr; }
.results-top   { grid-template-columns: 1fr 1fr; }
.results-top .res-card:last-child { grid-column: 1/-1; }
.stats-strip   { grid-template-columns: 1fr; }
}
</style>

</head>
<body>

<!-- Title -->

<div class="title-bar">
  <div class="title-icon">⚡</div>
  <div>
    <div class="title-text">XAU/USD Calculator</div>
    <div class="title-sub">Position · Risk · Profit</div>
  </div>
</div>

<!-- Direction -->

<div class="dir-toggle">
  <button class="dir-btn buy" id="btnBuy"  onclick="setDir('BUY')">▲ Buy / Long</button>
  <button class="dir-btn"    id="btnSell" onclick="setDir('SELL')">▼ Sell / Short</button>
</div>

<!-- Inputs -->

<div class="inputs">
  <div class="field">
    <div class="field-label">Account Balance</div>
    <div class="field-row">
      <input type="number" id="balance" value="250" min="1" step="10" oninput="calc()">
      <span class="field-unit">USD</span>
    </div>
  </div>

  <div class="field">
    <div class="field-label">Risk Per Trade</div>
    <div class="field-row">
      <input type="number" id="riskPct" value="2" min="0.1" max="100" step="0.1" oninput="syncR('n'); calc()">
      <span class="field-unit">%</span>
    </div>
    <div class="slider-row">
      <input type="range" id="riskSlider" min="0.5" max="20" step="0.5" value="2" oninput="syncR('s'); calc()">
      <span class="slider-val" id="sliderLabel">2%</span>
    </div>
  </div>

  <div class="field">
    <div class="field-label">Entry Price</div>
    <div class="field-row">
      <input type="number" id="entry" value="3300.00" step="0.10" oninput="calc()">
      <span class="field-unit">XAU</span>
    </div>
  </div>

  <div class="field">
    <div class="field-label">Pip Value (0.01 lot)</div>
    <div class="field-row">
      <input type="number" id="pipVal" value="0.10" min="0.01" step="0.01" oninput="calc()">
      <span class="field-unit">USD</span>
    </div>
  </div>

  <div class="field">
    <div class="field-label">Stop Loss</div>
    <div class="field-row">
      <input type="number" id="slPips" value="50" min="1" step="1" oninput="autoTP(); calc()">
      <span class="field-unit">PIPS</span>
    </div>
  </div>

  <div class="field">
    <div class="field-label">Take Profit</div>
    <div class="field-row">
      <input type="number" id="tpPips" value="100" min="1" step="1" oninput="calc()">
      <span class="field-unit">PIPS</span>
    </div>
  </div>
</div>

<!-- Top results -->

<div class="results-top">
  <div class="res-card">
    <div class="res-label">Lot Size</div>
    <div class="res-value c-gold" id="rLots">0.10</div>
    <div class="res-sub">lots</div>
  </div>
  <div class="res-card">
    <div class="res-label">Max Loss</div>
    <div class="res-value c-red" id="rRisk">$5.00</div>
    <div class="res-sub">if SL hit</div>
  </div>
  <div class="res-card">
    <div class="res-label">Profit</div>
    <div class="res-value c-green" id="rProfit">$10.00</div>
    <div class="res-sub">if TP hit</div>
  </div>
</div>

<!-- Stats strip -->

<div class="stats-strip">
  <div class="stat-pill">
    <span class="stat-key">R:R</span>
    <span class="stat-val c-gold" id="rRR">2.0R</span>
  </div>
  <div class="stat-pill">
    <span class="stat-key">Min Win Rate</span>
    <span class="stat-val c-blue" id="rBE">33.3%</span>
  </div>
  <div class="stat-pill">
    <span class="stat-key">Expectancy</span>
    <span class="stat-val" id="rExp">+$0.00</span>
  </div>
</div>

<!-- Price levels -->

<div class="levels">
  <div class="levels-hdr">Price Levels</div>

  <div class="level-row">
    <span class="level-tag tag-tp">TP</span>
    <span class="level-price c-green" id="lvTP">3310.00</span>
    <span class="level-pips c-green" id="lvTPpips">+100 pip</span>
    <span class="level-pnl c-green" id="lvTPpnl">+$10.00</span>
  </div>
  <div class="pip-bar"><div class="pip-fill tp" id="barTP" style="width:66%"></div></div>

  <div class="level-row">
    <span class="level-tag tag-entry">ENTRY</span>
    <span class="level-price c-gold" id="lvEntry">3300.00</span>
    <span class="level-pips" style="color:var(--text-3)">—</span>
    <span class="level-pnl" style="color:var(--text-3)">$0.00</span>
  </div>
  <div class="pip-bar"><div class="pip-fill sl" id="barSL" style="width:33%"></div></div>

  <div class="level-row">
    <span class="level-tag tag-sl">SL</span>
    <span class="level-price c-red" id="lvSL">3295.00</span>
    <span class="level-pips c-red" id="lvSLpips">-50 pip</span>
    <span class="level-pnl c-red" id="lvSLpnl">-$5.00</span>
  </div>
</div>

<!-- Breakdown -->

<div class="breakdown">
  <div class="breakdown-hdr">Full Breakdown</div>
  <div class="bd-row"><span class="bd-key">Dollar at Risk</span><span class="bd-val c-red" id="bRisk">$5.00</span></div>
  <div class="bd-row"><span class="bd-key">Margin Required (est.)</span><span class="bd-val c-gold" id="bMargin">$33.00</span></div>
  <div class="bd-row"><span class="bd-key">Lot Size</span><span class="bd-val" id="bLots">0.10 lots</span></div>
  <div class="bd-row"><span class="bd-key">Pip Value (this trade)</span><span class="bd-val" id="bPip">$10.00 / pip</span></div>
  <div class="bd-row"><span class="bd-key">Balance if WIN</span><span class="bd-val c-green" id="bWin">$260.00</span></div>
  <div class="bd-row"><span class="bd-key">Balance if LOSS</span><span class="bd-val c-red" id="bLoss">$245.00</span></div>
</div>

<!-- Risk warning -->

<div class="warn" id="warnBox">
  ⚠️ Risk above 5% — a 5-loss streak at this level cuts your account by <strong><span id="warnPct">0</span>%</strong>. Consider reducing to 1–2%.
</div>

<button class="reset-btn" onclick="reset()">↺ Reset to Defaults</button>

<script>
  let dir = 'BUY';

  function setDir(d) {
    dir = d;
    document.getElementById('btnBuy').className  = 'dir-btn' + (d==='BUY'  ? ' buy'  : '');
    document.getElementById('btnSell').className = 'dir-btn' + (d==='SELL' ? ' sell' : '');
    calc();
  }

  function syncR(src) {
    const n = document.getElementById('riskPct');
    const s = document.getElementById('riskSlider');
    const l = document.getElementById('sliderLabel');
    if (src === 'n') { s.value = Math.min(20, Math.max(0.5, n.value)); }
    else             { n.value = parseFloat(s.value).toFixed(1); }
    l.textContent = parseFloat(n.value).toFixed(1) + '%';
  }

  function autoTP() {
    const sl = parseFloat(document.getElementById('slPips').value) || 50;
    const tp = parseFloat(document.getElementById('tpPips').value) || 100;
    if (Math.abs(tp / sl - 2) < 0.15) document.getElementById('tpPips').value = sl * 2;
  }

  function $ (id) { return document.getElementById(id); }

  function money(n) {
    const s = Math.abs(n).toLocaleString('en-US',{minimumFractionDigits:2,maximumFractionDigits:2});
    return (n < 0 ? '-' : '') + '$' + s;
  }

  function flash(id) {
    const el = $(id);
    el.classList.remove('flash');
    void el.offsetWidth;
    el.classList.add('flash');
  }

  function calc() {
    const balance  = parseFloat($('balance').value)  || 250;
    const riskPct  = parseFloat($('riskPct').value)  / 100 || 0.02;
    const pipV01   = parseFloat($('pipVal').value)   || 0.10;
    const entry    = parseFloat($('entry').value)    || 3300;
    const slP      = parseFloat($('slPips').value)   || 50;
    const tpP      = parseFloat($('tpPips').value)   || 100;

    const pipV1    = pipV01 * 100;
    const riskAmt  = balance * riskPct;
    const lots     = Math.round(riskAmt / (slP * pipV1) * 100) / 100;
    const profit   = lots * tpP * pipV1;
    const loss     = lots * slP * pipV1;
    const rr       = tpP / slP;
    const be       = 1 / (1 + rr);
    const exp      = 0.55 * profit - 0.45 * loss;
    const margin   = lots * entry / 100;
    const pipTrade = lots * pipV1;

    const pip = 0.10;
    const tpPrice = dir === 'BUY' ? entry + tpP * pip : entry - tpP * pip;
    const slPrice = dir === 'BUY' ? entry - slP * pip : entry + slP * pip;

    // flash key outputs
    ['rLots','rRisk','rProfit','rRR','rBE','rExp'].forEach(flash);

    $('rLots').textContent   = lots.toFixed(2);
    $('rRisk').textContent   = money(loss);
    $('rProfit').textContent = money(profit);
    $('rRR').textContent     = rr.toFixed(1) + 'R';
    $('rBE').textContent     = (be * 100).toFixed(1) + '%';
    $('rExp').textContent    = (exp >= 0 ? '+' : '') + money(exp);
    $('rExp').style.color    = exp >= 0 ? 'var(--green)' : 'var(--red)';

    $('lvTP').textContent    = tpPrice.toFixed(2);
    $('lvEntry').textContent = entry.toFixed(2);
    $('lvSL').textContent    = slPrice.toFixed(2);
    $('lvTPpips').textContent  = '+' + tpP + ' pip';
    $('lvSLpips').textContent  = '-' + slP + ' pip';
    $('lvTPpnl').textContent = '+' + money(profit);
    $('lvSLpnl').textContent = '-' + money(loss);

    // pip bars (proportional, max 80%)
    const tot = slP + tpP;
    $('barTP').style.width = Math.min(80, (tpP/tot)*100) + '%';
    $('barSL').style.width = Math.min(80, (slP/tot)*100) + '%';

    $('bRisk').textContent   = money(loss);
    $('bMargin').textContent = money(margin);
    $('bLots').textContent   = lots.toFixed(2) + ' lots';
    $('bPip').textContent    = money(pipTrade) + ' / pip';
    $('bWin').textContent    = money(balance + profit);
    $('bLoss').textContent   = money(balance - loss);

    const warn = $('warnBox');
    if (riskPct > 0.05) {
      $('warnPct').textContent = ((1 - Math.pow(1-riskPct, 5))*100).toFixed(1);
      warn.classList.add('show');
    } else {
      warn.classList.remove('show');
    }

    // update slider label
    $('sliderLabel').textContent = parseFloat($('riskPct').value).toFixed(1) + '%';
    $('riskSlider').value = Math.min(20, parseFloat($('riskPct').value));
  }

  function reset() {
    $('balance').value   = 250;
    $('riskPct').value   = 2;
    $('riskSlider').value = 2;
    $('pipVal').value    = 0.10;
    $('entry').value     = 3300.00;
    $('slPips').value    = 50;
    $('tpPips').value    = 100;
    setDir('BUY');
  }

  calc();
</script>

</body>
</html>
