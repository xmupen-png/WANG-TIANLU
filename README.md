[<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>물리치료A WANG TIANLU 202217132 - 数字健康医疗·产业安全</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js">
    </script>
    <style>
        :root {
            --bg: #f4f7fc;
            --card-bg: #ffffff;
            --primary: #0066cc;
            --primary-dark: #004b99;
            --accent: #00a8cc;
            --danger: #d63031;
            --success: #00b894;
            --warning: #fdcb6e;
            --text: #2d3436;
            --text-light: #636e72;
            --border: #dfe6e9;
            --shadow: 0 8px 30px rgba(0, 0, 0, 0.08);
            --shadow-lg: 0 16px 40px rgba(0, 0, 0, 0.12);
            --radius: 16px;
            --radius-sm: 10px;
            --font: 'Segoe UI', 'PingFang SC', 'Microsoft YaHei', 'Noto Sans KR', sans-serif;
            --transition: 0.2s ease;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: var(--font);
            background: linear-gradient(135deg, #eef2f7 0%, #f8faff 100%);
            color: var(--text);
            line-height: 1.6;
            min-height: 100vh;
            -webkit-font-smoothing: antialiased;
        }

        /* 顶部导航 */
        .top-bar {
            background: linear-gradient(105deg, #0b1a2f 0%, #132b44 100%);
            color: #fff;
            padding: 12px 28px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 15px;
            position: sticky;
            top: 0;
            z-index: 1000;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.25);
            border-bottom: 1px solid rgba(255, 255, 255, 0.12);
        }
        .brand {
            display: flex;
            align-items: center;
            gap: 12px;
        }
        .brand-icon {
            width: 42px;
            height: 42px;
            border-radius: 50%;
            background: linear-gradient(135deg, #00a8cc, #0066cc);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.3rem;
            box-shadow: 0 0 18px rgba(0, 168, 204, 0.5);
            animation: soft-pulse 3s infinite;
        }
        @keyframes soft-pulse {
            0%,
            100% {
                box-shadow: 0 0 12px rgba(0, 168, 204, 0.4);
            }
            50% {
                box-shadow: 0 0 28px rgba(0, 168, 204, 0.8);
            }
        }
        .brand-text .main-title {
            font-weight: 700;
            font-size: 1rem;
            letter-spacing: 0.5px;
            line-height: 1.3;
        }
        .brand-text .sub-info {
            font-size: 0.7rem;
            opacity: 0.8;
            letter-spacing: 0.4px;
        }
        .top-actions {
            display: flex;
            align-items: center;
            gap: 12px;
        }
        .lang-switch {
            display: flex;
            border-radius: 30px;
            overflow: hidden;
            background: rgba(255, 255, 255, 0.12);
            border: 1px solid rgba(255, 255, 255, 0.25);
        }
        .lang-switch button {
            padding: 8px 18px;
            border: none;
            background: transparent;
            color: #ddd;
            font-weight: 600;
            font-size: 0.8rem;
            cursor: pointer;
            transition: var(--transition);
            font-family: var(--font);
            letter-spacing: 0.5px;
        }
        .lang-switch button.active {
            background: #fff;
            color: #0b1a2f;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.15);
        }
        .lang-switch button:hover:not(.active) {
            color: #fff;
            background: rgba(255, 255, 255, 0.15);
        }
        .btn-download {
            padding: 10px 22px;
            border: none;
            border-radius: 30px;
            background: linear-gradient(135deg, #d63031, #b71c1c);
            color: #fff;
            font-weight: 700;
            font-size: 0.85rem;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 6px;
            letter-spacing: 0.5px;
            transition: var(--transition);
            box-shadow: 0 4px 15px rgba(214, 48, 49, 0.35);
            font-family: var(--font);
        }
        .btn-download:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(214, 48, 49, 0.5);
        }
        .btn-download svg {
            width: 18px;
            height: 18px;
        }

        /* 浮动下载按钮 */
        .float-download {
            position: fixed;
            bottom: 24px;
            right: 24px;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: #d63031;
            border: none;
            cursor: pointer;
            box-shadow: 0 8px 24px rgba(214, 48, 49, 0.45);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 999;
            transition: transform 0.2s ease;
            color: #fff;
        }
        .float-download:hover {
            transform: scale(1.08);
        }
        .float-download svg {
            width: 24px;
            height: 24px;
        }

        /* PDF生成时隐藏按钮 */
        .hide-in-pdf {
            /* 用于在PDF捕获前隐藏的类 */
        }

        /* 主容器 */
        .main-container {
            max-width: 1280px;
            margin: 0 auto;
            padding: 30px 20px 40px;
        }

        .page-header {
            text-align: center;
            margin-bottom: 35px;
        }
        .page-header h1 {
            font-size: 2rem;
            font-weight: 800;
            background: linear-gradient(135deg, #0b1a2f, #0066cc);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 6px;
        }
        .page-header .subtitle {
            color: #636e72;
            font-weight: 500;
            letter-spacing: 0.5px;
        }

        .card {
            background: var(--card-bg);
            border-radius: var(--radius);
            padding: 28px;
            box-shadow: var(--shadow);
            border: 1px solid var(--border);
            margin-bottom: 24px;
            transition: var(--transition);
        }
        .card:hover {
            box-shadow: var(--shadow-lg);
        }
        .card-header {
            font-weight: 700;
            font-size: 1.1rem;
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            gap: 10px;
            color: #0b1a2f;
        }
        .card-header .dot {
            width: 10px;
            height: 10px;
            border-radius: 50%;
            background: var(--accent);
        }

        .two-col {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 24px;
        }
        @media (max-width: 850px) {
            .two-col {
                grid-template-columns: 1fr;
            }
            .top-bar {
                padding: 10px 16px;
            }
            .page-header h1 {
                font-size: 1.5rem;
            }
        }

        .form-group {
            margin-bottom: 18px;
        }
        .form-group label {
            display: block;
            font-weight: 600;
            font-size: 0.85rem;
            margin-bottom: 6px;
            color: #2d3436;
        }
        .form-group input,
        .form-group select,
        .form-group textarea {
            width: 100%;
            padding: 12px 15px;
            border: 2px solid #dfe6e9;
            border-radius: var(--radius-sm);
            font-size: 0.9rem;
            font-family: var(--font);
            transition: 0.2s;
            background: #fafbfc;
        }
        .form-group input:focus,
        .form-group select:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 4px rgba(0, 102, 204, 0.08);
            background: #fff;
        }
        .form-row {
            display: flex;
            gap: 16px;
            flex-wrap: wrap;
        }
        .form-row .form-group {
            flex: 1;
            min-width: 140px;
        }
        .btn-submit {
            width: 100%;
            padding: 14px;
            border: none;
            border-radius: 30px;
            font-weight: 700;
            font-size: 1rem;
            cursor: pointer;
            background: linear-gradient(135deg, #0066cc, #004b99);
            color: #fff;
            letter-spacing: 0.5px;
            box-shadow: 0 6px 20px rgba(0, 102, 204, 0.3);
            transition: var(--transition);
            font-family: var(--font);
        }
        .btn-submit:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 28px rgba(0, 102, 204, 0.45);
        }

        .result-area {
            min-height: 240px;
            border: 2px dashed #dfe6e9;
            border-radius: var(--radius-sm);
            padding: 20px;
            background: #fafcfd;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            color: #aaa;
            font-size: 0.9rem;
            transition: 0.2s;
        }
        .result-area.has-data {
            border-style: solid;
            border-color: #00b894;
            background: #f6fef9;
            color: #2d3436;
            text-align: left;
            display: block;
        }
        .result-item {
            padding: 8px 0;
            border-bottom: 1px solid #eef2f6;
            font-size: 0.9rem;
        }
        .badge-risk {
            display: inline-block;
            padding: 4px 14px;
            border-radius: 20px;
            font-weight: 700;
            font-size: 0.8rem;
        }
        .badge-low {
            background: #d4edda;
            color: #155724;
        }
        .badge-medium {
            background: #fff3cd;
            color: #856404;
        }
        .badge-high {
            background: #f8d7da;
            color: #721c24;
        }

        .info-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
            margin-top: 10px;
        }
        @media (max-width: 700px) {
            .info-grid {
                grid-template-columns: 1fr;
            }
        }
        .info-card {
            background: #fff;
            border-radius: var(--radius);
            padding: 22px;
            border-left: 5px solid var(--accent);
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.04);
            font-size: 0.85rem;
        }
        .info-card h3 {
            font-weight: 700;
            margin-bottom: 10px;
            color: #0b1a2f;
        }
        .footer-note {
            text-align: center;
            margin-top: 30px;
            color: #888;
            font-size: 0.75rem;
        }

        .toast {
            position: fixed;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            background: #2d3436;
            color: #fff;
            padding: 12px 28px;
            border-radius: 30px;
            font-weight: 600;
            font-size: 0.85rem;
            z-index: 2000;
            animation: toastIn 0.3s ease, toastOut 0.3s ease 2.2s forwards;
        }
        @keyframes toastIn {
            from {
                opacity: 0;
                transform: translateX(-50%) translateY(-20px);
            }
            to {
                opacity: 1;
                transform: translateX(-50%) translateY(0);
            }
        }
        @keyframes toastOut {
            to {
                opacity: 0;
                transform: translateX(-50%) translateY(-20px);
            }
        }

        .pain-slider-container {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        .pain-slider-container input {
            flex: 1;
        }
        .pain-value {
            font-weight: 700;
            font-size: 1.1rem;
            color: #d63031;
            min-width: 35px;
        }
    </style>
</head>
<body>
    <header class="top-bar">
        <div class="brand">
            <div class="brand-icon">🩺</div>
            <div class="brand-text">
                <div class="main-title">물리치료A WANG TIANLU 202217132</div>
                <div class="sub-info" data-i18n="brand_sub">数字健康医疗 · 产业安全平台</div>
            </div>
        </div>
        <div class="top-actions">
            <div class="lang-switch" id="langSwitch">
                <button data-lang="zh" class="active">🇨🇳 中文</button>
                <button data-lang="ko">🇰🇷 한국어</button>
            </div>
            <button class="btn-download hide-in-pdf" onclick="downloadPDF()">
                <svg viewBox="0 0 24 24" fill="currentColor"><path d="M19 9h-4V3H9v6H5l7 7 7-7zM5 18v2h14v-2H5z"/></svg>
                <span data-i18n="download_btn">下载PDF</span>
            </button>
        </div>
    </header>

    <div class="main-container" id="pdfCaptureArea">
        <div class="page-header">
            <h1>물리치료A WANG TIANLU 202217132</h1>
            <p class="subtitle" data-i18n="page_subtitle">数字健康医疗产业安全管理系统 / 디지털 헬스케어 산업안전 관리 시스템</p>
        </div>

        <div class="two-col">
            <div class="card">
                <div class="card-header"><span class="dot"></span> <span data-i18n="form_title">患者数据输入</span></div>
                <form id="patientForm" onsubmit="return handleSubmit(event)">
                    <div class="form-row">
                        <div class="form-group">
                            <label data-i18n="label_name">姓名</label>
                            <input type="text" id="patientName" placeholder="张三 / 홍길동" required>
                        </div>
                        <div class="form-group">
                            <label data-i18n="label_age">年龄</label>
                            <input type="number" id="patientAge" placeholder="18-99" min="1" max="120" required>
                        </div>
                    </div>
                    <div class="form-row">
                        <div class="form-group">
                            <label data-i18n="label_gender">性别</label>
                            <select id="patientGender" required></select>
                        </div>
                        <div class="form-group">
                            <label data-i18n="label_pain">疼痛等级 (1-10)</label>
                            <div class="pain-slider-container">
                                <input type="range" id="painLevel" min="1" max="10" value="3" oninput="document.getElementById('painDisplay').textContent=this.value">
                                <span class="pain-value" id="painDisplay">3</span>
                            </div>
                        </div>
                    </div>
                    <div class="form-group">
                        <label data-i18n="label_therapy">治疗类型</label>
                        <select id="therapyType" required></select>
                    </div>
                    <div class="form-group">
                        <label data-i18n="label_symptoms">症状描述</label>
                        <textarea id="symptoms" rows="3" placeholder="请输入详细症状... / 증상을 입력하세요..."></textarea>
                    </div>
                    <div class="form-group">
                        <label data-i18n="label_history">既往病史</label>
                        <input type="text" id="medicalHistory" placeholder="예: 고혈압, 당뇨 / 如：高血压、糖尿病">
                    </div>
                    <button type="submit" class="btn-submit" data-i18n="btn_generate">🔍 生成评估结果</button>
                </form>
            </div>
            <div class="card">
                <div class="card-header"><span class="dot" style="background:#00b894;"></span> <span data-i18n="result_title">评估结果</span></div>
                <div class="result-area" id="resultArea">
                    <span data-i18n="result_placeholder">👈 请先输入患者数据并点击生成按钮</span>
                </div>
            </div>
        </div>

        <div class="info-grid">
            <div class="info-card"><h3 data-i18n="info1_title">网站设计与开发方法</h3><p data-i18n="info1_content"></p></div>
            <div class="info-card"><h3 data-i18n="info2_title">主要功能介绍</h3><ul data-i18n="info2_content" style="padding-left:20px;"></ul></div>
            <div class="info-card"><h3 data-i18n="info3_title">预期效果与应用价值</h3><p data-i18n="info3_content"></p></div>
            <div class="info-card"><h3 data-i18n="info4_title">其他相关说明</h3><p data-i18n="info4_content"></p></div>
        </div>
        <div class="footer-note">© 2026 물리치료A WANG TIANLU 202217132 | Digital Health · Industrial Safety</div>
    </div>

    <button class="float-download hide-in-pdf" onclick="downloadPDF()" title="PDF 다운로드">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M19 9h-4V3H9v6H5l7 7 7-7zM5 18v2h14v-2H5z"/></svg>
    </button>

    <script>
        const i18n = {
            zh: {
                brand_sub: '数字健康医疗 · 产业安全平台',
                page_subtitle: '数字健康医疗产业安全管理系统',
                download_btn: '下载PDF',
                form_title: '📋 患者数据输入',
                label_name: '姓名',
                label_age: '年龄',
                label_gender: '性别',
                label_pain: '疼痛等级 (1-10)',
                label_therapy: '治疗类型',
                label_symptoms: '症状描述',
                label_history: '既往病史',
                btn_generate: '🔍 生成评估结果',
                result_title: '📊 评估结果',
                result_placeholder: '👈 请先输入患者数据并点击生成按钮',
                info1_title: '📐 网站设计与开发方法',
                info1_content: '本网站采用响应式Web设计，基于HTML5/CSS3/JS原生技术，集成html2pdf.js实现PDF导出。前端使用Flexbox与Grid布局，遵循MVVM模式，支持中韩双语无缝切换，代码模块化，注重维护性。',
                info2_title: '⚙️ 主要功能介绍',
                info2_list: [
                    '患者信息录入：姓名、年龄、性别、疼痛等级等。',
                    '治疗类型选择：运动、电疗、热冷疗、超声波、牵引、按摩、康复训练。',
                    '智能安全评估：基于多维度数据自动生成产业安全风险等级。',
                    '一键PDF报告：包含完整评估结果与系统说明。',
                    '中韩双语界面：所有文本实时同步切换。'
                ],
                info3_title: '🎯 预期效果与应用价值',
                info3_content: '提升物理治疗产业安全管理水平，辅助治疗师快速评估风险，优化个性化方案。为机构提供标准化记录与报告，推动数字健康医疗向智能化、安全化发展。',
                info4_title: '📝 其他相关说明',
                info4_content: '물리치료A课程项目，作者WANG TIANLU (202217132)。数据仅供演示，不构成医疗建议。实际应用需遵守HIPAA/GDPR等法规。评估基于预设规则，需结合专业判断。',
                risk_low: '低风险',
                risk_medium: '中风险',
                risk_high: '高风险',
                safety_good: '良好',
                safety_moderate: '一般',
                safety_poor: '需关注',
                gender_male: '男',
                gender_female: '女',
                gender_other: '其他',
                therapy_exercise: '运动疗法',
                therapy_electro: '电疗',
                therapy_thermal: '热疗/冷疗',
                therapy_ultrasound: '超声波治疗',
                therapy_traction: '牵引治疗',
                therapy_massage: '按摩疗法',
                therapy_rehab: '康复训练',
                toast_generated: '✅ 评估结果已生成',
                toast_pdf: '📄 PDF正在生成...',
                toast_pdf_done: '✅ PDF下载完成',
            },
            ko: {
                brand_sub: '디지털 헬스케어 · 산업안전 플랫폼',
                page_subtitle: '디지털 헬스케어 산업안전 관리 시스템',
                download_btn: 'PDF 다운로드',
                form_title: '📋 환자 데이터 입력',
                label_name: '이름',
                label_age: '나이',
                label_gender: '성별',
                label_pain: '통증 등급 (1-10)',
                label_therapy: '치료 유형',
                label_symptoms: '증상 설명',
                label_history: '과거 병력',
                btn_generate: '🔍 평가 결과 생성',
                result_title: '📊 평가 결과',
                result_placeholder: '👈 환자 데이터를 입력하고 생성 버튼을 클릭하세요',
                info1_title: '📐 웹사이트 설계 및 개발 방법',
                info1_content: '반응형 웹 디자인, HTML5/CSS3/JS 기반, html2pdf.js로 PDF 내보내기. Flexbox/Grid 레이아웃, MVVM 패턴, 중한 이중 언어 지원.',
                info2_title: '⚙️ 주요 기능',
                info2_list: [
                    '환자 정보 입력: 이름, 나이, 성별, 통증 등급',
                    '치료 유형 선택: 운동, 전기, 온열, 초음파, 견인, 마사지, 재활',
                    '스마트 안전 평가: 다차원 데이터 기반 산업안전 위험 등급 생성',
                    '원클릭 PDF 보고서: 완전한 평가 결과와 시스템 설명 포함',
                    '중국어/한국어 인터페이스: 모든 텍스트 실시간 동기화'
                ],
                info3_title: '🎯 기대 효과 및 응용 가치',
                info3_content: '물리치료 산업안전 관리 수준 향상, 치료사의 빠른 위험 평가 지원, 개인화된 치료 최적화. 표준화된 기록과 보고서 제공.',
                info4_title: '📝 기타 관련 사항',
                info4_content: '물리치료A 과정 프로젝트, WANG TIANLU (202217132). 데이터는 시연용이며 의학적 조언이 아닙니다. 실제 사용 시 HIPAA/GDPR 준수 필요.',
                risk_low: '저위험',
                risk_medium: '중위험',
                risk_high: '고위험',
                safety_good: '양호',
                safety_moderate: '보통',
                safety_poor: '주의 필요',
                gender_male: '남성',
                gender_female: '여성',
                gender_other: '기타',
                therapy_exercise: '운동 요법',
                therapy_electro: '전기 치료',
                therapy_thermal: '온열·냉각 치료',
                therapy_ultrasound: '초음파 치료',
                therapy_traction: '견인 치료',
                therapy_massage: '마사지 요법',
                therapy_rehab: '재활 훈련',
                toast_generated: '✅ 평가 결과 생성됨',
                toast_pdf: '📄 PDF 생성 중...',
                toast_pdf_done: '✅ PDF 다운로드 완료',
            }
        };

        let currentLang = 'zh';

        function applyLanguage(lang) {
            currentLang = lang;
            const dict = i18n[lang];
            document.querySelectorAll('[data-i18n]').forEach(el => {
                const key = el.dataset.i18n;
                if (!dict[key]) return;
                if (key === 'info2_list') {
                    el.innerHTML = dict[key].map(item => `<li>${item}</li>`).join('');
                } else if (el.tagName === 'UL') {
                    // 可能还有其他列表
                } else {
                    el.textContent = dict[key];
                }
            });

            // 重建性别和治疗类型下拉选项
            const genderSelect = document.getElementById('patientGender');
            const genderOptions = [
                { value: '', text: lang === 'zh' ? '请选择' : '선택하세요' },
                { value: 'male', text: dict.gender_male },
                { value: 'female', text: dict.gender_female },
                { value: 'other', text: dict.gender_other }
            ];
            genderSelect.innerHTML = genderOptions.map(o => `<option value="${o.value}">${o.text}</option>`).join('');

            const therapySelect = document.getElementById('therapyType');
            const therapyOptions = [
                { value: '', text: lang === 'zh' ? '请选择' : '선택하세요' },
                { value: 'exercise', text: dict.therapy_exercise },
                { value: 'electro', text: dict.therapy_electro },
                { value: 'thermal', text: dict.therapy_thermal },
                { value: 'ultrasound', text: dict.therapy_ultrasound },
                { value: 'traction', text: dict.therapy_traction },
                { value: 'massage', text: dict.therapy_massage },
                { value: 'rehab', text: dict.therapy_rehab }
            ];
            therapySelect.innerHTML = therapyOptions.map(o => `<option value="${o.value}">${o.text}</option>`).join('');

            // 更新placeholder
            document.getElementById('patientName').placeholder = lang === 'zh' ? '张三 / 홍길동' : '홍길동 / 张三';
            document.getElementById('symptoms').placeholder = lang === 'zh' ? '请输入详细症状...' :
                '증상을 입력하세요...';
            document.getElementById('medicalHistory').placeholder = lang === 'zh' ? '예: 고혈압, 당뇨' :
                '예: 고혈압, 당뇨';

            // 如果已有结果，刷新结果区域
            if (window._lastPatientData) {
                displayResult(window._lastPatientData);
            } else {
                const resultArea = document.getElementById('resultArea');
                if (!resultArea.classList.contains('has-data')) {
                    resultArea.innerHTML = `<span>${dict.result_placeholder}</span>`;
                }
            }

            document.querySelectorAll('#langSwitch button').forEach(btn => {
                btn.classList.toggle('active', btn.dataset.lang === lang);
            });
        }

        document.getElementById('langSwitch').addEventListener('click', (e) => {
            if (e.target.tagName === 'BUTTON' && e.target.dataset.lang) {
                applyLanguage(e.target.dataset.lang);
            }
        });

        function handleSubmit(event) {
            event.preventDefault();
            const name = document.getElementById('patientName').value.trim();
            const age = parseInt(document.getElementById('patientAge').value, 10);
            if (!name || isNaN(age) || age < 1 || age > 120) {
                alert(currentLang === 'zh' ? '请填写有效的姓名和年龄' : '유효한 이름과 나이를 입력하세요');
                return false;
            }
            const data = {
                name,
                age,
                gender: document.getElementById('patientGender').value,
                painLevel: parseInt(document.getElementById('painLevel').value, 10),
                therapyType: document.getElementById('therapyType').value,
                symptoms: document.getElementById('symptoms').value.trim(),
                medicalHistory: document.getElementById('medicalHistory').value.trim(),
                timestamp: new Date().toLocaleString(currentLang === 'zh' ? 'zh-CN' : 'ko-KR')
            };
            window._lastPatientData = data;
            displayResult(data);
            showToast(i18n[currentLang].toast_generated);
            return false;
        }

        function displayResult(data) {
            const dict = i18n[currentLang];
            const score = data.painLevel + (data.age > 60 ? 3 : data.age > 40 ? 1 : 0) +
                (data.medicalHistory && data.medicalHistory.length > 1 ? 2 : 0);
            let riskLevel, riskClass, safety;
            if (score <= 4) { riskLevel = dict.risk_low;
                riskClass = 'badge-low';
                safety = dict.safety_good; } else if (score <= 8) { riskLevel = dict.risk_medium;
                riskClass = 'badge-medium';
                safety = dict.safety_moderate; } else { riskLevel = dict.risk_high;
                riskClass = 'badge-high';
                safety = dict.safety_poor; }

            const genderText = data.gender === 'male' ? dict.gender_male : data.gender === 'female' ? dict
            .gender_female : dict.gender_other;
            const therapyText = dict['therapy_' + data.therapyType] || data.therapyType;

            const resultArea = document.getElementById('resultArea');
            resultArea.classList.add('has-data');
            resultArea.innerHTML = `
                <div class="result-item"><strong>${currentLang==='zh'?'患者':'환자'}:</strong> ${escapeHTML(data.name)}</div>
                <div class="result-item"><strong>${currentLang==='zh'?'年龄':'나이'}:</strong> ${data.age} | <strong>${currentLang==='zh'?'性别':'성별'}:</strong> ${genderText}</div>
                <div class="result-item"><strong>${currentLang==='zh'?'疼痛等级':'통증 등급'}:</strong> ${data.painLevel}/10</div>
                <div class="result-item"><strong>${currentLang==='zh'?'治疗类型':'치료 유형'}:</strong> ${therapyText}</div>
                <div class="result-item"><strong>${currentLang==='zh'?'症状':'증상'}:</strong> ${escapeHTML(data.symptoms) || (currentLang==='zh'?'未填写':'미기입')}</div>
                <div class="result-item"><strong>${currentLang==='zh'?'病史':'병력'}:</strong> ${escapeHTML(data.medicalHistory) || (currentLang==='zh'?'无':'없음')}</div>
                <div class="result-item" style="margin-top:10px;border-top:2px solid #dfe6e9;padding-top:10px;">
                    <strong>🔒 ${currentLang==='zh'?'产业安全风险':'산업안전 위험'}:</strong>
                    <span class="badge-risk ${riskClass}">${riskLevel}</span>
                </div>
                <div class="result-item"><strong>🛡️ ${currentLang==='zh'?'安全状态':'안전 상태'}:</strong> ${safety}</div>
                <div class="result-item"><strong>📅 ${currentLang==='zh'?'评估时间':'평가 시간'}:</strong> ${data.timestamp}</div>
                <div class="result-item" style="color:#0066cc;font-weight:500;">${currentLang==='zh'?'⚠️ 本评估仅供参考，不构成医疗建议。':'⚠️ 본 평가는 참고용이며 의학적 조언이 아닙니다.'}</div>
            `;
        }

        function escapeHTML(str) {
            const div = document.createElement('div');
            div.textContent = str;
            return div.innerHTML;
        }

        function showToast(msg) {
            const old = document.querySelector('.toast');
            if (old) old.remove();
            const toast = document.createElement('div');
            toast.className = 'toast';
            toast.textContent = msg;
            document.body.appendChild(toast);
            setTimeout(() => toast.remove(), 2500);
        }

        function downloadPDF() {
            showToast(i18n[currentLang].toast_pdf);
            // 隐藏所有下载按钮
            document.querySelectorAll('.hide-in-pdf').forEach(el => el.style.display = 'none');
            const element = document.getElementById('pdfCaptureArea');
            const opt = {
                margin: [8, 10, 8, 10],
                filename: `WANGTIANLU_202217132_${new Date().toISOString().slice(0,10)}.pdf`,
                image: { type: 'jpeg', quality: 0.95 },
                html2canvas: { scale: 2, backgroundColor: '#ffffff', logging: false },
                jsPDF: { unit: 'mm', format: 'a4', orientation: 'portrait' },
                pagebreak: { mode: ['avoid-all', 'css', 'legacy'] }
            };
            html2pdf().set(opt).from(element).save().then(() => {
                showToast(i18n[currentLang].toast_pdf_done);
                // 恢复按钮显示
                document.querySelectorAll('.hide-in-pdf').forEach(el => el.style.display = '');
            }).catch(() => {
                window.print();
                document.querySelectorAll('.hide-in-pdf').forEach(el => el.style.display = '');
            });
        }

        // 快捷键 Ctrl+S
        document.addEventListener('keydown', (e) => {
            if ((e.ctrlKey || e.metaKey) && e.key === 's') {
                e.preventDefault();
                downloadPDF();
            }
        });

        // 初始化语言
        applyLanguage('zh');
    </script>
</body>
</html>
](https://xmupen-png.github.io/http-delicate-ganache-bcfeaa.netlify.app-/)
