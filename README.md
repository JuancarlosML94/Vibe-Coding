# Vibe-Coding
PROMPT 1 – GENERACIÓN INICIAL

Quiero que generes una landing page completa usando SOLO HTML, CSS y JavaScript vanilla (sin frameworks, sin librerías externas).

Temática:
Landing page informativa e interactiva llamada “IA Cost Calculator”, que permita calcular de forma aproximada el coste económico y energético del uso de modelos de inteligencia artificial según la cantidad de tokens consumidos.

Requisitos:
- Estructura en un solo archivo index.html (CSS y JS incluidos dentro del HTML).
- Diseño moderno, limpio y profesional.
- Totalmente responsive (adaptado a móvil, tablet y escritorio).
- Lenguaje claro y divulgativo.

Contenido mínimo:
- Header con título y breve descripción del proyecto.
- Sección explicativa sobre qué son los tokens y por qué consumen energía.
- Calculadora interactiva:
  - Input numérico para introducir número de tokens.
  - Selector de tipo de modelo (básico, medio, avanzado).
  - Botón para calcular.
- Resultados mostrados dinámicamente:
  - Coste estimado en euros.
  - Consumo energético aproximado.
  - Comparación visual (por ejemplo: equivalente a horas de uso de una bombilla).
- Gráfica sencilla hecha con JavaScript y canvas (sin librerías).
- Footer con nota aclaratoria de que los datos son estimaciones.

Usa colores suaves, tipografía legible y animaciones ligeras.

PROMPT 2 – MEJORA VISUAL

Mejora el diseño visual de la landing:
- Añade transiciones suaves.
- Mejora el aspecto de botones e inputs.
- Usa una paleta de colores tecnológica (azules, verdes o morados).
No cambies la funcionalidad existente.

PROMPT 3 – INTERACTIVIDAD

Añade validaciones a los inputs y mensajes de error claros.
Haz que los resultados aparezcan con una animación suave.
No elimines nada del código existente.

PROMPT 4 – ACCESIBILIDAD

Mejora la accesibilidad:
- Buen contraste de colores.
- Etiquetas label en los inputs.
- Uso correcto de elementos semánticos HTML.
Mantén el diseño responsive.

