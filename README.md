<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Más allá del Interés: El Valor del Dinero en el Tiempo</title>
  <style>
    body { font-family: Arial, sans-serif; line-height: 1.6; color: #333; max-width: 800px; margin: 0 auto; padding: 20px; }
    h1 { color: #1a252c; text-align: center; }
    h2 { color: #0d6efd; border-bottom: 2px solid #e9ecef; padding-bottom: 8px; margin-top: 30px; }
    h3 { color: #495057; }
    .disclaimer { background: #fff3cd; color: #856404; padding: 15px; border-left: 5px solid #ffeeba; border-radius: 4px; font-size: 0.9em; margin-bottom: 25px; }
    .formula { background: #e9ecef; padding: 10px 15px; border-radius: 6px; font-weight: bold; font-family: monospace; }
    ul { margin-bottom: 20px; }
    .citacion { font-style: italic; color: #555; }
    /* Estilos del Simulador */
    .simulador-box { max-width: 500px; margin: 30px auto; padding: 25px; border-radius: 12px; background-color: #f8f9fa; border: 1px solid #e9ecef; box-shadow: 0 4px 10px rgba(0,0,0,0.08); }
    .form-group { margin-bottom: 15px; }
    .form-group label { display: block; font-weight: bold; margin-bottom: 5px; color: #495057; }
    .form-group input, .form-group select { width: 100%; padding: 10px; border-radius: 6px; border: 1px solid #ced4da; box-sizing: border-box; font-size: 14px; }
    .btn-calcular { width: 100%; padding: 12px; background-color: #0d6efd; color: white; border: none; border-radius: 6px; font-weight: bold; font-size: 15px; cursor: pointer; }
    .btn-calcular:hover { background-color: #0b5ed7; }
    .resultado-box { margin-top: 20px; padding: 16px; border-radius: 8px; background-color: #ffffff; border: 1px solid #dee2e6; display: none; }
    /* Estilos de Referencias */
    .referencias { background-color: #f8f9fa; padding: 20px; border-radius: 8px; border: 1px solid #e9ecef; font-size: 0.95em; }
    .referencias p { text-indent: -2em; padding-left: 2em; margin-bottom: 12px; }
  </style>
</head>
<body>

  <h1>Más allá del Interés: Cómo el Valor del Dinero en el Tiempo Gobierna tus Finanzas</h1>

  <div class="disclaimer">
    <strong>Aviso Legal y Exención de Responsabilidad:</strong> El contenido publicado en este artículo y las proyecciones del simulador interactivo tienen fines estrictamente informativos y educativos. No constituyen asesoramiento financiero, legal o de inversión formal.
  </div>

  <h2>1. El Valor del Dinero en el Tiempo (VDT)</h2>
  <p>El valor del dinero cambia de forma continua debido a factores como la inflación, el riesgo financiero y el costo de oportunidad. Un monto disponible hoy tiene mayor capacidad adquisitiva que esa misma cantidad recibida en el futuro, pues el capital actual puede invertirse para generar rendimientos (Gitman & Zutter, 2012).</p>

  <h2>2. Las Tasas de Interés</h2>
  <p>El interés representa el costo del capital o la rentabilidad obtenida por ceder recursos financieros en un periodo determinado.</p>
  <ul>
    <li><strong>Interés simple:</strong> Rendimiento calculado exclusivamente sobre el capital inicial (UNAM, 2020).</li>
    <li><strong>Interés compuesto:</strong> Proceso de capitalización en el que los intereses devengados se integran al capital principal para generar nuevos intereses en cada periodo (Redalyc, 2018).</li>
  </ul>

  <h2>3. Fórmulas de Valor Futuro y Valor Presente</h2>
  
  <h3>Valor Futuro (VF)</h3>
  <p>Monto que alcanzará un capital inicial al final de un horizonte temporal tras aplicar una tasa de interés determinada.</p>
  <p class="formula">VF = VP × (1 + i)^n</p>

  <h3>Valor Presente (VP)</h3>
  <p>Equivalente actual de un capital que se recibirá o pagará en una fecha futura a una tasa de descuento específica.</p>
  <p class="formula">VP = VF / (1 + i)^n</p>

  <h2>4. Simulador Interactivo Financiero</h2>

  <div class="simulador-box">
    <h3 style="margin-top:0; text-align: center;">Simulador Interactivo Financiero</h3>
    
    <div class="form-group">
      <label>¿Qué deseas calcular?</label>
      <select id="tipoCalculo" onchange="cambiarModo()">
        <option value="VF">Valor Futuro (VF) a partir de un Capital Inicial</option>
        <option value="VP">Valor Presente (VP) necesario para una Meta Futura</option>
      </select>
    </div>

    <div class="form-group">
      <label id="lblMonto">Valor Presente (VP / Capital Inicial):</label>
      <input type="number" id="monto" value="1000000">
    </div>

    <div class="form-group">
      <label>Tasa de Interés Anual (%):</label>
      <input type="number" id="tasa" value="10" step="0.1">
    </div>

    <div class="form-group">
      <label>Plazo (Años):</label>
      <input type="number" id="anios" value="5">
    </div>

    <button class="btn-calcular" onclick="calcularSimulacion()">Calcular Ahora</button>

    <div id="resultado" class="resultado-box">
      <p style="margin: 0 0 8px 0; font-size: 13px; color: #6c757d; text-transform: uppercase;">Resultado estimado:</p>
      <p style="margin: 0; font-size: 18px; font-weight: bold; color: #198754;"><span id="lblResultadoTitulo">Valor Futuro (VF):</span> <span id="valCalculado">$0</span></p>
      <p style="margin: 6px 0 0 0; font-size: 14px; color: #0d6efd;"><span id="lblDetalleTitulo">Intereses Generados:</span> <span id="valDiferencia">$0</span></p>
    </div>
  </div>

  <h2>5. Referencias Académicas (Normas APA 7)</h2>
  <div class="referencias">
    <p>Gitman, L. J., & Zutter, C. J. (2012). <em>Principios de administración financiera</em> (12.ª ed.). Pearson Educación.</p>
    <p>Redalyc. (2018). <em>Análisis de las tasas de interés y su impacto en las matemáticas financieras</em>. Red de Revistas Científicas de América Latina y el Caribe, España y Portugal.</p>
    <p>Universidad Nacional Autónoma de México [UNAM]. (2020). <em>Fundamentos de matemáticas financieras e interés compuesto</em>. Facultad de Contaduría y Administración.</p>
  </div>

  <script>
    function cambiarModo() {
      const modo = document.getElementById('tipoCalculo').value;
      const lblMonto = document.getElementById('lblMonto');
      if (modo === 'VF') {
        lblMonto.innerText = 'Valor Presente (VP / Capital Inicial):';
      } else {
        lblMonto.innerText = 'Valor Futuro deseado (VF / Meta Futura):';
      }
      document.getElementById('resultado').style.display = 'none';
    }

    function calcularSimulacion() {
      const modo = document.getElementById('tipoCalculo').value;
      const monto = parseFloat(document.getElementById('monto').value);
      const tasa = parseFloat(document.getElementById('tasa').value) / 100;
      const anios = parseFloat(document.getElementById('anios').value);

      if (isNaN(monto) || isNaN(tasa) || isNaN(anios) || monto <= 0 || anios <= 0) {
        alert("Por favor ingresa valores válidos.");
        return;
      }

      let resultadoFinal = 0;
      let diferencia = 0;

      if (modo === 'VF') {
        resultadoFinal = monto * Math.pow((1 + tasa), anios);
        diferencia = resultadoFinal - monto;
        document.getElementById('lblResultadoTitulo').innerText = 'Valor Futuro (VF):';
        document.getElementById('lblDetalleTitulo').innerText = 'Intereses Ganados:';
      } else {
        resultadoFinal = monto / Math.pow((1 + tasa), anios);
        diferencia = monto - resultadoFinal;
        document.getElementById('lblResultadoTitulo').innerText = 'Valor Presente requerido (VP):';
        document.getElementById('lblDetalleTitulo').innerText = 'Descuento / Rendimiento total:';
      }

      document.getElementById('valCalculado').innerText = "$" + resultadoFinal.toLocaleString('es-CO', { minimumFractionDigits: 2, maximumFractionDigits: 2 });
      document.getElementById('valDiferencia').innerText = "$" + diferencia.toLocaleString('es-CO', { minimumFractionDigits: 2, maximumFractionDigits: 2 });
      document.getElementById('resultado').style.display = 'block';
    }
  </script>

</body>
</html>
