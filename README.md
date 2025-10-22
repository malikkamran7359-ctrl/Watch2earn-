<!doctype html>
<html lang="ur" dir="rtl">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Watch2Earn — Watch2earn</title>
  <style>
    :root{
      --bg:#0b0b0d;
      --panel:#0f0f10;
      --gold:#d4a721;
      --muted:#bdbdbd;
      --glass: rgba(255,255,255,0.03);
      --accent: linear-gradient(90deg,#d4a721,#f0c85a);
      font-family: "Segoe UI", Tahoma, sans-serif;
    }
    html,body{height:100%;margin:0;background:var(--bg);color:#fff;}
    .wrap{
      min-height:100%;
      display:flex;
      align-items:center;
      justify-content:center;
      padding:32px;
    }
    .card{
      width:100%;
      max-width:920px;
      background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(0,0,0,0.02));
      border-radius:16px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.6);
      overflow:hidden;
      display:grid;
      grid-template-columns:1fr 420px;
      gap:0;
      border:1px solid rgba(255,255,255,0.03);
    }
    .left{
      padding:36px;
      background:
        linear-gradient(180deg, rgba(255,255,255,0.01), rgba(0,0,0,0.02));
    }
    h1{margin:0 0 8px 0;font-size:28px;letter-spacing:0.4px}
    p.lead{margin:0 0 18px 0;color:var(--muted)}
    .stat{
      display:flex;
      gap:12px;
      margin-top:18px;
      flex-wrap:wrap;
    }
    .stat .box{
      background:var(--glass);
      padding:12px 14px;
      border-radius:10px;
      min-width:120px;
      text-align:center;
    }
    .box .num{font-weight:700;color:var(--gold);font-size:18px}
    .right{
      padding:28px;
      background:linear-gradient(135deg, rgba(212,167,33,0.06), rgba(0,0,0,0.03));
      border-left:1px solid rgba(255,255,255,0.02);
      display:flex;
      flex-direction:column;
      gap:12px;
      justify-content:center;
      align-items:center;
    }
    .card-brand{
      display:flex;flex-direction:column;gap:6px;align-items:center;
    }
    .logo{
      width:64px;height:64px;border-radius:12px;
      background:var(--gold);display:flex;align-items:center;justify-content:center;color:#111;font-weight:800;
      box-shadow: 0 8px 30px rgba(212,167,33,0.12);
    }
    .btn{
      display:inline-block;
      padding:12px 18px;border-radius:10px;font-weight:600;border:none;cursor:pointer;
      background:var(--gold);color:#070707;text-decoration:none;
      box-shadow: 0 6px 20px rgba(212,167,33,0.12);
    }
    .linkless{background:transparent;border:1px solid rgba(255,255,255,0.06);color:var(--muted);padding:8px 12px;border-radius:8px}
    .ref{
      width:100%;
      display:flex;
      gap:8px;
      margin-top:14px;
      align-items:center;
    }
    .ref input{
      flex:1;padding:10px;border-radius:8px;border:1px solid rgba(255,255,255,0.04);background:transparent;color:#fff;
    }
    small.note{color:var(--muted);display:block;margin-top:8px;font-size:13px}
    footer{padding:12px 16px;text-align:center;color:var(--muted);font-size:13px}
    /* responsive */
    @media (max-width:880px){
      .card{grid-template-columns:1fr; padding:0}
      .right{order:2}
    }
  </style>
</head>
<body>
  <div class="wrap">
    <div class="card" role="main">
      <div class="left">
        <div class="card-brand">
          <div class="logo">W2E</div>
          <h1>Watch2Earn</h1>
          <p class="lead">Videos دیکھیں — ریفر کریں — پیسہ کمائیں. (یہ صرف نمونہ ویب صفحہ ہے)</p>
        </div>

        <div class="stat" aria-hidden>
          <div class="box">
            <div class="num" id="views">0</div>
            <div style="font-size:12px;color:var(--muted)">Total Views</div>
          </div>
          <div class="box">
            <div class="num" id="users">0</div>
            <div style="font-size:12px;color:var(--muted)">Active Users</div>
          </div>
          <div class="box">
            <div class="num" id="earn">0</div>
            <div style="font-size:12px;color:var(--muted)">Paid Out (USD)</div>
          </div>
        </div>

        <div style="margin-top:18px">
          <h3 style="margin:0 0 8px 0">خلاصہ</h3>
          <p class="lead">یہ صفحہ ایک بنیادی frontend نمونہ ہے — حقیقی deposits/withdrawals کے لیے آپ کو JazzCash/Easypaisa کے merchant APIs اور backend درکار ہوں گے۔</p>

          <div style="margin-top:14px">
            <a class="btn" id="watchBtn">ابھی ویڈیو دیکھیں</a>
            <a class="linkless" id="leader" style="margin-left:12px">Leaderboard</a>
          </div>

          <div class="ref" style="margin-top:14px">
            <input id="refInput" readonly />
            <button class="linkless" id="copyRef">Copy</button>
          </div>
          <small class="note">آپ کا referral link اوپر دکھائے گا — اسے دوستوں کو دیں۔</small>
        </div>
      </div>

      <div class="right" aria-label="Actions">
        <h3 style="margin:6px 0 6px 0">Account</h3>
        <div style="width:100%;display:flex;gap:10px;flex-direction:column;align-items:stretch">
          <button class="btn" id="depositBtn">Deposit (JazzCash / EasyPaisa)</button>
          <button class="linkless" id="withdrawBtn">Withdraw</button>
          <button class="linkless" id="settingsBtn">Settings</button>
        </div>
        <small style="margin-top:8px" class="note">نوٹس: ادائیگی کے لیے backend اور merchant account درکار۔</small>
      </div>
    </div>
  </div>

  <footer>© Watch2Earn — Design: Dark & Gold — Sample Demo</footer>

  <script>
    // Read referral code from URL param ?ref=CODE or ?referrer=CODE
    function getParam(name) {
      const params = new URLSearchParams(window.location.search);
      return params.get(name) || params.get(name.toLowerCase()) || '';
    }
    const ref = getParam('ref') || getParam('referrer') || 'direct';
    const refInput = document.getElementById('refInput');
    const fullLink = window.location.origin + window.location.pathname + '?ref=' + encodeURIComponent(ref);
    refInput.value = fullLink;

    document.getElementById('copyRef').addEventListener('click', () => {
      navigator.clipboard?.writeText(refInput.value).then(()=>alert('Referral link copied!'));
    });

    // simple demo stats animation
    function animate(id, to, ms) {
      const el = document.getElementById(id); let start=0; const step = Math.ceil(to/(ms/30));
      const t = setInterval(()=>{ start+=step; if(start>=to){ el.textContent=to; clearInterval(t)} else el.textContent=start },30);
    }
    animate('views', 12450, 800);
    animate('users', 842, 700);
    animate('earn', 1284, 900);
