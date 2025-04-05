
<html lang="ua">
<head>
    <meta charset="UTF-8">
    <title>Shop</title>
    <script src="https://telegram.org/js/telegram-web-app.js?56"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@200;500&display=swap');

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Montserrat', sans-serif;
            font-weight: 200;
            color: var(--tg-theme-text-color, #222);
            background: var(--tg-theme-bg-color, #f9f9f9);
        }

        #main {
            width: 100%;
            padding: 20px;
            text-align: center;
        }

        h1 {
            margin-top: 50px;
            margin-bottom: 10px;
        }

        img {
            width: 70px;
            margin: 30px auto;
        }

        p {
            width: 350px;
            margin: 0 auto;
        }

        button {
            border: 0;
            border-radius: 5px;
            margin-top: 20px;
            height: 50px;
            width: 200px;
            font-size: 18px;
            font-weight: 500;
            cursor: pointer;
            transition: all 300ms ease;
            color: var(--tg-theme-text-color, #fff);
            background: var(--tg-theme-button-text-color, #0088cc);
        }

        input {
            display: block;
            width: 80%;
            margin: 10px auto;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
    </style>
</head>
<body>
    <div id="main">
        <h1>Онлайн магазин</h1>
        <img src="https://cdn-icons-png.flaticon.com/512/3044/3044876.png">
        <p>Lorem ipsum sit amet, consectetur adipisicing elit. Accusantium ipsum magni, molestias.</p>
        <button id="buy" type="button">Купити</button>

        <form id="form">
            <input type="text" placeholder="Ім'я" id="user_name">
            <input type="text" placeholder="Email" id="user_email">
            <input type="text" placeholder="Телефон" id="user_phone">
            <button id="order" type="submit">Оформити</button>
        </form>
    </div>
</body>
</html>
