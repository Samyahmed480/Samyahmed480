<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Samy Ahmed | PHP & SQL Expert</title>
    <!-- استيراد خط تجوال -->
    <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700;800&display=swap" rel="stylesheet">
    <!-- استيراد مكتبة FontAwesome -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* --- المتغيرات والألوان (الوضع الداكن المحسن) --- */
        :root {
            --bg-color: #0d1117;
            --card-bg: #161b22;
            --card-hover: #1f2428;
            --border-color: #30363d;
            --text-main: #c9d1d9;
            --text-muted: #8b949e;
            --accent-color: #58a6ff;
            --accent-glow: rgba(88, 166, 255, 0.15);
            --gradient-bg: linear-gradient(135deg, rgba(88,166,255,0.1) 0%, rgba(13,17,23,0) 100%);
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            scroll-behavior: smooth;
        }

        body {
            font-family: 'Tajawal', sans-serif;
            background-color: var(--bg-color);
            background-image: radial-gradient(circle at top left, rgba(88,166,255,0.05), transparent 40%);
            color: var(--text-main);
            line-height: 1.6;
            overflow-x: hidden;
        }

        /* --- شريط التنقل --- */
        nav {
            position: sticky;
            top: 0;
            z-index: 100;
            background: rgba(13, 17, 23, 0.9);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid var(--border-color);
            padding: 1rem 0;
        }

        .nav-container {
            max-width: 900px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 1rem;
        }

        .logo {
            font-weight: 800;
            color: #fff;
            font-size: 1.2rem;
            text-decoration: none;
        }

        .nav-links {
            display: flex;
            gap: 1.5rem;
        }

        .nav-links a {
            color: var(--text-main);
            text-decoration: none;
            font-size: 0.95rem;
            transition: color 0.3s;
        }

        .nav-links a:hover {
            color: var(--accent-color);
        }

        /* --- الهيكل العام --- */
        .container {
            max-width: 900px;
            margin: 0 auto;
            padding: 2rem 1rem;
            min-height: 100vh;
        }

        /* --- الرأس (Header) --- */
        header {
            text-align: center;
            margin: 3rem 0 5rem;
            animation: fadeInDown 1s ease-out;
            position: relative;
        }

        .profile-header-img {
            width: 100%;
            border-radius: 1rem;
            margin-bottom: 2rem;
            box-shadow: 0 10px 30px -10px rgba(0,0,0,0.5);
            border: 1px solid var(--border-color);
        }

        h1 {
            font-size: 2.8rem;
            color: #ffffff;
            margin-bottom: 1rem;
            text-shadow: 0 0 20px rgba(88, 166, 255, 0.3);
        }

        .bio-text {
            max-width: 600px;
            margin: 0 auto 2rem;
            color: var(--text-muted);
            font-size: 1.1rem;
        }

        .tagline {
            display: inline-block;
            background: rgba(88, 166, 255, 0.1);
            color: var(--accent-color);
            padding: 5px 15px;
            border-radius: 20px;
            font-size: 0.9rem;
            margin-bottom: 1rem;
            border: 1px solid rgba(88, 166, 255, 0.2);
        }

        /* --- أزرار التواصل --- */
        .social-links {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 1rem;
        }

        .btn {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            padding: 12px 24px;
            border-radius: 8px;
            text-decoration: none;
            font-weight: bold;
            transition: all 0.3s ease;
            border: 1px solid var(--border-color);
            background: var(--card-bg);
            color: var(--text-main);
        }

        .btn:hover {
            transform: translateY(-3px);
            border-color: var(--accent-color);
            box-shadow: 0 4px 15px var(--accent-glow);
            color: #fff;
        }

        .btn-primary {
            background: var(--accent-color);
            color: #fff;
            border-color: var(--accent-color);
        }

        .btn-primary:hover {
            background: #388bfd;
        }

        /* --- الأقسام --- */
        section {
            margin-bottom: 6rem;
            opacity: 0;
            animation: fadeInUp 0.8s ease-out forwards;
        }
        
        section:nth-child(even) { animation-delay: 0.1s; }
        section:nth-child(odd) { animation-delay: 0.2s; }

        .section-title {
            display: flex;
            align-items: center;
            gap: 12px;
            margin-bottom: 2rem;
            padding-bottom: 1rem;
            border-bottom: 1px solid var(--border-color);
            color: #fff;
            font-size: 1.8rem;
        }

        .section-title i {
            color: var(--accent-color);
        }

        /* --- كود PHP الجمالي --- */
        .code-window {
            background: #0d1117;
            border: 1px solid var(--border-color);
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
        }

        .window-header {
            background: #161b22;
            padding: 8px 15px;
            display: flex;
            align-items: center;
            border-bottom: 1px solid var(--border-color);
        }

        .dots {
            display: flex;
            gap: 6px;
            margin-left: 10px;
        }

        .dot { width: 10px; height: 10px; border-radius: 50%; }
        .red { background: #ff5f56; }
        .yellow { background: #ffbd2e; }
        .green { background: #27c93f; }

        .filename {
            flex-grow: 1;
            text-align: center;
            font-family: monospace;
            font-size: 0.8rem;
            color: var(--text-muted);
        }

        .code-block {
            padding: 1.5rem;
            direction: ltr;
            text-align: left;
            font-family: 'Fira Code', monospace;
            overflow-x: auto;
            font-size: 0.95rem;
        }

        /* Syntax Highlighting */
        .keyword { color: #ff7b72; }
        .class-name { color: #d2a8ff; }
        .variable { color: #79c0ff; }
        .string { color: #a5d6ff; }
        .comment { color: #8b949e; font-style: italic; }

        /* --- الخدمات (Cards Grid) --- */
        .grid-3 {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1.5rem;
        }

        .card {
            background: var(--card-bg);
            border: 1px solid var(--border-color);
            border-radius: 10px;
            padding: 1.5rem;
            transition: 0.3s;
            height: 100%;
        }

        .card:hover {
            transform: translateY(-5px);
            border-color: var(--accent-color);
            background: var(--card-hover);
        }

        .card-icon {
            font-size: 2rem;
            color: var(--accent-color);
            margin-bottom: 1rem;
        }

        .card h3 { margin-bottom: 0.5rem; color: #fff; }
        .card p { font-size: 0.9rem; color: var(--text-muted); }

        /* --- المشاريع --- */
        .project-card {
            background: var(--card-bg);
            border: 1px solid var(--border-color);
            border-radius: 12px;
            overflow: hidden;
            transition: 0.3s;
            display: flex;
            flex-direction: column;
        }

        .project-card:hover {
            transform: translateY(-5px);
            border-color: var(--accent-color);
            box-shadow: 0 10px 20px rgba(0,0,0,0.2);
        }

        .project-body { padding: 1.5rem; flex-grow: 1; }
        
        .project-tags {
            margin-top: 1rem;
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
        }

        .tag {
            background: rgba(88, 166, 255, 0.1);
            color: var(--accent-color);
            padding: 4px 10px;
            border-radius: 15px;
            font-size: 0.75rem;
            font-weight: 600;
        }

        .project-links {
            padding: 1rem 1.5rem;
            border-top: 1px solid var(--border-color);
            display: flex;
            gap: 1rem;
        }

        .project-links a {
            color: var(--text-main);
            text-decoration: none;
            font-size: 0.9rem;
            display: flex;
            align-items: center;
            gap: 5px;
        }

        .project-links a:hover { color: var(--accent-color); }

        /* --- المهارات --- */
        .skills-container {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            justify-content: center;
        }
        
        .skill-badge {
            background: #21262d;
            border: 1px solid var(--border-color);
            padding: 10px 20px;
            border-radius: 8px;
            display: flex;
            align-items: center;
            gap: 10px;
            transition: 0.3s;
            text-decoration: none;
            color: var(--text-main);
        }

        .skill-badge:hover {
            border-color: var(--accent-color);
            background: #30363d;
        }

        /* --- الإحصائيات --- */
        .stats-wrapper {
            display: flex;
            flex-direction: column;
            gap: 1.5rem;
            align-items: center;
        }
        
        .stats-img {
            max-width: 100%;
            height: auto;
            border-radius: 8px;
            border: 1px solid var(--border-color);
        }

        /* --- الفوتر --- */
        footer {
            text-align: center;
            padding: 3rem 1rem;
            border-top: 1px solid var(--border-color);
            margin-top: 4rem;
            background: linear-gradient(to top, #161b22, #0d1117);
        }

        /* --- الأنيميشن --- */
        @keyframes fadeInDown {
            from { opacity: 0; transform: translateY(-30px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @keyframes fadeInUp {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* --- استجابة الجوال --- */
        @media (max-width: 768px) {
            h1 { font-size: 2rem; }
            .nav-links { display: none; } /* يمكن إضافة قائمة هامبرغر لاحقاً */
            .grid-3 { grid-template-columns: 1fr; }
        }
    </style>
</head>
<body>

    <!-- شريط التنقل -->
    <nav>
        <div class="nav-container">
            <a href="#" class="logo">&lt;Samy /&gt;</a>
            <div class="nav-links">
                <a href="#about">عني</a>
                <a href="#services">خدماتي</a>
                <a href="#projects">المشاريع</a>
                <a href="#stats">إحصائيات</a>
            </div>
        </div>
    </nav>

    <div class="container">
        
        <!-- الرأس -->
        <header>
            <span class="tagline">Backend Developer • PHP & SQL Specialist</span>
            
            <img src="https://capsule-render.vercel.app/api?type=waving&color=0d1117&height=200&section=header&text=Samy%20Ahmed&fontSize=60&animation=fadeIn&fontAlignY=38&desc=Building%20Robust%20Backend%20Systems&descAlignY=65&descAlign=50&fontColor=58a6ff" alt="Samy Ahmed Banner" class="profile-header-img">
            
            <h1>مرحباً، أنا سامي أحمد 👋</h1>
            <p class="bio-text">
                مطور برمجيات متخصص في بناء الأنظمة الخلفية (Backend) وقواعد البيانات. 
                أساعد الشركات والأفراد في تحويل الأفكار إلى منصات رقمية آمنة، سريعة، وقابلة للتوسع.
            </p>

            <div class="social-links">
                <a href="https://samy-ahmed.site/" class="btn btn-primary" target="_blank">
                    <i class="fas fa-globe"></i> الموقع الشخصي
                </a>
                <a href="mailto:contact@samy-ahmed.site" class="btn">
                    <i class="fas fa-envelope"></i> تواصل معي
                </a>
                <a href="https://github.com/Samy-Ahmed" class="btn">
                    <i class="fab fa-github"></i> GitHub
                </a>
                <a href="https://linkedin.com/" class="btn">
                    <i class="fab fa-linkedin"></i> LinkedIn
                </a>
            </div>
        </header>

        <!-- نبذة عني (كود) -->
        <section id="about">
            <h2 class="section-title"><i class="fas fa-terminal"></i> من أنا؟ (About Me)</h2>
            <div class="code-window">
                <div class="window-header">
                    <div class="dots">
                        <div class="dot red"></div>
                        <div class="dot yellow"></div>
                        <div class="dot green"></div>
                    </div>
                    <div class="filename">Profile.php</div>
                </div>
                <div class="code-block">
<pre><code><span class="keyword">&lt;?php</span>

<span class="keyword">class</span> <span class="class-name">SamyAhmed</span> {
    <span class="keyword">public</span> <span class="variable">$role</span> = <span class="string">"Full Stack Developer"</span>;
    <span class="keyword">public</span> <span class="variable">$specialty</span> = <span class="string">"PHP & SQL Architecture"</span>;
    <span class="keyword">public</span> <span class="variable">$location</span> = <span class="string">"Worldwide 🌍"</span>;
    
    <span class="comment">// هدفي هو بناء كود نظيف وقابل للصيانة</span>
    <span class="keyword">public function</span> <span class="class-name">getMission</span>() {
        <span class="keyword">return</span> <span class="string">"Building secure, scalable, and efficient web applications that solve real problems."</span>;
    }
}
<span class="keyword">?&gt;</span></code></pre>
                </div>
            </div>
        </section>
<!-- 
        <!-- ما الذي أقدمه؟ (الخدمات) -->
        <section id="services">
            <h2 class="section-title"><i class="fas fa-briefcase"></i> ما الذي أقدمه؟</h2>
            <div class="grid-3">
                <div class="card">
                    <div class="card-icon"><i class="fas fa-server"></i></div>
                    <h3>Backend Development</h3>
                    <p>بناء منطق الخادم (Server-side) باستخدام PHP وأطر عمل حديثة لضمان أداء عالٍ للنظام.</p>
                </div>
                <div class="card">
                    <div class="card-icon"><i class="fas fa-database"></i></div>
                    <h3>Database Design</h3>
                    <p>تصميم وهيكلة قواعد بيانات SQL معقدة، مع التركيز على تحسين الاستعلامات (Query Optimization).</p>
                </div>
                <div class="card">
                    <div class="card-icon"><i class="fas fa-shield-alt"></i></div>
                    <h3>API Security</h3>
                    <p>بناء واجهات برمجية (APIs) آمنة ومحمية ضد الثغرات الشائعة لضمان سلامة البيانات.</p>
                </div>
            </div>
        </section>

        <!-- المهارات -->
        <section id="skills">
            <h2 class="section-title"><i class="fas fa-laptop-code"></i> عدّة الشغل (Tech Stack)</h2>
            <div class="skills-container">
                <a href="#" class="skill-badge"><img src="https://img.icons8.com/color/24/000000/php.png"/> PHP</a>
                <a href="#" class="skill-badge"><img src="https://img.icons8.com/color/24/000000/mysql-logo.png"/> MySQL</a>
                <a href="#" class="skill-badge"><img src="https://img.icons8.com/color/24/000000/javascript--v1.png"/> JavaScript</a>
                <a href="#" class="skill-badge"><img src="https://img.icons8.com/color/24/000000/html-5--v1.png"/> HTML5</a>
                <a href="#" class="skill-badge"><img src="https://img.icons8.com/color/24/000000/css3.png"/> CSS3</a>
                <a href="#" class="skill-badge"><img src="https://img.icons8.com/color/24/000000/git.png"/> Git</a>
                <a href="#" class="skill-badge"><img src="https://img.icons8.com/color/24/000000/linux--v1.png"/> Linux</a>
            </div>
        </section>

        <!-- المشاريع -->
        <section id="projects">
            <h2 class="section-title"><i class="fas fa-project-diagram"></i> أبرز المشاريع</h2>
            <div class="grid-3">
                <!-- مشروع 1 -->
                <div class="project-card">
                    <div class="project-body">
                        <h3>🛒 E-Commerce API</h3>
                        <p>نظام خلفي متكامل لمتجر إلكتروني يدعم إدارة المنتجات، الطلبات، وبوابات الدفع.</p>
                        <div class="project-tags">
                            <span class="tag">PHP</span>
                            <span class="tag">MySQL</span>
                            <span class="tag">REST API</span>
                        </div>
                    </div>
                    <div class="project-links">
                        <a href="#"><i class="fas fa-code"></i> Code</a>
                        <a href="#"><i class="fas fa-external-link-alt"></i> Live</a>
                    </div>
                </div>

                <!-- مشروع 2 -->
                <div class="project-card">
                    <div class="project-body">
                        <h3>📊 Dashboard System</h3>
                        <p>لوحة تحكم إدارية لتحليل البيانات وإدارة المستخدمين بصلاحيات متعددة.</p>
                        <div class="project-tags">
                            <span class="tag">Laravel</span>
                            <span class="tag">Vue.js</span>
                            <span class="tag">SQL</span>
                        </div>
                    </div>
                    <div class="project-links">
                        <a href="#"><i class="fas fa-code"></i> Code</a>
                        <a href="#"><i class="fas fa-external-link-alt"></i> Live</a>
                    </div>
                </div>

                <!-- مشروع 3 -->
                <div class="project-card">
                    <div class="project-body">
                        <h3>💬 Real-time Chat</h3>
                        <p>تطبيق محادثة فوري يعتمد على WebSockets لتواصل سريع وآمن.</p>
                        <div class="project-tags">
                            <span class="tag">PHP</span>
                            <span class="tag">JS</span>
                            <span class="tag">Socket.io</span>
                        </div>
                    </div>
                    <div class="project-links">
                        <a href="#"><i class="fas fa-code"></i> Code</a>
                        <a href="#"><i class="fas fa-external-link-alt"></i> Live</a>
                    </div>
                </div>
            </div>
        </section>

        <!-- إحصائيات GitHub -->
        <section id="stats">
            <h2 class="section-title"><i class="fas fa-chart-line"></i> نشاطي على GitHub</h2>
            <div class="stats-wrapper">
                <div style="display: flex; gap: 1rem; flex-wrap: wrap; justify-content: center; width: 100%;">
                    <img src="https://github-readme-stats.vercel.app/api?username=Samy-Ahmed&show_icons=true&theme=tokyonight&hide_border=true&bg_color=161b22" alt="GitHub Stats" class="stats-img">
                    <img src="https://github-readme-streak-stats.herokuapp.com/?user=Samy-Ahmed&theme=tokyonight&hide_border=true&bg_color=161b22" alt="GitHub Streak" class="stats-img">
                </div>
                <!-- Snake Animation -->
                <div style="width: 100%; overflow: hidden; border-radius: 8px; border: 1px solid var(--border-color);">
                    <img src="https://github-readme-activity-graph.vercel.app/graph?username=Samy-Ahmed&bg_color=161b22&color=58a6ff&line=58a6ff&point=ffffff&area=true&hide_border=true" alt="Contribution Graph" style="width: 100%;">
                </div>
            </div>
        </section>

        <!-- الفوتر -->
        <footer>
            <h3>⚡ Motto</h3>
            <blockquote style="font-style: italic; color: var(--text-main); margin: 1rem 0; opacity: 0.8;">
                "Code is like humor. When you have to explain it, it’s bad."
            </blockquote>
            <p style="margin-top: 2rem; color: var(--text-muted); font-size: 0.9rem;">
                © 2026 Samy Ahmed. Built with ❤️ & ☕
            </p>
        </footer> -->

    </div>

</body>
</html>
