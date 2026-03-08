# Chatbot-Ai.
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>AI Assistant — Aditya Kumar</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@600;700;800&family=DM+Sans:ital,wght@0,400;0,500;0,600;1,400&display=swap" rel="stylesheet">
<style>
:root{
  --bg:#080C14;--s1:#0F1523;--s2:#141D2E;--border:#1C2740;
  --accent:#5B8DEF;--accent2:#7AAFF5;--glow:rgba(91,141,239,.18);
  --green:#3DD68C;--red:#EF4444;--white:#F0F4FF;--gray:#6B7A99;
  --light:#CBD5E8;--user-bg:#1A2B4A;--ai-bg:#111827;
}
*{margin:0;padding:0;box-sizing:border-box;-webkit-tap-highlight-color:transparent}
html,body{height:100%;overflow:hidden}
body{font-family:'DM Sans',sans-serif;background:var(--bg);color:var(--white);display:flex;flex-direction:column}
body::before{content:'';position:fixed;inset:0;background:radial-gradient(ellipse 70% 50% at 15% 0%,rgba(91,141,239,.12),transparent 60%),radial-gradient(ellipse 50% 40% at 85% 100%,rgba(61,214,140,.07),transparent 60%);pointer-events:none;z-index:0}

/* HEADER */
.header{background:rgba(8,12,20,.88);backdrop-filter:blur(16px);border-bottom:1px solid var(--border);padding:13px 18px;display:flex;align-items:center;justify-content:space-between;position:relative;z-index:10;flex-shrink:0}
.logo{display:flex;align-items:center;gap:10px}
.logo-icon{width:36px;height:36px;border-radius:10px;background:linear-gradient(135deg,var(--accent),#3D6FD6);display:flex;align-items:center;justify-content:center;font-size:18px;box-shadow:0 0 16px var(--glow)}
.logo-text{font-family:'Syne',sans-serif;font-size:16px;font-weight:800;color:var(--white)}
.logo-sub{font-size:10px;color:var(--gray)}
.status{display:flex;align-items:center;gap:6px;font-size:12px;color:var(--green);font-weight:600}
.sdot{width:7px;height:7px;border-radius:50%;background:var(--green);animation:pulse 2s infinite}
@keyframes pulse{0%,100%{box-shadow:0 0 0 0 rgba(61,214,140,.4)}50%{box-shadow:0 0 0 5px rgba(61,214,140,0)}}

/* CHAT */
.chat{flex:1;overflow-y:auto;padding:18px 14px;display:flex;flex-direction:column;gap:14px;position:relative;z-index:1;scroll-behavior:smooth}
.chat::-webkit-scrollbar{width:3px}
.chat::-webkit-scrollbar-thumb{background:var(--border);border-radius:2px}

/* WELCOME */
.welcome{text-align:center;padding:28px 16px;animation:fadeUp .6s ease both}
.w-icon{width:68px;height:68px;border-radius:18px;background:linear-gradient(135deg,var(--accent),#3D6FD6);display:flex;align-items:center;justify-content:center;font-size:30px;margin:0 auto 14px;box-shadow:0 8px 28px var(--glow)}
.welcome h2{font-family:'Syne',sans-serif;font-size:20px;font-weight:800;margin-bottom:7px}
.welcome p{font-size:13px;color:var(--gray);line-height:1.7;max-width:300px;margin:0 auto 18px}
.chips{display:flex;flex-wrap:wrap;gap:7px;justify-content:center}
.chip{padding:7px 13px;background:var(--s2);border:1px solid var(--border);border-radius:18px;font-size:12px;color:var(--light);cursor:pointer;transition:all .2s}
.chip:hover{border-color:var(--accent);color:var(--accent);background:var(--glow)}

/* MESSAGES */
.msg{display:flex;gap:9px;align-items:flex-start;animation:fadeUp .3s ease both;max-width:100%}
.msg.user{flex-direction:row-reverse}
.m-av{width:30px;height:30px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:14px;flex-shrink:0;margin-top:2px}
.msg.ai .m-av{background:linear-gradient(135deg,var(--accent),#3D6FD6)}
.msg.user .m-av{background:linear-gradient(135deg,#3DD68C,#2AB574)}
.m-bub{max-width:82%;padding:11px 14px;border-radius:15px;font-size:13.5px;line-height:1.75}
.msg.ai .m-bub{background:var(--ai-bg);border:1px solid var(--border);border-top-left-radius:4px;color:var(--light)}
.msg.user .m-bub{background:var(--user-bg);border:1px solid rgba(91,141,239,.25);border-top-right-radius:4px;color:var(--white)}
.m-time{font-size:10px;color:var(--gray);margin-top:4px}
.msg.user .m-time{text-align:right}

/* IMAGE IN CHAT */
.chat-img{max-width:220px;max-height:220px;border-radius:10px;object-fit:cover;display:block;margin-bottom:6px;border:1px solid var(--border)}

/* FILE PREVIEW */
.file-preview{display:flex;align-items:center;gap:9px;background:var(--s2);border:1px solid var(--border);border-radius:10px;padding:9px 12px;margin-bottom:6px}
.fp-icon{font-size:22px}
.fp-name{font-size:12px;color:var(--light);font-weight:600;max-width:160px;overflow:hidden;text-overflow:ellipsis;white-space:nowrap}
.fp-size{font-size:10px;color:var(--gray);margin-top:1px}

/* TYPING */
.typing{display:flex;gap:5px;align-items:center;padding:13px 15px}
.typing span{width:7px;height:7px;border-radius:50%;background:var(--accent);animation:bounce 1.2s infinite}
.typing span:nth-child(2){animation-delay:.2s}
.typing span:nth-child(3){animation-delay:.4s}
@keyframes bounce{0%,80%,100%{transform:translateY(0)}40%{transform:translateY(-8px)}}

/* ATTACHED PREVIEW BAR */
.attach-bar{display:none;padding:8px 14px 0;position:relative;z-index:10;flex-shrink:0}
.attach-items{display:flex;gap:8px;flex-wrap:wrap}
.attach-item{position:relative;display:inline-flex}
.attach-thumb{width:52px;height:52px;border-radius:9px;object-fit:cover;border:1.5px solid var(--accent)}
.attach-file-chip{display:flex;align-items:center;gap:6px;background:var(--s2);border:1.5px solid var(--accent);border-radius:9px;padding:6px 10px;font-size:11.5px;color:var(--light)}
.attach-x{position:absolute;top:-6px;right:-6px;width:18px;height:18px;background:var(--red);border-radius:50%;border:none;color:#fff;font-size:10px;cursor:pointer;display:flex;align-items:center;justify-content:center;line-height:1}

/* INPUT BAR */
.input-bar{background:rgba(8,12,20,.92);backdrop-filter:blur(16px);border-top:1px solid var(--border);padding:10px 14px 14px;position:relative;z-index:10;flex-shrink:0}
.input-row{display:flex;gap:8px;align-items:flex-end;background:var(--s1);border:1.5px solid var(--border);border-radius:15px;padding:8px 10px;transition:border-color .2s}
.input-row:focus-within{border-color:var(--accent);box-shadow:0 0 0 3px var(--glow)}
.icon-btn{width:34px;height:34px;border-radius:9px;background:transparent;border:1px solid var(--border);color:var(--gray);font-size:16px;cursor:pointer;display:flex;align-items:center;justify-content:center;transition:all .2s;flex-shrink:0}
.icon-btn:hover{border-color:var(--accent);color:var(--accent);background:var(--glow)}
.icon-btn.recording{background:rgba(239,68,68,.15);border-color:var(--red);color:var(--red);animation:recPulse 1s infinite}
@keyframes recPulse{0%,100%{box-shadow:0 0 0 0 rgba(239,68,68,.4)}50%{box-shadow:0 0 0 6px rgba(239,68,68,0)}}
.msg-input{flex:1;background:transparent;border:none;outline:none;font-size:13.5px;color:var(--white);font-family:'DM Sans',sans-serif;resize:none;min-height:20px;max-height:110px;line-height:1.5}
.msg-input::placeholder{color:var(--gray)}
.send-btn{width:34px;height:34px;border-radius:9px;background:linear-gradient(135deg,var(--accent),#3D6FD6);border:none;color:#fff;font-size:15px;cursor:pointer;display:flex;align-items:center;justify-content:center;transition:all .2s;flex-shrink:0;box-shadow:0 4px 12px var(--glow)}
.send-btn:hover{transform:scale(1.08)}
.send-btn:disabled{opacity:.4;cursor:not-allowed;transform:none}
.input-hint{font-size:10px;color:var(--gray);text-align:center;margin-top:7px}

/* VOICE OVERLAY */
.voice-overlay{position:fixed;inset:0;background:rgba(0,0,0,.75);z-index:999;display:none;flex-direction:column;align-items:center;justify-content:center;gap:20px;backdrop-filter:blur(8px)}
.voice-overlay.on{display:flex;animation:fadeIn .25s}
.voice-ring{width:110px;height:110px;border-radius:50%;background:rgba(239,68,68,.15);border:3px solid var(--red);display:flex;align-items:center;justify-content:center;font-size:42px;animation:voiceRing 1s ease-in-out infinite}
@keyframes voiceRing{0%,100%{transform:scale(1);box-shadow:0 0 0 0 rgba(239,68,68,.4)}50%{transform:scale(1.06);box-shadow:0 0 0 16px rgba(239,68,68,0)}}
.voice-txt{font-family:'Syne',sans-serif;font-size:18px;font-weight:700;color:var(--white)}
.voice-sub{font-size:13px;color:var(--gray)}
.voice-stop{background:var(--red);color:#fff;border:none;padding:12px 28px;border-radius:30px;font-size:14px;font-weight:700;cursor:pointer;font-family:'DM Sans',sans-serif;transition:all .2s}
.voice-stop:hover{opacity:.9;transform:scale(1.04)}

/* CODE */
.m-bub pre{background:#0A0F1A;border:1px solid var(--border);border-radius:9px;padding:11px;margin:8px 0;overflow-x:auto;font-size:12px;font-family:'Courier New',monospace;color:#A8C8FF;white-space:pre-wrap;word-break:break-word}
.m-bub code{background:rgba(91,141,239,.15);padding:2px 5px;border-radius:4px;font-size:12px;color:var(--accent2);font-family:'Courier New',monospace}
.m-bub pre code{background:transparent;padding:0;color:#A8C8FF}
.m-bub strong{color:var(--white);font-weight:700}
.m-bub em{color:var(--accent2);font-style:italic}
.m-bub ul,.m-bub ol{padding-left:16px;margin:5px 0}
.m-bub li{margin-bottom:3px}
.m-bub h3{font-size:14.5px;font-weight:700;color:var(--white);margin:9px 0 5px}
.copy-btn{display:inline-flex;align-items:center;gap:4px;background:var(--s2);border:1px solid var(--border);color:var(--gray);padding:3px 9px;border-radius:6px;font-size:11px;cursor:pointer;margin-top:5px;transition:all .2s;font-family:'DM Sans',sans-serif}
.copy-btn:hover{border-color:var(--accent);color:var(--accent)}
.err-bub{background:rgba(239,68,68,.1);border:1px solid rgba(239,68,68,.3);color:#FCA5A5;border-radius:11px;padding:11px 14px;font-size:13px}

@keyframes fadeUp{from{opacity:0;transform:translateY(10px)}to{opacity:1;transform:translateY(0)}}
@keyframes fadeIn{from{opacity:0}to{opacity:1}}

@media(max-width:480px){
  .m-bub{max-width:88%;font-size:13px}
  .welcome h2{font-size:18px}
}
</style>
</head>
<body>

<!-- VOICE OVERLAY -->
<div class="voice-overlay" id="voiceOverlay">
  <div class="voice-ring">🎙️</div>
  <div class="voice-txt">Bol rahe ho... Sun raha hoon</div>
  <div class="voice-sub" id="voiceLive">Awaiting speech...</div>
  <button class="voice-stop" onclick="stopVoice()">⏹ Rok do</button>
</div>

<!-- HEADER -->
<div class="header">
  <div class="logo">
    <div class="logo-icon">🤖</div>
    <div>
      <div class="logo-text">AI Assistant</div>
      <div class="logo-sub">Kumar Aditya ka Personal AI</div>
    </div>
  </div>
  <div class="status"><div class="sdot"></div>Online</div>
</div>

<!-- ATTACH PREVIEW BAR -->
<div class="attach-bar" id="attachBar">
  <div class="attach-items" id="attachItems"></div>
</div>

<!-- CHAT AREA -->
<div class="chat" id="chat">
  <div class="welcome" id="welcome">
    <div class="w-icon">🤖</div>
    <h2>Namaste! Main hoon aapka AI 👋</h2>
    <p>Koi bhi sawaal poochho, photo/file bhejo ya bolo — main hamesha taiyaar hoon!</p>
    <div class="chips">
      <div class="chip" onclick="quickAsk('School ke baare mein batao')">🏫 School info</div>
      <div class="chip" onclick="quickAsk('Admission process kya hai?')">📋 Admission</div>
      <div class="chip" onclick="quickAsk('Ek motivational quote batao')">🔥 Motivate karo</div>
      <div class="chip" onclick="quickAsk('Mujhe ek Hindi poem likho')">✍️ Poem likho</div>
      <div class="chip" onclick="quickAsk('Aaj ka mausam kaisa rahega?')">🌤️ Mausam</div>
      <div class="chip" onclick="quickAsk('Maths mein help karo')">📐 Maths help</div>
    </div>
  </div>
</div>

<!-- INPUT BAR -->
<div class="input-bar">
  <div class="input-row">
    <!-- Photo upload -->
    <label class="icon-btn" for="photoInput" title="Photo bhejo">📷</label>
    <input type="file" id="photoInput" accept="image/*" style="display:none" onchange="attachFile(this,'photo')">

    <!-- File upload -->
    <label class="icon-btn" for="fileInput" title="File bhejo">📎</label>
    <input type="file" id="fileInput" accept=".pdf,.doc,.docx,.txt,.csv,.xlsx" style="display:none" onchange="attachFile(this,'file')">

    <!-- Text input -->
    <textarea class="msg-input" id="msgInput" placeholder="Kuch bhi poochho... ya photo/file attach karo" rows="1"
      onkeydown="handleKey(event)" oninput="autoResize(this)"></textarea>

    <!-- Voice -->
    <button class="icon-btn" id="voiceBtn" onclick="startVoice()" title="Bolkar poochho">🎙️</button>

    <!-- Send -->
    <button class="send-btn" id="sendBtn" onclick="sendMsg()">➤</button>
  </div>
  <div class="input-hint">📷 Photo • 📎 File • 🎙️ Voice • ➤ Send — Sab supported!</div>
</div>

<script>
const SYSTEM = `Tum ek helpful, friendly aur smart AI assistant ho jo Kumar Aditya ke liye kaam karta hai.

Tum yeh sab kar sakte ho:
- Har tarah ke sawaalon ka jawab — Hindi ya English
- Photos dekhna aur describe karna
- Files/documents padhna aur summarize karna
- Math, coding, creative writing, sab kuch

School info:
- Naam: Aawasiya New Modern English School, Mohanpur, Nauhatta, Saharsa, Bihar
- Director: Sindhu Kumar Singh | Contact: 9113788228
- Classes: Nursery–8th, English Medium
- Admission 2026-27 open — 10 April se pehle free

Rules: Hamesha helpful, positive, aur clear raho. Hindi mein poochho toh Hindi mein jawab do.`;

let messages = [];
let isLoading = false;
let attachedFiles = []; // {type, name, size, base64, mediaType}

// ══════════════════════════
// FILE / PHOTO ATTACH
// ══════════════════════════
function attachFile(input, type){
  const file = input.files[0];
  if(!file) return;
  const maxMB = type==='photo' ? 5 : 10;
  if(file.size > maxMB*1024*1024){ alert(`File ${maxMB}MB se chhoti honi chahiye!`); return; }

  const reader = new FileReader();
  reader.onload = function(e){
    const base64 = e.target.result.split(',')[1];
    const mediaType = file.type;
    attachedFiles.push({type, name:file.name, size:file.size, base64, mediaType, dataUrl:e.target.result});
    renderAttachBar();
  };
  reader.readAsDataURL(file);
  input.value = '';
}

function renderAttachBar(){
  const bar   = document.getElementById('attachBar');
  const items = document.getElementById('attachItems');
  if(attachedFiles.length === 0){ bar.style.display='none'; return; }
  bar.style.display = 'block';
  items.innerHTML = '';
  attachedFiles.forEach((f,i) => {
    const div = document.createElement('div');
    div.className = 'attach-item';
    if(f.type==='photo'){
      div.innerHTML = `<img class="attach-thumb" src="${f.dataUrl}"><button class="attach-x" onclick="removeAttach(${i})">✕</button>`;
    } else {
      const icon = getFileIcon(f.name);
      const sz = (f.size/1024).toFixed(0)+'KB';
      div.innerHTML = `<div class="attach-file-chip">${icon}<span>${f.name.substring(0,18)}</span></div><button class="attach-x" onclick="removeAttach(${i})">✕</button>`;
    }
    items.appendChild(div);
  });
}

function removeAttach(i){
  attachedFiles.splice(i,1);
  renderAttachBar();
}

function getFileIcon(name){
  const ext = name.split('.').pop().toLowerCase();
  const map = {pdf:'📄',doc:'📝',docx:'📝',txt:'📃',csv:'📊',xlsx:'📊'};
  return map[ext] || '📎';
}

// ══════════════════════════
// SEND MESSAGE
// ══════════════════════════
async function sendMsg(){
  const input = document.getElementById('msgInput');
  const text  = input.value.trim();
  if((!text && attachedFiles.length===0) || isLoading) return;

  // Hide welcome
  document.getElementById('welcome')?.remove();

  // Build user message content for API
  let apiContent = [];
  let displayHtml = '';

  // Add attached images
  attachedFiles.forEach(f => {
    if(f.type==='photo'){
      apiContent.push({type:'image',source:{type:'base64',media_type:f.mediaType,data:f.base64}});
      displayHtml += `<img class="chat-img" src="${f.dataUrl}" alt="${f.name}">`;
    } else {
      // For non-image files, send as text description + base64 doc if PDF
      if(f.mediaType==='application/pdf'){
        apiContent.push({type:'document',source:{type:'base64',media_type:'application/pdf',data:f.base64}});
      } else {
        apiContent.push({type:'text',text:`[File attached: ${f.name}]`});
      }
      displayHtml += `<div class="file-preview"><span class="fp-icon">${getFileIcon(f.name)}</span><div><div class="fp-name">${f.name}</div><div class="fp-size">${(f.size/1024).toFixed(0)} KB</div></div></div>`;
    }
  });

  if(text) apiContent.push({type:'text',text});
  if(text) displayHtml += `<span>${escHtml(text)}</span>`;

  // Show user msg
  addRawMsg('user', displayHtml);
  messages.push({role:'user', content: apiContent.length===1 && apiContent[0].type==='text' ? text : apiContent});

  // Clear
  input.value='';
  autoResize(input);
  attachedFiles=[];
  renderAttachBar();

  // Loading
  const tid = showTyping();
  isLoading=true;
  document.getElementById('sendBtn').disabled=true;

  try{
    const res = await fetch('https://api.anthropic.com/v1/messages',{
      method:'POST',
      headers:{'Content-Type':'application/json'},
      body: JSON.stringify({
        model:'claude-sonnet-4-20250514',
        max_tokens:1024,
        system:SYSTEM,
        messages
      })
    });
    removeTyping(tid);
    if(!res.ok){
      const err=await res.json();
      addErrMsg(err.error?.message||'Kuch gadbad hui. Dobara try karo.');
      return;
    }
    const data=await res.json();
    const reply=data.content?.map(b=>b.text||'').join('')||'Koi jawab nahi mila.';
    messages.push({role:'assistant',content:reply});
    addAiMsg(reply);
  } catch(e){
    removeTyping(tid);
    addErrMsg('Network error. Internet check karein aur dobara try karein.');
  } finally{
    isLoading=false;
    document.getElementById('sendBtn').disabled=false;
    document.getElementById('msgInput').focus();
  }
}

// ══════════════════════════
// ADD MESSAGES
// ══════════════════════════
function addRawMsg(role, html){
  const chat=document.getElementById('chat');
  const time=now();
  const div=document.createElement('div');
  div.className=`msg ${role}`;
  const av = role==='ai'?'🤖':'😊';
  div.innerHTML=`<div class="m-av">${av}</div><div><div class="m-bub">${html}</div><div class="m-time">${time}</div></div>`;
  chat.appendChild(div);
  chat.scrollTop=chat.scrollHeight;
}

function addAiMsg(text){
  const chat=document.getElementById('chat');
  const time=now();
  const div=document.createElement('div');
  div.className='msg ai';
  const safe=btoa(unescape(encodeURIComponent(text)));
  div.innerHTML=`<div class="m-av">🤖</div><div><div class="m-bub">${formatText(text)}</div><button class="copy-btn" onclick="copyText(this,'${safe}')">📋 Copy</button><div class="m-time">${time}</div></div>`;
  chat.appendChild(div);
  chat.scrollTop=chat.scrollHeight;
}

function addErrMsg(msg){
  const chat=document.getElementById('chat');
  const div=document.createElement('div');
  div.className='msg ai';
  div.innerHTML=`<div class="m-av">🤖</div><div><div class="err-bub">❌ ${msg}</div></div>`;
  chat.appendChild(div);
  chat.scrollTop=chat.scrollHeight;
}

// ══════════════════════════
// VOICE INPUT
// ══════════════════════════
let recognition=null;
let isRecording=false;

function startVoice(){
  const SR=window.SpeechRecognition||window.webkitSpeechRecognition;
  if(!SR){ alert('Aapka browser voice support nahi karta. Chrome use karein!'); return; }

  recognition=new SR();
  recognition.lang='hi-IN';
  recognition.interimResults=true;
  recognition.continuous=false;

  recognition.onstart=()=>{
    isRecording=true;
    document.getElementById('voiceOverlay').classList.add('on');
    document.getElementById('voiceBtn').classList.add('recording');
    document.getElementById('voiceLive').textContent='Bol rahe ho...';
  };

  recognition.onresult=(e)=>{
    let interim='',final='';
    for(let i=e.resultIndex;i<e.results.length;i++){
      if(e.results[i].isFinal) final+=e.results[i][0].transcript;
      else interim+=e.results[i][0].transcript;
    }
    document.getElementById('voiceLive').textContent=interim||final||'...';
    if(final){
      document.getElementById('msgInput').value=final;
      autoResize(document.getElementById('msgInput'));
    }
  };

  recognition.onerror=(e)=>{
    stopVoice();
    if(e.error==='not-allowed') alert('Microphone permission do — browser settings mein jaao.');
    else alert('Voice error: '+e.error);
  };

  recognition.onend=()=>{
    stopVoice();
    // Auto send if text captured
    const txt=document.getElementById('msgInput').value.trim();
    if(txt) setTimeout(sendMsg,400);
  };

  recognition.start();
}

function stopVoice(){
  if(recognition) try{recognition.stop();}catch(e){}
  isRecording=false;
  document.getElementById('voiceOverlay').classList.remove('on');
  document.getElementById('voiceBtn').classList.remove('recording');
}

// ══════════════════════════
// HELPERS
// ══════════════════════════
function showTyping(){
  const chat=document.getElementById('chat');
  const div=document.createElement('div');
  const id='t'+Date.now();
  div.id=id;div.className='msg ai';
  div.innerHTML=`<div class="m-av">🤖</div><div class="m-bub" style="padding:0"><div class="typing"><span></span><span></span><span></span></div></div>`;
  chat.appendChild(div);chat.scrollTop=chat.scrollHeight;
  return id;
}
function removeTyping(id){document.getElementById(id)?.remove();}

function formatText(t){
  if(!t)return'';
  return t
    .replace(/```(\w*)\n?([\s\S]*?)```/g,(_,l,c)=>`<pre><code>${escHtml(c.trim())}</code></pre>`)
    .replace(/`([^`]+)`/g,'<code>$1</code>')
    .replace(/\*\*(.+?)\*\*/g,'<strong>$1</strong>')
    .replace(/\*(.+?)\*/g,'<em>$1</em>')
    .replace(/^### (.+)$/gm,'<h3>$1</h3>')
    .replace(/^- (.+)$/gm,'<li>$1</li>')
    .replace(/(<li>[\s\S]*?<\/li>\n?)+/g,s=>`<ul>${s}</ul>`)
    .replace(/\n\n/g,'</p><p>')
    .replace(/\n/g,'<br>');
}
function escHtml(t){return t.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');}
function now(){return new Date().toLocaleTimeString('en-IN',{hour:'2-digit',minute:'2-digit'});}
function handleKey(e){if(e.key==='Enter'&&!e.shiftKey){e.preventDefault();sendMsg();}}
function autoResize(el){el.style.height='auto';el.style.height=Math.min(el.scrollHeight,110)+'px';}
function quickAsk(q){document.getElementById('welcome')?.remove();document.getElementById('msgInput').value=q;sendMsg();}
function copyText(btn,encoded){
  const text=decodeURIComponent(escape(atob(encoded)));
  navigator.clipboard.writeText(text).then(()=>{btn.textContent='✅ Copied!';setTimeout(()=>btn.textContent='📋 Copy',2000);});
}

window.addEventListener('load',()=>document.getElementById('msgInput').focus());
</script>
</body>
</html>
