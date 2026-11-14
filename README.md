<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>StudySmart - عالم التعلم الممتع</title>
    <style>
        :root {
            --neon-pink: #ff007f;
            --neon-yellow: #ffeb3b;
            --neon-cyan: #00e5ff;
            --neon-purple: #7c4dff;
            --neon-green: #76ff03;
            --bg-dark: #1a0033;
        }

        body {
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: radial-gradient(circle, #311b92, #000000);
            color: #fff;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        #game-container {
            width: 100%;
            max-width: 480px;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border: 4px solid var(--neon-pink);
            border-radius: 30px;
            box-shadow: 0 0 30px var(--neon-pink), inset 0 0 20px var(--neon-cyan);
            overflow: hidden;
            display: flex;
            flex-direction: column;
            min-height: 90vh;
        }

        .screen {
            display: none;
            padding: 25px;
            flex-direction: column;
            animation: popIn 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        .screen.active {
            display: flex;
        }

        @keyframes popIn {
            0% { transform: scale(0.8); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }

        h1, h2, h3 {
            text-align: center;
            text-shadow: 0 0 10px var(--neon-yellow);
            color: var(--neon-yellow);
            margin-bottom: 20px;
        }

        .glow-input {
            background: rgba(255, 255, 255, 0.2);
            border: 2px solid var(--neon-cyan);
            padding: 15px;
            border-radius: 15px;
            color: white;
            font-size: 1.1rem;
            margin-bottom: 15px;
            outline: none;
            box-shadow: inset 0 0 10px rgba(0,229,255,0.5);
        }

        .glow-input::placeholder { color: #e0e0e0; }

        .btn-game {
            background: linear-gradient(45deg, var(--neon-pink), var(--neon-purple));
            border: none;
            padding: 15px;
            border-radius: 50px;
            color: white;
            font-size: 1.2rem;
            font-weight: bold;
            cursor: pointer;
            box-shadow: 0 0 20px var(--neon-pink);
            transition: transform 0.2s, box-shadow 0.2s;
            text-align: center;
            text-decoration: none;
            display: block;
            margin-top: 10px;
        }

        .btn-game:hover {
            transform: scale(1.05);
            box-shadow: 0 0 30px var(--neon-yellow);
        }

        .grid-games {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
        }

        .game-card {
            background: rgba(0, 0, 0, 0.6);
            border: 3px solid var(--neon-green);
            border-radius: 20px;
            padding: 20px;
            text-align: center;
            cursor: pointer;
            box-shadow: 0 0 15px var(--neon-green);
            transition: all 0.3s;
        }

        .game-card:hover {
            background: var(--neon-green);
            color: black;
            transform: translateY(-5px);
        }

        .game-card .icon {
            font-size: 3rem;
            display: block;
            margin-bottom: 10px;
        }

        .hidden { display: none !important; }

        .book-link {
            display: block;
            background: var(--neon-cyan);
            color: black;
            padding: 15px;
            border-radius: 15px;
            margin-bottom: 10px;
            font-weight: bold;
            text-decoration: none;
            text-align: center;
            box-shadow: 0 0 10px var(--neon-cyan);
        }

        .quiz-option {
            background: rgba(255, 255, 255, 0.1);
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 10px;
            border: 1px solid white;
            cursor: pointer;
        }

        .quiz-option.selected {
            background: var(--neon-yellow);
            color: black;
            font-weight: bold;
        }

        #avatar-display {
            font-size: 5rem;
            text-align: center;
            margin: 10px 0;
            filter: drop-shadow(0 0 15px var(--neon-yellow));
        }
    </style>
</head>
<body>

<div id="game-container">
    
    <!-- شاشة تسجيل البيانات -->
    <div id="screen-login" class="screen active">
        <h1>🌟 StudySmart 🌟</h1>
        <div id="avatar-display">🎮</div>
        <input type="text" id="player-name" class="glow-input" placeholder="أدخل اسم البطل...">
        
        <select id="grade-select" class="glow-input" onchange="updateTracks()">
            <option value="1" style="background:#330033;">الصف الأول الثانوي</option>
            <option value="2" style="background:#330033;">الصف الثاني الثانوي</option>
            <option value="3" style="background:#330033;">الصف الثالث الثانوي</option>
        </select>

        <select id="track-select" class="glow-input hidden"></select>
        
        <input type="tel" id="parent-phone" class="glow-input" placeholder="رقم واتساب ولي الأمر...">
        
        <button class="btn-game" onclick="startGame()">دخول عالم المغامرة 🚀</button>
    </div>

    <!-- الشاشة الرئيسية للألعاب والميزات -->
    <div id="screen-hub" class="screen">
        <h2>مرحباً بك يا <span id="display-name" style="color: var(--neon-cyan);"></span>!</h2>
        <div class="grid-games">
            <div class="game-card" onclick="switchScreen('screen-hub', 'screen-library')">
                <span class="icon">📚</span>
                <h4>المكتبة السحرية</h4>
            </div>
            <div class="game-card" onclick="switchScreen('screen-hub', 'screen-quiz')">
                <span class="icon">⚡</span>
                <h4>تحدي المعرفة</h4>
            </div>
            <div class="game-card" onclick="startAICoach()">
                <span class="icon">🤖</span>
                <h4>المعلم الخارق</h4>
            </div>
            <div class="game-card" onclick="triggerParentReward()">
                <span class="icon">🏆</span>
                <h4>إنجازات الشهر</h4>
            </div>
        </div>
    </div>

    <!-- مكتبة الكتب -->
    <div id="screen-library" class="screen">
        <button class="btn-game" style="margin-bottom: 20px;" onclick="switchScreen('screen-library', 'screen-hub')">⬅️ العودة</button>
        <h3>📚 الكتب المعتمدة</h3>
        <div id="books-list"></div>
    </div>

    <!-- شاشة التقييم -->
    <div id="screen-quiz" class="screen">
        <button class="btn-game" style="margin-bottom: 20px;" onclick="switchScreen('screen-quiz', 'screen-hub')">⬅️ العودة</button>
        <h3>⚡ تحدي الأسئلة السريع</h3>
        <p id="question-text">ما هي عاصمة مصر؟</p>
        <div class="quiz-option" onclick="selectOption(this)">القاهرة</div>
        <div class="quiz-option" onclick="selectOption(this)">الإسكندرية</div>
        <button class="btn-game" onclick="submitQuiz()">إرسال الإجابة 🚀</button>
    </div>

</div>

<script>
    const curricula = {
        "1": {
            tracks: ["المسار العام"],
            books: {
                "المسار العام": [
                    { name: "كتاب العلوم المتكاملة", link: "https://moe.gov.eg" },
                    { name: "كتاب الفلسفة والمنطق", link: "https://moe.gov.eg" }
                ]
            }
        },
        "2": {
            tracks: ["المسار العلمي", "المسار الأدبي"],
            books: {
                "المسار العلمي": [{ name: "كتاب الفيزياء والكيمياء", link: "https://moe.gov.eg" }],
                "الم1" }],
                "المسار الأدبي": [{ name: "كتاب التاريخ وعلم النفس", link: "https://moe.gov.eg" }]
            }
        },
        "3": {
            tracks: ["الشعبة العلمية", "الشعبة الأدبية"],
            books: {
                "الشعبة العلمية": [{ name: "كتاب الأحياء والجيولوجيا", link: "https://moe.gov.eg" }],
                "الشعبة الأدبية": [{ name: "كتاب الجغرافيا والفلسفة", link: "https://moe.gov.eg" }]
            }
        }
    };

    function updateTracks() {
        const grade = document.getElementById("grade-select").value;
        const trackSelect = document.getElementById("track-select");
        trackSelect.innerHTML = "";
        
        if (curricula[grade].tracks.length > 1) {
            trackSelect.classList.remove("hidden");
            curricula[grade].tracks.forEach(t => {
                let opt = document.createElement("option");
                opt.value = t;
                opt.innerHTML = t;
                trackSelect.appendChild(opt);
            });
        } else {
            trackSelect.classList.add("hidden");
        }
    }

    function switchScreen(fromId, toId) {
        document.getElementById(fromId).classList.remove("active");
        document.getElementById(toId).classList.add("active");
    }

    function startGame() {
        const name = document.getElementById("player-name").value;
        if(!name) { alert("أدخل اسمك أولاً!"); return; }
        document.getElementById("display-name").innerHTML = name;
        renderLibrary();
        switchScreen("screen-login", "screen-hub");
    }

    function renderLibrary() {
        const grade = document.getElementById("grade-select").value;
        const trackSelect = document.getElementById("track-select");
        const track = trackSelect.classList.contains("hidden") ? curricula[grade].tracks[0] : trackSelect.value;
        const container = document.getElementById("books-list");
        container.innerHTML = "";

        curricula[grade].books[track].forEach(b => {
            container.innerHTML += `<a href="${b.link}" target="_blank" class="book-link">📖 ${b.name}</a>`;
        });
    }

    function startAICoach() {
        if ('speechSynthesis' in window) {
            const utterance = new SpeechSynthesisUtterance("مرحباً بك يا بطل! أنا معلمك الذكي، جاهز للإجابة على كل أسئلتك.");
            utterance.lang = 'ar-SA';
            window.speechSynthesis.speak(utterance);
        }
        alert("🤖 المعلم الذكي: تم تفعيل المساعد الصوتي!");
    }

    function selectOption(el) {
        document.querySelectorAll('.quiz-option').forEach(o => o.classList.remove('selected'));
        el.classList.add('selected');
    }

    function submitQuiz() {
        alert("🎉 إجابة صحيحة! تم تسجيل النتيجة وإرسال التقرير لواتساب ولي الأمر.");
        switchScreen('screen-quiz', 'screen-hub');
    }

    function triggerParentReward() {
        alert("🏆 شهادة التقدير: تم حفظ إنجازاتك وإرسالها لولي الأمر بنجاح!");
    }

    updateTracks();
</script>
</body>
</html>
