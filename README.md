<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🚨 ADVERTENCIA DEL SISTEMA 🚨</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }
        body {
            background-color: #000;
            color: #ff0000;
            font-family: 'Courier New', Courier, monospace;
            text-align: center;
            padding: 20px;
            overflow: hidden;
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            user-select: none;
        }
        #pantalla-inicio {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            z-index: 10;
        }
        .btn-continuar {
            background-color: #ff0000;
            color: #fff;
            border: none;
            padding: 15px 30px;
            font-size: 1.2rem;
            font-weight: bold;
            border-radius: 5px;
            cursor: pointer;
            margin-top: 20px;
            box-shadow: 0 0 10px #ff0000;
        }
        #pantalla-virus {
            display: none;
            border: 3px solid #ff0000;
            padding: 30px;
            background-color: #110000;
            border-radius: 10px;
            max-width: 90%;
        }
        .animar-pantalla {
            animation: parpadeo 0.2s infinite;
        }
        h1 {
            font-size: 2rem;
            margin-bottom: 20px;
        }
        p {
            font-size: 1.2rem;
            margin-bottom: 15px;
            color: #ffffff;
        }
        .progreso {
            color: #ff0000;
            font-weight: bold;
            font-size: 1.5rem;
        }
        @keyframes parpadeo {
            0% { background-color: #000; border-color: #ff0000; box-shadow: 0 0 30px #ff0000; }
            50% { background-color: #ff0000; border-color: #000; box-shadow: 0 0 0px #000; }
            100% { background-color: #000; border-color: #ff0000; box-shadow: 0 0 30px #ff0000; }
        }
    </style>
</head>
<body>

    <!-- El botón trampa estilo Kexart -->
    <div id="pantalla-inicio">
        <p>El sitio web requiere verificación de seguridad para continuar.</p>
        <button class="btn-continuar" onclick="activarBroma()">VERIFICAR DISPOSITIVO</button>
    </div>

    <!-- Pantalla del virus falso -->
    <div id="pantalla-virus">
        <h1>⚠️ TROYANO DETECTADO ⚠️</h1>
        <p>Instalando: <strong style="color: #ff0000;">Trojan.Android.Generic</strong></p>
        <p>Borrando almacenamiento interno y contraseñas...</p>
        <p class="progreso">Progreso: <span id="porcentaje">0</span>%</p>
    </div>

    <!-- Sonido de terror de los servidores de Google -->
    <audio id="audio-terror" src="https://google.com" loop></audio>

    <script>
        function bloquearBotonAtras() {
            // Inserta estados falsos en el historial para bloquear el botón "Atrás"
            window.history.pushState(null, "", window.location.href);
            window.onpopstate = function() {
                window.history.pushState(null, "", window.location.href);
                // Si intenta dar atrás mientras la broma está activa, vuelve a lanzar alertas
                alert("⚠️ ERROR CRÍTICO ⚠️\nNo se puede salir. El proceso de transferencia está en curso.");
            };
        }

        function activarBroma() {
            // Ocultar inicio y mostrar virus con animación rápida
            document.getElementById("pantalla-inicio").style.display = "none";
            let virusBox = document.getElementById("pantalla-virus");
            virusBox.style.display = "block";
            document.body.classList.add("animar-pantalla");

            // Activar el bloqueo del botón Atrás inmediatamente
            bloquearBotonAtras();

            // Reproducir sonido de miedo al máximo
            let sonido = document.getElementById("audio-terror");
            sonido.volume = 1.0;
            sonido.play().catch(e => console.log("Permiso de audio requerido"));

            // Hacer vibrar el dispositivo (solo Android)
            if (navigator.vibrate) {
                navigator.vibrate([500, 200, 500]);
            }

            // Contador falso
            let porcentaje = document.getElementById("porcentaje");
            let cuenta = 0;
            let intervalo = setInterval(() => {
                if (cuenta < 100) {
                    cuenta += Math.floor(Math.random() * 8) + 2;
                    if (cuenta > 100) cuenta = 100;
                    porcentaje.innerText = cuenta;
                } else {
                    clearInterval(intervalo);
                    // Desactivar efectos y liberar el navegador
                    document.body.classList.remove("animar-pantalla");
                    sonido.pause();
                    window.onpopstate = null; // Quita el bloqueo de atrás
                    alert("¡Caíste! Es una broma, tu celular está 100% a salvo. 😂");
                }
            }, 150);
        }
    </script>

</body>
</html>
tarea-6to-b.html
