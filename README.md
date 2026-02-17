<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <meta name="theme-color" content="#ff6b9d">
    <title>Yinyer Studio Pro v2.0 - Constructor Web Definitivo</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700;900&display=swap');
        
        * { 
            margin: 0; 
            padding: 0; 
            box-sizing: border-box; 
            -webkit-tap-highlight-color: transparent;
        }
        
        :root {
            --primary: #ff6b9d;
            --secondary: #c44569;
            --accent: #ffa502;
            --success: #26de81;
            --warning: #fed330;
            --danger: #fc5c65;
            --info: #45aaf2;
            --dark: #1e1e2e;
            --darker: #16161d;
            --text: #ffffff;
            --text-dim: #a4a4bf;
            --border: #2d2d44;
            --glass: rgba(255, 255, 255, 0.05);
        }

        body { 
            font-family: 'Poppins', -apple-system, sans-serif;
            background: linear-gradient(135deg, var(--darker) 0%, var(--dark) 100%); 
            color: var(--text); 
            height: 100vh; 
            overflow: hidden;
            position: relative;
        }

        .preloader {
            position: fixed;
            inset: 0;
            background: linear-gradient(135deg, #1e1e2e 0%, #16161d 100%);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            z-index: 10000;
            transition: opacity 0.5s, visibility 0.5s;
        }

        .preloader.hidden {
            opacity: 0;
            visibility: hidden;
            pointer-events: none;
        }

        .preloader-logo {
            width: 280px;
            height: 280px;
            background: white;
            border-radius: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 20px 60px rgba(0,0,0,0.5);
            margin-bottom: 40px;
            animation: float 3s ease-in-out infinite;
        }

        .logo-text {
            font-family: 'Poppins', sans-serif;
            font-size: 4rem;
            font-weight: 900;
            color: #000;
            position: relative;
        }

        .logo-text .play-icon {
            position: absolute;
            right: -45px;
            top: -10px;
            font-size: 3rem;
            color: #ff6b9d;
        }

        .logo-mp3 {
            font-size: 2rem;
            font-weight: 400;
            margin-top: -20px;
            color: #666;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-20px); }
        }

        .preloader-progress {
            width: 250px;
            height: 4px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            overflow: hidden;
            margin-bottom: 20px;
        }

        .preloader-progress-bar {
            height: 100%;
            background: linear-gradient(90deg, var(--primary), var(--accent));
            border-radius: 10px;
            width: 0%;
            animation: loading 2s ease-in-out forwards;
        }

        @keyframes loading {
            0% { width: 0%; }
            100% { width: 100%; }
        }

        .preloader-text {
            color: var(--text-dim);
            font-size: 0.9rem;
            font-weight: 600;
            animation: pulse 1.5s ease-in-out infinite;
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.5; }
        }

        .header { 
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            padding: 10px 15px;
            background: rgba(30, 30, 46, 0.98);
            backdrop-filter: blur(20px);
            border-bottom: 2px solid var(--primary);
            z-index: 1000;
            display: flex;
            align-items: center;
            justify-content: space-between;
            box-shadow: 0 2px 20px rgba(0,0,0,0.3);
        }
        
        .header-logo {
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .header-icon {
            font-size: 1.8rem;
        }

        .header-title { 
            font-size: 1rem; 
            background: linear-gradient(135deg, var(--primary), var(--accent));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            font-weight: 900;
            letter-spacing: 0.5px;
        }
        
        .header-subtitle {
            font-size: 0.6rem;
            color: var(--text-dim);
        }
        
        .header-actions {
            display: flex;
            gap: 6px;
        }

        .header-btn {
            padding: 6px 10px;
            background: var(--glass);
            border: 1px solid var(--border);
            border-radius: 8px;
            color: var(--text);
            font-size: 0.7rem;
            cursor: pointer;
            transition: all 0.2s;
            display: flex;
            align-items: center;
            gap: 4px;
            font-weight: 600;
            font-family: inherit;
        }

        .header-btn:active {
            transform: scale(0.95);
        }

        .header-btn:hover {
            background: var(--border);
            border-color: var(--primary);
        }

        .header-btn.ai {
            background: linear-gradient(135deg, var(--primary), var(--accent));
            color: white;
            animation: glow 2s infinite;
            border: none;
        }

        @keyframes glow {
            0%, 100% { box-shadow: 0 0 10px rgba(255, 107, 157, 0.5); }
            50% { box-shadow: 0 0 20px rgba(255, 107, 157, 0.8); }
        }

        .content-wrapper { 
            position: fixed;
            top: 80px;
            left: 0;
            right: 0;
            bottom: 70px;
            overflow-y: auto;
            -webkit-overflow-scrolling: touch;
            padding: 0 12px 20px;
        }
        
        .content-wrapper::-webkit-scrollbar { width: 3px; }
        .content-wrapper::-webkit-scrollbar-thumb { 
            background: var(--primary); 
            border-radius: 10px; 
        }

        .tab-content { 
            display: none; 
            animation: fadeIn 0.3s;
        }
        .tab-content.active { display: block; }

        @keyframes fadeIn { 
            from { opacity: 0; transform: translateY(10px); } 
            to { opacity: 1; transform: translateY(0); } 
        }

        .stats-bar {
            display: flex;
            gap: 10px;
            margin-bottom: 10px;
        }

        .stat-card {
            flex: 1;
            padding: 10px;
            background: var(--glass);
            border: 1px solid var(--border);
            border-radius: 8px;
            text-align: center;
        }

        .stat-value {
            font-size: 1.2rem;
            font-weight: 900;
            color: var(--primary);
        }

        .stat-label {
            font-size: 0.6rem;
            color: var(--text-dim);
            text-transform: uppercase;
            margin-top: 2px;
        }

        .section {
            margin-bottom: 10px;
        }

        .section-header {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 12px 14px;
            background: var(--glass);
            border: 1px solid var(--border);
            border-radius: 10px;
            cursor: pointer;
            user-select: none;
            transition: all 0.2s;
        }

        .section-header:active {
            transform: scale(0.98);
        }

        .section-header:hover {
            background: rgba(255, 255, 255, 0.08);
            border-color: var(--primary);
        }

        .section-header-left {
            display: flex;
            align-items: center;
            gap: 10px;
            flex: 1;
        }

        .section-icon { 
            font-size: 1.1rem; 
        }
        
        .section-title { 
            font-size: 0.75rem; 
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }
        
        .badge {
            padding: 2px 6px;
            background: var(--primary);
            color: white;
            border-radius: 8px;
            font-size: 0.6rem;
            font-weight: 700;
        }

        .badge.pro {
            background: linear-gradient(135deg, #ffd700, #ffed4e);
            color: #000;
        }

        .badge.new {
            background: var(--success);
        }

        .expand-icon { 
            font-size: 0.85rem; 
            transition: transform 0.3s;
            color: var(--text-dim);
        }
        
        .section-header.open .expand-icon { 
            transform: rotate(180deg); 
        }
        
        .section-content {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.3s ease;
        }
        
        .section-content.open { 
            max-height: 5000px;
        }

        .card { 
            background: var(--glass); 
            padding: 14px; 
            border-radius: 10px; 
            margin-top: 8px;
            border: 1px solid var(--border);
        }

        .card-title {
            font-size: 0.7rem;
            color: var(--primary);
            font-weight: 700;
            text-transform: uppercase;
            margin-bottom: 10px;
            display: flex;
            align-items: center;
            gap: 6px;
        }

        .field { 
            margin-bottom: 12px; 
        }
        
        .field-label { 
            display: flex;
            align-items: center;
            gap: 6px;
            font-size: 0.7rem; 
            color: var(--text-dim); 
            margin-bottom: 6px;
            font-weight: 600;
        }
        
        .field-input, 
        .field-textarea, 
        .field-select { 
            width: 100%; 
            padding: 10px 12px; 
            background: rgba(22, 22, 29, 0.8); 
            border: 1px solid var(--border); 
            border-radius: 8px; 
            color: var(--text); 
            font-size: 0.8rem;
            font-family: inherit;
            transition: all 0.2s;
        }

        .field-input:focus, 
        .field-textarea:focus, 
        .field-select:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(255, 107, 157, 0.1);
        }

        .field-textarea {
            min-height: 60px;
            resize: vertical;
        }

        .field-select {
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='12' viewBox='0 0 12 12'%3E%3Cpath fill='%23ff6b9d' d='M6 9L1 4h10z'/%3E%3C/svg%3E");
            background-repeat: no-repeat;
            background-position: right 12px center;
            padding-right: 35px;
            cursor: pointer;
        }

        .field-color {
            height: 45px;
            padding: 4px;
            cursor: pointer;
        }

        .field-range {
            width: 100%;
            height: 4px;
            background: var(--border);
            border-radius: 5px;
            outline: none;
            -webkit-appearance: none;
            cursor: pointer;
        }

        .field-range::-webkit-slider-thumb {
            -webkit-appearance: none;
            width: 16px;
            height: 16px;
            background: var(--primary);
            cursor: pointer;
            border-radius: 50%;
            box-shadow: 0 2px 8px rgba(255, 107, 157, 0.5);
            transition: all 0.2s;
        }

        .field-range::-webkit-slider-thumb:hover {
            transform: scale(1.2);
        }

        .range-value {
            color: var(--primary);
            font-weight: 700;
            font-size: 0.75rem;
            margin-top: 4px;
            display: block;
        }

        .toggle-group { 
            display: flex; 
            align-items: center; 
            justify-content: space-between; 
            padding: 10px 12px; 
            background: rgba(22, 22, 29, 0.5);
            border-radius: 8px;
            margin-bottom: 10px;
            border: 1px solid var(--border);
            transition: all 0.2s;
        }

        .toggle-group:hover {
            background: rgba(22, 22, 29, 0.7);
            border-color: var(--primary);
        }
        
        .toggle-label {
            font-size: 0.75rem;
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 6px;
        }
        
        .switch { 
            position: relative; 
            width: 40px; 
            height: 22px; 
        }
        
        .switch input { 
            opacity: 0; 
            width: 0; 
            height: 0; 
        }
        
        .slider { 
            position: absolute; 
            cursor: pointer; 
            inset: 0;
            background: var(--border);
            transition: .3s; 
            border-radius: 22px;
        }
        
        .slider:before { 
            position: absolute; 
            content: ""; 
            height: 16px; 
            width: 16px; 
            left: 3px; 
            bottom: 3px; 
            background: white;
            transition: .3s; 
            border-radius: 50%;
        }
        
        input:checked + .slider { 
            background: var(--primary);
        }
        
        input:checked + .slider:before { 
            transform: translateX(18px); 
        }

        .color-palette {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 8px;
            margin-top: 10px;
        }

        .color-swatch {
            aspect-ratio: 1;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.2s;
            border: 2px solid transparent;
        }

        .color-swatch:active {
            transform: scale(0.9);
        }

        .color-swatch:hover {
            transform: scale(1.05);
            border-color: white;
        }

        .preview-container {
            display: flex;
            justify-content: center;
            padding: 12px 0;
        }

        .device-selector {
            display: flex;
            gap: 6px;
            justify-content: center;
            margin-bottom: 12px;
        }

        .device-btn {
            padding: 8px 14px;
            background: var(--glass);
            border: 1px solid var(--border);
            border-radius: 8px;
            color: var(--text);
            font-size: 0.7rem;
            cursor: pointer;
            transition: all 0.2s;
            display: flex;
            align-items: center;
            gap: 6px;
            font-family: inherit;
        }

        .device-btn.active {
            background: var(--primary);
            color: white;
            border-color: var(--primary);
        }

        .device-btn:hover:not(.active) {
            background: var(--border);
        }

        .preview-phone { 
            width: 100%;
            max-width: 360px;
            height: 550px;
            background: white; 
            border-radius: 25px; 
            border: 6px solid #1a1a2e;
            overflow: hidden;
            box-shadow: 0 20px 60px rgba(0,0,0,0.5);
            transition: all 0.3s;
        }

        .preview-phone.tablet {
            max-width: 700px;
            height: 480px;
        }

        .preview-phone.desktop {
            max-width: 100%;
            height: 480px;
            border-radius: 12px;
        }

        .preview-frame { 
            width: 100%; 
            height: 100%; 
            border: none; 
        }

        .btn { 
            padding: 11px 18px; 
            border-radius: 10px; 
            text-align: center; 
            font-weight: 700; 
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            margin: 8px 0;
            border: none;
            cursor: pointer;
            font-size: 0.8rem;
            transition: all 0.2s;
            width: 100%;
            font-family: inherit;
        }

        .btn:active {
            transform: scale(0.97);
        }

        .btn:hover {
            box-shadow: 0 4px 15px rgba(0,0,0,0.3);
        }

        .btn-primary {
            background: linear-gradient(135deg, var(--primary), var(--accent));
            color: white;
        }

        .btn-success {
            background: var(--success);
            color: white;
        }

        .btn-info {
            background: var(--info);
            color: white;
        }

        .btn-outline {
            background: transparent;
            border: 2px solid var(--primary);
            color: var(--primary);
        }

        .code-container {
            background: var(--darker);
            padding: 12px;
            border-radius: 10px;
            overflow-x: auto;
            border: 1px solid var(--border);
            margin-bottom: 10px;
            position: relative;
        }

        .code-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
            padding-bottom: 10px;
            border-bottom: 1px solid var(--border);
        }

        .code-label {
            font-size: 0.7rem;
            color: var(--text-dim);
            font-weight: 600;
        }

        .code-size {
            font-size: 0.65rem;
            color: var(--primary);
            font-weight: 700;
        }

        .code-output {
            font-family: 'Courier New', monospace;
            font-size: 0.65rem;
            color: #58a6ff;
            white-space: pre-wrap;
            word-break: break-all;
            line-height: 1.5;
            max-height: 350px;
            overflow-y: auto;
        }

        .code-output::-webkit-scrollbar { width: 5px; }
        .code-output::-webkit-scrollbar-thumb { 
            background: var(--primary); 
            border-radius: 10px; 
        }

        .template-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 10px;
            margin-top: 10px;
        }

        .template-card {
            background: var(--glass);
            border-radius: 10px;
            overflow: hidden;
            cursor: pointer;
            border: 1px solid var(--border);
            transition: all 0.2s;
        }

        .template-card:active {
            transform: scale(0.97);
        }

        .template-card:hover {
            border-color: var(--primary);
            box-shadow: 0 5px 20px rgba(255, 107, 157, 0.3);
        }

        .template-preview {
            width: 100%;
            height: 80px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.8rem;
        }

        .template-info {
            padding: 10px;
            background: rgba(22, 22, 29, 0.7);
        }

        .template-name {
            font-weight: 700;
            font-size: 0.75rem;
            margin-bottom: 3px;
        }

        .template-desc {
            font-size: 0.65rem;
            color: var(--text-dim);
        }

        .bottom-nav { 
            position: fixed; 
            bottom: 0; 
            left: 0;
            right: 0;
            background: rgba(30, 30, 46, 0.98);
            backdrop-filter: blur(20px);
            display: flex; 
            justify-content: space-around; 
            padding: 8px 0 max(8px, env(safe-area-inset-bottom)); 
            border-top: 1px solid var(--border);
            z-index: 1000;
            box-shadow: 0 -2px 20px rgba(0,0,0,0.3);
        }
        
        .nav-item { 
            color: var(--text-dim);
            text-align: center; 
            font-size: 0.6rem; 
            cursor: pointer; 
            transition: all 0.2s;
            padding: 6px 8px;
            border-radius: 10px;
            font-weight: 600;
            flex: 1;
            max-width: 70px;
        }
        
        .nav-item:active {
            transform: scale(0.95);
        }

        .nav-item.active { 
            color: var(--primary);
            background: rgba(255, 107, 157, 0.15);
        }
        
        .nav-item-icon { 
            font-size: 1.2rem; 
            display: block; 
            margin-bottom: 3px;
        }

        .toast {
            position: fixed;
            top: 90px;
            left: 50%;
            transform: translateX(-50%) translateY(-100px);
            background: var(--dark);
            color: white;
            padding: 10px 18px;
            border-radius: 10px;
            border-left: 4px solid var(--success);
            box-shadow: 0 8px 25px rgba(0,0,0,0.5);
            z-index: 2000;
            opacity: 0;
            transition: all 0.3s;
            font-size: 0.75rem;
            font-weight: 600;
            max-width: 90%;
        }

        .toast.show {
            opacity: 1;
            transform: translateX(-50%) translateY(0);
        }

        .toast.error { border-left-color: var(--danger); }
        .toast.warning { border-left-color: var(--warning); }
        .toast.info { border-left-color: var(--info); }

        .modal {
            position: fixed;
            inset: 0;
            background: rgba(0,0,0,0.8);
            display: none;
            align-items: center;
            justify-content: center;
            z-index: 3000;
            padding: 20px;
        }

        .modal.show {
            display: flex;
            animation: fadeIn 0.3s;
        }

        .modal-content {
            background: var(--dark);
            border: 1px solid var(--border);
            border-radius: 15px;
            padding: 20px;
            max-width: 400px;
            width: 100%;
            max-height: 80vh;
            overflow-y: auto;
        }

        .modal-header {
            font-size: 1.2rem;
            font-weight: 700;
            margin-bottom: 15px;
            color: var(--primary);
        }

        .modal-close {
            float: right;
            cursor: pointer;
            font-size: 1.5rem;
            color: var(--text-dim);
        }

        .ai-assistant {
            position: fixed;
            bottom: 80px;
            right: 15px;
            z-index: 999;
        }

        .ai-btn {
            width: 55px;
            height: 55px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--primary), var(--accent));
            border: none;
            color: white;
            font-size: 1.5rem;
            cursor: pointer;
            box-shadow: 0 4px 20px rgba(255, 107, 157, 0.4);
            animation: float2 3s infinite;
            transition: all 0.2s;
        }

        .ai-btn:active {
            transform: translateY(-10px) scale(0.95);
        }

        @keyframes float2 {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }

        .ai-chat {
            position: absolute;
            bottom: 70px;
            right: 0;
            width: 280px;
            max-height: 400px;
            background: var(--dark);
            border: 1px solid var(--border);
            border-radius: 15px;
            display: none;
            flex-direction: column;
            box-shadow: 0 10px 40px rgba(0,0,0,0.5);
        }

        .ai-chat.show {
            display: flex;
            animation: slideUp 0.3s ease;
        }

        @keyframes slideUp {
            from { 
                opacity: 0;
                transform: translateY(20px); 
            }
            to { 
                opacity: 1;
                transform: translateY(0); 
            }
        }

        .ai-header {
            padding: 12px;
            background: linear-gradient(135deg, var(--primary), var(--accent));
            border-radius: 15px 15px 0 0;
            font-weight: 700;
            font-size: 0.85rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .ai-close {
            cursor: pointer;
            font-size: 1.2rem;
            padding: 0 5px;
        }

        .ai-messages {
            flex: 1;
            padding: 12px;
            overflow-y: auto;
            max-height: 280px;
        }

        .ai-messages::-webkit-scrollbar { width: 4px; }
        .ai-messages::-webkit-scrollbar-thumb { 
            background: var(--primary); 
            border-radius: 10px; 
        }

        .ai-message {
            margin-bottom: 10px;
            padding: 8px 12px;
            background: var(--glass);
            border-radius: 10px;
            font-size: 0.75rem;
            line-height: 1.4;
            animation: messageIn 0.3s ease;
        }

        @keyframes messageIn {
            from { 
                opacity: 0;
                transform: translateX(-10px); 
            }
            to { 
                opacity: 1;
                transform: translateX(0); 
            }
        }

        .ai-message.user {
            background: var(--primary);
            margin-left: 30px;
        }

        .ai-input-container {
            padding: 10px;
            border-top: 1px solid var(--border);
            display: flex;
            gap: 5px;
        }

        .ai-input-container input {
            flex: 1;
            padding: 8px;
            background: var(--glass);
            border: 1px solid var(--border);
            border-radius: 8px;
            color: var(--text);
            font-size: 0.75rem;
            font-family: inherit;
        }

        .ai-send {
            padding: 8px 12px;
            background: var(--primary);
            border: none;
            border-radius: 8px;
            color: white;
            cursor: pointer;
            transition: all 0.2s;
        }

        .ai-send:active {
            transform: scale(0.95);
        }

        .mb-10 { margin-bottom: 10px; }
        .mt-10 { margin-top: 10px; }

        @media (max-width: 480px) {
            .header-title {
                font-size: 0.85rem;
            }
            
            .header-subtitle {
                display: none;
            }

            .template-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>

    <div class="preloader" id="preloader">
        <div class="preloader-logo">
            <div style="text-align: center;">
                <div class="logo-text">
                    Yinyer
                    <span class="play-icon">▶</span>
                </div>
                <div class="logo-mp3">mp3</div>
            </div>
        </div>
        <div class="preloader-progress">
            <div class="preloader-progress-bar"></div>
        </div>
        <div class="preloader-text">Cargando Yinyer Studio Pro v2.0...</div>
    </div>

    <div class="header">
        <div class="header-logo">
            <div class="header-icon">🔥</div>
            <div>
                <div class="header-title">YINYER STUDIO PRO v2.0</div>
                <div class="header-subtitle">Constructor Web Definitivo</div>
            </div>
        </div>
        <div class="header-actions">
            <button class="header-btn" onclick="undoAction()" title="Deshacer">
                <i class="fas fa-undo"></i>
            </button>
            <button class="header-btn" onclick="redoAction()" title="Rehacer">
                <i class="fas fa-redo"></i>
            </button>
            <button class="header-btn" onclick="saveProject()" title="Guardar">
                <i class="fas fa-save"></i>
            </button>
            <button class="header-btn ai" onclick="toggleAI()" title="Asistente IA">
                <i class="fas fa-robot"></i>
            </button>
        </div>
    </div>

    <div class="content-wrapper">
        
        <div id="tab-editor" class="tab-content active">
            
            <div class="stats-bar">
                <div class="stat-card">
                    <div class="stat-value" id="statsSize">0 KB</div>
                    <div class="stat-label">Tamaño</div>
                </div>
                <div class="stat-card">
                    <div class="stat-value" id="statsElements">0</div>
                    <div class="stat-label">Elementos</div>
                </div>
                <div class="stat-card">
                    <div class="stat-value" id="statsScore">0%</div>
                    <div class="stat-label">SEO</div>
                </div>
            </div>

            <div class="section">
                <div class="section-header" onclick="toggleSection(this)">
                    <div class="section-header-left">
                        <span class="section-icon">⚙️</span>
                        <span class="section-title">Básico</span>
                    </div>
                    <span class="expand-icon">▼</span>
                </div>
                <div class="section-content">
                    <div class="card">
                        <div class="field">
                            <label class="field-label">
                                <i class="fas fa-heading"></i> Título del Sitio
                            </label>
                            <input type="text" class="field-input" id="pageTitle" value="Mi Sitio Increíble" oninput="updatePreview()">
                        </div>
                        <div class="field">
                            <label class="field-label">
                                <i class="fas fa-file-alt"></i> Descripción SEO
                            </label>
                            <textarea class="field-textarea" id="metaDesc" oninput="updatePreview()">El mejor sitio web creado con Yinyer Studio Pro</textarea>
                        </div>
                    </div>
                </div>
            </div>

            <div class="section">
                <div class="section-header" onclick="toggleSection(this)">
                    <div class="section-header-left">
                        <span class="section-icon">🎨</span>
                        <span class="section-title">Colores</span>
                    </div>
                    <span class="expand-icon">▼</span>
                </div>
                <div class="section-content">
                    <div class="card">
                        <div class="field">
                            <label class="field-label">Color Principal</label>
                            <input type="color" class="field-input field-color" id="primaryColor" value="#ff6b9d" oninput="updatePreview()">
                        </div>
                        <div class="field">
                            <label class="field-label">Color Secundario</label>
                            <input type="color" class="field-input field-color" id="secondaryColor" value="#c44569" oninput="updatePreview()">
                        </div>
                        <div class="field">
                            <label class="field-label">Color de Fondo</label>
                            <input type="color" class="field-input field-color" id="bgColor" value="#ffffff" oninput="updatePreview()">
                        </div>
                        
                        <div class="card-title mt-10">Paletas Predefinidas</div>
                        <div class="color-palette">
                            <div class="color-swatch" style="background: linear-gradient(135deg, #667eea, #764ba2)" onclick="applyPalette('#667eea', '#764ba2')" title="Purple Dream"></div>
                            <div class="color-swatch" style="background: linear-gradient(135deg, #f093fb, #f5576c)" onclick="applyPalette('#f093fb', '#f5576c')" title="Pink Passion"></div>
                            <div class="color-swatch" style="background: linear-gradient(135deg, #4facfe, #00f2fe)" onclick="applyPalette('#4facfe', '#00f2fe')" title="Ocean Blue"></div>
                            <div class="color-swatch" style="background: linear-gradient(135deg, #43e97b, #38f9d7)" onclick="applyPalette('#43e97b', '#38f9d7')" title="Mint Fresh"></div>
                            <div class="color-swatch" style="background: linear-gradient(135deg, #fa709a, #fee140)" onclick="applyPalette('#fa709a', '#fee140')" title="Sunset"></div>
                            <div class="color-swatch" style="background: linear-gradient(135deg, #30cfd0, #330867)" onclick="applyPalette('#30cfd0', '#330867')" title="Deep Ocean"></div>
                            <div class="color-swatch" style="background: linear-gradient(135deg, #a8edea, #fed6e3)" onclick="applyPalette('#a8edea', '#fed6e3')" title="Pastel"></div>
                            <div class="color-swatch" style="background: linear-gradient(135deg, #ff9a56, #ff6a88)" onclick="applyPalette('#ff9a56', '#ff6a88')" title="Warm"></div>
                        </div>

                        <div class="toggle-group mt-10">
                            <span class="toggle-label">
                                <i class="fas fa-moon"></i> Modo Oscuro
                            </span>
                            <label class="switch">
                                <input type="checkbox" id="darkMode" onchange="updatePreview()">
                                <span class="slider"></span>
                            </label>
                        </div>
                    </div>
                </div>
            </div>

            <div class="section">
                <div class="section-header" onclick="toggleSection(this)">
                    <div class="section-header-left">
                        <span class="section-icon">🎯</span>
                        <span class="section-title">Hero</span>
                    </div>
                    <span class="expand-icon">▼</span>
                </div>
                <div class="section-content">
                    <div class="card">
                        <div class="toggle-group">
                            <span class="toggle-label">Activar Hero</span>
                            <label class="switch">
                                <input type="checkbox" id="heroEnabled" checked onchange="updatePreview()">
                                <span class="slider"></span>
                            </label>
                        </div>
                        <div class="field">
                            <label class="field-label">Título</label>
                            <input type="text" class="field-input" id="heroTitle" value="Bienvenido a Mi Sitio" oninput="updatePreview()">
                        </div>
                        <div class="field">
                            <label class="field-label">Subtítulo</label>
                            <input type="text" class="field-input" id="heroSubtitle" value="Experiencias digitales increíbles" oninput="updatePreview()">
                        </div>
                        <div class="field">
                            <label class="field-label">Tamaño Título</label>
                            <input type="range" class="field-range" id="heroTitleSize" min="30" max="70" value="50" oninput="updatePreview(); document.getElementById('heroSizeVal').textContent = this.value + 'px'">
                            <span class="range-value" id="heroSizeVal">50px</span>
                        </div>
                    </div>
                </div>
            </div>

        </div>

        <div id="tab-preview" class="tab-content">
            <div class="device-selector">
                <button class="device-btn active" onclick="changeDevice('mobile', event)">
                    <i class="fas fa-mobile-alt"></i> Móvil
                </button>
                <button class="device-btn" onclick="changeDevice('tablet', event)">
                    <i class="fas fa-tablet-alt"></i> Tablet
                </button>
                <button class="device-btn" onclick="changeDevice('desktop', event)">
                    <i class="fas fa-desktop"></i> Desktop
                </button>
            </div>
            <div class="preview-container">
                <div class="preview-phone" id="previewDevice">
                    <iframe id="previewFrame" class="preview-frame"></iframe>
                </div>
            </div>
            <button class="btn btn-success" onclick="downloadHTML()">
                <i class="fas fa-download"></i> Descargar HTML
            </button>
            <button class="btn btn-outline" onclick="openInNewTab()">
                <i class="fas fa-external-link-alt"></i> Abrir en Pestaña Nueva
            </button>
        </div>

        <div id="tab-code" class="tab-content">
            <div class="code-container">
                <div class="code-header">
                    <span class="code-label">
                        <i class="fas fa-code"></i> Código HTML
                    </span>
                    <span class="code-size" id="codeSizeDisplay">0 KB</span>
                </div>
                <pre id="codeDisplay" class="code-output"></pre>
            </div>
            <button class="btn btn-primary" onclick="copyCode()">
                <i class="fas fa-clipboard"></i> Copiar Código
            </button>
            <button class="btn btn-success" onclick="downloadHTML()">
                <i class="fas fa-download"></i> Descargar
            </button>
        </div>

        <div id="tab-templates" class="tab-content">
            <div class="card">
                <div class="card-title">Plantillas Profesionales</div>
                <div class="template-grid">
                    <div class="template-card" onclick="applyTemplate('modern')">
                        <div class="template-preview" style="background: linear-gradient(135deg, #667eea, #764ba2)">🚀</div>
                        <div class="template-info">
                            <div class="template-name">Moderno</div>
                            <div class="template-desc">Startup tech</div>
                        </div>
                    </div>
                    <div class="template-card" onclick="applyTemplate('creative')">
                        <div class="template-preview" style="background: linear-gradient(135deg, #f093fb, #f5576c)">🎨</div>
                        <div class="template-info">
                            <div class="template-name">Creativo</div>
                            <div class="template-desc">Portfolio</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

    </div>

    <div class="bottom-nav">
        <div class="nav-item active" onclick="switchTab('editor', event)">
            <span class="nav-item-icon">🎨</span>
            <span>Editor</span>
        </div>
        <div class="nav-item" onclick="switchTab('preview', event)">
            <span class="nav-item-icon">👁️</span>
            <span>Vista</span>
        </div>
        <div class="nav-item" onclick="switchTab('code', event)">
            <span class="nav-item-icon">💻</span>
            <span>Código</span>
        </div>
        <div class="nav-item" onclick="switchTab('templates', event)">
            <span class="nav-item-icon">📋</span>
            <span>Temas</span>
        </div>
    </div>

    <div id="toast" class="toast"></div>

    <div class="ai-assistant">
        <button class="ai-btn" onclick="toggleAI()">
            <i class="fas fa-robot"></i>
        </button>
        <div class="ai-chat" id="aiChat">
            <div class="ai-header">
                <span><i class="fas fa-robot"></i> Asistente IA</span>
                <span class="ai-close" onclick="toggleAI()">×</span>
            </div>
            <div class="ai-messages" id="aiMessages">
                <div class="ai-message">
                    Hola! Soy tu asistente. Pregúntame lo que necesites sobre colores, videos, WhatsApp, imágenes o diseño.
                </div>
            </div>
            <div class="ai-input-container">
                <input type="text" placeholder="Escribe tu pregunta..." id="aiInput" onkeypress="handleAIInput(event)">
                <button class="ai-send" onclick="sendAIMessage()">
                    <i class="fas fa-paper-plane"></i>
                </button>
            </div>
        </div>
    </div>

    <script>
        let generatedHTML = '';
        let history = [];
        let historyIndex = -1;
        const MAX_HISTORY = 50;

        window.addEventListener('load', function() {
            setTimeout(function() {
                document.getElementById('preloader').classList.add('hidden');
            }, 2000);
            
            updatePreview();
            expandFirstSections();
            updateStats();
        });

        function switchTab(tabName, event) {
            if (event) {
                event.preventDefault();
                event.stopPropagation();
            }
            
            document.querySelectorAll('.tab-content').forEach(function(tab) {
                tab.classList.remove('active');
            });
            document.getElementById('tab-' + tabName).classList.add('active');
            
            document.querySelectorAll('.nav-item').forEach(function(nav) {
                nav.classList.remove('active');
            });
            
            if (event && event.currentTarget) {
                event.currentTarget.classList.add('active');
            }

            if (tabName === 'preview' || tabName === 'code') {
                updatePreview();
            }
        }

        function toggleSection(element) {
            element.classList.toggle('open');
            element.nextElementSibling.classList.toggle('open');
        }

        function expandFirstSections() {
            var headers = document.querySelectorAll('.section-header');
            for (var i = 0; i < Math.min(3, headers.length); i++) {
                headers[i].classList.add('open');
                headers[i].nextElementSibling.classList.add('open');
            }
        }

        function applyPalette(primary, secondary) {
            document.getElementById('primaryColor').value = primary;
            document.getElementById('secondaryColor').value = secondary;
            updatePreview();
            showToast('Paleta aplicada', 'success');
        }

        function changeDevice(device, event) {
            if (event) {
                event.preventDefault();
                event.stopPropagation();
            }
            
            var preview = document.getElementById('previewDevice');
            var buttons = document.querySelectorAll('.device-btn');
            
            buttons.forEach(function(btn) {
                btn.classList.remove('active');
            });
            
            if (event && event.currentTarget) {
                event.currentTarget.classList.add('active');
            }

            preview.classList.remove('tablet', 'desktop');
            if (device === 'tablet') preview.classList.add('tablet');
            if (device === 'desktop') preview.classList.add('desktop');
        }

        function getConfig() {
            return {
                pageTitle: document.getElementById('pageTitle').value,
                metaDesc: document.getElementById('metaDesc').value,
                primaryColor: document.getElementById('primaryColor').value,
                secondaryColor: document.getElementById('secondaryColor').value,
                bgColor: document.getElementById('bgColor').value,
                darkMode: document.getElementById('darkMode').checked,
                heroEnabled: document.getElementById('heroEnabled').checked,
                heroTitle: document.getElementById('heroTitle').value,
                heroSubtitle: document.getElementById('heroSubtitle').value,
                heroTitleSize: document.getElementById('heroTitleSize').value
            };
        }

        function generateHTML() {
            var config = getConfig();
            var finalBg = config.darkMode ? '#0f172a' : config.bgColor;
            var finalText = config.darkMode ? '#e2e8f0' : '#1e293b';
            
            var heroHTML = '';
            if (config.heroEnabled) {
                var heroBg = 'background: linear-gradient(135deg, ' + config.primaryColor + ', ' + config.secondaryColor + ');';
                heroHTML = '<section style="' + heroBg + ' min-height: 100vh; display: flex; align-items: center; justify-content: center; text-align: center; color: white; padding: 80px 20px;"><div style="max-width: 950px;"><h1 style="font-size: ' + config.heroTitleSize + 'px; margin-bottom: 30px; font-weight: 900;">' + config.heroTitle + '</h1><p style="font-size: 1.5rem; margin-bottom: 40px;">' + config.heroSubtitle + '</p></div></section>';
            }

            return '<!DOCTYPE html>\n<html lang="es">\n<head>\n    <meta charset="UTF-8">\n    <meta name="viewport" content="width=device-width, initial-scale=1.0">\n    <title>' + config.pageTitle + '</title>\n    <meta name="description" content="' + config.metaDesc + '">\n    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700;900&display=swap" rel="stylesheet">\n    <style>\n        * { margin: 0; padding: 0; box-sizing: border-box; }\n        body { \n            font-family: "Poppins", sans-serif; \n            background: ' + finalBg + ';\n            color: ' + finalText + ';\n        }\n    </style>\n</head>\n<body>\n    ' + heroHTML + '\n</body>\n</html>';
        }

        function updatePreview() {
            generatedHTML = generateHTML();
            
            var iframe = document.getElementById('previewFrame');
            if (iframe) {
                var iframeDoc = iframe.contentDocument || iframe.contentWindow.document;
                iframeDoc.open();
                iframeDoc.write(generatedHTML);
                iframeDoc.close();
            }
            
            document.getElementById('codeDisplay').textContent = generatedHTML;
            updateStats();
        }

        function updateStats() {
            var sizeKB = (new Blob([generatedHTML]).size / 1024).toFixed(2);
            document.getElementById('statsSize').textContent = sizeKB + ' KB';
            document.getElementById('codeSizeDisplay').textContent = sizeKB + ' KB';
            
            var config = getConfig();
            var elements = 0;
            if (config.heroEnabled) elements++;
            document.getElementById('statsElements').textContent = elements;
            
            var seoScore = 0;
            if (config.pageTitle && config.pageTitle.length > 10) seoScore += 50;
            if (config.metaDesc && config.metaDesc.length > 50) seoScore += 50;
            document.getElementById('statsScore').textContent = seoScore + '%';
        }

        function copyCode() {
            if (navigator.clipboard) {
                navigator.clipboard.writeText(generatedHTML).then(function() {
                    showToast('Código copiado', 'success');
                });
            }
        }

        function downloadHTML() {
            try {
                var blob = new Blob([generatedHTML], { type: 'text/html;charset=utf-8' });
                var url = URL.createObjectURL(blob);
                var a = document.createElement('a');
                var fileName = document.getElementById('pageTitle').value.replace(/[^a-z0-9]/gi, '-').toLowerCase();
                a.href = url;
                a.download = fileName + '.html';
                document.body.appendChild(a);
                a.click();
                document.body.removeChild(a);
                URL.revokeObjectURL(url);
                showToast('Descarga completada', 'success');
            } catch(e) {
                showToast('Error en descarga', 'error');
            }
        }

        function openInNewTab() {
            var newWindow = window.open();
            if (newWindow) {
                newWindow.document.write(generatedHTML);
                newWindow.document.close();
                showToast('Abierto en nueva pestaña', 'success');
            }
        }

        function applyTemplate(template) {
            var templates = {
                modern: {
                    primaryColor: '#667eea',
                    secondaryColor: '#764ba2',
                    heroTitle: 'Innovación Digital',
                    heroSubtitle: 'Transformamos ideas en realidad'
                },
                creative: {
                    primaryColor: '#f093fb',
                    secondaryColor: '#f5576c',
                    heroTitle: 'Creatividad Sin Límites',
                    heroSubtitle: 'Diseños que inspiran'
                }
            };

            var t = templates[template];
            if (t) {
                document.getElementById('primaryColor').value = t.primaryColor;
                document.getElementById('secondaryColor').value = t.secondaryColor;
                document.getElementById('heroTitle').value = t.heroTitle;
                document.getElementById('heroSubtitle').value = t.heroSubtitle;
                updatePreview();
                showToast('Plantilla aplicada', 'success');
            }
        }

        function showToast(message, type) {
            var toast = document.getElementById('toast');
            toast.textContent = message;
            toast.className = 'toast show';
            if (type === 'error') toast.classList.add('error');
            if (type === 'warning') toast.classList.add('warning');
            if (type === 'info') toast.classList.add('info');
            
            setTimeout(function() {
                toast.classList.remove('show');
            }, 3000);
        }

        function undoAction() {
            showToast('Deshacer no disponible', 'warning');
        }

        function redoAction() {
            showToast('Rehacer no disponible', 'warning');
        }

        function saveProject() {
            var config = JSON.stringify(getConfig());
            localStorage.setItem('yinyerProject', config);
            showToast('Proyecto guardado', 'success');
        }

        function toggleAI() {
            var chat = document.getElementById('aiChat');
            chat.classList.toggle('show');
        }

        function sendAIMessage() {
            var input = document.getElementById('aiInput');
            var msg = input.value.trim();
            if (msg) {
                handleAIMessage(msg);
                input.value = '';
            }
        }

        function handleAIInput(event) {
            if (event.key === 'Enter') {
                sendAIMessage();
            }
        }

        function handleAIMessage(msg) {
            var messages = document.getElementById('aiMessages');
            
            var userMsg = document.createElement('div');
            userMsg.className = 'ai-message user';
            userMsg.textContent = msg;
            messages.appendChild(userMsg);

            var msgLower = msg.toLowerCase();
            var response = '';

            if (msgLower.includes('color')) {
                response = 'Para cambiar colores, ve a la seccion Colores y selecciona tus colores preferidos.';
            } else if (msgLower.includes('video')) {
                response = 'Para agregar video, necesitas ir a la seccion Multimedia.';
            } else {
                response = 'Preguntame sobre colores, diseño, o como usar el editor.';
            }

            setTimeout(function() {
                var botMsg = document.createElement('div');
                botMsg.className = 'ai-message';
                botMsg.textContent = response;
                messages.appendChild(botMsg);
                messages.scrollTop = messages.scrollHeight;
            }, 500);
        }
    </script>
</body>
</html>
