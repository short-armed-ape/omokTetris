<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Omok + Tetris</title>
    <style>
        body { 
            margin: 0; 
            padding: 0; 
            font-family: Arial, sans-serif;
            background-color: #333;
            color: white;
            text-align: center;
            padding: 20px;
            height: 100vh;
            box-sizing: border-box;
        }
        .container {
            max-width: 600px;
            margin: 0 auto;
        }
        canvas {
            background-color: #505050;
            border: 2px solid #777;
            display: block;
            margin: 0 auto;
            max-width: 100%;
            height: auto;
        }
        .controls {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin: 15px 0;
        }
        button {
            padding: 8px 15px;
            background-color: #0066cc;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 1em;
        }
        .mobile-controls {
            margin: 15px auto;
            max-width: 300px;
            display: none;
        }
        .mobile-row {
            display: flex;
            justify-content: center;
            margin: 5px 0;
        }
        .mobile-btn {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background-color: rgba(0,102,204,0.7);
            color: white;
            border: none;
            font-size: 20px;
            font-weight: bold;
            margin: 5px;
        }
        .info {
            background-color: #444;
            padding: 15px;
            border-radius: 5px;
            margin: 20px 0;
            text-align: left;
        }
        .credits {
            margin-bottom: 15px;
        }
        .credits a {
            color: #66ccff;
            text-decoration: none;
        }
        .credits a:hover {
            text-decoration: underline;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Omok + Tetris</h1>
        <div class="credits">
            <p>만든이: macho(endplan) | <a href="https://www.youtube.com/@endplan" target="_blank">YouTube 채널</a></p>
        </div>
        <canvas id="gameCanvas" width="450" height="600"></canvas>
        <div id="status" style="margin: 15px 0; height: 30px;">Player 1's Turn</div>
        <div class="controls">
            <button id="restartBtn">Restart Game</button>
        </div>
        
        <div id="mobileControls" class="mobile-controls">
            <div class="mobile-row">
                <button id="rotateBtn" class="mobile-btn">↻</button>
            </div>
            <div class="mobile-row">
                <button id="leftBtn" class="mobile-btn">←</button>
                <button id="downBtn" class="mobile-btn">↓</button>
                <button id="rightBtn" class="mobile-btn">→</button>
            </div>
            <div class="mobile-row">
                <button id="dropBtn" class="mobile-btn">⬇⬇</button>
            </div>
        </div>
        
        <div class="info">
            <h3>How to Play:</h3>
            <p>This game combines Omok (Five in a Row) with Tetris mechanics.</p>
            <p><strong>Player 1 (Blue):</strong> Control tetromino blocks using keyboard or touch.</p>
            <ul>
                <li>← → keys: Move left/right</li>
                <li>↑ key: Rotate</li>
                <li>↓ key: Move down</li>
                <li>Space: Hard drop</li>
            </ul>
            <p><strong>Player 2 (White):</strong> AI opponent</p>
            <p><strong>Win Conditions:</strong> Connect exactly five stones in a row horizontally, vertically, or diagonally.</p>
            <p>Clearing a full row will remove it, just like in Tetris!</p>
        </div>
    </div>

    <script>
    // Check if it's a touch device
    if ('ontouchstart' in window) {
        document.getElementById('mobileControls').style.display = 'block';
    }

    // Constants
    const GRID_WIDTH = 15;
    const GRID_HEIGHT = 20;
    const CELL_SIZE = 30;
    const PLAYER_COLORS = {
        1: "#0066ff", // Blue (Human)
        2: "#ffffff"  // White (AI)
    };

    // Get canvas and context
    const canvas = document.getElementById('gameCanvas');
    const ctx = canvas.getContext('2d');
    const statusText = document.getElementById('status');

    // Tetromino shapes
    const SHAPES = {
        'I': [
            [{x:0,y:0}, {x:0,y:1}, {x:0,y:2}, {x:0,y:3}], 
            [{x:0,y:0}, {x:1,y:0}, {x:2,y:0}, {x:3,y:0}]
        ],
        'O': [
            [{x:0,y:0}, {x:0,y:1}, {x:1,y:0}, {x:1,y:1}]
        ],
        'T': [
            [{x:0,y:0}, {x:0,y:1}, {x:0,y:2}, {x:1,y:1}], 
            [{x:0,y:1}, {x:1,y:0}, {x:1,y:1}, {x:2,y:1}], 
            [{x:0,y:1}, {x:1,y:0}, {x:1,y:1}, {x:1,y:2}], 
            [{x:0,y:0}, {x:1,y:0}, {x:1,y:1}, {x:2,y:0}]
        ],
        'S': [
            [{x:0,y:1}, {x:0,y:2}, {x:1,y:0}, {x:1,y:1}], 
            [{x:0,y:0}, {x:1,y:0}, {x:1,y:1}, {x:2,y:1}]
        ],
        'Z': [
            [{x:0,y:0}, {x:0,y:1}, {x:1,y:1}, {x:1,y:2}], 
            [{x:0,y:1}, {x:1,y:0}, {x:1,y:1}, {x:2,y:0}]
        ],
        'J': [
            [{x:0,y:0}, {x:0,y:1}, {x:0,y:2}, {x:1,y:2}], 
            [{x:0,y:1}, {x:1,y:1}, {x:2,y:1}, {x:2,y:0}], 
            [{x:0,y:0}, {x:1,y:0}, {x:1,y:1}, {x:1,y:2}], 
            [{x:0,y:1}, {x:0,y:2}, {x:1,y:1}, {x:2,y:1}]
        ],
        'L': [
            [{x:0,y:0}, {x:0,y:1}, {x:0,y:2}, {x:1,y:0}], 
            [{x:0,y:0}, {x:1,y:0}, {x:2,y:0}, {x:2,y:1}], 
            [{x:0,y:0}, {x:1,y:0}, {x:1,y:1}, {x:1,y:2}], 
            [{x:0,y:1}, {x:0,y:2}, {x:1,y:2}, {x:2,y:2}]
        ]
    };

    // Game grid
    class Grid {
        constructor() {
            this.grid = Array(GRID_HEIGHT).fill().map(() => Array(GRID_WIDTH).fill(0));
        }
        
        draw() {
            // Draw grid
            ctx.strokeStyle = "#c8c8c8";
            ctx.lineWidth = 1;
            
            // Draw horizontal lines
            for (let y = 0; y <= GRID_HEIGHT; y++) {
                ctx.beginPath();
                ctx.moveTo(0, y * CELL_SIZE);
                ctx.lineTo(GRID_WIDTH * CELL_SIZE, y * CELL_SIZE);
                ctx.stroke();
            }
            
            // Draw vertical lines
            for (let x = 0; x <= GRID_WIDTH; x++) {
                ctx.beginPath();
                ctx.moveTo(x * CELL_SIZE, 0);
                ctx.lineTo(x * CELL_SIZE, GRID_HEIGHT * CELL_SIZE);
                ctx.stroke();
            }
            
            // Draw stones
            for (let y = 0; y < GRID_HEIGHT; y++) {
                for (let x = 0; x < GRID_WIDTH; x++) {
                    const player = this.grid[y][x];
                    if (player !== 0) {
                        ctx.fillStyle = PLAYER_COLORS[player];
                        ctx.beginPath();
                        ctx.arc(
                            x * CELL_SIZE + CELL_SIZE / 2,
                            y * CELL_SIZE + CELL_SIZE / 2,
                            CELL_SIZE / 2 - 2,
                            0,
                            Math.PI * 2
                        );
                        ctx.fill();
                    }
                }
            }
        }
        
        placeStones(positions, player) {
            for (const [x, y] of positions) {
                if (x >= 0 && x < GRID_WIDTH && y >= 0 && y < GRID_HEIGHT) {
                    this.grid[y][x] = player;
                }
            }
        }
        
        checkFiveInARow(player) {
            const directions = [[1, 0], [0, 1], [1, 1], [1, -1]]; // horizontal, vertical, diagonal
            
            for (let y = 0; y < GRID_HEIGHT; y++) {
                for (let x = 0; x < GRID_WIDTH; x++) {
                    if (this.grid[y][x] !== player) continue;
                    
                    for (const [dx, dy] of directions) {
                        let count = 1;
                        
                        // Check in one direction
                        let nx = x + dx;
                        let ny = y + dy;
                        while (nx >= 0 && nx < GRID_WIDTH && ny >= 0 && ny < GRID_HEIGHT && this.grid[ny][nx] === player) {
                            count++;
                            nx += dx;
                            ny += dy;
                        }
                        
                        // Check in opposite direction
                        let px = x - dx;
                        let py = y - dy;
                        while (px >= 0 && px < GRID_WIDTH && py >= 0 && py < GRID_HEIGHT && this.grid[py][px] === player) {
                            count++;
                            px -= dx;
                            py -= dy;
                        }
                        
                        if (count === 5) {
                            return true; // Exactly 5 in a row
                        }
                    }
                }
            }
            
            return false;
        }
        
        clearFullRows() {
            const fullRows = [];
            for (let i = 0; i < GRID_HEIGHT; i++) {
                if (this.grid[i].every(cell => cell !== 0)) {
                    fullRows.push(i);
                }
            }
            
            for (let i = fullRows.length - 1; i >= 0; i--) {
                const row = fullRows[i];
                this.grid.splice(row, 1);
                this.grid.unshift(Array(GRID_WIDTH).fill(0));
            }
            
            return fullRows.length;
        }
    }

    // Tetromino class
    class Tetromino {
        constructor(shape, grid) {
            this.shape = shape;
            this.rotation = 0;
            this.x = Math.floor(GRID_WIDTH / 2) - 1;
            this.y = 0;
            this.grid = grid;
        }
        
        getBlocks() {
            const shapeCoords = SHAPES[this.shape][this.rotation];
            return shapeCoords.map(coord => [this.x + coord.x, this.y + coord.y]);
        }
        
        move(dx, dy) {
            const newX = this.x + dx;
            const newY = this.y + dy;
            if (!this.collides(newX, newY, this.rotation)) {
                this.x = newX;
                this.y = newY;
                return true;
            }
            return false;
        }
        
        rotate() {
            const newRotation = (this.rotation + 1) % SHAPES[this.shape].length;
            if (!this.collides(this.x, this.y, newRotation)) {
                this.rotation = newRotation;
            }
        }
        
        collides(x, y, rotation) {
            const shapeCoords = SHAPES[this.shape][rotation];
            for (const coord of shapeCoords) {
                const newX = x + coord.x;
                const newY = y + coord.y;
                if (newX < 0 || newX >= GRID_WIDTH || newY < 0 || newY >= GRID_HEIGHT ||
                    (newY < GRID_HEIGHT && this.grid.grid[newY][newX] !== 0)) {
                    return true;
                }
            }
            return false;
        }
        
        draw() {
            ctx.fillStyle = PLAYER_COLORS[game.currentPlayer];
            for (const [x, y] of this.getBlocks()) {
                if (x >= 0 && x < GRID_WIDTH && y >= 0 && y < GRID_HEIGHT) {
                    ctx.fillRect(x * CELL_SIZE, y * CELL_SIZE, CELL_SIZE, CELL_SIZE);
                    ctx.strokeStyle = "#c8c8c8";
                    ctx.strokeRect(x * CELL_SIZE, y * CELL_SIZE, CELL_SIZE, CELL_SIZE);
                }
            }
        }
    }

    // Game class
    class Game {
        constructor() {
            this.grid = new Grid();
            this.currentPlayer = 1;
            this.currentTetromino = null;
            this.gameOver = false;
            this.winner = null;
            this.fallTime = 0;
            this.fallSpeed = 500; // ms
            this.lastTime = 0;
            this.active = true;
            
            this.spawnTetromino();
        }
        
        restart() {
            this.grid = new Grid();
            this.currentPlayer = 1;
            this.currentTetromino = null;
            this.gameOver = false;
            this.winner = null;
            this.fallTime = 0;
            this.active = true;
            
            this.spawnTetromino();
            statusText.textContent = "Player 1's Turn";
        }
        
        spawnTetromino() {
            const shapes = Object.keys(SHAPES);
            const shape = shapes[Math.floor(Math.random() * shapes.length)];
            this.currentTetromino = new Tetromino(shape, this.grid);
            
            if (this.currentTetromino.collides(this.currentTetromino.x, this.currentTetromino.y, this.currentTetromino.rotation)) {
                this.gameOver = true;
                this.winner = null;
            }
        }
        
        update() {
            if (this.gameOver || !this.active) return;
            
            if (!this.currentTetromino.move(0, 1)) {
                this.grid.placeStones(this.currentTetromino.getBlocks(), this.currentPlayer);
                
                if (this.grid.checkFiveInARow(this.currentPlayer)) {
                    this.gameOver = true;
                    this.winner = this.currentPlayer;
                    this.showGameOver();
                } else {
                    this.grid.clearFullRows();
                    this.currentPlayer = 3 - this.currentPlayer; // Switch player
                    statusText.textContent = `Player ${this.currentPlayer}'s Turn`;
                    this.spawnTetromino();
                    
                    // AI turn
                    if (this.currentPlayer === 2 && this.active) {
                        setTimeout(() => this.aiMove(), 300);
                    }
                }
            }
        }
        
        aiMove() {
            if (this.gameOver || !this.active) return;
            
            // Simple AI
            const maxAttempts = 10;
            let moved = false;
            
            for (let attempt = 0; attempt < maxAttempts; attempt++) {
                // Random rotation
                const rotations = Math.floor(Math.random() * SHAPES[this.currentTetromino.shape].length);
                for (let r = 0; r < rotations; r++) {
                    this.currentTetromino.rotate();
                }
                
                // Random horizontal position
                const dx = Math.floor(Math.random() * GRID_WIDTH) - this.currentTetromino.x;
                if (this.currentTetromino.move(dx, 0)) {
                    while (this.currentTetromino.move(0, 1)) {
                        // Hard drop
                    }
                    this.update();
                    moved = true;
                    break;
                }
            }
            
            if (!moved) {
                while (this.currentTetromino.move(0, 1)) {
                    // Hard drop
                }
                this.update();
            }
        }
        
        handleKeyPress(key) {
            if (this.gameOver || this.currentPlayer !== 1 || !this.active) return;
            
            switch (key) {
                case 'ArrowLeft':
                    this.currentTetromino.move(-1, 0);
                    break;
                case 'ArrowRight':
                    this.currentTetromino.move(1, 0);
                    break;
                case 'ArrowDown':
                    this.currentTetromino.move(0, 1);
                    break;
                case 'ArrowUp':
                    this.currentTetromino.rotate();
                    break;
                case ' ': // Space
                    while (this.currentTetromino.move(0, 1)) {
                        // Hard drop
                    }
                    this.update();
                    break;
            }
        }
        
        draw() {
            // Clear canvas
            ctx.fillStyle = "#505050";
            ctx.fillRect(0, 0, canvas.width, canvas.height);
            
            this.grid.draw();
            
            if (this.currentTetromino) {
                this.currentTetromino.draw();
            }
        }
        
        gameLoop(timestamp) {
            const deltaTime = timestamp - this.lastTime;
            this.lastTime = timestamp;
            
            if (!this.gameOver && this.active) {
                if (this.currentPlayer === 1) {
                    this.fallTime += deltaTime;
                    if (this.fallTime >= this.fallSpeed) {
                        this.fallTime = 0;
                        this.update();
                    }
                }
            }
            
            this.draw();
            requestAnimationFrame((timestamp) => this.gameLoop(timestamp));
        }
        
        showGameOver() {
            if (this.winner) {
                statusText.textContent = `Player ${this.winner} Wins!`;
            } else {
                statusText.textContent = "Game Over - Draw!";
            }
            
            setTimeout(() => this.restart(), 3000);
        }
    }

    // Initialize game
    const game = new Game();

    // Start game loop
    requestAnimationFrame((timestamp) => game.gameLoop(timestamp));

    // Event Listeners
    window.addEventListener('keydown', (e) => {
        if (['ArrowLeft', 'ArrowRight', 'ArrowDown', 'ArrowUp', ' '].includes(e.key)) {
            e.preventDefault();
            game.handleKeyPress(e.key);
        }
    });

    document.getElementById('restartBtn').addEventListener('click', () => {
        game.restart();
    });

    // Mobile controls
    function setupMobileButton(id, key) {
        const btn = document.getElementById(id);
        if (btn) {
            btn.addEventListener('click', () => game.handleKeyPress(key));
            btn.addEventListener('touchstart', (e) => {
                e.preventDefault();
                game.handleKeyPress(key);
            });
        }
    }

    setupMobileButton('rotateBtn', 'ArrowUp');
    setupMobileButton('leftBtn', 'ArrowLeft');
    setupMobileButton('rightBtn', 'ArrowRight');
    setupMobileButton('downBtn', 'ArrowDown');
    setupMobileButton('dropBtn', ' ');
    </script>
</body>
</html>
