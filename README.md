# Proyecto BI - Hito 1: ETL base INDICES pregrado

ETL de la base de matrícula de pregrado (CNED) 2012-2026, integrada con dos fuentes externas: población del INE por región y titulados 2025 del SIES.

## Qué hay en la carpeta

- `ETL_Hito1.ipynb`: el notebook con todo el proceso (carga, integración, limpieza, homologación de puntajes, cruces y diccionario).
- `datos/`: los archivos originales, tal como se descargaron.
- `salida/`: lo que genera el notebook (base limpia, tablas de las fuentes externas y diccionario de datos).

## Cómo ejecutarlo

Se necesita Python 3.11 o más nuevo.

```bash
python3 -m venv .venv
source .venv/bin/activate          # en Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

Después se abre `ETL_Hito1.ipynb` en VS Code (eligiendo el kernel `.venv`) o en Jupyter y se ejecuta todo (Run All). Demora un par de minutos porque el Excel del CNED es grande.

Las rutas son relativas (`datos/` y `salida/`), así que hay que abrir el notebook desde esta carpeta.

## Fuentes

| Archivo | Qué es | Origen | Fecha de descarga |
|---|---|---|---|
| `01_BaseINDICES_Pregrado24.xlsx` | Base del curso, 2012-2022 | Entregada por el curso | No aplica |
| `Base-INDICES-Matricula-2005-2026.xlsx` | Base INDICES del CNED, 2005-2026 | https://cned.cl/wp-content/uploads/2026/08/Base-INDICES-Matricula-2005-2026.xlsx | 20/10/2026 |
| `01_Esquema_Registro_Base_Pregrado.pdf` | Esquema de registro del CNED (qué significa cada columna) | https://cned.cl/wp-content/uploads/2026/08/01_Esquema_Registro_Base_Pregrado.pdf | 20/10/2026 |
| `ine_estimaciones-y-proyecciones-2002-2035_base-2017_region_area_tabulados.xlsx` | INE, estimaciones y proyecciones de población por región 2002-2035 (base 2017) | https://www.ine.gob.cl/docs/default-source/proyecciones-de-poblacion/cuadros-estadisticos/base-2017/ine_estimaciones-y-proyecciones-2002-2035_base-2017_region_area_tabulados.xlsx | 19/10/2026 |
| `TITULADO_2025_web_27_05_2026_E.xlsx` | Titulados 2025 por programa (SIES) | https://www.mifuturo.cl/wp-content/uploads/2026/05/TITULADO_2025_web_27_05_2026_E.xlsx | 19/10/2026 |

## Resultados (`salida/`)

- `base_pregrado_2012_2026.csv`: base integrada y limpia, 158.070 filas.
- `poblacion_ine_region_anio.csv`: población por región y año, 2012-2026.
- `titulados_2025_por_institucion.csv`: matrícula y titulados 2025 por institución.
- `Diccionario_datos.xlsx`: diccionario de datos, nombres por año, fuentes externas, resumen de fuentes y tablas puente.
