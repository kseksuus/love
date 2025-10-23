<!DOCTYPE html>
<html lang="uk">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Love Message 💌</title>
  <style>
    body {
      margin: 0;
      height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      background: linear-gradient(to bottom, #ffe6ec, #ffd6e0);
      font-family: "Poppins", sans-serif;
      overflow: hidden;
    }

    .card {
      background: rgba(255, 255, 255, 0.8);
      border-radius: 20px;
      padding: 40px;
      width: 320px;
      text-align: center;
      box-shadow: 0 10px 30px rgba(255, 0, 100, 0.1);
      position: relative;
    }

    .icon {
      font-size: 50px;
      background: #ffdbe8;
      width: 80px;
      height: 80px;
      line-height: 80px;
      border-radius: 50%;
      margin: 0 auto 10px;
    }

    h2 {
      margin: 5px 0;
      color: #b1005a;
    }

    p {
      color: #444;
      font-size: 14px;
    }

    .message {
      margin-top: 25px;
      font-size: 18px;
      color: #d63384;
      min-height: 24px;
    }

    .buttons {
      margin-top: 25px;
      display: flex;
      justify-content: center;
      gap: 10px;
    }

    button {
      padding: 8px 16px;
      border-radius: 10px;
      border: none;
      cursor: pointer;
      transition: 0.2s;
      font-weight: 500;
    }

    .replay {
      background: #e83e8c;
      color: white;
    }

    .share {
      background: white;
      color: #e83e8c;
      border: 1px solid #e83e8c;
    }

    button:hover {
      transform: scale(1.05);
    }

    /* Анімація сердечок */
    .heart {
      position: absolute;
      bottom: 20px;
      font-size: 20px;
      animation: floatUp 3s linear infinite;
      opacity: 0;
    }

    @keyframes floatUp {
      0% {
        transform: translateY(0) scale(0.8);
        opacity: 0;
      }
      20% {
        opacity: 1;
      }
      100% {
        transform: translateY(-200px) scale(1.2);
        opacity: 0;
      }
    }
  </style>
</head>
<body>
  <div class="card">
    <div class="icon">💌</div>
    <h2>Love Message</h2>
    <p>маленькое сообщение с любовью ❤️</p>
    <div class="message" id="message"></div>

    <div class="buttons">
      <button class="replay" onclick="startTyping()">Повторить</button>
      <button class="share" onclick="share()">Поделиться</button>
    </div>
  </div>

  <script>
    const messageEl = document.getElementById("message");
    const messageText = "Ты делаешь мой мир ярче ✨";
    let index = 0;

    function startTyping() {
      messageEl.textContent = "";
      index = 0;
      type();
    }

    function type() {
      if (index < messageText.length) {
        messageEl.textContent += messageText.charAt(index);
        index++;
        setTimeout(type, 60);
      } else {
        spawnHearts();
      }
    }

    function spawnHearts() {
      for (let i = 0; i < 8; i++) {
        const heart = document.createElement("div");
        heart.classList.add("heart");
        heart.textContent = "💖";
        heart.style.left = Math.random() * 90 + "%";
        heart.style.animationDelay = (Math.random() * 2) + "s";
        document.body.appendChild(heart);
        setTimeout(() => heart.remove(), 4000);
      }
    }

    function share() {
      const url = window.location.href;
      navigator.clipboard.writeText(url);
      alert("Ссылку скопировано 💌");
    }

    // запуск автоматично при відкритті
    window.onload = startTyping;
  </script>
</body>
</html>
