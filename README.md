<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rock, Paper, Scissors Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f7f7f7;
            margin-top: 50px;
        }
        .game-container {
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        .choices {
            display: flex;
            justify-content: center;
            gap: 30px;
            margin-top: 30px;
        }
        .choices button {
            font-size: 20px;
            padding: 20px;
            cursor: pointer;
            background-color: #4CAF50;
            border: none;
            border-radius: 5px;
            color: white;
            transition: background-color 0.3s ease;
        }
        .choices button:hover {
            background-color: #45a049;
        }
        .result {
            font-size: 24px;
            margin-top: 20px;
        }
        .score {
            font-size: 20px;
            margin-top: 30px;
        }
        .reset-btn {
            font-size: 18px;
            padding: 10px 20px;
            cursor: pointer;
            background-color: #f44336;
            color: white;
            border: none;
            border-radius: 5px;
            margin-top: 20px;
        }
        .reset-btn:hover {
            background-color: #e53935;
        }
    </style>
</head>
<body>
    <h1>Rock, Paper, Scissors Game</h1>
    <div class="game-container">
        <div class="choices">
            <button onclick="playerChoice('rock')">Rock</button>
            <button onclick="playerChoice('paper')">Paper</button>
            <button onclick="playerChoice('scissors')">Scissors</button>
        </div>
        <div class="result" id="result">
            <p>Choose your move!</p>
        </div>
        <div class="score">
            <p>Player: <span id="player-score">0</span></p>
            <p>Computer: <span id="computer-score">0</span></p>
        </div>
        <button class="reset-btn" onclick="resetGame()">Reset Game</button>
    </div>

    <script>
        let playerScore = 0;
        let computerScore = 0;

        const resultElement = document.getElementById('result');
        const playerScoreElement = document.getElementById('player-score');
        const computerScoreElement = document.getElementById('computer-score');

        function computerChoice() {
            const choices = ['rock', 'paper', 'scissors'];
            const randomIndex = Math.floor(Math.random() * 3);
            return choices[randomIndex];
        }

        function determineWinner(player, computer) {
            if (player === computer) {
                return 'It\'s a tie!';
            }
            if (
                (player === 'rock' && computer === 'scissors') ||
                (player === 'paper' && computer === 'rock') ||
                (player === 'scissors' && computer === 'paper')
            ) {
                return 'You win!';
            }
            return 'Computer wins!';
        }

        function updateScore(winner) {
            if (winner === 'You win!') {
                playerScore++;
            } else if (winner === 'Computer wins!') {
                computerScore++;
            }
            playerScoreElement.textContent = playerScore;
            computerScoreElement.textContent = computerScore;
        }

        function playerChoice(player) {
            const computer = computerChoice();
            const winner = determineWinner(player, computer);
            resultElement.innerHTML = `
                <p>You chose: ${player}</p>
                <p>Computer chose: ${computer}</p>
                <p>${winner}</p>
            `;
            updateScore(winner);
        }

        function resetGame() {
            playerScore = 0;
            computerScore = 0;
            playerScoreElement.textContent = playerScore;
            computerScoreElement.textContent = computerScore;
            resultElement.innerHTML = `<p>Choose your move!</p>`;
        }
    </script>
</body>
</html>
