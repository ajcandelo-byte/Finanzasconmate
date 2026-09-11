# Finanzasconmate

Un rincón creado para dominar las matemáticas financieras sin dolor de cabeza. Analizamos cómo cambia el valor del dinero con el tiempo a través de explicaciones sencillas sobre interés, capitalización y flujos de efectivo. Incluye una calculadora interactiva para simular inversiones reales en segundos.

---

## 1. El Valor del Dinero en el Tiempo (VDT)

El valor del dinero cambia de forma continua debido a factores como la inflación, el riesgo financiero y el costo de oportunidad. Un monto de dinero disponible hoy posee mayor capacidad adquisitiva que esa misma cantidad recibida en el futuro, ya que el capital actual puede invertirse para generar rendimientos.

---

## 2. Fórmulas y Definiciones

### Valor Futuro ($VF$)

Es la suma que alcanzará un capital inicial al término de un tiempo determinado tras aplicarle una tasa de interés.

$$VF = VP \times (1 + i)^n$$

* **VF:** Valor Futuro.
* **VP:** Valor Presente (Capital inicial).
* **i:** Tasa de interés expresada en formato decimal por periodo.
* **n:** Número de periodos de capitalización.

### Valor Presente ($VP$)

Es el valor actual de un monto que se recibirá o pagará en una fecha futura, aplicando una tasa de descuento.

$$VP = \frac{VF}{(1 + i)^n}$$

---

## 3. Simulador Interactivo Financiero

```html
<!-- Mini Simulador Interactivo Financiero (VDT) -->
<div style="max-width: 500px; margin: 30px auto; padding: 25px; border-radius: 12px; background-color: #f8f9fa; border: 1px solid #e9ecef; font-family: Arial, sans-serif;">
  <h3 style="margin-top:0; color: #1a252c; text-align: center;">Simulador Interactivo Financiero</h3>
  
  <div style="margin-bottom: 15px;">
    <label style="display: block; font-weight: bold; margin-bottom: 5px;">¿Qué deseas calcular?</label>
    <select id="tipoCalculo" onchange="cambiarModo()" style="width: 100%; padding: 10px; border-radius: 6px; border: 1px solid #ced4da;">
      <option value="VF">Valor Futuro (VF) a partir de un Capital Inicial</option>
      <option value="VP">Valor Presente (VP) necesario para una Meta Futura</option>
    </select>
  </div>

  <div style="margin-bottom: 15px;">
    <label id="lblMonto" style="display: block; font-weight: bold; margin-bottom: 5px;">Valor Presente (VP / Capital Inicial):</label>
    <input type="number" id="monto" value="1000000" style="width: 100%; padding: 9px; border-radius: 6px; border: 1px solid #ced4da; box-sizing: border-box;">
  </div>

  <div style="margin-bottom: 15px;">
    <label style="display: block; font-weight: bold; margin-bottom: 5px;">Tasa de Interés Anual (%):</label>
    <input type="number" id="tasa" value="10" step="0.1" style="width: 100%; padding: 9px; border-radius: 6px; border: 1px solid #ced4da; box-sizing: border-box;">
  </div>

  <div style="margin-bottom: 20px;">
    <label style="display: block; font-weight: bold; margin-bottom: 5px;">Plazo (Años):</label>
    <input type="number" id="anios" value="5" style="width: 100%; padding: 9px; border-radius: 6px; border: 1px solid #ced4da; box-sizing: border-box;">
  </div>

  <button onclick="calcularSimulacion()" style="width: 100%; padding: 12px; background-color: #0d6efd; color: white; border: none; border-radius: 6px; font-weight: bold; cursor: pointer;">Calcular Ahora</button>

  <div id="resultado" style="margin-top: 20px; padding: 16px; border-radius: 8px; background-color: #ffffff; border: 1px solid #dee2e6; display: none;">
    <p style="margin: 0 0 8px 0; font-size: 13px; color: #6c757d;">Resultado estimado:</p>
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
