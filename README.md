<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Samy Ahmed - PHP & SQL Specialist Portfolio">
    <title>Samy Ahmed | PHP & SQL Specialist</title>
    
    <!-- استيراد الخطوط: تجوال للعربية و Fira Code للأكواد -->
    <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700;800&family=Fira+Code:wght@400;600&display=swap" rel="stylesheet">
    <!-- استيراد مكتبة أيقونات FontAwesome -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        /* --- إعدادات المتغيرات (Theme Variables) --- */
        :root {
            --bg-color: #090c10;
            --card-bg: #161b22;       /* GitHub Dark Dimmed */
            --border-color: #30363d;
            --text-main: #c9d1d9;
            --text-muted: #8b949e;
            --accent-blue: #58a6ff;
            --accent-green: #3fb950;
            --accent-purple: #d2a8ff;
            --accent-orange: #d18616;
            --code-font: 'Fira Code', monospace;
            --main-font: 'Tajawal', sans-serif;
        }

        /* --- التصفير الأساسي --- */
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        /* --- تنسيق الجسم والخلفية --- */
        body {
            font-family: var(--main-font);
            background-color: var(--bg-color);
            background-image: 
                linear-gradient(rgba(48, 54, 61, 0.2) 1px, transparent 1px),
                linear-gradient(90deg, rgba(48, 54, 61, 0.2) 1px, transparent 1px);
            background-size: 30px 30px;
            color: var(--text-main);
            line-height: 1.6;
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow-x: hidden;
        }

        .container {
            max-width: 850px;
            width: 100%;
            padding: 1rem;
            animation: fadeInUp 0.8s ease-out;
        }

        /* --- نافذة المحرر (Terminal Window Style) --- */
        .window-card {
            background: var(--card-bg);
            border: 1px solid var(--border-color);
            border-radius: 12px;
            box-shadow: 0 20px 50px rgba(0,0,0,0.6);
            overflow: hidden;
            position: relative;
        }

        /* شريط العنوان */
        .window-header {
            background: #0d1117;
            padding: 10px 15px;
            display: flex;
            align-items: center;
            border-bottom: 1px solid var(--border-color);
        }

        .window-controls {
            display: flex;
            gap: 8px;
            margin-left: 10px; /* هامش يسار بسبب RTL */
        }

        .control { width: 12px; height: 12px; border-radius: 50%; }
        .close { background: #ff5f56; }
        .minimize { background: #ffbd2e; }
        .maximize { background: #27c93f; }

        .window-title {
            flex-grow: 1;
            text-align: center;
            font-family: var(--code-font);
            font-size: 0.85rem;
            color: var(--text-muted);
            opacity: 0.8;
            direction: ltr; /* لعرض المسار بشكل صحيح */
        }

        /* جسم النافذة */
        .window-body {
            padding: 3rem 2rem;
            text-align: center;
            position: relative;
        }

        /* --- صورة الملف الشخصي --- */
        .img-container {
            position: relative;
            width: 160px;
            height: 160px;
            margin: 0 auto 1.5rem;
        }

        .profile-img {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            border: 4px solid var(--card-bg);
            object-fit: cover;
            position: relative;
            z-index: 2;
        }

        .img-border {
            position: absolute;
            top: -5px; left: -5px; right: -5px; bottom: -5px;
            border-radius: 50%;
            border: 2px dashed var(--accent-blue);
            animation: spin 10s linear infinite;
            z-index: 1;
        }

        /* --- النصوص والعناوين --- */
        h1 {
            font-size: 2.2rem;
            color: #ffffff;
            margin-bottom: 0.5rem;
            font-family: var(--main-font);
        }

        .code-tag {
            font-family: var(--code-font);
            color: var(--accent-purple);
            font-size: 1rem;
            display: inline-block;
            margin-bottom: 0.5rem;
        }

        .typing-container {
            font-family: var(--code-font);
            color: var(--accent-green);
            font-size: 1.1rem;
            margin-bottom: 2.5rem;
            height: 1.5em; /* لحفظ الارتفاع */
            direction: ltr;
        }

        .cursor {
            display: inline-block;
            width: 8px;
            background-color: var(--accent-green);
            animation: blink 1s infinite;
        }

        /* --- قسم المهارات (Skills) --- */
        .section-title {
            font-family: var(--code-font);
            color: var(--accent-orange);
            font-size: 1rem;
            margin-bottom: 1.5rem;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            direction: ltr;
        }

        .section-title::before, .section-title::after {
            content: "//";
            color: var(--text-muted);
            font-weight: normal;
        }

        .skills-grid {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 12px;
            margin-bottom: 3rem;
            direction: ltr;
        }

        .skill-item {
            background: rgba(88, 166, 255, 0.1);
            border: 1px solid rgba(88, 166, 255, 0.2);
            color: var(--text-main);
            padding: 8px 16px;
            border-radius: 6px;
            font-family: var(--code-font);
            font-size: 0.9rem;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .skill-item:hover {
            border-color: var(--accent-blue);
            background: rgba(88, 166, 255, 0.2);
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(88, 166, 255, 0.1);
        }

        .skill-item i { color: var(--accent-blue); }

        /* --- أزرار التواصل --- */
        .social-container {
            display: flex;
            justify-content: center;
            gap: 1.5rem;
            margin-top: 1rem;
        }

        .social-btn {
            width: 50px;
            height: 50px;
            border-radius: 12px;
            background: #21262d;
            border: 1px solid var(--border-color);
            color: var(--text-muted);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.4rem;
            text-decoration: none;
            transition: all 0.3s;
            position: relative;
        }

        .social-btn:hover {
            color: #fff;
            border-color: var(--accent-blue);
            background: #21262d;
            transform: translateY(-5px);
        }

        .social-btn::after {
            content: attr(data-tooltip);
            position: absolute;
            bottom: -35px;
            left: 50%;
            transform: translateX(-50%);
            background: #000;
            color: #fff;
            padding: 4px 8px;
            border-radius: 4px;
            font-size: 0.7rem;
            font-family: var(--code-font);
            opacity: 0;
            transition: 0.3s;
            pointer-events: none;
            white-space: nowrap;
        }

        .social-btn:hover::after {
            opacity: 1;
            bottom: -40px;
        }

        /* --- الفوتر --- */
        footer {
            margin-top: 3rem;
            color: var(--text-muted);
            font-size: 0.85rem;
            font-family: var(--code-font);
            border-top: 1px solid var(--border-color);
            padding-top: 1.5rem;
        }

        /* --- حركات الأنيميشن --- */
        @keyframes spin { 100% { transform: rotate(360deg); } }
        @keyframes blink { 50% { opacity: 0; } }
        @keyframes fadeInUp { from { opacity: 0; transform: translateY(20px); } to { opacity: 1; transform: translateY(0); } }

    </style>
</head>
<body>

    <div class="container">
        <div class="window-card">
            
            <!-- شريط العنوان -->
            <div class="window-header">
                <div class="window-controls">
                    <div class="control close"></div>
                    <div class="control minimize"></div>
                    <div class="control maximize"></div>
                </div>
                <!-- تمت إضافة (main) لمحاكاة Git Branch -->
                <div class="window-title">~/samy-ahmed/portfolio (main)</div>
            </div>

            <!-- المحتوى -->
            <div class="window-body">
                
                <!-- الصورة الشخصية -->
                <div class="img-container">
                    <div class="img-border"></div>
                    <!-- ⬇️ قم بتغيير الرابط هنا لصورتك الشخصية ⬇️ -->
                    <img src="https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?auto=format&fit=crop&w=300&q=80" alt="Samy Ahmed" class="profile-img">
                </div>

                <!-- الاسم والتخصص -->
                <div class="code-tag">&lt;Developer /&gt;</div>
                <h1>Samy Ahmed</h1>
                
                <div class="typing-container">
                    <span id="typing-text"></span><span class="cursor">&nbsp;</span>
                </div>

                <!-- المهارات -->
                <h3 class="section-title">My Skills</h3>
                <div class="skills-grid">
                    <!-- Backend -->
                    <div class="skill-item"><i class="fab fa-php"></i> PHP</div>
                    <div class="skill-item"><i class="fas fa-database"></i> MySQL</div>
                    <!-- Frontend -->
                    <div class="skill-item"><i class="fab fa-html5"></i> HTML5</div>
                    <div class="skill-item"><i class="fab fa-css3-alt"></i> CSS3</div>
                    <div class="skill-item"><i class="fab fa-js"></i> JavaScript</div>
                    <!-- Tools -->
                    <div class="skill-item"><i class="fab fa-git-alt"></i> Git</div>
                    <div class="skill-item"><i class="fas fa-palette"></i> Photoshop</div>
                </div>

                <!-- أزرار التواصل -->
                <h3 class="section-title">Contact Me</h3>
                <div class="social-container">
                    <a href="mailto:contact@samy-ahmed.site" class="social-btn" data-tooltip="Email Me">
                        <i class="fas fa-envelope"></i>
                    </a>
                    <a href="https://samy-ahmed.site/" target="_blank" class="social-btn" data-tooltip="Website">
                        <i class="fas fa-globe"></i>
                    </a>
                    <a href="https://github.com/Samy-Ahmed" target="_blank" class="social-btn" data-tooltip="GitHub">
                        <i class="fab fa-github"></i>
                    </a>
                    <a href="#" class="social-btn" data-tooltip="Download CV">
                        <i class="fas fa-file-download"></i>
                    </a>
                </div>

                <!-- الفوتر -->
                <footer>
                    <span style="color: var(--accent-orange);">const</span> 
                    <span style="color: var(--text-main);">year</span> = 
                    <span style="color: var(--accent-blue);">2026</span>; 
                    <br>
                    // Built with ❤️ by Samy Ahmed
                </footer>
            </div>
        </div>
    </div>

    <script>
        // دالة الكتابة التلقائية (Typing Effect)
        const textToType = "PHP & SQL Specialist | Backend Dev";
        const typingElement = document.getElementById('typing-text');
        let index = 0;

        function typeWriter() {
            if (index < textToType.length) {
                typingElement.textContent += textToType.charAt(index);
                index++;
                setTimeout(typeWriter, 100);
            }
        }

        // تشغيل الدالة عند تحميل الصفحة
        window.onload = typeWriter;
    </script>

</body>
</html>
