
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>The BIG guy v0.1</title>
    <style>
        /* Сброс стилей и базовые настройки */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            color: #333;
        }
        
        .app-container {
            max-width: 1200px;
            margin: 20px auto;
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            overflow: hidden;
            min-height: 90vh;
        }
        
        /* Хедер с авторизацией */
        .app-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px;
            background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
            border-bottom: 3px solid #667eea;
            flex-wrap: wrap;
            gap: 15px;
        }
        
        .logo {
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .logo h1 {
            color: #667eea;
            font-size: 1.8em;
        }
        
        .user-info {
            display: flex;
            align-items: center;
            gap: 15px;
            flex-wrap: wrap;
            justify-content: flex-end;
        }
        
        .user-avatar {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            border: 3px solid #667eea;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
        }
        
        .auth-btn {
            padding: 10px 20px;
            background: #667eea;
            color: white;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s ease;
            font-size: 14px;
        }
        
        .auth-btn:hover {
            background: #5a6fd8;
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.3);
        }
        
        /* Навигация */
        .nav-container {
            position: sticky;
            top: 0;
            z-index: 100;
            background: white;
            border-bottom: 2px solid #f0f0f0;
        }
        
        .nav-buttons {
            display: flex;
            justify-content: center;
            gap: 10px;
            padding: 15px;
            overflow-x: auto;
            -webkit-overflow-scrolling: touch;
        }
        
        .nav-btn {
            padding: 12px 20px;
            font-size: 16px;
            font-weight: 600;
            background: white;
            border: 2px solid #667eea;
            border-radius: 25px;
            color: #667eea;
            cursor: pointer;
            transition: all 0.3s ease;
            min-width: 140px;
            text-align: center;
            white-space: nowrap;
        }
        
        .nav-btn:hover {
            background: #667eea;
            color: white;
            transform: translateY(-2px);
        }
        
        .nav-btn.active {
            background: #667eea;
            color: white;
        }
        
        .nav-btn.admin-only {
            border-color: #dc3545;
            color: #dc3545;
        }
        
        .nav-btn.admin-only:hover,
        .nav-btn.admin-only.active {
            background: #dc3545;
            color: white;
        }
        
        /* Стили для контента */
        .content-area {
            padding: 20px;
            min-height: 600px;
        }
        
        .page {
            display: none;
            animation: fadeIn 0.5s ease;
        }
        
        .page.active {
            display: block;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        /* Стили для главной страницы */
        .welcome-header {
            text-align: center;
            margin-bottom: 30px;
        }
        
        .welcome-header h1 {
            color: #667eea;
            font-size: 2em;
            margin-bottom: 15px;
        }
        
        .welcome-text {
            font-size: 1.1em;
            line-height: 1.6;
            color: #555;
            max-width: 800px;
            margin: 0 auto 30px;
            text-align: center;
        }
        
        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 40px;
        }
        
        .feature-card {
            background: #f8f9fa;
            padding: 25px;
            border-radius: 15px;
            text-align: center;
            transition: transform 0.3s ease;
            border: 2px solid transparent;
        }
        
        .feature-card:hover {
            transform: translateY(-5px);
            border-color: #667eea;
        }
        
        /* Стили для анкеты */
        .questionnaire-form {
            max-width: 800px;
            margin: 0 auto;
        }
        
        .form-group {
            margin-bottom: 25px;
            padding: 20px;
            background: #f8f9fa;
            border-radius: 15px;
            border-left: 5px solid #667eea;
        }
        
        .form-group h3 {
            color: #667eea;
            margin-bottom: 15px;
            font-size: 1.3em;
        }
        
        .checkbox-grid, .radio-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
            gap: 12px;
            margin-top: 15px;
        }
        
        .option-label {
            display: flex;
            align-items: center;
            padding: 12px;
            background: white;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .option-label:hover {
            border-color: #667eea;
        }
        
        .option-label.selected {
            background: #e6eeff;
            border-color: #667eea;
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.2);
        }
        
        .option-label input {
            margin-right: 10px;
            width: 18px;
            height: 18px;
            cursor: pointer;
        }
        
        .input-field {
            width: 100%;
            padding: 12px;
            font-size: 16px;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            margin-top: 10px;
        }
        
        .input-field:focus {
            outline: none;
            border-color: #667eea;
        }
        
        .submit-btn {
            display: block;
            width: 100%;
            max-width: 300px;
            margin: 30px auto;
            padding: 15px;
            font-size: 16px;
            font-weight: bold;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .submit-btn:hover:not(:disabled) {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(102, 126, 234, 0.4);
        }
        
        .submit-btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }
        
        .submit-btn.admin-btn {
            background: linear-gradient(135deg, #dc3545 0%, #c82333 100%);
        }
        
        .submit-btn.admin-btn:hover:not(:disabled) {
            box-shadow: 0 10px 25px rgba(220, 53, 69, 0.4);
        }
        
        /* Стили для программы тренировки */
        .workout-plan {
            background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
            padding: 25px;
            border-radius: 15px;
            margin-bottom: 25px;
        }
        
        .workout-header {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 25px;
            padding-bottom: 15px;
            border-bottom: 2px solid #667eea;
            gap: 15px;
        }
        
        .workout-exercise {
            background: white;
            padding: 15px;
            margin-bottom: 15px;
            border-radius: 10px;
            border-left: 4px solid #667eea;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .workout-exercise:hover {
            transform: translateX(5px);
            background: #f8f9fa;
        }
        
        .workout-exercise h4 {
            color: #667eea;
            margin-bottom: 8px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .exercise-details {
            background: #f8f9fa;
            padding: 15px;
            margin-top: 10px;
            border-radius: 8px;
            border-left: 3px solid #764ba2;
            display: none;
        }
        
        .exercise-details.active {
            display: block;
            animation: slideDown 0.3s ease;
        }
        
        @keyframes slideDown {
            from { opacity: 0; max-height: 0; }
            to { opacity: 1; max-height: 200px; }
        }
        
        .exercise-toggle {
            background: none;
            border: none;
            color: #667eea;
            cursor: pointer;
            font-size: 18px;
            padding: 0 5px;
        }
        
        /* Стили для истории */
        .history-container {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }
        
        .history-sidebar {
            background: #f8f9fa;
            border-radius: 15px;
            padding: 20px;
        }
        
        .history-content {
            background: white;
            border-radius: 15px;
            padding: 20px;
            border: 2px solid #e0e0e0;
        }
        
        .history-list {
            max-height: 300px;
            overflow-y: auto;
        }
        
        .history-item {
            background: white;
            padding: 15px;
            margin-bottom: 10px;
            border-radius: 10px;
            border-left: 4px solid #764ba2;
            cursor: pointer;
            transition: all 0.3s ease;
            position: relative;
        }
        
        .history-item:hover {
            transform: translateX(5px);
            background: #e6eeff;
        }
        
        .history-item.active {
            background: #667eea;
            color: white;
            border-left-color: #764ba2;
        }
        
        .history-date {
            font-weight: bold;
            color: #764ba2;
            margin-bottom: 5px;
            font-size: 14px;
        }
        
        .history-item.active .history-date {
            color: white;
        }
        
        .history-program-type {
            font-size: 12px;
            background: rgba(255,255,255,0.2);
            padding: 3px 8px;
            border-radius: 12px;
            display: inline-block;
            margin-top: 5px;
        }
        
        .show-exercises-btn {
            position: absolute;
            right: 15px;
            top: 15px;
            background: #667eea;
            color: white;
            border: none;
            border-radius: 15px;
            padding: 5px 12px;
            font-size: 12px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .show-exercises-btn:hover {
            background: #5a6fd8;
            transform: scale(1.05);
        }
        
        .history-filters {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
            flex-wrap: wrap;
        }
        
        .filter-btn {
            padding: 8px 15px;
            background: #e0e0e0;
            border: none;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 14px;
        }
        
        .filter-btn.active {
            background: #667eea;
            color: white;
        }
        
        /* Стили для отображения упражнений в истории */
        .exercises-container {
            margin-top: 20px;
            max-height: 400px;
            overflow-y: auto;
        }
        
        .exercises-list {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 15px;
            margin-top: 15px;
        }
        
        .exercise-card {
            background: #f8f9fa;
            padding: 15px;
            border-radius: 10px;
            border-left: 4px solid #28a745;
        }
        
        .exercise-card h5 {
            color: #28a745;
            margin-bottom: 8px;
            font-size: 16px;
        }
        
        .exercise-stats {
            display: flex;
            gap: 15px;
            margin-top: 10px;
            font-size: 14px;
            color: #666;
        }
        
        .stat-item {
            display: flex;
            align-items: center;
            gap: 5px;
        }
        
        .stat-icon {
            font-size: 16px;
        }
        
        /* Стили для рефлексии */
        .reflection-container {
            max-width: 900px;
            margin: 0 auto;
        }
        
        .reflection-editor {
            background: #f8f9fa;
            padding: 25px;
            border-radius: 15px;
            margin-bottom: 25px;
        }
        
        .reflection-history {
            background: white;
            padding: 20px;
            border-radius: 10px;
            border: 2px solid #e0e0e0;
        }
        
        .reflection-item {
            padding: 15px;
            margin-bottom: 15px;
            border-left: 4px solid #28a745;
            background: #f8fff8;
            cursor: pointer;
        }
        
        .reflection-date {
            font-weight: bold;
            color: #28a745;
            margin-bottom: 10px;
            font-size: 14px;
        }
        
        .reflection-textarea {
            width: 100%;
            min-height: 120px;
            padding: 12px;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            font-size: 16px;
            resize: vertical;
            margin-bottom: 15px;
        }
        
        .reflection-textarea:focus {
            outline: none;
            border-color: #667eea;
        }
        
        .mood-selector {
            display: flex;
            gap: 10px;
            margin: 15px 0;
            flex-wrap: wrap;
        }
        
        .mood-option {
            padding: 10px 20px;
            background: white;
            border: 2px solid #e0e0e0;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 14px;
        }
        
        .mood-option:hover {
            transform: translateY(-2px);
        }
        
        .mood-option.selected {
            border-color: #667eea;
            background: #e6eeff;
        }
        
        /* Стили для окна входа/регистрации */
        .auth-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
            z-index: 1000;
            align-items: center;
            justify-content: center;
        }
        
        .auth-modal.active {
            display: flex;
        }
        
        .auth-form {
            background: white;
            padding: 30px;
            border-radius: 20px;
            width: 90%;
            max-width: 400px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.3);
            animation: slideUp 0.3s ease;
        }
        
        @keyframes slideUp {
            from { transform: translateY(30px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }
        
        .auth-form h2 {
            color: #667eea;
            text-align: center;
            margin-bottom: 25px;
        }
        
        .auth-tabs {
            display: flex;
            margin-bottom: 20px;
            border-bottom: 2px solid #e0e0e0;
        }
        
        .auth-tab {
            flex: 1;
            text-align: center;
            padding: 10px;
            cursor: pointer;
            border-bottom: 2px solid transparent;
            transition: all 0.3s ease;
        }
        
        .auth-tab.active {
            color: #667eea;
            border-bottom-color: #667eea;
            font-weight: 600;
        }
        
        .auth-tab.disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }
        
        .auth-input-group {
            margin-bottom: 20px;
        }
        
        .auth-input-group label {
            display: block;
            margin-bottom: 8px;
            color: #555;
            font-weight: 500;
        }
        
        .auth-input {
            width: 100%;
            padding: 12px;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            font-size: 16px;
            transition: all 0.3s ease;
        }
        
        .auth-input:focus {
            border-color: #667eea;
            outline: none;
        }
        
        .auth-error {
            color: #dc3545;
            font-size: 14px;
            margin-top: 5px;
            display: none;
        }
        
        /* Стили для админ-панели */
        .admin-panel {
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .admin-section {
            background: #f8f9fa;
            padding: 25px;
            border-radius: 15px;
            margin-bottom: 25px;
            border-left: 5px solid #dc3545;
        }
        
        .admin-section h3 {
            color: #dc3545;
            margin-bottom: 20px;
            font-size: 1.4em;
        }
        
        .admin-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
        }
        
        .admin-card {
            background: white;
            padding: 20px;
            border-radius: 10px;
            border: 2px solid #e0e0e0;
        }
        
        .admin-card h4 {
            color: #667eea;
            margin-bottom: 15px;
            font-size: 1.2em;
        }
        
        .user-list {
            max-height: 300px;
            overflow-y: auto;
        }
        
        .user-item {
            padding: 12px;
            border-bottom: 1px solid #e0e0e0;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .user-item:last-child {
            border-bottom: none;
        }
        
        .user-item.admin {
            background: #fff0f0;
        }
        
        .user-actions {
            display: flex;
            gap: 8px;
        }
        
        .user-action-btn {
            padding: 5px 10px;
            background: #667eea;
            color: white;
            border: none;
            border-radius: 15px;
            cursor: pointer;
            font-size: 12px;
            transition: all 0.3s ease;
        }
        
        .user-action-btn:hover {
            transform: scale(1.05);
        }
        
        .user-action-btn.delete {
            background: #dc3545;
        }
        
        .user-action-btn.view {
            background: #28a745;
        }
        
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 15px;
            margin-top: 15px;
        }
        
        .stat-card {
            background: white;
            padding: 15px;
            border-radius: 10px;
            border: 2px solid #e0e0e0;
        }
        
        .stat-number {
            font-size: 24px;
            font-weight: bold;
            color: #667eea;
            margin-bottom: 5px;
        }
        
        .stat-label {
            font-size: 14px;
            color: #666;
        }
        
        /* Стили для вопросов/поддержки */
        .support-container {
            max-width: 900px;
            margin: 0 auto;
        }
        
        .question-form {
            background: #f8f9fa;
            padding: 25px;
            border-radius: 15px;
            margin-bottom: 25px;
        }
        
        .question-list {
            background: white;
            padding: 20px;
            border-radius: 10px;
            border: 2px solid #e0e0e0;
        }
        
        .question-item {
            padding: 15px;
            margin-bottom: 15px;
            border-left: 4px solid #17a2b8;
            background: #f0f9ff;
            position: relative;
        }
        
        .question-item.answered {
            border-left-color: #28a745;
            background: #f8fff8;
        }
        
        .question-header {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            margin-bottom: 10px;
            flex-wrap: wrap;
            gap: 10px;
        }
        
        .question-date {
            font-size: 12px;
            color: #666;
        }
        
        .question-status {
            padding: 3px 8px;
            border-radius: 12px;
            font-size: 12px;
            font-weight: bold;
        }
        
        .question-status.pending {
            background: #ffc107;
            color: #212529;
        }
        
        .question-status.answered {
            background: #28a745;
            color: white;
        }
        
        .question-user {
            font-size: 14px;
            color: #667eea;
            font-weight: 500;
        }
        
        .question-text {
            font-size: 15px;
            line-height: 1.5;
            margin-bottom: 10px;
        }
        
        .answer-section {
            margin-top: 15px;
            padding-top: 15px;
            border-top: 1px dashed #e0e0e0;
        }
        
        .answer-label {
            font-size: 14px;
            color: #28a745;
            font-weight: 500;
            margin-bottom: 8px;
            display: block;
        }
        
        .answer-text {
            font-size: 14px;
            color: #555;
            line-height: 1.5;
            background: #f8f9fa;
            padding: 10px;
            border-radius: 8px;
            border-left: 3px solid #28a745;
        }
        
        .admin-answer-form {
            margin-top: 15px;
        }
        
        /* Стили для модального окна создания пользователя */
        .create-user-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
            z-index: 1001;
            align-items: center;
            justify-content: center;
        }
        
        .create-user-modal.active {
            display: flex;
        }
        
        .create-user-form {
            background: white;
            padding: 30px;
            border-radius: 20px;
            width: 90%;
            max-width: 500px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.3);
            animation: slideUp 0.3s ease;
        }
        
        .create-user-form h3 {
            color: #667eea;
            text-align: center;
            margin-bottom: 20px;
        }
        
        /* Утилиты */
        .hidden {
            display: none !important;
        }
        
        .error-message {
            color: #dc3545;
            background: #ffe6e6;
            padding: 12px;
            border-radius: 10px;
            margin: 15px 0;
            text-align: center;
            font-size: 14px;
        }
        
        .success-message {
            color: #28a745;
            background: #e6ffe6;
            padding: 12px;
            border-radius: 10px;
            margin: 15px 0;
            text-align: center;
            font-size: 14px;
        }
        
        .loading {
            text-align: center;
            padding: 30px;
            color: #667eea;
        }
        
        .sync-status {
            display: flex;
            align-items: center;
            gap: 8px;
            color: #666;
            font-size: 12px;
        }
        
        .sync-indicator {
            width: 8px;
            height: 8px;
            border-radius: 50%;
            background: #28a745;
            animation: pulse 2s infinite;
        }
        
        .sync-indicator.syncing {
            background: #ffc107;
        }
        
        .sync-indicator.error {
            background: #dc3545;
        }
        
        @keyframes pulse {
            0% { opacity: 1; }
            50% { opacity: 0.5; }
            100% { opacity: 1; }
        }
        
        /* Адаптивность для мобильных устройств */
        @media (max-width: 768px) {
            .app-container {
                margin: 10px;
                border-radius: 15px;
            }
            
            .app-header {
                padding: 15px;
                flex-direction: column;
                text-align: center;
                gap: 10px;
            }
            
            .logo h1 {
                font-size: 1.5em;
            }
            
            .user-info {
                justify-content: center;
                width: 100%;
            }
            
            .nav-buttons {
                padding: 10px;
                justify-content: flex-start;
            }
            
            .nav-btn {
                min-width: 120px;
                padding: 10px 15px;
                font-size: 14px;
            }
            
            .content-area {
                padding: 15px;
            }
            
            .welcome-header h1 {
                font-size: 1.8em;
            }
            
            .features-grid {
                grid-template-columns: 1fr;
                gap: 15px;
            }
            
            .form-group {
                padding: 15px;
            }
            
            .checkbox-grid, .radio-grid {
                grid-template-columns: 1fr;
            }
            
            .history-container {
                gap: 15px;
            }
            
            .history-sidebar,
            .history-content,
            .reflection-editor,
            .reflection-history {
                padding: 15px;
            }
            
            .workout-plan {
                padding: 15px;
            }
            
            .workout-header {
                flex-direction: column;
                align-items: flex-start;
            }
            
            .mood-selector {
                justify-content: center;
            }
            
            .mood-option {
                flex: 1;
                min-width: 100px;
                text-align: center;
            }
            
            .exercises-list {
                grid-template-columns: 1fr;
            }
            
            .show-exercises-btn {
                position: relative;
                top: 0;
                right: 0;
                margin-top: 10px;
                width: 100%;
            }
            
            .auth-form {
                padding: 20px;
                width: 95%;
            }
            
            .admin-grid {
                grid-template-columns: 1fr;
            }
            
            .stats-grid {
                grid-template-columns: repeat(2, 1fr);
            }
        }
        
        @media (max-width: 480px) {
            .nav-btn {
                min-width: 100px;
                padding: 8px 12px;
                font-size: 13px;
            }
            
            .form-group h3 {
                font-size: 1.2em;
            }
            
            .option-label {
                padding: 10px;
                font-size: 14px;
            }
            
            .submit-btn {
                font-size: 15px;
                padding: 12px;
            }
            
            .workout-exercise {
                padding: 12px;
            }
            
            .history-filters {
                justify-content: center;
            }
            
            .filter-btn {
                padding: 6px 12px;
                font-size: 13px;
            }
            
            .stats-grid {
                grid-template-columns: 1fr;
            }
        }
        
        /* Стили для мобильной навигации */
        .mobile-menu-btn {
            display: none;
            background: #667eea;
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 10px;
            cursor: pointer;
            margin: 10px auto;
            width: 90%;
            font-weight: 600;
        }
        
        @media (max-width: 768px) {
            .nav-buttons {
                flex-direction: column;
                display: none;
                gap: 10px;
            }
            
            .nav-buttons.active {
                display: flex;
            }
            
            .mobile-menu-btn {
                display: block;
            }
            
            .nav-btn {
                width: 100%;
            }
        }
    </style>
    </head>
     <body>
    <!-- Модальное окно входа -->
    <div class="auth-modal" id="auth-modal">
        <div class="auth-form">
            <h2>Вход в систему</h2>
            
            <div class="auth-tabs">
                <div class="auth-tab active" id="login-tab">Вход</div>
                <div class="auth-tab disabled" id="register-tab" title="Регистрация доступна только администратору">Регистрация</div>
            </div>
            
            <div id="login-form">
                <div class="auth-input-group">
                    <label for="login-username">Логин</label>
                    <input type="text" id="login-username" class="auth-input" placeholder="Введите логин">
                    <div class="auth-error" id="login-username-error"></div>
                </div>
                
                <div class="auth-input-group">
                    <label for="login-password">Пароль</label>
                    <input type="password" id="login-password" class="auth-input" placeholder="Введите пароль">
                    <div class="auth-error" id="login-password-error"></div>
                </div>
                
                <div class="auth-error" id="login-general-error"></div>
                
                <button class="submit-btn" id="login-submit-btn">Войти</button>
            </div>
        </div>
    </div>
    
    <!-- Модальное окно создания пользователя (админ) -->
    <div class="create-user-modal" id="create-user-modal">
        <div class="create-user-form">
            <h3>Создание нового пользователя</h3>
            
            <div class="auth-input-group">
                <label for="new-username">Логин пользователя</label>
                <input type="text" id="new-username" class="auth-input" placeholder="Введите логин">
                <div class="auth-error" id="new-username-error"></div>
            </div>
            
            <div class="auth-input-group">
                <label for="new-password">Пароль</label>
                <input type="password" id="new-password" class="auth-input" placeholder="Введите пароль">
                <div class="auth-error" id="new-password-error"></div>
            </div>
            
            <div class="auth-input-group">
                <label for="new-name">Имя пользователя</label>
                <input type="text" id="new-name" class="auth-input" placeholder="Введите имя">
                <div class="auth-error" id="new-name-error"></div>
            </div>
            
            <div class="auth-error" id="new-user-general-error"></div>
            
            <div style="display: flex; gap: 10px; margin-top: 20px;">
                <button class="submit-btn" id="create-user-submit-btn">Создать</button>
                <button class="submit-btn" id="cancel-create-user-btn" style="background: #6c757d;">Отмена</button>
            </div>
        </div>
    </div>

    <div class="app-container">
        <!-- Хедер с авторизацией -->
        <div class="app-header">
            <div class="logo">
                <h1>💪 The BIG guy PRO</h1>
            </div>
            <div class="user-info" id="user-info">
                <div class="sync-status" id="sync-status">
                    <div class="sync-indicator"></div>
                    <span>Готов к работе</span>
                </div>
                <div class="user-avatar hidden" id="user-avatar"></div>
                <span id="user-name" class="hidden"></span>
                <button class="auth-btn" id="auth-btn">Войти</button>
                <button class="auth-btn hidden" id="logout-btn" style="background: #dc3545;">Выйти</button>
            </div>
        </div>
        
        <!-- Мобильное меню -->
        <button class="mobile-menu-btn" id="mobile-menu-btn">
            ☰ Меню
        </button>
        
        <!-- Навигация -->
        <div class="nav-container">
            <div class="nav-buttons" id="nav-buttons">
                <button class="nav-btn active" data-page="home">Главная</button>
                <button class="nav-btn" data-page="questionnaire">Создать тренировку</button>
                <button class="nav-btn" data-page="history">История</button>
                <button class="nav-btn" data-page="reflection">Рефлексия</button>
                <button class="nav-btn" data-page="support">❓ Поддержка</button>
                <!-- Админ-навигация (будет показана только админу) -->
                <button class="nav-btn admin-only hidden" data-page="admin" id="admin-nav-btn">⚙️ Администрация</button>
            </div>
        </div>
        
        <!-- Основной контент -->
        <div class="content-area">
            <!-- Главная страница -->
            <div id="home-page" class="page active">
                <div class="welcome-header">
                    <h1>Добро пожаловать в ваше тренировочное приложение! 💪</h1>
                    <div class="welcome-text">
                        <p>Теперь  <strong>приступим к нашим первым шагам вместе</strong> в этом невероятном приложении!</p>
                        <p><strong>Новые возможности:</strong> бесконечность не предел, мы готовы улучшаться и меняться только к лучшему!</p>
                    </div>
                </div>
                
                <div class="features-grid">
                    <div class="feature-card">
                        <h3>👤 Безопасный вход</h3>
                        <p>Доступ только по логину и паролю</p>
                    </div>
                    <div class="feature-card">
                        <h3>📋 Просмотр упражнений</h3>
                        <p>Смотрите какие упражнения вы выполняли в каждой тренировке</p>
                    </div>
                    <div class="feature-card">
                        <h3>📊 Детальная статистика</h3>
                        <p>Анализируйте свой прогресс по каждому упражнению</p>
                    </div>
                    <div class="feature-card">
                        <h3>❓ Поддержка</h3>
                        <p>Задавайте вопросы администратору</p>
                    </div>
                </div>
            </div>
            
            <!-- Анкета для создания тренировки -->
            <div id="questionnaire-page" class="page">
                <h2 style="text-align: center; color: #667eea; margin-bottom: 30px;">Создание плана тренировки</h2>
                
                <form id="questionnaire-form" class="questionnaire-form">
                    <!-- Пункт 1: Пол -->
                    <div class="form-group">
                        <h3>1. Укажите ваш пол</h3>
                        <div class="radio-grid">
                            <label class="option-label" data-value="male">
                                <input type="radio" name="gender" value="male" required>
                                Мужской
                            </label>
                            <label class="option-label" data-value="female">
                                <input type="radio" name="gender" value="female">
                                Женский
                            </label>
                        </div>
                    </div>
                    
                    <!-- Пункт 2: Вес -->
                    <div class="form-group">
                        <h3>2. Укажите ваш вес (кг)</h3>
                        <input type="number" id="weight" class="input-field" min="30" max="200" 
                               placeholder="Например: 75" required>
                    </div>
                    
                    <!-- Пункт 3: Уровень подготовки -->
                    <div class="form-group">
                        <h3>3. Ваш уровень подготовки</h3>
                        <div class="radio-grid">
                            <label class="option-label" data-value="beginner">
                                <input type="radio" name="level" value="beginner" required>
                                Начинающий (до 1 года)
                            </label>
                            <label class="option-label" data-value="intermediate">
                                <input type="radio" name="level" value="intermediate">
                                Средний (1-3 года)
                            </label>
                            <label class="option-label" data-value="advanced">
                                <input type="radio" name="level" value="advanced">
                                Продвинутый (более 3 лет)
                            </label>
                        </div>
                    </div>
                    
                    <!-- Пункт 4: Цель тренировок -->
                    <div class="form-group">
                        <h3>4. Основная цель тренировок</h3>
                        <div class="radio-grid">
                            <label class="option-label" data-value="strength">
                                <input type="radio" name="goal" value="strength" required>
                                Сила (увеличение рабочих весов)
                            </label>
                            <label class="option-label" data-value="hypertrophy">
                                <input type="radio" name="goal" value="hypertrophy">
                                Мышечная масса
                            </label>
                            <label class="option-label" data-value="endurance">
                                <input type="radio" name="goal" value="endurance">
                                Выносливость
                            </label>
                            <label class="option-label" data-value="fatloss">
                                <input type="radio" name="goal" value="fatloss">
                                Сжигание жира / похудение
                            </label>
                            <label class="option-label" data-value="streetlifting">
                                <input type="radio" name="goal" value="streetlifting">
                                Стритлифтинг (подтягивания/брусья)
                            </label>
                        </div>
                    </div>
                    
                    <!-- Пункт 5: Исключаемые группы мышц -->
                    <div class="form-group">
                        <h3>5. Какие группы мышц НЕ хотите тренировать?</h3>
                        <div class="checkbox-grid">
                            <label class="option-label" data-value="legs">
                                <input type="checkbox" name="exclude" value="legs">
                                Ноги
                            </label>
                            <label class="option-label" data-value="arms">
                                <input type="checkbox" name="exclude" value="arms">
                                Руки
                            </label>
                            <label class="option-label" data-value="back">
                                <input type="checkbox" name="exclude" value="back">
                                Спина
                            </label>
                            <label class="option-label" data-value="chest">
                                <input type="checkbox" name="exclude" value="chest">
                                Грудь
                            </label>
                            <label class="option-label" data-value="shoulders">
                                <input type="checkbox" name="exclude" value="shoulders">
                                Плечи
                            </label>
                            <label class="option-label" data-value="abs">
                                <input type="checkbox" name="exclude" value="abs">
                                Пресс
                            </label>
                        </div>
                    </div>
                    
                    <!-- Пункт 6: Целевые группы мышц -->
                    <div class="form-group">
                        <h3>6. На какие группы мышц сделать упор?</h3>
                        <div class="checkbox-grid">
                            <label class="option-label" data-value="legs">
                                <input type="checkbox" name="target" value="legs">
                                Ноги
                            </label>
                            <label class="option-label" data-value="arms">
                                <input type="checkbox" name="target" value="arms">
                                Руки
                            </label>
                            <label class="option-label" data-value="back">
                                <input type="checkbox" name="target" value="back">
                                Спина
                            </label>
                            <label class="option-label" data-value="chest">
                                <input type="checkbox" name="target" value="chest">
                                Грудь
                            </label>
                            <label class="option-label" data-value="shoulders">
                                <input type="checkbox" name="target" value="shoulders">
                                Плечи
                            </label>
                            <label class="option-label" data-value="abs">
                                <input type="checkbox" name="target" value="abs">
                                Пресс
                            </label>
                        </div>
                    </div>
                    
                    <!-- Дополнительные вопросы для стритлифтинга -->
                    <div class="form-group" id="streetlifting-group" style="display: none;">
                        <h3>🔧 Специальные параметры для стритлифтинга</h3>
                        <div style="margin-top: 15px;">
                            <label style="display: block; margin-bottom: 10px;">
                                Вес на брусьях (5ПМ в кг):
                                <input type="number" id="bars-5rm" class="input-field" min="0" max="200" 
                                       placeholder="Например: 45">
                            </label>
                            <label style="display: block; margin-bottom: 10px;">
                                Вес на турнике (5ПМ в кг):
                                <input type="number" id="pullups-5rm" class="input-field" min="0" max="100" 
                                       placeholder="Например: 24">
                            </label>
                            <label style="display: block; margin-bottom: 10px;">
                                Вес на трицепс (10-12ПМ в кг):
                                <input type="number" id="triceps-rm" class="input-field" min="0" max="50" 
                                       placeholder="Например: 11.5">
                            </label>
                            <label style="display: block;">
                                Вес на бицепс (10-12ПМ в кг):
                                <input type="number" id="biceps-rm" class="input-field" min="0" max="50" 
                                       placeholder="Например: 11.5">
                            </label>
                        </div>
                    </div>
                    
                    <div id="form-error" class="error-message hidden"></div>
                    
                    <button type="submit" class="submit-btn" id="submit-btn">
                        Получить программу тренировки
                    </button>
                </form>
            </div>
            
            <!-- Программа тренировки -->
            <div id="workout-page" class="page">
                <div class="workout-header">
                    <h2 style="color: #667eea;" id="workout-title">Ваша персонализированная программа</h2>
                    <div class="workout-date" id="workout-date"></div>
                </div>
                
                <div id="workout-content">
                    <!-- Сюда будет загружена программа -->
                </div>
                
                <div style="text-align: center; margin-top: 30px;">
                    <button class="submit-btn" id="instruction-btn" style="margin-bottom: 15px;">
                        📚 Инструктаж
                    </button>
                    <button class="submit-btn" id="complete-workout-btn" 
                            style="background: linear-gradient(135deg, #28a745 0%, #20c997 100%);">
                        ✅ Завершить тренировку
                    </button>
                </div>
            </div>
            
            <!-- История тренировок и рефлексий -->
            <div id="history-page" class="page">
                <div class="history-container">
                    <div class="history-sidebar">
                        <h3 style="color: #667eea; margin-bottom: 15px;">История тренировок</h3>
                        
                        <div class="history-filters">
                            <button class="filter-btn active" data-filter="all">Все</button>
                            <button class="filter-btn" data-filter="workouts">Тренировки</button>
                            <button class="filter-btn" data-filter="reflections">Рефлексии</button>
                        </div>
                        
                        <div id="history-list" class="history-list">
                            <!-- Сюда будет загружена история -->
                        </div>
                    </div>
                    
                    <div class="history-content" id="history-content">
                        <div id="history-empty" style="text-align: center; padding: 40px; color: #666;">
                            <h3>Выберите запись из списка</h3>
                            <p>Здесь отобразится подробная информация</p>
                        </div>
                        
                        <div id="history-details" class="hidden">
                            <!-- Детали выбранной записи -->
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Рефлексия -->
            <div id="reflection-page" class="page">
                <div class="reflection-container">
                    <h2 style="text-align: center; color: #667eea; margin-bottom: 30px;">Рефлексия</h2>
                    
                    <div class="reflection-editor">
                        <h3 style="margin-bottom: 15px;">💭 Запишите свои мысли о тренировке</h3>
                        
                        <div class="form-group">
                            <h4>Что получилось лучше всего?</h4>
                            <textarea id="reflection-success" class="reflection-textarea" 
                                      placeholder="Опишите свои успехи, что удалось сделать хорошо..."></textarea>
                        </div>
                        
                        <div class="form-group">
                            <h4>Что можно улучшить в следующий раз?</h4>
                            <textarea id="reflection-improve" class="reflection-textarea" 
                                      placeholder="Что было сложно, над чем стоит поработать..."></textarea>
                        </div>
                        
                        <div class="form-group">
                            <h4>Ваше настроение после тренировки:</h4>
                            <div class="mood-selector">
                                <div class="mood-option" data-mood="excellent">
                                    😊 Отлично
                                </div>
                                <div class="mood-option" data-mood="good">
                                    🙂 Хорошо
                                </div>
                                <div class="mood-option" data-mood="neutral">
                                    😐 Нормально
                                </div>
                                <div class="mood-option" data-mood="tired">
                                    😴 Устал
                                </div>
                                <div class="mood-option" data-mood="frustrated">
                                    😔 Расстроен
                                </div>
                            </div>
                        </div>
                        
                        <div id="reflection-error" class="error-message hidden"></div>
                        
                        <button class="submit-btn" id="save-reflection-btn">
                            💾 Сохранить рефлексию
                        </button>
                    </div>
                    
                    <div class="reflection-history">
                        <h3 style="margin-bottom: 15px;">📖 История рефлексий</h3>
                        <div id="reflection-list">
                            <!-- Список рефлексий -->
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Поддержка / Вопросы -->
            <div id="support-page" class="page">
                <div class="support-container">
                    <h2 style="text-align: center; color: #667eea; margin-bottom: 30px;">❓ Поддержка и вопросы</h2>
                    
                    <div class="question-form">
                        <h3 style="margin-bottom: 15px;">📝 Задайте свой вопрос</h3>
                        <p style="margin-bottom: 15px; color: #666; font-size: 14px;">
                            Задавайте вопросы администратору по работе приложения, техническим проблемам или предложениям по улучшению.
                        </p>
                        
                        <div class="auth-input-group">
                            <label for="question-text">Ваш вопрос:</label>
                            <textarea id="question-text" class="reflection-textarea" 
                                      placeholder="Опишите вашу проблему или вопрос максимально подробно..."
                                      style="min-height: 100px;"></textarea>
                            <div class="auth-error" id="question-text-error"></div>
                        </div>
                        
                        <div id="question-error" class="error-message hidden"></div>
                        <div id="question-success" class="success-message hidden"></div>
                        
                        <button class="submit-btn" id="submit-question-btn">
                            📨 Отправить вопрос
                        </button>
                    </div>
                    
                    <div class="question-list">
                        <h3 style="margin-bottom: 15px;">📬 Ваши вопросы</h3>
                        <div id="questions-list">
                            <!-- Список вопросов -->
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Админ-панель (видна только администратору) -->
            <div id="admin-page" class="page">
                <div class="admin-panel">
                    <div style="text-align: center; margin-bottom: 30px;">
                        <h1 style="color: #dc3545;">⚙️ Панель администратора</h1>
                        <p style="color: #666;">Управление приложением и пользователями</p>
                    </div>
                    
                    <!-- Статистика -->
                    <div class="admin-section">
                        <h3>📊 Статистика приложения</h3>
                        <div class="stats-grid">
                            <div class="stat-card">
                                <div class="stat-number" id="total-users">0</div>
                                <div class="stat-label">Пользователей</div>
                            </div>
                            <div class="stat-card">
                                <div class="stat-number" id="total-workouts">0</div>
                                <div class="stat-label">Тренировок</div>
                            </div>
                            <div class="stat-card">
                                <div class="stat-number" id="total-reflections">0</div>
                                <div class="stat-label">Рефлексий</div>
                            </div>
                            <div class="stat-card">
                                <div class="stat-number" id="total-questions">0</div>
                                <div class="stat-label">Вопросов</div>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Управление пользователями -->
                    <div class="admin-section">
                        <h3>👥 Управление пользователями</h3>
                        
                        <div style="margin-bottom: 20px;">
                            <button class="submit-btn admin-btn" id="create-user-btn">
                                ➕ Создать нового пользователя
                            </button>
                        </div>
                        
                        <div class="admin-card">
                            <h4>Список пользователей</h4>
                            <div id="users-list" class="user-list">
                                <!-- Список пользователей -->
                            </div>
                        </div>
                    </div>
                    
                    <!-- Просмотр данных пользователей -->
                    <div class="admin-section">
                        <h3>👁️ Просмотр данных пользователей</h3>
                        <div class="admin-grid">
                            <div class="admin-card">
                                <h4>Выберите пользователя:</h4>
                                <select id="user-select" class="input-field" style="margin-bottom: 15px;">
                                    <option value="">-- Выберите пользователя --</option>
                                </select>
                                
                                <div id="user-data-preview">
                                    <p style="color: #666; font-style: italic;">Выберите пользователя для просмотра данных</p>
                                </div>
                            </div>
                            
                            <div class="admin-card">
                                <h4>Данные пользователя:</h4>
                                <div id="selected-user-data" style="min-height: 200px;">
                                    <p style="color: #666; font-style: italic;">Здесь отобразятся данные выбранного пользователя</p>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Управление вопросами -->
                    <div class="admin-section">
                        <h3>💬 Управление вопросами пользователей</h3>
                        <div class="admin-card">
                            <h4>Неотвеченные вопросы</h4>
                            <div id="pending-questions" style="min-height: 200px; max-height: 400px; overflow-y: auto;">
                                <!-- Вопросы без ответов -->
                            </div>
                        </div>
                    </div>
                    
                    <!-- Системная информация -->
                    <div class="admin-section">
                        <h3>⚙️ Системная информация</h3>
                        <div class="admin-grid">
                            <div class="admin-card">
                                <h4>Очистка данных</h4>
                                <p style="margin-bottom: 15px; font-size: 14px;">
                                    Осторожно: это действие удалит все данные приложения.
                                </p>
                                <button class="submit-btn admin-btn" id="clear-all-data-btn">
                                    🗑️ Очистить все данные
                                </button>
                            </div>
                            
                            <div class="admin-card">
                                <h4>Экспорт данных</h4>
                                <p style="margin-bottom: 15px; font-size: 14px;">
                                    Экспортировать все данные приложения в файл JSON.
                                </p>
                                <button class="submit-btn" id="export-data-btn">
                                    📥 Экспорт данных
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // ==================== КОНФИГУРАЦИЯ ====================
        // Предустановленные аккаунты (только админ может создавать новые)
        // Будем динамически загружать из localStorage или использовать встроенные
        const PRESET_ACCOUNTS = [
            {
                username: 'admin',
                password: '12435',
                name: 'Администратор',
                isAdmin: true,
                id: 'admin_account'
            }
        ];

        // Динамическая база пользователей, которая будет загружаться и обновляться
        let DYNAMIC_USER_DATABASE = [];

        // ==================== ГЛОБАЛЬНЫЕ ПЕРЕМЕННЫЕ ====================
        let currentUser = null;
        let currentWorkout = null;
        let userData = {
            workouts: [],
            reflections: [],
            questions: [] // Добавляем вопросы
        };
        let isSyncing = false;
        let allUsersData = {}; // Данные всех пользователей

        // ==================== РАСШИРЕННАЯ БАЗА ДАННЫХ УПРАЖНЕНИЙ ====================
        const exerciseDatabase = {
            strength: [
                { name: "Приседания со штангой", description: "3 подхода по 5-8 повторений, отдых 2-3 мин", muscles: ["legs"], intensity: "тяжелая" },
                { name: "Жим лежа", description: "4 подхода по 5-8 повторений, отдых 2-3 мин", muscles: ["chest", "arms"], intensity: "тяжелая" },
                { name: "Становая тяга", description: "3 подхода по 3-5 повторений, отдых 3-4 мин", muscles: ["back", "legs"], intensity: "тяжелая" },
                { name: "Армейский жим", description: "3 подхода по 6-8 повторений", muscles: ["shoulders"], intensity: "средняя" },
                { name: "Подтягивания с весом", description: "3 подхода до отказа", muscles: ["back", "arms"], intensity: "тяжелая" }
            ],
            endurance: [
                { name: "Бег на дорожке", description: "30 минут в среднем темпе", muscles: ["legs"], intensity: "легкая" },
                { name: "Круговая тренировка", description: "8 упражнений по 45 сек, отдых 15 сек", muscles: ["full"], intensity: "средняя" },
                { name: "Плавание", description: "20 минут непрерывно", muscles: ["full"], intensity: "легкая" },
                { name: "Велотренажер", description: "40 минут, умеренная интенсивность", muscles: ["legs"], intensity: "легкая" }
            ],
            hypertrophy: [
                { name: "Разведение гантелей лежа", description: "4 подхода по 10-12 повторений", muscles: ["chest"], intensity: "средняя" },
                { name: "Сгибания рук с гантелями", description: "3 подхода по 12-15 повторений", muscles: ["arms"], intensity: "средняя" },
                { name: "Разгибания ног в тренажере", description: "4 подхода по 12-15 повторений", muscles: ["legs"], intensity: "средняя" },
                { name: "Тяга штанги в наклоне", description: "4 подхода по 10-12 повторений", muscles: ["back"], intensity: "средняя" }
            ],
            fatloss: [
                { name: "Интервальный бег", description: "10 интервалов: 1 мин быстро/1 мин медленно", muscles: ["legs"], intensity: "высокая" },
                { name: "Берпи", description: "5 подходов по 15 повторений", muscles: ["full"], intensity: "высокая" },
                { name: "Прыжки на скакалке", description: "10 минут непрерывно", muscles: ["legs"], intensity: "средняя" },
                { name: "Гребной тренажер", description: "20 минут, высокая интенсивность", muscles: ["full"], intensity: "высокая" }
            ],
            
            // Новые упражнения из файлов Excel
            male_bodybuilding_more_than_year: [
                { name: "Жим лежа 0°", description: "4 подхода по 8-12 повторений", muscles: ["chest", "arms"], intensity: "средняя" },
                { name: "Тяга вертикального блока", description: "4 подхода по 8-12 повторений", muscles: ["back"], intensity: "средняя" },
                { name: "Отведения гантелей", description: "3 подхода по 12-15 повторений", muscles: ["shoulders"], intensity: "средняя" },
                { name: "Французский жим лежа", description: "3 подхода по 8-12 повторений", muscles: ["arms"], intensity: "средняя" },
                { name: "Присед со штангой", description: "3 подхода по 6-8 повторений", muscles: ["legs"], intensity: "легкая" },
                { name: "Румынская тяга", description: "4 подхода по 8-12 повторений", muscles: ["legs", "back"], intensity: "средняя" },
                { name: "Разгибания ног в тренажере", description: "4 подхода по 8-12 повторений", muscles: ["legs"], intensity: "тяжелая" },
                { name: "Тяга горизонтального блока", description: "3 подхода по 12-15 повторений", muscles: ["back"], intensity: "легкая" },
                { name: "Разгибания рук в блоке", description: "4 подхода по 10-12 повторений", muscles: ["arms"], intensity: "тяжелая" },
                { name: "Жим лёжа 0° (тяжелая)", description: "4 подхода по 8-12 повторений", muscles: ["chest", "arms"], intensity: "тяжелая" },
                { name: "Тяга вертикального блока (тяжелая)", description: "4 подхода по 8-12 повторений", muscles: ["back"], intensity: "тяжелая" },
                { name: "Отведения гантелей (средняя)", description: "4 подхода по 8-12 повторений", muscles: ["shoulders"], intensity: "средняя" },
                { name: "Присед со штангой (средняя)", description: "4 подхода по 8-12 повторений", muscles: ["legs"], intensity: "средняя" },
                { name: "Жим лёжа 30°", description: "4 подхода по 8-12 повторений", muscles: ["chest", "shoulders"], intensity: "средняя" },
                { name: "Сгибания с супинацией на бицепс", description: "3 подхода по 8-12 повторений", muscles: ["arms"], intensity: "легкая" },
                { name: "Жим лёжа 0° (легкая)", description: "4 подхода по 6-8 повторений", muscles: ["chest", "arms"], intensity: "легкая" },
                { name: "Тяга вертикального блока (легкая)", description: "4 подхода по 6-8 повторений", muscles: ["back"], intensity: "легкая" },
                { name: "Французский жим в блоке из-за головы", description: "4 подхода по 8-12 повторений", muscles: ["arms"], intensity: "средняя" },
                { name: "Подъем на носки стоя в смите", description: "3 подхода по 12-15 повторений", muscles: ["legs"], intensity: "средняя" },
                { name: "Жим ногами с упоров в верх платформы", description: "3 подхода по 6-8 повторений", muscles: ["legs"], intensity: "средняя" },
                { name: "Жим ногами с упором в низ платформы", description: "3 подхода по 8-12 повторений", muscles: ["legs"], intensity: "средняя" },
                { name: "Жим штанги сидя", description: "3 подхода по 8-12 повторений", muscles: ["shoulders"], intensity: "легкая" }
            ],
            
            male_bodybuilding_less_than_year: [
                { name: "Жим лежа", description: "3 подхода по 8-12 повторений", muscles: ["chest", "arms"], intensity: "средняя" },
                { name: "Тяга вертикального блока", description: "3 подхода по 8-12 повторений", muscles: ["back"], intensity: "средняя" },
                { name: "Разгибания ног в тренажере", description: "3 подхода по 12-15 повторений", muscles: ["legs"], intensity: "легкая" },
                { name: "Сгибания ног в тренажере", description: "3 подхода по 12-15 повторений", muscles: ["legs"], intensity: "легкая" },
                { name: "Жим ногами с упоров в верх платформы", description: "3 подхода по 6-8 повторений", muscles: ["legs"], intensity: "средняя" },
                { name: "Жим ногами с упором в низ платформы", description: "3 подхода по 8-12 повторений", muscles: ["legs"], intensity: "средняя" },
                { name: "Разгибания рук в блоке", description: "3 подхода по 12-15 повторений", muscles: ["arms"], intensity: "средняя" },
                { name: "Жим лёжа 30°", description: "3 подхода по 8-12 повторений", muscles: ["chest", "shoulders"], intensity: "средняя" },
                { name: "Тяга горизонтального блока", description: "3 подхода по 6-8 повторений", muscles: ["back"], intensity: "тяжелая" },
                { name: "Жим лежа (тяжелая)", description: "3 подхода по 8-12 повторений", muscles: ["chest", "arms"], intensity: "тяжелая" },
                { name: "Тяга вертикального блока (легкая)", description: "3 подхода по 6-8 повторений", muscles: ["back"], intensity: "легкая" },
                { name: "Разгибания ног в тренажере (тяжелая)", description: "3 подхода по 8-12 повторений", muscles: ["legs"], intensity: "тяжелая" },
                { name: "Сгибания ног в тренажере (средняя)", description: "3 подхода по 8-12 повторений", muscles: ["legs"], intensity: "средняя" },
                { name: "Разгибания рук в блоке (тяжелая)", description: "3 подхода по 8-12 повторений", muscles: ["arms"], intensity: "тяжелая" },
                { name: "Сгибания на бицепс с супинацией", description: "3 подхода по 8-12 повторений", muscles: ["arms"], intensity: "средняя" },
                { name: "Отведения на дельты", description: "3 подхода по 12-15 повторений", muscles: ["shoulders"], intensity: "легкая" },
                { name: "Французский жим лежа", description: "3 подхода по 8-12 повторений", muscles: ["arms"], intensity: "средняя" },
                { name: "Жим лежа (легкая)", description: "3 подхода по 6-8 повторений", muscles: ["chest", "arms"], intensity: "легкая" },
                { name: "Тяга вертикального блока (средняя)", description: "4 подхода по 8-12 повторений", muscles: ["back"], intensity: "средняя" },
                { name: "Разгибания рук в блоке (тяжелая)", description: "4 подхода по 8-12 повторений", muscles: ["arms"], intensity: "тяжелая" },
                { name: "Разгибания ног в тренажере (средняя)", description: "4 подхода по 8-12 повторений", muscles: ["legs"], intensity: "средняя" },
                { name: "Сгибания ног в тренажере (легкая)", description: "3 подхода по 6-8 повторений", muscles: ["legs"], intensity: "легкая" },
                { name: "Отведения на дельты (средняя)", description: "3 подхода по 8-12 повторений", muscles: ["shoulders"], intensity: "средняя" },
                { name: "Тяга горизонтального блока (средняя)", description: "3 подхода по 8-12 повторений", muscles: ["back"], intensity: "средняя" }
            ],
            
            streetlifting: {
                weeks: 8,
                description: "Профессиональная 8-недельная программа для увеличения силы в подтягиваниях и отжиманиях на брусьях",
                exercises: [
                    { name: "Брусья", description: "Основное упражнение на грудь и трицепс", muscles: ["chest", "arms"], type: "силовое" },
                    { name: "Турник", description: "Основное упражнение на спину и бицепс", muscles: ["back", "arms"], type: "силовое" },
                    { name: "Доп. жим", description: "Вспомогательное упражнение для жима", muscles: ["chest", "shoulders"], type: "вспомогательное" },
                    { name: "Доп. тяга", description: "Вспомогательное упражнение для тяги", muscles: ["back"], type: "вспомогательное" },
                    { name: "Трицепс", description: "Изолирующее упражнение на трицепс", muscles: ["arms"], type: "изолирующее" },
                    { name: "Бицепс", description: "Изолирующее упражнение на бицепс", muscles: ["arms"], type: "изолирующее" },
                    { name: "Пресс", description: "Упражнение на мышцы живота", muscles: ["abs"], type: "дополнительное" },
                    { name: "Предплечье", description: "Упражнение на мышцы предплечья", muscles: ["arms"], type: "дополнительное" }
                ]
            },
            
            womens_fatloss: {
                weeks: 8,
                description: "8-недельная программа для женщин, фокус на похудение и общую физическую подготовку",
                exercises: [
                    { name: "Жим лежа", description: "Базовое упражнение на грудь", muscles: ["chest"], intensity: "разная" },
                    { name: "Тяга вертикального блока", description: "Упражнение на верхнюю часть спины", muscles: ["back"], intensity: "разная" },
                    { name: "Присед со штангой", description: "Базовое упражнение на ноги", muscles: ["legs"], intensity: "разная" },
                    { name: "Ягодичный мост", description: "Упражнение на ягодичные мышцы", muscles: ["legs"], intensity: "разная" },
                    { name: "Румынская тяга", description: "Упражнение на заднюю поверхность бедра", muscles: ["legs"], intensity: "разная" },
                    { name: "Жим сидя в Смите", description: "Упражнение на плечи", muscles: ["shoulders"], intensity: "разная" },
                    { name: "Отведения на дельты", description: "Изолирующее упражнение на плечи", muscles: ["shoulders"], intensity: "разная" },
                    { name: "Сгибания на бицепс с супинацией", description: "Упражнение на бицепс", muscles: ["arms"], intensity: "разная" },
                    { name: "Разгибания рук в блоке на трицепс", description: "Упражнение на трицепс", muscles: ["arms"], intensity: "разная" }
                ]
            }
        };

        // ==================== ИНИЦИАЛИЗАЦИЯ ПРИЛОЖЕНИЯ ====================
        document.addEventListener('DOMContentLoaded', function() {
            initEventListeners();
            checkAuthStatus();
            loadLocalData();
            initMobileMenu();
            initWorkoutExercises();
            loadAllUsersData(); // Загружаем данные всех пользователей
            
            // Загружаем динамическую базу пользователей
            loadDynamicUserDatabase();
            
            // Добавляем периодическую проверку обновлений данных
            setupAutoRefresh();
        });

        // ==================== ДИНАМИЧЕСКАЯ БАЗА ПОЛЬЗОВАТЕЛЕЙ ====================
        function loadDynamicUserDatabase() {
            // Загружаем пользователей из localStorage
            const savedUsers = localStorage.getItem('users');
            if (savedUsers) {
                try {
                    DYNAMIC_USER_DATABASE = JSON.parse(savedUsers);
                    console.log('Динамическая база пользователей загружена:', DYNAMIC_USER_DATABASE.length, 'пользователей');
                } catch (e) {
                    console.error('Ошибка загрузки динамической базы пользователей:', e);
                    DYNAMIC_USER_DATABASE = [];
                }
            } else {
                DYNAMIC_USER_DATABASE = [];
                // Добавляем тестовых пользователей, если база пуста
                addTestUsers();
            }
            
            // Сохраняем текущее состояние базы в localStorage для синхронизации
            localStorage.setItem('dynamicUserDatabase', JSON.stringify(DYNAMIC_USER_DATABASE));
        }

        function addTestUsers() {
            // Добавляем тестовых пользователей, если база пуста
            const testUsers = [
                {
                    "id": "user_1769791129815_vi305kte3",
                    "username": "Legenda",
                    "password": "11111",
                    "name": "Dimon",
                    "isAdmin": false,
                    "createdBy": "admin",
                    "creationDate": "2026-01-30T16:38:49.815Z"
                },
                {
                    "id": "user_1769795601828_85kql5hgf",
                    "username": "Masha",
                    "password": "12345",
                    "name": "Солнышко",
                    "isAdmin": false,
                    "createdBy": "admin",
                    "creationDate": "2026-01-30T17:53:21.828Z"
                }
               
                ];
            
            DYNAMIC_USER_DATABASE.push(...testUsers);
            saveDynamicUserDatabase();
            
            console.log('Добавлены тестовые пользователи:', testUsers.length);
        }

        function saveDynamicUserDatabase() {
            localStorage.setItem('users', JSON.stringify(DYNAMIC_USER_DATABASE));
            localStorage.setItem('dynamicUserDatabase', JSON.stringify(DYNAMIC_USER_DATABASE));
            
            // Также сохраняем в специальное хранилище для кода
            localStorage.setItem('userDatabaseBackup', JSON.stringify({
                timestamp: new Date().toISOString(),
                users: DYNAMIC_USER_DATABASE,
                totalUsers: DYNAMIC_USER_DATABASE.length
            }));
        }

        function syncUserDatabaseFromStorage() {
            // Проверяем, есть ли обновления в localStorage
            const storedUsers = localStorage.getItem('users');
            if (storedUsers) {
                try {
                    const newUsers = JSON.parse(storedUsers);
                    
                    // Обновляем динамическую базу
                    DYNAMIC_USER_DATABASE = newUsers;
                    
                    // Обновляем кэшированные данные
                    saveDynamicUserDatabase();
                    
                    return true;
                } catch (e) {
                    console.error('Ошибка синхронизации базы пользователей:', e);
                }
            }
            return false;
        }



        // ==================== АВТОМАТИЧЕСКОЕ ОБНОВЛЕНИЕ ДАННЫХ ====================
        let lastUpdateTime = Date.now();
        let autoRefreshInterval = null;

        function setupAutoRefresh() {
            // Проверяем обновления каждые 5 секунд
            autoRefreshInterval = setInterval(checkForUpdates, 5000);
            
            // Также проверяем при активации вкладки
            document.addEventListener('visibilitychange', function() {
                if (!document.hidden) {
                    checkForUpdates();
                }
            });
        }

        function checkForUpdates() {
            // Проверяем, есть ли новые данные в localStorage
            const currentTimestamp = localStorage.getItem('lastDataUpdate');
            
            if (currentTimestamp && parseInt(currentTimestamp) > lastUpdateTime) {
                console.log('Обнаружены обновленные данные, перезагружаем...');
                reloadUpdatedData();
                lastUpdateTime = parseInt(currentTimestamp);
            }
            
            // Проверяем обновления базы пользователей
            syncUserDatabaseFromStorage();
        }

        function reloadUpdatedData() {
            if (!currentUser) return;
            
            // Перезагружаем данные пользователей
            loadAllUsersData();
            
            // Синхронизируем базу пользователей
            syncUserDatabaseFromStorage();
            
            // Если текущий пользователь - админ, обновляем панель администратора
            if (currentUser && currentUser.isAdmin && document.getElementById('admin-page').classList.contains('active')) {
                updateAdminPanel();
                showNotification('Данные пользователей обновлены', 'info');
            }
            
            // Если пользователь залогинен, обновляем его данные
            loadUserData();
            updateHistoryDisplay();
            updateReflectionList();
            updateQuestionsList();
        }

        function markDataAsUpdated() {
            const timestamp = Date.now();
            localStorage.setItem('lastDataUpdate', timestamp.toString());
        }

        // ==================== ИНИЦИАЛИЗАЦИЯ УПРАЖНЕНИЙ ====================
        function initWorkoutExercises() {
            document.addEventListener('click', function(e) {
                if (e.target.classList.contains('exercise-toggle')) {
                    const exerciseDiv = e.target.closest('.workout-exercise');
                    const detailsDiv = exerciseDiv.querySelector('.exercise-details');
                    detailsDiv.classList.toggle('active');
                    e.target.textContent = detailsDiv.classList.contains('active') ? '−' : '+';
                }
            });
        }

        // ==================== МОБИЛЬНОЕ МЕНЮ ====================
        function initMobileMenu() {
            const menuBtn = document.getElementById('mobile-menu-btn');
            const navButtons = document.getElementById('nav-buttons');
            
            menuBtn.addEventListener('click', function() {
                navButtons.classList.toggle('active');
            });
            
            document.querySelectorAll('.nav-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    if (window.innerWidth <= 768) {
                        navButtons.classList.remove('active');
                    }
                });
            });
            
            document.addEventListener('click', function(event) {
                if (!navButtons.contains(event.target) && !menuBtn.contains(event.target)) {
                    navButtons.classList.remove('active');
                }
            });
        }

        // ==================== НАВИГАЦИЯ ====================
        document.querySelectorAll('.nav-btn').forEach(btn => {
            btn.addEventListener('click', function() {
                const pageId = this.getAttribute('data-page');
                showPage(pageId);
                
                document.querySelectorAll('.nav-btn').forEach(b => b.classList.remove('active'));
                this.classList.add('active');
            });
        });

        function showPage(pageId) {
            document.querySelectorAll('.page').forEach(page => {
                page.classList.remove('active');
            });
            
            const targetPage = document.getElementById(`${pageId}-page`);
            if (targetPage) {
                targetPage.classList.add('active');
                
                if (pageId === 'history') {
                    updateHistoryDisplay();
                }
                else if (pageId === 'reflection') {
                    updateReflectionList();
                }
                else if (pageId === 'support') {
                    updateQuestionsList();
                }
                else if (pageId === 'admin') {
                    if (currentUser && currentUser.isAdmin) {
                        updateAdminPanel();
                    } else {
                        showPage('home');
                    }
                }
            }
        }

        // ==================== СИСТЕМА АУТЕНТИФИКАЦИИ ====================
        function showAuthModal() {
            document.getElementById('auth-modal').classList.add('active');
            document.getElementById('login-form').classList.remove('hidden');
            clearAuthErrors();
        }

        function hideAuthModal() {
            document.getElementById('auth-modal').classList.remove('active');
            clearAuthErrors();
        }

        function clearAuthErrors() {
            document.querySelectorAll('.auth-error').forEach(el => {
                el.textContent = '';
                el.style.display = 'none';
            });
        }

        function showAuthError(elementId, message) {
            const element = document.getElementById(elementId);
            element.textContent = message;
            element.style.display = 'block';
        }

        function loginUser(username, password) {
            // Сначала проверяем предустановленные аккаунты
            const presetAccount = PRESET_ACCOUNTS.find(acc => 
                acc.username === username && acc.password === password
            );
            
            if (presetAccount) {
                return {
                    success: true,
                    user: {
                        id: presetAccount.id,
                        username: presetAccount.username,
                        name: presetAccount.name,
                        isAdmin: presetAccount.isAdmin || false
                    }
                };
            }
            
            // Затем проверяем динамическую базу пользователей
            const dynamicUser = DYNAMIC_USER_DATABASE.find(u => u.username === username && u.password === password);
            
            if (dynamicUser) {
                return { 
                    success: true, 
                    user: {
                        id: dynamicUser.id,
                        username: dynamicUser.username,
                        name: dynamicUser.name,
                        isAdmin: dynamicUser.isAdmin || false
                    }
                };
            }
            
            // Если не нашли в динамической базе, проверяем старую систему (для совместимости)
            const users = JSON.parse(localStorage.getItem('users') || '[]');
            const legacyUser = users.find(u => u.username === username && u.password === password);
            
            if (legacyUser) {
                // Добавляем этого пользователя в динамическую базу
                if (!DYNAMIC_USER_DATABASE.some(u => u.id === legacyUser.id)) {
                    DYNAMIC_USER_DATABASE.push(legacyUser);
                    saveDynamicUserDatabase();
                }
                
                return { 
                    success: true, 
                    user: {
                        id: legacyUser.id,
                        username: legacyUser.username,
                        name: legacyUser.name,
                        isAdmin: legacyUser.isAdmin || false
                    }
                };
            }
            
            return { success: false, message: 'Неверный логин или пароль' };
        }

        // ==================== ОБРАБОТЧИКИ ФОРМЫ ====================
        document.getElementById('questionnaire-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const formData = {
                gender: document.querySelector('input[name="gender"]:checked')?.value,
                weight: document.getElementById('weight').value,
                level: document.querySelector('input[name="level"]:checked')?.value,
                goal: document.querySelector('input[name="goal"]:checked')?.value,
                exclude: Array.from(document.querySelectorAll('input[name="exclude"]:checked'))
                            .map(cb => cb.value),
                target: Array.from(document.querySelectorAll('input[name="target"]:checked'))
                            .map(cb => cb.value),
                date: new Date().toLocaleDateString('ru-RU')
            };
            
            if (formData.goal === 'streetlifting') {
                formData.bars5RM = document.getElementById('bars-5rm').value;
                formData.pullups5RM = document.getElementById('pullups-5rm').value;
                formData.tricepsRM = document.getElementById('triceps-rm').value;
                formData.bicepsRM = document.getElementById('biceps-rm').value;
            }
            
            const errorElement = document.getElementById('form-error');
            if (!formData.gender || !formData.weight || !formData.level || !formData.goal) {
                errorElement.textContent = 'Пожалуйста, заполните все обязательные поля!';
                errorElement.classList.remove('hidden');
                return;
            }
            
            if (formData.weight < 30 || formData.weight > 200) {
                errorElement.textContent = 'Пожалуйста, укажите реальный вес (30-200 кг)';
                errorElement.classList.remove('hidden');
                return;
            }
            
            if (formData.goal === 'streetlifting') {
                if (!formData.bars5RM || !formData.pullups5RM || !formData.tricepsRM || !formData.bicepsRM) {
                    errorElement.textContent = 'Для программы стритлифтинга заполните все специальные параметры!';
                    errorElement.classList.remove('hidden');
                    return;
                }
            }
            
            errorElement.classList.add('hidden');
            
            const workoutProgram = generateWorkoutProgramWithExercises(formData);
            currentWorkout = {
                ...formData,
                program: workoutProgram,
                id: Date.now(),
                completed: false,
                programType: workoutProgram.type,
                exercises: workoutProgram.exercises
            };
            
            showWorkoutPage(workoutProgram, formData.goal);
        });

        document.querySelectorAll('input[name="goal"]').forEach(radio => {
            radio.addEventListener('change', function() {
                const streetliftingGroup = document.getElementById('streetlifting-group');
                streetliftingGroup.style.display = this.value === 'streetlifting' ? 'block' : 'none';
            });
        });

        // ==================== ГЕНЕРАЦИЯ ПРОГРАММЫ ====================
        function generateWorkoutProgramWithExercises(formData) {
            const goal = formData.goal;
            const gender = formData.gender;
            const level = formData.level;
            
            let programType = 'general';
            let programData = null;
            let exercises = [];
            
            if (goal === 'streetlifting' && gender === 'male' && level === 'advanced') {
                programType = 'streetlifting';
                programData = generateStreetliftingProgram(formData);
                exercises = exerciseDatabase.streetlifting.exercises;
            } 
            else if (gender === 'female' && (goal === 'fatloss' || goal === 'hypertrophy')) {
                programType = goal === 'fatloss' ? 'womens_fatloss' : 'womens_bodybuilding';
                programData = generateWomensProgram(formData, goal);
                exercises = exerciseDatabase.womens_fatloss.exercises;
            }
            else {
                programType = goal;
                programData = generateGeneralProgram(formData);
                exercises = programData.exercises || [];
            }
            
            return {
                type: programType,
                data: programData,
                description: getProgramDescription(programType, formData),
                exercises: exercises.map(ex => ({
                    ...ex,
                    date: new Date().toISOString(),
                    completed: false,
                    notes: ""
                }))
            };
        }

        function generateStreetliftingProgram(formData) {
            return {
                name: "Программа стритлифтинга (8 недель)",
                description: "Профессиональная программа для увеличения силы в подтягиваниях и отжиманиях на брусьях",
                weeks: [],
                userData: {
                    bars5RM: formData.bars5RM,
                    pullups5RM: formData.pullups5RM,
                    tricepsRM: formData.tricepsRM,
                    bicepsRM: formData.bicepsRM,
                    bodyWeight: formData.weight
                }
            };
        }

        function generateWomensProgram(formData, goal) {
            return {
                name: goal === 'fatloss' ? "Женская программа (похудение)" : "Женская программа (бодибилдинг)",
                description: goal === 'fatloss' 
                    ? "8-недельная программа для похудение и общей физической подготовки" 
                    : "8-недельная программа для набора мышечной массы",
                weeks: [],
                schedule: goal === 'fatloss' ? 3 : 4
            };
        }

        function generateGeneralProgram(formData) {
            let exercises = [];
            const goal = formData.goal;
            const level = formData.level;
            const gender = formData.gender;
            
            // Определяем, какую базу упражнений использовать
            let exercisePool = [];
            
            if (gender === 'male' && goal === 'hypertrophy') {
                if (level === 'beginner') {
                    // Меньше года опыта
                    exercisePool = exerciseDatabase.male_bodybuilding_less_than_year;
                } else if (level === 'intermediate' || level === 'advanced') {
                    // Более года опыта
                    exercisePool = exerciseDatabase.male_bodybuilding_more_than_year;
                }
            }
            
            // Если не нашли специфическую программу, используем общую
            if (exercisePool.length === 0 && exerciseDatabase[goal]) {
                exercises = [...exerciseDatabase[goal]];
            } else if (exercisePool.length > 0) {
                exercises = [...exercisePool];
            }
            
            // Фильтрация по исключенным группам мышц
            if (formData.exclude.length > 0) {
                exercises = exercises.filter(exercise => {
                    if (!exercise.muscles) return true;
                    return !exercise.muscles.some(muscle => formData.exclude.includes(muscle));
                });
            }
            
            // Приоритет для целевые группы мышц
            if (formData.target.length > 0) {
                // Сначала добавляем упражнения на целевые группы
                const targetExercises = exercises.filter(exercise => {
                    if (!exercise.muscles) return false;
                    return exercise.muscles.some(muscle => formData.target.includes(muscle));
                });
                
                // Затем добавляем остальные
                const otherExercises = exercises.filter(exercise => {
                    if (!exercise.muscles) return true;
                    return !exercise.muscles.some(muscle => formData.target.includes(muscle));
                });
                
                exercises = [...targetExercises, ...otherExercises];
            }
            
            // Ограничиваем количество упражнений
            const maxExercises = level === 'beginner' ? 4 : 6;
            exercises = exercises.slice(0, maxExercises);
            
            // Если упражнений мало, добавляем базовые
            if (exercises.length < 4) {
                exercises.push(
                    { name: "Кардио-разминка", description: "10 минут легкого бега или ходьбы", muscles: ["legs"], intensity: "легкая" },
                    { name: "Общая разминка", description: "Динамическая растяжка всех суставов", muscles: ["full"], intensity: "легкая" },
                    { name: "Отжимания", description: "3 подхода по 10-15 повторений", muscles: ["chest", "arms"], intensity: "средняя" },
                    { name: "Приседания", description: "3 подхода по 10-15 повторений", muscles: ["legs"], intensity: "средняя" }
                );
            }
            
            return {
                name: getGoalName(formData.goal),
                exercises: exercises,
                duration: level === 'beginner' ? "4 недели" : "8 недель",
                level: level,
                gender: gender
            };
        }

        function getProgramDescription(type, formData) {
            const descriptions = {
                streetlifting: "8-недельная программа стритлифтинга для опытных спортсменов.",
                womens_fatloss: "8-недельная программа для женщин с фокусом на похудение.",
                womens_bodybuilding: "8-недельная программа для женщин с фокусом на мышечную массу.",
                strength: "Программа для развития максимальной силы.",
                hypertrophy: "Программа для набора мышечной массы.",
                endurance: "Программа для развития выносливости.",
                fatloss: "Программа для сжигания жира."
            };
            
            return descriptions[type] || "Персонализированная программа тренировок";
        }

        function getGoalName(goal) {
            const names = {
                strength: "Силовая программа",
                hypertrophy: "Программа на массу",
                endurance: "Программа на выносливость",
                fatloss: "Программа для похудения"
            };
            
            return names[goal] || "Общая программа";
        }

        // ==================== ПОКАЗ ПРОГРАММЫ ТРЕНИРОВКИ ====================
        function showWorkoutPage(workoutProgram, goal) {
            const workoutContent = document.getElementById('workout-content');
            const workoutTitle = document.getElementById('workout-title');
            const workoutDate = document.getElementById('workout-date');
            
            workoutDate.textContent = new Date().toLocaleDateString('ru-RU', {
                day: '2-digit',
                month: '2-digit',
                year: 'numeric'
            });
            
            workoutContent.innerHTML = '';
            
            let planClass = 'workout-plan';
            if (workoutProgram.type === 'streetlifting') {
                planClass = 'streetlifting-plan';
                workoutTitle.textContent = "🏋️‍♂️ Программа стритлифтинга";
            } else if (workoutProgram.type.includes('womens')) {
                planClass = 'womens-plan';
                workoutTitle.textContent = workoutProgram.type === 'womens_fatloss' 
                    ? "👩 Программа для похудения" 
                    : "👩 Программа для бодибилдинга";
            } else {
                workoutTitle.textContent = "Ваша персонализированная программа";
            }
            
            const planDiv = document.createElement('div');
            planDiv.className = planClass;
            
            let html = '';
            
            if (workoutProgram.type === 'streetlifting') {
                html = renderStreetliftingProgram(workoutProgram.data);
            } else if (workoutProgram.type.includes('womens')) {
                html = renderWomensProgram(workoutProgram.data);
            } else {
                html = renderGeneralProgramWithExercises(workoutProgram.data, workoutProgram.exercises);
            }
            
            planDiv.innerHTML = html;
            workoutContent.appendChild(planDiv);
            
            showPage('workout');
            document.querySelectorAll('.nav-btn').forEach(btn => btn.classList.remove('active'));
            document.querySelector('[data-page="questionnaire"]').classList.add('active');
        }

        function renderGeneralProgramWithExercises(program, exercises) {
            let html = `
                <h3>${program.name}</h3>
                <p>Продолжительность: ${program.duration}</p>
                ${program.level ? `<p>Уровень: ${getLevelName(program.level)}</p>` : ''}
                ${program.gender ? `<p>Пол: ${program.gender === 'male' ? 'Мужской' : 'Женский'}</p>` : ''}
                
                <h4 style="margin: 20px 0 15px;">Ваш план на сегодня:</h4>
            `;
            
            exercises.forEach((exercise, index) => {
                html += `
                    <div class="workout-exercise">
                        <h4>
                            ${index + 1}. ${exercise.name}
                            <button class="exercise-toggle">+</button>
                        </h4>
                        <p>${exercise.description}</p>
                        <div class="exercise-details">
                            <div class="exercise-stats">
                                <div class="stat-item">
                                    <span class="stat-icon">⚡</span>
                                    <span>${exercise.intensity || 'Средняя'}</span>
                                </div>
                                <div class="stat-item">
                                    <span class="stat-icon">💪</span>
                                    <span>${exercise.muscles ? exercise.muscles.join(', ') : 'Общая'}</span>
                                </div>
                                ${exercise.type ? `
                                <div class="stat-item">
                                    <span class="stat-icon">📊</span>
                                    <span>${exercise.type}</span>
                                </div>` : ''}
                            </div>
                        </div>
                    </div>
                `;
            });
            
            html += `
                <div style="background: #e6eeff; padding: 15px; border-radius: 10px; margin-top: 20px;">
                    <h4>💡 Рекомендации:</h4>
                    <p>• Разминка: 10-15 минут кардио + динамическая растяжка</p>
                    <p>• Заминка: 5-10 минут растяжки всех рабочих мышц</p>
                    <p>• Пейте воду во время тренировки</p>
                    <p>• Слушайте свое тело - не тренируйтесь через боль</p>
                    ${program.level === 'beginner' ? `<p>• Для начинающих: сосредоточьтесь на технике, а не на весах</p>` : ''}
                    ${program.level === 'advanced' ? `<p>• Для продвинутых: контролируйте восстановление между тренировками</p>` : ''}
                </div>
            `;
            
            return html;
        }

        function renderStreetliftingProgram(program) {
            let html = `
                <h3>${program.name}</h3>
                <p>${program.description}</p>
                
                <div style="background: rgba(255,255,255,0.1); padding: 15px; border-radius: 10px; margin: 20px 0;">
                    <h4>📊 Ваши параметры:</h4>
                    <p>• Вес на брусьях (5ПМ): <strong>${program.userData.bars5RM} кг</strong></p>
                    <p>• Вес на турнике (5ПМ): <strong>${program.userData.pullups5RM} кг</strong></p>
                    <p>• Собственный вес: <strong>${program.userData.bodyWeight} кг</strong></p>
                </div>
                
                <h4 style="margin-top: 25px;">📅 Упражнения программы:</h4>
            `;
            
            exerciseDatabase.streetlifting.exercises.forEach((exercise, index) => {
                html += `
                    <div class="workout-exercise">
                        <h4>
                            ${index + 1}. ${exercise.name}
                            <button class="exercise-toggle">+</button>
                        </h4>
                        <p>${exercise.description}</p>
                        <div class="exercise-details">
                            <div class="exercise-stats">
                                <div class="stat-item">
                                    <span class="stat-icon">💪</span>
                                    <span>${exercise.muscles.join(', ')}</span>
                                </div>
                                <div class="stat-item">
                                    <span class="stat-icon">📊</span>
                                    <span>${exercise.type}</span>
                                </div>
                            </div>
                        </div>
                    </div>
                `;
            });
            
            html += `
                <div style="margin-top: 20px; padding: 15px; background: rgba(255,152,0,0.1); border-radius: 10px; border: 2px solid #ff9800;">
                    <h4>📝 Инструкция:</h4>
                    <p>• Тренируйтесь 2 раза в неделю с перерывом 2-3 дня</p>
                    <p>• Обязательно делайте разминку перед тренировкой</p>
                    <p>• Соблюдайте технику выполнения упражнений</p>
                    <p>• На 8-й неделе тестируйте новые максимумы</p>
                </div>
            `;
            
            return html;
        }

        function renderWomensProgram(program) {
            let html = `
                <h3>${program.name}</h3>
                <p>${program.description}</p>
                
                <div style="background: rgba(255,255,255,0.1); padding: 15px; border-radius: 10px; margin: 20px 0;">
                    <h4>📅 График тренировок:</h4>
                    <p>• ${program.schedule} тренировки в неделю</p>
                    <p>• Продолжительность: 8 недель</p>
                    <p>• Интенсивность: прогрессивная (легкая → средняя → тяжелая)</p>
                </div>
                
                <h4 style="margin-top: 25px;">📋 Основные упражнения:</h4>
            `;
            
            exerciseDatabase.womens_fatloss.exercises.forEach((exercise, index) => {
                html += `
                    <div class="workout-exercise">
                        <h4>
                            ${index + 1}. ${exercise.name}
                            <button class="exercise-toggle">+</button>
                        </h4>
                        <p>${exercise.description}</p>
                        <div class="exercise-details">
                            <div class="exercise-stats">
                                <div class="stat-item">
                                    <span class="stat-icon">💪</span>
                                    <span>${exercise.muscles.join(', ')}</span>
                                </div>
                                <div class="stat-item">
                                    <span class="stat-icon">⚡</span>
                                    <span>Интенсивность: ${exercise.intensity}</span>
                                </div>
                            </div>
                        </div>
                    </div>
                `;
            });
            
            html += `
                <div style="margin-top: 20px; padding: 15px; background: rgba(244,143,177,0.1); border-radius: 10px; border: 2px solid #f48fb1;">
                    <h4>💡 Рекомендации:</h4>
                    <p>• Соблюдайте график тренировок</p>
                    <p>• Отдыхайте 1-2 минуты между подходами</p>
                    <p>• Следите за техникой выполнения</p>
                    <p>• Питайтесь сбалансированно</p>
                </div>
            `;
            
            return html;
        }

        // ==================== АВТОРИЗАЦИЯ И СИНХРОНИЗАЦИЯ ====================
        function updateUIAfterLogin() {
            document.getElementById('auth-btn').classList.add('hidden');
            document.getElementById('logout-btn').classList.remove('hidden');
            document.getElementById('user-avatar').classList.remove('hidden');
            document.getElementById('user-name').classList.remove('hidden');
            
            const avatar = document.getElementById('user-avatar');
            avatar.textContent = currentUser.name.charAt(0).toUpperCase();
            
            if (currentUser.isAdmin) {
                avatar.style.borderColor = '#dc3545';
                document.getElementById('admin-nav-btn').classList.remove('hidden');
            }
            
            document.getElementById('user-name').textContent = currentUser.name;
            
            showNotification(`Добро пожаловать, ${currentUser.name}!`, 'success');
            hideAuthModal();
            
            // Показываем главную страницу
            showPage('home');
            document.querySelectorAll('.nav-btn').forEach(btn => btn.classList.remove('active'));
            document.querySelector('[data-page="home"]').classList.add('active');
        }

        function logout() {
            // Сохраняем данные перед выходом
            if (currentUser) {
                saveUserData();
            }
            
            currentUser = null;
            userData = { workouts: [], reflections: [], questions: [] };
            
            document.getElementById('auth-btn').classList.remove('hidden');
            document.getElementById('logout-btn').classList.add('hidden');
            document.getElementById('user-avatar').classList.add('hidden');
            document.getElementById('user-name').classList.add('hidden');
            document.getElementById('admin-nav-btn').classList.add('hidden');
            
            updateHistoryDisplay();
            updateReflectionList();
            updateQuestionsList();
            
            showNotification('Вы вышли из системы', 'info');
            
            // Показываем главную страницу
            showPage('home');
            document.querySelectorAll('.nav-btn').forEach(btn => btn.classList.remove('active'));
            document.querySelector('[data-page="home"]').classList.add('active');
        }

        function checkAuthStatus() {
            const savedUser = localStorage.getItem('currentUser');
            if (savedUser) {
                try {
                    currentUser = JSON.parse(savedUser);
                    updateUIAfterLogin();
                    syncUserData();
                } catch (e) {
                    console.error('Ошибка загрузки пользователя:', e);
                }
            }
        }

        function syncUserData() {
            if (!currentUser) return;
            
            isSyncing = true;
            updateSyncStatus('syncing');
            
            try {
                localStorage.setItem('currentUser', JSON.stringify(currentUser));
                
                // Загружаем данные пользователя
                loadUserData();
                
                updateSyncStatus('success');
                showNotification('Данные загружены', 'success');
                
                updateHistoryDisplay();
                updateReflectionList();
                updateQuestionsList();
                
            } catch (error) {
                console.error('Ошибка синхронизации:', error);
                updateSyncStatus('error');
                showNotification('Ошибка загрузки данных', 'error');
            } finally {
                isSyncing = false;
            }
        }

        function updateSyncStatus(status) {
            const indicator = document.querySelector('.sync-indicator');
            const text = document.querySelector('#sync-status span');
            
            indicator.className = 'sync-indicator';
            
            switch(status) {
                case 'syncing':
                    indicator.classList.add('syncing');
                    text.textContent = 'Синхронизация...';
                    break;
                case 'success':
                    text.textContent = 'Синхронизировано';
                    break;
                case 'error':
                    indicator.classList.add('error');
                    text.textContent = 'Ошибка синхронизации';
                    break;
                default:
                    text.textContent = 'Готов к работе';
            }
        }

        // ==================== РАБОТА С ДАННЫМИ ====================
        function loadLocalData() {
            if (!currentUser) {
                const savedWorkouts = localStorage.getItem('localWorkouts');
                const savedReflections = localStorage.getItem('localReflections');
                const savedQuestions = localStorage.getItem('localQuestions');
                
                if (savedWorkouts) {
                    userData.workouts = JSON.parse(savedWorkouts);
                }
                if (savedReflections) {
                    userData.reflections = JSON.parse(savedReflections);
                }
                if (savedQuestions) {
                    userData.questions = JSON.parse(savedQuestions);
                }
            }
            
            updateHistoryDisplay();
            updateReflectionList();
            updateQuestionsList();
        }

        function loadUserData() {
            if (!currentUser) return;
            
            const savedData = localStorage.getItem(`userData_${currentUser.id}`);
            if (savedData) {
                try {
                    const data = JSON.parse(savedData);
                    userData.workouts = data.workouts || [];
                    userData.reflections = data.reflections || [];
                    userData.questions = data.questions || [];
                } catch (e) {
                    console.error('Ошибка загрузки данных пользователя:', e);
                }
            }
        }

        function saveUserData() {
            if (!currentUser) return;
            
            localStorage.setItem(`userData_${currentUser.id}`, JSON.stringify(userData));
            
            // Обновляем общие данные всех пользователей
            allUsersData[currentUser.id] = {
                ...currentUser,
                data: userData
            };
            localStorage.setItem('allUsersData', JSON.stringify(allUsersData));
            
            // Отмечаем, что данные были обновлены
            markDataAsUpdated();
        }

        function loadAllUsersData() {
            const savedData = localStorage.getItem('allUsersData');
            if (savedData) {
                try {
                    allUsersData = JSON.parse(savedData);
                } catch (e) {
                    console.error('Ошибка загрузки данных всех пользователей:', e);
                    allUsersData = {};
                }
            }
        }

        function saveWorkout(workout) {
            workout.id = Date.now();
            workout.userId = currentUser ? currentUser.id : 'anonymous';
            workout.date = new Date().toISOString();
            
            if (!workout.exercises && workout.program && workout.program.exercises) {
                workout.exercises = workout.program.exercises;
            }
            
            userData.workouts.unshift(workout);
            updateHistoryDisplay();
            
            if (currentUser) {
                saveUserData();
            } else {
                localStorage.setItem('localWorkouts', JSON.stringify(userData.workouts));
            }
            
            showNotification('Тренировка сохранена', 'success');
        }

        function saveReflection(reflectionData) {
            const reflection = {
                id: Date.now(),
                userId: currentUser ? currentUser.id : 'anonymous',
                date: new Date().toISOString(),
                success: reflectionData.success,
                improve: reflectionData.improve,
                mood: reflectionData.mood
            };
            
            userData.reflections.unshift(reflection);
            updateReflectionList();
            
            if (currentUser) {
                saveUserData();
            } else {
                localStorage.setItem('localReflections', JSON.stringify(userData.reflections));
            }
            
            showNotification('Рефлексия сохранена', 'success');
            
            document.getElementById('reflection-success').value = '';
            document.getElementById('reflection-improve').value = '';
            document.querySelectorAll('.mood-option').forEach(opt => opt.classList.remove('selected'));
        }

        // ==================== СИСТЕМА ВОПРОСОВ ====================
        function saveQuestion(questionText) {
            const question = {
                id: Date.now(),
                userId: currentUser.id,
                username: currentUser.username,
                name: currentUser.name,
                text: questionText,
                date: new Date().toISOString(),
                answered: false,
                answer: null,
                answerDate: null
            };
            
            userData.questions.unshift(question);
            updateQuestionsList();
            
            // Сохраняем в общие вопросы
            const allQuestions = JSON.parse(localStorage.getItem('allQuestions') || '[]');
            allQuestions.unshift(question);
            localStorage.setItem('allQuestions', JSON.stringify(allQuestions));
            
            saveUserData();
            
            showNotification('Вопрос отправлен администратору', 'success');
            
            // Очищаем поле ввода
            document.getElementById('question-text').value = '';
            document.getElementById('question-text-error').style.display = 'none';
            
            // Показываем сообщение об успехе
            const successElement = document.getElementById('question-success');
            successElement.textContent = 'Ваш вопрос отправлен! Администратор ответит в ближайшее время.';
            successElement.classList.remove('hidden');
            
            setTimeout(() => {
                successElement.classList.add('hidden');
            }, 5000);
        }

        function updateQuestionsList() {
            const listDiv = document.getElementById('questions-list');
            const questions = userData.questions.sort((a, b) => new Date(b.date) - new Date(a.date));
            
            if (questions.length === 0) {
                listDiv.innerHTML = `
                    <div style="text-align: center; padding: 40px; color: #666;">
                        <p>У вас пока нет отправленных вопросов</p>
                        <p style="font-size: 14px; margin-top: 10px;">Задайте свой вопрос администратору в форме выше</p>
                    </div>
                `;
                return;
            }
            
            let html = '';
            questions.forEach(question => {
                const date = new Date(question.date).toLocaleDateString('ru-RU', {
                    day: '2-digit',
                    month: '2-digit',
                    year: 'numeric',
                    hour: '2-digit',
                    minute: '2-digit'
                });
                
                html += `
                    <div class="question-item ${question.answered ? 'answered' : ''}">
                        <div class="question-header">
                            <div>
                                <div class="question-date">${date}</div>
                                <div class="question-status ${question.answered ? 'answered' : 'pending'}">
                                    ${question.answered ? 'Ответ получен' : 'Ожидает ответа'}
                                </div>
                            </div>
                        </div>
                        <div class="question-text">${question.text}</div>
                        ${question.answered ? `
                        <div class="answer-section">
                            <span class="answer-label">Ответ администратора:</span>
                            <div class="answer-text">${question.answer}</div>
                            ${question.answerDate ? `
                            <div style="font-size: 12px; color: #666; margin-top: 5px;">
                                Ответ получен: ${new Date(question.answerDate).toLocaleDateString('ru-RU', {
                                    day: '2-digit',
                                    month: '2-digit',
                                    year: 'numeric',
                                    hour: '2-digit',
                                    minute: '2-digit'
                                })}
                            </div>` : ''}
                        </div>` : ''}
                    </div>
                `;
            });
            
            listDiv.innerHTML = html;
        }

        // ==================== АДМИН-ПАНЕЛЬ ====================
        function updateAdminPanel() {
            if (!currentUser || !currentUser.isAdmin) return;
            
            // Обновляем динамическую базу пользователей
            loadDynamicUserDatabase();
            
            // Объединяем предустановленные аккаунты и динамические
            const allUsers = [...PRESET_ACCOUNTS, ...DYNAMIC_USER_DATABASE];
            
            // Обновляем статистику
            let totalWorkouts = 0;
            let totalReflections = 0;
            let totalQuestions = 0;
            
            Object.values(allUsersData).forEach(userDataItem => {
                if (userDataItem.data) {
                    totalWorkouts += userDataItem.data.workouts?.length || 0;
                    totalReflections += userDataItem.data.reflections?.length || 0;
                    totalQuestions += userDataItem.data.questions?.length || 0;
                }
            });
            
            document.getElementById('total-users').textContent = allUsers.length;
            document.getElementById('total-workouts').textContent = totalWorkouts;
            document.getElementById('total-reflections').textContent = totalReflections;
            document.getElementById('total-questions').textContent = totalQuestions;
            
            // Обновляем список пользователей
            updateUsersList(allUsers);
            
            // Обновляем список вопросов
            updateAdminQuestionsList();
            
            // Обновляем список пользователей для выбора
            updateUserSelect(allUsers);
        }

        function updateUsersList(users) {
            const usersList = document.getElementById('users-list');
            
            if (users.length === 0) {
                usersList.innerHTML = '<p style="color: #666; font-style: italic;">Нет зарегистрированных пользователей</p>';
                return;
            }
            
            let html = '';
            users.forEach(user => {
                const userDataItem = allUsersData[user.id];
                const workoutsCount = userDataItem?.data?.workouts?.length || 0;
                const reflectionsCount = userDataItem?.data?.reflections?.length || 0;
                const questionsCount = userDataItem?.data?.questions?.length || 0;
                
                html += `
                    <div class="user-item ${user.isAdmin ? 'admin' : ''}">
                        <div>
                            <div style="font-weight: 500;">${user.name} ${user.isAdmin ? '(Админ)' : ''}</div>
                            <div style="font-size: 12px; color: #666;">Логин: ${user.username}</div>
                            <div style="font-size: 12px; color: #666;">
                                Тренировок: ${workoutsCount} | Рефлексий: ${reflectionsCount} | Вопросов: ${questionsCount}
                            </div>
                        </div>
                        <div class="user-actions">
                            <button class="user-action-btn view" onclick="viewUserData('${user.id}')">
                                Просмотр
                            </button>
                            ${!user.isAdmin ? `
                            <button class="user-action-btn delete" onclick="deleteUser('${user.id}', '${user.username}')">
                                Удалить
                            </button>
                            ` : ''}
                        </div>
                    </div>
                `;
            });
            
            usersList.innerHTML = html;
        }

        function updateAdminQuestionsList() {
            const pendingQuestionsDiv = document.getElementById('pending-questions');
            const allQuestions = JSON.parse(localStorage.getItem('allQuestions') || '[]');
            const pendingQuestions = allQuestions.filter(q => !q.answered);
            
            if (pendingQuestions.length === 0) {
                pendingQuestionsDiv.innerHTML = '<p style="color: #666; font-style: italic;">Нет неотвеченных вопросов</p>';
                return;
            }
            
            let html = '';
            pendingQuestions.forEach(question => {
                const date = new Date(question.date).toLocaleDateString('ru-RU', {
                    day: '2-digit',
                    month: '2-digit',
                    year: 'numeric',
                    hour: '2-digit',
                    minute: '2-digit'
                });
                
                html += `
                    <div class="question-item">
                        <div class="question-header">
                            <div>
                                <div class="question-user">${question.name} (${question.username})</div>
                                <div class="question-date">${date}</div>
                            </div>
                            <div class="question-status pending">Ожидает ответа</div>
                        </div>
                        <div class="question-text">${question.text}</div>
                        <div class="admin-answer-form">
                            <textarea id="answer-${question.id}" class="reflection-textarea" 
                                      placeholder="Введите ответ на вопрос..."
                                      style="min-height: 80px; font-size: 14px;"></textarea>
                            <button class="user-action-btn" style="margin-top: 10px;" 
                                    onclick="answerQuestion('${question.id}')">
                                Ответить
                            </button>
                        </div>
                    </div>
                `;
            });
            
            pendingQuestionsDiv.innerHTML = html;
        }

        function updateUserSelect(users) {
            const select = document.getElementById('user-select');
            select.innerHTML = '<option value="">-- Выберите пользователя --</option>';
            
            users.forEach(user => {
                if (!user.isAdmin) { // Не показываем админов в списке
                    const option = document.createElement('option');
                    option.value = user.id;
                    option.textContent = `${user.name} (${user.username})`;
                    select.appendChild(option);
                }
            });
        }

        window.viewUserData = function(userId) {
            const userDataItem = allUsersData[userId];
            if (!userDataItem) {
                document.getElementById('selected-user-data').innerHTML = 
                    '<p style="color: #666; font-style: italic;">Нет данных для этого пользователя</p>';
                return;
            }
            
            const data = userDataItem.data || {};
            const workouts = data.workouts || [];
            const reflections = data.reflections || [];
            const questions = data.questions || [];
            
            let html = `
                <h5 style="color: #667eea; margin-bottom: 15px;">${userDataItem.name} (${userDataItem.username})</h5>
                
                <div style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; margin-bottom: 20px;">
                    <div style="background: #f8f9fa; padding: 10px; border-radius: 8px; text-align: center;">
                        <div style="font-size: 18px; font-weight: bold; color: #667eea;">${workouts.length}</div>
                        <div style="font-size: 12px; color: #666;">Тренировок</div>
                    </div>
                    <div style="background: #f8f9fa; padding: 10px; border-radius: 8px; text-align: center;">
                        <div style="font-size: 18px; font-weight: bold; color: #28a745;">${reflections.length}</div>
                        <div style="font-size: 12px; color: #666;">Рефлексий</div>
                    </div>
                    <div style="background: #f8f9fa; padding: 10px; border-radius: 8px; text-align: center;">
                        <div style="font-size: 18px; font-weight: bold; color: #17a2b8;">${questions.length}</div>
                        <div style="font-size: 12px; color: #666;">Вопросов</div>
                    </div>
                </div>
            `;
            
            if (workouts.length > 0) {
                html += `
                    <div style="margin-top: 15px;">
                        <h6 style="color: #667eea; margin-bottom: 8px;">Последние тренировки:</h6>
                        <div style="max-height: 150px; overflow-y: auto;">
                `;
                
                workouts.slice(0, 3).forEach(workout => {
                    const date = new Date(workout.date).toLocaleDateString('ru-RU', {
                        day: '2-digit',
                        month: '2-digit',
                        year: 'numeric'
                    });
                    
                    html += `
                        <div style="font-size: 12px; padding: 5px; border-bottom: 1px solid #e0e0e0;">
                            ${date}: ${workout.goal || 'Тренировка'} (${workout.programType || 'общая'})
                        </div>
                    `;
                });
                
                html += `</div></div>`;
            }
            
            document.getElementById('selected-user-data').innerHTML = html;
        };

        window.deleteUser = function(userId, username) {
            if (!confirm(`Вы уверены, что хотите удалить пользователя ${username}? Все данные пользователя будут удалены.`)) {
                return;
            }
            
            // Удаляем пользователя из динамической базы
            DYNAMIC_USER_DATABASE = DYNAMIC_USER_DATABASE.filter(u => u.id !== userId);
            saveDynamicUserDatabase();
            
            // Удаляем пользователя из старой системы (для совместимости)
            const users = JSON.parse(localStorage.getItem('users') || '[]');
            const updatedUsers = users.filter(u => u.id !== userId);
            localStorage.setItem('users', JSON.stringify(updatedUsers));
            
            // Удаляем данные пользователя
            delete allUsersData[userId];
            localStorage.setItem('allUsersData', JSON.stringify(allUsersData));
            localStorage.removeItem(`userData_${userId}`);
            
            // Отмечаем обновление данных
            markDataAsUpdated();
            
            showNotification(`Пользователь ${username} удален`, 'success');
            updateAdminPanel();
        };

        window.answerQuestion = function(questionId) {
            const answerText = document.getElementById(`answer-${questionId}`).value.trim();
            
            if (!answerText) {
                alert('Введите ответ на вопрос');
                return;
            }
            
            // Находим вопрос в общих вопросах
            const allQuestions = JSON.parse(localStorage.getItem('allQuestions') || '[]');
            const questionIndex = allQuestions.findIndex(q => q.id == questionId);
            
            if (questionIndex === -1) {
                alert('Вопрос не найден');
                return;
            }
            
            // Обновляем вопрос
            allQuestions[questionIndex].answered = true;
            allQuestions[questionIndex].answer = answerText;
            allQuestions[questionIndex].answerDate = new Date().toISOString();
            localStorage.setItem('allQuestions', JSON.stringify(allQuestions));
            
            // Обновляем вопрос в данных пользователя
            const userId = allQuestions[questionIndex].userId;
            const userDataKey = `userData_${userId}`;
            const userDataStr = localStorage.getItem(userDataKey);
            
            if (userDataStr) {
                const userData = JSON.parse(userDataStr);
                const userQuestionIndex = userData.questions?.findIndex(q => q.id == questionId);
                
                if (userQuestionIndex !== -1 && userQuestionIndex !== undefined) {
                    userData.questions[userQuestionIndex].answered = true;
                    userData.questions[userQuestionIndex].answer = answerText;
                    userData.questions[userQuestionIndex].answerDate = new Date().toISOString();
                    localStorage.setItem(userDataKey, JSON.stringify(userData));
                }
            }
            
            // Отмечаем обновление данных
            markDataAsUpdated();
            
            showNotification('Ответ отправлен пользователю', 'success');
            updateAdminPanel();
        };

        // ==================== УПРАВЛЕНИЕ ПОЛЬЗОВАТЕЛЯМИ (АДМИН) ====================
        function showCreateUserModal() {
            document.getElementById('create-user-modal').classList.add('active');
            clearCreateUserErrors();
        }

        function hideCreateUserModal() {
            document.getElementById('create-user-modal').classList.remove('active');
            clearCreateUserErrors();
        }

        function clearCreateUserErrors() {
            document.querySelectorAll('#create-user-form .auth-error').forEach(el => {
                el.textContent = '';
                el.style.display = 'none';
            });
        }

        function showCreateUserError(elementId, message) {
            const element = document.getElementById(elementId);
            element.textContent = message;
            element.style.display = 'block';
        }

        function createUser(username, password, name) {
            // Проверяем, существует ли пользователь в предустановленных аккаунтах
            const existingPreset = PRESET_ACCOUNTS.find(acc => acc.username === username);
            if (existingPreset) {
                return { success: false, message: 'Пользователь с таким логином уже существует (системный аккаунт)' };
            }
            
            // Проверяем, существует ли пользователь в динамической базе
            const existingUser = DYNAMIC_USER_DATABASE.find(u => u.username === username);
            if (existingUser) {
                return { success: false, message: 'Пользователь с таким логином уже существует' };
            }
            
            // Проверяем, существует ли пользователь в старой системе (для совместимости)
            const oldUsers = JSON.parse(localStorage.getItem('users') || '[]');
            const existingOldUser = oldUsers.find(u => u.username === username);
            if (existingOldUser) {
                return { success: false, message: 'Пользователь с таким логином уже существует в старой системе' };
            }
            
            const newUser = {
                id: 'user_' + Date.now() + '_' + Math.random().toString(36).substr(2, 9),
                username: username,
                password: password,
                name: name,
                isAdmin: false,
                createdBy: currentUser.username,
                creationDate: new Date().toISOString()
            };
            
            // Добавляем в динамическую базу
            DYNAMIC_USER_DATABASE.push(newUser);
            saveDynamicUserDatabase();
            
            // Также добавляем в старую систему (для совместимости)
            oldUsers.push(newUser);
            localStorage.setItem('users', JSON.stringify(oldUsers));
            
            // Инициализируем пустые данные для нового пользователя
            const initialUserData = {
                workouts: [],
                reflections: [],
                questions: []
            };
            
            localStorage.setItem(`userData_${newUser.id}`, JSON.stringify(initialUserData));
            
            // Добавляем в общие данные
            allUsersData[newUser.id] = {
                ...newUser,
                data: initialUserData
            };
            localStorage.setItem('allUsersData', JSON.stringify(allUsersData));
            
            // Отмечаем, что данные были обновлены
            markDataAsUpdated();
            
            // Создаем резервную копию базы пользователей для встраивания в код
            createUserDatabaseBackup();
            
            return { success: true, user: newUser };
        }

        function createUserDatabaseBackup() {
            // Создаем копию базы пользователей в формате для встраивания в код
            const backup = {
                timestamp: new Date().toISOString(),
                users: DYNAMIC_USER_DATABASE,
                presetAccounts: PRESET_ACCOUNTS,
                totalUsers: DYNAMIC_USER_DATABASE.length + PRESET_ACCOUNTS.length
            };
            
            localStorage.setItem('embeddedUserDatabase', JSON.stringify(backup));
            
            // Также сохраняем в формате JavaScript для вставки в код
            const jsCode = `// Динамическая база пользователей (автоматически обновляется)
       const DYNAMIC_USER_DATABASE = ${JSON.stringify(DYNAMIC_USER_DATABASE, null, 2)};

        // Объединенная база пользователей для аутентификации
         function getAllUsersForAuth() {
    return [...PRESET_ACCOUNTS, ...DYNAMIC_USER_DATABASE];
     }`;
            
            localStorage.setItem('userDatabaseCode', jsCode);
        }

        // ==================== ОТОБРАЖЕНИЕ ИСТОРИИ ====================
        function updateHistoryDisplay(filter = 'all') {
            const historyList = document.getElementById('history-list');
            
            let allItems = [
                ...userData.workouts.map(w => ({...w, type: 'workout'})),
                ...userData.reflections.map(r => ({...r, type: 'reflection'}))
            ].sort((a, b) => new Date(b.date) - new Date(a.date));
            
            if (filter !== 'all') {
                allItems = allItems.filter(item => item.type === filter);
            }
            
            if (allItems.length === 0) {
                historyList.innerHTML = `
                    <div style="text-align: center; padding: 20px; color: #666;">
                        <p>Нет сохраненных записей</p>
                    </div>
                `;
                return;
            }
            
            let html = '';
            allItems.forEach(item => {
                const date = new Date(item.date).toLocaleDateString('ru-RU', {
                    day: '2-digit',
                    month: '2-digit',
                    year: 'numeric'
                });
                
                if (item.type === 'workout') {
                    const programType = item.programType || 'general';
                    const typeIcon = programType === 'streetlifting' ? '🏋️‍♂️' : 
                                   programType.includes('womens') ? '👩' : '💪';
                    const hasExercises = item.exercises && item.exercises.length > 0;
                    
                    html += `
                        <div class="history-item" onclick="showWorkoutDetails(${item.id})">
                            <div class="history-date">${date}</div>
                            <div><strong>${typeIcon} ${getProgramTypeName(programType)}</strong></div>
                            <div>${item.goal || 'Тренировка'}</div>
                            <span class="history-program-type">${getGoalName(item.goal)}</span>
                            ${hasExercises ? `
                            <button class="show-exercises-btn" onclick="event.stopPropagation(); showExercises(${item.id})">
                                👁️ Упражнения
                            </button>` : ''}
                        </div>
                    `;
                } else {
                    html += `
                        <div class="history-item" onclick="showReflectionDetails(${item.id})">
                            <div class="history-date">${date}</div>
                            <div><strong>💭 Рефлексия</strong></div>
                            <div>${getMoodEmoji(item.mood)} ${getMoodText(item.mood)}</div>
                        </div>
                    `;
                }
            });
            
            historyList.innerHTML = html;
        }

        function getProgramTypeName(type) {
            const names = {
                streetlifting: 'Стритлифтинг',
                womens_fatloss: 'Женская (похудение)',
                womens_bodybuilding: 'Женская (масса)',
                strength: 'Силовая',
                hypertrophy: 'На массу',
                endurance: 'На выносливость',
                fatloss: 'На похудение',
                general: 'Общая'
            };
            
            return names[type] || 'Тренировка';
        }

        window.showExercises = function(workoutId) {
            const workout = userData.workouts.find(w => w.id === workoutId);
            if (!workout) return;
            
            const detailsDiv = document.getElementById('history-details');
            const emptyDiv = document.getElementById('history-empty');
            
            emptyDiv.classList.add('hidden');
            detailsDiv.classList.remove('hidden');
            
            const date = new Date(workout.date).toLocaleDateString('ru-RU', {
                day: '2-digit',
                month: '2-digit',
                year: 'numeric'
            });
            
            let html = `
                <h3 style="color: #667eea; margin-bottom: 20px;">
                    ${getProgramTypeIcon(workout.programType)} Упражнения из тренировки от ${date}
                </h3>
                
                <div style="display: flex; gap: 15px; margin-bottom: 20px; flex-wrap: wrap;">
                    <div style="background: #f8f9fa; padding: 12px; border-radius: 8px; font-size: 14px;">
                        <strong>Программа:</strong> ${getProgramTypeName(workout.programType)}
                    </div>
                    <div style="background: #f8f9fa; padding: 12px; border-radius: 8px; font-size: 14px;">
                        <strong>Цель:</strong> ${getGoalName(workout.goal)}
                    </div>
                    <div style="background: #f8f9fa; padding: 12px; border-radius: 8px; font-size: 14px;">
                        <strong>Уровень:</strong> ${getLevelName(workout.level)}
                    </div>
                </div>
                
                <div style="margin-top: 10px;">
                    <button onclick="showWorkoutDetails(${workout.id})" 
                            style="background: #667eea; color: white; border: none; padding: 10px 20px; border-radius: 20px; cursor: pointer;">
                        ← Назад к деталям
                    </button>
                </div>
            `;
            
            const exercises = workout.exercises || workout.program?.exercises || [];
            
            if (exercises.length > 0) {
                html += `
                    <div class="exercises-container">
                        <h4 style="margin: 25px 0 15px; color: #28a745;">🏋️‍♂️ Выполненные упражнения (${exercises.length})</h4>
                        <div class="exercises-list">
                `;
                
                exercises.forEach((exercise, index) => {
                    html += `
                        <div class="exercise-card">
                            <h5>${index + 1}. ${exercise.name}</h5>
                            <p style="font-size: 14px; color: #666; margin-bottom: 10px;">${exercise.description}</p>
                            <div class="exercise-stats">
                                ${exercise.intensity ? `
                                <div class="stat-item">
                                    <span class="stat-icon">⚡</span>
                                    <span>${exercise.intensity}</span>
                                </div>` : ''}
                                ${exercise.muscles ? `
                                <div class="stat-item">
                                    <span class="stat-icon">💪</span>
                                    <span>${Array.isArray(exercise.muscles) ? exercise.muscles.join(', ') : exercise.muscles}</span>
                                </div>` : ''}
                                ${exercise.type ? `
                                <div class="stat-item">
                                    <span class="stat-icon">📊</span>
                                    <span>${exercise.type}</span>
                                </div>` : ''}
                            </div>
                        </div>
                    `;
                });
                
                html += `
                        </div>
                    </div>
                    
                    <div style="margin-top: 20px; padding: 15px; background: #e6eeff; border-radius: 10px;">
                        <h5>📊 Статистика по упражнениям:</h5>
                        <p>• Всего упражнений: <strong>${exercises.length}</strong></p>
                        <p>• Группы мышц: <strong>${getUniqueMuscles(exercises).join(', ')}</strong></p>
                        <p>• Типы упражнения: <strong>${getExerciseTypes(exercises).join(', ')}</strong></p>
                    </div>
                `;
            } else {
                html += `
                    <div style="text-align: center; padding: 40px; color: #666;">
                        <h4>🤔 Упражнения не сохранены</h4>
                        <p>Для этой тренировки не сохранились детальные данные упражнений.</p>
                    </div>
                `;
            }
            
            detailsDiv.innerHTML = html;
        };

        function getUniqueMuscles(exercises) {
            const muscles = new Set();
            exercises.forEach(exercise => {
                if (exercise.muscles) {
                    if (Array.isArray(exercise.muscles)) {
                        exercise.muscles.forEach(m => muscles.add(m));
                    } else {
                        muscles.add(exercise.muscles);
                    }
                }
            });
            return Array.from(muscles);
        }

        function getExerciseTypes(exercises) {
            const types = new Set();
            exercises.forEach(exercise => {
                if (exercise.type) {
                    types.add(exercise.type);
                }
            });
            return Array.from(types);
        }

        window.showWorkoutDetails = function(workoutId) {
            const workout = userData.workouts.find(w => w.id === workoutId);
            if (!workout) return;
            
            const detailsDiv = document.getElementById('history-details');
            const emptyDiv = document.getElementById('history-empty');
            
            emptyDiv.classList.add('hidden');
            detailsDiv.classList.remove('hidden');
            
            const date = new Date(workout.date).toLocaleDateString('ru-RU', {
                day: '2-digit',
                month: '2-digit',
                year: 'numeric',
                hour: '2-digit',
                minute: '2-digit'
            });
            
            const hasExercises = workout.exercises && workout.exercises.length > 0;
            
            let html = `
                <h3 style="color: #667eea; margin-bottom: 15px;">
                    ${getProgramTypeIcon(workout.programType)} ${getProgramTypeName(workout.programType)} от ${date}
                </h3>
                
                ${hasExercises ? `
                <div style="margin-bottom: 15px;">
                    <button onclick="showExercises(${workout.id})" 
                            style="background: #28a745; color: white; border: none; padding: 10px 20px; border-radius: 20px; cursor: pointer; font-weight: bold;">
                        👁️ Показать упражнения (${workout.exercises.length})
                    </button>
                </div>` : ''}
                
                <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(180px, 1fr)); gap: 12px; margin-bottom: 20px;">
                    <div style="background: #f8f9fa; padding: 12px; border-radius: 8px; font-size: 14px;">
                        <strong>Пол:</strong> ${workout.gender === 'male' ? 'Мужской' : 'Женский'}
                    </div>
                    <div style="background: #f8f9fa; padding: 12px; border-radius: 8px; font-size: 14px;">
                        <strong>Вес:</strong> ${workout.weight} кг
                    </div>
                    <div style="background: #f8f9fa; padding: 12px; border-radius: 8px; font-size: 14px;">
                        <strong>Цель:</strong> ${getGoalName(workout.goal)}
                    </div>
                    <div style="background: #f8f9fa; padding: 12px; border-radius: 8px; font-size: 14px;">
                        <strong>Уровень:</strong> ${getLevelName(workout.level)}
                    </div>
                </div>
            `;
            
            if (workout.program && workout.program.description) {
                html += `<p style="margin-bottom: 15px;">${workout.program.description}</p>`;
            }
            
            if (workout.programType === 'streetlifting' && workout.program && workout.program.data && workout.program.data.userData) {
                html += `
                    <div style="background: #e6eeff; padding: 15px; border-radius: 10px; margin-top: 15px;">
                        <h5 style="color: #667eea; margin-bottom: 10px;">📊 Параметры стритлифтинга:</h5>
                        <p>• Брусья 5ПМ: <strong>${workout.program.data.userData.bars5RM} кг</strong></p>
                        <p>• Турник 5ПМ: <strong>${workout.program.data.userData.pullups5RM} кг</strong></p>
                        <p>• Трицепс 10-12ПМ: <strong>${workout.program.data.userData.tricepsRM} кг</strong></p>
                        <p>• Бицепс 10-12ПМ: <strong>${workout.program.data.userData.bicepsRM} кг</strong></p>
                    </div>
                `;
            }
            
            detailsDiv.innerHTML = html;
        };

        function getProgramTypeIcon(type) {
            const icons = {
                streetlifting: '🏋️‍♂️',
                womens_fatloss: '👩',
                womens_bodybuilding: '👩',
                strength: '💪',
                hypertrophy: '🏋️',
                endurance: '🏃',
                fatloss: '🔥'
            };
            
            return icons[type] || '💪';
        }

        function getLevelName(level) {
            const names = {
                beginner: 'Начинающий',
                intermediate: 'Средний',
                advanced: 'Продвинутый'
            };
            
            return names[level] || level;
        }

        window.showReflectionDetails = function(reflectionId) {
            const reflection = userData.reflections.find(r => r.id === reflectionId);
            if (!reflection) return;
            
            const detailsDiv = document.getElementById('history-details');
            const emptyDiv = document.getElementById('history-empty');
            
            emptyDiv.classList.add('hidden');
            detailsDiv.classList.remove('hidden');
            
            const date = new Date(reflection.date).toLocaleDateString('ru-RU', {
                day: '2-digit',
                month: '2-digit',
                year: 'numeric',
                hour: '2-digit',
                minute: '2-digit'
            });
            
            let html = `
                <h3 style="color: #28a745; margin-bottom: 15px;">
                    💭 Рефлексия от ${date}
                </h3>
                
                <div style="background: #f8f9fa; padding: 15px; border-radius: 10px; margin-bottom: 15px;">
                    <div style="display: flex; align-items: center; gap: 10px; margin-bottom: 10px;">
                        <span style="font-size: 20px;">${getMoodEmoji(reflection.mood)}</span>
                        <span><strong>Настроение:</strong> ${getMoodText(reflection.mood)}</span>
                    </div>
                </div>
            `;
            
            if (reflection.success) {
                html += `
                    <div style="background: #fff8e6; padding: 15px; border-radius: 10px; margin-bottom: 10px;">
                        <h4 style="color: #ff9800; margin-bottom: 8px; font-size: 16px;">✅ Что получилось хорошо:</h4>
                        <p style="white-space: pre-line; font-size: 14px;">${reflection.success}</p>
                    </div>
                `;
            }
            
            if (reflection.improve) {
                html += `
                    <div style="background: #e6f7ff; padding: 15px; border-radius: 10px;">
                        <h4 style="color: #2196f3; margin-bottom: 8px; font-size: 16px;">📈 Что можно улучшить:</h4>
                        <p style="white-space: pre-line; font-size: 14px;">${reflection.improve}</p>
                    </div>
                `;
            }
            
            detailsDiv.innerHTML = html;
        };

        // ==================== ОТОБРАЖЕНИЕ РЕФЛЕКСИЙ ====================
        function updateReflectionList() {
            const listDiv = document.getElementById('reflection-list');
            const reflections = userData.reflections.sort((a, b) => new Date(b.date) - new Date(a.date));
            
            if (reflections.length === 0) {
                listDiv.innerHTML = `
                    <div style="text-align: center; padding: 20px; color: #666;">
                        <p>Пока нет сохраненных рефлексий</p>
                    </div>
                `;
                return;
            }
            
            let html = '';
            reflections.slice(0, 5).forEach(reflection => {
                const date = new Date(reflection.date).toLocaleDateString('ru-RU', {
                    day: '2-digit',
                    month: '2-digit',
                    year: 'numeric'
                });
                
                const preview = reflection.success ? 
                    reflection.success.substring(0, 80) + (reflection.success.length > 80 ? '...' : '') : 
                    'Без текста';
                
                html += `
                    <div class="reflection-item" onclick="showReflectionDetails(${reflection.id})">
                        <div class="reflection-date">${date} ${getMoodEmoji(reflection.mood)}</div>
                        <div style="font-size: 14px;">${preview}</div>
                    </div>
                `;
            });
            
            listDiv.innerHTML = html;
        }

        // ==================== УТИЛИТЫ ====================
        function getMoodEmoji(mood) {
            const emojis = {
                excellent: '😊',
                good: '🙂',
                neutral: '😐',
                tired: '😴',
                frustrated: '😔'
            };
            return emojis[mood] || '😐';
        }

        function getMoodText(mood) {
            const texts = {
                excellent: 'Отлично',
                good: 'Хорошо',
                neutral: 'Нормально',
                tired: 'Устал',
                frustrated: 'Расстроен'
            };
            return texts[mood] || 'Не указано';
        }

        function showNotification(message, type = 'info') {
            const notification = document.createElement('div');
            notification.style.cssText = `
                position: fixed;
                top: 20px;
                right: 20px;
                padding: 12px 20px;
                background: ${type === 'success' ? '#28a745' : type === 'error' ? '#dc3545' : '#667eea'};
                color: white;
                border-radius: 10px;
                box-shadow: 0 5px 15px rgba(0,0,0,0.2);
                z-index: 1000;
                animation: slideIn 0.3s ease;
                max-width: 300px;
                font-size: 14px;
            `;
            
            notification.textContent = message;
            document.body.appendChild(notification);
            
            setTimeout(() => {
                notification.style.animation = 'slideOut 0.3s ease';
                setTimeout(() => notification.remove(), 300);
            }, 3000);
            
            if (!document.querySelector('#notification-styles')) {
                const style = document.createElement('style');
                style.id = 'notification-styles';
                style.textContent = `
                    @keyframes slideIn {
                        from { transform: translateX(100%); opacity: 0; }
                        to { transform: translateX(0); opacity: 1; }
                    }
                    @keyframes slideOut {
                        from { transform: translateX(0); opacity: 1; }
                        to { transform: translateX(100%); opacity: 0; }
                    }
                `;
                document.head.appendChild(style);
            }
        }

        // ==================== ОБРАБОТЧИКИ СОБЫТИЙ ====================
        function initEventListeners() {
            // Вход/выход
            document.getElementById('auth-btn').addEventListener('click', showAuthModal);
            document.getElementById('logout-btn').addEventListener('click', logout);
            
            // Закрытие модального окна при клике вне его
            document.getElementById('auth-modal').addEventListener('click', function(e) {
                if (e.target === this) {
                    hideAuthModal();
                }
            });
            
            // Кнопка входа
            document.getElementById('login-submit-btn').addEventListener('click', function() {
                const username = document.getElementById('login-username').value.trim();
                const password = document.getElementById('login-password').value.trim();
                
                clearAuthErrors();
                
                if (!username) {
                    showAuthError('login-username-error', 'Введите логин');
                    return;
                }
                
                if (!password) {
                    showAuthError('login-password-error', 'Введите пароль');
                    return;
                }
                
                const result = loginUser(username, password);
                
                if (result.success) {
                    currentUser = result.user;
                    updateUIAfterLogin();
                    syncUserData();
                } else {
                    showAuthError('login-general-error', result.message);
                }
            });
            
            // Быстрый вход для тестирования
            document.getElementById('login-username').addEventListener('keypress', function(e) {
                if (e.key === 'Enter') {
                    document.getElementById('login-submit-btn').click();
                }
            });
            
            document.getElementById('login-password').addEventListener('keypress', function(e) {
                if (e.key === 'Enter') {
                    document.getElementById('login-submit-btn').click();
                }
            });
            
            // Фильтры истории
            document.querySelectorAll('.filter-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
                    this.classList.add('active');
                    const filter = this.getAttribute('data-filter');
                    updateHistoryDisplay(filter);
                });
            });
            
            // Сохранение рефлексии
            document.getElementById('save-reflection-btn').addEventListener('click', function() {
                const success = document.getElementById('reflection-success').value.trim();
                const improve = document.getElementById('reflection-improve').value.trim();
                const moodOption = document.querySelector('.mood-option.selected');
                
                if (!moodOption) {
                    showNotification('Выберите настроение', 'error');
                    return;
                }
                
                const mood = moodOption.getAttribute('data-mood');
                
                saveReflection({
                    success,
                    improve,
                    mood
                });
            });
            
            // Выбор настроения
            document.querySelectorAll('.mood-option').forEach(option => {
                option.addEventListener('click', function() {
                    document.querySelectorAll('.mood-option').forEach(opt => opt.classList.remove('selected'));
                    this.classList.add('selected');
                });
            });
            
            // Кнопка инструктажа
            document.getElementById('instruction-btn').addEventListener('click', function() {
                const instruction = `
     📋 ИНСТРУКЦИЯ ПО ВЫПОЛНЕНИЮ ТРЕНИРОВКИ:

    1. РАЗМИНКА (10-15 минут):
    • 5 мин легкого кардио
    • Динамическая растяжка суставов
    • Подготовительные подходы
 
    2. ОСНОВНАЯ ЧАСТЬ:
    • Соблюдайте технику
    • Отдых 1-3 минуты между подходами
    • Контролируйте дыхание

    3. ЗАМИНКА (5-10 минут):
    • Статическая растяжка
    • Восстановительное дыхание

    ⚠️ ПРИ ОЩУЩЕНИИ БОЛИ ПРЕКРАТИТЕ УПРАЖНЕНИЕ!
                `;
                alert(instruction);
            });
            
            // Завершение тренировки
            document.getElementById('complete-workout-btn').addEventListener('click', function() {
                if (currentWorkout) {
                    currentWorkout.completed = true;
                    currentWorkout.completionDate = new Date().toISOString();
                    saveWorkout(currentWorkout);
                    
                    showPage('home');
                    document.querySelectorAll('.nav-btn').forEach(btn => btn.classList.remove('active'));
                    document.querySelector('[data-page="home"]').classList.add('active');
                } else {
                    showNotification('Сначала создайте тренировку', 'error');
                }
            });
            
            // Клик по вариантам в анкете
            document.querySelectorAll('.option-label').forEach(label => {
                label.addEventListener('click', function() {
                    const input = this.querySelector('input');
                    
                    if (input.type === 'checkbox') {
                        this.classList.toggle('selected');
                    } else if (input.type === 'radio') {
                        document.querySelectorAll(`input[name="${input.name}"]`).forEach(inp => {
                            inp.parentElement.classList.remove('selected');
                        });
                        this.classList.add('selected');
                    }
                });
            });
            
            // Отправка вопроса
            document.getElementById('submit-question-btn').addEventListener('click', function() {
                if (!currentUser) {
                    showNotification('Для отправки вопроса необходимо войти в систему', 'error');
                    return;
                }
                
                const questionText = document.getElementById('question-text').value.trim();
                
                if (!questionText) {
                    showAuthError('question-text-error', 'Введите текст вопроса');
                    return;
                }
                
                if (questionText.length < 10) {
                    showAuthError('question-text-error', 'Вопрос должен содержать не менее 10 символов');
                    return;
                }
                
                saveQuestion(questionText);
            });
            
            // Админ: создание пользователя
            document.getElementById('create-user-btn').addEventListener('click', function() {
                if (!currentUser || !currentUser.isAdmin) {
                    showNotification('Доступно только администратору', 'error');
                    return;
                }
                
                showCreateUserModal();
            });
            
            // Админ: создание пользователя (кнопка)
            document.getElementById('create-user-submit-btn').addEventListener('click', function() {
                const username = document.getElementById('new-username').value.trim();
                const password = document.getElementById('new-password').value.trim();
                const name = document.getElementById('new-name').value.trim();
                
                clearCreateUserErrors();
                
                if (!username) {
                    showCreateUserError('new-username-error', 'Введите логин');
                    return;
                }
                
                if (username.length < 3) {
                    showCreateUserError('new-username-error', 'Логин должен быть не менее 3 символов');
                    return;
                }
                
                if (!password) {
                    showCreateUserError('new-password-error', 'Введите пароль');
                    return;
                }
                
                if (password.length < 5) {
                    showCreateUserError('new-password-error', 'Пароль должен быть не менее 5 символов');
                    return;
                }
                
                if (!name) {
                    showCreateUserError('new-name-error', 'Введите имя пользователя');
                    return;
                }
                
                const result = createUser(username, password, name);
                
                if (result.success) {
                    hideCreateUserModal();
                    showNotification('Пользователь успешно создан', 'success');
                    updateAdminPanel();
                    
                    // Очищаем форму
                    document.getElementById('new-username').value = '';
                    document.getElementById('new-password').value = '';
                    document.getElementById('new-name').value = '';
                } else {
                    showCreateUserError('new-user-general-error', result.message);
                }
            });
            
            // Админ: отмена создания пользователя
            document.getElementById('cancel-create-user-btn').addEventListener('click', function() {
                hideCreateUserModal();
            });
            
            // Админ: очистка всех данных
            document.getElementById('clear-all-data-btn').addEventListener('click', function() {
                if (!currentUser || !currentUser.isAdmin) return;
                
                if (!confirm('ВНИМАНИЕ: Это действие удалит ВСЕ данные приложения, включая всех пользователей, тренировки, рефлексии и вопросы. Вы уверены?')) {
                    return;
                }
                
                // Очищаем все данные
                localStorage.clear();
                
                // Сбрасываем глобальные переменные
                currentUser = null;
                userData = { workouts: [], reflections: [], questions: [] };
                allUsersData = {};
                DYNAMIC_USER_DATABASE = [];
                
                // Перезагружаем страницу
                location.reload();
            });
            
            // Админ: экспорт данных
            document.getElementById('export-data-btn').addEventListener('click', function() {
                if (!currentUser || !currentUser.isAdmin) return;
                
                // Собираем все данные
                const exportData = {
                    timestamp: new Date().toISOString(),
                    exportedBy: currentUser.username,
                    presetAccounts: PRESET_ACCOUNTS,
                    dynamicUsers: DYNAMIC_USER_DATABASE,
                    allUsersData: allUsersData,
                    allQuestions: JSON.parse(localStorage.getItem('allQuestions') || '[]'),
                    userDatabaseCode: localStorage.getItem('userDatabaseCode')
                };
                
                // Создаем файл для скачивания
                const dataStr = JSON.stringify(exportData, null, 2);
                const dataUri = 'data:application/json;charset=utf-8,'+ encodeURIComponent(dataStr);
                
                const exportFileDefaultName = `fitness-app-backup-${new Date().toISOString().split('T')[0]}.json`;
                
                const linkElement = document.createElement('a');
                linkElement.setAttribute('href', dataUri);
                linkElement.setAttribute('download', exportFileDefaultName);
                linkElement.click();
                
                showNotification('Данные успешно экспортированы', 'success');
            });
            
            // Админ: выбор пользователя для просмотра
            document.getElementById('user-select').addEventListener('change', function() {
                const userId = this.value;
                if (userId) {
                    window.viewUserData(userId);
                } else {
                    document.getElementById('selected-user-data').innerHTML = 
                        '<p style="color: #666; font-style: italic;">Выберите пользователя для просмотра данных</p>';
                }
            });
            
            // Закрытие модального окна создания пользователя при клике вне его
            document.getElementById('create-user-modal').addEventListener('click', function(e) {
                if (e.target === this) {
                    hideCreateUserModal();
                }
            });
        }

        // Глобальные функции для вызова из HTML
        window.showHistoryList = function() {
            document.getElementById('history-empty').classList.remove('hidden');
            document.getElementById('history-details').classList.add('hidden');
        };
    </script>
     </body>
     </html>
