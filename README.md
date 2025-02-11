<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Feliz San Valentín, Jaqueline</title>
  <style>
    /* Estilos generales */
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      background-color: #ffe6e6;
      color: #b30000;
      overflow: hidden;
      margin: 0;
      padding: 0;
    }
    h1, h2, p {
      margin: 10px;
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
    /* Pantalla de bienvenida */
    .pantalla-bienvenida {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(255,255,255,0.9);
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
      justify-content: center;
      gap: 50px; /* Mayor separación entre botones */
      margin-top: 20px;
    }
    .boton-no {
      position: absolute;
    }
    /* Contenido principal (inicialmente oculto) */
    .contenido {
      display: none;
      padding: 20px;
      overflow-y: auto;
      height: 100vh;
    }
    /* Animación de corazones flotando */
    .corazones {
      position: fixed;
      top: 0;
      left: 50%;
      transform: translateX(-50%);
      pointer-events: none;
      width: 100%;
      height: 100%;
      z-index: 1;
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
    /* Estilos para el rompecabezas */
    #rompecabezas {
      margin-top: 40px;
    }
    #puzzle-board {
      display: grid;
      grid-template-columns: repeat(3, 100px);
      grid-gap: 5px;
      justify-content: center;
      margin: 20px auto;
      width: 310px;
      height: 310px;
      border: 2px solid #b30000;
      padding: 5px;
      background-color: #fff;
    }
    .puzzle-cell {
      width: 100px;
      height: 100px;
      border: 1px dashed #ccc;
      position: relative;
    }
    #puzzle-pieces {
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      gap: 10px;
      margin: 20px auto;
      width: 320px;
    }
    .puzzle-piece {
      width: 100px;
      height: 100px;
      background-image: url('https://github.com/tuusuario/tu-repositorio/raw/main/rompecabezas.jpg');
      background-size: 300px 300px;
      border: 1px solid #b30000;
      cursor: grab;
    }
    .puzzle-piece.dragging {
      opacity: 0.5;
    }
    /* Sección de Perritos Enamorados */
    #perritos {
      margin-top: 40px;
    }
    #perritos h2 {
      font-size: 28px;
      margin-bottom: 20px;
    }
    .galeria {
      display: flex;
      justify-content: center;
      gap: 20px;
      flex-wrap: wrap;
    }
    .galeria img {
      width: 300px;
      max-width: 100%;
      border: 3px solid #b30000;
      border-radius: 10px;
      transition: transform 0.3s;
    }
    .galeria img:hover {
      transform: scale(1.05);
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

  <!-- Contenido Principal -->
  <div class="contenido">
    <h1>Feliz San Valentín, <span class="nombre">Jaqueline</span> ❤️</h1>
    <div class="contenedor">
      <img class="gatito" src="https://media.giphy.com/media/3oriO0OEd9QIDdllqo/giphy.gif" alt="Gatitos abrazándose" style="width:200px; animation: latido 1.5s infinite alternate;">
      <div class="frase" style="font-size:24px; margin:20px; padding:20px; border:2px solid #b30000; background:#fff; display:inline-block; border-radius:10px; box-shadow:2px 2px 10px rgba(0,0,0,0.2);">
        "Eres mi razón de sonreír cada día."
      </div>
      <div class="frase" style="font-size:24px; margin:20px; padding:20px; border:2px solid #b30000; background:#fff; display:inline-block; border-radius:10px; box-shadow:2px 2px 10px rgba(0,0,0,0.2);">
        "Si tuviera que elegir entre amarte y respirar, usaría mi último aliento para decirte cuánto te amo."
      </div>
    </div>
    <p class="mensaje" style="font-size:22px; font-weight:bold; color:#d10000; animation: parpadeo 1s infinite alternate;">💖 ¡Siempre estaré aquí para ti! 💖</p>
    <button class="boton" onclick="enviarMensaje()">💌 Enviar Mensaje de Amor</button>

    <!-- Sección del rompecabezas -->
    <section id="rompecabezas">
      <h2>Arma el rompecabezas</h2>
      <p>Arrastra y suelta las piezas para armar la imagen.</p>
      <div id="puzzle-board"></div>
      <div id="puzzle-pieces"></div>
      <button id="check-puzzle" class="boton">Verificar rompecabezas</button>
      <p id="puzzle-message"></p>
    </section>

    <!-- Sección de Perritos Enamorados -->
    <section id="perritos">
      <h2>Perritos Enamorados</h2>
      <p>Disfruta de estas tiernas imágenes de perritos en blanco y negro enamorados.</p>
      <div class="galeria">
        <img src="https://images.pexels.com/photos/1820081/pexels-photo-1820081.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940" alt="Perrito enamorado 1">
        <img src="https://images.pexels.com/photos/416160/pexels-photo-416160.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940" alt="Perrito enamorado 2">
      </div>
    </section>

    <audio autoplay loop>
      <source src="https://www.bensound.com/bensound-music/bensound-romantic.mp3" type="audio/mpeg">
      Tu navegador no soporta el audio.
    </audio>
  </div>

  <div class="corazones"></div>

  <script>
    // Funciones de la pantalla de bienvenida
    function aceptar() {
      document.querySelector(".pantalla-bienvenida").style.display = "none";
      document.querySelector(".contenido").style.display = "block";
    }
    function moverNo() {
      let botonNo = document.getElementById("botonNo");
      let x = Math.random() * (window.innerWidth - 100);
      let y = Math.random() * (window.innerHeight - 50);
      botonNo.style.left = x + "px";
      botonNo.style.top = y + "px";
    }
    function enviarMensaje() {
      alert("💖 ¡Te quiero mucho, Jaqueline! 💖");
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

    // Funcionalidad del rompecabezas
    const rows = 3;
    const cols = 3;
    const pieceWidth = 100;
    const pieceHeight = 100;
    // Reemplaza la URL de abajo con la URL de tu foto en GitHub
    const imageUrl = 'https://raw.githubusercontent.com/Alexiscj23/San-valentines/refs/heads/main/IMG_20190812_212839.jpg
      ';

    function setupPuzzle() {
      const puzzleBoard = document.getElementById('puzzle-board');
      const puzzlePieces = document.getElementById('puzzle-pieces');
      
      // Crear celdas en el tablero (áreas donde se soltarán las piezas)
      for (let i = 0; i < rows * cols; i++) {
        const cell = document.createElement('div');
        cell.classList.add('puzzle-cell');
        cell.dataset.index = i;
        cell.addEventListener('dragover', allowDrop);
        cell.addEventListener('drop', drop);
        puzzleBoard.appendChild(cell);
      }
      
      // Crear las piezas del rompecabezas
      let piecesArray = [];
      for (let row = 0; row < rows; row++) {
        for (let col = 0; col < cols; col++) {
          const index = row * cols + col;
          const piece = document.createElement('div');
          piece.classList.add('puzzle-piece');
          piece.draggable = true;
          piece.dataset.index = index;
          // Ajustar el fondo para mostrar la parte correspondiente de la imagen
          piece.style.backgroundImage = `url('${imageUrl}')`;
          piece.style.backgroundSize = `${cols * pieceWidth}px ${rows * pieceHeight}px`;
          piece.style.backgroundPosition = `-${col * pieceWidth}px -${row * pieceHeight}px`;
          piece.addEventListener('dragstart', dragStart);
          piece.addEventListener('dragend', dragEnd);
          piecesArray.push(piece);
        }
      }
      // Mezclar las piezas
      piecesArray = shuffleArray(piecesArray);
      piecesArray.forEach(piece => puzzlePieces.appendChild(piece));
    }

    // Función para mezclar un arreglo (shuffle)
    function shuffleArray(array) {
      for (let i = array.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [array[i], array[j]] = [array[j], array[i]];
      }
      return array;
    }

    let draggedPiece = null;
    function dragStart(e) {
      draggedPiece = this;
      setTimeout(() => {
        this.classList.add('dragging');
      }, 0);
    }
    function dragEnd(e) {
      this.classList.remove('dragging');
      draggedPiece = null;
    }
    function allowDrop(e) {
      e.preventDefault();
    }
    function drop(e) {
      e.preventDefault();
      if (draggedPiece) {
        // Si la celda ya tiene una pieza, la devolvemos al contenedor de piezas
        if (this.children.length > 0) {
          document.getElementById('puzzle-pieces').appendChild(this.children[0]);
        }
        this.appendChild(draggedPiece);
      }
    }

    // Verificar si el rompecabezas está armado correctamente y redirigir a la sorpresa
    document.getElementById('check-puzzle').addEventListener('click', () => {
      const cells = document.querySelectorAll('.puzzle-cell');
      let correct = 0;
      cells.forEach(cell => {
        if (cell.children.length > 0) {
          const piece = cell.children[0];
          if (piece.dataset.index === cell.dataset.index) {
            correct++;
          }
        }
      });
      const message = document.getElementById('puzzle-message');
      if (correct === rows * cols) {
        message.textContent = "¡Correcto! Rompecabezas armado perfectamente. 💖";
        // Redirigir a la página de sorpresa después de 3 segundos
        setTimeout(() => {
          window.location.href = 'sorpresa.html';
        }, 3000);
      } else {
        message.textContent = `Faltan ${rows * cols - correct} piezas correctas. ¡Sigue intentando!`;
      }
    });

    // Inicializar el rompecabezas cuando la página esté lista
    document.addEventListener('DOMContentLoaded', setupPuzzle);
  </script>
</body>
</html>
