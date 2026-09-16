# Informe de auditoría y limpieza de datos (Semana 1)

**Archivo fuente:** `data/raw/residuos_urbanos_raw.csv` (no se modifica)
**Archivo resultante:** `data/processed/datos_residuos_procesados.xlsx` → tabla `TablaResiduosLimpios`

## Recuento de filas

| Concepto | Filas | % sobre RAW |
|---|---:|---:|
| Filas iniciales (RAW) | 1.095 | 100,0 % |
| Duplicados exactos (misma fila repetida) | 45 | 4,1 % |
| Registros sin dato de `Toneladas` (no duplicados) | 10 | 0,9 % |
| **Total aislado** (hoja `anomalias`) | **55** | **5,0 %** |
| **Filas válidas para el análisis** | **1.040** | **95,0 %** |

> Hubo 11 filas con `Toneladas` vacío en total; una de ellas además estaba duplicada y se contó como duplicado.

## Decisiones tomadas (criterio del analista)

1. **Duplicados:** se conserva la primera aparición y se aíslan las siguientes. Se verificó que no existen IDs repetidos con datos distintos.
2. **Toneladas vacías:** no se imputan con la media para no sesgar el análisis (criterio MVP). Se aíslan en la hoja `anomalias`.
3. **Provincias:** 86 valores (7,9 %) tenían errores de escritura, mayúsculas o espacios. Se normalizaron con `=ESPACIOS()` + Buscar y Reemplazar:

| Variantes en RAW | Valor normalizado |
|---|---|
| `Bs As`, `Bs. As.`, `buenos aires`, `BUENOS AIRES ` | Buenos Aires |
| `cordoba`, `CORDOBA`, `Córdoba ` (espacio final) | Córdoba |
| `santa fe`, `SANTA FE`, `Sta Fe` | Santa Fe |
| `mendoza`, `MENDOZA` | Mendoza |

4. **Fechas:** todas llegaron con formato `DD/MM/AAAA` válido; se convirtieron a tipo fecha. Rango: 01/01/2024 – 10/03/2026.
5. **Números:** las toneladas se convirtieron a número decimal (separador `.` en origen), con 2 decimales visibles.
6. **Columnas añadidas:** `Anio`, `Mes`, `Region` (búsqueda en `catalogo_provincias`) y `Categoria_Volumen` (`=SI()` anidado).
