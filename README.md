<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Feliz San Valentín, Jaqueline</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #ffe6e6;
            color: #b30000;
            overflow: hidden;
        }

        /* Estilos de la pantalla de bienvenida */
        .pantalla-bienvenida {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(255, 255, 255, 0.9);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            z-index: 10;
        }

        .pregunta {
            font-size: 28px;
            font-weight: bold;
            color: #d10000;
            margin-bottom: 20px;
        }

        .botones {
            display: flex;
            gap: 20px;
        }

        .boton {
            padding: 15px 30px;
            font-size: 20px;
            background-color: #ff4d4d;
            color: white;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            transition: 0.3s;
        }

        .boton:hover {
            background-color: #b30000;
        }

        /* Botón NO que se mueve */
        .boton-no {
            position: absolute;
        }

        /* Contenedor principal (se oculta hasta que acepte) */
        .contenido {
            display: none;
        }

        /* Animaciones de corazones */
        .corazones {
            position: fixed;
            top: 0;
            left: 50%;
            transform: translateX(-50%);
            pointer-events: none;
            width: 100%;
            height: 100%;
        }

        .corazon {
            position: absolute;
            width: 20px;
            height: 20px;
            background: red;
            clip-path: polygon(50% 0%, 100% 40%, 80% 100%, 50% 80%, 20% 100%, 0% 40%);
            opacity: 0.7;
            animation: flotar 5s linear infinite;
        }

        @keyframes flotar {
            0% { transform: translateY(100vh) scale(1); opacity: 1; }
            100% { transform: translateY(-10vh) scale(0.5); opacity: 0; }
        }
    </style>
</head>
<body>

    <!-- Pantalla de Bienvenida -->
    <div class="pantalla-bienvenida">
        <p class="pregunta">¿Quieres ser mi San Valentín? 💖</p>
        <div class="botones">
            <button class="boton" onclick="aceptar()">💘 ¡Sí, claro! 💘</button>
            <button class="boton boton-no" id="botonNo" onmouseover="moverNo()">❌ No ❌</button>
        </div>
    </div>

    <!-- Contenido Principal (se oculta hasta que acepte) -->
    <div class="contenido">
        <h1>Feliz San Valentín, <span class="nombre">Jaqueline</span> ❤️</h1>

        <div class="contenedor">
            <img class="gatito" src="https://media.giphy.com/media/3oriO0OEd9QIDdllqo/giphy.gif" alt="Gatitos abrazándose">
            <div class="frase">"Eres mi razón de sonreír cada día."</div>
            <div class="frase">"Si tuviera que elegir entre amarte y respirar, usaría mi último aliento para decirte cuánto te amo."</div>
        </div>

        <p class="mensaje">💖 ¡Siempre estaré aquí para ti! 💖</p>

        <button class="boton" onclick="enviarMensaje()">💌 Enviar Mensaje de Amor</button>

        <audio autoplay loop>
            <source src="https://www.bensound.com/bensound-music/bensound-romantic.mp3" type="audio/mpeg">
            Tu navegador no soporta el audio.
        </audio>

        <div class="corazones"></div>
    </div>

    <script>
        // Cuando presiona "Sí"
        function aceptar() {
            document.querySelector(".pantalla-bienvenida").style.display = "none";
            document.querySelector(".contenido").style.display = "block";
        }

        // Botón "No" que se mueve cuando intentan tocarlo
        function moverNo() {
            let botonNo = document.getElementById("botonNo");
            let x = Math.random() * (window.innerWidth - 100);
            let y = Math.random() * (window.innerHeight - 50);
            botonNo.style.left = x + "px";
            botonNo.style.top = y + "px";
        }

        // Animación de corazones flotando
        function crearCorazon() {
            const corazon = document.createElement("div");
            corazon.classList.add("corazon");
            corazon.style.left = Math.random() * 100 + "vw";
            corazon.style.animationDuration = Math.random() * 2 + 3 + "s";
            document.querySelector(".corazones").appendChild(corazon);
            setTimeout(() => {
                corazon.remove();
            }, 5000);
        }
        setInterval(crearCorazon, 300);

        function enviarMensaje() {
            alert("💖 ¡Te quiero mucho, Jaqueline! 💖");
        }
    </script>
</body>
</html>
