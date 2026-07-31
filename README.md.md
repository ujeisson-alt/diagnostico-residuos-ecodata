# Diagnóstico de Generación de Residuos Urbanos  EcoData

Análisis exploratorio y diagnóstico de la generación de residuos sólidos urbanos en 8 provincias, a partir de un dataset de 1.095 registros brutos (2024–2026). El proyecto cubre el ciclo completo de un análisis de datos: auditoría y limpieza, análisis estadístico, segmentación, tablas resumen tipo pivote, dashboard interactivo y reporte ejecutivo para una audiencia no técnica.

## Problema que resuelve

La organización no contaba con una fuente confiable para entender cómo, dónde y en qué categoría se concentra la generación de residuos. Este proyecto transforma datos crudos con errores de formato, duplicados y valores faltantes en un panel de control confiable, capaz de responder: ¿qué provincias generan más residuos?, ¿qué tipo de residuo predomina?, ¿la generación está creciendo?, ¿dónde se concentran los picos de volumen?

## Principales hallazgos

- Volumen total analizado: **2.505.016 toneladas** (1.040 registros válidos).
- Los **plásticos** son la categoría de mayor generación (33,1% del total), seguidos de orgánicos (25,2%) y vidrio (17,0%).
- **Buenos Aires, Tucumán y Córdoba** concentran la mayor generación acumulada.
- La generación de plásticos creció **3,46%** entre 2024 y 2025 (años completos comparables).
- El 7,6% de los registros clasificados como "Alto Volumen" concentra el **20,3%** de las toneladas totales — evidencia de eventos de generación atípicos que requieren atención prioritaria.

Detalle completo en [`docs/reporte_ejecutivo.pdf`](docs/reporte_ejecutivo.pdf).

## Herramientas utilizadas

- **Microsoft Excel** — limpieza de datos, funciones de texto y lógica condicional (`SI`, `BUSCARV`/`INDICE-COINCIDIR`), tablas dinámicas, dashboard interactivo con segmentadores.
- **Funciones estadísticas** — `PROMEDIO`, `MEDIANA`, `DESVEST`, `MODA`.
- **Redacción técnica** — reporte ejecutivo con storytelling de datos para una audiencia de dirección y legisladores.

## Estructura del repositorio

```
diagnostico-residuos-ecodata/
├── data/
│   ├── raw/            # Datos originales sin modificar
│   └── processed/      # Datos limpios + Dashboard + cálculos (Excel)
├── docs/                # Reporte ejecutivo (PDF) y auditoría de datos
├── notebooks_reports/  # Borradores de trabajo
└── README.md
```

## Cómo revisar este proyecto

1. `data/raw/residuos_urbanos_raw.xlsx` — dataset original, tal como fue recibido.
2. `data/processed/datos_residuos_procesados.xlsx` — archivo final con 5 pestañas:
   - `Dashboard`: panel ejecutivo con KPIs y gráficos.
   - `Cálculos_Estadísticos`: media, mediana, moda, desviación estándar.
   - `Tablas_Dinamicas`: tablas resumen por provincia, año y tipo de residuo.
   - `Datos_Limpios`: tabla estructurada (`TablaResiduosLimpios`) ya normalizada.
   - `Registros_Incompletos`: registros aislados por falta de dato clave (no se descartaron ni se imputaron).
3. `docs/reporte_ejecutivo.pdf` — hallazgos y recomendaciones en lenguaje ejecutivo.
4. `docs/reporte_auditoria_sesion1.txt` — bitácora de la auditoría inicial de calidad de datos.

## Autor

Jeisson Uribe — Analista de Datos Jr.
