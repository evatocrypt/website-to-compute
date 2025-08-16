<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Mint Your .AZ Name!</title>
  <style>
    body {
      margin: 0;
      height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      background: linear-gradient(135deg, #8C7EFF, #EDA1FF);
      font-family: 'Segoe UI', sans-serif;
      color: #fff;
    }
    .container {
      text-align: center;
      width: 90%;
      max-width: 400px;
    }
    .logo {
      width: 80px;
      margin-bottom: 1rem;
    }
    input {
      width: 80%;
      padding: 0.75rem;
      font-size: 1.1rem;
      border: none;
      border-radius: 8px;
      margin: 1rem 0;
    }
    button {
      background: #466CF7;
      color: white;
      padding: 0.75rem 1.5rem;
      font-size: 1.1rem;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      transition: transform 0.2s, background 0.2s;
      margin: 0.5rem;
    }
    button:hover {
      transform: scale(1.05);
      background: #31A67B;
    }
    .card {
      margin-top: 2rem;
      padding: 1.5rem;
      background: rgba(255, 255, 255, 0.1);
      backdrop-filter: blur(10px);
      border-radius: 16px;
      border: 2px solid transparent;
      background-clip: padding-box;
      position: relative;
      overflow: hidden;
      opacity: 0;
      transform: translateY(50px) scale(0.9);
      transition: opacity 0.6s ease, transform 0.6s ease;
    }
    .card.show {
      opacity: 1;
      transform: translateY(0) scale(1);
    }
    .card-border {
      position: absolute;
      top: -2px;
      left: -2px;
      right: -2px;
      bottom: -2px;
      background: linear-gradient(135deg, #8C7EFF, #EDA1FF, #466CF7);
      z-index: -1;
    }
    .card-logo {
      width: 40px;
      display: block;
      margin-bottom: 1rem;
    }
    .card-name {
      font-size: 1.8rem;
      font-weight: bold;
    }
    .card-title {
      font-size: 1rem;
      margin-top: 0.3rem;
      opacity: 0.85;
      font-style: italic;
    }
    .card-footer {
      font-size: 0.85rem;
      margin-top: 0.8rem;
      opacity: 0.7;
      font-style: italic;
    }
  </style>
</head>
<body>
  <div class="container">
    <img src="https://aztec.network/favicon.ico" alt="Aztec Logo" class="logo" />
    <h1>Mint your .AZ name!</h1>
    <input type="text" id="nameInput" placeholder="Enter your name..." />
    <br />
    <button id="mintButton">Mint</button>
    <button id="shareButton" style="display:none;">Share on X</button>
    <button id="downloadButton" style="display:none;">Download Card</button>

    <div class="card" id="card">
      <div class="card-border"></div>
      <img src="https://aztec.network/favicon.ico" alt="Aztec Logo" class="card-logo" />
      <div class="card-name" id="cardName"></div>
      <div class="card-title" id="cardTitle"></div>
      <div class="card-footer">For Aztec network community</div>
    </div>
  </div>

  <!-- Confetti -->
  <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
  <!-- HTML2Canvas for screenshot -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>

  <script>
    const titles = [
      "PRIVACY WARRIOR",
      "PRIVACY ADVOCATE",
      "PRIVACY CHIEF",
      "PRIVACY POLICE",
      "PRIVACY WIZARD"
    ];

    const mintButton = document.getElementById('mintButton');
    const shareButton = document.getElementById('shareButton');
    const downloadButton = document.getElementById('downloadButton');
    const card = document.getElementById('card');
    const cardName = document.getElementById('cardName');
    const cardTitle = document.getElementById('cardTitle');
    const nameInput = document.getElementById('nameInput');

    mintButton.addEventListener('click', () => {
      const name = nameInput.value.trim();
      if (!name) return;

      const randomTitle = titles[Math.floor(Math.random() * titles.length)];

      cardName.textContent = name + '.AZ';
      cardTitle.textContent = randomTitle;

      card.classList.add('show');
      shareButton.style.display = 'inline-block';
      downloadButton.style.display = 'inline-block';

      // Confetti celebration
      confetti({ particleCount: 100, spread: 70, origin: { y: 0.6 } });
    });

    shareButton.addEventListener('click', () => {
      const text = `I just minted my name: ${cardName.textContent} 🔥 #AztecNetwork`;
      const url = `https://twitter.com/intent/tweet?text=${encodeURIComponent(text)}`;
      window.open(url, '_blank');
    });

    downloadButton.addEventListener('click', async () => {
      const canvas = await html2canvas(card);
      const image = canvas.toDataURL("image/png");
      const link = document.createElement('a');
      link.href = image;
      link.download = `${cardName.textContent}-membership.png`;
      link.click();
    });
  </script>
</body>
</html>
