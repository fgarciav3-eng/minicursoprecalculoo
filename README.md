<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mini Curso de Precálculo</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 1000px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            overflow: hidden;
        }

        header {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 40px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        header::before {
            content: '🎓📐✏️🧮📊';
            position: absolute;
            font-size: 3em;
            opacity: 0.1;
            top: 10px;
            left: 0;
            right: 0;
            letter-spacing: 30px;
        }

        header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
            position: relative;
            z-index: 1;
        }

        header p {
            font-size: 1.3em;
            opacity: 0.95;
            position: relative;
            z-index: 1;
        }

        .content {
            padding: 40px;
        }

        .intro-section {
            margin-bottom: 40px;
            line-height: 1.8;
            color: #333;
        }

        .intro-section h2 {
            color: #667eea;
            margin-bottom: 20px;
            font-size: 2em;
        }

        .intro-section h2::before {
            content: '👋 ';
        }

        .intro-section p {
            margin-bottom: 15px;
            font-size: 1.1em;
        }

        .image-banner {
            width: 100%;
            height: 300px;
            background: linear-gradient(135deg, rgba(102, 126, 234, 0.1) 0%, rgba(118, 75, 162, 0.1) 100%);
            border-radius: 15px;
            margin: 30px 0;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 5em;
            border: 3px dashed #667eea;
            position: relative;
            overflow: hidden;
        }

        .image-banner::after {
            content: '';
            position: absolute;
            width: 200%;
            height: 200%;
            background: repeating-linear-gradient(
                45deg,
                transparent,
                transparent 20px,
                rgba(102, 126, 234, 0.03) 20px,
                rgba(102, 126, 234, 0.03) 40px
            );
            animation: slide 20s linear infinite;
        }

        @keyframes slide {
            0% { transform: translate(0, 0); }
            100% { transform: translate(50px, 50px); }
        }

        .emoji-float {
            position: relative;
            z-index: 1;
        }

        .modules-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
            gap: 30px;
            margin-top: 40px;
        }

        .module-card {
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            border-radius: 15px;
            padding: 30px;
            color: white;
            cursor: pointer;
            transition: transform 0.3s, box-shadow 0.3s;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            position: relative;
            overflow: hidden;
        }

        .module-card::before {
            content: '';
            position: absolute;
            top: -50%;
            right: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.1) 0%, transparent 70%);
            transition: transform 0.5s;
        }

        .module-card:hover::before {
            transform: translate(-25%, -25%);
        }

        .module-card:hover {
            transform: translateY(-10px) scale(1.02);
            box-shadow: 0 15px 30px rgba(0,0,0,0.3);
        }

        .module-card h3 {
            font-size: 2em;
            margin-bottom: 15px;
            position: relative;
            z-index: 1;
        }

        .module-card p {
            font-size: 1.1em;
            line-height: 1.6;
            position: relative;
            z-index: 1;
        }

        .module-card.ecuaciones {
            background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
        }

        .module-card.inecuaciones {
            background: linear-gradient(135deg, #43e97b 0%, #38f9d7 100%);
        }

        .module-content {
            display: none;
            animation: fadeIn 0.5s;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .module-content.active {
            display: block;
        }

        .back-button {
            background: #667eea;
            color: white;
            border: none;
            padding: 12px 30px;
            border-radius: 25px;
            font-size: 1em;
            cursor: pointer;
            margin-bottom: 30px;
            transition: background 0.3s, transform 0.2s;
        }

        .back-button:hover {
            background: #5568d3;
            transform: scale(1.05);
        }

        .section {
            margin-bottom: 40px;
            background: #f8f9fa;
            padding: 30px;
            border-radius: 15px;
            border-left: 5px solid #667eea;
        }

        .section h3 {
            color: #667eea;
            font-size: 1.8em;
            margin-bottom: 20px;
            padding-bottom: 10px;
        }

        .section p {
            line-height: 1.8;
            color: #555;
            font-size: 1.05em;
            margin-bottom: 15px;
        }

        .math-image {
            width: 100%;
            max-width: 600px;
            height: 200px;
            background: white;
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 20px auto;
            border: 3px solid #667eea;
            font-size: 3em;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        .ejemplos {
            background: white;
            padding: 25px;
            border-radius: 10px;
            margin: 20px 0;
        }

        .ejemplo-item {
            margin-bottom: 20px;
            padding: 20px;
            background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            border-left: 4px solid #667eea;
        }

        .ejemplo-item h4 {
            color: #667eea;
            margin-bottom: 15px;
            font-size: 1.3em;
        }

        .ejemplo-item h4::before {
            content: '✨ ';
        }

        .video-container {
            position: relative;
            width: 100%;
            max-width: 800px;
            margin: 30px auto;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
            background: #000;
        }

        .video-container video {
            width: 100%;
            height: auto;
            display: block;
        }

        .formula {
            background: linear-gradient(135deg, #fff3cd 0%, #ffe69c 100%);
            padding: 20px;
            border-radius: 8px;
            font-family: 'Courier New', monospace;
            font-size: 1.2em;
            margin: 15px 0;
            border-left: 5px solid #ffc107;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
            text-align: center;
        }

        .home-section.hidden {
            display: none;
        }

        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin: 30px 0;
        }

        .feature-box {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 25px;
            border-radius: 15px;
            text-align: center;
            transition: transform 0.3s;
        }

        .feature-box:hover {
            transform: translateY(-5px);
        }

        .feature-box .emoji {
            font-size: 3em;
            display: block;
            margin-bottom: 10px;
        }

        @media (max-width: 768px) {
            .modules-grid {
                grid-template-columns: 1fr;
            }
            
            header h1 {
                font-size: 2em;
            }
            
            .content {
                padding: 20px;
            }

            .image-banner {
                height: 200px;
                font-size: 3em;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>📐 Mini Curso de Precálculo</h1>
            <p>Ecuaciones e Inecuaciones de Primer Grado</p>
        </header>

        <div class="content">
            <!-- Sección de Inicio/Bienvenida -->
            <div id="home-section" class="home-section">
                <div class="intro-section">
                    <h2>Bienvenido al Curso</h2>
                    <p>
                        🎯 Este mini curso de <strong>Precálculo</strong> está diseñado para que domines los conceptos 
                        fundamentales de <strong>ecuaciones e inecuaciones de primer grado</strong>. Estos temas son 
                        la base esencial para tu éxito en matemáticas avanzadas.
                    </p>
                    
                    <div class="image-banner">
                        <div class="emoji-float">📚 🔢 ➗ ✏️ 📊</div>
                    </div>

                    <p>
                        💡 A través de este curso interactivo, aprenderás paso a paso cómo resolver problemas matemáticos 
                        con confianza. Cada módulo está cuidadosamente estructurado para maximizar tu aprendizaje.
                    </p>

                    <div class="features-grid">
                        <div class="feature-box">
                            <span class="emoji">📖</span>
                            <strong>Definiciones Claras</strong>
                        </div>
                        <div class="feature-box">
                            <span class="emoji">✍️</span>
                            <strong>Ejemplos Prácticos</strong>
                        </div>
                        <div class="feature-box">
                            <span class="emoji">🎥</span>
                            <strong>Videos Tutoriales</strong>
                        </div>
                        <div class="feature-box">
                            <span class="emoji">🎓</span>
                            <strong>Paso a Paso</strong>
                        </div>
                    </div>

                    <p style="font-size: 1.2em; text-align: center; margin-top: 30px;">
                        <strong>🚀 ¡Comienza tu viaje matemático ahora!</strong>
                    </p>
                </div>

                <h2 style="color: #667eea; text-align: center; margin: 40px 0; font-size: 2em;">
                    🎯 Selecciona un Módulo
                </h2>
                
                <div class="modules-grid">
                    <div class="module-card ecuaciones" onclick="showModule('ecuaciones')">
                        <h3>📊 Módulo 1</h3>
                        <h3>Ecuaciones de Primer Grado</h3>
                        <p>🔍 Aprende a resolver ecuaciones lineales, entiende su estructura algebraica y domina los métodos de solución con ejemplos detallados.</p>
                    </div>

                    <div class="module-card inecuaciones" onclick="showModule('inecuaciones')">
                        <h3>📈 Módulo 2</h3>
                        <h3>Inecuaciones de Primer Grado</h3>
                        <p>📐 Descubre cómo trabajar con desigualdades matemáticas, interpreta sus soluciones y representa intervalos en la recta numérica.</p>
                    </div>
                </div>
            </div>

            <!-- Módulo de Ecuaciones -->
            <div id="ecuaciones-module" class="module-content">
                <button class="back-button" onclick="showHome()">← Volver al Inicio</button>
                
                <h2 style="color: #4facfe; font-size: 2.5em; margin-bottom: 30px; text-align: center;">
                    📊 Módulo 1: Ecuaciones de Primer Grado
                </h2>

                <div class="math-image">
                    ⚖️ 2x + 5 = 13
                </div>

                <div class="section">
                    <h3>📖 Definición</h3>
                    <p>
                        ✏️ Una <strong>ecuación</strong> es una igualdad matemática que contiene una o más variables (incógnitas) 
                        y se cumple solo para ciertos valores específicos de dichas variables.
                    </p>
                    <p>
                        🎯 Una ecuación de primer grado (o lineal) es aquella en la que la variable está elevada únicamente 
                        a la potencia 1, sin exponentes mayores.
                    </p>
                    <div class="math-image" style="height: 150px;">
                        📐 ax + b = 0
                    </div>
                    <p>
                        📌 Donde:<br>
                        • <strong>a</strong> y <strong>b</strong> son números reales (coeficientes)<br>
                        • <strong>x</strong> es la variable o incógnita<br>
                        • <strong>a ≠ 0</strong> (el coeficiente de x no puede ser cero)
                    </p>
                    <p>
                        🎯 <strong>Objetivo principal:</strong> Encontrar el valor numérico de la variable que hace verdadera la igualdad.
                    </p>
                </div>

                <div class="section">
                    <h3>💡 Ejemplos Resueltos Paso a Paso</h3>
                    <div class="ejemplos">
                        <div class="ejemplo-item">
                            <h4>Ejemplo 1: Ecuación Simple</h4>
                            <p><strong>🔢 Resolver:</strong> 2x + 5 = 13</p>
                            <p><strong>📝 Solución:</strong></p>
                            <p>1️⃣ Restamos 5 a ambos lados: 2x = 13 - 5</p>
                            <p>2️⃣ Simplificamos: 2x = 8</p>
                            <p>3️⃣ Dividimos entre 2: x = 4</p>
                            <div class="formula">✅ Respuesta: x = 4</div>
                        </div>

                        <div class="ejemplo-item">
                            <h4>Ejemplo 2: Ecuación con Paréntesis</h4>
                            <p><strong>🔢 Resolver:</strong> 3(x - 2) = 2x + 4</p>
                            <p><strong>📝 Solución:</strong></p>
                            <p>1️⃣ Aplicamos propiedad distributiva: 3x - 6 = 2x + 4</p>
                            <p>2️⃣ Restamos 2x a ambos lados: x - 6 = 4</p>
                            <p>3️⃣ Sumamos 6 a ambos lados: x = 10</p>
                            <div class="formula">✅ Respuesta: x = 10</div>
                        </div>

                        <div class="ejemplo-item">
                            <h4>Ejemplo 3: Ecuación con Fracciones</h4>
                            <p><strong>🔢 Resolver:</strong> x/2 + 3 = 7</p>
                            <p><strong>📝 Solución:</strong></p>
                            <p>1️⃣ Restamos 3 a ambos lados: x/2 = 4</p>
                            <p>2️⃣ Multiplicamos por 2: x = 8</p>
                            <div class="formula">✅ Respuesta: x = 8</div>
                        </div>
                    </div>
                </div>

                <div class="section">
                    <h3>🎥 Video Tutorial Interactivo</h3>
                    <p>📺 Observa cómo resolver ecuaciones de primer grado paso a paso con este video explicativo:</p>
                    <div class="video-container">
                        <video controls>
                            <source src="https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4" type="video/mp4">
                            Tu navegador no soporta el elemento de video.
                        </video>
                    </div>
                    <p style="text-align: center; color: #666; margin-top: 15px;">
                        💡 <em>Nota: Video demostrativo. Practica los pasos mostrados en los ejemplos anteriores.</em>
                    </p>
                </div>
            </div>

            <!-- Módulo de Inecuaciones -->
            <div id="inecuaciones-module" class="module-content">
                <button class="back-button" onclick="showHome()">← Volver al Inicio</button>
                
                <h2 style="color: #43e97b; font-size: 2.5em; margin-bottom: 30px; text-align: center;">
                    📈 Módulo 2: Inecuaciones de Primer Grado
                </h2>

                <div class="math-image">
                    📊 3x + 2 > 11
                </div>

                <div class="section">
                    <h3>📖 Definición</h3>
                    <p>
                        ✏️ Una <strong>inecuación</strong> es una desigualdad matemática que relaciona expresiones algebraicas 
                        mediante símbolos de comparación (<, >, ≤, ≥).
                    </p>
                    <p>
                        🎯 A diferencia de las ecuaciones que tienen un valor específico como solución, las inecuaciones 
                        tienen un <strong>conjunto o intervalo de valores</strong> que satisfacen la desigualdad.
                    </p>
                    <div class="math-image" style="height: 150px;">
                        📐 ax + b < 0
                    </div>
                    <p>
                        📌 <strong>Símbolos de desigualdad:</strong><br>
                        • 🔹 <strong><</strong> menor que (intervalo abierto)<br>
                        • 🔸 <strong>></strong> mayor que (intervalo abierto)<br>
                        • 🔹 <strong>≤</strong> menor o igual que (intervalo cerrado)<br>
                        • 🔸 <strong>≥</strong> mayor o igual que (intervalo cerrado)
                    </p>
                    <p>
                        ⚠️ <strong>Regla fundamental:</strong> Al multiplicar o dividir ambos lados de una inecuación 
                        por un número <strong>negativo</strong>, se debe <strong>invertir el sentido</strong> del símbolo de desigualdad.
                    </p>
                </div>

                <div class="section">
                    <h3>💡 Ejemplos Resueltos Paso a Paso</h3>
                    <div class="ejemplos">
                        <div class="ejemplo-item">
                            <h4>Ejemplo 1: Inecuación Simple</h4>
                            <p><strong>🔢 Resolver:</strong> 3x + 2 > 11</p>
                            <p><strong>📝 Solución:</strong></p>
                            <p>1️⃣ Restamos 2 a ambos lados: 3x > 9</p>
                            <p>2️⃣ Dividimos entre 3: x > 3</p>
                            <div class="formula">✅ Respuesta: x > 3  📍 Intervalo: (3, +∞)</div>
                        </div>

                        <div class="ejemplo-item">
                            <h4>Ejemplo 2: Inecuación con Número Negativo</h4>
                            <p><strong>🔢 Resolver:</strong> -2x + 5 ≤ 9</p>
                            <p><strong>📝 Solución:</strong></p>
                            <p>1️⃣ Restamos 5 a ambos lados: -2x ≤ 4</p>
                            <p>2️⃣ Dividimos entre -2 y ⚠️ <strong>invertimos el símbolo</strong>: x ≥ -2</p>
                            <div class="formula">✅ Respuesta: x ≥ -2  📍 Intervalo: [-2, +∞)</div>
                        </div>

                        <div class="ejemplo-item">
                            <h4>Ejemplo 3: Inecuación con Paréntesis</h4>
                            <p><strong>🔢 Resolver:</strong> 2(x - 3) < x + 1</p>
                            <p><strong>📝 Solución:</strong></p>
                            <p>1️⃣ Aplicamos propiedad distributiva: 2x - 6 < x + 1</p>
                            <p>2️⃣ Restamos x de ambos lados: x - 6 < 1</p>
                            <p>3️⃣ Sumamos 6 a ambos lados: x < 7</p>
                            <div class="formula">✅ Respuesta: x < 7  📍 Intervalo: (-∞, 7)</div>
                        </div>
                    </div>
                </div>

                <div class="section">
                    <h3>🎥 Video Tutorial Interactivo</h3>
                    <p>📺 Aprende a resolver inecuaciones de primer grado con este video paso a paso:</p>
                    <div class="video-container">
                        <video controls>
                            <source src="https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/ElephantsDream.mp4" type="video/mp4">
                            Tu navegador no soporta el elemento de video.
                        </video>
                    </div>
                    <p style="text-align: center; color: #666; margin-top: 15px;">
                        💡 <em>Nota: Video demostrativo. Practica los pasos mostrados en los ejemplos anteriores.</em>
                    </p>
                </div>
            </div>
        </div>
    </div>

    <script>
        function showModule(module) {
            document.getElementById('home-section').classList.add('hidden');
            document.getElementById(module + '-module').classList.add('active');
            window.scrollTo(0, 0);
        }

        function showHome() {
            document.getElementById('home-section').classList.remove('hidden');
            document.querySelectorAll('.module-content').forEach(module => {
                module.classList.remove('active');
            });
            window.scrollTo(0, 0);
        }
    </script>
</body>
</html>
