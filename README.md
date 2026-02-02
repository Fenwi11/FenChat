# Fenchat
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>FenChat</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

<!-- HEADER -->
<div class="header">
  <img src="logo.png" class="logo">
  <h2>FenChat</h2>
</div>

<!-- USERNAME -->
<div id="login">
  <input type="text" id="username" placeholder="Masukkan nama kamu">
  <button onclick="saveName()">Masuk</button>
</div>

<!-- CHAT -->
<div id="chat" class="hidden">
  <div id="messages"></div>
  <input id="messageInput" placeholder="Ketik pesan...">
  <button onclick="sendMessage()">Kirim</button>
</div>

<!-- STORY -->
<div id="story" class="hidden">
  <p>🚧 Story masih versi awal</p>
</div>

<!-- MENU BAWAH -->
<div class="menu">
  <button onclick="openChat()">Chat</button>
  <button onclick="openStory()">Story</button>
</div>

<script src="script.js"></script>
</body>
</html>

body {
  font-family: Arial;
  margin: 0;
  background: #f5f5f5;
}

.header {
  background: purple;
  color: white;
  padding: 10px;
  display: flex;
  align-items: center;
}

.logo {
  width: 40px;
  margin-right: 10px;
}

#messages {
  height: 60vh;
  overflow-y: auto;
  padding: 10px;
}

.menu {
  position: fixed;
  bottom: 0;
  width: 100%;
  display: flex;
}

.menu button {
  flex: 1;
  padding: 15px;
  border: none;
}

.hidden {
  display: none;
}

let name = "";

function saveName() {
  name = document.getElementById("username").value;
  if (name === "") return alert("Isi nama dulu");
  document.getElementById("login").style.display = "none";
  document.getElementById("chat").classList.remove("hidden");
}

function sendMessage() {
  let input = document.getElementById("messageInput");
  let msg = document.createElement("div");
  msg.innerText = name + ": " + input.value;
  document.getElementById("messages").appendChild(msg);
  input.value = "";
}

function openChat() {
  document.getElementById("chat").classList.remove("hidden");
  document.getElementById("story").classList.add("hidden");
}

function openStory() {
  document.getElementById("story").classList.remove("hidden");
  document.getElementById("chat").classList.add("hidden");
}
