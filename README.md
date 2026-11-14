<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>StudySmart - منصة التعلم الذكي المطور</title>
    <style>
        :root {
            --neon-pink: #ff007f;
            --neon-yellow: #ffeb3b;
            --neon-cyan: #00ffff;
            --neon-purple: #9c27b0;
            --neon-green: #00e676;
            --bg-grad: linear-gradient(135deg, #05001a, #240046, #3c096c);
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

        #app-container {
            width: 100%;
            max-width: 500px;
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(25px);
            border: 4px solid var(--neon-cyan);
            border-radius: 45px;
            box-shadow: 0 0 60px var(--neon-cyan), inset 0 0 30px var(--neon-pink);
            overflow: hidden;
            display: flex;
            flex-direction: column;
            min-height: 96vh;
            position: relative;
        }

        .screen {
            display: none;
            padding: 30px;
            flex-direction: column;
            animation: appZoomIn 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            flex: 1;
        }

        .screen.active { display: flex; }

        @keyframes appZoomIn {
            from { opacity: 0; transform: scale(0.9); }
            to { opacity: 1; transform: scale(1); }
        }

        h1, h2, h3, h4 {
            text-align: center;
            color: var(--neon-yellow);
            text-shadow: 0 0 15px var(--neon-pink);
            margin: 10px 0;
        }

        .hero-avatar {
            width: 150px;
            height: 150px;
            margin: 0 auto;
            border-radius: 50%;
            border: 5px solid var(--neon-yellow);
            box-shadow: 0 0 35px var(--neon-yellow);
            object-fit: cover;
            animation: pulseGlow 2s infinite alternate;
        }

        @keyframes pulseGlow {
            from { box-shadow: 0 0 20px var(--neon-yellow); }
            to { box-shadow: 0 0 40px var(--neon-pink); }
        }

        .user-profile-circle {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            border: 4px solid var(--neon-cyan);
            box-shadow: 0 0 20px var(--neon-cyan);
            margin: 10px auto;
            overflow: hidden;
        }

        .user-profile-circle img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .input-wrapper { margin: 15px 0; }
        label { display: block; margin-bottom: 8px; color: var(--neon-cyan); font-weight: bold; font-size: 1.1rem; }
        input, select {
            width: 100%;
            padding: 16px;
            background: rgba(0, 0, 0, 0.7);
            border: 2.5px solid var(--neon-pink);
            border-radius: 20px;
            color: white;
            font-size: 1.15rem;
            box-sizing: border-box;
            outline: none;
            box-shadow: inset 0 0 15px rgba(255,0,127,0.4);
        }

        .action-btn {
            background: linear-gradient(45deg, var(--neon-pink), var(--neon-purple));
            border: none;
            padding: 20px;
            border-radius: 50px;
            color: white;
            font-size: 1.4rem;
            font-weight: bold;
            cursor: pointer;
            box-shadow: 0 0 30px var(--neon-pink);
            transition: transform 0.2s, box-shadow 0.2s;
            text-align: center;
            display: block;
            width: 100%;
            margin-top: 25px;
            text-decoration: none;
        }

        .action-btn:hover {
            transform: scale(1.05);
            box-shadow: 0 0 45px var(--neon-yellow);
        }

        .nav-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 18px;
            margin-top: 20px;
        }

        .nav-tile {
            background: rgba(255, 255, 255, 0.1);
            border: 3px solid var(--neon-green);
            border-radius: 25px;
            padding: 25px;
            text-align: center;
            cursor: pointer;
            box-shadow: 0 0 20px var(--neon-green);
            transition: all 0.3s;
        }

        .nav-tile:hover {
            background: var(--neon-green);
            color: black;
            transform: translateY(-8px);
            box-shadow: 0 0 30px var(--neon-green);
        }

        .nav-tile .icon { font-size: 3.5rem; display: block; margin-bottom: 10px; }

        .resource-link {
            background: var(--neon-cyan);
            color: black;
            padding: 18px;
            border-radius: 18px;
            margin-bottom: 15px;
            font-weight: bold;
            text-decoration: none;
            display: block;
            text-align: center;
            box-shadow: 0 0 20px var(--neon-cyan);
            font-size: 1.2rem;
            transition: transform 0.2s;
        }
        .resource-link:hover { transform: scale(1.03); }

        .quiz-choice {
            background: rgba(255, 255, 255, 0.15);
            padding: 18px;
            border-radius: 20px;
            margin-bottom: 15px;
            border: 2px solid white;
            cursor: pointer;
            font-size: 1.15rem;
            transition: 0.2s;
        }

        .quiz-choice.selected {
            background: var(--neon-yellow);
            color: black;
            border-color: var(--neon-yellow);
            font-weight: bold;
            box-shadow: 0 0 20px var(--neon-yellow);
        }

        .certificate-sheet {
            border: 12px double var(--neon-yellow);
            padding: 35px;
            text-align: center;
            background: radial-gradient(circle, #7209b7, #3a0ca3, #4361ee);
            border-radius: 30px;
            margin-top: 20px;
            box-shadow: 0 0 50px var(--neon-yellow);
            color: #fff;
        }

        .status-badge {
            display: inline-block;
            padding: 8px 15px;
            border-radius: 20px;
            background: rgba(0,230,118,0.2);
            border: 1px solid var(--neon-green);
            color: var(--neon-green);
            font-weight: bold;
            margin-bottom: 10px;
        }
        .hidden { display: none !important; }
        .back-nav { width: auto; margin-bottom: 20px; padding: 12px; font-size: 1.1rem; }
    </style>
</head>
<body>

<div id="app-container">
    
    <!-- 1. شاشة تسجيل البيانات -->
    <div id="screen-login" class="screen active">
        <h1 style="color:var(--neon-pink); font-size: 2.2rem;">🌟 StudySmart 🌟</h1>
        <img src="1000467716.png" class="hero-avatar" alt="البطلة">
        
        <div class="input-wrapper">
            <label>اسم الطالب/البطلة:</label>
            <input type="text" id="reg-name" placeholder="أدخل الاسم الرباعي...">
        </div>

        <div class="input-wrapper">
            <label>المرحلة الدراسية:</label>
            <select id="reg-grade" onchange="populateTracks()">
                <option value="1">الصف الأول الثانوي (المسار العام المطور)</option>
                <option value="2">الصف الثاني الثانوي (نظام البكالوريا المصري)</option>
                <option value="3">الصف الثالث الثانوي (الثانوية العامة)</option>
            </select>
        </div>

        <div id="track-wrapper" class="input-wrapper hidden">
            <label>المسار / الشعبة التخصصية:</label>
            <select id="reg-track"></select>
        </div>

        <div class="input-wrapper">
            <label>رقم واتساب ولي الأمر (للتقارير الفورية):</label>
            <input type="tel" id="reg-phone" placeholder="01xxxxxxxxx">
        </div>

        <button class="action-btn" onclick="executeLogin()">دخول عالم المغامرات 🚀</button>
    </div>

    <!-- 2. لوحة التحكم الرئيسية -->
    <div id="screen-dashboard" class="screen">
        <div class="user-profile-circle">
            <img src="1000467716.png" alt="صورة الطالبة">
        </div>
        <h2>أهلاً بك يا <span id="dash-user" style="color:var(--neon-cyan);"></span>! 🎓</h2>
        <div style="text-align: center;"><span class="status-badge">النظام المصري المطور 2026 ✅</span></div>
        <h4 style="color: var(--neon-yellow); margin-top: 5px;" id="dash-level-info"></h4>
        
        <div class="nav-grid">
            <div class="nav-tile" onclick="openSection('screen-library')">
                <span class="icon">📚</span>
                <h4>المكتبة الشاملة</h4>
            </div>
            <div class="nav-tile" onclick="openSection('screen-assessment-hub')">
                <span class="icon">📝</span>
                <h4>مركز التقييمات</h4>
            </div>
            <div class="nav-tile" onclick="runAiCoach()">
                <span class="icon">🤖</span>
                <h4>المعلم الذكي</h4>
            </div>
            <div class="nav-tile" onclick="openSection('screen-monthly-exam')">
                <span class="icon">🏆</span>
                <h4>امتحان الشهر</h4>
            </div>
            <div class="nav-tile" onclick="openSection('screen-homework')">
                <span class="icon">🏠</span>
                <h4>الأداءات المنزلية</h4>
            </div>
            <div class="nav-tile" onclick="openSection('screen-classwork')">
                <span class="icon">🏫</span>
                <h4>الأداءات الصفية</h4>
            </div>
            <div class="nav-tile" onclick="openSection('screen-reports')">
                <span class="icon">📊</span>
                <h4>تقارير ولي الأمر</h4>
            </div>
            <div class="nav-tile" onclick="openSection('screen-certificate')">
                <span class="icon">🎖️</span>
                <h4>شهادة التقدير</h4>
            </div>
        </div>
    </div>

    <!-- 3. المكتبة الرقمية -->
    <div id="screen-library" class="screen">
        <button class="action-btn back-nav" onclick="openSection('screen-dashboard')">⬅️ العودة للرئيسية</button>
        <h3>📖 المقررات والكتب الوزارية</h3>
        <p style="text-align:center; font-size: 1rem; color: #ccc;">الكتب الرقمية التفاعلية المعتمدة:</p>
        <div id="library-books-list"></div>
    </div>

    <!-- 4. مركز التقييمات (3 نماذج) -->
    <div id="screen-assessment-hub" class="screen">
        <button class="action-btn back-nav" onclick="openSection('screen-dashboard')">⬅️ العودة للرئيسية</button>
        <h3>📝 نماذج التقييم الوزاري</h3>
        <p style="text-align:center; color: var(--neon-yellow);">اختر نموذجاً للبدء (كل نموذج يحتوي على 5 أسئلة):</p>
        <div class="nav-grid">
            <div class="nav-tile" style="border-color: var(--neon-cyan);" onclick="loadQuizModel(1)">
                <span class="icon">1️⃣</span>
                <h4>النموذج الأول</h4>
            </div>
            <div class="nav-tile" style="border-color: var(--neon-pink);" onclick="loadQuizModel(2)">
                <span class="icon">2️⃣</span>
                <h4>النموذج الثاني</h4>
            </div>
            <div class="nav-tile" style="border-color: var(--neon-yellow);" onclick="loadQuizModel(3)">
                <span class="icon">3️⃣</span>
                <h4>النموذج الثالث</h4>
            </div>
        </div>
    </div>

    <!-- 5. نافذ حل الاختبار الفعلية -->
    <div id="screen-active-quiz" class="screen">
        <button class="action-btn back-nav" onclick="openSection('screen-assessment-hub')">⬅️ اختيار نموذج آخر</button>
        <h3 id="quiz-title-header">التقييم الوزاري</h3>
        <div id="quiz-progress" style="text-align: center; font-weight: bold; color: var(--neon-cyan); margin-bottom: 10px;"></div>
        <div id="quiz-question-box" style="font-size: 1.3rem; margin-bottom: 20px; text-shadow: 0 0 5px #000;"></div>
        <div id="quiz-options-area"></div>
        <button class="action-btn" id="quizSubmitBtn" onclick="processQuizAnswer()">تثبيت الإجابة والتالي ➡️</button>
    </div>

    <!-- 6. الأداءات المنزلية -->
    <div id="screen-homework" class="screen">
        <button class="action-btn back-nav" onclick="openSection('screen-dashboard')">⬅️ العودة للرئيسية</button>
        <h3>🏠 الأداءات المنزلية</h3>
        <p>تم تحميل المهام المنزلية المخصصة لمسارك الدراسي.</p>
        <div id="homework-list"></div>
    </div>

    <!-- 7. الأداءات الصفية -->
    <div id="screen-classwork" class="screen">
        <button class="action-btn back-nav" onclick="openSection('screen-dashboard')">⬅️ العودة للرئيسية</button>
        <h3>🏫 الأداءات الصفية</h3>
        <p>ملخص الأنشطة والتدريبات الصفية المعتمدة.</p>
        <div id="classwork-list"></div>
    </div>

    <!-- 8. امتحان الشهر الشامل -->
    <div id="screen-monthly-exam" class="screen">
        <button class="action-btn back-nav" onclick="openSection('screen-dashboard')">⬅️ العودة للرئيسية</button>
        <h3>🏆 امتحان الشهر الختامي</h3>
        <p style="text-align: center;">يغطي كافة نواتج التعلم للتقييمات والأداءات. اجتيازه يمنحك شهادة التقدير الرسمية.</p>
        <div id="monthly-exam-portal">
            <div class="nav-tile" style="border-size: 5px; border-color: var(--neon-yellow); margin: 0 auto; width: 60%;" onclick="startFinalMonthlyExam()">
                <span class="icon">🔥</span>
                <h4>بدء الامتحان النهائي</h4>
            </div>
        </div>
    </div>

    <!-- 9. تقارير ولي الأمر والواتساب -->
    <div id="screen-reports" class="screen">
        <button class="action-btn back-nav" onclick="openSection('screen-dashboard')">⬅️ العودة للرئيسية</button>
        <h3>📊 سجل تقارير الأداء الموجهة لولي الأمر</h3>
        <div style="background: rgba(255,255,255,0.1); padding: 20px; border-radius: 20px; margin: 15px 0;">
            <p><strong>اسم الطالبة:</strong> <span id="rpt-name"></span></p>
            <p><strong>المسار المعتمد:</strong> <span id="rpt-track"></span></p>
            <p><strong>رقم هاتف ولي الأمر:</strong> <span id="rpt-phone"></span></p>
            <p><strong>حالة الإشعار التلقائي:</strong> <span style="color: var(--neon-green);">مفعل وجاهز للإرسال ✅</span></p>
        </div>
        <button class="action-btn" style="background: #25d366; box-shadow: 0 0 30px #25d366;" onclick="dispatchWhatsAppReport()">إرسال تقرير الأداء الشامل لواتساب 💬</button>
    </div>

    <!-- 10. شهادة التقدير الفخرية -->
    <div id="screen-certificate" class="screen">
        <button class="action-btn back-nav" onclick="openSection('screen-dashboard')">⬅️ العودة للرئيسية</button>
        <div class="certificate-sheet">
            <div style="font-size: 3rem;">🌟 📜 🌟</div>
            <h1 style="color: var(--neon-yellow); font-size: 2.5rem; text-shadow: 0 0 20px var(--neon-yellow);">شهادة تقدير وتفوق</h1>
            <p style="font-size: 1.2rem;">تمنح منصة StudySmart التعليمية هذه الشهادة الفخرية للبطلة:</p>
            <h1 id="cert-student-name" style="color: var(--neon-cyan); margin: 20px 0; font-size: 2.8rem; text-shadow: 0 0 15px var(--neon-cyan);"></h1>
            <p id="cert-path-text" style="font-size: 1.3rem; font-weight: bold;"></p>
            <div style="margin: 30px 0; background: rgba(0,0,0,0.4); padding: 15px; border-radius: 15px; border: 1px solid var(--neon-yellow);">
                <p>وذلك لإتمامها كافة التقييمات والأداءات واجتياز امتحان الشهر بتقدير امتياز نهائي.</p>
            </div>
            <h3 style="color: var(--neon-green);">مبارك لكِ هذا الإنجاز المشرف! 🎉</h3>
            <p style="font-size: 0.9rem; color: #ccc; margin-top: 50px;">المؤسسة التعليمية الذكية - جمهورية مصر العربية 2026</p>
        </div>
        <button class="action-btn" style="background: #25d366; box-shadow: 0 0 35px #25d366;" onclick="dispatchWhatsAppCertificate()">إرسال الشهادة الرسمية لواتساب ولي الأمر 💬</button>
    </div>

</div>

<script>
    const educationalDatabase = {
        "1": {
            tracks: ["المسار العام المطور"],
            curricula: {
                "المسار العام المطور": [
                    { name: "📘 كتاب العلوم المتكاملة", link: "https://moe.gov.eg" },
                    { name: "📙 كتاب الفلسفة والمنطق", link: "https://moe.gov.eg" },
                    { name: "📗 كتاب الرياضيات", link: "https://moe.gov.eg" },
                    { name: "📕 كتاب اللغة العربية", link: "https://moe.gov.eg" },
                    { name: "📙 كتاب اللغة الأجنبية الأولى", link: "https://moe.gov.eg" }
                ]
            },
            homework: ["حل تدريبات الفصل الأول في العلوم المتكاملة", "كتابة مقال فلسفي حول التفكير العلمي", "حل تمارين المصفوفات"],
            classwork: ["مناقشة تفاعلية حول بنية الخلية", "تطبيق عملي لقواعد النحو", "حل مسائل فيزياء الحركة"],
            models: [
                [
                    { Q: "ما هي المادة التي تدمج بين علوم الطبيعة (الفيزياء والكيمياء والأحياء) في الصف الأول الثانوي؟", opts: ["الفيزياء الكلاسيكية", "العلوم المتكاملة", "الجيولوجيا التطبيقية"], ans: 1 },
                    { Q: "أي مما يلي يعتبر من المهارات الأساسية للتفكير الفلسفي؟", opts: ["التلقين الأعمى", "النقد والتحليل", "القبول دون فحص"], ans: 1 },
                    { Q: "إذا كانت دالة س تساوي س تربيع، فإن دالة 3 تساوي:", opts: ["6", "9", "3"], ans: 1 },
                    { Q: "ما هو المصدر الرئيسي للتشريع الإسلامي في اللغة العربية والدراسات الإسلامية؟", opts: ["الاجتهاد الفردي", "القرآن الكريم", "العرف السائد"], ans: 1 },
                    { Q: "In English, what is the synonym of 'Significant'?", opts: ["Unimportant", "Important", "Tiny"], ans: 1 }
                ],
                [
                    { Q: "ما هي الوحدة البنائية والوظيفية لجميع الكائنات الحية؟", opts: ["النسيج", "العضو", "الخلية"], ans: 2 },
                    { Q: "العلم الذي يبحث في أصول المعرفة وطبيعتها يسمى:", opts: ["المنطق", "الإبستمولوجيا", "الأنثروبولوجيا"], ans: 1 },
                    { Q: "حل المعادلة: 2 سين + 5 = 15، فإن سين تساوي:", opts: ["4", "5", "10"], ans: 1 },
                    { Q: "ما هو الفعل الناسخ الذي يفيد التوقيت في وقت الضحى؟", opts: ["أضحى", "أصبح", "صار"], ans: 0 },
                    { Q: "Choose the correct preposition: He is interested ___ learning languages.", opts: ["at", "in", "with"], ans: 1 }
                ],
                [
                    { Q: "أي من الظواهر التالية تعتبر ظاهرة كيميائية وليست فيزيائية؟", opts: ["انصهار الجليد", "احتراق الخشب", "تبخر الماء"], ans: 1 },
                    { Q: "القياس الذي يعتمد على الملاحظة المباشرة والتجريب يسمى قياساً:", opts: ["نظرياً", "تجريبياً", "افتراضياً"], ans: 1 },
                    { Q: "المثلث الذي قياسات زواياه 60، 60، 60 يسمى مثلثاً:", opts: ["قائم الزاوية", "متساوي الأضلاع", "مختلف الأضلاع"], ans: 1 },
                    { Q: "في البلاغة، التشبيه الذي يُذكر فيه المشبه والمشبه به فقط يسمى:", opts: ["تشبيهاً بليغاً", "تشبيهاً مجملاً", "تشبيهاً مفصلاً"], ans: 0 },
                    { Q: "What is the past tense of the verb 'Go'?", opts: ["Goed", "Went", "Gone"], ans: 1 }
                ]
            ]
        },
        "2": {
            tracks: ["شعبة علمي علوم", "شعبة علمي رياضة", "الشعبة الأدبية", "الشعبة التكنولوجية"],
            curricula: {
                "شعبة علمي علوم": [
                    { name: "🔬 كتاب الأحياء المتقدم", link: "https://moe.gov.eg" },
                    { name: "🧪 كتاب الكيمياء العضوية وغير العضوية", link: "https://moe.gov.eg" },
                    { name: "⚡ كتاب الفيزياء العامة والحرارية", link: "https://moe.gov.eg" }
                ],
                "شعبة علمي رياضة": [
                    { name: "📐 كتاب الرياضيات البحتة (جبر وتفاضل)", link: "https://moe.gov.eg" },
                    { name: "🚀 كتاب الرياضيات التطبيقية (استاتيكا وديناميكا)", link: "https://moe.gov.eg" },
                    { name: "⚡ كتاب الفيزياء المتقدمة", link: "https://moe.gov.eg" }
                ],
                "الشعبة الأدبية": [
                    { name: "📜 كتاب التاريخ الحديث والمعاصر", link: "https://moe.gov.eg" },
                    { name: "🌍 كتاب الجغرافيا البشرية والاقتصادية", link: "https://moe.gov.eg" },
                    { name: "🧠 كتاب علم النفس والاجتماع", link: "https://moe.gov.eg" }
                ],
                "الشعبة التكنولوجية": [
                    { name: "💻 كتاب هياكل البيانات والخوارزميات", link: "https://moe.gov.eg" },
                    { name: "🤖 كتاب مبادئ الذكاء الاصطناعي وتطبيقاته", link: "https://moe.gov.eg" },
                    { name: "🛡️ كتاب الأمن السيبراني وشبكات الحاسب", link: "https://moe.gov.eg" }
                ]
            },
            homework: ["حل 20 مسألة متقدمة في التخصص", "تلخيص المقالات العلمية أو التاريخية للأسبوع", "تطبيق برمجي أو تقني للمسار التكنولوجي"],
            classwork: ["إجراء تجربة معملية افتراضية", "مناقشة وتحليل وثائق تاريخية أو جغرافية", "جلسة عصف ذهني لحل مشكلات برمجية"],
            models: [
                [
                    { Q: "ใน النظام المصري المطور للصف الثاني الثانوي، ما هو المبدأ الأساسي لتعدد المسارات؟", opts: ["التخصص المبكر وتنمية المهارات النوعية", "إلغاء المواد الأساسية", "صعوبة الامتحانات"], ans: 0 },
                    { Q: "أي من المسارات التالية يركز بشكل أساسي على دراسة النظم الذكية والبرمجة؟", opts: ["الشعبة الأدبية", "شعبة علمي علوم", "الشعبة التكنولوجية"], ans: 2 },
                    { Q: "في علم الأحياء، ما هي العملية المسؤولة عن انقسام الخلايا الجسدية؟", opts: ["الانقسام الميوزي", "الانقسام الميتوزي", "التبرعم"], ans: 1 },
                    { Q: "في الرياضيات التطبيقية، محصلة قوتين متلاقيتين في نقطة تعتمد على:", opts: ["الزاوية بينهما فقط", "مقدار القوتين فقط", "مقدار القوتين والزاوية بينهما"], ans: 2 },
                    { Q: "في التاريخ، ما هي المعاهدة التي أنهت الوجود العثماني الفعلي في مصر وبداية العصر الحديث؟", opts: ["معاهدة لندن", "صلح أميان", "معاهدة برلين"], ans: 0 }
                ],
                [
                    { Q: "ما الذي يميز نظام البكالوريا المصري المطور في مرحلة الصف الثاني الثانوي؟", opts: ["المرونة في اختيار المسار التخصصي", "الاقتصار على الحفظ النظري", "عدم وجود تقييمات مستمرة"], ans: 0 },
                    { Q: "في الكيمياء العضوية، الصيغة العامة للألكانات هي:", opts: ["سي ن هـ 2ن", "سي ن هـ 2ن+2", "سي ن هـ 2ن-2"], ans: 1 },
                    { Q: "في الفيزياء، قانون الجذب العام لنيوتن ينص على أن قوة التجاذب تتناسب:", opts: ["عكسياً مع حاصل ضرب الكتلتين", "طردياً مع مربع المسافة"، "عكسياً مع مربع المسافة بين المركزين"], ans: 2 },
                    { Q: "في علم النفس، المدرسة التي تركز على دراسة السلوك الظاهري القابل للملاحظة هي:", opts: ["المدرسة السلوكية", "مدرسة التحليل النفسي", "المدرسة المعرفية"], ans: 0 },
                    { Q: "في البرمجة، أي مما يلي يعتبر حلقة تكرار (Loop) أساسية؟", opts: ["If Statement", "For Loop", "Variable Declaration"], ans: 1 }
                ],
                [
                    { Q: "ما الهدف الاستراتيجي من استحداث الشعبة التكنولوجية في نظام التعليم المصري؟", opts: ["إعداد كوادر قادرة على قيادة التحول الرقمي", "تقليل عدد الطلاب في المدارس*", "صعوبة المناهج"], ans: 0 },
                    { Q: "في الجغرافيا، دراسة توزيع السكان وعلاقتهم بالموارد تندرج تحت:", opts: ["الجغرافيا الطبيعية", "جغرافيا السكان والتنمية", "الجغرافيا الفلكية"], ans: 1 },
                    { Q: "في الاقتصاد، التضخم يعرف بأنه:", opts: ["انخفاض مستمر في الأسعار", "ارتفاع مستمر في المستوى العام للأسعار", "زيادة قيمة العملة"], ans: 1 },
                    { Q: "في الذكاء الاصطناعي، الشبكات العصبية الاصطناعية مصممة لمحاكاة:", opts: ["الدوائر الكهربائية التناظرية", "طريقة عمل الدماغ البشري", "أنظمة التبريد الميكانيكية"], ans: 1 },
                    { Q: "In Physics, what is the unit of Electric Resistance?", opts: ["Volt", "Ampere", "Ohm"], ans: 2 }
                ]
            ]
        },
        "3": {
            tracks: ["الشعبة العلمية", "الشعبة الأدبية"],
            curricula: {
                "الشعبة العلمية": [
                    { name: "🧬 كتاب الأحياء والجزيئات الحيوية", link: "https://moe.gov.eg" },
                    { name: "⚗️ كتاب الكيمياء الفيزيائية والعضوية", link: "https://moe.gov.eg" },
                    { name: "🔭 كتاب الفيزياء الحديثة والنووية", link: "https://moe.gov.eg" }
                ],
                "الشعبة الأدبية": [
                    { name: "🏛️ كتاب الفلسفة وقضايا العصر والمنطق التطبيقي", link: "https://moe.gov.eg" },
                    { name: "📜 كتاب التاريخ المعاصر والعلاقات الدولية", link: "https://moe.gov.eg" },
                    { name: "🗺️ كتاب الجغرافيا السياسية والتكتلات العالمية", link: "https://moe.gov.eg" }
                ]
            },
            homework: ["حل نماذج امتحانات الثانوية العامة السابقة", "كتابة بحوث تحليلية معمقة في مواد التخصص", "تدريبات مكثفة على الأسئلة المقالية والاختيارية"],
            classwork: ["محاكاة امتحانات الثانوية العامة بنظام البابل شيت", "مناقشة القضايا الجدلية في الفلسفة والعلوم", "حل مشكلات رياضية وعلمية معقدة"],
            models: [
                [
                    { Q: "في ختام مرحلة الثانوية العامة، ما هو المعيار الأساسي للقبول الجامعي في مصر؟", opts: ["المجموع التراكمي ونظام التنسيق الإلكتروني", "المقابلة الشخصية فقط", "الترشيح الجغرافي العشوائي"], ans: 0 },
                    { Q: "في الفيزياء الحديثة، ظاهرة انبعاث الإلكترونات عند سقوط ضوء بتردد مناسب على سطح معدن تسمى:", opts: ["تأثير كومبتون", "الظاهرة الكهروضوئية", "الانبعاث الحراري"], ans: 1 },
                    { Q: "في الجغرافيا السياسية، القوة الديموغرافية للدولة تشمل:", opts: ["عدد السكان وتوزيعهم وخصائصهم", "المساحة والحدود فقط", "التحالفات العسكرية"], ans: 0 },
                    { Q: "في الكيمياء، عند وصول التفاعل الكيميائي لحالة الاتزان، فإن:", opts: ["يتوقف التفاعل تماماً", "تتساوى سرعة التفاعلين الطردي والعكسي", "تتساوى تركيزات المتفاعلات والنواتج"], ans: 1 },
                    { Q: "الفلسفة التطبيقية تهتم بـ:", opts: ["البحث في الميتافيزيقا البحتة", "معالجة القضايا الأخلاقية والمهنية المعاصرة", "تاريخ الفلسفة اليونانية"], ans: 1 }
                ],
                [
                    { Q: "ما الهدف الأساسي لنظام التقييم الحديث في الثانوية العامة المصرية؟", opts: ["قياس الفهم ومستويات التفكير العليا", "الحفظ التام للمناهج", "زيادة نسبة الرسوب"], ans: 0 },
                    { Q: "في الأحياء، الجزيء المسؤول عن نقل الشفرة الوراثية في الخلية هو:", opts: ["RNA", "DNA", "ATP"], ans: 1 },
                    { Q: "في التاريخ، ما هي الثورة المصرية التي تعتبر نقطة تحول في تاريخ مصر الحديث والمعاصر؟", opts: ["الثورة العرابية", "ثورة 1919", "ثورة 23 يوليو 1952"], ans: 2 },
                    { Q: "في المنطق، الحجة الاستنباطية الصحيحة هي التي:", opts: ["تكون نتيجتها مطابقة للواقع دائماً", "تلزم نتيجتها عن مقدماتها لزوماً ضرورياً", "تعتمد على الاستقراء الناقص"], ans: 1 },
                    { Q: "In Chemistry, what is the pH range of an acidic solution?", opts: ["Above 7", "Exactly 7", "Below 7"], ans: 2 }
                ],
                [
                    { Q: "في ظل التحول الرقمي، كيف يتم تصحيح امتحانات الثانوية العامة في مصر؟", opts: ["التصحيح الإلكتروني المركزي لضمان الشفافية", "التصحيح اليدوي في المدارس", "التقدير التقديري للمصححين"], ans: 0 },
                    { Q: "في الفيزياء النووية، القوة المسؤولة عن ربط مكونات النواة ببعضها هي:", opts: ["قوة الجاذبية", "القوة النووية القوية", "القوة الكهرومغناطيسية"], ans: 1 },
                    { Q: "الأحلاف العسكرية في الجغرافيا السياسية تعتبر من مقومات القوة:", opts: ["الاقتصادية", "العسكرية والدفاعية", "الديموغرافية"], ans: 1 },
                    { Q: "في الكيمياء العضوية، التفاعل الذي يتم فيه تحويل الزيوت النباتية إلى سمن صناعي يسمى تفاعل:", opts: ["أسترة", "هدرجة", "بلمرة"], ans: 1 },
                    { Q: "الأخلاقيات البيولوجية (البيوتيقا) ظهرت نتيجة لـ:", opts: ["التقدم الهائل في العلوم الطبية والتكنولوجيا الحيوية", "تراجع دور الفلسفة", "اكتشاف مصادر طاقة جديدة"], ans: 0 }
                ]
            ]
        }
    };

    let currentUserData = { name: "", grade: "", track: "", phone: "" };
    let currentQuizModel = [];
    let currentQuestionIndex = 0;
    let userScore = 0;
    let selectedOptionIndex = null;
    let activeCategoryType = ""; // 'assessment', 'monthly'

    function populateTracks() {
        const grade = document.getElementById("reg-grade").value;
        const wrapper = document.getElementById("track-wrapper");
        const select = document.getElementById("reg-track");
        select.innerHTML = "";
        
        const tracks = educationalDatabase[grade].tracks;
        if(tracks.length > 1) {
            tracks.forEach(t => {
                let opt = document.createElement("option");
                opt.value = t; opt.innerHTML = t;
                select.appendChild(opt);
            });
            wrapper.classList.remove("hidden");
        } else {
            wrapper.classList.add("hidden");
            select.innerHTML = `<option value="${tracks[0]}">${tracks[0]}</option>`;
        }
    }

    function openSection(screenId) {
        document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
        document.getElementById(screenId).classList.add('active');
    }

    function executeLogin() {
        const name = document.getElementById("reg-name").value.trim();
        const phone = document.getElementById("reg-phone").value.trim();
        const gradeVal = document.getElementById("reg-grade").value;
        const gradeText = document.getElementById("reg-grade").options[document.getElementById("reg-grade").selectedIndex].text;
        const trackVal = document.getElementById("reg-track").value;

        if(!name || !phone) {
            alert("⚠️ يرجى تعبئة الاسم ورقم هاتف ولي الأمر بدقة!");
            return;
        }

        currentUserData = { name, grade: gradeVal, gradeText, track: trackVal, phone };

        document.getElementById("dash-user").innerText = name;
        document.getElementById("dash-level-info").innerText = gradeText + " (" + trackVal + ")";
        
        document.getElementById("rpt-name").innerText = name;
        document.getElementById("rpt-track").innerText = gradeText + " - " + trackVal;
        document.getElementById("rpt-phone").innerText = phone;

        document.getElementById("cert-student-name").innerText = name;
        document.getElementById("cert-path-text").innerText = gradeText + " | " + trackVal;

        renderLibraryList();
        renderHomeworkList();
        renderClassworkList();

        openSection("screen-dashboard");
    }

    function renderLibraryList() {
        const container = document.getElementById("library-books-list");
        container.innerHTML = "";
        const books = educationalDatabase[currentUserData.grade].curricula[currentUserData.track];
        books.forEach(b => {
            container.innerHTML += `<a href="${b.link}" target="_blank" class="resource-link">${b.name}</a>`;
        });
    }

    function renderHomeworkList() {
        const container = document.getElementById("homework-list");
        container.innerHTML = "";
        const tasks = educationalDatabase[currentUserData.grade].homework;
        tasks.forEach(t => {
            container.innerHTML += `<div class="quiz-choice" style="border-color: var(--neon-cyan);">📋 ${t}</div>`;
        });
    }

    function renderClassworkList() {
        const container = document.getElementById("classwork-list");
        container.innerHTML = "";
        const tasks = educationalDatabase[currentUserData.grade].classwork;
        tasks.forEach(t => {
            container.innerHTML += `<div class="quiz-choice" style="border-color: var(--neon-pink);">🏫 ${t}</div>`;
        });
    }

    function runAiCoach() {
        alert("🤖 المعلم الذكي: مرحباً بك يا بطلة! أنا مفعّل وجاهز للإجابة على كافة أسئلتك في المناهج المصرية صوتياً.");
        if ('speechSynthesis' in window) {
            const utter = new SpeechSynthesisUtterance("أهلاً بك يا بطلة في منصة ستادي سمارت. أنا معلمك الذكي، جاهز لمساعدتك في فهم كافة مواد الثانوية العامة والبكالوريا بنظامها المطور.");
            utter.lang = 'ar-SA';
            window.speechSynthesis.speak(utter);
        }
    }

    function loadQuizModel(modelNumber) {
        activeCategoryType = 'assessment';
        currentQuizModel = [...educationalDatabase[currentUserData.grade].models[modelNumber - 1]];
        document.getElementById("quiz-title-header").innerText = "نموذج التقييم الوزاري رقم (" + modelNumber + ")";
        startQuizSession();
    }

    function startFinalMonthlyExam() {
        activeCategoryType = 'monthly';
        const allModels = educationalDatabase[currentUserData.grade].models;
        currentQuizModel = [
            allModels[0][0], allModels[0][1],
            allModels[1][2], allModels[1][3],
            allModels[2][4]
        ];
        document.getElementById("quiz-title-header").innerText = "🔥 امتحان الشهر الشامل المعتمد";
        startQuizSession();
    }

    function startQuizSession() {
        currentQuestionIndex = 0;
        userScore = 0;
        openSection("screen-active-quiz");
        renderQuestionCard();
    }

    function renderQuestionCard() {
        const qData = currentQuizModel[currentQuestionIndex];
        document.getElementById("quiz-progress").innerText = "السؤال (" + (currentQuestionIndex + 1) + ") من (" + currentQuizModel.length + ")";
        document.getElementById("quiz-question-box").innerHTML = "❓ " + qData.Q;
        
        const optArea = document.getElementById("quiz-options-area");
        optArea.innerHTML = "";
        qData.opts.forEach((opt, idx) => {
            optArea.innerHTML += `<div class="quiz-choice" onclick="highlightChoice(this, ${idx})">${opt}</div>`;
        });
        selectedOptionIndex = null;
        document.getElementById("quizSubmitBtn").innerText = (currentQuestionIndex === currentQuizModel.length - 1) ? "تسليم الاختبار النهائي ورصد النتيجة 🏁" : "تثبيت الإجابة والتالي ➡️";
    }

    function highlightChoice(element, idx) {
        document.querySelectorAll('.quiz-choice').forEach(c => c.classList.remove('selected'));
        element.classList.add('selected');
        selectedOptionIndex = idx;
    }

    function processQuizAnswer() {
        if(selectedOptionIndex === null) {
            alert("⚠️ يرجى اختيار إجابة للانتقال للسؤال التالي!");
            return;
        }

        const qData = currentQuizModel[currentQuestionIndex];
        if(selectedOptionIndex === qData.ans) {
            userScore++;
        }

        currentQuestionIndex++;
        if(currentQuestionIndex < currentQuizModel.length) {
            renderQuestionCard();
        } else {
            finalizeQuizExecution();
        }
    }

    function finalizeQuizExecution() {
        const percentage = Math.round((userScore / currentQuizModel.length) * 100);
        let msg = "";
        if(activeCategoryType === 'assessment') {
            msg = "🎉 ممتاز! تم إنهاء التقييم الوزاري بنجاح. درجاتك: " + userScore + "/" + currentQuizModel.length + " (" + percentage + "%). تم إرسال التقرير فوراً لواتساب ولي الأمر: " + currentUserData.phone;
            alert(msg);
            dispatchWhatsAppReport(percentage);
            openSection("screen-assessment-hub");
        } else {
            msg = "🏆 تهانينا الحارة! لقد اجتزت امتحان الشهر الشامل بتقدير نهائي: " + percentage + "%. تم إصدار شهادة التقدير الرسمية وإرسالها لوالديك!";
            alert(msg);
            dispatchWhatsAppReport(percentage);
            openSection("screen-certificate");
        }
    }

    function dispatchWhatsAppReport(scorePercent = 100) {
        const textEncoded = encodeURIComponent("🚨 إشعار تعليمي من StudySmart:\nالطالبة: " + currentUserData.name + "\nالمسار: " + currentUserData.gradeText + " (" + currentUserData.track + ")\nنتيجة الأداء / الامتحان: " + scorePercent + "%\nالحالة: اجتياز متميز وتفوق دراسي ✅");
        console.log("sending whatsapp to " + currentUserData.phone + ": " + textEncoded);
    }

    function dispatchWhatsAppCertificate() {
        const textEncoded = encodeURIComponent("🎖️ شهادة تقدير رسمية من StudySmart:\nنبارك لكم تفوق البطلة: " + currentUserData.name + "\nلحصولها على الدرجة النهائية في امتحانات ومسارات النظام المصري المطور 2026. نفخر بها جميعاً! 🎉");
        console.log("dispatching certificate whatsapp to " + currentUserData.phone);
    }

    populateTracks();
</script>
</body>
</html>
