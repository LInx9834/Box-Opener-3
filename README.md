# Box-Opener-3
<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Shop</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            text-align: center;
            background-color: #ffffff;
        }
        h1 {
            color: #333;
            margin: 20px 0;
        }
        .container {
            max-width: 600px;
            margin: 20px auto;
            padding: 20px;
            background: #ffffff;
        }
        button {
            font-size: 18px;
            padding: 10px 20px;
            margin: 10px;
            border: none;
            border-radius: 5px;
            background-color: #007BFF;
            color: white;
            cursor: pointer;
        }
        button:hover:not(:disabled) {
            background-color: #0056b3;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Shop</h1>
        <p class="info">Münzen: <span id="coins">0</span></p>
        <button id="buyNormalBox">Normale Box (2 Münzen)</button>
        <button id="buyRareBox">Seltene Box (5 Münzen)</button>
        <button id="backToGame">Zurück zum Spiel</button>
        <p class="info" id="result">Wähle eine Box aus!</p>
    </div>

    <script>
        // Lade Münzstand aus localStorage
        let coins = parseInt(localStorage.getItem("coins")) || 10;
        const coinsElement = document.getElementById("coins");
        const resultElement = document.getElementById("result");

        const updateCoins = (amount) => {
            coins += amount;
            if (coins < 0) coins = 0;
            coinsElement.textContent = coins;
            localStorage.setItem("coins", coins); // Münzstand speichern
        };

        const buyBox = (cost) => {
            if (coins >= cost) {
                updateCoins(-cost);
                resultElement.textContent = `Du hast eine Box für ${cost} Münzen gekauft!`;
            } else {
                resultElement.textContent = "Nicht genug Münzen!";
            }
        };

        document.getElementById("buyNormalBox").addEventListener("click", () => {
            buyBox(2);
        });

        document.getElementById("buyRareBox").addEventListener("click", () => {
            buyBox(5);
        });

        document.getElementById("backToGame").addEventListener("click", () => {
            window.location.href = "index.html";
        });

        // Zeige den aktuellen Münzstand an
        coinsElement.textContent = coins;
    </script>
</body>
</html>
