<!DOCTYPE html>
<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Для мого найдорожчого 🖤</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background-color: #030305;
            color: #ffffff;
            font-family: 'Segoe UI', Roboto, Helvetica, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            overflow: hidden;
            text-align: center;
            position: relative;
        }

        body::before, body::after {
            content: '';
            position: absolute;
            width: 400px;
            height: 400px;
            border-radius: 50%;
            background: rgba(138, 43, 226, 0.08);
            filter: blur(140px);
            z-index: 0;
            pointer-events: none;
        }
        body::before { top: -100px; left: -100px; }
        body::after { bottom: -100px; right: -100px; }

        .container {
            width: 100%;
            max-width: 420px;
            padding: 40px 25px;
            background: #09090e;
            border-radius: 24px;
            border: 1px solid rgba(138, 43, 226, 0.3);
            box-shadow: 0 0 30px rgba(138, 43, 226, 0.1);
            margin: 20px;
            z-index: 10;
            position: relative;
        }

        h1 {
            font-size: 1.8rem;
            font-weight: 800;
            color: #ffffff;
            margin-bottom: 25px;
            text-shadow: 0 0 10px rgba(138, 43, 226, 0.5);
        }

        .message-box {
            min-height: 180px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 25px;
            background: rgba(255, 255, 255, 0.01);
            border: 1px solid rgba(255, 255, 255, 0.03);
            border-radius: 16px;
            padding: 20px;
        }

        .message {
            font-size: 1.05rem;
            line-height: 1.6;
            color: #d1d1d6;
            text-align: left;
            width: 100%;
        }

        .question-title {
            color: #ba68c8;
            font-weight: 700;
            font-size: 1.2rem;
            margin-bottom: 10px;
            text-align: center;
        }

        .quiz-input {
            width: 100%;
            padding: 15px 20px;
            background: #111118;
            border: 1px solid rgba(255, 255, 255, 0.08);
            border-radius: 14px;
            color: #ffffff;
            font-size: 1rem;
            outline: none;
            margin-bottom: 20px;
            text-align: center;
            transition: all 0.3s;
        }

        .quiz-input:focus {
            border-color: #8a2be2;
            box-shadow: 0 0 15px rgba(138, 43, 226, 0.3);
            background: #141420;
        }

        .buttons {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 20px;
            position: relative;
            height: 60px;
            width: 100%;
        }

        .btn {
            padding: 14px 40px;
            font-size: 1.05rem;
            font-weight: 700;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: transform 0.2s, background 0.3s, box-shadow 0.3s;
            user-select: none;
        }

        #yesBtn, .next-btn {
            background: linear-gradient(45deg, #8a2be2, #4a00e0);
            color: white;
            box-shadow: 0 8px 20px rgba(138, 43, 226, 0.3);
        }

        #yesBtn:hover, .next-btn:hover {
            transform: scale(1.03);
            box-shadow: 0 10px 25px rgba(138, 43, 226, 0.5);
        }

        #noBtn {
            background-color: #0d0d13;
            color: #535364;
            border: 1px solid rgba(255, 255, 255, 0.08);
            position: absolute;
            transition: left 0.18s cubic-bezier(0.175, 0.885, 0.32, 1.275), 
                        top 0.18s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            z-index: 9999;
            touch-action: none;
        }

        .effects-layer {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            pointer-events: none;
            z-index: 5;
            overflow: hidden;
        }

        .particle {
            position: absolute;
            bottom: -60px;
            animation: floatStrictlyUp 2.2s cubic-bezier(0.08, 0.8, 0.2, 1) forwards;
            user-select: none;
        }

        @keyframes floatStrictlyUp {
            0% { transform: translateY(0) scale(0.4); opacity: 0; }
            15% { opacity: 0.85; }
            90% { opacity: 0.7; }
            100% { transform: translateY(-115vh) scale(1.3); opacity: 0; }
        }
    </style>
