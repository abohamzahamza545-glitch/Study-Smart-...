<div id="screen-login" class="screen active">
    <h1>🌟 StudySmart 🌟</h1>
    <img src="1000467716.png" class="hero-avatar" alt="البطلة">
    <form onsubmit="event.preventDefault(); executeLogin();">
        <div class="input-wrapper">
            <label>اسم الطالب/البطلة:</label>
            <input type="text" id="reg-name" required placeholder="أدخل الاسم الرباعي...">
        </div>
        <div class="input-wrapper">
            <label>المرحلة الدراسية:</label>
            <select id="reg-grade" onchange="populateTracks()">
                <option value="1">الصف الأول الثانوي</option>
                <option value="2">الصف الثاني الثانوي</option>
                <option value="3">الصف الثالث الثانوي</option>
            </select>
        </div>
        <div id="track-wrapper" class="input-wrapper">
            <label>المسار / الشعبة:</label>
            <select id="reg-track"></select>
        </div>
        <div class="input-wrapper">
            <label>رقم واتساب ولي الأمر:</label>
            <input type="tel" id="reg-phone" required placeholder="01xxxxxxxxx">
        </div>
        <button type="submit" class="action-btn">دخول عالم المغامرات 🚀</button>
    </form>
</div>
