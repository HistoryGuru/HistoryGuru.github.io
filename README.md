<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jin 老师's Chinese Games</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Arial', sans-serif;
            background-color: #000000;
            color: #ffffff;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
            border: 10px solid #ffffff;
        }
        
        h1 {
            font-size: 48px;
            margin-bottom: 60px;
            text-align: center;
            letter-spacing: 2px;
        }
        
        .game-button {
            padding: 20px 40px;
            font-size: 24px;
            background-color: #ffffff;
            color: #000000;
            border: 3px solid #ffffff;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
            display: inline-block;
            font-weight: bold;
        }
        
        .game-button:hover {
            background-color: #000000;
            color: #ffffff;
            transform: scale(1.05);
        }
        
        .disclaimer {
            position: fixed;
            bottom: 20px;
            font-size: 12px;
            color: #888888;
        }
    </style>
</head>
<body>
    <h1>Jin 老师's Chinese Games</h1>
    
    <a href="https://historyguru.github.io/Asteroidgame" class="game-button">
        Play Asteroid Game
    </a>
    
    <div class="disclaimer">All code by Leroy Qu</div>
</body>
</html>
