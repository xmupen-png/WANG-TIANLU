# WANG-TIANL<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>디지털 헬스케어 산업 보안 | Digital Healthcare Industry Security</title>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@300;400;500;700;900&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js">
    </script>l
    <style>
        :root {
            --primary: #0d4f7c;
            --primary-light: #1a6fa0;
            --primary-dark: #0a3a5c;
            --accent: #1e8c7a;
            --accent-light: #2aab96;
            --danger: #d94436;
            --danger-light: #fef2f0;
            --bg: #f5f7fa;
            --bg-card: #ffffff;
            --text: #1a202c;
            --text-secondary: #4a5568;
            --text-light: #718096;
            --border: #e2e8f0;
            --border-light: #edf2f7;
            --shadow-sm: 0 1px 3px rgba(0, 0, 0, 0.06), 0 1px 2px rgba(0, 0, 0, 0.04);
            --shadow: 0 4px 16px rgba(0, 0, 0, 0.08), 0 2px 6px rgba(0, 0, 0, 0.04);
            --shadow-lg: 0 12px 32px rgba(0, 0, 0, 0.12), 0 4px 12px rgba(0, 0, 0, 0.06);
            --shadow-xl: 0 20px 48px rgba(0, 0, 0, 0.18), 0 8px 20px rgba(0, 0, 0, 0.08);
            --radius-sm: 8px;
            --radius: 12px;
            --radius-lg: 20px;
            --radius-xl: 28px;
            --transition: 0.25s cubic-bezier(0.4, 0, 0.2, 1);
            --font-kr: 'Noto Sans KR', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html {
            scroll-behavior: smooth;
            font-size: 16px;
        }

        body {
            font-family: var(--font-kr);
            background: var(--bg);
            color: var(--text);
            line-height: 1.7;
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
            min-height: 100vh;
        }

        /* ============ HEADER / NAVIGATION ============ */
        .header {
            position: sticky;
            top: 0;
            z-index: 1000;
            background: rgba(255, 255, 255, 0.92);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border-bottom: 1px solid var(--border-light);
            transition: var(--transition);
            padding: 0 2rem;
        }

        .header.scrolled {
            box-shadow: var(--shadow);
            background: rgba(255, 255, 255, 0.97);
        }

        .nav {
            max-width: 1280px;
            margin: 0 auto;
            display: flex;
            align-items: center;
            justify-content: space-between;
            height: 68px;
            gap: 2rem;
        }

        .nav-logo {
            display: flex;
            align-items: center;
            gap: 10px;
            text-decoration: none;
            color: var(--primary-dark);
            font-weight: 800;
            font-size: 1.25rem;
            letter-spacing: -0.3px;
            white-space: nowrap;
            flex-shrink: 0;
        }

        .nav-logo .logo-icon {
            width: 42px;
            height: 42px;
            border-radius: var(--radius-sm);
            background: linear-gradient(135deg, var(--primary), var(--primary-light));
            display: flex;
            align-items: center;
            justify-content: center;
            color: #fff;
            font-size: 1.3rem;
            flex-shrink: 0;
            box-shadow: 0 3px 10px rgba(13, 79, 124, 0.3);
        }

        .nav-links {
            display: flex;
            align-items: center;
            gap: 0.3rem;
            list-style: none;
            flex-wrap: wrap;
            justify-content: flex-end;
        }

        .nav-links a {
            text-decoration: none;
            color: var(--text-secondary);
            font-weight: 500;
            font-size: 0.9rem;
            padding: 0.5rem 0.9rem;
            border-radius: 20px;
            transition: var(--transition);
            white-space: nowrap;
            letter-spacing: -0.2px;
        }

        .nav-links a:hover,
        .nav-links a.active {
            color: var(--primary);
            background: rgba(13, 79, 124, 0.06);
        }

        .nav-download-btn {
            display: inline-flex;
            align-items: center;
            gap: 7px;
            padding: 0.55rem 1.2rem;
            background: var(--primary);
            color: #fff !important;
            border-radius: 24px;
            font-weight: 600 !important;
            font-size: 0.88rem !important;
            cursor: pointer;
            border: none;
            transition: var(--transition);
            white-space: nowrap;
            letter-spacing: -0.2px;
            box-shadow: 0 3px 12px rgba(13, 79, 124, 0.25);
            text-decoration: none;
            flex-shrink: 0;
        }

        .nav-download-btn:hover {
            background: var(--primary-dark);
            box-shadow: 0 6px 20px rgba(13, 79, 124, 0.35);
            transform: translateY(-1px);
            color: #fff !important;
        }

        /* ============ HERO SECTION ============ */
        .hero {
            background: linear-gradient(160deg, #f0f6fb 0%, #e8f2f9 30%, #f5f9fc 60%, #fefefe 100%);
            padding: 4rem 2rem 3.5rem;
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: -120px;
            right: -80px;
            width: 420px;
            height: 420px;
            border-radius: 50%;
            background: radial-gradient(circle, rgba(26, 111, 160, 0.07) 0%, transparent 70%);
            pointer-events: none;
        }

        .hero::after {
            content: '';
            position: absolute;
            bottom: -60px;
            left: -40px;
            width: 280px;
            height: 280px;
            border-radius: 50%;
            background: radial-gradient(circle, rgba(30, 140, 122, 0.06) 0%, transparent 70%);
            pointer-events: none;
        }

        .hero-inner {
            max-width: 1280px;
            margin: 0 auto;
            display: flex;
            align-items: center;
            gap: 3rem;
            position: relative;
            z-index: 1;
        }

        .hero-text {
            flex: 1;
            min-width: 0;
        }

        .hero-badge {
            display: inline-block;
            padding: 0.4rem 1rem;
            background: rgba(217, 68, 54, 0.08);
            color: var(--danger);
            font-weight: 700;
            font-size: 0.82rem;
            border-radius: 20px;
            letter-spacing: 0.3px;
            margin-bottom: 1.2rem;
            border: 1px solid rgba(217, 68, 54, 0.15);
        }

        .hero-badge i {
            margin-right: 5px;
            animation: pulse-badge 2s infinite;
        }

        @keyframes pulse-badge {
            0%,
            100% {
                opacity: 1;
            }
            50% {
                opacity: 0.5;
            }
        }

        .hero h1 {
            font-size: clamp(2rem, 4vw, 3rem);
            font-weight: 900;
            color: var(--primary-dark);
            line-height: 1.25;
            letter-spacing: -0.8px;
            margin-bottom: 1rem;
        }

        .hero h1 .highlight {
            color: var(--primary);
            position: relative;
            display: inline-block;
        }

        .hero h1 .highlight::after {
            content: '';
            position: absolute;
            bottom: 2px;
            left: 0;
            right: 0;
            height: 8px;
            background: rgba(26, 111, 160, 0.13);
            border-radius: 4px;
            z-index: -1;
        }

        .hero-desc {
            font-size: 1.1rem;
            color: var(--text-secondary);
            line-height: 1.8;
            margin-bottom: 1.8rem;
            max-width: 560px;
            letter-spacing: -0.3px;
        }

        .hero-stats {
            display: flex;
            gap: 2rem;
            flex-wrap: wrap;
        }

        .hero-stat {
            text-align: center;
            background: var(--bg-card);
            border-radius: var(--radius);
            padding: 1rem 1.5rem;
            box-shadow: var(--shadow-sm);
            border: 1px solid var(--border-light);
            min-width: 90px;
        }

        .hero-stat .stat-num {
            font-size: 1.8rem;
            font-weight: 900;
            color: var(--primary);
            letter-spacing: -0.5px;
            line-height: 1;
        }

        .hero-stat .stat-label {
            font-size: 0.78rem;
            color: var(--text-light);
            margin-top: 0.3rem;
            letter-spacing: -0.2px;
        }

        .hero-visual {
            flex-shrink: 0;
            width: 280px;
            height: 280px;
            border-radius: 50%;
            background: linear-gradient(145deg, #eef5fa, #dce9f3);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 5rem;
            color: var(--primary);
            box-shadow: var(--shadow-lg), inset 0 0 0 4px rgba(255, 255, 255, 0.6);
            position: relative;
        }

        .hero-visual::after {
            content: '';
            position: absolute;
            inset: -12px;
            border-radius: 50%;
            border: 2px dashed rgba(13, 79, 124, 0.15);
            pointer-events: none;
            animation: rotate-dash 30s linear infinite;
        }

        @keyframes rotate-dash {
            from {
                transform: rotate(0deg);
            }
            to {
                transform: rotate(360deg);
            }
        }

        /* ============ MAIN CONTENT ============ */
        .main-content {
            max-width: 1280px;
            margin: 0 auto;
            padding: 3rem 2rem 5rem;
        }

        .section {
            margin-bottom: 3rem;
            background: var(--bg-card);
            border-radius: var(--radius-lg);
            padding: 2.5rem 2.8rem;
            box-shadow: var(--shadow);
            border: 1px solid var(--border-light);
            transition: var(--transition);
            position: relative;
        }

        .section:hover {
            box-shadow: var(--shadow-lg);
            border-color: #dce5ec;
        }

        .section-header {
            display: flex;
            align-items: center;
            gap: 1rem;
            margin-bottom: 1.8rem;
            padding-bottom: 1.2rem;
            border-bottom: 2px solid var(--border-light);
        }

        .section-icon {
            width: 52px;
            height: 52px;
            border-radius: var(--radius);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            flex-shrink: 0;
        }

        .section-icon.blue {
            background: linear-gradient(135deg, #e3f0f8, #d0e6f4);
            color: var(--primary);
        }
        .section-icon.green {
            background: linear-gradient(135deg, #e0f5f1, #c8ede4);
            color: var(--accent);
        }
        .section-icon.orange {
            background: linear-gradient(135deg, #fef4e8, #fde8d0);
            color: #c2781a;
        }
        .section-icon.purple {
            background: linear-gradient(135deg, #f3effb, #e4dcf6);
            color: #6b46c1;
        }

        .section-title {
            font-size: 1.5rem;
            font-weight: 800;
            color: var(--primary-dark);
            letter-spacing: -0.5px;
        }

        .section-subtitle {
            font-size: 0.9rem;
            color: var(--text-light);
            margin-top: 0.2rem;
            letter-spacing: -0.2px;
        }

        .section-body h3 {
            font-size: 1.15rem;
            font-weight: 700;
            color: var(--text);
            margin: 1.6rem 0 0.7rem;
            letter-spacing: -0.3px;
        }

        .section-body h3:first-child {
            margin-top: 0;
        }

        .section-body p {
            color: var(--text-secondary);
            margin-bottom: 0.9rem;
            letter-spacing: -0.2px;
            line-height: 1.85;
        }

        .section-body ul,
        .section-body ol {
            margin: 0.8rem 0 1.2rem 1.3rem;
            color: var(--text-secondary);
            line-height: 1.9;
        }

        .section-body li {
            margin-bottom: 0.4rem;
            letter-spacing: -0.2px;
            padding-left: 0.3rem;
        }

        .section-body li strong {
            color: var(--text);
        }

        /* Card Grid */
        .card-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
            gap: 1.2rem;
            margin: 1.5rem 0;
        }

        .info-card {
            background: #fafcfd;
            border: 1px solid var(--border-light);
            border-radius: var(--radius);
            padding: 1.4rem 1.5rem;
            transition: var(--transition);
            position: relative;
            overflow: hidden;
        }

        .info-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 4px;
            height: 100%;
            border-radius: 4px 0 0 4px;
        }

        .info-card.card-blue::before {
            background: var(--primary);
        }
        .info-card.card-green::before {
            background: var(--accent);
        }
        .info-card.card-orange::before {
            background: #d69e2e;
        }
        .info-card.card-red::before {
            background: var(--danger);
        }

        .info-card:hover {
            transform: translateY(-3px);
            box-shadow: var(--shadow);
            border-color: #d0dce6;
        }

        .info-card .card-icon {
            font-size: 1.8rem;
            margin-bottom: 0.6rem;
        }

        .info-card h4 {
            font-size: 1rem;
            font-weight: 700;
            color: var(--text);
            margin-bottom: 0.4rem;
            letter-spacing: -0.3px;
        }

        .info-card p {
            font-size: 0.88rem;
            color: var(--text-light);
            margin: 0;
            letter-spacing: -0.2px;
            line-height: 1.6;
        }

        /* Highlight Box */
        .highlight-box {
            background: linear-gradient(135deg, #fef9f0, #fdf4e5);
            border: 1px solid #f0d89c;
            border-radius: var(--radius);
            padding: 1.3rem 1.6rem;
            margin: 1.5rem 0;
            display: flex;
            align-items: flex-start;
            gap: 1rem;
        }

        .highlight-box.danger-box {
            background: linear-gradient(135deg, #fef5f4, #fdecea);
            border-color: #f5c6c0;
        }

        .highlight-box i {
            font-size: 1.5rem;
            flex-shrink: 0;
            margin-top: 0.15rem;
        }
        .highlight-box.warn i {
            color: #d69e2e;
        }
        .highlight-box.danger-box i {
            color: var(--danger);
        }

        .highlight-box p {
            margin: 0;
            font-weight: 500;
            color: #5c3d10;
            letter-spacing: -0.2px;
            line-height: 1.7;
        }
        .highlight-box.danger-box p {
            color: #6b1c16;
        }

        /* Table-like layout */
        .spec-table {
            width: 100%;
            border-collapse: collapse;
            margin: 1.2rem 0;
            font-size: 0.9rem;
            border-radius: var(--radius-sm);
            overflow: hidden;
            box-shadow: var(--shadow-sm);
        }

        .spec-table th,
        .spec-table td {
            padding: 0.85rem 1.1rem;
            text-align: left;
            border-bottom: 1px solid var(--border-light);
            letter-spacing: -0.2px;
        }

        .spec-table th {
            background: #f8fafb;
            font-weight: 700;
            color: var(--primary-dark);
            white-space: nowrap;
            width: 28%;
        }

        .spec-table td {
            color: var(--text-secondary);
            background: #fff;
        }

        .spec-table tr:last-child th,
        .spec-table tr:last-child td {
            border-bottom: none;
        }

        /* ============ FLOATING DOWNLOAD BUTTON ============ */
        .floating-download {
            position: fixed;
            bottom: 32px;
            right: 32px;
            z-index: 9999;
            display: flex;
            flex-direction: column;
            align-items: flex-end;
            gap: 10px;
        }

        .floating-download .download-tooltip {
            background: var(--primary-dark);
            color: #fff;
            padding: 0.5rem 1rem;
            border-radius: 20px;
            font-size: 0.82rem;
            font-weight: 600;
            letter-spacing: -0.2px;
            opacity: 0;
            transform: translateY(10px);
            pointer-events: none;
            transition: var(--transition);
            white-space: nowrap;
            box-shadow: var(--shadow-lg);
        }

        .floating-download:hover .download-tooltip {
            opacity: 1;
            transform: translateY(0);
        }

        .floating-download .download-btn-main {
            width: 62px;
            height: 62px;
            border-radius: 50%;
            background: linear-gradient(135deg, #d94436, #c0392b);
            color: #fff;
            border: none;
            cursor: pointer;
            font-size: 1.5rem;
            box-shadow: var(--shadow-xl);
            transition: var(--transition);
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            animation: float-gentle 3s ease-in-out infinite;
        }

        @keyframes float-gentle {
            0%,
            100% {
                transform: translateY(0);
            }
            50% {
                transform: translateY(-8px);
            }
        }

        .floating-download .download-btn-main:hover {
            transform: scale(1.08);
            box-shadow: 0 24px 56px rgba(217, 68, 54, 0.45);
            animation: none;
        }

        .floating-download .download-btn-main:active {
            transform: scale(0.94);
            transition: 0.1s;
        }

        .floating-download .download-btn-main .pulse-ring {
            position: absolute;
            inset: -6px;
            border-radius: 50%;
            border: 3px solid rgba(217, 68, 54, 0.35);
            animation: pulse-ring 2s ease-out infinite;
            pointer-events: none;
        }

        @keyframes pulse-ring {
            0% {
                transform: scale(1);
                opacity: 0.7;
            }
            100% {
                transform: scale(1.6);
                opacity: 0;
            }
        }

        /* Loading overlay */
        .loading-overlay {
            display: none;
            position: fixed;
            inset: 0;
            z-index: 99999;
            background: rgba(0, 0, 0, 0.55);
            backdrop-filter: blur(4px);
            -webkit-backdrop-filter: blur(4px);
            align-items: center;
            justify-content: center;
            flex-direction: column;
            gap: 1.2rem;
        }

        .loading-overlay.active {
            display: flex;
        }

        .loading-spinner {
            width: 52px;
            height: 52px;
            border-radius: 50%;
            border: 4px solid rgba(255, 255, 255, 0.3);
            border-top-color: #fff;
            animation: spin 0.8s linear infinite;
        }

        @keyframes spin {
            to {
                transform: rotate(360deg);
            }
        }

        .loading-text {
            color: #fff;
            font-weight: 600;
            font-size: 1rem;
            letter-spacing: -0.2px;
        }

        /* ============ FOOTER ============ */
        .footer {
            background: #1a2634;
            color: #a0b4c4;
            text-align: center;
            padding: 2rem;
            font-size: 0.85rem;
            letter-spacing: -0.2px;
            line-height: 1.8;
        }

        .footer strong {
            color: #d0dde6;
        }

        /* ============ RESPONSIVE ============ */
        @media (max-width: 1024px) {
            .hero-inner {
                flex-direction: column;
                text-align: center;
                gap: 2rem;
            }
            .hero-desc {
                max-width: 100%;
            }
            .hero-stats {
                justify-content: center;
            }
            .hero-visual {
                width: 180px;
                height: 180px;
                font-size: 3.5rem;
            }
            .section {
                padding: 1.8rem 1.5rem;
            }
            .nav {
                height: auto;
                padding: 0.8rem 0;
                flex-wrap: wrap;
                gap: 0.8rem;
            }
            .nav-links {
                gap: 0.15rem;
            }
            .nav-links a {
                font-size: 0.8rem;
                padding: 0.4rem 0.65rem;
            }
            .nav-download-btn {
                padding: 0.45rem 0.9rem;
                font-size: 0.8rem !important;
            }
            .floating-download {
                bottom: 20px;
                right: 20px;
            }
            .floating-download .download-btn-main {
                width: 50px;
                height: 50px;
                font-size: 1.2rem;
            }
            .card-grid {
                grid-template-columns: 1fr;
            }
        }

        @media (max-width: 640px) {
            .hero {
                padding: 2.5rem 1rem 2rem;
            }
            .hero h1 {
                font-size: 1.5rem;
            }
            .hero-desc {
                font-size: 0.9rem;
            }
            .hero-stats {
                gap: 0.8rem;
            }
            .hero-stat {
                padding: 0.7rem 1rem;
            }
            .hero-stat .stat-num {
                font-size: 1.3rem;
            }
            .hero-visual {
                width: 120px;
                height: 120px;
                font-size: 2.5rem;
            }
            .main-content {
                padding: 1.5rem 0.8rem 3rem;
            }
            .section {
                padding: 1.3rem 1rem;
                border-radius: var(--radius);
                margin-bottom: 1.5rem;
            }
            .section-title {
                font-size: 1.2rem;
            }
            .section-header {
                gap: 0.6rem;
                margin-bottom: 1rem;
            }
            .section-icon {
                width: 38px;
                height: 38px;
                font-size: 1.1rem;
                border-radius: 8px;
            }
            .spec-table th,
            .spec-table td {
                padding: 0.6rem 0.7rem;
                font-size: 0.78rem;
            }
            .nav-logo {
                font-size: 1rem;
            }
            .nav-logo .logo-icon {
                width: 32px;
                height: 32px;
                font-size: 1rem;
            }
            .nav-download-btn {
                padding: 0.4rem 0.7rem;
                font-size: 0.75rem !important;
                gap: 4px;
            }
            .floating-download {
                bottom: 14px;
                right: 14px;
            }
            .floating-download .download-btn-main {
                width: 44px;
                height: 44px;
                font-size: 1.1rem;
            }
            .floating-download .download-tooltip {
                font-size: 0.7rem;
                padding: 0.4rem 0.8rem;
            }
        }

        /* Print / PDF specific: hide floating elements */
        @media print {
            .floating-download,
            .loading-overlay,
            .nav-download-btn,
            .header {
                display: none !important;
            }
            body {
                background: #fff;
            }
            .section {
                box-shadow: none;
                border: 1px solid #ddd;
                break-inside: avoid;
                page-break-inside: avoid;
            }
            .hero {
                background: #fff;
                padding: 1rem 0;
            }
            .hero::before,
            .hero::after,
            .hero-visual::after {
                display: none;
            }
        }
    </style>
</head>
<body>

    <!-- ==================== HEADER ==================== -->
    <header class="header" id="header">
        <nav class="nav">
            <a href="#" class="nav-logo">
                <span class="logo-icon"><i class="fa-solid fa-shield-halved"></i></span>
                <span>DHIS 보안센터</span>
            </a>
            <ul class="nav-links">
                <li><a href="#design" class="active">설계·개발</a></li>
                <li><a href="#features">주요 기능</a></li>
                <li><a href="#effects">기대 효과</a></li>
                <li><a href="#notes">기타 사항</a></li>
            </ul>
            <button class="nav-download-btn" onclick="triggerPDFDownload()" title="PDF 다운로드">
                <i class="fa-solid fa-file-pdf"></i> PDF 다운로드
            </button>
        </nav>
    </header>

    <!-- ==================== HERO ==================== -->
    <section class="hero">
        <div class="hero-inner">
            <div class="hero-text">
                <span class="hero-badge"><i class="fa-solid fa-triangle-exclamation"></i> 산업 보안 핵심 이슈</span>
                <h1>디지털 헬스케어<br><span class="highlight">산업 보안</span> 플랫폼</h1>
                <p class="hero-desc">
                    의료 데이터 보호, 환자 개인정보 안전, 의료기기 사이버 보안까지—<br>
                    디지털 헬스케어 산업의 지속 가능한 성장을 위한 <strong>통합 보안 관리 체계</strong>를 제시합니다.
                </p>
                <div class="hero-stats">
                    <div class="hero-stat">
                        <div class="stat-num">98.7<span style="font-size:1rem;">%</span></div>
                        <div class="stat-label">데이터 보호율</div>
                    </div>
                    <div class="hero-stat">
                        <div class="stat-num">24/7</div>
                        <div class="stat-label">실시간 모니터링</div>
                    </div>
                    <div class="hero-stat">
                        <div class="stat-num">ISO</div>
                        <div class="stat-label">27001 인증 기준</div>
                    </div>
                </div>
            </div>
            <div class="hero-visual">
                <span>🛡️</span>
            </div>
        </div>
    </section>

    <!-- ==================== MAIN CONTENT (PDF 대상 영역) ==================== -->
    <main class="main-content" id="pdf-content">

        <!-- Section 1: 웹사이트 디자인 및 개발 방법 -->
        <section class="section" id="design">
            <div class="section-header">
                <div class="section-icon blue">
                    <i class="fa-solid fa-code"></i>
                </div>
                <div>
                    <h2 class="section-title">1. 웹사이트 디자인 및 개발 방법</h2>
                    <p class="section-subtitle">Website Design & Development Methodology</p>
                </div>
            </div>
            <div class="section-body">
                <h3>🔐 보안 우선 설계 철학 (Security-First Design)</h3>
                <p>
                    본 웹사이트는 <strong>디지털 헬스케어 산업 보안</strong>이라는 핵심 주제에 부합하도록
                    설계 초기 단계부터 <strong>보안 중심 아키텍처</strong>를 채택하였습니다.
                    OWASP Top 10 취약점 가이드라인을 준수하고, 의료 정보 보호에 특화된
                    HIPAA 및 국내 의료법 개인정보보호 기준을 반영하여 개발되었습니다.
                </p>

                <div class="card-grid">
                    <div class="info-card card-blue">
                        <div class="card-icon">📐</div>
                        <h4>반응형 웹 디자인 (RWD)</h4>
                        <p>모바일·태블릿·데스크톱 환경에 최적화된 유동형 그리드 시스템을 적용하여 모든 기기에서 일관된 사용자 경험을 제공합니다.</p>
                    </div>
                    <div class="info-card card-green">
                        <div class="card-icon">🔒</div>
                        <h4>HTTPS & TLS 1.3 암호화</h4>
                        <p>전송 구간 암호화를 기본으로 적용하며, 의료 민감 데이터의 안전한 통신을 위해 최신 TLS 프로토콜을 사용합니다.</p>
                    </div>
                    <div class="info-card card-blue">
                        <div class="card-icon">🧩</div>
                        <h4>모듈형 프론트엔드 구조</h4>
                        <p>컴포넌트 기반의 모듈형 아키텍처로, 유지보수성과 확장성을 극대화하고 보안 패치를 신속하게 적용할 수 있습니다.</p>
                    </div>
                    <div class="info-card card-green">
                        <div class="card-icon">🗄️</div>
                        <h4>안전한 데이터베이스 설계</h4>
                        <p>환자 식별 정보(PII)의 암호화 저장, 접근 제어(Access Control), 감사 로그(Audit Trail)를 기본으로 구현합니다.</p>
                    </div>
                </div>

                <h3>🛠️ 기술 스택 (Technology Stack)</h3>
                <table class="spec-table">
                    <tbody>
                        <tr><th>프론트엔드</th><td>HTML5 / CSS3 / Vanilla JavaScript (ES6+) — 경량화 및 빠른 로딩 속도 확보</td></tr>
                        <tr><th>보안 통신</th><td>HTTPS (TLS 1.3), HSTS 헤더 적용, CSP(Content Security Policy) 설정</td></tr>
                        <tr><th>데이터 암호화</th><td>AES-256-GCM 대칭키 암호화, bcrypt 해싱 알고리즘</td></tr>
                        <tr><th>인증 체계</th><td>OAuth 2.0 / OpenID Connect 기반 다중 인증(MFA) 지원</td></tr>
                        <tr><th>모니터링</th><td>실시간 SIEM 연동, 이상 탐지(Anomaly Detection) 로그 분석</td></tr>
                        <tr><th>컴플라이언스</th><td>ISO 27001, HIPAA, GDPR, 국내 개인정보보호법 기준 준수</td></tr>
                    </tbody>
                </table>

                <h3>📋 개발 프로세스</h3>
                <p>
                    애자일(Agile) 방법론을 기반으로 <strong>2주 스프린트</strong> 단위의 반복적 개발을 수행하였으며,
                    각 스프린트 종료 시 <strong>보안 코드 리뷰</strong>와 <strong>취약점 스캔</strong>을 의무적으로 실시합니다.
                    CI/CD 파이프라인에는 자동화된 SAST(Static Application Security Testing) 도구를 통합하여
                    배포 전 보안 검증을 완료합니다.
                </p>
            </div>
        </section>

        <!-- Section 2: 웹사이트 주요 기능 소개 -->
        <section class="section" id="features">
            <div class="section-header">
                <div class="section-icon green">
                    <i class="fa-solid fa-list-check"></i>
                </div>
                <div>
                    <h2 class="section-title">2. 웹사이트 주요 기능 소개</h2>
                    <p class="section-subtitle">Key Features & Capabilities</p>
                </div>
            </div>
            <div class="section-body">
                <h3>📊 실시간 보안 대시보드</h3>
                <p>
                    의료 기관 내 전체 IT 자산의 <strong>보안 상태를 한눈에 파악</strong>할 수 있는
                    직관적인 대시보드를 제공합니다. 침입 탐지 건수, 이상 접근 로그, 데이터 유출 위험 지수 등을
                    실시간 그래프와 차트로 시각화합니다.
                </p>

                <div class="card-grid">
                    <div class="info-card card-red">
                        <div class="card-icon">🚨</div>
                        <h4>위협 탐지 및 알림</h4>
                        <p>AI 기반 이상 행위 탐지 엔진이 비정상 접근 패턴을 식별하고, SMS·이메일·앱 푸시로 즉시 경고를 발송합니다.</p>
                    </div>
                    <div class="info-card card-orange">
                        <div class="card-icon">📋</div>
                        <h4>보안 정책·법규 데이터베이스</h4>
                        <p>국내외 의료 보안 법규, 가이드라인, 컴플라이언스 체크리스트를 통합 검색할 수 있는 지식 베이스입니다.</p>
                    </div>
                    <div class="info-card card-blue">
                        <div class="card-icon">🎓</div>
                        <h4>보안 교육·훈련 포털</h4>
                        <p>의료진과 IT 관리자를 위한 온라인 보안 교육 콘텐츠, 모의 훈련 시나리오, 인증 평가 시스템을 제공합니다.</p>
                    </div>
                    <div class="info-card card-green">
                        <div class="card-icon">🔍</div>
                        <h4>취약점 진단·리포트</h4>
                        <p>정기적인 자동 취약점 스캔 결과를 리포트로 생성하고, 조치 가이드를 단계별로 제시합니다.</p>
                    </div>
                </div>

                <h3>📁 의료 데이터 안전 관리</h3>
                <ul>
                    <li><strong>환자 개인정보 비식별화</strong> — 데이터 활용 시 자동 비식별 처리 파이프라인 작동</li>
                    <li><strong>접근 권한 세분화</strong> — 역할 기반 접근 제어(RBAC)로 최소 권한 원칙 적용</li>
                    <li><strong>감사 추적 로그</strong> — 모든 데이터 접근·수정·삭제 이력을 블록체인 기반으로 기록</li>
                    <li><strong>백업 및 복구</strong> — 랜섬웨어 대비 격리된 오프라인 백업 시스템 자동 운영</li>
                </ul>

                <div class="highlight-box warn">
                    <i class="fa-solid fa-circle-info"></i>
                    <p><strong>핵심 차별점:</strong> 본 플랫폼은 단순 정보 제공을 넘어, 실제 의료 현장에서 발생할 수 있는 보안 사고 시나리오에 대한 <strong>시뮬레이션 훈련 모듈</strong>을 내장하고 있어 실전 대응 역량을 강화할 수 있습니다.</p>
                </div>
            </div>
        </section>

        <!-- Section 3: 기대 효과 및 활용 가치 -->
        <section class="section" id="effects">
            <div class="section-header">
                <div class="section-icon orange">
                    <i class="fa-solid fa-chart-line"></i>
                </div>
                <div>
                    <h2 class="section-title">3. 기대 효과 및 활용 가치</h2>
                    <p class="section-subtitle">Expected Outcomes & Application Value</p>
                </div>
            </div>
            <div class="section-body">
                <h3>🏥 의료 기관 대상 기대 효과</h3>
                <div class="card-grid">
                    <div class="info-card card-blue">
                        <div class="card-icon">⬇️</div>
                        <h4>보안 사고 발생률 감소</h4>
                        <p>실시간 모니터링과 조기 경보 체계를 통해 보안 침해 사고를 <strong>최대 75% 이상 예방</strong>할 수 있습니다.</p>
                    </div>
                    <div class="info-card card-green">
                        <div class="card-icon">💰</div>
                        <h4>운영 비용 절감</h4>
                        <p>자동화된 보안 관리로 인력 의존도를 낮추고, 사고 대응 비용을 <strong>연간 약 40% 절감</strong>합니다.</p>
                    </div>
                    <div class="info-card card-orange">
                        <div class="card-icon">✅</div>
                        <h4>규제 컴플라이언스 달성</h4>
                        <p>ISO 27001, HIPAA 등 국제 표준과 국내 의료법 요구사항을 <strong>체계적으로 충족</strong>할 수 있습니다.</p>
                    </div>
                    <div class="info-card card-red">
                        <div class="card-icon">🤝</div>
                        <h4>환자 신뢰도 향상</h4>
                        <p>강화된 보안 체계는 환자에게 <strong>신뢰할 수 있는 의료 환경</strong>을 제공하여 기관 평판을 높입니다.</p>
                    </div>
                </div>

                <h3>🌐 산업적 활용 가치</h3>
                <ul>
                    <li><strong>의료기기 제조사</strong> — 제품 출시 전 보안 인증 가이드 및 테스트베드 활용</li>
                    <li><strong>보안 솔루션 기업</strong> — 헬스케어 특화 보안 제품의 레퍼런스 플랫폼으로 활용</li>
                    <li><strong>정부·규제 기관</strong> — 의료 보안 정책 수립을 위한 데이터 기반 인사이트 제공</li>
                    <li><strong>학계·연구소</strong> — 의료 보안 연구를 위한 오픈 데이터 및 협업 환경 지원</li>
                </ul>

                <div class="highlight-box danger-box">
                    <i class="fa-solid fa-shield-virus"></i>
                    <p><strong>긴급 대응 가치:</strong> 랜섬웨어 공격이 의료 기관을 대상으로 급증하는 현 상황에서, 본 플랫폼은 <strong>골든타임 내 초기 대응</strong>을 가능하게 하는 핵심 인프라로 기능합니다. 2025년 기준 의료 분야 랜섬웨어 피해액은 전년 대비 300% 증가했습니다.</p>
                </div>
            </div>
        </section>

        <!-- Section 4: 기타 관련 사항 -->
        <section class="section" id="notes">
            <div class="section-header">
                <div class="section-icon purple">
                    <i class="fa-solid fa-note-sticky"></i>
                </div>
                <div>
                    <h2 class="section-title">4. 기타 관련 사항</h2>
                    <p class="section-subtitle">Additional Information & Notes</p>
                </div>
            </div>
            <div class="section-body">
                <h3>📅 유지보수 및 업데이트 계획</h3>
                <p>
                    본 웹사이트는 <strong>월 1회 정기 보안 패치</strong>와 <strong>분기별 기능 업데이트</strong>를 원칙으로 운영됩니다.
                    중대한 보안 취약점(CVE Critical 등급) 발견 시 24시간 이내 긴급 핫픽스를 배포합니다.
                    또한 연 1회 외부 보안 감사 기관의 <strong>침투 테스트(Penetration Test)</strong>를 의무적으로 실시하여
                    시스템의 견고성을 지속적으로 검증합니다.
                </p>

                <h3>📞 기술 지원 및 문의</h3>
                <table class="spec-table">
                    <tbody>
                        <tr><th>기술 지원 이메일</th><td>security-support@dhis-platform.kr</td></tr>
                        <tr><th>긴급 보안 핫라인</th><td>080-1234-5678 (연중무휴 24시간)</td></tr>
                        <tr><th>보안 취약점 제보</th><td>bug-bounty@dhis-platform.kr (책임 있는 공개 정책 운영)</td></tr>
                        <tr><th>공식 문서 저장소</th><td>https://docs.dhis-platform.kr/security</td></tr>
                    </tbody>
                </table>

                <h3>⚖️ 법적 고지 사항</h3>
                <ul>
                    <li>본 웹사이트에서 제공하는 모든 보안 정보는 <strong>참고 및 교육 목적</strong>으로 제공되며, 법률 자문을 대체하지 않습니다.</li>
                    <li>의료 데이터의 실제 처리 및 보관에 관한 사항은 반드시 <strong>관할 규제 기관의 승인</strong>을 받아야 합니다.</li>
                    <li>본 플랫폼은 <strong>대한민국 개인정보보호법</strong>, <strong>의료법</strong>, <strong>정보통신망법</strong>을 준수합니다.</li>
                    <li>PDF 문서의 내용은 2026년 6월 기준으로 작성되었으며, 추후 업데이트될 수 있습니다.</li>
                </ul>

                <div class="highlight-box warn">
                    <i class="fa-solid fa-circle-check"></i>
                    <p><strong>라이선스:</strong> 본 웹사이트의 소스 코드는 MIT 라이선스로 제공되며, 보안 모듈 일부는 별도 라이선스가 적용될 수 있습니다. 상업적 활용 시 사전 문의를 권장합니다.</p>
                </div>
            </div>
        </section>

    </main>

    <!-- ==================== FOOTER ==================== -->
    <footer class="footer">
        <p>© 2026 <strong>DHIS 보안센터 (Digital Healthcare Industry Security Center)</strong>. All Rights Reserved.</p>
        <p>본 사이트는 디지털 헬스케어 산업 보안 인식 제고를 위한 교육·정보 제공 플랫폼입니다.</p>
        <p style="margin-top:0.4rem;font-size:0.78rem;color:#6b8299;">ISO 27001 인증 준비 중 | 개인정보보호법 완전 준수 | 최종 업데이트: 2026년 6월</p>
    </footer>

    <!-- ==================== FLOATING DOWNLOAD BUTTON ==================== -->
    <div class="floating-download" id="floating-download">
        <span class="download-tooltip">📥 한글 PDF 저장하기</span>
        <button class="download-btn-main" onclick="triggerPDFDownload()" title="PDF 다운로드" aria-label="PDF 다운로드">
            <span class="pulse-ring"></span>
            <i class="fa-solid fa-download"></i>
        </button>
    </div>

    <!-- ==================== LOADING OVERLAY ==================== -->
    <div class="loading-overlay" id="loading-overlay">
        <div class="loading-spinner"></div>
        <span class="loading-text">PDF 생성 중입니다... 잠시만 기다려 주세요</span>
    </div>

    <!-- ==================== SCRIPTS ==================== -->
    <script>
        (function() {
            // ========== Header scroll effect ==========
            const header = document.getElementById('header');
            let lastScrollY = 0;

            function updateHeader() {
                const scrollY = window.scrollY;
                if (scrollY > 40) {
                    header.classList.add('scrolled');
                } else {
                    header.classList.remove('scrolled');
                }
                lastScrollY = scrollY;
            }

            window.addEventListener('scroll', updateHeader, { passive: true });
            // 초기 상태 확인
            updateHeader();

            // ========== Smooth scroll for nav links ==========
            document.querySelectorAll('.nav-links a[href^="#"]').forEach(link => {
                link.addEventListener('click', function(e) {
                    e.preventDefault();
                    const targetId = this.getAttribute('href').substring(1);
                    const target = document.getElementById(targetId);
                    if (target) {
                        const headerHeight = header.offsetHeight;
                        const targetPosition = target.getBoundingClientRect().top + window
                            .pageYOffset - headerHeight - 16;
                        window.scrollTo({
                            top: targetPosition,
                            behavior: 'smooth'
                        });
                    }
                });
            });

            // ========== Active nav link update on scroll ==========
            const navLinks = document.querySelectorAll('.nav-links a');
            const sections = [];
            navLinks.forEach(link => {
                const href = link.getAttribute('href');
                if (href && href.startsWith('#')) {
                    const target = document.getElementById(href.substring(1));
                    if (target) sections.push({ link, target });
                }
            });

            function updateActiveLink() {
                const scrollPos = window.scrollY + header.offsetHeight + 80;
                let activeLink = null;
                sections.forEach(({ link, target }) => {
                    if (target.offsetTop <= scrollPos) {
                        activeLink = link;
                    }
                });
                navLinks.forEach(l => l.classList.remove('active'));
                if (activeLink) activeLink.classList.add('active');
            }

            window.addEventListener('scroll', updateActiveLink, { passive: true });
            updateActiveLink();

            // ========== PDF Download Function ==========
            window.triggerPDFDownload = function() {
                const overlay = document.getElementById('loading-overlay');
                const floatingBtn = document.getElementById('floating-download');
                const pdfContent = document.getElementById('pdf-content');

                // Show loading overlay
                overlay.classList.add('active');

                // Hide floating button during PDF generation
                if (floatingBtn) {
                    floatingBtn.style.display = 'none';
                }

                // Clone the content for PDF to avoid modifying visible DOM
                const clone = pdfContent.cloneNode(true);

                // Create a temporary wrapper with proper styling for PDF
                const tempWrapper = document.createElement('div');
                tempWrapper.style.cssText = `
                    position: absolute;
                    left: -9999px;
                    top: 0;
                    width: 800px;
                    background: #ffffff;
                    font-family: 'Noto Sans KR', sans-serif;
                    color: #1a202c;
                    line-height: 1.7;
                    padding: 20px;
                `;

                // Add title header for PDF
                const pdfTitle = document.createElement('div');
                pdfTitle.style.cssText = `
                    text-align: center;
                    padding: 20px 0 30px;
                    border-bottom: 3px solid #0d4f7c;
                    margin-bottom: 30px;
                `;
                pdfTitle.innerHTML = `
                    <h1 style="font-size:1.8rem;font-weight:900;color:#0a3a5c;margin:0 0 8px;letter-spacing:-0.5px;">
                        디지털 헬스케어 산업 보안
                    </h1>
                    <p style="font-size:1rem;color:#4a5568;margin:0;">
                        Digital Healthcare Industry Security Platform
                    </p>
                    <p style="font-size:0.82rem;color:#718096;margin:6px 0 0;">
                        문서 생성일: 2026년 6월 4일 | 버전 1.0
                    </p>
                `;
                tempWrapper.appendChild(pdfTitle);

                // Append cloned content
                tempWrapper.appendChild(clone);

                // Append footer for PDF
                const pdfFooter = document.createElement('div');
                pdfFooter.style.cssText = `
                    text-align: center;
                    margin-top: 30px;
                    padding-top: 20px;
                    border-top: 2px solid #e2e8f0;
                    font-size: 0.8rem;
                    color: #718096;
                `;
                pdfFooter.innerHTML =
                    '<p>© 2026 DHIS 보안센터 | 본 문서는 디지털 헬스케어 산업 보안 플랫폼의 개요 문서입니다.</p>';
                tempWrapper.appendChild(pdfFooter);

                document.body.appendChild(tempWrapper);

                // html2pdf configuration
                const opt = {
                    margin: [8, 10, 8, 10],
                    filename: '디지털_헬스케어_산업_보안_플랫폼.pdf',
                    image: { type: 'jpeg', quality: 0.98 },
                    html2canvas: {
                        scale: 2,
                        useCORS: true,
                        letterRendering: true,
                        logging: false,
                        width: tempWrapper.offsetWidth,
                        windowWidth: tempWrapper.offsetWidth,
                    },
                    jsPDF: {
                        unit: 'mm',
                        format: 'a4',
                        orientation: 'portrait',
                    },
                    pagebreak: { mode: ['avoid-all', 'css', 'legacy'] },
                };

                // Generate PDF
                html2pdf()
                    .set(opt)
                    .from(tempWrapper)
                    .save()
                    .then(function() {
                        // Clean up
                        document.body.removeChild(tempWrapper);
                        overlay.classList.remove('active');
                        if (floatingBtn) {
                            floatingBtn.style.display = '';
                        }
                        console.log('✅ PDF 다운로드가 완료되었습니다.');
                    })
                    .catch(function(err) {
                        console.error('PDF 생성 중 오류 발생:', err);
                        // Fallback: try browser print
                        document.body.removeChild(tempWrapper);
                        overlay.classList.remove('active');
                        if (floatingBtn) {
                            floatingBtn.style.display = '';
                        }
                        alert(
                            'PDF 자동 생성에 실패했습니다. 브라우저 인쇄 기능(Ctrl+P)을 사용하여 "PDF로 저장"을 선택해 주세요.');
                    });
            };

            // ========== Keyboard shortcut: Ctrl+Shift+P for PDF ==========
            document.addEventListener('keydown', function(e) {
                if (e.ctrlKey && e.shiftKey && e.key === 'P') {
                    e.preventDefault();
                    triggerPDFDownload();
                }
            });

            console.log('🛡️ DHIS 보안센터 — 디지털 헬스케어 산업 보안 플랫폼');
            console.log('📥 PDF 다운로드: 우측 하단 버튼 클릭 또는 Ctrl+Shift+P');
            console.log('🌐 지원 언어: 한국어 (Korean)');
            console.log('✅ 페이지 로딩 완료');
        })();
    </script>
</body>
</html>
