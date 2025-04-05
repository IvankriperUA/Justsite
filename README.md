
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
            color: var(--tg-theme-text-color, #000);
            background: var(--tg-theme-bg-color, #fff);
        }

        #main {
            width: 100%;
            padding: 20px;
            text-align: center;
        }

        #form {
            display: none;
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

        input {
            margin: 10px auto;
            padding: 10px;
            width: 80%;
            border-radius: 5px;
            border: 1px solid #ccc;
        }

        button {
            border: 0;
            border-radius: 5px;
            margin-top: 20px;
            height: 60px;
            width: 200px;
            font-size: 20px;
            font-weight: 500;
            cursor: pointer;
            transition: all 500ms ease;
            color: var(--tg-theme-text-color, #fff);
            background: var(--tg-theme-button-text-color, #0088cc);
        }
    </style>
</head>
<body>
    <div id="main">
        <h1>Онлайн магазин</h1>
        <img src="https://cdn-icons-png.flaticon.com/512/3044/3044876.png">
        <p>Lorem ipsum sit amet, consectetur adipisicing elit. Accusantium ipsum magni, molestias.</p>
        <button id="buy" type="button">Купити</button>
    </div>

    <form id="form">
        <input type="text" placeholder="Ім'я" id="user_name">
        <input type="text" placeholder="Email" id="user_email">
        <input type="text" placeholder="Телефон" id="user_phone">
        <button id="order" type="button">Оформити</button>
    </form>

    <script>
        let tg = window.Telegram.WebApp;
        let buy = document.getElementById("buy");
        let order = document.getElementById("order");

        buy.addEventListener("click", () => {
            document.getElementById("main").style.display = "none";
            document.getElementById("form").style.display = "block";
            document.getElementById("user_name").value =
                (tg.initDataUnsafe.first_name || "") + " " + (tg.initDataUnsafe.last_name || "");
        });

        order.addEventListener("click", () => {
            tg.close();
        });
    </script>
</body>
</html>
