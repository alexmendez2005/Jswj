<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Escena Anime en HTML</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background: linear-gradient(135deg, #1a2a6c, #b21f1f, #fdbb2d);
            font-family: 'Arial', sans-serif;
            overflow: hidden;
        }
        
        .container {
            position: relative;
            width: 900px;
            height: 600px;
        }
        
        .scene {
            position: relative;
            width: 100%;
            height: 100%;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.5);
            background: linear-gradient(to bottom, #87CEEB, #E0F7FA);
        }
        
        /* Estrellas */
        .star {
            position: absolute;
            background: white;
            border-radius: 50%;
            animation: twinkle 3s infinite;
        }
        
        @keyframes twinkle {
            0%, 100% { opacity: 0.2; }
            50% { opacity: 1; }
        }
        
        /* Montañas */
        .mountain {
            position: absolute;
            bottom: 0;
            width: 0;
            height: 0;
            border-left: 200px solid transparent;
            border-right: 200px solid transparent;
            border-bottom: 300px solid #4a7a5d;
            z-index: 5;
        }
        
        .mountain:nth-child(1) {
            left: 100px;
            border-bottom-color: #3d634f;
        }
        
        .mountain:nth-child(2) {
            left: 350px;
            border-bottom-color: #2d4a3a;
            transform: scale(0.9);
        }
        
        .mountain:nth-child(3) {
            left: 600px;
            border-bottom-color: #3d634f;
            transform: scale(0.8);
        }
        
        /* Árboles */
        .tree {
            position: absolute;
            bottom: 0;
            z-index: 10;
        }
        
        .tree-trunk {
            width: 15px;
            height: 60px;
            background: #5d4037;
            margin: 0 auto;
        }
        
        .tree-leaves {
            width: 80px;
            height: 80px;
            background: #2e7d32;
            border-radius: 50%;
            margin-top: -40px;
            margin-left: -32.5px;
        }
        
        .tree:nth-child(4) { left: 200px; }
        .tree:nth-child(5) { left: 300px; transform: scale(0.8); }
        .tree:nth-child(6) { left: 450px; transform: scale(1.1); }
        .tree:nth-child(7) { left: 700px; }
        
        /* Personaje anime */
        .character {
            position: absolute;
            bottom: 50px;
            left: 50%;
            transform: translateX(-50%);
            z-index: 20;
            animation: float 4s ease-in-out infinite;
        }
        
        .head {
            width: 100px;
            height: 100px;
            background: #ffdbac;
            border-radius: 50%;
            position: relative;
            z-index: 2;
        }
        
        .hair {
            width: 120px;
            height: 60px;
            background: #5d4037;
            border-radius: 60px 60px 0 0;
            position: absolute;
            top: -30px;
            left: -10px;
            z-index: 1;
        }
        
        .eye {
            width: 20px;
            height: 25px;
            background: white;
            border-radius: 50%;
            position: absolute;
            top: 40px;
        }
        
        .eye.left { left: 25px; }
        .eye.right { right: 25px; }
        
        .pupil {
            width: 10px;
            height: 10px;
            background: #212121;
            border-radius: 50%;
            position: absolute;
            top: 8px;
            left: 5px;
        }
        
        .body {
            width: 80px;
            height: 120px;
            background: #4a148c;
            border-radius: 40px 40px 10px 10px;
            position: absolute;
            top: 100px;
            left: 10px;
            z-index: 1;
        }
        
        .arm {
            width: 20px;
            height: 70px;
            background: #4a148c;
            position: absolute;
            top: 110px;
        }
        
        .arm.left {
            left: -10px;
            transform: rotate(15deg);
            animation: wave-left 3s infinite;
        }
        
        .arm.right {
            right: -10px;
            transform: rotate(-15deg);
            animation: wave-right 3s infinite;
        }
        
        .leg {
            width: 25px;
            height: 80px;
            background: #311b92;
            position: absolute;
            top: 215px;
        }
        
        .leg.left { left: 20px; }
        .leg.right { right: 20px; }
        
        /* Sol */
        .sun {
            position: absolute;
            top: 100px;
            right: 150px;
            width: 80px;
            height: 80px;
            background: #ffeb3b;
            border-radius: 50%;
            box-shadow: 0 0 40px #ff9800, 0 0 80px #ff5722;
            animation: sun-pulse 4s infinite;
            z-index: 4;
        }
        
        /* Nubes */
        .cloud {
            position: absolute;
            background: white;
            border-radius: 50%;
            filter: drop-shadow(0 0 5px rgba(0,0,0,0.1));
            animation: cloud-move 30s linear infinite;
            z-index: 3;
        }
        
        /* Mensaje anime */
        .speech-bubble {
            position: absolute;
            top: 50px;
            left: 50%;
            transform: translateX(-50%);
            background: white;
            padding: 20px;
            border-radius: 20px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            font-family: 'Comic Sans MS', cursive;
            font-size: 18px;
            text-align: center;
            max-width: 300px;
            z-index: 30;
            animation: bubble-pulse 2s infinite;
        }
        
        .speech-bubble:after {
            content: '';
            position: absolute;
            bottom: -20px;
            left: 50%;
            border: 10px solid transparent;
            border-top: 10px solid white;
        }
        
        /* Botón interactivo */
        .btn-container {
            position: absolute;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            z-index: 50;
        }
        
        .anime-btn {
            background: #ff4081;
            color: white;
            border: none;
            padding: 12px 30px;
            font-size: 18px;
            border-radius: 30px;
            cursor: pointer;
            font-family: 'Arial', sans-serif;
            font-weight: bold;
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
            transition: all 0.3s ease;
        }
        
        .anime-btn:hover {
            background: #d81b60;
            transform: scale(1.05);
            box-shadow: 0 7px 20px rgba(0,0,0,0.4);
        }
        
        /* Animaciones */
        @keyframes float {
            0%, 100% { transform: translateX(-50%) translateY(0); }
            50% { transform: translateX(-50%) translateY(-20px); }
        }
        
        @keyframes wave-left {
            0%, 100% { transform: rotate(15deg); }
            50% { transform: rotate(25deg); }
        }
        
        @keyframes wave-right {
            0%, 100% { transform: rotate(-15deg); }
            50% { transform: rotate(-25deg); }
        }
        
        @keyframes sun-pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.1); }
        }
        
        @keyframes cloud-move {
            0% { transform: translateX(900px); }
            100% { transform: translateX(-200px); }
        }
        
        @keyframes bubble-pulse {
            0%, 100% { transform: translateX(-50%) scale(1); }
            50% { transform: translateX(-50%) scale(1.03); }
        }
        
        .title {
            position: absolute;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            color: white;
            font-size: 36px;
            text-shadow: 0 2px 10px rgba(0,0,0,0.5);
            z-index: 40;
            font-family: 'Arial', sans-serif;
            text-align: center;
            width: 100%;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1 class="title">Escena Anime en HTML</h1>
        
        <div class="scene" id="scene">
            <!-- Estrellas -->
            <div class="star" style="top: 50px; left: 100px; width: 3px; height: 3px; animation-delay: 0s;"></div>
            <div class="star" style="top: 80px; left: 300px; width: 2px; height: 2px; animation-delay: 1s;"></div>
            <div class="star" style="top: 120px; left: 500px; width: 4px; height: 4px; animation-delay: 0.5s;"></div>
            <div class="star" style="top: 70px; left: 700px; width: 3px; height: 3px; animation-delay: 1.5s;"></div>
            
            <!-- Sol -->
            <div class="sun"></div>
            
            <!-- Montañas -->
            <div class="mountain"></div>
            <div class="mountain"></div>
            <div class="mountain"></div>
            
            <!-- Árboles -->
            <div class="tree">
                <div class="tree-trunk"></div>
                <div class="tree-leaves"></div>
            </div>
            <div class="tree">
                <div class="tree-trunk"></div>
                <div class="tree-leaves"></div>
            </div>
            <div class="tree">
                <div class="tree-trunk"></div>
                <div class="tree-leaves"></div>
            </div>
            <div class="tree">
                <div class="tree-trunk"></div>
                <div class="tree-leaves"></div>
            </div>
            
            <!-- Personaje anime -->
            <div class="character">
                <div class="hair"></div>
                <div class="head">
                    <div class="eye left">
                        <div class="pupil"></div>
                    </div>
                    <div class="eye right">
                        <div class="pupil"></div>
                    </div>
                </div>
                <div class="body"></div>
                <div class="arm left"></div>
                <div class="arm right"></div>
                <div class="leg left"></div>
                <div class="leg right"></div>
            </div>
            
            <!-- Nubes -->
            <div class="cloud" style="top: 150px; width: 100px; height: 50px; animation-delay: 0s;"></div>
            <div class="cloud" style="top: 100px; width: 80px; height: 40px; animation-delay: 5s;"></div>
            <div class="cloud" style="top: 200px; width: 120px; height: 60px; animation-delay: 10s;"></div>
            <div class="cloud" style="top: 180px; width: 70px; height: 35px; animation-delay: 15s;"></div>
            
            <!-- Mensaje -->
            <div class="speech-bubble">¡Hola! Soy un personaje anime creado con HTML y CSS</div>
            
            <!-- Botón -->
            <div class="btn-container">
                <button class="anime-btn" onclick="changeScene()">Cambiar Escena</button>
            </div>
        </div>
    </div>

    <script>
        // Crear estrellas dinámicamente
        for(let i = 0; i < 30; i++) {
            const star = document.createElement('div');
            star.className = 'star';
            
            const top = Math.random() * 250;
            const left = Math.random() * 900;
            const size = Math.random() * 3 + 1;
            const delay = Math.random() * 3;
            
            star.style.top = `${top}px`;
            star.style.left = `${left}px`;
            star.style.width = `${size}px`;
            star.style.height = `${size}px`;
            star.style.animationDelay = `${delay}s`;
            
            document.getElementById('scene').appendChild(star);
        }
        
        // Cambio de escena
        function changeScene() {
            const scene = document.querySelector('.scene');
            const sun = document.querySelector('.sun');
            const title = document.querySelector('.title');
            
            if(scene.style.background.includes('87CEEB')) {
                // Cambiar a noche
                scene.style.background = 'linear-gradient(to bottom, #0f2027, #203a43, #2c5364)';
                sun.style.background = '#e0e0e0';
                sun.style.boxShadow = '0 0 40px #ffffff, 0 0 80px #e0e0e0';
                title.textContent = 'Escena Nocturna Anime';
            } else {
                // Volver a día
                scene.style.background = 'linear-gradient(to bottom, #87CEEB, #E0F7FA)';
                sun.style.background = '#ffeb3b';
                sun.style.boxShadow = '0 0 40px #ff9800, 0 0 80px #ff5722';
                title.textContent = 'Escena Anime en HTML';
            }
        }
    </script>
</body>
</html>
