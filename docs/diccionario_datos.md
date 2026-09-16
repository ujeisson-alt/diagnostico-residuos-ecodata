# Diccionario de datos — `TablaResiduosLimpios`

| Columna | Tipo | Descripción | Origen |
|---|---|---|---|
| `ID_Registro` | Texto | Identificador único de la medición (`REG-####`) | RAW |
| `Fecha_Medicion` | Fecha `DD/MM/AAAA` | Fecha en que se registró la medición | RAW (convertido) |
| `Anio` | Entero | `=AÑO(Fecha_Medicion)` | Calculado |
| `Mes` | Fecha (1.er día del mes) | `=FECHA(AÑO();MES();1)` — eje de la tendencia mensual | Calculado |
| `Provincia` | Texto normalizado | 8 provincias: Buenos Aires, Córdoba, Santa Fe, Mendoza, Salta, Tucumán, Chaco, Misiones | RAW (limpio) |
| `Region` | Texto | Centro, Cuyo, NOA, NEA — `=BUSCARV()` sobre `catalogo_provincias` | Calculado |
| `Tipo_Residuo` | Texto categórico | Plásticos, Orgánico, Vidrio, Papel y Cartón, Peligrosos, Metales | RAW |
| `Toneladas` | Decimal (2 decimales) | Volumen medido en toneladas | RAW (convertido) |
| `Categoria_Volumen` | Texto | Bajo (< 1.000 t), Medio (1.000–5.000 t), Alto (> 5.000 t) | Calculado |

## Glosario
- **Outlier (valor atípico):** registro por encima de media + 3 desviaciones estándar (7.461,94 t).
- **Z-score provincial:** cuántas desviaciones estándar se aleja el total de una provincia del promedio de las 8 provincias. ≥ 1 = crítica.
- **Coeficiente de variación:** desviación estándar / media. Mide dispersión relativa.
- **Segmentador (slicer):** botón visual de Excel para filtrar tablas y gráficos dinámicos con un clic.
