# Inteligencia y Modelado de ROI en Publicidad Digital | TAVARDT México

[![Calculadora ROI](https://img.shields.io/badge/TAVARDT-Calculadora%20ROI-5b3cf5.svg)](https://tools.tavardt.com/mx/calculadora-roi-trafico-de-pago/)
[![Jurisdiccion](https://img.shields.io/badge/Jurisdiccion-Mexico-00C853.svg)](https://ag.tavardt.com/mx/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)

Modelado matemático para análisis de ROAS, ROI y proyecciones de escala con rendimientos decrecientes para inversión digital corporativa.

Desarrollado y mantenido por la division de ingenieria de ingresos y medios de pago de **[TAVARDT Mexico](https://ag.tavardt.com/mx/)**.

---

## Modelado Matematico y Metricas

* **ROAS Base**: Razon directa entre facturacion generada e inversion publicitaria.
* **ROI Base**: Rendimiento porcentual neto sobre el capital invertido en medios.
* **Proyeccion de Escala con Rendimientos Decrecientes**: Coeficiente de decaimiento marginal (estandar 0.85) que modela la reduccion de eficiencia al ampliar presupuestos.
* **Formatos de Salida**: Informe de texto en consola o estructura de datos JSON para pipelines de analitica.

---

## Instalacion y Ejecucion

Requiere unicamente Python 3.8 o superior, sin paquetes externos.

```bash
git clone https://github.com/TAVARDT-Mexico/ads-roi-intelligence-mx.git
cd ads-roi-intelligence-mx
python roi_engine.py --spend 10000 --revenue 50000 --target-spend 25000
```

Para exportar en formato estructurado JSON:

```bash
python roi_engine.py --spend 10000 --revenue 50000 --target-spend 25000 --json
```

---

## Calculadora Interactiva en la Web

Para simulaciones graficas y proyecciones de presupuestos empresariales, acceda a la suite oficial:

* **[Calculadora de ROI de Trafico de Pago](https://tools.tavardt.com/mx/calculadora-roi-trafico-de-pago/)**
* **[Portal Corporativo TAVARDT Mexico](https://ag.tavardt.com/mx/)**

---

## Consultoria en Ingenieria de Crecimiento

Para auditoria de inversion publicitaria corporativa y modelado econometrico en Mexico, consulte al equipo tecnico de **[TAVARDT Mexico](https://ag.tavardt.com/mx/contacto/)**.
