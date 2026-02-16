# happy-new-year
<!doctype html>
<html lang="zh-CN">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover" />
  <title>给你｜新年小惊喜</title>
  <style>
    :root{
      --bg1:#060914; --bg2:#141b3c; --rose:#ff6aa2; --gold:#ffd48a; --mint:#7fffd4;
      --card:#0c1330cc; --border:#ffffff22;
      --shadow: 0 24px 90px rgba(0,0,0,.45);
      --r: 22px;
    }
    *{box-sizing:border-box}
    body{
      margin:0; min-height:100vh; display:flex; align-items:center; justify-content:center;
      font-family:-apple-system,BlinkMacSystemFont,"PingFang SC","Microsoft YaHei",Segoe UI,Roboto,Helvetica,Arial,sans-serif;
      background:
        radial-gradient(900px 700px at 20% 20%, rgba(255,106,162,.25) 0%, transparent 60%),
        radial-gradient(900px 700px at 80% 30%, rgba(127,255,212,.16) 0%, transparent 60%),
        linear-gradient(160deg, var(--bg1), var(--bg2));
      color:#fff;
      overflow:hidden;
      padding: 18px;
    }

    /* 星光 */
    .stars{
      position:fixed; inset:0; pointer-events:none; z-index:1;
      background-image:
        radial-gradient(2px 2px at 18% 28%, rgba(255,255,255,.75) 40%, transparent 41%),
        radial-gradient(1.6px 1.6px at 70% 20%, rgba(255,255,255,.55) 40%, transparent 41%),
        radial-gradient(1.4px 1.4px at 40% 75%, rgba(255,255,255,.52) 40%, transparent 41%),
        radial-gradient(1.2px 1.2px at 85% 70%, rgba(255,255,255,.45) 40%, transparent 41%),
        radial-gradient(1px 1px at 10% 82%, rgba(255,255,255,.40) 40%, transparent 41%);
      opacity:.65;
      animation: twinkle 3.8s ease-in-out infinite;
    }
    @keyframes twinkle{ 0%,100%{opacity:.55} 50%{opacity:.85} }

    /* 心跳光晕 */
    .halo{
      position:fixed; inset:-20%;
      background: radial-gradient(circle at 50% 45%, rgba(255,106,162,.18) 0%, transparent 50%);
      filter: blur(2px);
      z-index:0; pointer-events:none;
      animation: pulse 2.6s ease-in-out infinite;
    }
    @keyframes pulse{
      0%,100%{ transform: scale(1); opacity:.75;}
      50%{ transform: scale(1.06); opacity:1;}
    }

    .wrap{ width:min(560px,100%); position:relative; z-index:2; }
    .card{
      background: var(--card);
      border:1px solid var(--border);
      border-radius: var(--r);
      box-shadow: var(--shadow);
      padding: 18px 18px 14px;
      backdrop-filter: blur(12px);
    }
    .top{
      display:flex; align-items:center; justify-content:space-between; gap:10px;
      margin-bottom: 8px;
    }
    .tag{
      font-size:12px; padding:6px 10px; border-radius:999px;
      border:1px solid #ffffff33; background:#ffffff10; white-space:nowrap;
      opacity:.92;
    }
    h1{
      margin: 10px 0 6px;
      font-size: 28px;
      letter-spacing: .5px;
      line-height:1.15;
      background: linear-gradient(90deg, #fff, var(--gold), var(--rose));
      -webkit-background-clip:text; background-clip:text; color: transparent;
      text-shadow: 0 0 28px rgba(255,212,138,.12);
    }
    .sub{
      margin:0 0 12px;
      opacity:.9;
      line-height:1.65;
      font-size: 14px;
    }

    .btns{ display:flex; gap:10px; flex-wrap:wrap; margin: 10px 0 14px; }
    button{
      border:0; border-radius: 14px;
      padding: 12px 14px;
      font-size: 14px; font-weight:700;
      color:#071026;
      cursor:pointer;
      flex: 1 1 170px;
      transition: transform .08s ease;
    }
    button:active{ transform: scale(.98); }

    .primary{ background: linear-gradient(90deg, var(--gold), #fff); box-shadow: 0 10px 30px rgba(255,212,138,.14); }
    .secondary{ background: linear-gradient(90deg, var(--rose), #fff); box-shadow: 0 10px 30px rgba(255,106,162,.12); }

    .panel{
      border:1px solid #ffffff22;
      border-radius: 16px;
      background:#00000022;
      padding: 12px;
      margin-top: 10px;
    }
    .panelTitle{ font-size: 13px; opacity:.82; margin-bottom: 8px; }
    .panelText{ font-size: 16px; line-height:1.65; }

    /* 心愿卡 */
    .cards{
      display:grid;
      grid-template-columns: repeat(3, 1fr);
      gap:10px;
      margin-top: 10px;
    }
    .wishCard{
      border-radius: 16px;
      border:1px solid #ffffff22;
      background: linear-gradient(160deg, rgba(255,255,255,.10), rgba(255,255,255,.04));
      padding: 12px 10px;
      min-height: 98px;
      cursor:pointer;
      position:relative;
      overflow:hidden;
      transition: transform .12s ease, border-color .12s ease;
    }
    .wishCard:active{ transform: scale(.99); }
    .wishCard .front{
      font-size: 13px; opacity:.9;
    }
    .wishCard .front b{ color: var(--gold); }
    .wishCard .back{
      display:none;
      margin-top: 8px;
      font-size: 14px;
      line-height:1.55;
      opacity:.95;
    }
    .wishCard.revealed{
      border-color: rgba(255,212,138,.55);
      box-shadow: 0 12px 40px rgba(255,212,138,.10);
    }
    .wishCard.revealed .back{ display:block; }
    .spark{
      position:absolute; inset:-40%;
      background: radial-gradient(circle at 40% 40%, rgba(255,212,138,.22) 0%, transparent 45%);
      transform: rotate(18deg);
      opacity:.0;
      transition: opacity .18s ease;
      pointer-events:none;
    }
    .wishCard.revealed .spark{ opacity:1; }

    /* 刮刮乐 */
    .scratchWrap{
      margin-top: 14px;
      border-radius: 18px;
      overflow:hidden;
      border:1px solid #ffffff22;
      background: #07102655;
      position:relative;
    }
    .secret{
      position:absolute; inset:0;
      display:flex; align-items:center; justify-content:center;
      text-align:center;
      padding: 16px;
      z-index:0;
    }
    .secret p{
      margin:0;
      font-size: 18px;
      line-height:1.65;
      background: linear-gradient(90deg, #fff, var(--gold));
      -webkit-background-clip:text; background-clip:text; color: transparent;
      text-shadow: 0 0 22px rgba(255,212,138,.10);
    }
    canvas{ display:block; width:100%; height:170px; z-index:2; position:relative; }

    .footer{ display:flex; justify-content:space-between; margin-top: 10px; font-size: 12px; opacity:.72; }

    /* 彩带 */
    .confetti{ position:fixed; inset:0; pointer-events:none; z-index:3; overflow:hidden; }
    .piece{
      position:absolute; width:10px; height:16px; border-radius: 3px; opacity:.95;
      transform: translateY(-20px) rotate(0deg);
      animation: fall 1.9s ease-in forwards;
    }
    @keyframes fall{
      to{ transform: translateY(110vh) rotate(720deg); opacity:.9; }
    }

    /* 小提示 */
    .hint{ font-size:12px; opacity:.75; margin-top: 8px; line-height:1.5; }
  </style>
</head>
<body>
  <div class="halo"></div>
  <div class="stars"></div>
  <div class="confetti" id="confetti"></div>

  <div class="wrap">
    <div class="card">
      <div class="top">
        <div class="tag" id="yearTag">✨ 新年小惊喜</div>
        <div class="tag">只对你生效</div>
      </div>

      <h1 id="h1">新年快乐，愿你被温柔以待</h1>
      <p class="sub" id="sub">
        我把祝福写进了一个小小的页面里。<br/>
        你先抽一张「心愿卡」，再把最后的惊喜刮开吧。
      </p>

      <div class="btns">
        <button class="primary" id="boomBtn">💫 点亮这一刻</button>
        <button class="secondary" id="resetBtn">🌙 再看一次</button>
      </div>

      <div class="panel">
        <div class="panelTitle">我想对你说：</div>
        <div class="panelText" id="mainText"></div>
        <div class="hint">提示：点下面任意一张卡，会揭晓一段专属祝福。</div>
      </div>

      <div class="cards" id="cards"></div>

      <div class="scratchWrap">
        <div class="secret" aria-hidden="true">
          <p id="secretText">🎁 最后一个惊喜：<br/>今年我想更认真地对你好。<br/>（暗号：<b>晚安</b>）</p>
        </div>
        <canvas id="scratch"></canvas>
      </div>

      <div class="footer">
        <span>把灰色刮开，就能看到最后一句话</span>
        <span id="progress">刮开：0%</span>
      </div>
    </div>
  </div>

<script>
  // ====== 只改这几处就够了 ======
  const herName = "";   // 例如："你的小鹿" / "XX" / 留空
  const yourName = "";  // 例如："MING" / 留空
  const openingLines = [
    "新的一年，愿你被世界温柔相待，也愿你永远有勇气做自己。",
    "我希望你每天都能睡得好、吃得香、心里亮堂堂的。",
    "你认真生活的样子很动人，愿好运总是偏爱你。"
  ];
  const cardBacks = [
    "愿你拥有一种笃定：不慌不忙，也能抵达想去的地方。",
    "愿你把自己照顾得很好：开心、健康、被爱、被理解。",
    "愿你遇见的每一次难，都能换来更强的你与更好的答案。"
  ];
  const secretPool = [
    "🎁 最后一个惊喜：<br/>今年我想更认真地对你好。<br/>（暗号：<b>晚安</b>）",
    "🎁 最后一个惊喜：<br/>如果你愿意，我们一起去看一场烟花。<br/>（暗号：<b>安排</b>）",
    "🎁 最后一个惊喜：<br/>我欠你一次拥抱，随时兑现。<br/>（暗号：<b>抱抱</b>）",
    "🎁 最后一个惊喜：<br/>你不必很厉害才被爱，你本来就值得。<br/>（暗号：<b>值得</b>）"
  ];
  // =================================

  const $ = s => document.querySelector(s);
  const yearTag = $("#yearTag");
  const h1 = $("#h1");
  const mainText = $("#mainText");
  const cardsEl = $("#cards");
  const secretText = $("#secretText");
  const progress = $("#progress");

  function pick(arr){ return arr[Math.floor(Math.random()*arr.length)]; }

  function personalizeTitle(){
    const y = new Date().getFullYear();
    yearTag.textContent = `✨ ${y} 给你的新年小惊喜`;
    const prefix = herName ? (herName + "，") : "";
    h1.textContent = prefix + "新年快乐，愿你被温柔以待";
  }

  function setOpening(){
    const line = pick(openingLines);
    mainText.textContent = line + (yourName ? ` —— ${yourName}` : "");
  }

  function confettiBurst(){
    const box = $("#confetti");
    const n = 70;
    const colors = ["#ffd48a","#ff6aa2","#7fffd4","#ffffff","#c8b6ff"];
    for(let i=0;i<n;i++){
      const d = document.createElement("div");
      d.className = "piece";
      d.style.left = (Math.random()*100) + "vw";
      d.style.top = (-10 - Math.random()*30) + "px";
      d.style.background = colors[Math.floor(Math.random()*colors.length)];
      d.style.animationDuration = (1.25 + Math.random()*1.35) + "s";
      d.style.width = (6 + Math.random()*10) + "px";
      d.style.height = (10 + Math.random()*18) + "px";
      box.appendChild(d);
      setTimeout(()=>d.remove(), 2800);
    }
  }

  function boom(){
    confettiBurst();
    setTimeout(confettiBurst, 220);
    h1.animate(
      [{transform:"scale(1)"},{transform:"scale(1.05)"},{transform:"scale(1)"}],
      {duration:420, easing:"ease-out"}
    );
  }

  // 心愿卡构建：3张
  function buildCards(){
    cardsEl.innerHTML = "";
    const fronts = [
      "抽一张 <b>心愿卡</b>",
      "抽一张 <b>好运卡</b>",
      "抽一张 <b>温柔卡</b>"
    ];
    for(let i=0;i<3;i++){
      const div = document.createElement("div");
      div.className = "wishCard";
      div.innerHTML = `
        <div class="spark"></div>
        <div class="front">${fronts[i]}</div>
        <div class="back">${cardBacks[i]}</div>
      `;
      div.addEventListener("click", ()=>{
        if(div.classList.contains("revealed")) return;
        div.classList.add("revealed");
        confettiBurst();
      });
      cardsEl.appendChild(div);
    }
  }

  // ====== 刮刮乐 ======
  const canvas = $("#scratch");
  const ctx = canvas.getContext("2d");
  let scratching = false;

  function resizeCanvas(){
    const rect = canvas.getBoundingClientRect();
    canvas.width = Math.floor(rect.width * devicePixelRatio);
    canvas.height = Math.floor(rect.height * devicePixelRatio);
    ctx.setTransform(devicePixelRatio,0,0,devicePixelRatio,0,0);
    drawCover();
  }

  function drawCover(){
    const w = canvas.getBoundingClientRect().width;
    const h = canvas.getBoundingClientRect().height;
    ctx.globalCompositeOperation = "source-over";
    const g = ctx.createLinearGradient(0,0,w,h);
    g.addColorStop(0, "rgba(215,215,215,0.95)");
    g.addColorStop(1, "rgba(145,145,145,0.95)");
    ctx.fillStyle = g;
    ctx.fillRect(0,0,w,h);

    ctx.fillStyle = "rgba(20,20,20,0.55)";
    ctx.font = "700 17px system-ui, -apple-system, PingFang SC, Microsoft YaHei";
    ctx.textAlign = "center";
    ctx.fillText("把这里刮开", w/2, h/2 + 6);
  }

  function scratchAt(x,y){
    const w = canvas.getBoundingClientRect().width;
    const h = canvas.getBoundingClientRect().height;
    ctx.globalCompositeOperation = "destination-out";
    ctx.beginPath();
    ctx.arc(x, y, 18, 0, Math.PI*2);
    ctx.fill();
    ctx.closePath();
    updateProgress(w,h);
  }

  function updateProgress(w,h){
    const img = ctx.getImageData(0,0, Math.floor(w), Math.floor(h)).data;
    let transparent = 0;
    const step = 16;
    const total = Math.floor((w*h)/step);
    for(let i=3, count=0; i<img.length; i+=4*step){
      if(img[i] < 20) transparent++;
      count++;
      if(count >= total) break;
    }
    const pct = Math.min(100, Math.max(0, Math.round(transparent / total * 100)));
    progress.textContent = "刮开：" + pct + "%";
    if(pct > 55){
      ctx.clearRect(0,0,w,h);
      progress.textContent = "刮开：100%";
      confettiBurst();
    }
  }

  function getPoint(e){
    const rect = canvas.getBoundingClientRect();
    const t = e.touches ? e.touches[0] : e;
    return { x: t.clientX - rect.left, y: t.clientY - rect.top };
  }

  canvas.addEventListener("touchstart", (e)=>{ scratching = true; const p=getPoint(e); scratchAt(p.x,p.y); }, {passive:true});
  canvas.addEventListener("touchmove", (e)=>{ if(!scratching) return; const p=getPoint(e); scratchAt(p.x,p.y); }, {passive:true});
  canvas.addEventListener("touchend", ()=> scratching=false);

  canvas.addEventListener("mousedown", (e)=>{ scratching = true; const p=getPoint(e); scratchAt(p.x,p.y); });
  window.addEventListener("mousemove", (e)=>{ if(!scratching) return; const p=getPoint(e); scratchAt(p.x,p.y); });
  window.addEventListener("mouseup", ()=> scratching=false);

  function resetScratch(){
    drawCover();
    progress.textContent = "刮开：0%";
  }

  function resetAll(){
    setOpening();
    buildCards();
    secretText.innerHTML = pick(secretPool);
    resetScratch();
    confettiBurst();
  }

  // 初始化
  personalizeTitle();
  resetAll();
  requestAnimationFrame(()=>{ resizeCanvas(); resetScratch(); setTimeout(confettiBurst, 280); });
  window.addEventListener("resize", ()=>{ resizeCanvas(); resetScratch(); });
  $("#boomBtn").addEventListener("click", boom);
  $("#resetBtn").addEventListener("click", resetAll);
</script>
</body>
</html>