--- LANDING PAGE COMPLETA ---
  
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IA Cost Calculator - Calculadora de Impacto Económico y Energético</title>
    <meta name="description" content="Calculadora accesible para estimar costes y consumo energético de modelos de Inteligencia Artificial.">
    
    <style>
        /* --- VARIABLES & ACCESIBILIDAD --- */
        :root {
            /* Paleta Tecnológica Accesible */
            /* Se han oscurecido los colores base para mejorar el ratio de contraste */
            --primary-color: #4f46e5;
            --primary-dark: #4338ca;
            --accent-cyan: #0891b2; /* Cian más oscuro para contraste sobre fondos claros */
            --error-color: #d32f2f; /* Rojo oscuro accesible */
            
            /* Fondos y Textos */
            --bg-body: #f8fafc;
            --bg-card: #ffffff;
            --text-main: #0f172a; /* Slate 900 */
            --text-light: #475569; /* Slate 600 - Ratio contraste > 4.5:1 */
            --border-color: #cbd5e1;
            
            /* UI Elements */
            --radius-md: 12px;
            --radius-lg: 16px;
            --shadow-soft: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
            --focus-ring: 0 0 0 3px rgba(79, 70, 229, 0.4); /* Anillo de foco visible */
            
            --transition-speed: 0.3s ease;
        }

        /* RESET & BASE */
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            background-color: var(--bg-body);
            color: var(--text-main);
            line-height: 1.6;
            padding-bottom: 3rem;
        }

        /* --- ACCESIBILIDAD TECLADO --- */
        *:focus-visible {
            outline: none;
            box-shadow: var(--focus-ring);
            border-color: var(--primary-color);
        }

        /* --- LAYOUT --- */
        .container {
            max-width: 800px;
            margin: 0 auto;
            padding: 0 1.5rem;
        }

        /* --- TIPOGRAFÍA --- */
        h1, h2, h3 {
            color: var(--text-main);
            font-weight: 800;
            line-height: 1.2;
        }

        h1 {
            font-size: 2.5rem; /* ~40px */
            margin-bottom: 1rem;
            color: var(--primary-color);
        }

        h2 {
            font-size: 1.5rem; /* ~24px */
            margin-bottom: 1rem;
        }

        p {
            margin-bottom: 1.2rem;
            color: var(--text-light);
            font-size: 1.05rem; /* Texto base ligeramente más grande */
        }

        /* --- HEADER --- */
        header {
            text-align: center;
            padding: 4rem 0 2.5rem;
        }

        .subtitle {
            font-size: 1.25rem;
            max-width: 600px;
            margin: 0 auto;
        }

        /* --- SECCIONES (Cards) --- */
        section {
            background: var(--bg-card);
            border-radius: var(--radius-lg);
            border: 1px solid var(--border-color);
            box-shadow: var(--shadow-soft);
            padding: 2rem;
            margin-bottom: 2rem;
        }

        .info-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 2rem;
        }

        @media (max-width: 700px) {
            .info-grid { grid-template-columns: 1fr; }
            h1 { font-size: 2rem; }
        }

        /* --- FORMULARIOS ACCESIBLES --- */
        .form-group {
            margin-bottom: 1.5rem;
        }

        label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 700;
            color: var(--text-main);
            font-size: 1rem;
        }

        .helper-text {
            display: block;
            margin-top: 0.5rem;
            font-size: 0.9rem;
            color: var(--text-light);
        }

        input, select {
            width: 100%;
            padding: 0.875rem;
            font-size: 1rem;
            border: 2px solid var(--border-color);
            border-radius: var(--radius-md);
            background-color: #fff;
            color: var(--text-main);
            transition: border-color 0.2s;
        }

        input:hover, select:hover {
            border-color: #94a3b8;
        }

        /* Estados de Error */
        input[aria-invalid="true"] {
            border-color: var(--error-color);
            background-color: #fef2f2;
        }

        .error-msg {
            color: var(--error-color);
            font-weight: 600;
            font-size: 0.9rem;
            margin-top: 0.5rem;
            display: none; /* Oculto por defecto */
            align-items: center;
            gap: 0.5rem;
        }

        .error-msg.visible {
            display: flex;
            animation: slideDown 0.2s ease-out;
        }

        @keyframes slideDown {
            from { opacity: 0; transform: translateY(-5px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* BOTÓN */
        button {
            display: block;
            width: 100%;
            padding: 1rem;
            background-color: var(--primary-color);
            color: white;
            border: none;
            border-radius: var(--radius-md);
            font-size: 1.125rem;
            font-weight: 700;
            cursor: pointer;
            transition: background-color 0.2s, transform 0.1s;
        }

        button:hover {
            background-color: var(--primary-dark);
        }

        button:active {
            transform: scale(0.98);
        }

        /* --- RESULTADOS --- */
        #results {
            display: none;
            background: linear-gradient(to bottom, #ffffff, #eff6ff);
            border-top: 4px solid var(--primary-color);
        }

        #results.visible {
            display: block;
            animation: fadeIn 0.5s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .metrics-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1.5rem;
            margin: 1.5rem 0;
        }

        .metric-card {
            background: white;
            padding: 1.5rem;
            border-radius: var(--radius-md);
            border: 1px solid var(--border-color);
            text-align: center;
        }

        .metric-value {
            display: block;
            font-size: 2.25rem;
            font-weight: 800;
            color: var(--primary-color);
            margin: 0.5rem 0;
            font-variant-numeric: tabular-nums;
        }

        .bulb-analogy {
            background-color: #ecfeff;
            border: 1px solid #cffafe;
            border-left: 5px solid var(--accent-cyan);
            padding: 1.25rem;
            border-radius: 8px;
            margin-bottom: 2rem;
            display: flex;
            align-items: flex-start;
            gap: 1rem;
        }

        .bulb-icon {
            font-size: 1.5rem;
            flex-shrink: 0;
        }

        /* CANVAS CONTAINER */
        .chart-container {
            width: 100%;
            overflow-x: auto;
            background: #f8fafc;
            border: 1px solid var(--border-color);
            border-radius: var(--radius-md);
            padding: 1rem;
            margin-top: 1rem;
        }

        footer {
            text-align: center;
            font-size: 0.875rem;
            color: var(--text-light);
            margin-top: 4rem;
        }
    </style>
</head>
<body>

    <header class="container">
        <h1>IA Cost Calculator</h1>
        <p class="subtitle">Calculadora accesible para estimar el impacto económico y energético de la Inteligencia Artificial.</p>
    </header>

    <main class="container">
        
        <section aria-labelledby="heading-info">
            <h2 id="heading-info">Conceptos Básicos</h2>
            <div class="info-grid">
                <article>
                    <h3>¿Qué es un Token?</h3>
                    <p>Un token es la unidad básica de información en IA (similar a una sílaba). 1,000 tokens equivalen aproximadamente a 750 palabras.</p>
                </article>
                <article>
                    <h3>¿Por qué consume energía?</h3>
                    <p>Cada consulta activa miles de procesadores en centros de datos, consumiendo electricidad para el cálculo y la refrigeración.</p>
                </article>
            </div>
        </section>

        <section aria-labelledby="heading-calc">
            <h2 id="heading-calc">Calculadora</h2>
            
            <form id="calcForm" novalidate onsubmit="return false;">
                <div class="form-group">
                    <label for="tokens">Cantidad de Tokens (Entrada + Salida)</label>
                    
                    <input 
                        type="number" 
                        id="tokens" 
                        name="tokens"
                        min="1" 
                        placeholder="Ej: 1000000" 
                        aria-describedby="tokens-hint tokens-error"
                        required
                    >
                    
                    <span id="tokens-hint" class="helper-text">
                        Tip: Una novela corta tiene unos 100,000 tokens.
                    </span>
                    
                    <div id="tokens-error" class="error-msg" role="alert">
                        <span>⚠️</span>
                        <span id="tokens-error-text">Por favor introduce un número válido.</span>
                    </div>
                </div>

                <div class="form-group">
                    <label for="modelType">Tipo de Modelo de IA</label>
                    <select id="modelType" name="modelType">
                        <option value="basic">Modelo Básico (Rápido y económico)</option>
                        <option value="standard" selected>Modelo Estándar (Equilibrado)</option>
                        <option value="advanced">Modelo Avanzado (Razonamiento complejo)</option>
                    </select>
                </div>

                <button type="button" onclick="handleCalculate()">Calcular Impacto</button>
            </form>
        </section>

        <section id="results" aria-labelledby="heading-results" aria-live="polite">
            <h2 id="heading-results">Resultados Estimados</h2>
            
            <div class="metrics-grid">
                <div class="metric-card">
                    <span class="metric-label">Coste Económico</span>
                    <output class="metric-value" id="res-cost">0.00 €</output>
                </div>
                <div class="metric-card">
                    <span class="metric-label">Energía Consumida</span>
                    <output class="metric-value" id="res-energy">0.00 Wh</output>
                </div>
            </div>

            <div class="bulb-analogy">
                <span class="bulb-icon" aria-hidden="true">💡</span>
                <p id="res-analogy" style="margin:0">
                    Calculando equivalencia...
                </p>
            </div>

            <h3>Comparativa Visual de Costes</h3>
            <div class="chart-container">
                <canvas id="costChart" width="600" height="300" role="img" aria-label="Gráfico de barras comparando el coste de tu consulta entre modelos básico, estándar y avanzado.">
                    <p>Tu navegador no soporta gráficos. Datos textuales: El modelo básico costaría <span id="alt-basic"></span>, el estándar <span id="alt-std"></span> y el avanzado <span id="alt-adv"></span>.</p>
                </canvas>
            </div>
        </section>

    </main>

    <footer>
        <p><strong>Aviso:</strong> Datos estimados basados en precios promedio de mercado (2025). Proyecto Open Source.</p>
    </footer>

    <script>
        // Datos constantes
        const PRICING = { basic: 0.50, standard: 5.00, advanced: 15.00 };
        const ENERGY_FACTOR = { basic: 0.3, standard: 1.5, advanced: 4.0 };
        const BULB_WATTS = 9;

        // Gestión de Errores Accesible
        function setError(hasError, message = "") {
            const input = document.getElementById('tokens');
            const errorContainer = document.getElementById('tokens-error');
            const errorText = document.getElementById('tokens-error-text');

            if (hasError) {
                input.setAttribute('aria-invalid', 'true');
                errorText.textContent = message;
                errorContainer.classList.add('visible');
                input.focus(); // Llevar foco al error para corrección rápida
            } else {
                input.setAttribute('aria-invalid', 'false');
                errorContainer.classList.remove('visible');
            }
        }

        // Limpiar error al escribir
        document.getElementById('tokens').addEventListener('input', () => setError(false));

        function handleCalculate() {
            const tokensInput = document.getElementById('tokens');
            const modelType = document.getElementById('modelType').value;
            const resultsSection = document.getElementById('results');

            // Validación
            const val = parseFloat(tokensInput.value);

            if (!tokensInput.value || isNaN(val)) {
                setError(true, "El campo no puede estar vacío.");
                return;
            }
            if (val <= 0) {
                setError(true, "La cantidad debe ser mayor a 0.");
                return;
            }
            if (!Number.isInteger(val)) {
                setError(true, "Por favor introduce un número entero.");
                return;
            }

            // Cálculos
            const cost = (val / 1000000) * PRICING[modelType];
            const energyWh = (val / 1000) * ENERGY_FACTOR[modelType];
            const bulbHours = energyWh / BULB_WATTS;

            // Mostrar Sección
            resultsSection.classList.add('visible');
            
            // Animación y Actualización de DOM
            animateValue("res-cost", cost, true);
            animateValue("res-energy", energyWh, false);

            // Texto de analogía
            const hoursStr = bulbHours.toFixed(2);
            let analogyHTML = `Esta energía equivale a una bombilla LED encendida durante <strong>${hoursStr} horas</strong>.`;
            document.getElementById('res-analogy').innerHTML = analogyHTML;

            // Dibujar gráfica y actualizar fallback de accesibilidad
            updateChartAccessibility(val);
            drawChart(val, modelType);
            
            // Scroll suave accesible (prefiere-reducción-movimiento respetado por CSS default, aquí forzamos smooth si no)
            resultsSection.scrollIntoView({ behavior: 'smooth', block: 'nearest' });
        }

        // Función para actualizar el texto alternativo del Canvas
        function updateChartAccessibility(tokens) {
            const keys = ["basic", "standard", "advanced"];
            keys.forEach(k => {
                const val = (tokens / 1000000) * PRICING[k];
                const el = document.getElementById(`alt-${k === 'standard' ? 'std' : (k === 'advanced' ? 'adv' : 'basic')}`);
                if(el) el.textContent = formatCurrency(val);
            });
        }

        function animateValue(id, end, isCurrency) {
            const obj = document.getElementById(id);
            // Simulación simple para no complicar el lector de pantalla con cambios muy rápidos
            // En a11y, a veces es mejor poner el valor final directo si la animación es muy rápida
            if (isCurrency) obj.textContent = formatCurrency(end);
            else obj.textContent = formatEnergy(end);
        }

        function formatCurrency(val) {
            return new Intl.NumberFormat('es-ES', { style: 'currency', currency: 'EUR', minimumFractionDigits: 4 }).format(val);
        }

        function formatEnergy(val) {
            return val >= 1000 ? (val/1000).toFixed(3) + " kWh" : val.toFixed(2) + " Wh";
        }

        function drawChart(tokens, currentModel) {
            const canvas = document.getElementById('costChart');
            const ctx = canvas.getContext('2d');
            const w = canvas.width;
            const h = canvas.height;
            
            ctx.clearRect(0, 0, w, h);

            const labels = ["Básico", "Estándar", "Avanzado"];
            const keys = ["basic", "standard", "advanced"];
            const values = keys.map(k => (tokens / 1000000) * PRICING[k]);
            const maxVal = Math.max(...values) || 1;

            const padding = 40;
            const chartH = h - padding * 2;
            const barW = 80;
            const gap = (w - (padding * 2) - (barW * 3)) / 2;

            // Dibujar ejes
            ctx.beginPath();
            ctx.strokeStyle = '#94a3b8';
            ctx.moveTo(padding, padding);
            ctx.lineTo(padding, h - padding);
            ctx.lineTo(w - padding, h - padding);
            ctx.stroke();

            keys.forEach((key, i) => {
                const val = values[i];
                const barH = (val / maxVal) * chartH;
                const x = padding + 40 + (i * (barW + gap));
                const y = h - padding - barH;

                // Color con contraste suficiente
                ctx.fillStyle = key === currentModel ? '#4f46e5' : '#cbd5e1'; 
                
                ctx.fillRect(x, y, barW, barH);

                // Texto Valor
                ctx.fillStyle = '#0f172a';
                ctx.font = 'bold 14px Arial'; // Fuente más grande para legibilidad
                ctx.textAlign = 'center';
                let txt = val < 0.01 ? val.toFixed(4) : val.toFixed(2);
                ctx.fillText(txt + '€', x + barW/2, y - 10);

                // Texto Etiqueta
                ctx.fillStyle = '#475569';
                ctx.fillText(labels[i], x + barW/2, h - padding + 20);
            });
        }
    </script>
</body>
</html>
