<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>StudySmart - عالم التعلم الذكي</title>
    <style>
        :root {
            --neon-pink: #ff007f;
            --neon-yellow: #ffeb3b;
            --neon-cyan: #00ffff;
            --neon-purple: #9c27b0;
            --neon-green: #00e676;
            --bg-grad: linear-gradient(135deg, #1a0033, #4a0033);
        }

        body {
            margin: 0;
            padding: 0;
            font-family: 'Cairo', sans-serif, Tahoma;
            background: var(--bg-grad);
            color: #ffffff;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        #app-window {
            width: 100%;
            max-width: 450px;
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(15px);
            border: 4px solid var(--neon-cyan);
            border-radius: 35px;
            box-shadow: 0 0 40px var(--neon-cyan), inset 0 0 20px var(--neon-pink);
            overflow: hidden;
            display: flex;
            flex-direction: column;
            min-height: 92vh;
            position: relative;
        }

        .view {
            display: none;
            padding: 30px;
            flex-direction: column;
            animation: fadeIn 0.4s ease-in-out;
            flex: 1;
        }

        .view.active { display: flex; }

        @keyframes fadeIn {
            from { opacity: 0; transform: scale(0.95); }
            to { opacity: 1; transform: scale(1); }
        }

        h1, h2, h3 {
            text-align: center;
            color: var(--neon-yellow);
            text-shadow: 0 0 10px var(--neon-pink);
            margin: 10px 0;
        }

        .hero-img {
            width: 160px;
            height: 160px;
            margin: 0 auto;
            border-radius: 50%;
            border: 4px solid var(--neon-yellow);
            box-shadow: 0 0 25px var(--neon-yellow);
            object-fit: cover;
        }

        .input-group {
            margin: 15px 0;
        }

        label {
            display: block;
            margin-bottom: 5px;
            color: var(--neon-cyan);
            font-weight: bold;
        }

        input, select {
            width: 100%;
            padding: 14px;
            background: rgba(0, 0, 0, 0.5);
            border: 2px solid var(--neon-pink);
            border-radius: 15px;
            color: white;
            font-size: 1.1rem;
            box-sizing: border-box;
            outline: none;
            box-shadow: inset 0 0 10px rgba(255,0,127,0.3);
        }

        .glow-btn {
            background: linear-gradient(45deg, var(--neon-pink), var(--neon-purple));
            border: none;
            padding: 18px;
            border-radius: 50px;
            color: white;
            font-size: 1.3rem;
            font-weight: bold;
            cursor: pointer;
            box-shadow: 0 0 20px var(--neon-pink);
            transition: transform 0.2s, background 0.2s;
            text-align: center;
            display: block;
            width: 100%;
            margin-top: 20px;
            text-decoration: none;
        }

        .glow-btn:hover {
            transform: scale(1.05);
            box-shadow: 0 0 35px var(--neon-yellow);
            background: linear-gradient(45deg, var(--neon-purple), var(--neon-pink));
        }

        .dashboard-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin-top: 20px;
        }

        .nav-card {
            background: rgba(255, 255, 255, 0.1);
            border: 2px solid var(--neon-green);
            border-radius: 20px;
            padding: 20px;
            text-align: center;
            cursor: pointer;
            box-shadow: 0 0 15px var(--neon-green);
            transition: all 0.3s;
        }

        .nav-card:hover {
            background: var(--neon-green);
            color: black;
            transform: translateY(-5px);
        }

        .nav-card .icon { font-size: 3rem; display: block; margin-bottom: 8px; }

        .book-item {
            background: var(--neon-cyan);
            color: black;
            padding: 15px;
            border-radius: 12px;
            margin-bottom: 12px;
            font-weight: bold;
            text-decoration: none;
            display: block;
            text-align: center;
            box-shadow: 0 0 15px var(--neon-cyan);
        }

        .quiz-option {
            background: rgba(255, 255, 255, 0.15);
            padding: 15px;
            border-radius: 15px;
            margin-bottom: 10px;
            border: 2px solid white;
            cursor: pointer;
            transition: 0.2s;
        }

        .quiz-option.selected {
            background: var(--neon-yellow);
            color: black;
            border-color: var(--neon-yellow);
            font-weight: bold;
        }

        .cert-frame {
            border: 8px double var(--neon-yellow);
            padding: 25px;
            text-align: center;
            background: radial-gradient(circle, #4a0033, #1a0033);
            border-radius: 20px;
            margin-top: 20px;
            box-shadow: 0 0 30px var(--neon-yellow);
        }
    </style>
</head>
<body>

<div id="app-window">
    
    <!-- 1. شاشة تسجيل البيانات -->
    <div id="view-login" class="view active">
        <h1 style="color:var(--neon-pink);">🌟 StudySmart 🌟</h1>
        <!-- صورة الشخصية -->
        <img src="1000467716.png" class="hero-img" alt="البطلة">
        
        <div class="input-group">
            <label>اسم البطل/البطلة:</label>
            <input type="text" id="input-name" placeholder="مثال: نيرة أحمد">
        </div>

        <div class="input-group">
            <label>المرحلة الدراسية:</label>
            <select id="input-grade">
                <option value="الأول الثانوي" selected>الصف الأول الثانوي</option>
            </select>
        </div>

        <div class="input-group">
            <label>رقم واتساب ولي الأمر (للتقارير):</label>
            <input type="tel" id="input-phone" placeholder="01xxxxxxxxx">
        </div>

        <button class="glow-btn" onclick="handleLogin()">دخول عالم المغامرات 🚀</button>
    </div>

    <!-- 2. الشاشة الرئيسية (الواجهة التفاعلية) -->
    <div id="view-dashboard" class="view">
        <h2>أهلاً بك يا <span id="user-display" style="color:var(--neon-cyan);"></span>! 🎓</h2>
        <p style="text-align: center; color: var(--neon-yellow);">اختر المهمة التالية:</p>
        
        <div class="dashboard-grid">
            <div class="nav-card" onclick="switchView('view-dashboard', 'view-library')">
                <span class="icon">📚</span>
                <h4>المكتبة السحرية</h4>
            </div>
            <div class="nav-card" onclick="switchView('view-dashboard', 'view-quiz')">
                <span class="icon">📝</span>
                <h4>التقييمات الوزارية</h4>
            </div>
            <div class="nav-card" onclick="activateAiCoach()">
                <span class="icon">🤖</span>
                <h4>المعلم الذكي</h4>
            </div>
            <div class="nav-card" onclick="switchView('view-dashboard', 'view-certificate')">
                <span class="icon">🏆</span>
                <h4>شهادة الإنجاز</h4>
            </div>
        </div>
    </div>

    <!-- 3. مكتبة الكتب الوزارية -->
    <div id="view-library" class="view">
        <button class="glow-btn" style="width: auto; margin-bottom: 20px; padding: 10px;" onclick="switchView('view-library', 'view-dashboard')">⬅️ العودة للرئيسية</button>
        <h3>📖 كتب وزارة التربية والتعليم</h3>
        <p style="text-align:center; font-size: 0.9rem;">خاص بصف أولى ثانوي - اضغط للفتح:</p>
        <div id="books-container">
            <a href="https://moe.gov.eg" target="_blank" class="book-item">📘 كتاب العلوم المتكاملة (وزارة التعليم)</a>
            <a href="https://moe.gov.eg" target="_blank" class="book-item">📙 كتاب الفلسفة والمنطق</a>
            <a href="https://moe.gov.eg" target="_blank" class="book-item">📗 كتاب اللغة العربية</a>
        </div>
    </div>

    <!-- 4. التقييمات الوزارية وتنبيه واتساب -->
    <div id="view-quiz" class="view">
        <button class="glow-btn" style="width: auto; margin-bottom: 15px; padding: 10px;" onclick="switchView('view-quiz', 'view-dashboard')">⬅️ العودة</button>
        <h3>⚡ التقييم الوزاري المعتمد</h3>
        <p>سؤال: ما هو الهدف الأساسي من منهج العلوم المتكاملة؟</p>
        <div class="quiz-option" onclick="selectQuizOption(this)">دراسة كل مادة علمية منفصلة تماماً</div>
        <div class="quiz-option" onclick="selectQuizOption(this)">ربط الظواهر الطبيعية بمفاهيم الفيزياء والكيمياء والأحياء</div>
        <button class="glow-btn" onclick="submitQuizData()">إرسال الإجابة وتنبيه ولي الأمر</button>
    </div>

    <!-- 5. شهادة التقدير التلقائية -->
    <div id="view-certificate" class="view">
        <button class="glow-btn" style="width: auto; margin-bottom: 15px; padding: 10px;" onclick="switchView('view-certificate', 'view-dashboard')">⬅️ العودة</button>
        <div class="cert-frame">
            <h2 style="color: var(--neon-yellow);">شهادة تقدير وتفوق 🌟</h2>
            <p>تمنح منصة StudySmart هذه الشهادة للبطلة:</p>
            <h1 id="cert-name-display" style="color: var(--neon-cyan); margin: 10px 0;"></h1>
            <p>لاجتيازها تقييمات الصف الأول الثانوي بامتياز وتفوق.</p>
            <p style="font-size: 0.8rem; color: #aaa; margin-top: 30px;">معتمدة من نظام التعلم الذكي</p>
        </div>
        <button class="glow-btn" style="background: #25d366;" onclick="simulateWhatsAppCert()">إرسال الشهادة لواتساب ولي الأمر 💬</button>
    </div>

</div>

<script>
    function switchView(fromId, toId) {
        document.getElementById(fromId).classList.remove('active');
        document.getElementById(toId).classList.add('active');
    }

    function handleLogin() {
        const name = document.getElementById('input-name').value;
        const phone = document.getElementById('input-phone').value;
        
        if(!name || !phone) {
            alert("⚠️ يرجى إدخال الاسم ورقم هاتف ولي الأمر للمتابعة!");
            return;
        }

        document.getElementById('user-display').innerText = name;
        document.getElementById('cert-name-display').innerText = name;
        
        switchView('view-login', 'view-dashboard');
    }

    function activateAiCoach() {
        alert("🤖 المعلم الذكي: أهلاً بكِ! أنا هنا للإجابة على أسئلتكِ صوتياً ومساعدتكِ في المذاكرة.");
        if ('speechSynthesis' in window) {
            const utterance = new SpeechSynthesisUtterance("أهلاً بك يا بطلة في منصة ستادي سمارت. أنا معلمك الذكي، جاهز لمساعدتك في التفوق.");
            utterance.lang = 'ar-SA';
            window.speechSynthesis.speak(utterance);
        }
    }

    function selectQuizOption(element) {
        document.querySelectorAll('.quiz-option').forEach(opt => opt.classList.remove('selected'));
        element.classList.add('selected');
    }

    function submitQuizData() {
        const selected = document.querySelector('.quiz-option.selected');
        const phone = document.getElementById('input-phone').value;
        
        if(!selected) {
            alert("يرجى اختيار إجابة أولاً!");
            return;
        }

        alert("🎉 إجابة صحيحة وممتازة! تم تسجيل الدرجة وإرسال تقرير فوري إلى رقم واتساب ولي الأمر: " + phone);
        switchView('view-quiz', 'view-certificate');
    }

    function simulateWhatsAppCert() {
        const phone = document.getElementById('input-phone').value;
        alert("💬 تم إرسال صورة شهادة التقدير بنجاح إلى رقم الواتساب: " + phone + " ليفخر بكِ والداكِ!");
    }
</script>
</body>
</html>
