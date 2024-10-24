---
layout: page
title: Cookie Clicker
permalink: /cookie_clicker/
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cookie Clicker Game</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f2f2f2;
            font-family: Arial, sans-serif;
            margin: 0;
        }
        .game-container {
            text-align: center;
            border: 1px solid #ddd;
            border-radius: 10px;
            padding: 20px;
            background-color: #fff;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }
        #cookie {
            width: 150px;
            height: 150px;
            background-image: url('https://www.pngitem.com/pimgs/m/151-1511620_cookie-icon-png-transparent-png.png');
            background-size: cover;
            background-color: Brown;
            border: none;
            cursor: pointer;
            margin: 20px;
            border-radius: 50%;
        }
        #counter {
            font-size: 2em;
            margin-bottom: 20px;
        }
        .upgrade {
            margin-top: 10px;
            padding: 10px 20px;
            font-size: 1.2em;
            cursor: pointer;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 5px;
            margin: 5px;
        }
        .upgrade:disabled {
            background-color: #ddd;
            cursor: not-allowed;
        }
    </style>
</head>
<body>
    <div class="game-container">
        <div id="counter">Cookies: 0</div>
        <button id="cookie" onclick="clickCookie()"></button>
        <div id="upgrades">
            <button class="upgrade" id="upgrade1" onclick="buyUpgrade(1)">Upgrade 1 (Cost: 50)</button>
            <button class="upgrade" id="upgrade2" onclick="buyUpgrade(2)">Upgrade 2 (Cost: 200)</button>
            <button class="upgrade" id="upgrade3" onclick="buyUpgrade(3)">Upgrade 3 (Cost: 500)</button>
        </div>
    </div>

    <script>
        let cookies = 0;
        let cookiesPerClick = 1;
        const upgrades = {
            1: { cost: 50, level: 0, multiplier: 1.5 },
            2: { cost: 500, level: 0, multiplier: 2 },
            3: { cost: 5000, level: 0, multiplier: 2.5 },
        };

        function updateDisplay() {
            document.getElementById('counter').textContent = `Cookies: ${cookies}`;
            for (let i = 1; i <= 3; i++) {
                const upgrade = upgrades[i];
                const button = document.getElementById(`upgrade${i}`);
                button.disabled = cookies < upgrade.cost;
                button.textContent = `Upgrade ${i} (Cost: ${upgrade.cost}) Level: ${upgrade.level}`;
            }
        }

        function clickCookie() {
            cookies += cookiesPerClick;
            updateDisplay();
        }

        function buyUpgrade(upgradeId) {
            const upgrade = upgrades[upgradeId];
            if (cookies >= upgrade.cost) {
                cookies -= upgrade.cost;
                cookiesPerClick *= upgrade.multiplier;
                upgrade.level += 1;
                upgrade.cost = Math.round(upgrade.cost * 1.5); // Increase cost for next level
                updateDisplay();
            }
        }

        // Initialize display
        updateDisplay();
    </script>
</body>
</html>
