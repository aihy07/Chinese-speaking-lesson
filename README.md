[deepseek_html_20260716_96545e.html](https://github.com/user-attachments/files/30082488/deepseek_html_20260716_96545e.html)
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>《标准汉语会话360句1》第一课</title>
    <script src="https://cdn.jsdelivr.net/npm/qrcodejs@1.0.0/qrcode.min.js">
    </script>
    <style>
        /* ===== 全局样式（精简但完整） ===== */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            font-family: 'Segoe UI', 'PingFang SC', Roboto, 'Helvetica Neue', sans-serif;
            background: linear-gradient(145deg, #fdf6f0 0%, #f5e6da 100%);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }
        .app-container {
            width: 100%;
            max-width: 960px;
            margin: 0 auto;
            position: relative;
        }
        .card {
            background: rgba(255, 248, 242, 0.85);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border-radius: 40px;
            box-shadow: 0 20px 60px rgba(180, 120, 80, 0.18), 0 6px 20px rgba(180, 120, 80, 0.08);
            padding: 32px 30px 28px;
            transition: all 0.25s ease;
            border: 1px solid rgba(255, 235, 220, 0.6);
        }
        .page {
            display: none;
        }
        .page.active {
            display: block;
        }
        /* ===== 全局工具栏 ===== */
        .global-toolbar {
            display: flex;
            align-items: center;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 12px;
            margin-bottom: 16px;
            padding: 8px 16px;
            background: rgba(255, 248, 242, 0.6);
            backdrop-filter: blur(4px);
            border-radius: 60px;
            border: 1px solid rgba(255, 235, 220, 0.8);
        }
        .global-toolbar .brand {
            font-weight: 700;
            color: #7a4a3a;
            font-size: 1.2rem;
            letter-spacing: 1px;
        }
        .global-toolbar .brand small {
            font-weight: 400;
            font-size: 0.8rem;
            color: #a67c6a;
            margin-left: 6px;
        }
        .global-toolbar .actions {
            display: flex;
            gap: 10px;
            align-items: center;
            flex-wrap: wrap;
        }
        .global-toolbar .actions button {
            background: #7a4a3a;
            border: none;
            color: #fff;
            padding: 6px 18px;
            border-radius: 40px;
            font-size: 0.9rem;
            font-weight: 600;
            cursor: pointer;
            transition: 0.15s;
            box-shadow: 0 2px 8px rgba(122, 74, 58, 0.2);
        }
        .global-toolbar .actions button:hover {
            transform: translateY(-2px);
            background: #8f5d4a;
        }
        .global-toolbar .actions button.secondary {
            background: #ecd7cb;
            color: #5a3f33;
            box-shadow: none;
        }
        .global-toolbar .actions button.secondary:hover {
            background: #ddc3b3;
        }
        /* ===== 课程列表 ===== */
        #courseListPage .card {
            text-align: center;
            padding-bottom: 36px;
        }
        .main-title {
            font-size: 2.4rem;
            font-weight: 700;
            color: #7a4a3a;
            letter-spacing: 2px;
            margin-bottom: 4px;
        }
        .main-title small {
            font-size: 1.2rem;
            font-weight: 400;
            color: #a67c6a;
            display: block;
            margin-top: 4px;
            letter-spacing: 6px;
        }
        .main-subtitle {
            color: #a67c6a;
            font-size: 1.05rem;
            letter-spacing: 4px;
            margin-bottom: 16px;
            border-bottom: 2px dashed #ecd7cb;
            padding-bottom: 16px;
        }
        .course-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 20px;
            margin-top: 8px;
        }
        .course-card {
            background: #fffaf6;
            border-radius: 28px;
            padding: 24px 16px 20px;
            box-shadow: 0 6px 18px rgba(160, 110, 70, 0.10);
            transition: all 0.2s ease;
            border: 2px solid transparent;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 6px;
            position: relative;
            min-height: 160px;
            justify-content: center;
        }
        .course-card .num {
            font-size: 1.8rem;
            font-weight: 700;
            color: #5a3f33;
        }
        .course-card .cname {
            font-size: 1.15rem;
            font-weight: 700;
            color: #5a3f33;
        }
        .course-card .cdesc {
            font-size: 0.82rem;
            color: #8f7568;
            line-height: 1.4;
        }
        .course-card .status {
            margin-top: 6px;
            font-size: 0.75rem;
            font-weight: 600;
            padding: 4px 16px;
            border-radius: 30px;
            display: inline-block;
        }
        .course-card .status.unlocked {
            background: #b8d9b0;
            color: #2d5a1e;
        }
        .course-card .status.locked {
            background: #ecd7cb;
            color: #8f7568;
        }
        .course-card .lock-icon {
            font-size: 1.6rem;
            margin-top: 4px;
        }
        .course-card.unlocked {
            cursor: pointer;
            border-color: #c49a82;
        }
        .course-card.unlocked:hover {
            transform: translateY(-5px);
            box-shadow: 0 14px 30px rgba(160, 110, 70, 0.16);
            border-color: #a67058;
        }
        .course-card.unlocked:active {
            transform: scale(0.97);
        }
        .course-card.locked {
            cursor: not-allowed;
            opacity: 0.7;
            filter: grayscale(0.2);
        }
        /* ===== 教师控制台 ===== */
        #teacherPanel .card {
            text-align: left;
        }
        .panel-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 20px;
            flex-wrap: wrap;
            gap: 10px;
        }
        .panel-header h2 {
            font-size: 1.8rem;
            color: #7a4a3a;
        }
        .panel-header .back-btn {
            background: #ecd7cb;
            border: none;
            font-size: 1.1rem;
            padding: 8px 18px;
            border-radius: 60px;
            cursor: pointer;
            color: #5a3f33;
            font-weight: 600;
            transition: 0.15s;
            display: flex;
            align-items: center;
            gap: 6px;
        }
        .panel-header .back-btn:hover {
            background: #ddc3b3;
            transform: translateX(-3px);
        }
        .panel-controls {
            display: flex;
            gap: 20px;
            flex-wrap: wrap;
            align-items: center;
            margin-bottom: 16px;
            background: #faf0ea;
            padding: 16px 20px;
            border-radius: 20px;
        }
        .panel-controls label {
            font-weight: 600;
            color: #5a3f33;
            display: flex;
            align-items: center;
            gap: 10px;
            cursor: pointer;
        }
        .panel-controls input[type="checkbox"] {
            width: 20px;
            height: 20px;
            cursor: pointer;
        }
        .panel-controls .export-btn {
            background: #7a4a3a;
            border: none;
            color: #fff;
            padding: 8px 24px;
            border-radius: 40px;
            font-weight: 600;
            cursor: pointer;
            transition: 0.15s;
        }
        .panel-controls .export-btn:hover {
            background: #8f5d4a;
        }
        .panel-controls .code-btn {
            background: #d9b8a0;
            border: none;
            color: #5a3f33;
            padding: 8px 24px;
            border-radius: 40px;
            font-weight: 600;
            cursor: pointer;
            transition: 0.15s;
        }
        .panel-controls .code-btn:hover {
            background: #c9a890;
        }
        .panel-controls .code-display {
            background: #fff;
            padding: 4px 16px;
            border-radius: 30px;
            font-size: 1.4rem;
            font-weight: 700;
            letter-spacing: 4px;
            color: #7a4a3a;
            min-width: 80px;
            text-align: center;
        }
        .panel-link {
            background: #f5e6da;
            padding: 10px 16px;
            border-radius: 30px;
            display: flex;
            align-items: center;
            gap: 12px;
            flex-wrap: wrap;
            margin-bottom: 16px;
        }
        .panel-link span {
            font-size: 0.9rem;
            color: #5a3f33;
            word-break: break-all;
        }
        .panel-link button {
            background: #7a4a3a;
            border: none;
            color: #fff;
            padding: 4px 16px;
            border-radius: 30px;
            cursor: pointer;
            font-size: 0.9rem;
        }
        .panel-link button:hover {
            background: #8f5d4a;
        }
        .student-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 12px;
            font-size: 0.95rem;
        }
        .student-table th {
            background: #ecd7cb;
            color: #5a3f33;
            padding: 10px 12px;
            text-align: left;
            border-radius: 12px 12px 0 0;
        }
        .student-table td {
            padding: 10px 12px;
            border-bottom: 1px solid #ecd7cb;
        }
        .student-table tr:hover {
            background: #f5e6da;
        }
        .empty-msg {
            color: #a67c6a;
            text-align: center;
            padding: 30px 0;
            font-size: 1.1rem;
        }
        /* ===== 学生加入页 ===== */
        #studentJoin .card {
            text-align: center;
        }
        .join-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 16px;
            flex-wrap: wrap;
            gap: 10px;
        }
        .join-header .back-btn {
            background: #ecd7cb;
            border: none;
            font-size: 1.1rem;
            padding: 8px 18px;
            border-radius: 60px;
            cursor: pointer;
            color: #5a3f33;
            font-weight: 600;
            transition: 0.15s;
            display: flex;
            align-items: center;
            gap: 6px;
        }
        .join-header .back-btn:hover {
            background: #ddc3b3;
            transform: translateX(-3px);
        }
        .join-header h2 {
            font-size: 1.8rem;
            color: #7a4a3a;
        }
        .qr-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            margin: 16px 0;
        }
        #qrcode {
            background: #fff;
            padding: 16px;
            border-radius: 20px;
            box-shadow: 0 6px 20px rgba(0, 0, 0, 0.08);
            display: inline-block;
        }
        .join-link {
            margin: 8px 0 16px;
            font-size: 0.9rem;
            color: #5a3f33;
            background: #f5e6da;
            padding: 8px 16px;
            border-radius: 30px;
            display: inline-flex;
            align-items: center;
            gap: 12px;
            flex-wrap: wrap;
            justify-content: center;
        }
        .join-link button {
            background: #7a4a3a;
            border: none;
            color: #fff;
            padding: 4px 16px;
            border-radius: 30px;
            cursor: pointer;
            font-size: 0.9rem;
        }
        .join-link button:hover {
            background: #8f5d4a;
        }
        .join-form {
            margin: 16px 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 14px;
        }
        .join-form .row {
            display: flex;
            gap: 12px;
            flex-wrap: wrap;
            justify-content: center;
        }
        .join-form input {
            padding: 12px 20px;
            border: 2px solid #ecd7cb;
            border-radius: 40px;
            font-size: 1.1rem;
            width: 200px;
            max-width: 90%;
            outline: none;
            transition: 0.15s;
        }
        .join-form input:focus {
            border-color: #c49a82;
            box-shadow: 0 0 0 4px rgba(196, 154, 130, 0.2);
        }
        .join-form button {
            background: #7a4a3a;
            border: none;
            color: #fff;
            padding: 12px 40px;
            border-radius: 40px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: 0.15s;
            box-shadow: 0 4px 12px rgba(122, 74, 58, 0.25);
        }
        .join-form button:hover {
            background: #8f5d4a;
            transform: translateY(-2px);
        }
        .join-message {
            margin-top: 12px;
            font-size: 1rem;
            color: #7a5f50;
            min-height: 30px;
        }
        .join-message.success {
            color: #2d5a1e;
            font-weight: 600;
        }
        /* ===== 第一课内容页 ===== */
        #lessonContentPage .card {
            text-align: center;
            padding-bottom: 36px;
        }
        .lesson-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 12px;
            flex-wrap: wrap;
            gap: 10px;
        }
        .lesson-header .back-btn {
            background: #ecd7cb;
            border: none;
            font-size: 1.1rem;
            padding: 8px 18px;
            border-radius: 60px;
            cursor: pointer;
            color: #5a3f33;
            font-weight: 600;
            transition: 0.15s;
            display: flex;
            align-items: center;
            gap: 6px;
        }
        .lesson-header .back-btn:hover {
            background: #ddc3b3;
            transform: translateX(-3px);
        }
        .lesson-header .lesson-title {
            font-size: 1.8rem;
            font-weight: 700;
            color: #7a4a3a;
            letter-spacing: 1px;
        }
        .lesson-header .lesson-badge {
            background: #7a4a3a;
            color: #fff;
            font-size: 0.8rem;
            padding: 4px 18px;
            border-radius: 40px;
            font-weight: 500;
        }
        .lesson-subtitle {
            color: #a67c6a;
            font-size: 1rem;
            letter-spacing: 3px;
            margin-bottom: 24px;
            border-bottom: 2px dashed #ecd7cb;
            padding-bottom: 14px;
        }
        .exercise-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
            gap: 18px;
            margin-top: 8px;
        }
        .ex-card {
            background: #fffaf6;
            border-radius: 28px;
            padding: 24px 16px 20px;
            box-shadow: 0 6px 18px rgba(160, 110, 70, 0.10);
            cursor: pointer;
            transition: all 0.2s ease;
            border: 2px solid transparent;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 6px;
        }
        .ex-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 14px 30px rgba(160, 110, 70, 0.16);
            border-color: #e7c9b8;
        }
        .ex-card:active {
            transform: scale(0.97);
        }
        .ex-card .icon {
            font-size: 2.8rem;
            line-height: 1.2;
        }
        .ex-card .ex-title {
            font-size: 1.05rem;
            font-weight: 700;
            color: #5a3f33;
        }
        .ex-card .ex-desc {
            font-size: 0.78rem;
            color: #8f7568;
            line-height: 1.4;
            max-width: 140px;
        }
        .ex-card .badge {
            margin-top: 4px;
            background: #e7d3c6;
            color: #5a3f33;
            font-size: 0.65rem;
            padding: 2px 14px;
            border-radius: 30px;
            font-weight: 600;
        }
        /* ===== 练习页 ===== */
        #practicePage .card {
            padding: 32px 30px 28px;
        }
        .practice-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 16px;
            flex-wrap: wrap;
            gap: 10px;
        }
        .practice-header .back-btn {
            background: #ecd7cb;
            border: none;
            font-size: 1.1rem;
            padding: 8px 18px;
            border-radius: 60px;
            cursor: pointer;
            color: #5a3f33;
            font-weight: 600;
            transition: 0.15s;
            display: flex;
            align-items: center;
            gap: 6px;
        }
        .practice-header .back-btn:hover {
            background: #ddc3b3;
            transform: translateX(-3px);
        }
        .practice-header .practice-title {
            font-size: 1.5rem;
            font-weight: 700;
            color: #5a3f33;
            letter-spacing: 1px;
        }
        .practice-header .practice-stats {
            display: flex;
            align-items: center;
            gap: 18px;
            font-size: 0.95rem;
            color: #7a5f50;
            font-weight: 500;
        }
        .practice-header .practice-stats .score {
            background: #7a4a3a;
            color: #fff;
            padding: 4px 16px;
            border-radius: 40px;
            font-size: 0.9rem;
        }
        .progress-bar {
            width: 100%;
            height: 6px;
            background: #ecd7cb;
            border-radius: 10px;
            margin-bottom: 24px;
            overflow: hidden;
        }
        .progress-bar .fill {
            height: 100%;
            background: linear-gradient(90deg, #c49a82, #a67058);
            border-radius: 10px;
            transition: width 0.4s ease;
            width: 0%;
        }
        .question-area {
            text-align: center;
            padding: 20px 0 12px;
            min-height: 120px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }
        .question-area .display-char {
            font-size: 4.8rem;
            font-weight: 700;
            color: #3f2b21;
        }
        .question-area .hint-text {
            font-size: 1rem;
            color: #a67c6a;
            margin-top: 6px;
        }
        .audio-btn {
            background: #7a4a3a;
            border: none;
            color: #fff;
            font-size: 2.6rem;
            width: 80px;
            height: 80px;
            border-radius: 50%;
            cursor: pointer;
            transition: all 0.15s;
            box-shadow: 0 6px 20px rgba(122, 74, 58, 0.30);
            display: inline-flex;
            align-items: center;
            justify-content: center;
        }
        .audio-btn:hover {
            transform: scale(1.06);
            background: #8f5d4a;
        }
        .audio-btn:active {
            transform: scale(0.94);
        }
        .audio-btn.playing {
            animation: pulse 0.8s ease-in-out infinite alternate;
        }
        @keyframes pulse {
            0% {
                box-shadow: 0 0 0 0 rgba(122, 74, 58, 0.5);
            }
            100% {
                box-shadow: 0 0 0 20px rgba(122, 74, 58, 0);
            }
        }
        .options-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 14px;
            margin: 18px 0 12px;
        }
        .options-grid .opt-btn {
            background: #fffcf9;
            border: 2px solid #ecd7cb;
            border-radius: 20px;
            padding: 16px 8px;
            font-size: 1.5rem;
            font-weight: 600;
            color: #3f2b21;
            cursor: pointer;
            transition: all 0.12s;
            text-align: center;
            box-shadow: 0 2px 6px rgba(0, 0, 0, 0.02);
        }
        .options-grid .opt-btn:hover:not(.disabled) {
            background: #f5e6da;
            border-color: #c49a82;
            transform: scale(1.02);
        }
        .options-grid .opt-btn:active:not(.disabled) {
            transform: scale(0.96);
        }
        .options-grid .opt-btn.correct {
            background: #b8d9b0;
            border-color: #6f9e5e;
            color: #2d5a1e;
        }
        .options-grid .opt-btn.wrong {
            background: #f0c8c0;
            border-color: #c47a6a;
            color: #7a3a2a;
        }
        .options-grid .opt-btn.disabled {
            cursor: default;
            opacity: 0.85;
        }
        .feedback {
            margin: 16px 0 10px;
            padding: 14px 20px;
            border-radius: 20px;
            font-size: 1.1rem;
            font-weight: 500;
            min-height: 60px;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
            gap: 4px;
            text-align: center;
            background: #faf0ea;
            border: 1px solid #ecd7cb;
            transition: all 0.2s;
        }
        .feedback .meaning {
            font-weight: 400;
            font-size: 0.95rem;
            color: #7a5f50;
        }
        .feedback.correct {
            background: #e8f5e3;
            border-color: #b8d9b0;
        }
        .feedback.wrong {
            background: #fae8e3;
            border-color: #f0c8c0;
        }
        .next-btn {
            background: #7a4a3a;
            border: none;
            color: #fff;
            font-size: 1.1rem;
            font-weight: 600;
            padding: 14px 34px;
            border-radius: 60px;
            cursor: pointer;
            transition: all 0.15s;
            margin-top: 6px;
            box-shadow: 0 4px 14px rgba(122, 74, 58, 0.25);
            width: 100%;
            max-width: 200px;
        }
        .next-btn:hover {
            background: #8f5d4a;
            transform: translateY(-2px);
        }
        .next-btn:active {
            transform: scale(0.96);
        }
        .next-btn:disabled {
            opacity: 0.4;
            cursor: not-allowed;
            transform: none !important;
        }
        .result-box {
            text-align: center;
            padding: 30px 10px 10px;
        }
        .result-box .big-icon {
            font-size: 5rem;
        }
        .result-box .result-title {
            font-size: 2rem;
            font-weight: 700;
            color: #3f2b21;
            margin: 8px 0;
        }
        .result-box .result-score {
            font-size: 3.6rem;
            font-weight: 800;
            color: #7a4a3a;
        }
        .result-box .result-detail {
            color: #7a5f50;
            font-size: 1.1rem;
            margin: 4px 0 18px;
        }
        .result-box .result-stars {
            font-size: 2.8rem;
            letter-spacing: 6px;
            margin: 4px 0 14px;
        }
        .interact-bar {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 16px;
            flex-wrap: wrap;
            background: #f5e6da;
            padding: 10px 20px;
            border-radius: 40px;
            margin-bottom: 16px;
        }
        .interact-bar label {
            font-weight: 600;
            color: #5a3f33;
        }
        .interact-bar select {
            padding: 6px 16px;
            border: 2px solid #ecd7cb;
            border-radius: 30px;
            font-size: 1rem;
            background: #fffcf9;
            outline: none;
        }
        .interact-bar .point-badge {
            background: #7a4a3a;
            color: #fff;
            padding: 2px 14px;
            border-radius: 30px;
            font-size: 0.9rem;
        }
        .hidden {
            display: none !important;
        }
        .deploy-guide {
            background: #faf0ea;
            border-radius: 20px;
            padding: 16px 20px;
            margin-top: 20px;
            text-align: left;
            border: 1px solid #ecd7cb;
        }
        .deploy-guide h4 {
            color: #5a3f33;
            margin-bottom: 8px;
        }
        .deploy-guide ol {
            padding-left: 20px;
            color: #5a3f33;
            line-height: 1.8;
        }
        .deploy-guide code {
            background: #fff;
            padding: 2px 8px;
            border-radius: 6px;
            font-size: 0.85rem;
            color: #7a4a3a;
        }
        .mode-selector {
            display: flex;
            gap: 16px;
            justify-content: center;
            margin: 12px 0 18px;
        }
        .mode-btn {
            background: #ecd7cb;
            border: none;
            padding: 10px 28px;
            border-radius: 40px;
            font-size: 1.1rem;
            font-weight: 600;
            color: #5a3f33;
            cursor: pointer;
            transition: 0.15s;
        }
        .mode-btn.active {
            background: #7a4a3a;
            color: #fff;
            box-shadow: 0 4px 12px rgba(122, 74, 58, 0.3);
        }
        .mode-btn:hover {
            transform: translateY(-2px);
        }
        .card-display {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            margin: 20px 0;
        }
        .card-display .big-card {
            background: #fffaf6;
            border: 3px solid #ecd7cb;
            border-radius: 30px;
            padding: 30px 50px;
            font-size: 5rem;
            font-weight: 700;
            color: #3f2b21;
            min-width: 200px;
            text-align: center;
            box-shadow: 0 8px 24px rgba(160, 110, 70, 0.12);
        }
        .card-display .example {
            margin-top: 12px;
            font-size: 1.8rem;
            color: #7a5f50;
            background: #f5e6da;
            padding: 6px 24px;
            border-radius: 40px;
        }
        .card-display .student-name {
            font-size: 2.2rem;
            font-weight: 700;
            color: #7a4a3a;
            margin: 10px 0;
        }
        .control-buttons {
            display: flex;
            gap: 16px;
            justify-content: center;
            flex-wrap: wrap;
            margin: 16px 0;
        }
        .control-buttons button {
            background: #7a4a3a;
            border: none;
            color: #fff;
            padding: 12px 28px;
            border-radius: 40px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: 0.15s;
            box-shadow: 0 4px 12px rgba(122, 74, 58, 0.25);
        }
        .control-buttons button:hover {
            transform: translateY(-2px);
            background: #8f5d4a;
        }
        .control-buttons button:active {
            transform: scale(0.96);
        }
        .info-feedback {
            margin: 12px 0;
            padding: 14px;
            border-radius: 20px;
            background: #faf0ea;
            font-size: 1.1rem;
            color: #5a3f33;
            min-height: 50px;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
        }

        /* ===== 响应式（略） ===== */
        @media (max-width: 600px) {
            /* 简化，实际保留基本样式 */
        }
        @media (max-width: 420px) {}
        .flex-center {
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .mt-8 {
            margin-top: 8px;
        }
    </style>
</head>
<body>

    <div class="app-container">

        <!-- ===== 全局顶部工具栏 ===== -->
        <div class="global-toolbar">
            <div class="brand">
                📖 标准汉语 <small>360句 · 第1课</small>
            </div>
            <div class="actions">
                <button id="globalJoinBtn" class="secondary">📲 加入课堂</button>
                <button id="globalTeacherBtn">👩‍🏫 控制台</button>
            </div>
        </div>

        <!-- ===== 页面1: 课程列表 ===== -->
        <div id="courseListPage" class="page active">
            <div class="card">
                <div class="main-title">
                    📖 《标准汉语会话360句1》
                    <small>Standard Chinese Conversation 360 · Book 1</small>
                </div>
                <div class="main-subtitle">— 选择课程开始学习 —</div>
                <div class="course-grid">
                    <div class="course-card unlocked" data-lesson="1">
                        <div class="num">第 1 课</div>
                        <div class="cname">🔤 你好 &amp; 拼音</div>
                        <div class="cdesc">声母 · 韵母 · 声调 · 拼读</div>
                        <span class="status unlocked">✅ 已解锁</span>
                    </div>
                    <div class="course-card locked">
                        <div class="num">第 2 课</div>
                        <div class="cname">👋 问候与介绍</div>
                        <div class="cdesc">你好 · 我叫…</div>
                        <span class="status locked">🔒 即将解锁</span>
                        <div class="lock-icon">🔒</div>
                    </div>
                    <div class="course-card locked">
                        <div class="num">第 3 课</div>
                        <div class="cname">🔢 数字与时间</div>
                        <div class="cdesc">一 ~ 十 · 几点</div>
                        <span class="status locked">🔒 即将解锁</span>
                        <div class="lock-icon">🔒</div>
                    </div>
                    <div class="course-card locked">
                        <div class="num">第 4 课</div>
                        <div class="cname">👨‍👩‍👦 家庭与朋友</div>
                        <div class="cdesc">爸爸 · 妈妈 · 朋友</div>
                        <span class="status locked">🔒 即将解锁</span>
                        <div class="lock-icon">🔒</div>
                    </div>
                    <div class="course-card locked">
                        <div class="num">第 5 课</div>
                        <div class="cname">🍜 饮食与购物</div>
                        <div class="cdesc">吃 · 喝 · 买</div>
                        <span class="status locked">🔒 即将解锁</span>
                        <div class="lock-icon">🔒</div>
                    </div>
                    <div class="course-card locked">
                        <div class="num">第 6 课</div>
                        <div class="cname">🚌 交通与旅游</div>
                        <div class="cdesc">坐车 · 去哪里</div>
                        <span class="status locked">🔒 即将解锁</span>
                        <div class="lock-icon">🔒</div>
                    </div>
                    <div class="course-card locked">
                        <div class="num">第 7 课</div>
                        <div class="cname">🌤️ 天气与季节</div>
                        <div class="cdesc">冷 · 热 · 春天</div>
                        <span class="status locked">🔒 即将解锁</span>
                        <div class="lock-icon">🔒</div>
                    </div>
                    <div class="course-card locked">
                        <div class="num">第 8 课</div>
                        <div class="cname">⚽ 爱好与运动</div>
                        <div class="cdesc">喜欢 · 打球</div>
                        <span class="status locked">🔒 即将解锁</span>
                        <div class="lock-icon">🔒</div>
                    </div>
                </div>
                <div style="margin-top:24px; font-size:0.8rem; color:#b89a88; letter-spacing:1px;">
                    🌟 完成第一课，解锁更多内容！
                </div>
                <div class="deploy-guide">
                    <h4>🚀 如何用 GitHub 部署本页面</h4>
                    <ol>
                        <li>创建 GitHub 仓库，将本页面保存为 <code>index.html</code> 并上传。</li>
                        <li>进入仓库 Settings → Pages，选择 <code>main</code> 分支，点击 Save。</li>
                        <li>等待几分钟，页面会获得一个 <code>https://你的用户名.github.io/仓库名</code> 的链接。</li>
                        <li>将链接分享给学生，学生打开后即可扫码或输入课堂码加入。</li>
                        <li>教师可在控制台开启“全局互动模式”，学生答题即可获得积分。</li>
                    </ol>
                    <p style="margin-top:8px;color:#7a5f50;font-size:0.9rem;">💡 所有练习无需任何同步，打开即用！</p>
                </div>
            </div>
        </div>

        <!-- ===== 页面2: 教师控制台 ===== -->
        <div id="teacherPanel" class="page">
            <div class="card">
                <div class="panel-header">
                    <h2>👩‍🏫 教师控制台</h2>
                    <button class="back-btn" id="backFromTeacherBtn">← 返回课程</button>
                </div>
                <div class="panel-link">
                    <span>🔗 课堂链接：<span id="pageLinkDisplay"></span></span>
                    <button id="copyLinkBtn">复制链接</button>
                </div>
                <div class="panel-controls">
                    <label>
                        <input type="checkbox" id="interactToggle" /> 全局互动模式（积分）
                    </label>
                    <label>
                        <input type="checkbox" id="codeToggle" /> 启用课堂码验证
                    </label>
                    <button class="code-btn" id="generateCodeBtn">🔄 生成课堂码</button>
                    <span class="code-display" id="codeDisplay">——</span>
                    <button class="export-btn" id="exportCsvBtn">📊 导出积分 CSV</button>
                    <span style="font-size:0.9rem;color:#7a5f50;" id="studentCount">当前学生：0 人</span>
                </div>
                <div id="studentListContainer">
                    <table class="student-table" id="studentTable">
                        <thead><tr><th>姓名</th><th>积分</th></tr></thead>
                        <tbody id="studentTableBody"></tbody>
                    </table>
                    <div id="emptyStudentMsg" class="empty-msg">暂无学生加入，请让学生扫码或输入课堂码加入。</div>
                </div>
            </div>
        </div>

        <!-- ===== 页面3: 学生扫码加入 ===== -->
        <div id="studentJoin" class="page">
            <div class="card">
                <div class="join-header">
                    <button class="back-btn" id="backFromJoinBtn">← 返回课程</button>
                    <h2>📲 加入课堂</h2>
                    <span style="width:60px;"></span>
                </div>
                <div class="qr-container">
                    <div id="qrcode"></div>
                    <p style="margin-top:6px;color:#7a5f50;font-size:0.9rem;">扫描二维码加入（如无法扫码，请使用下方方式）</p>
                </div>
                <div class="join-link">
                    <span>🔗 课堂链接：<span id="joinPageLink"></span></span>
                    <button id="copyJoinLinkBtn">复制链接</button>
                </div>
                <div class="join-form">
                    <div class="row">
                        <input type="text" id="joinStudentName" placeholder="输入你的姓名" maxlength="20" />
                        <input type="text" id="joinClassCode" placeholder="课堂码（若需要）" maxlength="10" style="width:140px;" />
                    </div>
                    <button id="joinClassBtn">加入课堂</button>
                </div>
                <div id="joinMessage" class="join-message"></div>
            </div>
        </div>

        <!-- ===== 页面4: 第一课内容 ===== -->
        <div id="lessonContentPage" class="page">
            <div class="card">
                <div class="lesson-header">
                    <button class="back-btn" id="backToCourseBtn">← 课程列表</button>
                    <div class="lesson-title">📚 第一课 · 你好 &amp; 拼音</div>
                    <span class="lesson-badge">✅ 已解锁</span>
                </div>
                <div class="lesson-subtitle">— 选择一种练习方式开始 —</div>
                <div class="exercise-grid">
                    <div class="ex-card" data-ex="initials">
                        <div class="icon">🔤</div>
                        <div class="ex-title">声母词卡</div>
                        <div class="ex-desc">声母卡片，带示例</div>
                        <div class="badge">声母</div>
                    </div>
                    <div class="ex-card" data-ex="finals">
                        <div class="icon">🔡</div>
                        <div class="ex-title">韵母词卡</div>
                        <div class="ex-desc">韵母卡片，带示例</div>
                        <div class="badge">韵母</div>
                    </div>
                    <div class="ex-card" data-ex="natural">
                        <div class="icon">📣</div>
                        <div class="ex-title">自然拼读</div>
                        <div class="ex-desc">抽选学生或集体练习拼读</div>
                        <div class="badge">拼读</div>
                    </div>
                    <div class="ex-card" data-ex="listen2pinyin">
                        <div class="icon">🎧</div>
                        <div class="ex-title">听音选拼音</div>
                        <div class="ex-desc">听发音，选拼音（无汉字）</div>
                        <div class="badge">听→音</div>
                    </div>
                    <div class="ex-card" data-ex="listen2tone">
                        <div class="icon">🔊</div>
                        <div class="ex-title">听音选声调</div>
                        <div class="ex-desc">听发音，选声调符号（无汉字）</div>
                        <div class="badge">听→调</div>
                    </div>
                    <div class="ex-card" data-ex="char2pinyin">
                        <div class="icon">✍️</div>
                        <div class="ex-title">看汉字选拼音</div>
                        <div class="ex-desc">从指定字词中选出正确拼音</div>
                        <div class="badge">形→音</div>
                    </div>
                    <div class="ex-card" data-ex="listen2compound">
                        <div class="icon">🔥</div>
                        <div class="ex-title">挑战·听词选拼音</div>
                        <div class="ex-desc">听双字词，选完整拼音</div>
                        <div class="badge">双字</div>
                    </div>
                </div>
                <div style="margin-top:24px; font-size:0.8rem; color:#b89a88; letter-spacing:1px;">
                    🌟 测验模块每轮 50 题 · 词卡模块可反复翻看
                </div>
            </div>
        </div>

        <!-- ===== 页面5: 具体练习 ===== -->
        <div id="practicePage" class="page">
            <div class="card">
                <div class="practice-header">
                    <button class="back-btn" id="backToLessonBtn">← 返回课程</button>
                    <div class="practice-title" id="practiceTitle">练习</div>
                    <div class="practice-stats">
                        <span id="progressText">1 / 50</span>
                        <span class="score" id="scoreText">✓ 0</span>
                    </div>
                </div>
                <div class="progress-bar">
                    <div class="fill" id="progressFill"></div>
                </div>

                <!-- 互动栏（当有学生且互动模式开启时显示） -->
                <div id="interactBar" class="interact-bar hidden">
                    <label>👤 当前学生：</label>
                    <select id="studentSelector"></select>
                    <span class="point-badge" id="currentStudentPoints">积分：0</span>
                </div>

                <div class="question-area" id="questionArea"></div>
                <div class="options-grid" id="optionsGrid"></div>
                <div class="feedback" id="feedbackArea">💡 选择一个选项开始</div>
                <div class="flex-center mt-8">
                    <button class="next-btn" id="nextBtn" disabled>下一题 →</button>
                </div>
                <div id="resultArea" class="result-box hidden">
                    <div class="big-icon" id="resultIcon">🎉</div>
                    <div class="result-title" id="resultTitle">完成！</div>
                    <div class="result-stars" id="resultStars">⭐⭐⭐</div>
                    <div class="result-score" id="resultScore">50 / 50</div>
                    <div class="result-detail" id="resultDetail">太棒了，全部答对！</div>
                    <button class="next-btn" id="retryBtn" style="max-width:160px;">🔄 再来一轮</button>
                </div>

                <!-- 展示型模块（词卡、自然拼读） -->
                <div id="displayArea" class="hidden" style="margin-top:20px;">
                    <div class="mode-selector" id="modeSelector">
                        <button class="mode-btn active" data-mode="random">🎲 抽选学生</button>
                        <button class="mode-btn" data-mode="group">👥 集体练习</button>
                    </div>
                    <div class="card-display" id="cardDisplay">
                        <div class="student-name" id="studentDisplay">👤 点击“生成”开始</div>
                        <div class="big-card" id="bigCard">b</div>
                        <div class="example" id="exampleCard">bā</div>
                    </div>
                    <div class="control-buttons">
                        <button id="generateDisplayBtn">🔄 随机生成</button>
                        <button id="speakDisplayBtn">🔊 朗读</button>
                    </div>
                    <div class="info-feedback" id="displayFeedback">💡 点击“随机生成”开始练习</div>
                </div>
            </div>
        </div>

    </div>

    <script>
        // ================================================================
        //  词库（同前，为节省篇幅略去，实际完整保留）
        // ================================================================
        const INITIALS = [
            { initial: 'b', example: 'bā' }, { initial: 'p', example: 'pā' },
            { initial: 'm', example: 'mā' }, { initial: 'f', example: 'fā' },
            { initial: 'd', example: 'dā' }, { initial: 't', example: 'tā' },
            { initial: 'n', example: 'nā' }, { initial: 'l', example: 'lā' },
            { initial: 'g', example: 'gā' }, { initial: 'k', example: 'kā' },
            { initial: 'h', example: 'hā' }, { initial: 'j', example: 'jī' },
            { initial: 'q', example: 'qī' }, { initial: 'x', example: 'xī' },
            { initial: 'zh', example: 'zhā' }, { initial: 'ch', example: 'chā' },
            { initial: 'sh', example: 'shā' }, { initial: 'r', example: 'rì' },
            { initial: 'z', example: 'zā' }, { initial: 'c', example: 'cā' },
            { initial: 's', example: 'sā' }, { initial: 'y', example: 'yā' },
            { initial: 'w', example: 'wā' },
        ];
        const FINALS = [
            { final: 'a', example: 'ā' }, { final: 'o', example: 'ō' },
            { final: 'e', example: 'ē' }, { final: 'i', example: 'ī' },
            { final: 'u', example: 'ū' }, { final: 'ü', example: 'ǖ' },
            { final: 'ai', example: 'āi' }, { final: 'ei', example: 'ēi' },
            { final: 'ui', example: 'uī' }, { final: 'ao', example: 'āo' },
            { final: 'ou', example: 'ōu' }, { final: 'iu', example: 'iū' },
            { final: 'ie', example: 'iē' }, { final: 'üe', example: 'üē' },
            { final: 'er', example: 'ēr' }, { final: 'an', example: 'ān' },
            { final: 'en', example: 'ēn' }, { final: 'in', example: 'īn' },
            { final: 'un', example: 'ūn' }, { final: 'ün', example: 'ǖn' },
            { final: 'ang', example: 'āng' }, { final: 'eng', example: 'ēng' },
            { final: 'ing', example: 'īng' }, { final: 'ong', example: 'ōng' },
        ];
        const SINGLE_WORDS = [
            { text: '你', pinyin: 'nǐ', tone: 3, meaning: '你' },
            { text: '我', pinyin: 'wǒ', tone: 3, meaning: '我' },
            { text: '他', pinyin: 'tā', tone: 1, meaning: '他' },
            { text: '她', pinyin: 'tā', tone: 1, meaning: '她' },
            { text: '们', pinyin: 'men', tone: 0, meaning: '们' },
            { text: '老', pinyin: 'lǎo', tone: 3, meaning: '老' },
            { text: '师', pinyin: 'shī', tone: 1, meaning: '师' },
            { text: '您', pinyin: 'nín', tone: 2, meaning: '您' },
            { text: '再', pinyin: 'zài', tone: 4, meaning: '再' },
            { text: '见', pinyin: 'jiàn', tone: 4, meaning: '见' },
            { text: '好', pinyin: 'hǎo', tone: 3, meaning: '好' },
            { text: '大', pinyin: 'dà', tone: 4, meaning: '大' },
            { text: '学', pinyin: 'xué', tone: 2, meaning: '学' },
            { text: '生', pinyin: 'shēng', tone: 1, meaning: '生' },
            { text: '中', pinyin: 'zhōng', tone: 1, meaning: '中' },
            { text: '国', pinyin: 'guó', tone: 2, meaning: '国' },
            { text: '人', pinyin: 'rén', tone: 2, meaning: '人' },
            { text: '爱', pinyin: 'ài', tone: 4, meaning: '爱' },
            { text: '心', pinyin: 'xīn', tone: 1, meaning: '心' },
            { text: '春', pinyin: 'chūn', tone: 1, meaning: '春' },
            { text: '天', pinyin: 'tiān', tone: 1, meaning: '天' },
            { text: '明', pinyin: 'míng', tone: 2, meaning: '明' },
            { text: '月', pinyin: 'yuè', tone: 4, meaning: '月' },
            { text: '水', pinyin: 'shuǐ', tone: 3, meaning: '水' },
            { text: '火', pinyin: 'huǒ', tone: 3, meaning: '火' },
            { text: '山', pinyin: 'shān', tone: 1, meaning: '山' },
            { text: '石', pinyin: 'shí', tone: 2, meaning: '石' },
            { text: '田', pinyin: 'tián', tone: 2, meaning: '田' },
            { text: '林', pinyin: 'lín', tone: 2, meaning: '林' },
            { text: '风', pinyin: 'fēng', tone: 1, meaning: '风' },
            { text: '雨', pinyin: 'yǔ', tone: 3, meaning: '雨' },
            { text: '雪', pinyin: 'xuě', tone: 3, meaning: '雪' },
            { text: '云', pinyin: 'yún', tone: 2, meaning: '云' },
            { text: '花', pinyin: 'huā', tone: 1, meaning: '花' },
            { text: '草', pinyin: 'cǎo', tone: 3, meaning: '草' },
            { text: '树', pinyin: 'shù', tone: 4, meaning: '树' },
            { text: '木', pinyin: 'mù', tone: 4, meaning: '木' },
            { text: '江', pinyin: 'jiāng', tone: 1, meaning: '江' },
            { text: '河', pinyin: 'hé', tone: 2, meaning: '河' },
            { text: '海', pinyin: 'hǎi', tone: 3, meaning: '海' },
            { text: '湖', pinyin: 'hú', tone: 2, meaning: '湖' },
            { text: '日', pinyin: 'rì', tone: 4, meaning: '日' },
            { text: '星', pinyin: 'xīng', tone: 1, meaning: '星' },
            { text: '光', pinyin: 'guāng', tone: 1, meaning: '光' },
            { text: '亮', pinyin: 'liàng', tone: 4, meaning: '亮' },
            { text: '白', pinyin: 'bái', tone: 2, meaning: '白' },
            { text: '黑', pinyin: 'hēi', tone: 1, meaning: '黑' },
            { text: '红', pinyin: 'hóng', tone: 2, meaning: '红' },
            { text: '绿', pinyin: 'lǜ', tone: 4, meaning: '绿' },
            { text: '蓝', pinyin: 'lán', tone: 2, meaning: '蓝' },
            { text: '黄', pinyin: 'huáng', tone: 2, meaning: '黄' },
            { text: '青', pinyin: 'qīng', tone: 1, meaning: '青' },
            { text: '紫', pinyin: 'zǐ', tone: 3, meaning: '紫' },
            { text: '粉', pinyin: 'fěn', tone: 3, meaning: '粉' },
            { text: '灰', pinyin: 'huī', tone: 1, meaning: '灰' },
            { text: '金', pinyin: 'jīn', tone: 1, meaning: '金' },
            { text: '银', pinyin: 'yín', tone: 2, meaning: '银' },
            { text: '铜', pinyin: 'tóng', tone: 2, meaning: '铜' },
            { text: '铁', pinyin: 'tiě', tone: 3, meaning: '铁' },
            { text: '钢', pinyin: 'gāng', tone: 1, meaning: '钢' },
            { text: '森', pinyin: 'sēn', tone: 1, meaning: '森' },
            { text: '川', pinyin: 'chuān', tone: 1, meaning: '川' },
            { text: '流', pinyin: 'liú', tone: 2, meaning: '流' },
            { text: '动', pinyin: 'dòng', tone: 4, meaning: '动' },
            { text: '静', pinyin: 'jìng', tone: 4, meaning: '静' },
            { text: '安', pinyin: 'ān', tone: 1, meaning: '安' },
            { text: '全', pinyin: 'quán', tone: 2, meaning: '全' },
            { text: '部', pinyin: 'bù', tone: 4, meaning: '部' },
            { text: '分', pinyin: 'fēn', tone: 1, meaning: '分' },
            { text: '子', pinyin: 'zǐ', tone: 3, meaning: '子' },
            { text: '女', pinyin: 'nǚ', tone: 3, meaning: '女' },
            { text: '男', pinyin: 'nán', tone: 2, meaning: '男' },
            { text: '父', pinyin: 'fù', tone: 4, meaning: '父' },
            { text: '母', pinyin: 'mǔ', tone: 3, meaning: '母' },
            { text: '儿', pinyin: 'ér', tone: 2, meaning: '儿' },
            { text: '孙', pinyin: 'sūn', tone: 1, meaning: '孙' },
            { text: '爷', pinyin: 'yé', tone: 2, meaning: '爷' },
            { text: '奶', pinyin: 'nǎi', tone: 3, meaning: '奶' },
        ];
        const uniqueMap = new Map();
        SINGLE_WORDS.forEach(w => { if (!uniqueMap.has(w.text)) uniqueMap.set(w.text, w); });
        const SINGLE_WORDS_UNIQUE = Array.from(uniqueMap.values());
        const SPECIFIED_WORDS = [
            { text: '你', pinyin: 'nǐ', tone: 3, meaning: '你' },
            { text: '我', pinyin: 'wǒ', tone: 3, meaning: '我' },
            { text: '他', pinyin: 'tā', tone: 1, meaning: '他' },
            { text: '她', pinyin: 'tā', tone: 1, meaning: '她' },
            { text: '们', pinyin: 'men', tone: 0, meaning: '们' },
            { text: '老', pinyin: 'lǎo', tone: 3, meaning: '老' },
            { text: '师', pinyin: 'shī', tone: 1, meaning: '师' },
            { text: '老师', pinyin: 'lǎoshī', tone: [3, 1], meaning: '老师' },
            { text: '您', pinyin: 'nín', tone: 2, meaning: '您' },
            { text: '再', pinyin: 'zài', tone: 4, meaning: '再' },
            { text: '见', pinyin: 'jiàn', tone: 4, meaning: '见' },
            { text: '再见', pinyin: 'zàijiàn', tone: [4, 4], meaning: '再见' },
        ];
        const COMPOUND_WORDS = [
            { text: '老师', pinyin: 'lǎoshī', meaning: '老师' },
            { text: '再见', pinyin: 'zàijiàn', meaning: '再见' },
            { text: '你好', pinyin: 'nǐhǎo', meaning: '你好' },
            { text: '我们', pinyin: 'wǒmen', meaning: '我们' },
            { text: '他们', pinyin: 'tāmen', meaning: '他们' },
            { text: '中国', pinyin: 'zhōngguó', meaning: '中国' },
            { text: '人民', pinyin: 'rénmín', meaning: '人民' },
            { text: '学习', pinyin: 'xuéxí', meaning: '学习' },
            { text: '学生', pinyin: 'xuésheng', meaning: '学生' },
            { text: '大学', pinyin: 'dàxué', meaning: '大学' },
            { text: '爱心', pinyin: 'àixīn', meaning: '爱心' },
            { text: '春天', pinyin: 'chūntiān', meaning: '春天' },
            { text: '明月', pinyin: 'míngyuè', meaning: '明月' },
            { text: '山水', pinyin: 'shānshuǐ', meaning: '山水' },
            { text: '风雨', pinyin: 'fēngyǔ', meaning: '风雨' },
            { text: '雪云', pinyin: 'xuěyún', meaning: '雪云' },
            { text: '花木', pinyin: 'huāmù', meaning: '花木' },
            { text: '江河', pinyin: 'jiānghé', meaning: '江河' },
            { text: '湖海', pinyin: 'húhǎi', meaning: '湖海' },
        ];
        const STUDENTS = [
            'BUGROVA ALENA', 'EVSIUKOVA DARINA', 'ERMILINA DARIA',
            'KIRIUSHKINA DARIA', 'KISLITSYNA ULIANA', 'KUZINA ALEKSANDRA',
            'LOGUTINA ALISA', 'MILEVSKII NIKOLAI', 'PASTUKHOVA ANASTASIIA',
            'UEISKII MAKSIM', 'YUFEROVA VERONIKA', 'BELOZEROV ILIA',
            'ALEKSEEVA MARIIA', 'KARA-SAL ELINA', 'MARFENKO VERONIKA',
            'CHUPALAEV AMIR', 'VORONKOV EGOR', 'KHOMIAKOV IVAN',
            'STOLIAROV ROMAN'
        ];

        // ================================================================
        //  工具函数
        // ================================================================
        function shuffle(arr) {
            for (let i = arr.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [arr[i], arr[j]] = [arr[j], arr[i]];
            }
            return arr;
        }

        function getDistractors(excludeItem, pool, n) {
            const candidates = pool.filter(w => w.text !== excludeItem.text && w.pinyin !== excludeItem.pinyin);
            shuffle(candidates);
            return candidates.slice(0, n);
        }

        function getNonNeutralSingles() {
            return SINGLE_WORDS_UNIQUE.filter(w => w.tone !== 0);
        }

        // ================================================================
        //  学生数据管理 (localStorage)
        // ================================================================
        function getStudents() {
            try { return JSON.parse(localStorage.getItem('pinyin_students')) || []; } catch { return []; }
        }

        function saveStudents(students) {
            localStorage.setItem('pinyin_students', JSON.stringify(students));
        }

        function addStudent(name) {
            const students = getStudents();
            if (students.find(s => s.name === name)) return false;
            students.push({ name, points: 0 });
            saveStudents(students);
            return true;
        }

        function getStudentPoints(name) {
            const s = getStudents().find(st => st.name === name);
            return s ? s.points : 0;
        }

        function addPoints(name, delta) {
            const students = getStudents();
            const s = students.find(st => st.name === name);
            if (s) { s.points += delta;
                saveStudents(students); return true; }
            return false;
        }

        function getInteractMode() { return localStorage.getItem('pinyin_interact') === 'true'; }

        function setInteractMode(val) { localStorage.setItem('pinyin_interact', String(val)); }

        function getCurrentStudent() { return localStorage.getItem('pinyin_current_student') || ''; }

        function setCurrentStudent(name) { localStorage.setItem('pinyin_current_student', name); }

        function getClassCode() { return localStorage.getItem('pinyin_class_code') || ''; }

        function setClassCode(code) { localStorage.setItem('pinyin_class_code', code); }

        function isCodeEnabled() { return localStorage.getItem('pinyin_code_enabled') === 'true'; }

        function setCodeEnabled(val) { localStorage.setItem('pinyin_code_enabled', String(val)); }

        function generateRandomCode() { return Math.floor(100000 + Math.random() * 900000).toString(); }

        // ================================================================
        //  应用状态
        // ================================================================
        const state = {
            currentExercise: null,
            questions: [],
            currentIndex: 0,
            score: 0,
            answered: false,
            totalQuestions: 50,
            isPlaying: false,
            displayMode: 'random',
            currentDisplayItem: null,
            currentPinyinGroup: [],
            initialQueue: [],
            finalQueue: [],
            initialIndex: 0,
            finalIndex: 0,
            interactMode: false,
            currentStudent: '',
            questionAdded: false,
        };

        // ================================================================
        //  DOM 引用
        // ================================================================
        const $ = (id) => document.getElementById(id);
        const getEl = (id) => document.getElementById(id);

        const courseListPage = getEl('courseListPage');
        const teacherPanel = getEl('teacherPanel');
        const studentJoin = getEl('studentJoin');
        const lessonContentPage = getEl('lessonContentPage');
        const practicePage = getEl('practicePage');
        const backToCourseBtn = getEl('backToCourseBtn');
        const backToLessonBtn = getEl('backToLessonBtn');
        const backFromTeacherBtn = getEl('backFromTeacherBtn');
        const backFromJoinBtn = getEl('backFromJoinBtn');
        const teacherPanelBtn = getEl('teacherPanelBtn');
        const studentJoinBtn = getEl('studentJoinBtn');
        const practiceTitle = getEl('practiceTitle');
        const progressText = getEl('progressText');
        const scoreText = getEl('scoreText');
        const progressFill = getEl('progressFill');
        const questionArea = getEl('questionArea');
        const optionsGrid = getEl('optionsGrid');
        const feedbackArea = getEl('feedbackArea');
        const nextBtn = getEl('nextBtn');
        const resultArea = getEl('resultArea');
        const resultIcon = getEl('resultIcon');
        const resultTitle = getEl('resultTitle');
        const resultStars = getEl('resultStars');
        const resultScore = getEl('resultScore');
        const resultDetail = getEl('resultDetail');
        const retryBtn = getEl('retryBtn');
        const displayArea = getEl('displayArea');
        const modeSelector = getEl('modeSelector');
        const studentDisplay = getEl('studentDisplay');
        const bigCard = getEl('bigCard');
        const exampleCard = getEl('exampleCard');
        const displayFeedback = getEl('displayFeedback');
        const generateDisplayBtn = getEl('generateDisplayBtn');
        const speakDisplayBtn = getEl('speakDisplayBtn');
        const modeBtns = document.querySelectorAll('.mode-btn');

        const interactToggle = getEl('interactToggle');
        const codeToggle = getEl('codeToggle');
        const generateCodeBtn = getEl('generateCodeBtn');
        const codeDisplay = getEl('codeDisplay');
        const studentTableBody = getEl('studentTableBody');
        const emptyStudentMsg = getEl('emptyStudentMsg');
        const studentCount = getEl('studentCount');
        const exportCsvBtn = getEl('exportCsvBtn');
        const pageLinkDisplay = getEl('pageLinkDisplay');
        const copyLinkBtn = getEl('copyLinkBtn');

        const joinStudentName = getEl('joinStudentName');
        const joinClassCode = getEl('joinClassCode');
        const joinClassBtn = getEl('joinClassBtn');
        const joinMessage = getEl('joinMessage');
        const qrcodeContainer = getEl('qrcode');
        const joinPageLink = getEl('joinPageLink');
        const copyJoinLinkBtn = getEl('copyJoinLinkBtn');

        const interactBar = getEl('interactBar');
        const studentSelector = getEl('studentSelector');
        const currentStudentPoints = getEl('currentStudentPoints');

        const globalJoinBtn = getEl('globalJoinBtn');
        const globalTeacherBtn = getEl('globalTeacherBtn');

        // ================================================================
        //  语音合成
        // ================================================================
        function speakText(text, callback) {
            if (!window.speechSynthesis) { if (callback) callback(); return; }
            window.speechSynthesis.cancel();
            const utterance = new SpeechSynthesisUtterance(text);
            utterance.lang = 'zh-CN';
            utterance.rate = 0.7;
            utterance.pitch = 1.0;
            utterance.volume = 1;
            utterance.onend = () => {
                state.isPlaying = false;
                const btn = document.querySelector('.audio-btn');
                if (btn) btn.classList.remove('playing');
                if (callback) callback();
            };
            utterance.onerror = () => {
                state.isPlaying = false;
                const btn = document.querySelector('.audio-btn');
                if (btn) btn.classList.remove('playing');
                if (callback) callback();
            };
            state.isPlaying = true;
            const btn = document.querySelector('.audio-btn');
            if (btn) btn.classList.add('playing');
            window.speechSynthesis.speak(utterance);
        }

        // ================================================================
        //  生成题目（选项随机）
        // ================================================================
        function generateQuestions(exercise, count = 50) {
            const questions = [];
            const usedSet = new Set();

            if (exercise === 'listen2pinyin') {
                const pool = getNonNeutralSingles();
                let attempts = 0;
                while (questions.length < count && attempts < 2000) {
                    attempts++;
                    shuffle(pool);
                    let added = false;
                    for (const item of pool) {
                        if (questions.length >= count) break;
                        const distractors = getDistractors(item, pool, 3);
                        const options = shuffle([item.pinyin, ...distractors.map(w => w.pinyin)]);
                        const key = item.text + '|' + options.join(',');
                        if (!usedSet.has(key)) {
                            usedSet.add(key);
                            questions.push({
                                correct: item,
                                display: null,
                                displayType: 'audio_only',
                                options: options,
                                correctAnswer: item.pinyin,
                                meaning: item.meaning,
                                audioText: item.text,
                                exercise: exercise,
                            });
                            added = true;
                        }
                    }
                    if (!added && questions.length < count) {
                        usedSet.clear();
                        questions.forEach(q => {
                            const k = q.correct.text + '|' + q.options.join(',');
                            usedSet.add(k);
                        });
                    }
                }
            } else if (exercise === 'listen2tone') {
                const pool = getNonNeutralSingles();
                let attempts = 0;
                while (questions.length < count && attempts < 2000) {
                    attempts++;
                    shuffle(pool);
                    let added = false;
                    for (const item of pool) {
                        if (questions.length >= count) break;
                        const opts = shuffle([1, 2, 3, 4]);
                        const key = item.text + '|' + opts.join(',');
                        if (!usedSet.has(key)) {
                            usedSet.add(key);
                            questions.push({
                                correct: item,
                                display: null,
                                displayType: 'audio_only',
                                options: opts,
                                correctAnswer: item.tone,
                                meaning: item.meaning,
                                audioText: item.text,
                                exercise: exercise,
                            });
                            added = true;
                        }
                    }
                    if (!added && questions.length < count) {
                        usedSet.clear();
                        questions.forEach(q => {
                            const k = q.correct.text + '|' + q.options.join(',');
                            usedSet.add(k);
                        });
                    }
                }
            } else if (exercise === 'char2pinyin') {
                const pool = SPECIFIED_WORDS;
                let attempts = 0;
                while (questions.length < count && attempts < 1000) {
                    attempts++;
                    shuffle(pool);
                    let added = false;
                    for (const item of pool) {
                        if (questions.length >= count) break;
                        const distractors = getDistractors(item, pool, 3);
                        let extraPool = SINGLE_WORDS_UNIQUE.filter(w => w.pinyin !== item.pinyin && !distractors.some(d => d
                            .pinyin === w.pinyin));
                        shuffle(extraPool);
                        while (distractors.length < 3 && extraPool.length > 0) {
                            distractors.push(extraPool.pop());
                        }
                        const options = shuffle([item.pinyin, ...distractors.map(w => w.pinyin)]);
                        const key = item.text + '|' + options.join(',');
                        if (!usedSet.has(key)) {
                            usedSet.add(key);
                            questions.push({
                                correct: item,
                                display: item.text,
                                displayType: 'char',
                                options: options,
                                correctAnswer: item.pinyin,
                                meaning: item.meaning,
                                audioText: null,
                                exercise: exercise,
                            });
                            added = true;
                        }
                    }
                    if (!added && questions.length < count) {
                        usedSet.clear();
                        questions.forEach(q => {
                            const k = q.correct.text + '|' + q.options.join(',');
                            usedSet.add(k);
                        });
                    }
                }
            } else if (exercise === 'listen2compound') {
                const pool = COMPOUND_WORDS;
                let attempts = 0;
                while (questions.length < count && attempts < 1000) {
                    attempts++;
                    shuffle(pool);
                    let added = false;
                    for (const item of pool) {
                        if (questions.length >= count) break;
                        const distractors = getDistractors(item, pool, 3);
                        let extraPool = SINGLE_WORDS_UNIQUE.filter(w => w.pinyin !== item.pinyin && !distractors.some(d => d
                            .pinyin === w.pinyin));
                        shuffle(extraPool);
                        while (distractors.length < 3 && extraPool.length > 0) {
                            distractors.push(extraPool.pop());
                        }
                        const options = shuffle([item.pinyin, ...distractors.map(w => w.pinyin)]);
                        const key = item.text + '|' + options.join(',');
                        if (!usedSet.has(key)) {
                            usedSet.add(key);
                            questions.push({
                                correct: item,
                                display: item.text,
                                displayType: 'char',
                                options: options,
                                correctAnswer: item.pinyin,
                                meaning: item.meaning,
                                audioText: item.text,
                                exercise: exercise,
                            });
                            added = true;
                        }
                    }
                    if (!added && questions.length < count) {
                        usedSet.clear();
                        questions.forEach(q => {
                            const k = q.correct.text + '|' + q.options.join(',');
                            usedSet.add(k);
                        });
                    }
                }
            }

            while (questions.length < count) {
                const fallback = getNonNeutralSingles()[0] || { text: '你', pinyin: 'nǐ', tone: 3, meaning: '你' };
                const opts = shuffle([1, 2, 3, 4]);
                questions.push({
                    correct: fallback,
                    display: null,
                    displayType: 'audio_only',
                    options: opts,
                    correctAnswer: fallback.tone,
                    meaning: fallback.meaning,
                    audioText: fallback.text,
                    exercise: exercise,
                });
            }
            return shuffle(questions).slice(0, count);
        }

        // ================================================================
        //  渲染题目
        // ================================================================
        const EXERCISE_NAMES = {
            'listen2pinyin': '🎧 听音选拼音',
            'listen2tone': '🔊 听音选声调',
            'char2pinyin': '✍️ 看汉字选拼音',
            'listen2compound': '🔥 挑战·听词选拼音',
        };

        function renderQuestion() {
            const q = state.questions[state.currentIndex];
            if (!q) {
                if (questionArea) questionArea.innerHTML = '<div class="hint-text">⚠️ 题目生成失败，请返回重试</div>';
                if (optionsGrid) optionsGrid.innerHTML = '';
                if (feedbackArea) { feedbackArea.className = 'feedback';
                    feedbackArea.innerHTML = '💡 请重新进入模块'; }
                if (nextBtn) nextBtn.disabled = true;
                return;
            }

            const total = state.questions.length;
            if (progressText) progressText.textContent = `${state.currentIndex + 1} / ${total}`;
            if (scoreText) scoreText.textContent = `✓ ${state.score}`;
            if (progressFill) progressFill.style.width = `${((state.currentIndex) / total) * 100}%`;

            if (resultArea) resultArea.classList.add('hidden');
            if (nextBtn) nextBtn.disabled = true;
            if (feedbackArea) {
                feedbackArea.className = 'feedback';
                feedbackArea.innerHTML = '💡 选择一个选项';
            }
            if (displayArea) displayArea.classList.add('hidden');
            state.questionAdded = false;

            // 更新互动栏（是否显示取决于学生列表和互动模式）
            updateInteractBar();

            let displayHtml = '';
            if (q.displayType === 'char') {
                displayHtml = `<div class="display-char">${q.display}</div>`;
                if (q.exercise === 'char2pinyin') {
                    displayHtml += `<div class="hint-text">👆 选择正确的拼音</div>`;
                } else if (q.exercise === 'listen2compound') {
                    displayHtml += `<div class="hint-text">👆 听词发音，选完整拼音</div>`;
                }
            } else if (q.displayType === 'audio_only') {
                if (q.exercise === 'listen2tone') {
                    displayHtml = `<div class="hint-text" style="font-size:1.2rem;">🔊 听发音，选择正确的声调符号</div>`;
                } else {
                    displayHtml = `<div class="hint-text" style="font-size:1.2rem;">🔊 听发音，选择正确的拼音</div>`;
                }
            }

            let audioHtml = '';
            if (q.audioText) {
                audioHtml = `
                    <button class="audio-btn" id="playAudioBtn" title="点击播放发音">🔊</button>
                `;
            }

            if (questionArea) {
                questionArea.innerHTML = `
                    ${displayHtml}
                    ${audioHtml}
                `;
            }

            const audioBtn = document.getElementById('playAudioBtn');
            if (audioBtn) {
                audioBtn.addEventListener('click', () => {
                    if (state.isPlaying) {
                        window.speechSynthesis.cancel();
                        state.isPlaying = false;
                        audioBtn.classList.remove('playing');
                        return;
                    }
                    speakText(q.audioText, () => {
                        audioBtn.classList.remove('playing');
                    });
                });
            }

            if (optionsGrid) {
                optionsGrid.innerHTML = '';
                q.options.forEach((opt, idx) => {
                    const btn = document.createElement('button');
                    btn.className = 'opt-btn';
                    btn.dataset.index = idx;
                    let label = opt;
                    if (typeof opt === 'number' && q.exercise === 'listen2tone') {
                        const symbols = { 1: 'ˉ', 2: 'ˊ', 3: 'ˇ', 4: 'ˋ' };
                        label = symbols[opt] || opt;
                        btn.dataset.value = opt;
                    } else {
                        btn.dataset.value = opt;
                        label = opt;
                    }
                    btn.innerHTML = label;
                    btn.addEventListener('click', () => {
                        handleOptionClick(btn, q);
                    });
                    optionsGrid.appendChild(btn);
                });
            }

            state.answered = false;
            if (nextBtn) nextBtn.disabled = true; // 初始不可点，回答后启用
        }

        // ================================================================
        //  处理选项点击
        // ================================================================
        function handleOptionClick(btn, q) {
            if (state.answered) return;
            const selectedValue = btn.dataset.value;
            let isCorrect = false;
            if (q.exercise === 'listen2tone') {
                isCorrect = (parseInt(selectedValue) === q.correctAnswer);
            } else {
                isCorrect = (selectedValue === q.correctAnswer);
            }

            state.answered = true;

            const allBtns = optionsGrid.querySelectorAll('.opt-btn');
            allBtns.forEach(b => b.classList.add('disabled'));

            allBtns.forEach((b) => {
                const val = b.dataset.value;
                let isCorrectOpt = false;
                if (q.exercise === 'listen2tone') {
                    isCorrectOpt = (parseInt(val) === q.correctAnswer);
                } else {
                    isCorrectOpt = (val === q.correctAnswer);
                }
                if (isCorrectOpt) {
                    b.classList.add('correct');
                } else if (b === btn && !isCorrect) {
                    b.classList.add('wrong');
                }
            });

            if (isCorrect) {
                state.score++;
                if (scoreText) scoreText.textContent = `✓ ${state.score}`;
                // 互动积分：只有在互动模式开启、有当前学生、且本题未加过分时
                if (state.interactMode && state.currentStudent && !state.questionAdded) {
                    const success = addPoints(state.currentStudent, 1);
                    if (success) {
                        state.questionAdded = true;
                        updateInteractBar();
                    }
                }
            }

            const meaningText = q.meaning ? ` · ${q.meaning}` : '';
            const charText = q.correct.text ? `「${q.correct.text}」` : '';
            let correctDisplay = q.correctAnswer;
            if (q.exercise === 'listen2tone') {
                const symbols = { 1: 'ˉ', 2: 'ˊ', 3: 'ˇ', 4: 'ˋ' };
                correctDisplay = symbols[q.correctAnswer] || q.correctAnswer;
            }
            if (feedbackArea) {
                if (isCorrect) {
                    feedbackArea.className = 'feedback correct';
                    feedbackArea.innerHTML = `
                        ✅ 回答正确！ ${charText} ${meaningText}
                        <span class="meaning">${q.meaning ? '含义：' + q.meaning : ''}</span>
                    `;
                } else {
                    feedbackArea.className = 'feedback wrong';
                    feedbackArea.innerHTML = `
                        ❌ 回答错误。正确答案是：<strong>${correctDisplay}</strong>
                        ${charText} ${meaningText}
                        <span class="meaning">${q.meaning ? '含义：' + q.meaning : ''}</span>
                    `;
                }
            }

            if (nextBtn) nextBtn.disabled = false;
            const total = state.questions.length;
            if (progressFill) progressFill.style.width = `${((state.currentIndex + 1) / total) * 100}%`;
        }

        // ================================================================
        //  下一题 / 完成
        // ================================================================
        function goToNext() {
            if (nextBtn && nextBtn.disabled) return;
            state.currentIndex++;
            if (state.currentIndex >= state.questions.length) {
                showResult();
            } else {
                renderQuestion();
            }
        }

        function showResult() {
            const total = state.questions.length;
            const correct = state.score;
            const pct = correct / total;

            if (questionArea) questionArea.innerHTML = '';
            if (optionsGrid) optionsGrid.innerHTML = '';
            if (feedbackArea) { feedbackArea.className = 'feedback';
                feedbackArea.innerHTML = ''; }
            if (nextBtn) nextBtn.disabled = true;
            if (progressFill) progressFill.style.width = '100%';
            if (displayArea) displayArea.classList.add('hidden');
            if (interactBar) interactBar.classList.add('hidden');

            if (resultArea) {
                resultArea.classList.remove('hidden');
                let icon, stars, title, detail;
                if (pct === 1) {
                    icon = '🏆';
                    stars = '⭐⭐⭐';
                    title = '完美通关！';
                    detail = '太棒了，全部答对！你是拼音小达人！';
                } else if (pct >= 0.8) {
                    icon = '🌟';
                    stars = '⭐⭐';
                    title = '非常优秀！';
                    detail = `答对 ${correct}/${total}，继续保持！`;
                } else if (pct >= 0.6) {
                    icon = '💪';
                    stars = '⭐';
                    title = '还不错！';
                    detail = `答对 ${correct}/${total}，多加练习会更好！`;
                } else {
                    icon = '📚';
                    stars = '☆';
                    title = '继续加油！';
                    detail = `答对 ${correct}/${total}，多多复习，你可以的！`;
                }
                if (resultIcon) resultIcon.textContent = icon;
                if (resultStars) resultStars.textContent = stars;
                if (resultTitle) resultTitle.textContent = title;
                if (resultScore) resultScore.textContent = `${correct} / ${total}`;
                if (resultDetail) resultDetail.textContent = detail;
                if (progressText) progressText.textContent = `${total} / ${total}`;
            }
        }

        // ================================================================
        //  展示型模块
        // ================================================================
        function initDisplayModule(exercise) {
            if (questionArea) questionArea.innerHTML = '';
            if (optionsGrid) optionsGrid.innerHTML = '';
            if (feedbackArea) { feedbackArea.className = 'feedback';
                feedbackArea.innerHTML = ''; }
            if (nextBtn) nextBtn.disabled = true;
            if (resultArea) resultArea.classList.add('hidden');
            if (displayArea) displayArea.classList.remove('hidden');
            if (interactBar) interactBar.classList.add('hidden');
            if (progressText) progressText.textContent = '词卡';
            if (scoreText) scoreText.textContent = '';
            if (progressFill) progressFill.style.width = '0%';

            if (exercise === 'initials') {
                if (practiceTitle) practiceTitle.textContent = '🔤 声母词卡';
                if (modeSelector) modeSelector.classList.add('hidden');
                if (state.initialQueue.length === 0) {
                    state.initialQueue = shuffle([...INITIALS]);
                    state.initialIndex = 0;
                }
            } else if (exercise === 'finals') {
                if (practiceTitle) practiceTitle.textContent = '🔡 韵母词卡';
                if (modeSelector) modeSelector.classList.add('hidden');
                if (state.finalQueue.length === 0) {
                    state.finalQueue = shuffle([...FINALS]);
                    state.finalIndex = 0;
                }
            } else if (exercise === 'natural') {
                if (practiceTitle) practiceTitle.textContent = '📣 自然拼读';
                if (modeSelector) modeSelector.classList.remove('hidden');
                state.displayMode = 'random';
                document.querySelectorAll('.mode-btn').forEach(btn => {
                    btn.classList.toggle('active', btn.dataset.mode === 'random');
                });
            }

            state.currentExercise = exercise;
            generateDisplayItem();
        }

        function generateDisplayItem() {
            const ex = state.currentExercise;
            if (ex === 'initials') {
                if (state.initialQueue.length === 0) {
                    state.initialQueue = shuffle([...INITIALS]);
                    state.initialIndex = 0;
                }
                const item = state.initialQueue[state.initialIndex];
                state.currentDisplayItem = item;
                if (bigCard) bigCard.textContent = item.initial;
                if (exampleCard) exampleCard.textContent = item.example;
                if (studentDisplay) studentDisplay.textContent = `🔤 声母 (${state.initialIndex + 1}/${state.initialQueue.length})`;
                if (displayFeedback) displayFeedback.textContent = `声母：${item.initial}，示例音节：${item.example}`;
                state.initialIndex = (state.initialIndex + 1) % state.initialQueue.length;
            } else if (ex === 'finals') {
                if (state.finalQueue.length === 0) {
                    state.finalQueue = shuffle([...FINALS]);
                    state.finalIndex = 0;
                }
                const item = state.finalQueue[state.finalIndex];
                state.currentDisplayItem = item;
                if (bigCard) bigCard.textContent = item.final;
                if (exampleCard) exampleCard.textContent = item.example;
                if (studentDisplay) studentDisplay.textContent = `🔡 韵母 (${state.finalIndex + 1}/${state.finalQueue.length})`;
                if (displayFeedback) displayFeedback.textContent = `韵母：${item.final}，示例音节：${item.example}`;
                state.finalIndex = (state.finalIndex + 1) % state.finalQueue.length;
            } else if (ex === 'natural') {
                const pool = getNonNeutralSingles();
                shuffle(pool);
                const group = pool.slice(0, 3).map(w => w.pinyin);
                state.currentPinyinGroup = group;
                if (bigCard) bigCard.textContent = group.join('  ');
                if (exampleCard) exampleCard.textContent = '';
                if (state.displayMode === 'random') {
                    const student = STUDENTS[Math.floor(Math.random() * STUDENTS.length)];
                    if (studentDisplay) studentDisplay.textContent = `👤 ${student}`;
                    if (displayFeedback) displayFeedback.textContent = `🎯 ${student}，请朗读以下拼音：`;
                } else {
                    if (studentDisplay) studentDisplay.textContent = '👥 集体练习';
                    if (displayFeedback) displayFeedback.textContent = '🗣️ 大家一起朗读以下拼音：';
                }
            }
        }

        function speakDisplayItem() {
            const ex = state.currentExercise;
            let text = '';
            if (ex === 'initials' && state.currentDisplayItem) {
                text = state.currentDisplayItem.example;
            } else if (ex === 'finals' && state.currentDisplayItem) {
                text = state.currentDisplayItem.example;
            } else if (ex === 'natural' && state.currentPinyinGroup.length > 0) {
                text = state.currentPinyinGroup.join(' ');
            }
            if (text) {
                speakText(text, () => {});
            }
        }

        // ================================================================
        //  互动栏更新
        // ================================================================
        function updateInteractBar() {
            const mode = getInteractMode();
            const students = getStudents();
            const current = getCurrentStudent();

            state.interactMode = mode;
            state.currentStudent = current;

            // 显示条件：互动模式开启 且 有学生 且 当前是测验模块
            const show = mode && students.length > 0 &&
                state.currentExercise && !['initials', 'finals', 'natural'].includes(state.currentExercise);

            if (show && interactBar && studentSelector) {
                interactBar.classList.remove('hidden');
                const sel = studentSelector;
                sel.innerHTML = '';
                students.forEach(s => {
                    const opt = document.createElement('option');
                    opt.value = s.name;
                    opt.textContent = s.name;
                    if (s.name === current) opt.selected = true;
                    sel.appendChild(opt);
                });
                if (current && currentStudentPoints) {
                    currentStudentPoints.textContent = `积分：${getStudentPoints(current)}`;
                } else if (currentStudentPoints) {
                    currentStudentPoints.textContent = '积分：0';
                }
                sel.onchange = function() {
                    const name = this.value;
                    setCurrentStudent(name);
                    state.currentStudent = name;
                    if (currentStudentPoints) currentStudentPoints.textContent = `积分：${getStudentPoints(name)}`;
                };
            } else {
                if (interactBar) interactBar.classList.add('hidden');
            }
        }

        // ================================================================
        //  教师控制台渲染
        // ================================================================
        function renderTeacherPanel() {
            const students = getStudents();
            const mode = getInteractMode();
            const code = getClassCode();
            const codeEnabled = isCodeEnabled();

            if (interactToggle) interactToggle.checked = mode;
            if (codeToggle) codeToggle.checked = codeEnabled;
            if (codeDisplay) codeDisplay.textContent = code || '——';
            if (pageLinkDisplay) pageLinkDisplay.textContent = window.location.href;

            if (studentTableBody) {
                const tbody = studentTableBody;
                tbody.innerHTML = '';
                if (students.length === 0) {
                    if (emptyStudentMsg) emptyStudentMsg.style.display = 'block';
                    if (studentTableBody) studentTableBody.style.display = 'none';
                } else {
                    if (emptyStudentMsg) emptyStudentMsg.style.display = 'none';
                    if (studentTableBody) studentTableBody.style.display = 'table-row-group';
                    students.forEach(s => {
                        const tr = document.createElement('tr');
                        tr.innerHTML = `<td>${s.name}</td><td>${s.points}</td>`;
                        tbody.appendChild(tr);
                    });
                }
            }
            if (studentCount) studentCount.textContent = `当前学生：${students.length} 人`;
        }

        function exportCsv() {
            const students = getStudents();
            if (students.length === 0) { alert('暂无学生数据可导出。'); return; }
            let csv = '姓名,积分\n';
            students.forEach(s => { csv += `${s.name},${s.points}\n`; });
            const blob = new Blob(['\uFEFF' + csv], { type: 'text/csv;charset=utf-8;' });
            const link = document.createElement('a');
            link.href = URL.createObjectURL(blob);
            link.download = '学生积分.csv';
            link.click();
            URL.revokeObjectURL(link.href);
        }

        // ================================================================
        //  启动练习
        // ================================================================
        function startExercise(exercise) {
            state.currentExercise = exercise;
            state.score = 0;
            state.currentIndex = 0;
            state.answered = false;

            // 隐藏所有页面
            document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
            if (practicePage) practicePage.classList.add('active');

            if (exercise === 'initials' || exercise === 'finals' || exercise === 'natural') {
                initDisplayModule(exercise);
                return;
            }

            if (displayArea) displayArea.classList.add('hidden');
            if (modeSelector) modeSelector.classList.add('hidden');
            const questions = generateQuestions(exercise, 50);
            state.questions = questions;
            state.totalQuestions = questions.length;

            if (practiceTitle) practiceTitle.textContent = EXERCISE_NAMES[exercise] || '练习';
            if (resultArea) resultArea.classList.add('hidden');
            if (nextBtn) nextBtn.disabled = true;
            renderQuestion();
            // 互动栏更新
            updateInteractBar();
        }

        // ================================================================
        //  页面切换
        // ================================================================
        function showPage(pageId) {
            document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
            const target = document.getElementById(pageId);
            if (target) target.classList.add('active');
        }

        function showCourseList() {
            if (window.speechSynthesis) { window.speechSynthesis.cancel();
                state.isPlaying = false; }
            showPage('courseListPage');
            state.currentExercise = null;
            state.questions = [];
            state.currentIndex = 0;
            state.score = 0;
            state.answered = false;
            if (displayArea) displayArea.classList.add('hidden');
            if (modeSelector) modeSelector.classList.add('hidden');
            if (interactBar) interactBar.classList.add('hidden');
        }

        function showLessonContent() {
            if (window.speechSynthesis) { window.speechSynthesis.cancel();
                state.isPlaying = false; }
            showPage('lessonContentPage');
            state.currentExercise = null;
            state.questions = [];
            state.currentIndex = 0;
            state.score = 0;
            state.answered = false;
            if (displayArea) displayArea.classList.add('hidden');
            if (modeSelector) modeSelector.classList.add('hidden');
            if (interactBar) interactBar.classList.add('hidden');
        }

        function goBackToLesson() {
            if (window.speechSynthesis) { window.speechSynthesis.cancel();
                state.isPlaying = false; }
            showPage('lessonContentPage');
            state.currentExercise = null;
            state.questions = [];
            state.currentIndex = 0;
            state.score = 0;
            state.answered = false;
            if (displayArea) displayArea.classList.add('hidden');
            if (modeSelector) modeSelector.classList.add('hidden');
            if (interactBar) interactBar.classList.add('hidden');
        }

        function showTeacherPanel() {
            if (window.speechSynthesis) { window.speechSynthesis.cancel();
                state.isPlaying = false; }
            showPage('teacherPanel');
            renderTeacherPanel();
        }

        function showStudentJoin() {
            if (window.speechSynthesis) { window.speechSynthesis.cancel();
                state.isPlaying = false; }
            showPage('studentJoin');
            setTimeout(() => {
                if (qrcodeContainer) {
                    qrcodeContainer.innerHTML = '';
                    try {
                        new QRCode(qrcodeContainer, {
                            text: window.location.href,
                            width: 200,
                            height: 200,
                            colorDark: '#3f2b21',
                            colorLight: '#ffffff',
                            correctLevel: QRCode.CorrectLevel.H
                        });
                    } catch (e) { console.warn('QRCode库加载失败，请检查网络'); }
                }
            }, 100);
            if (joinPageLink) joinPageLink.textContent = window.location.href;
        }

        // ================================================================
        //  事件绑定
        // ================================================================
        // 课程列表点击第一课
        document.querySelector('.course-grid')?.addEventListener('click', function(e) {
            const card = e.target.closest('.course-card.unlocked');
            if (card) {
                showLessonContent();
            }
        });

        // 第一课内容页练习卡片
        document.querySelector('#lessonContentPage .exercise-grid')?.addEventListener('click', function(e) {
            const card = e.target.closest('.ex-card');
            if (card) {
                const ex = card.dataset.ex;
                if (ex) startExercise(ex);
            }
        });

        // 返回按钮
        if (backToCourseBtn) backToCourseBtn.addEventListener('click', showCourseList);
        if (backToLessonBtn) backToLessonBtn.addEventListener('click', goBackToLesson);
        if (backFromTeacherBtn) backFromTeacherBtn.addEventListener('click', showCourseList);
        if (backFromJoinBtn) backFromJoinBtn.addEventListener('click', showCourseList);

        // 全局工具栏按钮
        if (globalJoinBtn) globalJoinBtn.addEventListener('click', showStudentJoin);
        if (globalTeacherBtn) globalTeacherBtn.addEventListener('click', showTeacherPanel);

        // 下一题
        if (nextBtn) nextBtn.addEventListener('click', goToNext);

        // 重试
        if (retryBtn) {
            retryBtn.addEventListener('click', () => {
                if (state.currentExercise) {
                    startExercise(state.currentExercise);
                }
            });
        }

        // 展示模块控制
        if (generateDisplayBtn) generateDisplayBtn.addEventListener('click', generateDisplayItem);
        if (speakDisplayBtn) speakDisplayBtn.addEventListener('click', speakDisplayItem);

        // 自然拼读模式切换
        modeBtns.forEach(btn => {
            btn.addEventListener('click', () => {
                modeBtns.forEach(b => b.classList.remove('active'));
                btn.classList.add('active');
                state.displayMode = btn.dataset.mode;
                if (state.currentExercise === 'natural') {
                    generateDisplayItem();
                }
            });
        });

        // 教师控制台
        if (interactToggle) {
            interactToggle.addEventListener('change', function() {
                setInteractMode(this.checked);
                renderTeacherPanel();
                // 如果当前在练习页且是测验模块，刷新互动栏
                if (practicePage && practicePage.classList.contains('active') && state.currentExercise && ![
                        'initials', 'finals', 'natural'
                    ].includes(state.currentExercise)) {
                    updateInteractBar();
                }
            });
        }

        if (codeToggle) {
            codeToggle.addEventListener('change', function() {
                setCodeEnabled(this.checked);
                renderTeacherPanel();
            });
        }

        if (generateCodeBtn) {
            generateCodeBtn.addEventListener('click', function() {
                const code = generateRandomCode();
                setClassCode(code);
                renderTeacherPanel();
            });
        }

        if (copyLinkBtn) {
            copyLinkBtn.addEventListener('click', function() {
                const url = window.location.href;
                navigator.clipboard?.writeText(url).then(() => {
                    alert('链接已复制！');
                }).catch(() => {
                    const input = document.createElement('input');
                    input.value = url;
                    document.body.appendChild(input);
                    input.select();
                    document.execCommand('copy');
                    input.remove();
                    alert('链接已复制！');
                });
            });
        }

        if (copyJoinLinkBtn) {
            copyJoinLinkBtn.addEventListener('click', function() {
                const url = window.location.href;
                navigator.clipboard?.writeText(url).then(() => {
                    alert('链接已复制！');
                }).catch(() => {
                    const input = document.createElement('input');
                    input.value = url;
                    document.body.appendChild(input);
                    input.select();
                    document.execCommand('copy');
                    input.remove();
                    alert('链接已复制！');
                });
            });
        }

        if (exportCsvBtn) exportCsvBtn.addEventListener('click', exportCsv);

        // 学生加入
        if (joinClassBtn) {
            joinClassBtn.addEventListener('click', () => {
                const name = joinStudentName ? joinStudentName.value.trim() : '';
                const code = joinClassCode ? joinClassCode.value.trim() : '';
                if (!name) {
                    if (joinMessage) { joinMessage.textContent = '⚠️ 请输入姓名';
                        joinMessage.className = 'join-message'; }
                    return;
                }
                if (isCodeEnabled()) {
                    const expected = getClassCode();
                    if (code !== expected) {
                        if (joinMessage) { joinMessage.textContent = '⚠️ 课堂码错误，请向老师获取正确的课堂码';
                            joinMessage.className = 'join-message'; }
                        return;
                    }
                }
                if (addStudent(name)) {
                    if (joinMessage) { joinMessage.textContent = `✅ ${name} 加入成功！`;
                        joinMessage.className = 'join-message success'; }
                    if (joinStudentName) joinStudentName.value = '';
                    if (joinClassCode) joinClassCode.value = '';
                    setCurrentStudent(name);
                    if (teacherPanel && teacherPanel.classList.contains('active')) renderTeacherPanel();
                    if (practicePage && practicePage.classList.contains('active')) {
                        updateInteractBar();
                    }
                } else {
                    if (joinMessage) { joinMessage.textContent = `⚠️ 姓名 “${name}” 已存在，请使用其他名字`;
                        joinMessage.className = 'join-message'; }
                }
            });
        }

        // 键盘事件
        document.addEventListener('keydown', (e) => {
            if (e.key === 'Enter' && nextBtn && !nextBtn.disabled && practicePage && practicePage.classList.contains(
                    'active') && state.currentExercise && !['initials', 'finals', 'natural'].includes(state
                    .currentExercise)) {
                goToNext();
            }
        });

        // 语音合成提示
        if (!window.speechSynthesis) {
            const hint = document.createElement('div');
            hint.style.cssText =
                'background:#fae8e3;padding:12px 16px;border-radius:16px;margin-top:12px;font-size:0.9rem;color:#7a3a2a;';
            hint.textContent = '⚠️ 您的浏览器不支持语音合成，听音练习将无法使用。请使用 Chrome、Edge 或 Safari 浏览器。';
            document.querySelector('.app-container')?.prepend(hint);
        }

        // 初始化
        state.interactMode = getInteractMode();
        state.currentStudent = getCurrentStudent();
        console.log('📚 《标准汉语会话360句1》第一课练习已加载！');
        console.log('✅ 所有练习默认可用，无需同步。开启互动模式后，学生答题可积分。');
    </script>

</body>
</html>
