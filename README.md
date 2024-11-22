<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Number Guessing Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 50px;
            text-align: center;
        }
        input, button {
            padding: 10px;
            font-size: 16px;
            margin-top: 10px;
        }
    </style>
</head>
<body>
    <h1>Number Guessing Game</h1>
    <p>Guess a number between 1 and 100:</p>
    
    <input type="number" id="guess" placeholder="Enter your guess" />
    <button onclick="checkGuess()">Guess</button>
    
    <p id="feedback"></p>

    <script>
        const numberToGuess = Math.floor(Math.random() * 100) + 1;
        let attempts = 0;

        function checkGuess() {
            const userGuess = parseInt(document.getElementById('guess').value);
            attempts++;
            
            if (userGuess < numberToGuess) {
                document.getElementById('feedback').textContent = 'Too low! Try again.';
            } else if (userGuess > numberToGuess) {
                document.getElementById('feedback').textContent = 'Too high! Try again.';
            } else {
                document.getElementById('feedback').textContent = `Correct! You guessed the right number in ${attempts} attempts.`;
            }
        }
    </script>
</body>
</html>
