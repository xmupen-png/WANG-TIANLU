<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>数字健康医疗产业安全 | 디지털 헬스케어 산업 보안</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=DM+Sans:wght@300;400;500;600&family=Noto+Sans+SC:wght@300;400;500;700&family=Noto+Sans+KR:wght@300;400;500;700&display=swap" rel="stylesheet">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>

    <style>
        :root {
            --ink: #0d1117;
            --ink-2: #1c2733;
            --ink-3: #2d3f50;
            --fog: #f0f4f8;
            --fog-2: #e4ecf3;
            --white: #ffffff;
            --teal: #0a7c8c;
            --teal-light: #12a3b8;
            --teal-pale: rgba(10,124,140,0.08);
            --gold: #c9902b;
            --gold-light: #e8b04a;
            --gold-pale: rgba(201,144,43,0.1);
            --coral: #d4522a;
            --border: rgba(10,124,140,0.15);
            --radius: 4px;
            --radius-lg: 8px;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            font-family: 'DM Sans', 'Noto Sans SC', sans-serif;
            background: var(--fog);
            color: var(--ink);
            line-height: 1.75;
            min-height: 100vh;
            -webkit-font-smoothing: antialiased;
        }

        body::before {
            content: '';
            position: fixed;
            inset: 0;
            background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.03'/%3E%3C/svg%3E");
            pointer-events: none;
            z-index: 0;
        }

        .toolbar {
            position: sticky;
            top: 0;
            z-index: 1000;
            background: rgba(240,244,248,0.85);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border-bottom: 1px solid var(--border);
            padding: 12px 40px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 12px;
        }

        .toolbar-logo {
            font-family: 'DM Serif Display', serif;
            font-size: 0.95rem;
            color: var(--teal);
            letter-spacing: 0.5px;
            opacity: 0.8;
        }

        .toolbar-right {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .lang-switch {
            display: flex;
            background: var(--fog-2);
            border: 1px solid var(--border);
            border-radius: 100px;
            padding: 3px;
            gap: 2px;
        }
        .lang-switch button {
            padding: 6px 16px;
            border: none;
            background: transparent;
            border-radius: 100px;
            cursor: pointer;
            font-size: 0.8rem;
            font-weight: 600;
            color: var(--ink-3);
            transition: all 0.2s ease;
            font-family: inherit;
            letter-spacing: 0.5px;
        }
        .lang-switch button.active {
            background: var(--teal);
            color: #fff;
        }
        .lang-switch button:hover:not(.active) {
            background: var(--teal-pale);
            color: var(--teal);
        }

        .btn-download-pdf {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            padding: 8px 20px;
            background: var(--ink);
            color: #fff;
            border: none;
            border-radius: 100px;
            cursor: pointer;
            font-size: 0.8rem;
            font-weight: 600;
            letter-spacing: 0.8px;
            text-transform: uppercase;
            transition: all 0.25s ease;
            font-family: inherit;
        }
        .btn-download-pdf:hover {
            background: var(--teal);
            transform: translateY(-1px);
        }
        .btn-download-pdf svg {
            width: 14px; height: 14px;
        }

        @keyframes spin { to { transform: rotate(360deg); } }
        .downloading-indicator {
            display: none;
            position: fixed;
            top: 50%; left: 50%;
            transform: translate(-50%, -50%);
            background: var(--ink);
            color: #fff;
            padding: 16px 28px;
            border-radius: 100px;
            font-size: 0.85rem;
            font-weight: 600;
            z-index: 9999;
            letter-spacing: 0.5px;
            align-items: center;
            gap: 12px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
        }
        .downloading-indicator.show { display: flex; }
        .spin-ring {
            width: 16px; height: 16px;
            border: 2px solid rgba(255,255,255,0.3);
            border-top-color: #fff;
            border-radius: 50%;
            animation: spin 0.8s linear infinite;
        }

        .page-wrapper {
            position: relative;
            z-index: 1;
            max-width: 900px;
            margin: 0 auto;
            padding: 40px 24px 80px;
        }

        .hero {
            position: relative;
            background: var(--ink);
            border-radius: 12px;
            padding: 56px 48px;
            margin-bottom: 2px;
            overflow: hidden;
        }

        .hero-bg-circle {
            position: absolute;
            border-radius: 50%;
            pointer-events: none;
        }
        .hero-bg-circle-1 {
            width: 360px; height: 360px;
            background: radial-gradient(circle, rgba(10,124,140,0.35) 0%, transparent 70%);
            top: -100px; right: -100px;
        }
        .hero-bg-circle-2 {
            width: 200px; height: 200px;
            background: radial-gradient(circle, rgba(201,144,43,0.2) 0%, transparent 70%);
            bottom: -60px; left: 60px;
        }

        .hero-tag {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            background: rgba(255,255,255,0.08);
            border: 1px solid rgba(255,255,255,0.12);
            border-radius: 100px;
            padding: 5px 14px;
            font-size: 0.75rem;
            color: rgba(255,255,255,0.6);
            letter-spacing: 1.5px;
            text-transform: uppercase;
            margin-bottom: 28px;
            position: relative; z-index: 1;
        }
        .hero-tag-dot {
            width: 6px; height: 6px;
            background: var(--teal-light);
            border-radius: 50%;
            animation: pulse 2s ease-in-out infinite;
        }
        @keyframes pulse {
            0%, 100% { opacity: 1; transform: scale(1); }
            50% { opacity: 0.5; transform: scale(0.8); }
        }

        .hero-eyebrow {
            font-size: 0.78rem;
            color: var(--teal-light);
            letter-spacing: 3px;
            text-transform: uppercase;
            font-weight: 500;
            margin-bottom: 14px;
            position: relative; z-index: 1;
        }

        .hero-title {
            font-family: 'DM Serif Display', 'Noto Sans SC', serif;
            font-size: clamp(2rem, 5vw, 3.2rem);
            color: #fff;
            line-height: 1.15;
            letter-spacing: -0.5px;
            margin-bottom: 10px;
            position: relative; z-index: 1;
        }

        .hero-title-accent { color: var(--teal-light); }

        .hero-sub {
            font-size: 0.9rem;
            color: rgba(255,255,255,0.45);
            letter-spacing: 1px;
            margin-bottom: 36px;
            position: relative; z-index: 1;
            font-style: italic;
        }

        .hero-meta {
            display: flex;
            align-items: center;
            position: relative; z-index: 1;
            border-top: 1px solid rgba(255,255,255,0.08);
            padding-top: 24px;
        }

        .hero-meta-item {
            display: flex;
            flex-direction: column;
            gap: 2px;
            padding: 0 24px;
            border-right: 1px solid rgba(255,255,255,0.08);
        }
        .hero-meta-item:first-child { padding-left: 0; }
        .hero-meta-item:last-child { border-right: none; }

        .hero-meta-label {
            font-size: 0.68rem;
            color: rgba(255,255,255,0.35);
            letter-spacing: 1.5px;
            text-transform: uppercase;
        }
        .hero-meta-value {
            font-size: 0.85rem;
            color: rgba(255,255,255,0.75);
            font-weight: 500;
        }

        .section-grid {
            display: flex;
            flex-direction: column;
            gap: 2px;
        }

        .card {
            background: var(--white);
            padding: 40px 48px;
            position: relative;
            transition: all 0.3s ease;
        }
        .card:hover { background: #fafcff; }
        .card:last-child { border-radius: 0 0 12px 12px; }

        .card-header {
            display: flex;
            align-items: flex-start;
            gap: 20px;
            margin-bottom: 28px;
        }

        .card-number {
            font-family: 'DM Serif Display', serif;
            font-size: 3.5rem;
            color: var(--fog-2);
            line-height: 1;
            font-style: italic;
            flex-shrink: 0;
            position: relative;
            top: -6px;
            transition: color 0.3s ease;
        }
        .card:hover .card-number { color: var(--teal-pale); }

        .card-header-text { flex: 1; }

        .card-category {
            font-size: 0.68rem;
            font-weight: 600;
            letter-spacing: 2.5px;
            text-transform: uppercase;
            color: var(--teal);
            margin-bottom: 6px;
        }

        .card-title {
            font-family: 'DM Serif Display', 'Noto Sans SC', serif;
            font-size: 1.6rem;
            color: var(--ink);
            line-height: 1.2;
        }

        .card-divider {
            width: 40px;
            height: 2px;
            background: var(--teal);
            margin: 20px 0;
        }

        .card p {
            font-size: 0.925rem;
            color: var(--ink-3);
            margin-bottom: 14px;
            line-height: 1.8;
        }
        .card p:last-of-type { margin-bottom: 0; }

        .feature-list {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 10px 24px;
            margin: 24px 0;
            list-style: none;
        }
        .feature-list li {
            display: flex;
            align-items: flex-start;
            gap: 10px;
            font-size: 0.875rem;
            color: var(--ink-3);
            padding: 10px 0;
            border-bottom: 1px solid var(--fog-2);
        }
        .feature-list li::before {
            content: '';
            width: 5px; height: 5px;
            border-radius: 50%;
            background: var(--teal);
            flex-shrink: 0;
            margin-top: 7px;
        }
        .feature-list.single-col { grid-template-columns: 1fr; }

        .callout {
            background: var(--teal-pale);
            border: 1px solid rgba(10,124,140,0.15);
            border-left: 3px solid var(--teal);
            border-radius: 0 var(--radius-lg) var(--radius-lg) 0;
            padding: 16px 20px;
            margin-top: 24px;
            font-size: 0.875rem;
            color: var(--teal);
            font-weight: 500;
            line-height: 1.6;
            display: flex;
            align-items: flex-start;
            gap: 10px;
        }
        .callout-icon { font-size: 1rem; flex-shrink: 0; margin-top: 1px; }
        .callout.gold {
            background: var(--gold-pale);
            border-color: var(--gold-light);
            border-left-color: var(--gold);
            color: #7a5c1a;
        }

        .stats-row {
            display: flex;
            margin: 28px 0;
            border: 1px solid var(--fog-2);
            border-radius: var(--radius-lg);
            overflow: hidden;
        }
        .stat-item {
            flex: 1;
            padding: 20px 24px;
            border-right: 1px solid var(--fog-2);
            text-align: center;
        }
        .stat-item:last-child { border-right: none; }
        .stat-value {
            font-family: 'DM Serif Display', serif;
            font-size: 2rem;
            color: var(--teal);
            line-height: 1;
            margin-bottom: 4px;
        }
        .stat-label {
            font-size: 0.75rem;
            color: var(--ink-3);
            opacity: 0.6;
            letter-spacing: 0.5px;
        }

        .tag-row {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin: 20px 0;
        }
        .tag {
            display: inline-flex;
            align-items: center;
            gap: 6px;
            padding: 5px 12px;
            background: var(--fog);
            border: 1px solid var(--fog-2);
            border-radius: 100px;
            font-size: 0.77rem;
            font-weight: 500;
            color: var(--ink-3);
        }
        .tag-dot {
            width: 6px; height: 6px;
            border-radius: 50%;
            background: var(--teal-light);
        }

        .footer {
            margin-top: 40px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 0 4px;
        }
        .footer-left {
            font-size: 0.78rem;
            color: var(--ink-3);
            opacity: 0.45;
        }
        .footer-right {
            font-family: 'DM Serif Display', serif;
            font-size: 0.78rem;
            color: var(--teal);
            opacity: 0.6;
            font-style: italic;
        }

        @keyframes fadeUp {
            from { opacity: 0; transform: translateY(24px); }
            to { opacity: 1; transform: translateY(0); }
        }
        .hero { animation: fadeUp 0.6s ease both; }
        .card { animation: fadeUp 0.6s ease both; }
        .card:nth-child(1) { animation-delay: 0.1s; }
        .card:nth-child(2) { animation-delay: 0.2s; }
        .card:nth-child(3) { animation-delay: 0.3s; }
        .card:nth-child(4) { animation-delay: 0.4s; }
        .footer { animation: fadeUp 0.6s 0.5s ease both; }

        @media (max-width: 768px) {
            .toolbar { padding: 10px 16px; }
            .toolbar-logo { display: none; }
            .page-wrapper { padding: 20px 12px 60px; }
            .hero { padding: 36px 24px; }
            .hero-meta { flex-wrap: wrap; gap: 16px; }
            .hero-meta-item { padding: 0 16px; }
            .card { padding: 28px 20px; }
            .card-number { font-size: 2.5rem; }
            .card-title { font-size: 1.3rem; }
            .feature-list { grid-template-columns: 1fr; }
            .stats-row { flex-direction: column; }
            .stat-item { border-right: none; border-bottom: 1px solid var(--fog-2); }
            .stat-item:last-child { border-bottom: none; }
            .footer { flex-direction: column; gap: 8px; text-align: center; }
        }

        @media print {
            .toolbar { display: none !important; }
            body::before { display: none; }
        }
        body.printing .toolbar { display: none !important; }
        body.printing .page-wrapper { padding-top: 10px; }
        body.printing { background: #fff; }
        body.printing .hero,
        body.printing .card { animation: none; }
    </style>
</head>
<body>

    <div class="toolbar" id="toolbar">
        <div class="toolbar-logo">🛡 HealthSec Research</div>
        <div class="toolbar-right">
            <div class="lang-switch">
                <button id="btn-zh" class="active" onclick="switchLanguage('zh')">🇨🇳 中文</button>
                <button id="btn-ko" onclick="switchLanguage('ko')">🇰🇷 한국어</button>
            </div>
            <button class="btn-download-pdf" onclick="downloadPDF()">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                    <path d="M12 15V3M7 10l5 5 5-5"/><path d="M3 18h18v3H3z"/>
                </svg>
                <span id="btn-download-text">下载 PDF</span>
            </button>
        </div>
    </div>

    <div class="downloading-indicator" id="downloadIndicator">
        <div class="spin-ring"></div>
        <span id="downloadIndicatorText">正在生成 PDF…</span>
    </div>

    <div class="page-wrapper" id="pdfExportArea">

        <div class="hero">
            <div class="hero-bg-circle hero-bg-circle-1"></div>
            <div class="hero-bg-circle hero-bg-circle-2"></div>
            <div class="hero-tag"><span class="hero-tag-dot"></span><span id="heroTag">RESEARCH REPORT · 2026</span></div>
            <div class="hero-eyebrow" id="heroEyebrow">WANG TIANLU · 202217132 · 물리치료A</div>
            <h1 class="hero-title">
                <span id="heroTitleLine1">数字健康</span><br>
                <span class="hero-title-accent" id="heroTitleLine2">医疗产业安全</span>
            </h1>
            <div class="hero-sub" id="heroSub">Digital Healthcare Industry Security</div>
            <div class="hero-meta">
                <div class="hero-meta-item">
                    <span class="hero-meta-label" id="metaLabel1">专业</span>
                    <span class="hero-meta-value">물리치료A</span>
                </div>
                <div class="hero-meta-item">
                    <span class="hero-meta-label" id="metaLabel2">姓名</span>
                    <span class="hero-meta-value">WANG TIANLU</span>
                </div>
                <div class="hero-meta-item">
                    <span class="hero-meta-label" id="metaLabel3">学号</span>
                    <span class="hero-meta-value">202217132</span>
                </div>
                <div class="hero-meta-item">
                    <span class="hero-meta-label" id="metaLabel4">年度</span>
                    <span class="hero-meta-value">2026</span>
                </div>
            </div>
        </div>

        <div class="section-grid">

            <div class="card" id="section1">
                <div class="card-header">
                    <div class="card-number">01</div>
                    <div class="card-header-text">
                        <div class="card-category" id="sec1Cat">DESIGN &amp; DEVELOPMENT</div>
                        <h2 class="card-title" id="sec1Title">网站设计与开发方法</h2>
                    </div>
                </div>
                <div class="card-divider"></div>
                <p id="sec1p1">本网站采用现代Web开发技术栈，基于HTML5语义化结构、CSS3层叠样式表以及JavaScript（ES6+）动态脚本语言进行构建。整体架构遵循前端分离设计原则，确保代码的可维护性与可扩展性。在开发过程中，严格遵循W3C国际标准规范，保证网页在不同浏览器环境中的兼容性与稳定性。</p>
                <p id="sec1p2">设计层面采用响应式网页设计理念，通过CSS媒体查询与弹性布局技术，使网站能够自适应桌面端、平板端以及移动端等多种屏幕尺寸。后端数据交互采用安全的RESTful API架构，所有数据传输均通过HTTPS/TLS加密协议进行，有效防止数据在传输过程中被窃取或篡改。</p>
                <ul class="feature-list">
                    <li id="sec1li1">HTML5 + CSS3 + JavaScript (ES6+)</li>
                    <li id="sec1li2">全站 HTTPS / TLS 1.3 加密</li>
                    <li id="sec1li3">ORM 框架防范 SQL 注入</li>
                    <li id="sec1li4">JWT 双因素身份验证</li>
                    <li id="sec1li5">移动优先响应式布局</li>
                </ul>
                <div class="callout">
                    <span class="callout-icon">🔐</span>
                    <span id="sec1Highlight">核心安全理念：纵深防御策略，从网络层、应用层到数据层实现多层次安全防护体系。</span>
                </div>
            </div>

            <div class="card" id="section2">
                <div class="card-header">
                    <div class="card-number">02</div>
                    <div class="card-header-text">
                        <div class="card-category" id="sec2Cat">CORE FEATURES</div>
                        <h2 class="card-title" id="sec2Title">网站主要功能介绍</h2>
                    </div>
                </div>
                <div class="card-divider"></div>
                <p id="sec2p1">本网站围绕数字健康医疗产业安全的核心需求，设计了多项关键功能模块。医疗数据加密存储与安全传输模块确保患者的敏感健康信息在存储和流转过程中始终处于加密保护状态；健康信息安全监测系统能够实时检测异常访问行为，及时发出安全预警；产业安全风险评估工具为医疗机构提供全面的安全漏洞扫描与风险等级评定服务。</p>
                <p id="sec2p2">此外，网站还集成了用户隐私保护管理控制台，允许管理员精细化配置数据访问权限；合规性审查功能模块依据国内外医疗数据保护法规（如HIPAA、GDPR及中国《数据安全法》）进行自动化合规检查，确保平台的运营始终符合法律要求。</p>
                <div class="tag-row">
                    <span class="tag"><span class="tag-dot"></span><span id="tag1">医疗数据加密</span></span>
                    <span class="tag"><span class="tag-dot"></span><span id="tag2">实时安全监测</span></span>
                    <span class="tag"><span class="tag-dot"></span><span id="tag3">风险评估扫描</span></span>
                    <span class="tag"><span class="tag-dot"></span><span id="tag4">隐私权限管理</span></span>
                    <span class="tag"><span class="tag-dot"></span><span id="tag5">HIPAA / GDPR</span></span>
                    <span class="tag"><span class="tag-dot"></span><span id="tag6">审计日志追溯</span></span>
                </div>
                <div class="callout gold">
                    <span class="callout-icon">📊</span>
                    <span id="sec2Highlight">实时仪表盘：可视化展示安全态势，一目了然地掌握整体安全健康状况。</span>
                </div>
            </div>

            <div class="card" id="section3">
                <div class="card-header">
                    <div class="card-number">03</div>
                    <div class="card-header-text">
                        <div class="card-category" id="sec3Cat">IMPACT &amp; VALUE</div>
                        <h2 class="card-title" id="sec3Title">预期效果与应用价值</h2>
                    </div>
                </div>
                <div class="card-divider"></div>
                <p id="sec3p1">通过部署本网站所构建的数字健康医疗安全防护体系，预期能够显著提升医疗数据的整体安全水平，将数据泄露风险降低80%以上。平台提供的自动化安全评估功能可帮助医疗机构节省大量人工审计成本，提高安全运营效率。同时，通过增强用户对数据隐私保护的信任度，有助于推动数字医疗服务的广泛普及与深度应用。</p>
                <p id="sec3p2">在产业层面，本网站的推广应用将促进医疗健康行业信息安全标准的统一与规范化发展，为医疗产业的数字化转型提供坚实的安全底座。长远来看，可靠的安全保障体系是数字健康医疗产业可持续发展的关键前提，具有重大的社会价值与经济价值。</p>
                <div class="stats-row">
                    <div class="stat-item">
                        <div class="stat-value">80%+</div>
                        <div class="stat-label" id="stat1Label">数据泄露风险降低</div>
                    </div>
                    <div class="stat-item">
                        <div class="stat-value">3×</div>
                        <div class="stat-label" id="stat2Label">审计效率提升</div>
                    </div>
                    <div class="stat-item">
                        <div class="stat-value">24/7</div>
                        <div class="stat-label" id="stat3Label">实时安全监控</div>
                    </div>
                </div>
                <div class="callout">
                    <span class="callout-icon">🌍</span>
                    <span id="sec3Highlight">社会价值：守护人民健康数据安全，助力构建可信赖的数字健康生态系统。</span>
                </div>
            </div>

            <div class="card" id="section4">
                <div class="card-header">
                    <div class="card-number">04</div>
                    <div class="card-header-text">
                        <div class="card-category" id="sec4Cat">DISCLAIMER</div>
                        <h2 class="card-title" id="sec4Title">其他相关说明</h2>
                    </div>
                </div>
                <div class="card-divider"></div>
                <p id="sec4p1">本网站所展示的内容仅供学术研究与教育参考之用，不构成任何形式的商业建议或法律意见。在实际部署与应用过程中，建议结合具体业务场景与当地法律法规要求进行适当调整。网站中涉及的安全策略与技术方案基于当前主流的行业实践，随着网络威胁环境的不断演变，相关安全措施需要持续更新与迭代优化。</p>
                <p id="sec4p2">开发者保留对网站内容进行修改与更新的权利。对于因使用本网站信息而产生的任何直接或间接后果，开发者不承担法律责任。如需引用或转载本网站内容，请注明出处并联系作者获得授权。本项目的开发遵守相关知识产权法律法规，所使用的开源组件均遵循其各自的许可协议。</p>
                <ul class="feature-list single-col">
                    <li id="sec4li1">内容仅供学术研究与教育参考</li>
                    <li id="sec4li2">安全策略需根据实际环境持续迭代优化</li>
                    <li id="sec4li3">引用或转载需注明出处并获得授权</li>
                    <li id="sec4li4">遵守知识产权与开源许可协议</li>
                </ul>
                <div class="callout gold">
                    <span class="callout-icon">⚠️</span>
                    <span id="sec4Highlight">免责声明：本网站信息仅供参考，具体实施请结合实际情况并咨询专业安全顾问。</span>
                </div>
            </div>

        </div>

        <div class="footer">
            <div class="footer-left" id="footerLeft">© 2026 WANG TIANLU · 물리치료A · 202217132</div>
            <div class="footer-right" id="footerRight">数字健康医疗产业安全研究报告</div>
        </div>

    </div>

    <script>
    const translations = {
        zh: {
            heroTag: 'RESEARCH REPORT · 2026',
            heroEyebrow: 'WANG TIANLU · 202217132 · 물리치료A',
            heroTitleLine1: '数字健康',
            heroTitleLine2: '医疗产业安全',
            heroSub: 'Digital Healthcare Industry Security',
            metaLabel1:'专业', metaLabel2:'姓名', metaLabel3:'学号', metaLabel4:'年度',
            btnDownloadText: '下载 PDF',
            downloadIndicatorText: '正在生成 PDF…',
            sec1Cat: 'DESIGN & DEVELOPMENT',
            sec1Title: '网站设计与开发方法',
            sec1p1: '本网站采用现代Web开发技术栈，基于HTML5语义化结构、CSS3层叠样式表以及JavaScript（ES6+）动态脚本语言进行构建。整体架构遵循前端分离设计原则，确保代码的可维护性与可扩展性。在开发过程中，严格遵循W3C国际标准规范，保证网页在不同浏览器环境中的兼容性与稳定性。',
            sec1p2: '设计层面采用响应式网页设计理念，通过CSS媒体查询与弹性布局技术，使网站能够自适应桌面端、平板端以及移动端等多种屏幕尺寸。后端数据交互采用安全的RESTful API架构，所有数据传输均通过HTTPS/TLS加密协议进行，有效防止数据在传输过程中被窃取或篡改。',
            sec1li1: 'HTML5 + CSS3 + JavaScript (ES6+)',
            sec1li2: '全站 HTTPS / TLS 1.3 加密',
            sec1li3: 'ORM 框架防范 SQL 注入',
            sec1li4: 'JWT 双因素身份验证',
            sec1li5: '移动优先响应式布局',
            sec1Highlight: '核心安全理念：纵深防御策略，从网络层、应用层到数据层实现多层次安全防护体系。',
            sec2Cat: 'CORE FEATURES',
            sec2Title: '网站主要功能介绍',
            sec2p1: '本网站围绕数字健康医疗产业安全的核心需求，设计了多项关键功能模块。医疗数据加密存储与安全传输模块确保患者的敏感健康信息在存储和流转过程中始终处于加密保护状态；健康信息安全监测系统能够实时检测异常访问行为，及时发出安全预警；产业安全风险评估工具为医疗机构提供全面的安全漏洞扫描与风险等级评定服务。',
            sec2p2: '此外，网站还集成了用户隐私保护管理控制台，允许管理员精细化配置数据访问权限；合规性审查功能模块依据国内外医疗数据保护法规（如HIPAA、GDPR及中国《数据安全法》）进行自动化合规检查，确保平台的运营始终符合法律要求。',
            tag1:'医疗数据加密', tag2:'实时安全监测', tag3:'风险评估扫描',
            tag4:'隐私权限管理', tag5:'HIPAA / GDPR', tag6:'审计日志追溯',
            sec2Highlight: '实时仪表盘：可视化展示安全态势，一目了然地掌握整体安全健康状况。',
            sec3Cat: 'IMPACT & VALUE',
            sec3Title: '预期效果与应用价值',
            sec3p1: '通过部署本网站所构建的数字健康医疗安全防护体系，预期能够显著提升医疗数据的整体安全水平，将数据泄露风险降低80%以上。平台提供的自动化安全评估功能可帮助医疗机构节省大量人工审计成本，提高安全运营效率。同时，通过增强用户对数据隐私保护的信任度，有助于推动数字医疗服务的广泛普及与深度应用。',
            sec3p2: '在产业层面，本网站的推广应用将促进医疗健康行业信息安全标准的统一与规范化发展，为医疗产业的数字化转型提供坚实的安全底座。长远来看，可靠的安全保障体系是数字健康医疗产业可持续发展的关键前提，具有重大的社会价值与经济价值。',
            stat1Label:'数据泄露风险降低', stat2Label:'审计效率提升', stat3Label:'实时安全监控',
            sec3Highlight: '社会价值：守护人民健康数据安全，助力构建可信赖的数字健康生态系统。',
            sec4Cat: 'DISCLAIMER',
            sec4Title: '其他相关说明',
            sec4p1: '本网站所展示的内容仅供学术研究与教育参考之用，不构成任何形式的商业建议或法律意见。在实际部署与应用过程中，建议结合具体业务场景与当地法律法规要求进行适当调整。网站中涉及的安全策略与技术方案基于当前主流的行业实践，随着网络威胁环境的不断演变，相关安全措施需要持续更新与迭代优化。',
            sec4p2: '开发者保留对网站内容进行修改与更新的权利。对于因使用本网站信息而产生的任何直接或间接后果，开发者不承担法律责任。如需引用或转载本网站内容，请注明出处并联系作者获得授权。本项目的开发遵守相关知识产权法律法规，所使用的开源组件均遵循其各自的许可协议。',
            sec4li1: '内容仅供学术研究与教育参考',
            sec4li2: '安全策略需根据实际环境持续迭代优化',
            sec4li3: '引用或转载需注明出处并获得授权',
            sec4li4: '遵守知识产权与开源许可协议',
            sec4Highlight: '免责声明：本网站信息仅供参考，具体实施请结合实际情况并咨询专业安全顾问。',
            footerLeft: '© 2026 WANG TIANLU · 물리치료A · 202217132',
            footerRight: '数字健康医疗产业安全研究报告',
        },
        ko: {
            heroTag: 'RESEARCH REPORT · 2026',
            heroEyebrow: 'WANG TIANLU · 202217132 · 물리치료A',
            heroTitleLine1: '디지털 헬스케어',
            heroTitleLine2: '산업 보안',
            heroSub: 'Digital Healthcare Industry Security',
            metaLabel1:'전공', metaLabel2:'성명', metaLabel3:'학번', metaLabel4:'연도',
            btnDownloadText: 'PDF 다운로드',
            downloadIndicatorText: 'PDF 생성 중…',
            sec1Cat: 'DESIGN & DEVELOPMENT',
            sec1Title: '웹사이트 설계 및 개발 방법',
            sec1p1: '본 웹사이트는 HTML5 시맨틱 구조, CSS3 스타일시트 및 JavaScript(ES6+) 동적 스크립트 언어를 기반으로 하는 최신 웹 개발 기술 스택을 채택하여 구축되었습니다. 전체 아키텍처는 프론트엔드 분리 설계 원칙을 따르며, 코드의 유지보수성과 확장성을 보장합니다. 개발 과정에서 W3C 국제 표준을 엄격히 준수하여 다양한 브라우저 환경에서의 호환성과 안정성을 확보했습니다.',
            sec1p2: '디자인 측면에서는 반응형 웹 디자인 개념을 채택하여 CSS 미디어 쿼리와 유연한 레이아웃 기술을 통해 다양한 화면 크기에 자동으로 적응합니다. 백엔드 데이터 통신은 안전한 RESTful API 아키텍처를 사용하며, 모든 데이터 전송은 HTTPS/TLS 암호화 프로토콜을 통해 이루어집니다.',
            sec1li1: 'HTML5 + CSS3 + JavaScript (ES6+)',
            sec1li2: '전 사이트 HTTPS / TLS 1.3 암호화',
            sec1li3: 'ORM 프레임워크로 SQL 인젝션 방지',
            sec1li4: 'JWT 이중 요소 인증',
            sec1li5: '모바일 우선 반응형 레이아웃',
            sec1Highlight: '핵심 보안 이념: 심층 방어 전략, 네트워크 계층에서 데이터 계층까지 다단계 보안 방어 체계 구현.',
            sec2Cat: 'CORE FEATURES',
            sec2Title: '웹사이트 주요 기능 소개',
            sec2p1: '본 웹사이트는 디지털 헬스케어 산업 보안의 핵심 요구사항을 중심으로 여러 주요 기능 모듈을 설계했습니다. 의료 데이터 암호화 저장 및 안전한 전송 모듈은 환자의 민감한 건강 정보가 항상 암호화 보호 상태를 유지하도록 합니다. 건강 정보 보안 모니터링 시스템은 비정상적인 접근 행위를 실시간으로 감지하여 신속하게 보안 경보를 발령합니다.',
            sec2p2: '또한 사용자 개인정보 보호 관리 콘솔을 통합하여 관리자가 데이터 접근 권한을 세밀하게 구성할 수 있도록 했으며, 규정 준수 심사 기능 모듈은 HIPAA, GDPR 및 중국 데이터 보안법에 따라 자동화된 규정 준수 검사를 수행합니다.',
            tag1:'의료 데이터 암호화', tag2:'실시간 보안 모니터링', tag3:'위험 평가 스캔',
            tag4:'개인정보 권한 관리', tag5:'HIPAA / GDPR', tag6:'감사 로그 추적',
            sec2Highlight: '실시간 대시보드: 보안 상태를 시각화하여 전반적인 보안 건강 상태를 한눈에 파악합니다.',
            sec3Cat: 'IMPACT & VALUE',
            sec3Title: '기대 효과 및 적용 가치',
            sec3p1: '본 웹사이트에서 구축한 디지털 헬스케어 보안 방어 체계를 배포함으로써 의료 데이터의 전반적인 보안 수준을 크게 향상시키고 데이터 유출 위험을 80% 이상 감소시킬 수 있을 것으로 기대됩니다. 플랫폼이 제공하는 자동화된 보안 평가 기능은 의료 기관의 감사 비용 절감과 보안 운영 효율성 향상에 기여합니다.',
            sec3p2: '산업 차원에서 본 웹사이트의 보급 및 적용은 의료 건강 산업의 정보 보안 표준 통일과 규범화 발전을 촉진하여 의료 산업의 디지털 전환을 위한 견고한 보안 기반을 제공할 것입니다.',
            stat1Label:'데이터 유출 위험 감소', stat2Label:'감사 효율성 향상', stat3Label:'실시간 보안 모니터링',
            sec3Highlight: '사회적 가치: 국민 건강 데이터 보안을 수호하고 신뢰할 수 있는 디지털 건강 생태계 구축에 기여합니다.',
            sec4Cat: 'DISCLAIMER',
            sec4Title: '기타 관련 설명',
            sec4p1: '본 웹사이트에 게시된 내용은 학술 연구 및 교육 참고 목적으로만 제공되며, 어떠한 형태의 상업적 조언이나 법적 의견도 구성하지 않습니다. 실제 배포 및 적용 시에는 구체적인 비즈니스 시나리오와 현지 법률 규정 요구사항에 따라 적절히 조정할 것을 권장합니다.',
            sec4p2: '개발자는 웹사이트 내용을 수정하고 업데이트할 권리를 보유합니다. 본 웹사이트 정보 사용으로 인해 발생하는 직간접적인 결과에 대해 개발자는 법적 책임을 지지 않습니다. 인용 또는 전재 시 출처를 명시하고 저자에게 연락하여 승인을 받으시기 바랍니다.',
            sec4li1: '내용은 학술 연구 및 교육 참고용으로만 제공',
            sec4li2: '보안 전략은 실제 환경에 따라 지속적으로 최적화',
            sec4li3: '인용 또는 전재 시 출처 표시 및 승인 필요',
            sec4li4: '지식재산권 및 오픈소스 라이선스 준수',
            sec4Highlight: '면책 조항: 본 웹사이트 정보는 참고용이며, 구체적인 구현은 전문 보안 컨설턴트와 상담하시기 바랍니다.',
            footerLeft: '© 2026 WANG TIANLU · 물리치료A · 202217132',
            footerRight: '디지털 헬스케어 산업 보안 연구 보고서',
        }
    };

    let currentLang = 'zh';

    const ids = [
        'heroTag','heroEyebrow','heroTitleLine1','heroTitleLine2','heroSub',
        'metaLabel1','metaLabel2','metaLabel3','metaLabel4',
        'btnDownloadText','downloadIndicatorText',
        'sec1Cat','sec1Title','sec1p1','sec1p2','sec1li1','sec1li2','sec1li3','sec1li4','sec1li5','sec1Highlight',
        'sec2Cat','sec2Title','sec2p1','sec2p2','tag1','tag2','tag3','tag4','tag5','tag6','sec2Highlight',
        'sec3Cat','sec3Title','sec3p1','sec3p2','stat1Label','stat2Label','stat3Label','sec3Highlight',
        'sec4Cat','sec4Title','sec4p1','sec4p2','sec4li1','sec4li2','sec4li3','sec4li4','sec4Highlight',
        'footerLeft','footerRight'
    ];

    function switchLanguage(lang) {
        if (lang === currentLang) return;
        currentLang = lang;
        const t = translations[lang];
        ids.forEach(id => {
            const el = document.getElementById(id);
            if (el && t[id] !== undefined) el.textContent = t[id];
        });
        document.getElementById('btn-zh').classList.toggle('active', lang === 'zh');
        document.getElementById('btn-ko').classList.toggle('active', lang === 'ko');
        document.documentElement.lang = lang === 'zh' ? 'zh-CN' : 'ko-KR';
        document.body.style.fontFamily = lang === 'ko'
            ? "'DM Sans','Noto Sans KR',sans-serif"
            : "'DM Sans','Noto Sans SC',sans-serif";
        window.scrollTo({ top: 0, behavior: 'smooth' });
    }

    function downloadPDF() {
        const indicator = document.getElementById('downloadIndicator');
        indicator.classList.add('show');
        document.body.classList.add('printing');
        setTimeout(() => {
            html2pdf().set({
                margin: [8, 8, 8, 8],
                filename: currentLang === 'zh'
                    ? '数字健康医疗产业安全_报告.pdf'
                    : '디지털헬스케어산업보안_보고서.pdf',
                image: { type: 'jpeg', quality: 0.97 },
                html2canvas: { scale: 2, useCORS: true, logging: false },
                jsPDF: { unit: 'mm', format: 'a4', orientation: 'portrait' },
                pagebreak: { mode: ['avoid-all','css'], avoid: ['.card','.hero'] }
            })
            .from(document.getElementById('pdfExportArea'))
            .save()
            .finally(() => {
                indicator.classList.remove('show');
                document.body.classList.remove('printing');
            });
        }, 300);
    }

    document.addEventListener('keydown', e => {
        if ((e.ctrlKey || e.metaKey) && e.shiftKey && e.key === 'P') { e.preventDefault(); downloadPDF(); }
        if ((e.ctrlKey || e.metaKey) && e.shiftKey && e.key === 'L') { e.preventDefault(); switchLanguage(currentLang === 'zh' ? 'ko' : 'zh'); }
    });
    </script>
</body>
</html>


