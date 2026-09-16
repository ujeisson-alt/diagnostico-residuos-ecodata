# Guía: versión con Tablas Dinámicas + Segmentadores (Slicers)

El libro `notebooks_reports/diagnostico_residuos_ecodata.xlsx` usa **filtros con listas desplegables + `SUMAR.SI.CONJUNTO`**, lo que funciona igual en Excel, LibreOffice y Google Sheets.
Si deseas la versión nativa con **Gráficos Dinámicos y Segmentadores** (Excel de escritorio), sigue estos pasos (≈15 min):

1. Abre el libro y selecciona cualquier celda de la tabla `TablaResiduosLimpios` (hoja `datos_procesados`).
2. **Insertar › Tabla dinámica** › *Hoja de cálculo existente* › hoja `tablas_dinamicas`, celda `N12`.
   - Filas: `Provincia` · Valores: `Suma de Toneladas` · Ordena de mayor a menor › *Filtro de valores › Diez mejores › 5*.
3. Repite para la **evolución temporal** en `N30` (Filas: `Mes` o `Anio`) y la **distribución por tipo** en `N50` (Filas: `Tipo_Residuo`).
   Deja al menos 5 columnas o 10 filas de separación para evitar el error *«no se pueden superponer tablas dinámicas»*.
4. Sobre cada tabla dinámica: **Analizar › Gráfico dinámico** (barras horizontales para el Top 5, líneas para la tendencia, columnas para tipo). Córtalos y pégalos en la hoja `dashboard`.
5. Selecciona un gráfico › **Análisis de gráfico dinámico › Insertar Segmentación de datos** › marca `Anio`, `Region` y `Tipo_Residuo`.
6. **Clic derecho en cada segmentador › Conexiones de informe** › marca **todas** las tablas dinámicas.
7. Vista › desmarca *Líneas de cuadrícula*. Aplica la paleta verde/gris (`#1B4332`, `#2D6A4F`, `#52B788`, `#5F6B66`).

✓ Criterio de completitud: al hacer clic en un año del segmentador, todos los gráficos se actualizan a la vez.
