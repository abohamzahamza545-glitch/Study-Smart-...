<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>StudySmart - منصة التعلم الذكي</title>
    <style>
        :root {
            --neon-pink: #ff007f;
            --neon-yellow: #ffeb3b;
            --neon-cyan: #00ffff;
            --neon-purple: #9c27b0;
            --neon-green: #00e676;
            --party-grad: linear-gradient(135deg, #ff007f, #9c27b0, #00ffff, #00e676);
        }

        body {
            margin: 0;
            padding: 0;
            font-family: 'Cairo', sans-serif, Tahoma;
            background: #1a052e;
            background-image: radial-gradient(circle, #380a59 10%, transparent 10%), radial-gradient(circle, #ff007f 10%, transparent 11%), radial-gradient(circle, #00ffff 10%, transparent 11%);
            background-size: 50px 50px;
            color: #ffffff;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        #app-container {
            width: 100%;
            max-width: 500px;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(20px);
            border: 5px solid var(--neon-yellow);
            border-radius: 40px;
            box-shadow: 0 0 50px var(--neon-pink), inset 0 0 30px var(--neon-cyan);
            overflow: hidden;
            display: flex;
            flex-direction: column;
            min-height: 95vh;
            position: relative;
        }

        .screen {
            display: none;
            padding: 30px;
            flex-direction: column;
            flex: 1;
            animation: popIn 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        .screen.active { display: flex; }

        @keyframes popIn {
            0% { transform: scale(0.8); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }

        h1, h2, h3 {
            text-align: center;
            color: var(--neon-yellow);
            text-shadow: 0 0 10px var(--neon-pink), 0 0 20px var(--neon-pink);
            margin: 10px 0;
            font-size: 2rem;
        }

        .cartoon-banner {
            background: var(--party-grad);
            padding: 15px;
            border-radius: 25px;
            text-align: center;
            font-size: 2.5rem;
            margin-bottom: 15px;
            box-shadow: 0 0 20px var(--neon-yellow);
        }

        .user-profile-circle {
            width: 125px;
            height: 125px;
            border-radius: 50%;
            border: 4px solid var(--neon-cyan);
            box-shadow: 0 0 35px var(--neon-cyan);
            margin: 15px auto;
            overflow: hidden;
            background: #fff;
        }

        .user-profile-circle img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .input-wrapper { margin: 15px 0; }
        label { display: block; margin-bottom: 8px; color: var(--neon-cyan); font-weight: bold; font-size: 1.1rem; text-shadow: 0 0 5px #000; }
        input, select {
            width: 100%;
            padding: 16px;
            background: rgba(0, 0, 0, 0.6);
            border: 3px solid var(--neon-pink);
            border-radius: 20px;
            color: var(--neon-yellow);
            font-size: 1.2rem;
            font-weight: bold;
            box-sizing: border-box;
            outline: none;
            box-shadow: inset 0 0 10px var(--neon-pink);
        }

        .nav-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin-top: 15px;
        }

        .nav-tile {
            background: linear-gradient(135deg, rgba(255,255,255,0.15), rgba(255,255,255,0.05));
            border: 3px solid var(--neon-green);
            border-radius: 25px;
            padding: 20px;
            text-align: center;
            cursor: pointer;
            box-shadow: 0 0 15px var(--neon-green);
            transition: transform 0.2s;
        }

        .nav-tile:hover {
            transform: scale(1.08);
            background: var(--neon-green);
            color: black;
        }

        .nav-tile .icon { font-size: 3.5rem; display: block; margin-bottom: 5px; }

        .resource-link {
            background: var(--neon-cyan);
            color: black;
            padding: 16px;
            border-radius: 20px;
            margin-bottom: 15px;
            font-weight: bold;
            text-decoration: none;
            display: block;
            text-align: center;
            box-shadow: 0 0 18px var(--neon-cyan);
            font-size: 1.2rem;
        }

        .quiz-choice {
            background: rgba(255, 255, 255, 0.2);
            padding: 16px;
            border-radius: 20px;
            margin-bottom: 12px;
            border: 3px solid var(--neon-yellow);
            cursor: pointer;
            font-size: 1.2rem;
            color: #fff;
        }

        .quiz-choice.selected {
            background: var(--neon-yellow);
            color: black;
            font-weight: bold;
            box-shadow: 0 0 25px var(--neon-yellow);
        }

        .certificate-sheet {
            border: 12px double var(--neon-yellow);
            padding: 30px;
            text-align: center;
            background: radial-gradient(circle, #9c27b0, #3f51b5);
            border-radius: 30px;
            margin-top: 15px;
            box-shadow: 0 0 40px var(--neon-yellow);
        }

        .hidden { display: none !important; }
        .action-btn { background: #25d366; border: none; padding: 18px; border-radius: 40px; color: white; font-size: 1.3rem; font-weight: bold; cursor: pointer; width: 100%; margin-top: 20px; box-shadow: 0 0 20px #25d366; }
    </style>
</head>
<body>

<div id="app-container">
    
    <!-- 1. شاشة البيانات -->
    <div id="screen-login" class="screen active">
        <div class="cartoon-banner">🎓 🌟 📚 🎒</div>
        <h1>StudySmart</h1>
        <div class="user-profile-circle">
            <img src="1000467716.png" alt="البطلة">
        </div>
        
        <div class="input-wrapper">
            <label>اسم البطلة:</label>
            <input type="text" id="reg-name" placeholder="اكتبي الاسم هنا...">
        </div>

        <div class="input-wrapper">
            <label>المرحلة الدراسية:</label>
            <select id="reg-grade" onchange="populateTracks()">
                <option value="1">الصف الأول الثانوي</option>
                <option value="2">الصف الثاني الثانوي (نظام البكالوريا)</option>
                <option value="3">الصف الثالث الثانوي</option>
            </select>
        </div>

        <div id="track-wrapper" class="input-wrapper hidden">
            <label>المسار / الشعبة:</label>
            <select id="reg-track"></select>
        </div>

        <div class="input-wrapper">
            <label>رقم واتساب ولي الأمر:</label>
            <input type="tel" id="reg-phone" placeholder="01xxxxxxxxx" oninput="checkAutoLogin()">
        </div>
    </div>

    <!-- 2. لوحة التحكم الرئيسية -->
    <div id="screen-dashboard" class="screen">
        <div class="cartoon-banner">🎉 👩‍🎓 🏆 🚀</div>
        <div class="user-profile-circle">
            <img src="1000467716.png" alt="صورة الطالبة">
        </div>
        <h2>أهلاً بكِ يا <span id="dash-user" style="color:var(--neon-cyan);"></span>!</h2>
        <h4 style="color: var(--neon-yellow); text-align: center;" id="dash-level-info"></h4>
        
        <div class="nav-grid">
            <div class="nav-tile" onclick="openSection('screen-library')">
                <span class="icon">📚</span><h4>المكتبة المرحة</h4>
            </div>
            <div class="nav-tile" onclick="openSection('screen-assessment-hub')">
                <span class="icon">📝</span><h4>كوكب التقييمات</h4>
            </div>
            <div class="nav-tile" onclick="runAiCoach()">
                <span class="icon">🤖</span><h4>المعلم الذكي</h4>
            </div>
            <div class="nav-tile" onclick="openSection('screen-monthly-exam')">
                <span class="icon">🏆</span><h4>تحدي الشهر</h4>
            </div>
            <div class="nav-tile" onclick="openSection('screen-homework')">
                <span class="icon">🏠</span><h4>المهام المنزلية</h4>
            </div>
            <div class="nav-tile" onclick="openSection('screen-classwork')">
                <span class="icon">🏫</span><h4>أنشطة الفصل</h4>
            </div>
            <div class="nav-tile" onclick="openSection('screen-reports')">
                <span class="icon">📊</span><h4>تقارير الأهل</h4>
            </div>
            <div class="nav-tile" onclick="openSection('screen-certificate')">
                <span class="icon">🎖️</span><h4>لوحة الشرف</h4>
            </div>
        </div>
    </div>

    <!-- 3. المكتبة الرقمية -->
    <div id="screen-library" class="screen">
        <h3>📖 الكتب والمناهج الممتعة</h3>
        <div id="library-books-list"></div>
    </div>

    <!-- 4. مركز التقييمات -->
    <div id="screen-assessment-hub" class="screen">
        <h3>📝 اختبارات التقييم الوزاري</h3>
        <div class="nav-grid">
            <div class="nav-tile" onclick="loadQuizModel(1)"><span class="icon">1️⃣</span><h4>النموذج الأول</h4></div>
            <div class="nav-tile" onclick="loadQuizModel(2)"><span class="icon">2️⃣</span><h4>النموذج الثاني</h4></div>
            <div class="nav-tile" onclick="loadQuizModel(3)"><span class="icon">3️⃣</span><h4>النموذج الثالث</h4></div>
        </div>
    </div>

    <!-- 5. نافذة الاختبار الفعلي -->
    <div id="screen-active-quiz" class="screen">
        <h3 id="quiz-title-header">التقييم الوزاري</h3>
        <div id="quiz-progress" style="text-align: center; color: var(--neon-cyan); font-weight: bold;"></div>
        <div id="quiz-question-box" style="font-size: 1.3rem; margin: 20px 0; text-align: center;"></div>
        <div id="quiz-options-area"></div>
        <button class="action-btn" id="quizSubmitBtn" onclick="processQuizAnswer()">تثبيت الإجابة والتالي ➡️</button>
    </div>

    <!-- 6. الأداءات المنزلية -->
    <div id="screen-homework" class="screen">
        <h3>🏠 المهام والتدريبات المنزلية</h3>
        <div id="homework-list"></div>
    </div>

    <!-- 7. الأداءات الصفية -->
    <div id="screen-classwork" class="screen">
        <h3>🏫 الأنشطة الصفية التفاعلية</h3>
        <div id="classwork-list"></div>
    </div>

    <!-- 8. امتحان الشهر الشامل -->
    <div id="screen-monthly-exam" class="screen">
        <h3>🏆 التحدي الختامي للشهر</h3>
        <div class="nav-tile" style="border-color: var(--neon-yellow); margin: 30px auto; width: 80%;" onclick="startFinalMonthlyExam()">
            <span class="icon">🔥</span><h4>بدء التحدي الكبير</h4>
        </div>
    </div>

    <!-- 9. تقارير ولي الأمر -->
    <div id="screen-reports" class="screen">
        <h3>📊 إرسال التقارير للأهل</h3>
        <div style="background: rgba(255,255,255,0.1); padding: 20px; border-radius: 20px; margin: 15px 0;">
            <p><strong>الطالبة:</strong> <span id="rpt-name"></span></p>
            <p><strong>المسار:</strong> <span id="rpt-track"></span></p>
        </div>
        <button class="action-btn" onclick="dispatchWhatsAppReport()">إرسال التقرير لواتساب 💬</button>
    </div>

    <!-- 10. الشهادة الفخرية -->
    <div id="screen-certificate" class="screen">
        <div class="certificate-sheet">
            <h1>🌟 شهادة التميز والتفوق 🌟</h1>
            <p>تمنح منصة StudySmart هذه الشهادة للبطلة:</p>
            <h1 id="cert-student-name" style="color: var(--neon-cyan);"></h1>
            <p id="cert-path-text"></p>
        </div>
        <button class="action-btn" onclick="dispatchWhatsAppCertificate()">مشاركة الشهادة مع الأهل 💬</button>
    </div>

</div>

<script>
    const educationalDatabase = {
        "1": {
            tracks: ["المسار العام المطور"],
            curricula: { "المسار العام المطور": [{ name: "📘 كتاب العلوم المتكاملة", link: "https://moe.gov.eg" }] },
            homework: ["حل تدريبات العلوم"], classwork: ["مناقشة تفاعلية"],
            models: [[{ Q: "ما هي المادة التي تدمج العلوم؟", opts: ["الفيزياء", "العلوم المتكاملة", "الأحياء"], ans: 1 }]]
        },
        "2": {
            tracks: ["شعبة علمي علوم", "شعبة علمي رياضة", "الشعبة الأدبية", "الشعبة التكنولوجية"],
            curricula: {
                "شعبة علمي علوم": [{ name: "🔬 الأحياء المتقدم", link: "https://moe.gov.eg" }],
                "شعبة علمي رياضة": [{ name: "📐 الرياضيات البحتة", link: "https://moe.gov.eg" }],
                "الشعبة الأدبية": [{ name: "📜 التاريخ المعاصر", link: "https://moe.gov.eg" }],
                "الشعبة التكنولوجية": [{ name: "🤖 الذكاء الاصطناعي", link: "https://moe.gov.eg" }]
            },
            homework: ["حل مسائـل التخصص"], classwork: ["تجربة معملية"],
            models: [[{ Q: "ما هي سمة نظام البكالوريا؟", opts: ["الحفظ", "تعدد المسارات", "مادة واحدة"], ans: 1 }]]
        },
        "3": {
            tracks: ["الشعبة العلمية", "الشعبة الأدبية"],
            curricula: {
                "الشعبة العلمية": [{ name: "🧬 الأحياء والجزيئات", link: "https://moe.gov.eg" }],
                "الشعبة الأدبية": [{ name: "🏛️ الفلسفة التطبيقية", link: "https://moe.gov.eg" }]
            },
            homework: ["حل نماذج امتحانات"], classwork: ["محاكاة الامتحانات"],
            models: [[{ Q: "ما هدف نظام التقييم الجديد؟", opts: ["قياس الفهم", "الحفظ التام", "الرسوب"], ans: 0 }]]
        }
    };

    let currentUserData = {};
    let currentQuizModel = [], currentQuestionIndex = 0, userScore = 0, selectedOptionIndex = null, activeCategoryType = "";

    function populateTracks() {
        const grade = document.getElementById("reg-grade").value;
        const wrapper = document.getElementById("track-wrapper");
        const select = document.getElementById("reg-track");
        select.innerHTML = "";
        const tracks = educationalDatabase[grade].tracks;
        if(tracks.length > 1) {
            tracks.forEach(t => select.innerHTML += `<option value="${t}">${t}</option>`);
            wrapper.classList.remove("hidden");
        } else {
            wrapper.classList.add("hidden");
            select.innerHTML = `<option value="${tracks[0]}">${tracks[0]}</option>`;
        }
    }

    function checkAutoLogin() {
        const name = document.getElementById("reg-name").value.trim();
        const phone = document.getElementById("reg-phone").value.trim();
        if(name.length > 3 && phone.length >= 10) {
            executeLogin();
        }
    }

    function openSection(screenId) {
        document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
        document.getElementById(screenId).classList.add('active');
    }

    function executeLogin() {
        const name = document.getElementById("reg-name").value.trim();
        const phone = document.getElementById("reg-phone").value.trim();
        const gradeText = document.getElementById("reg-grade").options[document.getElementById("reg-grade").selectedIndex].text;
        const trackVal = document.getElementById("reg-track").value;

        currentUserData = { name, track: trackVal };

        document.getElementById("dash-user").innerText = name;
        document.getElementById("dash-level-info").innerText = gradeText + " (" + trackVal + ")";
        document.getElementById("rpt-name").innerText = name;
        document.getElementById("rpt-track").innerText = trackVal;
        document.getElementById("cert-student-name").innerText = name;
        document.getElementById("cert-path-text").innerText = trackVal;

        renderLibraryList();
        renderHomeworkList();
        renderClassworkList();
        openSection("screen-dashboard");
    }

    function renderLibraryList() {
        const container = document.getElementById("library-books-list");
        container.innerHTML = "";
        educationalDatabase["1"].curricula["المسار العام المطور"].forEach(b => {
            container.innerHTML += `<a href="${b.link}" target="_blank" class="resource-link">${b.name}</a>`;
        });
    }

    function renderHomeworkList() {
        const container = document.getElementById("homework-list");
        container.innerHTML = `<div class="quiz-choice">📋 حل تدريبات العلوم</div>`;
    }

    function renderClassworkList() {
        const container = document.getElementById("classwork-list");
        container.innerHTML = `<div class="quiz-choice">🏫 مناقشة تفاعلية</div>`;
    }

    function loadQuizModel(modelNumber) {
        activeCategoryType = 'assessment';
        currentQuizModel = educationalDatabase["1"].models[0];
        document.getElementById("quiz-title-header").innerText = "اختبار التحدي (" + modelNumber + ")";
        startQuizSession();
    }

    function startFinalMonthlyExam() {
        activeCategoryType = 'monthly';
        currentQuizModel = educationalDatabase["1"].models[0];
        document.getElementById("quiz-title-header").innerText = "🔥 تحدي الشهر الكبير";
        startQuizSession();
    }

    function startQuizSession() {
        currentQuestionIndex = 0; userScore = 0;
        openSection("screen-active-quiz");
        renderQuestionCard();
    }

    function renderQuestionCard() {
        const qData = currentQuizModel[currentQuestionIndex];
        document.getElementById("quiz-progress").innerText = "السؤال 1 من 1";
        document.getElementById("quiz-question-box").innerHTML = "❓ " + qData.Q;
        const optArea = document.getElementById("quiz-options-area");
        optArea.innerHTML = "";
        qData.opts.forEach((opt, idx) => {
            optArea.innerHTML += `<div class="quiz-choice" onclick="selectChoice(this, ${idx})">${opt}</div>`;
        });
        selectedOptionIndex = null;
    }

    function selectChoice(el, idx) {
        document.querySelectorAll('.quiz-choice').forEach(c => c.classList.remove('selected'));
        el.classList.add('selected');
        selectedOptionIndex = idx;
    }

    function processQuizAnswer() {
        if(selectedOptionIndex === null) return;
        alert("🎉 إجابة رائعة! تم تسجيل النتيجة.");
        if(activeCategoryType === 'assessment') openSection("screen-assessment-hub");
        else openSection("screen-certificate");
    }

    function runAiCoach() { alert("🤖 المعلم الذكي جاهز للشرح الصوتي!"); }
    function dispatchWhatsAppReport() { alert("💬 تم إرسال التقرير للأهل!"); }
    function dispatchWhatsAppCertificate() { alert("💬 تم إرسال الشهادة للأهل!"); }

    populateTracks();
</script>
</body>
</html>
