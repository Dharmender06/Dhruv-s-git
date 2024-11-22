<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tic-Tac-Toe Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f4f4f9;
            margin: 0;
        }
        .game-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            background-color: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
        }
        .board {
            display: grid;
            grid-template-columns: repeat(3, 100px);
            grid-template-rows: repeat(3, 100px);
            gap: 10px;
            margin-top: 20px;
        }
        .cell {
            width: 100px;
            height: 100px;
            background-color: #e9e9e9;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 36px;
            cursor: pointer;
            border-radius: 10px;
            transition: background-color 0.3s ease;
        }
        .cell:hover {
            background-color: #d4d4d4;
        }
        .status {
            font-size: 20px;
            margin-top: 20px;
        }
        .reset-btn {
            font-size: 18px;
            padding: 10px 20px;
            cursor: pointer;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 5px;
            margin-top: 20px;
        }
        .reset-btn:hover {
            background-color: #45a049;
        }
    </style>
</head>
<body>

    <div class="game-container">
        <h1>Tic-Tac-Toe</h1>
        <div class="board" id="board">
            <div class="cell" onclick="makeMove(0)"></div>
            <div class="cell" onclick="makeMove(1)"></div>
            <div class="cell" onclick="makeMove(2)"></div>
            <div class="cell" onclick="makeMove(3)"></div>
            <div class="cell" onclick="makeMove(4)"></div>
            <div class="cell" onclick="makeMove(5)"></div>
            <div class="cell" onclick="makeMove(6)"></div>
            <div class="cell" onclick="makeMove(7)"></div>
            <div class="cell" onclick="makeMove(8)"></div>
        </div>
        <div class="status" id="status">Player X's Turn</div>
        <button class="reset-btn" onclick="resetGame()">Reset Game</button>
    </div>

    <script>
        let board = ['', '', '', '', '', '', '', '', '']; // Empty cells
        let currentPlayer = 'X';
        let gameActive = true;

        // Check if a player has won
        function checkWinner() {
            const winningCombination = [
                [0, 1, 2],
                [3, 4, 5],
                [6, 7, 8],
                [0, 3, 6],
                [1, 4, 7],
                [2, 5, 8],
                [0, 4, 8],
                [2, 4, 6]
            ];

            for (let combo of winningCombination) {
                const [a, b, c] = combo;
                if (board[a] && board[a] === board[b] && board[a] === board[c]) {
                    return board[a]; // Return winner 'X' or 'O'
                }
            }
            return null;
        }

        // Handle player's move
        function makeMove(index) {
            if (board[index] === '' && gameActive) {
                board[index] = currentPlayer;
                document.getElementsByClassName('cell')[index].textContent = currentPlayer;
                let winner = checkWinner();
                
                if (winner) {
                    document.getElementById('status').textContent = `${winner} Wins!`;
                    gameActive = false;
                } else if (!board.includes('')) {
                    document.getElementById('status').textContent = 'It\'s a Tie!';
                    gameActive = false;
                } else {
                    currentPlayer = currentPlayer === 'X' ? 'O' : 'X';
                    document.getElementById('status').textContent = `Player ${currentPlayer}'s Turn`;
                }
            }
        }

        // Reset the game
        function resetGame() {
            board = ['', '', '', '', '', '', '', '', ''];
            currentPlayer = 'X';
            gameActive = true;
            document.getElementById('status').textContent = `Player X's Turn`;
            
            const cells = document.getElementsByClassName('cell');
            for (let cell of cells) {
                cell.textContent = '';
            }
        }
    </script>

</body>
</html>
