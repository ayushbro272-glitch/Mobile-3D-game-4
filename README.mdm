<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<meta name="theme-color" content="#0072ff">
<title>कोडिंग लवर</title>
<style>
*{margin:0;padding:0;box-sizing:border-box;-webkit-tap-highlight-color:transparent}
body{font-family:-apple-system,'Segoe UI',Roboto,Arial,sans-serif;background:linear-gradient(135deg,#0f2027 0%,#203a43 50%,#2c5364 100%);color:#fff;height:100vh;display:flex;flex-direction:column;overflow:hidden;position:fixed;width:100%}
.header{padding:10px 12px;background:linear-gradient(90deg,#00c6ff 0%,#0072ff 100%);display:flex;justify-content:space-between;align-items:center;box-shadow:0 4px 20px rgba(0,0,0,.4);z-index:10;flex-shrink:0;gap:6px}
.header h1{font-size:1em;font-weight:700;flex:1;text-align:center;overflow:hidden;white-space:nowrap;text-overflow:ellipsis}
.icon-btn{background:rgba(255,255,255,.2);border:none;color:#fff;width:36px;height:36px;border-radius:8px;font-size:1em;cursor:pointer;display:flex;align-items:center;justify-content:center;flex-shrink:0}
.icon-btn:active{background:rgba(255,255,255,.35)}
.icon-btn.active{background:rgba(39,174,96,.8)}
.sidebar{position:fixed;top:0;left:-280px;width:280px;height:100vh;background:#16213e;z-index:200;transition:left .3s ease;display:flex;flex-direction:column;box-shadow:4px 0 20px rgba(0,0,0,.5)}
.sidebar.open{left:0}
.sidebar-header{padding:16px;background:linear-gradient(90deg,#00c6ff,#0072ff);display:flex;justify-content:space-between;align-items:center}
.sidebar-header h2{font-size:1.1em}
.close-sidebar{background:transparent;border:none;color:#fff;font-size:1.4em;cursor:pointer;padding:4px 8px}
.sidebar-new{padding:12px 16px}
.sidebar-new button{width:100%;padding:12px;background:linear-gradient(90deg,#00c6ff,#0072ff);color:#fff;border:none;border-radius:10px;font-size:.95em;font-weight:600;cursor:pointer}
.sessions-list{flex:1;overflow-y:auto;padding:8px 12px}
.session-item{padding:12px 14px;margin-bottom:8px;background:rgba(255,255,255,.05);border-radius:10px;cursor:pointer;font-size:.9em;display:flex;justify-content:space-between;align-items:center;gap:8px;border-left:3px solid transparent}
.session-item:hover,.session-item.active{background:rgba(0,198,255,.15);border-left-color:#00c6ff}
.session-item .title{flex:1;overflow:hidden;white-space:nowrap;text-overflow:ellipsis}
.session-item .delete-btn{background:transparent;border:none;color:rgba(255,255,255,.5);font-size:1em;cursor:pointer;padding:2px 6px}
.overlay{display:none;position:fixed;inset:0;background:rgba(0,0,0,.6);z-index:150}
.overlay.open{display:block}
.brains-bar{display:flex;gap:6px;padding:8px 12px;background:rgba(0,0,0,.3);overflow-x:auto;scrollbar-width:none;flex-shrink:0}
.brains-bar::-webkit-scrollbar{display:none}
.brain-chip{padding:6px 12px;background:rgba(255,255,255,.08);border:1px solid rgba(255,255,255,.15);border-radius:20px;font-size:.8em;white-space:nowrap;color:#fff;cursor:pointer;transition:all .2s}
.brain-chip.active{background:linear-gradient(90deg,#00c6ff,#0072ff);border-color:transparent}
.messages{flex:1;overflow-y:auto;padding:16px;display:flex;flex-direction:column;gap:14px;-webkit-overflow-scrolling:touch}
.message{max-width:88%;padding:12px 16px;border-radius:16px;line-height:1.6;word-wrap:break-word;font-size:.95em;animation:slideIn .3s ease;position:relative}
@keyframes slideIn{from{opacity:0;transform:translateY(10px)}to{opacity:1;transform:translateY(0)}}
.message.user{align-self:flex-end;background:linear-gradient(135deg,#00c6ff,#0072ff);border-bottom-right-radius:4px}
.message.assistant{align-self:flex-start;background:rgba(255,255,255,.08);border-left:3px solid #00c6ff;border-bottom-left-radius:4px;padding-right:44px}
.message pre{background:#0a0a15;padding:10px;border-radius:8px;margin:8px 0;overflow-x:auto;font-size:.85em;font-family:'Consolas',monospace}
.message code{background:rgba(0,0,0,.4);padding:2px 6px;border-radius:4px;font-size:.9em;font-family:'Consolas',monospace}
.message img,.message video{max-width:100%;border-radius:10px;margin-top:8px;max-height:300px}
.brain-tag{display:inline-block;font-size:.7em;padding:2px 8px;background:rgba(0,198,255,.2);border-radius:10px;margin-bottom:6px;color:#00c6ff}
.speak-btn{position:absolute;bottom:8px;right:8px;background:rgba(0,198,255,.2);border:none;color:#00c6ff;width:32px;height:32px;border-radius:50%;cursor:pointer;font-size:.9em;display:flex;align-items:center;justify-content:center}
.speak-btn:active{background:rgba(0,198,255,.4)}
.speak-btn.speaking{background:#00c6ff;color:#fff;animation:pulse 1s infinite}
@keyframes pulse{0%,100%{opacity:1}50%{opacity:.6}}
.file-preview{padding:8px 12px;background:rgba(0,198,255,.1);border-top:1px solid rgba(0,198,255,.3);display:none;flex-shrink:0}
.file-preview.show{display:block}
.file-info{display:flex;align-items:center;gap:10px;font-size:.85em}
.file-icon{font-size:1.8em}
.file-details{flex:1;overflow:hidden}
.file-name{font-weight:600;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.file-size{font-size:.75em;color:rgba(255,255,255,.6);margin-top:2px}
.file-remove{background:rgba(231,76,60,.3);border:none;color:#fff;padding:6px 10px;border-radius:6px;cursor:pointer;font-size:.9em}
.file-thumb{width:50px;height:50px;border-radius:6px;object-fit:cover}
.input-area{padding:10px 12px 14px;background:rgba(0,0,0,.4);border-top:1px solid rgba(255,255,255,.1);flex-shrink:0}
.lang-row{display:flex;gap:6px;margin-bottom:8px;overflow-x:auto;scrollbar-width:none;padding-bottom:2px}
.lang-row::-webkit-scrollbar{display:none}
.lang-chip{padding:4px 10px;background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.12);border-radius:14px;font-size:.75em;white-space:nowrap;color:#fff;cursor:pointer}
.lang-chip.active{background:linear-gradient(90deg,#00c6ff,#0072ff);border-color:transparent}
.input-row{display:flex;gap:8px;align-items:flex-end}
textarea{flex:1;padding:12px 16px;background:rgba(255,255,255,.08);border:1px solid rgba(255,255,255,.15);border-radius:22px;color:#fff;font-family:inherit;font-size:.95em;resize:none;min-height:46px;max-height:120px;line-height:1.4}
textarea:focus{outline:none;border-color:#00c6ff}
textarea::placeholder{color:rgba(255,255,255,.4)}
.attach-btn,.mic-btn,.send-btn{width:46px;height:46px;border:none;border-radius:50%;font-size:1.2em;cursor:pointer;display:flex;align-items:center;justify-content:center;flex-shrink:0;color:#fff}
.attach-btn{background:rgba(255,255,255,.1)}
.attach-btn.has-file{background:#27ae60}
.mic-btn{background:rgba(255,255,255,.1)}
.mic-btn.recording{background:#e74c3c;animation:pulse 1s infinite}
.send-btn{background:linear-gradient(135deg,#00c6ff,#0072ff)}
.send-btn:disabled{opacity:.4}
.typing-dot{display:inline-block;width:6px;height:6px;margin:0 2px;background:#00c6ff;border-radius:50%;animation:blink 1.4s infinite}
.typing-dot:nth-child(2){animation-delay:.2s}
.typing-dot:nth-child(3){animation-delay:.4s}
@keyframes blink{0%,60%,100%{opacity:.3;transform:translateY(0)}30%{opacity:1;transform:translateY(-4px)}}
.modal{display:none;position:fixed;inset:0;background:rgba(0,0,0,.85);z-index:300;padding:20px;overflow-y:auto}
.modal.open{display:block}
.modal-content{max-width:500px;margin:20px auto;background:#1a1a2e;border-radius:16px;padding:24px;border:1px solid rgba(0,198,255,.3)}
.modal h2{color:#00c6ff;margin-bottom:8px;font-size:1.3em}
.modal p{color:rgba(255,255,255,.7);font-size:.85em;margin-bottom:16px;line-height:1.5}
.modal label{display:block;color:#00c6ff;font-size:.85em;margin:14px 0 6px;font-weight:600}
.modal input{width:100%;padding:10px 14px;background:rgba(255,255,255,.08);border:1px solid rgba(255,255,255,.15);border-radius:8px;color:#fff;font-size:.9em;font-family:monospace}
.modal input:focus{outline:none;border-color:#00c6ff}
.modal .hint{font-size:.75em;color:rgba(255,255,255,.5);margin-top:4px}
.modal .hint a{color:#00c6ff;text-decoration:none}
.modal-buttons{display:flex;gap:10px;margin-top:22px}
.modal-buttons button{flex:1;padding:12px;border:none;border-radius:10px;font-size:.95em;font-weight:600;cursor:pointer}
.btn-primary{background:linear-gradient(135deg,#00c6ff,#0072ff);color:#fff}
.btn-secondary{background:rgba(255,255,255,.1);color:#fff}
.welcome{text-align:center;padding:20px;color:rgba(255,255,255,.7)}
.welcome h2{color:#00c6ff;margin-bottom:10px;font-size:1.4em}
.welcome .examples{display:grid;gap:8px;margin-top:20px;text-align:left}
.example{padding:12px 16px;background:rgba(255,255,255,.05);border:1px solid rgba(255,255,255,.1);border-radius:10px;font-size:.85em;cursor:pointer}
</style>
</head>
<body>

<div class="header">
<button class="icon-btn" onclick="toggleSidebar()">☰</button>
<h1 id="chatTitle">⚡ कोडिंग लवर</h1>
<button class="icon-btn" onclick="newChat()">➕</button>
<button class="icon-btn" id="autoSpeakBtn" onclick="toggleAutoSpeak()">🔊</button>
<button class="icon-btn" onclick="openSettings()">⚙️</button>
</div>

<div class="overlay" id="overlay" onclick="toggleSidebar()"></div>

<div class="sidebar" id="sidebar">
<div class="sidebar-header">
<h2>💬 बातचीत</h2>
<button class="close-sidebar" onclick="toggleSidebar()">✕</button>
</div>
<div class="sidebar-new">
<button onclick="newChat()">➕ नई बातचीत</button>
</div>
<div class="sessions-list" id="sessionsList"></div>
</div>

<div class="brains-bar">
<div class="brain-chip active" data-brain="auto">🤖 ऑटो</div>
<div class="brain-chip" data-brain="code">💻 कोड</div>
<div class="brain-chip" data-brain="reason">🧠 सोच</div>
<div class="brain-chip" data-brain="gemini">🔍 खोज</div>
<div class="brain-chip" data-brain="image">🎨 इमेज</div>
<div class="brain-chip" data-brain="groq">⚡ तेज़</div>
<div class="brain-chip" data-brain="vision">👁️ देखो</div>
</div>

<div class="messages" id="messages">
<div class="welcome">
<h2>नमस्ते! मैं कोडिंग लवर हूँ 💻</h2>
<p>बोलो, लिखो, फ़ोटो भेजो, वीडियो भेजो, फ़ाइल भेजो — सब समझूँगा।</p>
<div class="examples">
<div class="example" onclick="useExample(this)">पाइथन में फ़ाइबोनैचि लिखो</div>
<div class="example" onclick="useExample(this)">2x + 5 = 15, x क्या है?</div>
<div class="example" onclick="useExample(this)">आज का मौसम बताओ</div>
</div>
</div>
</div>

<div class="file-preview" id="filePreview">
<div class="file-info">
<div id="fileIcon" class="file-icon">📄</div>
<img id="fileThumb" class="file-thumb" style="display:none">
<div class="file-details">
<div class="file-name" id="fileName">file</div>
<div class="file-size" id="fileSize">0 KB</div>
</div>
<button class="file-remove" onclick="removeFile()">✕</button>
</div>
</div>

<div class="input-area">
<div class="lang-row" id="langRow">
<div class="lang-chip active" data-lang="hi-IN">हिंदी</div>
<div class="lang-chip" data-lang="en-US">English</div>
<div class="lang-chip" data-lang="en-IN">English (India)</div>
<div class="lang-chip" data-lang="bn-IN">বাংলা</div>
<div class="lang-chip" data-lang="ta-IN">தமிழ்</div>
<div class="lang-chip" data-lang="te-IN">తెలుగు</div>
<div class="lang-chip" data-lang="mr-IN">मराठी</div>
<div class="lang-chip" data-lang="gu-IN">ગુજરાતી</div>
<div class="lang-chip" data-lang="kn-IN">ಕನ್ನಡ</div>
<div class="lang-chip" data-lang="ml-IN">മലയാളം</div>
<div class="lang-chip" data-lang="pa-IN">ਪੰਜਾਬੀ</div>
<div class="lang-chip" data-lang="ur-IN">اردو</div>
<div class="lang-chip" data-lang="es-ES">Español</div>
<div class="lang-chip" data-lang="fr-FR">Français</div>
<div class="lang-chip" data-lang="de-DE">Deutsch</div>
<div class="lang-chip" data-lang="ja-JP">日本語</div>
<div class="lang-chip" data-lang="ko-KR">한국어</div>
<div class="lang-chip" data-lang="zh-CN">中文</div>
<div class="lang-chip" data-lang="ar-SA">العربية</div>
<div class="lang-chip" data-lang="ru-RU">Русский</div>
</div>
<div class="input-row">
<input type="file" id="fileInput" style="display:none" accept="image/*,video/*,audio/*,.pdf,.txt,.doc,.docx,.csv,.json,.py,.js,.java,.cpp,.html,.css,.xml,.md" onchange="handleFileSelect(event)">
<button class="attach-btn" id="attachBtn" onclick="document.getElementById('fileInput').click()">📎</button>
<textarea id="input" placeholder="कुछ भी पूछो..." rows="1"></textarea>
<button class="mic-btn" id="micBtn" onclick="toggleMic()">🎤</button>
<button class="send-btn" id="sendBtn" onclick="sendMessage()">➤</button>
</div>
</div>

<div class="modal" id="settingsModal">
<div class="modal-content">
<h2>⚙️ सेटिंग्स</h2>
<p>सिर्फ़ दो मुफ़्त चाबियाँ। कोई कार्ड नहीं, कोई बिल नहीं।</p>
<label>⚡ ग्रोक API Key</label>
<input type="password" id="groqKey" placeholder="gsk_...">
<div class="hint">मुफ़्त: <a href="https://console.groq.com" target="_blank">console.groq.com</a></div>
<label>🔍 जेमिनी API Key</label>
<input type="password" id="geminiKey" placeholder="AIza...">
<div class="hint">मुफ़्त: <a href="https://aistudio.google.com/apikey" target="_blank">aistudio.google.com</a></div>
<div class="modal-buttons">
<button class="btn-secondary" onclick="closeSettings()">रद्द</button>
<button class="btn-primary" onclick="saveSettings()">सहेजो</button>
</div>
</div>
</div>

<script>
var STORAGE_KEY = "coding_lover_v4";
var CHATS_KEY = "coding_lover_chats_v1";
var currentBrain = "auto";
var currentLang = "hi-IN";
var messagesEl = document.getElementById("messages");
var currentChatId = null;
var allChats = {};
var recognition = null;
var isRecording = false;
var autoSpeak = false;
var currentUtterance = null;
var attachedFile = null;

function loadKeys() {
    try {
        var saved = localStorage.getItem(STORAGE_KEY);
        if (saved) return JSON.parse(saved);
    } catch(e) {}
    return { groq: "", gemini: "" };
}
function saveKeysToStorage(keys) {
    try { localStorage.setItem(STORAGE_KEY, JSON.stringify(keys)); } catch(e) {}
}
function openSettings() {
    var keys = loadKeys();
    document.getElementById("groqKey").value = keys.groq || "";
    document.getElementById("geminiKey").value = keys.gemini || "";
    document.getElementById("settingsModal").classList.add("open");
}
function closeSettings() { document.getElementById("settingsModal").classList.remove("open"); }
function saveSettings() {
    var keys = {
        groq: document.getElementById("groqKey").value.trim(),
        gemini: document.getElementById("geminiKey").value.trim()
    };
    saveKeysToStorage(keys);
    closeSettings();
    addMessage("assistant", "✅ चाबियाँ सहेज लीं!");
}

function loadChats() {
    try {
        var saved = localStorage.getItem(CHATS_KEY);
        if (saved) allChats = JSON.parse(saved);
    } catch(e) { allChats = {}; }
}
function saveChats() {
    try { localStorage.setItem(CHATS_KEY, JSON.stringify(allChats)); } catch(e) {}
}
function createNewChat() {
    var id = "chat_" + Date.now();
    allChats[id] = { id: id, title: "नई बातचीत", messages: [], created: Date.now() };
    saveChats();
    return id;
}
function renderSessions() {
    var list = document.getElementById("sessionsList");
    list.innerHTML = "";
    var ids = Object.keys(allChats).sort(function(a,b){ return allChats[b].created - allChats[a].created; });
    if (ids.length === 0) {
        list.innerHTML = '<div style="text-align:center;color:rgba(255,255,255,.4);padding:20px;font-size:.85em;">अभी कोई बातचीत नहीं</div>';
        return;
    }
    ids.forEach(function(id) {
        var chat = allChats[id];
        var el = document.createElement("div");
        el.className = "session-item" + (id === currentChatId ? " active" : "");
        el.innerHTML = '<span class="title">💬 ' + (chat.title || "बातचीत") + '</span><button class="delete-btn" onclick="deleteChat(event, \'' + id + '\')">🗑️</button>';
        el.onclick = function(e) { if (!e.target.classList.contains("delete-btn")) openChat(id); };
        list.appendChild(el);
    });
}
function deleteChat(e, id) {
    e.stopPropagation();
    if (!confirm("यह बातचीत मिटानी है?")) return;
    delete allChats[id];
    saveChats();
    if (currentChatId === id) newChat();
    else renderSessions();
}
function openChat(id) {
    currentChatId = id;
    var chat = allChats[id];
    if (!chat) return;
    messagesEl.innerHTML = "";
    chat.messages.forEach(function(m) {
        addMessage(m.role, m.content, m.brain, true);
    });
    document.getElementById("chatTitle").textContent = "💬 " + (chat.title || "बातचीत");
    toggleSidebar();
    renderSessions();
}
function saveMessageToChat(role, content, brain) {
    if (!currentChatId) return;
    var chat = allChats[currentChatId];
    if (!chat) return;
    chat.messages.push({ role: role, content: content, brain: brain, time: Date.now() });
    if (chat.title === "नई बातचीत" && role === "user") {
        chat.title = content.substring(0, 30).replace(/\n/g, " ") + (content.length > 30 ? "..." : "");
        document.getElementById("chatTitle").textContent = "💬 " + chat.title;
    }
    saveChats();
    renderSessions();
}
function newChat() {
    currentChatId = createNewChat();
    messagesEl.innerHTML = '<div class="welcome"><h2>नमस्ते! नई बातचीत 💬</h2><p>कुछ भी पूछो, फ़ोटो/वीडियो/फ़ाइल भेजो।</p></div>';
    document.getElementById("chatTitle").textContent = "⚡ कोडिंग लवर";
    removeFile();
    renderSessions();
    if (document.getElementById("sidebar").classList.contains("open")) toggleSidebar();
}
function toggleSidebar() {
    document.getElementById("sidebar").classList.toggle("open");
    document.getElementById("overlay").classList.toggle("open");
}

var chips = document.querySelectorAll(".brain-chip");
for (var i = 0; i < chips.length; i++) {
    chips[i].addEventListener("click", function() {
        var all = document.querySelectorAll(".brain-chip");
        for (var j = 0; j < all.length; j++) all[j].classList.remove("active");
        this.classList.add("active");
        currentBrain = this.getAttribute("data-brain");
    });
}

var langChips = document.querySelectorAll(".lang-chip");
for (var i = 0; i < langChips.length; i++) {
    langChips[i].addEventListener("click", function() {
        var all = document.querySelectorAll(".lang-chip");
        for (var j = 0; j < all.length; j++) all[j].classList.remove("active");
        this.classList.add("active");
        currentLang = this.getAttribute("data-lang");
    });
}

// ============ फ़ाइल अपलोड ============
function handleFileSelect(event) {
    var file = event.target.files[0];
    if (!file) return;
    if (file.size > 20 * 1024 * 1024) {
        alert("फ़ाइल 20 MB से बड़ी है। छोटी फ़ाइल भेजो।");
        return;
    }
    attachedFile = file;
    var btn = document.getElementById("attachBtn");
    btn.classList.add("has-file");
    document.getElementById("filePreview").classList.add("show");
    document.getElementById("fileName").textContent = file.name;
    document.getElementById("fileSize").textContent = formatSize(file.size);

    var icon = "📄";
    if (file.type.startsWith("image/")) icon = "🖼️";
    else if (file.type.startsWith("video/")) icon = "🎬";
    else if (file.type.startsWith("audio/")) icon = "🎵";
    else if (file.name.endsWith(".pdf")) icon = "📕";
    else if (/\.(py|js|java|cpp|c|html|css|json|xml)$/.test(file.name)) icon = "💻";
    else if (/\.(txt|md|csv)$/.test(file.name)) icon = "📝";
    document.getElementById("fileIcon").textContent = icon;

    if (file.type.startsWith("image/")) {
        var reader = new FileReader();
        reader.onload = function(e) {
            var thumb = document.getElementById("fileThumb");
            thumb.src = e.target.result;
            thumb.style.display = "block";
        };
        reader.readAsDataURL(file);
    } else {
        document.getElementById("fileThumb").style.display = "none";
    }
}

function formatSize(bytes) {
    if (bytes < 1024) return bytes + " B";
    if (bytes < 1024 * 1024) return (bytes / 1024).toFixed(1) + " KB";
    return (bytes / (1024 * 1024)).toFixed(1) + " MB";
}

function removeFile() {
    attachedFile = null;
    document.getElementById("attachBtn").classList.remove("has-file");
    document.getElementById("filePreview").classList.remove("show");
    document.getElementById("fileInput").value = "";
    document.getElementById("fileThumb").style.display = "none";
}

function fileToBase64(file) {
    return new Promise(function(resolve, reject) {
        var reader = new FileReader();
        reader.onload = function() { resolve(reader.result.split(",")[1]); };
        reader.onerror = reject;
        reader.readAsDataURL(file);
    });
}

function fileToText(file) {
    return new Promise(function(resolve, reject) {
        var reader = new FileReader();
        reader.onload = function() { resolve(reader.result); };
        reader.onerror = reject;
        reader.readAsText(file);
    });
}

// ============ आवाज़ ============
function initRecognition() {
    var SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;
    if (!SpeechRecognition) {
        alert("तुम्हारा ब्राउज़र आवाज़ नहीं पहचानता। क्रोम इस्तेमाल करो।");
        return null;
    }
    var rec = new SpeechRecognition();
    rec.continuous = false;
    rec.interimResults = true;
    rec.lang = currentLang;
    rec.onstart = function() {
        isRecording = true;
        document.getElementById("micBtn").classList.add("recording");
        document.getElementById("micBtn").textContent = "⏹";
    };
    rec.onresult = function(event) {
        var transcript = "";
        for (var i = event.resultIndex; i < event.results.length; i++) {
            transcript += event.results[i][0].transcript;
        }
        document.getElementById("input").value = transcript;
    };
    rec.onerror = function(e) { stopMic(); };
    rec.onend = function() {
        stopMic();
        var txt = document.getElementById("input").value.trim();
        if (txt) sendMessage();
    };
    return rec;
}
function toggleMic() {
    if (isRecording) {
        if (recognition) recognition.stop();
        stopMic();
        return;
    }
    recognition = initRecognition();
    if (!recognition) return;
    recognition.lang = currentLang;
    try { recognition.start(); } catch(e) { stopMic(); }
}
function stopMic() {
    isRecording = false;
    var btn = document.getElementById("micBtn");
    btn.classList.remove("recording");
    btn.textContent = "🎤";
}

function speakText(text, btn) {
    if (!window.speechSynthesis) return;
    if (currentUtterance && speechSynthesis.speaking) {
        speechSynthesis.cancel();
        if (btn) btn.classList.remove("speaking");
        currentUtterance = null;
        return;
    }
    var clean = text.replace(/```[\s\S]*?```/g, " कोड ब्लॉक ")
                    .replace(/`([^`]+)`/g, "$1")
                    .replace(/[#*_>]/g, "")
                    .replace(/<[^>]+>/g, "")
                    .replace(/\n+/g, "। ");
    var utter = new SpeechSynthesisUtterance(clean);
    utter.lang = currentLang;
    utter.rate = 1;
    utter.onend = function() {
        if (btn) btn.classList.remove("speaking");
        currentUtterance = null;
    };
    currentUtterance = utter;
    if (btn) btn.classList.add("speaking");
    speechSynthesis.speak(utter);
}
function toggleAutoSpeak() {
    autoSpeak = !autoSpeak;
    document.getElementById("autoSpeakBtn").classList.toggle("active", autoSpeak);
    addMessage("assistant", autoSpeak ? "🔊 हर जवाब बोलकर सुनाया जाएगा" : "🔇 बोलना बंद");
}

// ============ संदेश ============
function addMessage(role, content, brainName, skipSave) {
    var welcome = document.querySelector(".welcome");
    if (welcome) welcome.remove();
    var el = document.createElement("div");
    el.className = "message " + role;
    var html = "";
    if (brainName && role === "assistant") {
        html += '<span class="brain-tag">' + brainName + '</span><br>';
    }
    html += formatMessage(content);
    if (role === "assistant" && content && content.indexOf("<img") !== 0) {
        html += '<button class="speak-btn" onclick="speakText(this.getAttribute(\'data-text\'), this)" data-text="' + escapeAttr(content) + '">🔊</button>';
    }
    el.innerHTML = html;
    messagesEl.appendChild(el);
    messagesEl.scrollTop = messagesEl.scrollHeight;
    if (!skipSave) saveMessageToChat(role, content, brainName);
    if (role === "assistant" && autoSpeak && content && content.indexOf("<img") !== 0) {
        setTimeout(function() { speakText(content, null); }, 300);
    }
    return el;
}
function escapeAttr(s) {
    return String(s).replace(/&/g,"&amp;").replace(/"/g,"&quot;").replace(/'/g,"&#39;").replace(/</g,"&lt;").replace(/>/g,"&gt;");
}
function formatMessage(text) {
    if (!text) return "";
    if (text.indexOf("<img") === 0 || text.indexOf("<video") === 0) return text;
    var s = text.replace(/&/g, "&amp;").replace(/</g, "&lt;").replace(/>/g, "&gt;");
    s = s.replace(/```(\w+)?\n?([\s\S]*?)```/g, function(m, lang, code) {
        return '<pre><code>' + code + '</code></pre>';
    });
    s = s.replace(/`([^`]+)`/g, "<code>$1</code>");
    s = s.replace(/\n/g, "<br>");
    return s;
}
function addTyping() {
    var welcome = document.querySelector(".welcome");
    if (welcome) welcome.remove();
    var el = document.createElement("div");
    el.className = "message assistant";
    el.id = "typingIndicator";
    el.innerHTML = '<span class="typing-dot"></span><span class="typing-dot"></span><span class="typing-dot"></span>';
    messagesEl.appendChild(el);
    messagesEl.scrollTop = messagesEl.scrollHeight;
}
function removeTyping() {
    var el = document.getElementById("typingIndicator");
    if (el) el.remove();
}

function detectBrain(text, hasFile) {
    if (currentBrain !== "auto") return currentBrain;
    if (hasFile) return "vision";
    var t = text.toLowerCase();
    if (/(tasveer|image|photo|chitra|तस्वीर|चित्र|फोटो|picture|draw|banao)/.test(t) && !/dekh|देख/.test(t)) return "image";
    if (/(\d+\s*[\+\-\*\/\^=]\s*\d+|x\s*=|समीकरण|equation|solve|हल करो|गणित|math|logic|तर्क|puzzle|पहेली)/.test(t)) return "reason";
    if (/(aaj|आज|ताज़ा|latest|news|खबर|मौसम|weather|price|कीमत|who is|कौन है|kab|कब|kahan|कहाँ|search|खोजो|dhundo)/.test(t)) return "gemini";
    if (/(code|कोड|program|प्रोग्राम|function|फंक्शन|likho|लिखो|debug|error|त्रुटि|fix|ठीक|python|javascript|java|cpp|html|css|react|node|sql|api)/.test(t)) return "code";
    return "groq";
}

async function callGroq(text, keys, model, systemPrompt) {
    if (!keys.groq) throw new Error("ग्रोक चाबी नहीं है।");
    var resp = await fetch("https://api.groq.com/openai/v1/chat/completions", {
        method: "POST",
        headers: { "Content-Type": "application/json", "Authorization": "Bearer " + keys.groq },
        body: JSON.stringify({
            model: model,
            messages: [
                { role: "system", content: systemPrompt },
                { role: "user", content: text }
            ],
            temperature: 0.3,
            max_tokens: 8000
        })
    });
    if (!resp.ok) throw new Error("ग्रोक त्रुटि " + resp.status);
    var data = await resp.json();
    return data.choices[0].message.content;
}

async function callGemini(text, keys) {
    if (!keys.gemini) throw new Error("जेमिनी चाबी नहीं है।");
    var url = "https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash-exp:generateContent?key=" + keys.gemini;
    var resp = await fetch(url, {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({
            contents: [{ parts: [{ text: "तुम कोडिंग लवर हो। हिंदी में जवाब दो।\n\n" + text }] }]
        })
    });
    if (!resp.ok) throw new Error("जेमिनी त्रुटि: " + resp.status);
    var data = await resp.json();
    return data.candidates[0].content.parts[0].text;
}

async function callImage(text, keys) {
    if (!keys.gemini) throw new Error("जेमिनी चाबी नहीं है।");
    var url = "https://generativelanguage.googleapis.com/v1beta/models/imagen-3.0-generate-001:predict?key=" + keys.gemini;
    var resp = await fetch(url, {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({
            instances: [{ prompt: text }],
            parameters: { sampleCount: 1, aspectRatio: "1:1" }
        })
    });
    if (!resp.ok) throw new Error("इमेज त्रुटि: " + resp.status);
    var data = await resp.json();
    var b64 = data.predictions[0].bytesBase64Encoded;
    return '<img src="data:image/png;base64,' + b64 + '" alt="तस्वीर">';
}

// ============ फ़ाइल/फ़ोटो/वीडियो देखना (Vision) ============
async function callVision(file, userText, keys) {
    if (!keys.gemini) throw new Error("जेमिनी चाबी नहीं है (फ़ाइल देखने के लिए ज़रूरी)।");
    var prompt = userText || "इस फ़ाइल में क्या है? विस्तार से हिंदी में बताओ।";

    var parts = [];
    var mimeType = file.type || "application/octet-stream";

    // टेक्स्ट फ़ाइल सीधे पढ़ो
    if (mimeType.startsWith("text/") || /\.(txt|md|csv|json|xml|py|js|java|cpp|c|html|css|log)$/.test(file.name)) {
        var textContent = await fileToText(file);
        if (textContent.length > 100000) textContent = textContent.substring(0, 100000) + "\n...(बाक़ी काट दिया)";
        parts.push({ text: "फ़ाइल: " + file.name + "\n\n```\n" + textContent + "\n```\n\n" + prompt });
    } else {
        // इमेज/वीडियो/ऑडियो/PDF → base64
        var b64 = await fileToBase64(file);
        parts.push({ text: prompt });
        parts.push({ inline_data: { mime_type: mimeType, data: b64 } });
    }

    var url = "https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash-exp:generateContent?key=" + keys.gemini;
    var resp = await fetch(url, {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({
            contents: [{ parts: parts }],
            systemInstruction: { parts: [{ text: "तुम कोडिंग लवर हो। हिंदी में विस्तार से बताओ। जो दिख रहा है या पढ़ा है, वह साफ़-साफ़ समझाओ।" }] }
        })
    });
    if (!resp.ok) {
        var errText = await resp.text();
        throw new Error("त्रुटि " + resp.status + ": " + errText.substring(0, 200));
    }
    var data = await resp.json();
    return data.candidates[0].content.parts[0].text;
}

// ============ भेजो ============
async function sendMessage() {
    var input = document.getElementById("input");
    var text = input.value.trim();
    var file = attachedFile;

    if (!text && !file) return;
    if (!currentChatId) currentChatId = createNewChat();

    var keys = loadKeys();
    var brain = detectBrain(text, !!file);

    input.value = "";
    input.style.height = "auto";

    // उपयोगकर्ता का संदेश दिखाओ
    var userDisplay = text || "";
    if (file) {
        var icon = "📎";
        if (file.type.startsWith("image/")) icon = "🖼️";
        else if (file.type.startsWith("video/")) icon = "🎬";
        else if (file.type.startsWith("audio/")) icon = "🎵";
        userDisplay = icon + " " + file.name + (text ? "\n\n" + text : "");
    }
    addMessage("user", userDisplay);
    addTyping();

    var btn = document.getElementById("sendBtn");
    btn.disabled = true;

    var brainNames = {
        code: "💻 क़्वेन कोडर",
        reason: "🧠 क़्वेन सोच",
        gemini: "🔍 जेमिनी",
        groq: "⚡ लामा",
        image: "🎨 इमेजन",
        vision: "👁️ जेमिनी विज़न"
    };

    try {
        var result;
        if (file) {
            // फ़ाइल भेजी है → विज़न
            result = await callVision(file, text, keys);
            removeFile();
        } else if (brain === "code") {
            result = await callGroq(text, keys, "qwen-2.5-coder-32b",
                "तुम कोडिंग लवर हो। हिंदी में जवाब दो। पूरा कोड लिखो।");
        } else if (brain === "reason") {
            result = await callGroq(text, keys, "qwen-qwq-32b",
                "तुम गणित और तर्क के विशेषज्ञ हो। चरण-दर-चरण हल करो। हिंदी में।");
        } else if (brain === "gemini") {
            result = await callGemini(text, keys);
        } else if (brain === "image") {
            result = await callImage(text, keys);
        } else {
            result = await callGroq(text, keys, "llama-3.3-70b-versatile",
                "तुम कोडिंग लवर हो। हिंदी में छोटा और तेज़ जवाब दो।");
        }

        removeTyping();
        addMessage("assistant", result, brainNames[brain]);
    } catch (e) {
        removeTyping();
        addMessage("assistant", "❌ त्रुटि: " + e.message, "त्रुटि");
    } finally {
        btn.disabled = false;
    }
}

function useExample(el) {
    document.getElementById("input").value = el.textContent;
    sendMessage();
}

var inputEl = document.getElementById("input");
inputEl.addEventListener("input", function() {
    this.style.height = "auto";
    this.style.height = Math.min(this.scrollHeight, 120) + "px";
});
inputEl.addEventListener("keydown", function(e) {
    if (e.key === "Enter" && !e.shiftKey) {
        e.preventDefault();
        sendMessage();
    }
});

loadChats();
if (Object.keys(allChats).length === 0) newChat();
else { renderSessions(); }

var keys = loadKeys();
if (!keys.groq || !keys.gemini) {
    setTimeout(openSettings, 600);
}
</script>

</body>
</html>
