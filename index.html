<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1,user-scalable=no" />
  <title>To do • Outlook</title>
  <style>
    :root{ --bg:#ffffff; --card:#f6f6f7; --text:#111; --muted:#666; --border:#e6e6e6; --accent:#111; }
    body{ font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Arial, sans-serif; margin:14px; background:var(--bg); color:var(--text); }
    h1{ font-size:18px; margin:0 0 10px; letter-spacing:.2px; }
    .card{ background:var(--card); border:1px solid var(--border); border-radius:16px; padding:12px; margin:10px 0; }
    .row{ display:flex; gap:10px; flex-wrap:wrap; }
    textarea{ width:100%; min-height:110px; padding:12px; border-radius:14px; border:1px solid var(--border); font-size:16px; box-sizing:border-box; resize:vertical; background:#fff; }
    button{
      appearance:none; border:none; border-radius:999px; padding:12px 14px; font-size:15px; font-weight:650;
      cursor:pointer; background:var(--accent); color:#fff;
      flex:1;
      min-width:140px;
    }
    button.secondary{ background:#f2f2f2; color:#111; border:1px solid #e6e6e6; }
    button.danger{ background:#ffeff0; color:#b00020; border:1px solid #ffd0d7; }
    .hint{ font-size:13px; color:var(--muted); line-height:1.35; }
    .out{
      white-space:pre-wrap; border:1px solid var(--border); border-radius:14px; padding:12px;
      min-height:90px; background:#fff; font-size:16px; box-sizing:border-box;
    }
    .status{ font-size:13px; color:var(--muted); margin-top:8px; min-height:18px; }
    .pillbar{ display:flex; gap:8px; flex-wrap:wrap; margin-top:8px; }
    .pill{
      font-size:12px; color:#333; background:#fff; border:1px solid var(--border);
      border-radius:999px; padding:7px 10px;
    }
    code{ background:#f5f5f5; padding:2px 6px; border-radius:8px; border:1px solid #eee; }
    @media (max-width:420px){
      button{ min-width:120px; }
    }
  </style>
</head>

<body>
  <h1>To do • Outlook</h1>

  <div class="card">
    <div class="hint">
      Speak or type tasks. Use <b>new task</b> between items (best results).<br/>
      Then tap <b>Add to Outlook</b>.
    </div>

    <div class="pillbar" aria-hidden="true">
      <div class="pill">Split: <code>new task</code></div>
      <div class="pill">Also: <code>,</code> <code>;</code> + line breaks</div>
    </div>
  </div>

  <div class="card">
    <div class="row">
      <button id="speakBtn" class="secondary">🎤 Speak to fill</button>
      <button id="copyBtn" class="secondary">📋 Copy</button>
    </div>

    <div style="height:10px"></div>

    <textarea id="input" placeholder="e.g. Buy milk new task Email John"></textarea>

    <div class="status" id="status"></div>

    <div style="height:10px"></div>

    <div class="row">
      <button id="addBtn">➕ Add to Outlook</button>
    </div>

    <div style="height:10px"></div>

    <div class="row">
      <button id="connectBtn" class="secondary">🔗 Connect Outlook</button>
      <button id="openOutlookBtn" class="secondary">📅 Open Outlook</button>
    </div>
  </div>

  <div class="card">
    <div class="hint" style="margin-bottom:8px;">Formatted bullets:</div>
    <div id="formatted" class="out">• [ ] </div>
  </div>

<script>
  // ✅ SET THESE EXACTLY to your Shortcut names
  const ADD_SHORTCUT_NAME = "ToDo";               // your add-tasks shortcut
  const CONNECT_SHORTCUT_NAME = "ConnectOutlook"; // create this shortcut and name it exactly

  const $input = document.getElementById('input');
  const $formatted = document.getElementById('formatted');
  const $addBtn = document.getElementById('addBtn');
  const $copyBtn = document.getElementById('copyBtn');
  const $speakBtn = document.getElementById('speakBtn');
  const $status = document.getElementById('status');
  const $connectBtn = document.getElementById('connectBtn');
  const $openOutlookBtn = document.getElementById('openOutlookBtn');

  function stripLeadingBullet(s){
    return (s || "")
      .replace(/^\s*•\s*\[ ?[ xX] ?[ ]?\]\s*/g,'')
      .replace(/^\s*•\s*\[ ?[ ] ?\]\s*/g,'')
      .replace(/^\s*•\s*/g,'')
      .trim();
  }

  function normalizeSeparators(text){
    if(!text) return '';
    return text
      .replace(/\r\n/g, '\n')
      .replace(/\r/g, '\n')
      .replace(/new task/gi, '###DELIM###')
      .replace(/[;,]/g, '###DELIM###')
      .replace(/\n+/g, '###DELIM###');
  }

  function parseTasks(rawText){
    const norm = normalizeSeparators(rawText);
    const parts = norm
      .split('###DELIM###')
      .map(s => stripLeadingBullet(s))
      .map(s => s.trim())
      .filter(Boolean);

    // de-dupe for display (case-insensitive)
    const seen = new Set();
    const out = [];
    for(const p of parts){
      const key = p.toLowerCase();
      if(!seen.has(key)){
        seen.add(key);
        out.push(p);
      }
    }
    return out;
  }

  function formatTasks(tasks){
    if(!tasks.length) return "• [ ] ";
    return tasks.map(t => `• [ ] ${t}`).join('\n');
  }

  function updateFormatted(){
    const tasks = parseTasks($input.value || "");
    $formatted.textContent = formatTasks(tasks);
    return tasks;
  }

  function getPayloadForShortcut(){
    updateFormatted();
    return ($formatted.textContent || "").trim();
  }

  function setStatus(msg){
    $status.textContent = msg || "";
  }

  async function copyFormatted(){
    try{
      await navigator.clipboard.writeText($formatted.textContent);
      setStatus('Copied ✅');
      setTimeout(()=>setStatus(''), 1200);
    }catch(e){
      alert("Copy failed. You may need to long-press and copy manually.");
    }
  }

  function runShortcutByName(name, input){
    const url = `shortcuts://run-shortcut?name=${encodeURIComponent(name)}&input=${encodeURIComponent(input || "")}`;
    window.location.href = url;
  }

  function addToOutlook(){
    const payload = getPayloadForShortcut();
    if(!payload || payload.length < 2){
      setStatus('Type or speak something first.');
      return;
    }
    setStatus('Opening shortcut…');
    runShortcutByName(ADD_SHORTCUT_NAME, payload);
  }

  // ---- Speech ----
  function canSpeak(){
    return ('webkitSpeechRecognition' in window) || ('SpeechRecognition' in window);
  }

  function appendSpeechToTextarea(newText){
    const add = (newText || "").trim();
    if(!add) return;

    const existing = ($input.value || "").trim();
    // Always append on a new line so speech never overwrites/merges
    $input.value = existing ? (existing + '\n' + add) : add;

    updateFormatted();
  }

  function startSpeech(){
    setStatus('');
    if(!canSpeak()){
      setStatus('Speech not supported on this device/browser.');
      alert('Speech recognition not supported.');
      return;
    }

    const SR = window.SpeechRecognition || window.webkitSpeechRecognition;
    const rec = new SR();

    rec.lang = "en-GB";
    rec.interimResults = true;
    rec.continuous = false;

    let finalText = "";
    $speakBtn.textContent = "🛑 Listening...";
    $speakBtn.disabled = true;

    rec.onresult = (event) => {
      let interim = "";
      for(let i = event.resultIndex; i < event.results.length; i++){
        const res = event.results[i];
        const transcript = res[0].transcript || "";
        if(res.isFinal) finalText += transcript + " ";
        else interim += transcript + " ";
      }
      // optional: could show interim somewhere, but keep it simple
    };

    rec.onerror = (e) => {
      $speakBtn.textContent = "🎤 Speak to fill";
      $speakBtn.disabled = false;
      setStatus('Speech failed: ' + (e.error || 'unknown'));
    };

    rec.onend = () => {
      $speakBtn.textContent = "🎤 Speak to fill";
      $speakBtn.disabled = false;

      const cleaned = finalText.trim();
      if(!cleaned){
        setStatus('No speech captured.');
        return;
      }

      appendSpeechToTextarea(cleaned);
      setStatus('Done speaking ✅');
      setTimeout(()=>setStatus(''), 1200);
    };

    try{
      rec.start();
      setStatus('Listening…');
    }catch(e){
      $speakBtn.textContent = "🎤 Speak to fill";
      $speakBtn.disabled = false;
      setStatus('Could not start speech.');
    }
  }

  // ---- Buttons ----
  $input.addEventListener('input', updateFormatted);
  $copyBtn.addEventListener('click', copyFormatted);
  $addBtn.addEventListener('click', addToOutlook);
  $speakBtn.addEventListener('click', startSpeech);

  $connectBtn.addEventListener('click', () => {
    setStatus('Opening Connect Outlook…');
    // Preferred: run a Shortcut that triggers Outlook permission flow
    // (Shortcut should use Outlook/Calendar actions so iOS prompts for sign-in)
    try{
      runShortcutByName(CONNECT_SHORTCUT_NAME, "");
    }catch(e){
      setStatus('Could not run connect shortcut.');
      alert('Please create the "ConnectOutlook" shortcut (name must match).');
    }
  });

  $openOutlookBtn.addEventListener('click', () => {
    setStatus('Opening Outlook…');
    // Works if Outlook app installed
    window.location.href = "ms-outlook://";
    setTimeout(()=>setStatus(''), 1200);
  });

  updateFormatted();
</script>
</body>
</html>
