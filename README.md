<!DOCTYPE html>
<html lang="ua">
<head>
    <meta charset="UTF-8">
    <title>Shop</title>
    <script src="https://telegram.org/js/telegram-web-app.js"></script>
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
            color: var(--tg-theme-text-color);
            background: var(--tg-theme-bg-color);
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
            color: var(--tg-theme-text-color);
            background: var(--tg-theme-button-color);
        }

        #form {
            display: none;
            padding: 20px;
            text-align: center;
        }

        #form input {
            display: block;
            margin: 10px auto;
            padding: 10px;
            width: 80%;
            font-size: 16px;
        }

        #error {
            color: red;
            margin-top: 10px;
        }
    </style>
</head>
<body>
    <div id="main">
        <h1>Онлайн магазин</h1>
        <img src="https://cdn-icons-png.flaticon.com/512/3044/3044876.png" alt="icon">
        <p>Lorem ipsum sit amet, consectetur adipisicing elit. Accusantium ipsum magni, molestias.</p>
        <button id="buy">Купити</button>
    </div>

    <div id="form">
        <input type="text" placeholder="Ім'я" id="user_name">
        <input type="text" placeholder="Email" id="user_email">
        <input type="text" placeholder="Телефон" id="user_phone">
        <p id="error"></p>
        <button id="order">Оформити</button>
    </div>

    <script>
        const tg = window.Telegram.WebApp;
        const buy = document.getElementById("buy");
        const order = document.getElementById("order");

        tg.expand();

        buy.addEventListener("click", () => {
            document.getElementById("main").style.display = "none";
            document.getElementById("form").style.display = "block";

            const firstName = tg.initDataUnsafe?.user?.first_name || "";
            const lastName = tg.initDataUnsafe?.user?.last_name || "";

            document.getElementById("user_name").value = firstName + " " + lastName;
        });

        order.addEventListener("click", (e) => {
            e.preventDefault();

            document.getElementById("error").innerText = "";

            const name = document.getElementById("user_name").value.trim();
            const email = document.getElementById("user_email").value.trim();
            const phone = document.getElementById("user_phone").value.trim();

            if (name.length < 5) {
                document.getElementById("error").innerText = "Помилка в полі Ім'я";
                return;
            }

            if (email.length < 5 || !email.includes("@")) {
                document.getElementById("error").innerText = "Помилка в полі Email";
                return;
            }

            if (phone.length < 5) {
                document.getElementById("error").innerText = "Помилка в номері телефону";
                return;
            }

            const data = {
                name: name,
                email: email,
                phone: phone
            };

            tg.sendData(JSON.stringify(data));
            tg.close();
        });
    </script>
</body>
</html>
