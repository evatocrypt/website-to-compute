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
      background: rgba(255, 255, 255, 0.1);
      padding: 2rem;
      border-radius: 16px;
      box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
      width: 90%;
      max-width: 400px;
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
    }
    button:hover {
      transform: scale(1.05);
      background: #31A67B;
    }
    .result {
      margin-top: 1.5rem;
      font-size: 1.5rem;
      font-weight: bold;
      opacity: 0;
      transform: translateY(20px);
      transition: opacity 0.5s, transform 0.5s;
    }
    .result.show {
      opacity: 1;
      transform: translateY(0);
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Mint your .AZ name!</h1>
    <input type="text" id="nameInput" placeholder="Enter your name..." />
    <br />
    <button id="mintButton">Mint</button>
    <div class="result" id="result"></div>
  </div>
  <script>
    document.getElementById('mintButton').addEventListener('click', () => {
      const name = document.getElementById('nameInput').value.trim();
      const result = document.getElementById('result');
      if (!name) {
        result.textContent = "Oops! Please type something.";
      } else {
        result.textContent = name + '.AZ';
      }
      result.classList.add('show');
    });
  </script>
</body>
</html>
