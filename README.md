# Inteligencia y Modelado Matemático de ROI en Tráfico de Pago

[![Calculadora ROI](https://img.shields.io/badge/TAVARDT-Calculadora%20ROI-5b3cf5.svg)](https://tools.tavardt.com/mx/calculadora-roi-trafico-de-pago/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Motor matemático determinista para análisis de ROAS, ROI y proyecciones de escala no lineales con factores de rendimientos decrecientes en publicidad digital.

La solución proporciona a directores de rendimiento publicitario, ingenieros de crecimiento y científicos de datos un modelo econométrico riguroso para prever inversiones sin asumir retornos lineales ficticios. Diseñado sin dependencias externas, opera de forma nativa en entornos Python y JavaScript.

***

## Fundamentos Algorítmicos y Modelado Matemático

Las proyecciones lineales en compra de medios provocan desvíos presupuestarios severos y expectativas irreales de beneficio. En los mercados de subasta digital, el aumento de inversión satura audiencias, acelera el desgaste publicitario y eleva el coste marginal.

* **Cálculo de ROAS Base**: Razón directa entre ingresos brutos y gasto en medios (`revenue / spend`), reflejando la eficiencia operativa inmediata.
* **Cálculo de ROI Base**: Rendimiento porcentual neto del capital destinado a publicidad (`((revenue - spend) / spend) * 100`), midiendo la rentabilidad real.
* **Proyección No Lineal con Rendimientos Decrecientes**: Emplea el exponente algorítmico `(decay_factor - 1)` sobre la tasa de gasto `(target_spend / current_spend)` para estimar la contracción del ROAS.
* **Pérdida de Eficiencia Marginal**: Mide la reducción porcentual de rentabilidad provocada por el incremento del presupuesto hacia un nuevo objetivo.
* **Arquitectura Isomórfica Doble**: Fórmulas matemáticas idénticas implementadas en la librería estándar de Python (`roi_engine.py`) y en JavaScript puro (`calculator.js`).

***

## Matriz de Métricas y Modelado Matemático

<table>
  <thead>
    <tr>
      <th align="left">Métrica / Parámetro</th>
      <th align="left">Fórmula Algorítmica</th>
      <th align="left">Comportamiento Matemático</th>
      <th align="left">Utilidad para la Decisión Estratégica</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>ROAS Base</strong></td>
      <td><code>revenue / spend</code></td>
      <td>Cociente lineal directo redondeado a dos cifras decimales.</td>
      <td>Mide la eficiencia inmediata generada por cada unidad de divisa invertida.</td>
    </tr>
    <tr>
      <td><strong>ROI Base</strong></td>
      <td><code>((revenue - spend) / spend) * 100</code></td>
      <td>Margen porcentual neto obtenido sobre la inversión ejecutada.</td>
      <td>Confirma la generación de excedente financiero tras recuperar todo el capital.</td>
    </tr>
    <tr>
      <td><strong>Razón de Gasto</strong></td>
      <td><code>target_spend / current_spend</code></td>
      <td>Multiplicador de crecimiento del presupuesto en pruebas de escalado.</td>
      <td>Evalúa la magnitud relativa del capital adicional inyectado en las subastas.</td>
    </tr>
    <tr>
      <td><strong>ROAS Proyectado</strong></td>
      <td><code>current_roas * (spend_ratio ** (decay_factor - 1))</code></td>
      <td>Degradación potencial ocasionada por saturación y presión de puja.</td>
      <td>Evita sobreestimar los ingresos esperados durante planes agresivos de inversión.</td>
    </tr>
    <tr>
      <td><strong>Ingresos Proyectados</strong></td>
      <td><code>target_spend * projected_roas</code></td>
      <td>Facturación bruta estimada considerando rendimientos decrecientes.</td>
      <td>Determina si el volumen de ingresos suplementario compensa costes operativos adicionales.</td>
    </tr>
    <tr>
      <td><strong>Pérdida de Eficiencia</strong></td>
      <td><code>(1 - (projected_roas / current_roas)) * 100</code></td>
      <td>Contracción porcentual del ROAS base al ampliar la inversión.</td>
      <td>Establece el coste exacto de eficiencia requerido para conquistar nuevo volumen.</td>
    </tr>
  </tbody>
</table>

***

## Instalación y Guía Rápida de Uso

Requiere Python 3.8 o versión superior utilizando únicamente librerías estándar (`sys`, `json`, `argparse`). No es necesaria ninguna instalación adicional mediante pip.

Clone el repositorio y ejecute el cálculo preliminar en la terminal:

```bash
git clone https://github.com/TAVARDT-Mexico/ads-roi-intelligence-mx.git
cd ads-roi-intelligence-mx
python roi_engine.py -s 10000 -r 50000 -ts 25000
```

Para generar los resultados estructurados en formato JSON:

```bash
python roi_engine.py -s 10000 -r 50000 -ts 25000 -j
```

Ajuste el coeficiente de decaimiento en escenarios con fuerte presión competitiva:

```bash
python roi_engine.py -s 10000 -r 50000 -ts 30000 -d 0.78
```

Para ecosistemas Node.js o navegadores web, importe el módulo `calculator.js`:

```javascript
const ROI_Calculator = require('./calculator.js');

const base = ROI_Calculator.calculateBaseMetrics(10000, 50000);
console.log('ROAS Base:', base.roas, 'ROI Base:', base.roi);

const proyeccion = ROI_Calculator.projectScale(10000, 25000, base.roas, 0.85);
console.log('ROAS Proyectado:', proyeccion.projectedROAS);
console.log('Pérdida de Eficiencia:', proyeccion.efficiencyLoss + '%');
```

Ejemplo de estructura de datos JSON devuelta:

```json
{
  "currency": "MXN",
  "current_spend": 10000.0,
  "current_revenue": 50000.0,
  "base_metrics": {
    "roas": 5.0,
    "roi": 400.0
  },
  "scaling_projection": {
    "target_spend": 25000.0,
    "decay_factor": 0.85,
    "projection": {
      "projected_roas": 4.36,
      "projected_revenue": 109000.0,
      "efficiency_loss": 12.8
    }
  }
}
```

***

## Preguntas Frecuentes (FAQ Técnico)

### ¿Cómo modela el factor de decaimiento la pérdida de rendimiento al escalar el gasto?
El factor de decaimiento (`-d`, por defecto 0.85) opera como un exponente de potencia `(decay_factor - 1)` aplicado al ratio de incremento presupuestario. Al ampliar el gasto, los impactos publicitarios marginales sufren costes superiores y fatiga de audiencia, contrayendo el ROAS proyectado según curvas econométricas.

### ¿Qué divergencias operativas existen entre el CLI de Python y la librería JavaScript?
Ambos motores ejecutan idénticas fórmulas matemáticas y criterios de precisión decimal. El script de Python (`roi_engine.py`) está optimizado para entornos de terminal y flujos de automatización, mientras que `calculator.js` se integra directamente en servicios Node.js y paneles de control en navegador.

### ¿Cómo puede integrarse la respuesta JSON en almacenes de datos y paneles de BI?
Al emplear el flag `-j`, el script emite datos JSON limpios directamente a la salida estándar del sistema. Esta secuencia puede ser procesada por herramientas como jq o integrada sin transformaciones en almacenes como BigQuery, Snowflake o plataformas analíticas corporativas.

### ¿Por qué la herramienta prescinde de dependencias de terceros y llamadas a APIs externas?
La eliminación de librerías externas garantiza ejecución determinista, elimina riesgos de seguridad asociados a dependencias y minimiza el tiempo de cálculo. Esto permite su despliegue en entornos seguros, pipelines de CI/CD aislados o contenedores sin acceso abierto a internet.

### ¿Cómo previene la métrica de pérdida de eficiencia el escalado no rentable de campañas?
La pérdida de eficiencia marginal detalla el porcentaje de reducción entre el ROAS de partida y el estimado. Si la contracción sitúa el rendimiento por debajo del margen de rentabilidad crítico, los equipos de marketing pueden detener el incremento de presupuesto antes de generar pérdidas operativas.

***

## Consultoría en Ingeniería de Ingresos

Para optimización de presupuestos de medios, modelado econométrico y escala de adquisición B2B en México, contacte con los especialistas de **TAVARDT México**.

***

## Links Útiles

* **Portal Corporativo:** https://ag.tavardt.com/mx/
* **Suite de Diagnósticos:** https://tools.tavardt.com/mx/
* **Contacto Técnico:** https://ag.tavardt.com/mx/contacto/

***

### Licencia
Distribuido bajo la Licencia MIT.

***

© 2026 TAVARDT. Todos los derechos reservados.