</head>
<body>

    <div class="effects-layer" id="effectsContainer"></div>

    <div class="container">
        <h1 id="mainTitle">Привіт, коханий... 🖤</h1>
        
        <div class="message-box">
            <div class="message" id="textMessage">
                Я довго думала, як підібрати правильні слова, тому вирішила створити цей маленький сайт суто для тебе...<br><br>
                Я хочу зізнатися, що дуже сильно тебе люблю. Мене зводять з розуму твої неймовірні зелені очі, в яких можна просто потонути. А твоя мила усмішка... вона у тебе наче в кота — така ж тепла, хитрюща і рідна, що я просто тану кожен раз, коли її бачу. 🥰<br><br>
                Ти мій найпрекрасніший, найтурботливіший і найкращий хлопчик у світі. Поруч із тобою так спокійно і затишно.
            </div>
        </div>
        
        <div id="quizContainer">
            <button class="btn next-btn" onclick="startQuiz()">Почати квест ⚡</button>
        </div>
        
        <div class="buttons" id="btnContainer" style="display: none;">
            <button class="btn" id="yesBtn" onclick="celebrate()">Так</button>
            <button class="btn" id="noBtn" onmouseenter="moveButton()" ontouchstart="moveButton(event)">Ні</button>
        </div>
    </div>

    <script>
        const questions = [
            { title: "Питання 1", q: "Де ми з тобою познайомилися?", answers: ["пабг", "пабгу", "pubg", "в пабзі", "в пабгу", "у пабгу", "у пабзі"] },
            { title: "Питання 2", q: "Скільки ми вже разом?", answers: ["1 рік", "рік", "один рік", "1рік", "1 rik", "rik"] },
            { title: "Питання 3", q: "Які у мене очі?", answers: ["карі", "каріокі", "карічка"] },
            { title: "Питання 4", q: "Яка у мене фамілія коть?", answers: ["паралюк", "паралючок"] },
            { title: "Питання 5", q: "Моя любима страва?", answers: ["бануш", "деруни", "дируни", "макарони", "паста", "спагеті", "всі види макаронів"] },
            { title: "Питання 6", q: "На кого я йду вчитись?", answers: ["прокурор", "на прокурора", "прокурорка"] },
            { title: "Питання 7", q: "Як звати нашого ведмедика?", answers: ["генка", "геннадій", "генадій", "гена"] },
            { title: "Питання 8", q: "Від чого я найбільше кайфую?", answers: ["від тебе", "від нього", "від його язика", "від язика", "того що він смущається", "він смущається", "смущається"] },
            { title: "Питання 9", q: "Яка моя любима тварина?", answers: ["собачки", "пінгвіни", "він", "собаки", "пінгвів", "ти"] },
            { title: "Питання 10", q: "Як я тебе називала на самому початку?", answers: ["муж на час", "муж на час)", "муж"] },
            { title: "Питання 11", q: "Що мені саме більше подобається у тобі?", answers: ["ти весь мені подобаєшся", "весь", "ти весь", "все", "ти все", "все подобається"] },
            { title: "Питання 12", q: "Що я найбільше люблю? (Тебе і...)", answers: ["його і чукерки", "тебе і цукерки", "тебе і чукерки", "чукерки", "цукерки", "цукерки і тебе", "чукерки і тебе"] }
        ];

        let currentQuestionIndex = 0;
        const msgElement = document.getElementById("textMessage");
        const quizBox = document.getElementById("quizContainer");
        const btnBox = document.getElementById("btnContainer");

        function startQuiz() {
            document.getElementById("mainTitle").innerHTML = "Квест для коханого 🧩";
            loadQuestion();
        }

        function loadQuestion() {
            const currentQ = questions[currentQuestionIndex];
            
            // Виводимо питання миттєво, без багів друку
            msgElement.innerHTML = `
                <div class="question-title">${currentQ.title}</div>
                <div style="text-align: center; font-size: 1.15rem;">${currentQ.q}</div>
            `;
            
            quizBox.innerHTML = `
                <input type="text" id="answerInput" class="quiz-input" placeholder="Твоя відповідь..." autocomplete="off">
                <button class="btn next-btn" onclick="checkAnswer()">Відповісти</button>
            `;
            
            const input = document.getElementById("answerInput");
            input.focus();
            input.addEventListener("keypress", (e) => {
                if (e.key === "Enter") checkAnswer();
            });
        }

        function checkAnswer() {
            const inputElement = document.getElementById("answerInput");
            if (!inputElement) return;

            const userAns = inputElement.value.trim().toLowerCase().replace(/[^a-zA-Zа-яієїґь0-9\s]/g, "");
            const currentQ = questions[currentQuestionIndex];

            const isCorrect = currentQ.answers.some(ans => {
                const cleanAns = ans.toLowerCase().trim();
                return userAns.includes(cleanAns) || cleanAns.includes(userAns) && userAns.length >= 2;
            });

            if (isCorrect && userAns !== "") {
                spawnParticles(['🖤', '✨', '❤️', '💕'], 35);
                currentQuestionIndex++;
                
                if (currentQuestionIndex < questions.length) {
                    loadQuestion();
                } else {
                    quizBox.innerHTML = "";
                    document.getElementById("mainTitle").innerHTML = "Останнє питання... 👑";
                    msgElement.innerHTML = "Ну все, ти офіційно довів, що найкращий хлопчик і все пам'ятаєш! 🥹<br><br><span style='display:block; text-align:center; font-weight:bold;'>А тепер скажи: ти будеш моїм коханням назавжди?</span>";
                    btnBox.style.display = "flex"; 
                }
            } else {
                spawnParticles(['🌧️', '😭', '💧'], 25);
                inputElement.value = "";
                inputElement.placeholder = "Неправильно... Подумай ще!";
            }
        }

        function spawnParticles(typesArray, count) {
            for (let i = 0; i < count; i++) {
                setTimeout(() => { createParticle(typesArray); }, i * 35);
            }
        }

        function createParticle(typesArray) {
            const container = document.getElementById('effectsContainer');
            const element = document.createElement('div');
            
            element.innerHTML = typesArray[Math.floor(Math.random() * typesArray.length)];
            element.className = 'particle';
            element.style.left = Math.random() * 100 + 'vw';
            element.style.fontSize = Math.random() * 24 + 18 + 'px';
            element.style.animationDuration = Math.random() * 1.2 + 1.4 + 's'; 
            
            if (typesArray.includes('❤️')) {
                element.style.filter = `drop-shadow(0 0 8px rgba(138, 43, 226, 0.6))`;
            }
            
            container.appendChild(element);
            setTimeout(() => { element.remove(); }, 2200);
        }

        function moveButton(e) {
            if (e) e.preventDefault(); 
            const noBtn = document.getElementById('noBtn');
            const padding = 35;
            
            const maxX = window.innerWidth - noBtn.offsetWidth - padding;
            const maxY = window.innerHeight - noBtn.offsetHeight - padding;
            
            const randomX = Math.max(padding, Math.floor(Math.random() * maxX));
            const randomY = Math.max(padding, Math.floor(Math.random() * maxY));
            
            noBtn.style.position = 'fixed';
            noBtn.style.left = randomX + 'px';
            noBtn.style.top = randomY + 'px';
        }

        function celebrate() {
            document.getElementById("mainTitle").innerHTML = "Моє серце твоє! 👑❤️";
            msgElement.style.textAlign = "center";
            msgElement.innerHTML = "Я знала, що ти вибереш цей варіант (іншого ж і не було, хіхі)!<br><br>Дякую, що ти є. Ти робиш мене найщасливішою дівчиною у світі! Обіймаю тебе дуже-дуже міцно і вже чекаю в качці пабгу або в житті! 😘";
            
            btnBox.style.display = "none"; 
            spawnParticles(['🖤', '✨', '❤️', '💕', '👑'], 80); 
        }
    </script>
</body>
</html>
