<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Justin Bieber & the Rubik's Cube</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            color: #333;
            overflow-x: hidden;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        header {
            text-align: center;
            background: rgba(255, 255, 255, 0.95);
            padding: 30px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            margin-bottom: 30px;
            backdrop-filter: blur(10px);
        }

        h1 {
            font-size: 3rem;
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
        }

        .subtitle {
            font-size: 1.2rem;
            color: #666;
            font-style: italic;
        }

        .section {
            background: rgba(255, 255, 255, 0.9);
            margin: 20px 0;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.2);
            backdrop-filter: blur(5px);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .section:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 40px rgba(0, 0, 0, 0.3);
        }

        .image-container {
            text-align: center;
            margin: 20px 0;
        }

        .celebrity-image, .rubiks-image {
            width: 200px;
            height: 200px;
            border-radius: 50%;
            object-fit: cover;
            border: 5px solid #fff;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            margin: 10px;
            transition: transform 0.3s ease;
        }

        .celebrity-image:hover, .rubiks-image:hover {
            transform: scale(1.1) rotate(5deg);
        }

        .rubiks-image {
            border-radius: 20px;
        }

        .game-section {
            background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 100%);
            color: #333;
        }

        .game-container {
            text-align: center;
            margin: 20px 0;
        }

        .game-btn {
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
            color: white;
            border: none;
            padding: 15px 30px;
            font-size: 1.1rem;
            border-radius: 25px;
            cursor: pointer;
            margin: 10px;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }

        .game-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
        }

        .quiz-container {
            background: #f8f9fa;
            padding: 20px;
            border-radius: 10px;
            margin: 20px 0;
            border-left: 5px solid #4ecdc4;
        }

        .question {
            font-size: 1.1rem;
            margin-bottom: 15px;
            font-weight: bold;
        }

        .options {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 10px;
            margin-bottom: 15px;
        }

        .option {
            padding: 10px;
            background: #e9ecef;
            border: 2px solid transparent;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .option:hover {
            background: #dee2e6;
            transform: scale(1.02);
        }

        .option.selected {
            background: #4ecdc4;
            color: white;
            border-color: #45b7aa;
        }

        .option.correct {
            background: #28a745;
            color: white;
        }

        .option.incorrect {
            background: #dc3545;
            color: white;
        }

        .memory-game {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
            max-width: 400px;
            margin: 20px auto;
        }

        .memory-card {
            width: 80px;
            height: 80px;
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2rem;
            cursor: pointer;
            transition: all 0.3s ease;
            color: white;
        }

        .memory-card:hover {
            transform: scale(1.05);
        }

        .memory-card.flipped {
            background: #fff;
            color: #333;
            border: 2px solid #4ecdc4;
        }

        .memory-card.matched {
            background: #28a745;
            color: white;
        }

        .success-tips {
            background: linear-gradient(135deg, #ffecd2 0%, #fcb69f 100%);
        }

        .tip-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .tip-card {
            background: rgba(255, 255, 255, 0.9);
            padding: 20px;
            border-radius: 10px;
            text-align: center;
            transition: transform 0.3s ease;
        }

        .tip-card:hover {
            transform: translateY(-5px);
        }

        .tip-icon {
            font-size: 3rem;
            margin-bottom: 10px;
        }

        .score-display {
            text-align: center;
            font-size: 1.5rem;
            color: #4ecdc4;
            font-weight: bold;
            margin: 20px 0;
        }

        .floating-animation {
            animation: float 3s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
        }

        .pulse-animation {
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.7; }
        }

        @media (max-width: 768px) {
            h1 {
                font-size: 2rem;
            }
            
            .memory-game {
                grid-template-columns: repeat(3, 1fr);
            }
            
            .celebrity-image, .rubiks-image {
                width: 150px;
                height: 150px;
            }
            
            .options {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header class="floating-animation">
            <h1>Justin Bieber & the Rubik's Cube</h1>
            <p class="subtitle">A Surprising Talent Project</p>
        </header>

        <div class="section">
            <h2>🎤 Meet the Cube Master!</h2>
            <div class="image-container">
                <img src="https://upload.wikimedia.org/wikipedia/commons/d/da/Justin_Bieber_in_2015.jpg" 
                     alt="Justin Bieber" class="celebrity-image pulse-animation">
                <img src="https://upload.wikimedia.org/wikipedia/commons/a/a6/Rubik%27s_cube.svg" 
                     alt="Rubik's Cube" class="rubiks-image pulse-animation">
            </div>
            <p>Did you know that Justin Bieber, the famous singer, is incredibly skilled at solving the Rubik's Cube? 
               He's demonstrated this talent on TV and in videos, leaving audiences amazed! This project explores 
               his surprising skill and how anyone can develop cube-solving abilities.</p>
        </div>

        <div class="section">
            <h2>🔑 The Three Keys to Cube Mastery</h2>
            <div class="tip-grid">
                <div class="tip-card">
                    <div class="tip-icon">📚</div>
                    <h3>Learn the Steps</h3>
                    <p>Master the layer-by-layer method with proven algorithms and techniques.</p>
                </div>
                <div class="tip-card">
                    <div class="tip-icon">🏃‍♂️</div>
                    <h3>Practice Daily</h3>
                    <p>Regular practice develops muscle memory and increases solving speed.</p>
                </div>
                <div class="tip-card">
                    <div class="tip-icon">⚡</div>
                    <h3>Learn from Experts</h3>
                    <p>Study speedcuber techniques and advanced algorithms for faster solutions.</p>
                </div>
            </div>
        </div>

        <div class="section game-section">
            <h2>🎮 Interactive Games</h2>
            
            <div class="game-container">
                <h3>Rubik's Cube Knowledge Quiz</h3>
                <div class="quiz-container">
                    <div class="question" id="question">Click "Start Quiz" to begin!</div>
                    <div class="options" id="options"></div>
                    <button class="game-btn" onclick="startQuiz()">Start Quiz</button>
                    <div class="score-display" id="score">Score: 0/0</div>
                </div>
            </div>

            <div class="game-container">
                <h3>Memory Challenge - Cube Colors</h3>
                <p>Match the cube color pairs!</p>
                <div class="memory-game" id="memoryGame"></div>
                <button class="game-btn" onclick="startMemoryGame()">New Game</button>
                <div class="score-display" id="memoryScore">Moves: 0</div>
            </div>
        </div>

        <div class="section success-tips">
            <h2>🏆 Path to Success</h2>
            <div class="tip-grid">
                <div class="tip-card">
                    <div class="tip-icon">🏅</div>
                    <h3>Become a Champion</h3>
                    <p>Compete in contests and try to break speed records in your school, city, or even worldwide!</p>
                </div>
                <div class="tip-card">
                    <div class="tip-icon">🌟</div>
                    <h3>Digital Stardom</h3>
                    <p>Create YouTube or TikTok content, teach others, and share your cube-solving journey!</p>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Quiz Game Logic
        const quizQuestions = [
            {
                question: "What makes Justin Bieber good at solving the Rubik's Cube?",
                options: ["He's naturally gifted", "He learned steps and practiced", "He uses magic", "He memorized one solution"],
                correct: 1
            },
            {
                question: "How many main steps are there to master the Rubik's Cube?",
                options: ["Two", "Three", "Four", "Five"],
                correct: 1
            },
            {
                question: "What do speedcubers use to solve cubes quickly?",
                options: ["Luck", "Algorithms", "Special cubes", "Time machines"],
                correct: 1
            },
            {
                question: "What's the best way to get faster at solving cubes?",
                options: ["Watch videos only", "Practice regularly", "Buy expensive cubes", "Solve once a month"],
                correct: 1
            }
        ];

        let currentQuestion = 0;
        let score = 0;
        let quizStarted = false;

        function startQuiz() {
            currentQuestion = 0;
            score = 0;
            quizStarted = true;
            showQuestion();
        }

        function showQuestion() {
            if (currentQuestion >= quizQuestions.length) {
                endQuiz();
                return;
            }

            const question = quizQuestions[currentQuestion];
            document.getElementById('question').textContent = question.question;
            
            const optionsDiv = document.getElementById('options');
            optionsDiv.innerHTML = '';
            
            question.options.forEach((option, index) => {
                const optionDiv = document.createElement('div');
                optionDiv.className = 'option';
                optionDiv.textContent = option;
                optionDiv.onclick = () => selectOption(index);
                optionsDiv.appendChild(optionDiv);
            });

            updateScore();
        }

        function selectOption(selectedIndex) {
            const options = document.querySelectorAll('.option');
            const correct = quizQuestions[currentQuestion].correct;
            
            options.forEach((option, index) => {
                option.onclick = null;
                if (index === correct) {
                    option.classList.add('correct');
                } else if (index === selectedIndex) {
                    option.classList.add('incorrect');
                }
            });

            if (selectedIndex === correct) {
                score++;
            }

            setTimeout(() => {
                currentQuestion++;
                showQuestion();
            }, 1500);
        }

        function endQuiz() {
            document.getElementById('question').textContent = `Quiz Complete! You scored ${score} out of ${quizQuestions.length}!`;
            document.getElementById('options').innerHTML = '';
            quizStarted = false;
        }

        function updateScore() {
            document.getElementById('score').textContent = `Score: ${score}/${quizQuestions.length}`;
        }

        // Memory Game Logic
        const colors = ['🔴', '🟡', '🟢', '🔵', '🟠', '🟣', '⚫', '⚪'];
        let memoryCards = [];
        let flippedCards = [];
        let matchedPairs = 0;
        let moves = 0;

        function startMemoryGame() {
            // Create pairs
            const cardValues = [...colors, ...colors];
            cardValues.sort(() => Math.random() - 0.5);
            
            const gameDiv = document.getElementById('memoryGame');
            gameDiv.innerHTML = '';
            
            memoryCards = [];
            flippedCards = [];
            matchedPairs = 0;
            moves = 0;
            
            cardValues.forEach((value, index) => {
                const card = document.createElement('div');
                card.className = 'memory-card';
                card.textContent = '?';
                card.dataset.value = value;
                card.dataset.index = index;
                card.onclick = () => flipCard(card);
                gameDiv.appendChild(card);
                memoryCards.push(card);
            });
            
            updateMemoryScore();
        }

        function flipCard(card) {
            if (flippedCards.length >= 2 || card.classList.contains('flipped') || card.classList.contains('matched')) {
                return;
            }

            card.classList.add('flipped');
            card.textContent = card.dataset.value;
            flippedCards.push(card);

            if (flippedCards.length === 2) {
                moves++;
                updateMemoryScore();
                
                setTimeout(() => {
                    checkMatch();
                }, 1000);
            }
        }

        function checkMatch() {
            const [card1, card2] = flippedCards;
            
            if (card1.dataset.value === card2.dataset.value) {
                card1.classList.add('matched');
                card2.classList.add('matched');
                matchedPairs++;
                
                if (matchedPairs === colors.length) {
                    setTimeout(() => {
                        alert(`Congratulations! You completed the game in ${moves} moves!`);
                    }, 500);
                }
            } else {
                card1.classList.remove('flipped');
                card2.classList.remove('flipped');
                card1.textContent = '?';
                card2.textContent = '?';
            }
            
            flippedCards = [];
        }

        function updateMemoryScore() {
            document.getElementById('memoryScore').textContent = `Moves: ${moves}`;
        }

        // Initialize memory game on load
        window.onload = function() {
            startMemoryGame();
        };
    </script>
</body>
</html>
