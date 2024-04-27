<!DOCTYPE html>
<html>
<head>
    <title>CARS EL BEBOTE</title>
    <style>
        header {
            background-color: #FFFFFF;
            color: black;
            align-items: center;
            text-align: center;
        }
        header img {
            width: 200px;
            height: auto;
            margin-right: 15px;
        }
        header h1 {
            font-size: 24px;
        }
        #menuBotones {
            display: none;  /* Inicialmente oculto */
        }
        #mostrarMenu {
            margin-bottom: 10px;
            cursor: pointer;
            text-decoration: underline;
        }
        video {
            width: 320px;
            height: 240px;
            display: block;
            margin: 10px auto;
        }
        .sellButton {
            display: block;
            margin-top: 5px;
        }
        .modal {
            display: none; 
            position: fixed; 
            z-index: 1; 
            left: 0;
            top: 0;
            width: 100%; 
            height: 100%; 
            overflow: auto; 
            background-color: rgba(0,0,0,0.4); /* Fondo semitransparente */
            padding-top: 60px;
        }
        .modal-content {
            background-color: #fefefe;
            margin: 5% auto;
            padding: 20px;
            border: 1px solid #888;
            width: 80%;
        }
        .close {
            color: #aaa;
            float: right;
            font-size: 28px;
            font-weight: bold;
        }
        .close:hover,
        .close:focus {
            color: black;
            text-decoration: none;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <header>
        <h1>Título de la página</h1>
        <img src="ruta_a_tu_logotipo.jpg" alt="Logotipo"/>
    </header>
    <div id="mostrarMenu" onclick="toggleMenu()">Mostrar Menú</div>
    <div id="menuBotones">
        <button onclick="showCarInfo('Dodge')">Dodge</button>
        <button onclick="showCarInfo('Chevy')">Chevy</button>
        <button onclick="showCarInfo('Toyota')">Toyota</button>
        <button onclick="showCarInfo('BMW')">BMW</button>
    </div>
    <div id="displayArea"></div>

    <!-- Modal -->
    <div id="myModal" class="modal">
        <!-- Contenido del modal -->
        <div class="modal-content">
            <span class="close" onclick="closeModal()">&times;</span>
            <h2>Información del comprador</h2>
            <p>Ingresa tu información para comprar este producto:</p>
            <!-- Formulario de compra -->
            <form id="buyForm">
                <input type="text" placeholder="Nombre"><br>
                <input type="text" placeholder="Apellido"><br>
                <input type="email" placeholder="Correo electrónico"><br>
                <select>
                    <option value="" disabled selected>Selecciona tu tarjeta de crédito</option>
                    <option value="visa">Visa</option>
                    <option value="mastercard">Mastercard</option>
                    <option value="amex">American Express</option>
                    <option value="discover">Discover</option>
                </select><br>
                <textarea placeholder="Notas adicionales (opcional)"></textarea><br>
                <button type="button" onclick="submitPurchase()">Comprar</button>
            </form>
        </div>
    </div>

    <script>
        const carInfo = {
            Dodge: {
                description: "Charger<p> Modelos disponibles<p> *sxt motor V6 pentastar 305 caballos de fuerza y 264 libras de torque 0-60mph en 6.4 segundos El precio empieza en los 15,990 dolares. <p> *R/T motor 5.7 Hemi 363 caballos de fuerza y 394 libras de torque 0-60mph en 3.3 segundos El precio empieza en los 24000 dolares. <p> *Scatpack motor V8 392 Hemi 485 de fuerza y 475 libras de torque 3 segundos El precio empieza en los 38995 dolares. <p> *Hellcat motor V8 6.2 supercargado 707 caballos de fuerza y 802 libras de torque 0-60mph en 2.7 segundos El precio empieza en los 42900 dolares.",
                videoUrl: "ruta_del_video_dodge.mp4",
            },
            Chevy: {
                description: "Camaro<p> Modelos disponibles<p> *RS motor V6 3.6 335 caballos 285 libras de torque 0-60mph en 6.2 segundos El precio empieza en los 16700 dolares. <p> *SS motor V8 6.2 LT4 455 caballos de fuerza y 617 libras de torque 0-60mph en 5.4 segundos El precio empieza en los 25996 dolares. <p> *ZL1 motor V8 6.2 LT4 supercargado 650 caballos de fuerza y 650 libras de torque.",
                videoUrl: "ruta_del_video_chevy.mp4",
            },
            Toyota: {
                description: "Información del Toyota",
                videoUrl: "ruta_del_video_toyota.mp4",
            },
            BMW: {
                description: "Información del BMW",
                videoUrl: "ruta_del_video_bmw.mp4",
            }
        };

        function showCarInfo(carName) {
            const car = carInfo[carName];
            const displayArea = document.getElementById('displayArea');
            if (car) {
                displayArea.innerHTML = "<p>" + carName + ": " + car.description + "</p>" +
                    '<video autoplay loop muted controlsList="nodownload">' +
                    '<source src="' + car.videoUrl + '" type="video/mp4">' +
                    'Tu navegador no soporta el elemento de video.' +
                    '</video>' +
                    '<button class="sellButton" onclick="openModal()">Comprar</button>';
            } else {
                displayArea.innerHTML = "<p>No se encontró información para " + carName + "</p>";
            }
        }

        function toggleMenu() {
            var menuBotones = document.getElementById('menuBotones');
            var mostrarMenu = document.getElementById('mostrarMenu');
            var displayArea = document.getElementById('displayArea');

            if (menuBotones.style.display === 'none') {
                menuBotones.style.display = 'block';
                mostrarMenu.innerHTML = 'Ocultar Menú';
            } else {
                menuBotones.style.display = 'none';
                mostrarMenu.innerHTML = 'Mostrar Menú';
                displayArea.innerHTML = '';
            }
        }

        function openModal() {
            var modal = document.getElementById('myModal');
            modal.style.display = "block";
            // Limpiar los campos del formulario al abrir el modal
            document.getElementById('buyForm').reset();
        }

        function closeModal() {
            var modal = document.getElementById('myModal');
            modal.style.display = "none";
        }

        function submitPurchase() {
            closeModal();
            alert("¡Gracias por tu compra!");
        }
    </script>
</body>
</html>
