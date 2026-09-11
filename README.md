# Finanzasconmate

Aviso Legal: El contenido publicado en este artículo y los resultados arrojados por el simulador interactivo son exclusivamente de carácter informativo, divulgativo y educativo. No constituyen asesoría financiera, legal, tributaria o de inversión profesional. El uso de las herramientas expuestas se realiza bajo la exclusiva responsabilidad del usuario.

Un rincón creado para dominar las matemáticas financieras sin dolor de cabeza. Analizamos cómo cambia el valor del dinero con el tiempo a través de explicaciones sencillas sobre interés, capitalización y flujos de efectivo. Incluye una calculadora interactiva para simular inversiones reales en segundos.

# Tasas de Interés, Valor Presente y Valor Futuro en Operaciones Financieras
Las finanzas personales y corporativas se estructuran sobre un principio básico: el dinero no conserva el mismo valor a lo largo del tiempo. Comprender las variables de tasa de interés, valor presente ($VP$) y valor futuro ($VF$) permite analizar desde un préstamo bancario hasta proyecciones de inversión a largo plazo.

# El Valor del Dinero en el Tiempo (VDT)

El valor del dinero cambia de forma continua debido a factores como la inflación, el riesgo financiero y el costo de oportunidad. Un monto de dinero disponible hoy posee mayor capacidad adquisitiva que esa misma cantidad recibida en el futuro, ya que el capital actual puede invertirse para generar rendimientos.

# Fórmulas y Definiciones de Valor Presente y Valor FuturoValor Futuro ($VF$)

Es la suma que alcanzará un capital inicial al término de un tiempo determinado tras aplicarle una tasa de interés.
$$\Large VF = VP \times (1 + i)^n$$$VF$: Valor Futuro.$VP$: Valor Presente (Capital inicial).$i$: 
Tasa de interés expresada en formato decimal por periodo.$n$: Número de periodos de capitalización.

# Valor Presente ($VP$)
Es el valor actual de un monto que se recibirá o pagará en una fecha futura, aplicando una tasa de descuento.$$\Large VP = \frac{VF}{(1 + i)^n}$$



# El Valor del Dinero en el Tiempo (VDT)

El valor del dinero cambia de forma continua debido a factores como la inflación, el riesgo financiero y el costo de oportunidad. Un monto de dinero disponible hoy posee mayor capacidad adquisitiva que esa misma cantidad recibida en el futuro, ya que el capital actual puede invertirse para generar rendimientos.


<!-- Mini Simulador Interactivo Financiero (VDT) -->
<div style="max-width: 500px; margin: 30px auto; padding: 25px; border-radius: 12px; background-color: #f8f9fa; border: 1px solid #e9ecef; font-family: Arial, sans-serif; box-shadow: 0 4px 10px rgba(0,0,0,0.08);">
  <h3 style="margin-top:0; color: #1a252c; text-align: center; font-size: 20px;">Simulador Interactivo Financiero</h3>
  
  <div style="margin-bottom: 15px;">
    <label style="display: block; font-weight: bold; margin-bottom: 5px; color: #495057;">¿Qué deseas calcular?</label>
    <select id="tipoCalculo" onchange="cambiarModo()" style="width: 100%; padding: 10px; border-radius: 6px; border: 1px solid #ced4da; font-size: 14px; background-color: #fff;">
      <option value="VF">Valor Futuro (VF) a partir de un Capital Inicial</option>
      <option value="VP">Valor Presente (VP) necesario para una Meta Futura</option>
    </select>
  </div>

  <div style="margin-bottom: 15px;">
    <label id="lblMonto" style="display: block; font-weight: bold; margin-bottom: 5px; color: #495057;">Valor Presente (VP / Capital Inicial):</label>
    <input type="number" id="monto" value="1000000" placeholder="Ej. 1000000" style="width: 100%; padding: 9px; border-radius: 6px; border: 1px solid #ced4da; box-sizing: border-box; font-size: 14px;">
  </div>

  <div style="margin-bottom: 15px;">
    <label style="display: block; font-weight: bold; margin-bottom: 5px; color: #495057;">Tasa de Interés Anual (%):</label>
    <input type="number" id="tasa" value="10" step="0.1" placeholder="Ej. 10" style="width: 100%; padding: 9px; border-radius: 6px; border: 1px solid #ced4da; box-sizing: border-box; font-size: 14px;">
  </div>

  <div style="margin-bottom: 20px;">
    <label style="display: block; font-weight: bold; margin-bottom: 5px; color: #495057;">Plazo (Años):</label>
    <input type="number" id="anios" value="5" placeholder="Ej. 5" style="width: 100%; padding: 9px; border-radius: 6px; border: 1px solid #ced4da; box-sizing: border-box; font-size: 14px;">
  </div>

  <button onclick="calcularSimulacion()" style="width: 100%; padding: 12px; background-color: #0d6efd; color: white; border: none; border-radius: 6px; font-weight: bold; font-size: 15px; cursor: pointer;">Calcular Ahora</button>

  <div id="resultado" style="margin-top: 20px; padding: 16px; border-radius: 8px; background-color: #ffffff; border: 1px solid #dee2e6; display: none;">
    <p style="margin: 0 0 8px 0; font-size: 13px; color: #6c757d; text-transform: uppercase;">Resultado estimado:</p>
    <p style="margin: 0; font-size: 18px; font-weight: bold; color: #198754;"><span id="lblResultadoTitulo">Valor Futuro (VF):</span> <span id="valCalculado">$0</span></p>
    <p style="margin: 6px 0 0 0; font-size: 14px; color: #0d6efd;"><span id="lblDetalleTitulo">Intereses Generados:</span> <span id="valDiferencia">$0</span></p>
  </div>
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
    alert("Por favor ingresa valores válidos y mayores a cero.");
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


# Note
Para sustento académico y protección de derechos de autor 
Gitman, L. J., & Zutter, C. J. (2016). Principios de administración financiera (14.ª ed.). Pearson Educación.

Red de Revistas Científicas de América Latina y el Caribe, España y Portugal [Redalyc]. (2018). La tasa de interés: Información con estructura y equivalencia de tasas. Redalyc. https://www.redalyc.org

Universidad Nacional Autónoma de México [UNAM]. (2020). Apuntes de matemáticas financieras. Facultad de Contaduría y Administración, Sistema Universidad Abierta y Educación a Distancia (SUAYED). http://www.fca.unam.mx
