
<p id="error" style="color: red;"></p>
<script>
    let tg = window.Telegram.WebApp;
    let buy = document.getElementById("buy");
    let order = document.getElementById("order");
    tg.expand();

    buy.addEventListener("click", () => {
        document.getElementById("main").style.display = "none";
        document.getElementById("form").style.display = "block";
        document.getElementById("user_name").value =
            (tg.initDataUnsafe.first_name || "") + " " + (tg.initDataUnsafe.last_name || "");
    });

    order.addEventListener("click", (event) => {
        event.preventDefault();
        document.getElementById("error").innerText = "";
        let name = document.getElementById("user_name").value;
        let email = document.getElementById("user_email").value;
        let phone = document.getElementById("user_phone").value;

        if (name.length < 5) {
            document.getElementById("error").innerText = "Помилка в полі Ім'я";
            return;
        }

        if (email.length < 5) {
            document.getElementById("error").innerText = "Помилка в полі Email";
            return;
        }

        if (phone.length < 5) {
            document.getElementById("error").innerText = "Помилка в номері телефону";
            return;
        }

        let data = {
            name: name,
            email: email,
            phone: phone
        };

        tg.sendData(JSON.stringify(data));
        tg.close();
    });
</script>
