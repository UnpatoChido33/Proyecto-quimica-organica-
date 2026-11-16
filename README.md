# Análisis de Reacciones Químicas Orgánicas y Propiedades Fisicoquímicas

Este repositorio centraliza el flujo de trabajo completo para el procesamiento, análisis estadístico, visualización interactiva y documentación técnica de reacciones químicas orgánicas y propiedades fisicoquímicas de sustratos y productos.

---

## Estructura del Repositorio

El proyecto está organizado en los siguientes entregables principales dentro de la rama `main`:

* `Datos_Reacciones.xlsx`: Base de datos tabular con el registro consolidado de reacciones, condiciones experimentales y propiedades fisicoquímicas (`tabla_limpia.csv` en el modelo semántico).
* `Analisis_graficoV3.ipynb`: Cuaderno de Jupyter (Python) utilizado para la limpieza exploratoria, análisis estadístico y generación de gráficas de correlación.
* `PRESENTACION DE REACCIONES.pbix`: Informe interactivo desarrollado en Microsoft Power BI para la exploración multivariable de mecanismos, solventes y propiedades moleculares.
* `proyecto.pdf`: Documento técnico final compilado con la metodología, análisis de resultados y conclusiones del estudio.
* `proyecto codigo.txt`: Código fuente en LaTeX correspondiente a la maquetación del informe técnico.
* `README.md`: Documentación general y guía de arquitectura del repositorio.

---

## Arquitectura del Modelo en Power BI

El archivo `PRESENTACION DE REACCIONES.pbix` se alimenta de un dataset estructurado de 56 columnas (codificación UTF-8) procesado mediante Power Query y modelado con expresiones DAX:

### 1. Tabla Principal (`tabla_limpia`)
* **Identificación y Clasificación:** `Nombre de reaccion`, `NUMERO CAS SUSTRATO`, `NUMERO CAS PRODUCTO`, `NUMERO CAS REACCION`, `Rol`, `Compuesto`, `Tipo_n` (*Adición nucleofílica, Sustitución radicalaria, Oxidación, Acoplamiento*, entre otros), `Medio_n` y `Solvente_n`.
* **Condiciones Experimentales:** `Reactivo`, `Disolvente`, catalizadores (`C1`, `C2`, `C3`), `Medio`, `Tpr`, `Condicion 1(min)`, `Condicion 2`, temperatura de reacción (`Tr (°C)` / `T_rx`) y tiempo de reacción en escala logarítmica (`t_min`).
* **Propiedades del Sustrato (`_S`):** Peso molecular (`PM_S`), punto de fusión (`Tf_S`), punto de ebullición (`Teb_S`), densidad (`Dens_S`), constante de acidez (`pKa_S`), momento dipolar (`Dip_S`), solubilidad en agua (`Sol_S`) y presión de vapor a 298 K (`Pv_S`).
* **Propiedades del Producto (`_P`) y Variaciones:** Equivalentes fisicoquímicos para el producto (`PM_P`, `Tf_P`, `Teb_P`, `Dens_P`, `pKa_P`, `Dip_P`, `Sol_P`, `Pv_P`) y diferencial de masa molar (`dPM`).

### 2. Tablas Calculadas (DAX)
* **`Sustancias`:** Tabla generada mediante `SUMMARIZE` sobre registros con `Rol = "Reacción"`, agrupando compuestos únicos y calculando la mediana de sus propiedades fisicoquímicas (`PM`, `Punto de fusión`, `Punto de ebullición`, `Densidad`, `pKa`, `Momento dipolar` y `Solubilidad`).
* **`Tipos`:** Tabla de dimensiones (`DATATABLE`) que estandariza las 9 categorías de mecanismos de reacción orgánica.

---

## Vistas del Informe Interactivo

1. **Panel General de Reacciones:**
   * Tarjetas KPI con el conteo de sustratos, productos, reacciones únicas y temperatura promedio.
   * Distribución de frecuencias por mecanismo de reacción (`Tipo_n`).
   * Gráficos de dispersión de condiciones térmicas y temporales (`t_min` vs. `T_rx`) y distribución por solventes (`Solvente_n`) y medios (`Medio_n`).
2. **Comparativa Fisicoquímica (Sustrato vs. Producto):**
   * Gráficos de dispersión cruzada que evalúan el cambio entre sustrato y producto en peso molecular (`PM`), punto de ebullición (`Teb`), momento dipolar (`Dip`) y solubilidad (`Sol`).
   * Análisis de distribución de presión de vapor y densidad segmentado por tipo de mecanismo.
3. **Explorador Detallado de Compuestos y Reacciones:**
   * Matriz tabular con el desglose completo por registro: números CAS, reactivos, catalizadores (`C1–C3`), condiciones experimentales y propiedades individuales.

---

## Requisitos y Reproducibilidad

### Entorno de Análisis (Python)
* **Dependencias:** Python 3.x con librerías estándar de análisis de datos (`pandas`, `numpy`, `matplotlib`, `seaborn`) para ejecutar `Analisis_graficoV3.ipynb`.

### Entorno de Visualización (Power BI)
1. **Software:** Microsoft Power BI Desktop (compatibilidad tabular `1606` o superior).
2. **Vinculación de Datos:**
   * Abrir `PRESENTACION DE REACCIONES.pbix`.
   * Ir a **Transformar datos > Configuración de origen de datos** en Power Query.
   * Actualizar la ruta de origen apuntando al archivo CSV limpio correspondiente en el directorio local.

### Compilación de Documentación (LaTeX)
* El archivo `proyecto codigo.txt` contiene el código fuente completo listo para ser compilado en cualquier distribución TeX estándar (TeX Live, MiKTeX u Overleaf) para regenerar `proyecto.pdf`.

## Autores

**Moises David Acuña Salas, Lenin Mauricio Veloza Plata, Maira Alejandra Candela Useche, Juan Pablo Vargas Pacanchique, Gabriela Alejandra Gonzales Lopez.**
