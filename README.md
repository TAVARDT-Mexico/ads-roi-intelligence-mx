# Inteligencia y Modelado de ROI en Publicidad Digital

[![Calculadora ROI](https://img.shields.io/badge/TAVARDT-Calculadora%20ROI-5b3cf5.svg)](https://tools.tavardt.com/mx/calculadora-roi-trafico-de-pago/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Modelado matemático para análisis de ROAS, ROI y proyecciones de escala con rendimientos decrecientes para inversión digital corporativa.

***

## Modelado Matematico y Metricas

* **ROAS Base**: Razon directa entre facturacion generada e inversion publicitaria.
* **ROI Base**: Rendimiento porcentual neto sobre el capital invertido en medios.
* **Proyeccion de Escala con Rendimientos Decrecientes**: Coeficiente de decaimiento marginal (estandar 0.85) que modela la reduccion de eficiencia al ampliar presupuestos.
* **Formatos de Salida**: Informe de texto en consola o estructura de datos JSON para pipelines de analitica.

***

## Instalacion y Ejecucion

Requiere unicamente Python 3.8 o superior, sin paquetes externos.

```bash
git clone https://github.com/TAVARDT/ads-roi-intelligence-mx.git
cd ads-roi-intelligence-mx
python roi_engine.py -spend 10000 -revenue 50000 -target-spend 25000
```

Para exportar en formato estructurado JSON:

```bash
python roi_engine.py -spend 10000 -revenue 50000 -target-spend 25000 -json
```

***

## Consultoria en Ingenieria de Crecimiento

Para auditoria de inversion publicitaria corporativa y modelado econometrico en Mexico, consulte al equipo tecnico de **TAVARDT**.

***

## Enlaces Útiles

* **Portal Corporativo:** https://ag.tavardt.com/mx/
* **Suite de Diagnósticos:** https://tools.tavardt.com/mx/
* **Contacto Técnico:** https://ag.tavardt.com/mx/contacto/

***

### Licencia
Distribuido bajo la Licencia MIT.

***

© 2026 TAVARDT. Todos los derechos reservados.
