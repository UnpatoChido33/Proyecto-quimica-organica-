
# Análisis gráfico de Química Orgánica

## Proyecto final

Proyecto desarrollado en Python para el análisis estadístico y la visualización de datos químicos relacionados con diez compuestos orgánicos carbonílicos.

El objetivo es estudiar las propiedades fisicoquímicas de las sustancias de referencia y de los compuestos involucrados en sus reacciones de transformación y obtención.

El proyecto utiliza información recopilada en **CAS SciFinder** y almacenada en un archivo Excel, que posteriormente es procesada, normalizada y analizada mediante herramientas de Python.

## Objetivos

- Recopilar información sobre las propiedades fisicoquímicas de diez compuestos orgánicos.
- Analizar reacciones químicas y rutas de obtención asociadas a cada sustancia.
- Identificar tendencias en las propiedades fisicoquímicas de los compuestos.
- Estudiar la relación entre las condiciones experimentales y los tipos de reacción.
- Generar gráficas estadísticas que faciliten la interpretación de los resultados.
- Exportar los datos procesados para su posterior consulta y análisis.

## Compuestos estudiados

El proyecto contempla el análisis de las siguientes sustancias:

1. Acetaldehído.
2. Acetona.
3. Benzaldehído.
4. Ciclohexanona.
5. Butanona.
6. Propanaldehído.
7. Formaldehído.
8. Acetofenona.
9. Benzofenona.
10. Cinamaldehído.

## Propiedades fisicoquímicas

Para cada compuesto se recopilan las siguientes propiedades:

| Propiedad | Abreviatura | Unidad |
|---|---|---|
| Peso molecular | PM | g/mol |
| Punto de fusión | PF | °C |
| Punto de ebullición | PE | °C |
| Densidad | D | g/cm³ |
| Constante de acidez | pKa | Adimensional |
| Momento dipolar | MD | Debye (D) |
| Solubilidad en agua | SA | g/L |
| Presión de vapor | Pv | Pa |

Las propiedades se consultan tanto para las sustancias de referencia como para los productos principales de las reacciones y los reactantes correspondientes a las rutas de obtención.

## Información de las reacciones químicas

La información experimental se obtiene mediante consultas en CAS SciFinder y se organiza en una base de datos Excel.

Para cada reacción u obtención se busca registrar:

- Catalizador o catalizadores.
- Reactivo o reactivos.
- Solvente o solventes.
- Temperatura de reacción.
- Medio de reacción: ácido, básico, neutro o apolar.
- Producto principal, cuando corresponda.
- Nombre de la reacción.
- Tipo de reacción.
- Propiedades fisicoquímicas de las sustancias involucradas.

### Cantidad de registros

El proyecto contempla:

- 10 reacciones por cada sustancia de referencia.
- 10 rutas de obtención por cada sustancia de referencia.

Para diez compuestos, esto corresponde a un objetivo de **200 registros químicos: 100 reacciones y 100 obtenciones**.

Esta cantidad constituye el alcance de la recopilación de información. El programa analiza los registros disponibles en el Excel y no verifica automáticamente que se hayan completado todos los registros requeridos.

## Tecnologías utilizadas

| Biblioteca | Función |
|---|---|
| Python | Lenguaje de programación principal. |
| Pandas | Carga, limpieza, organización y procesamiento de datos tabulares. |
| NumPy | Operaciones numéricas y cálculos estadísticos. |
| Matplotlib | Generación y personalización de gráficos. |
| Seaborn | Visualizaciones estadísticas y análisis gráfico. |
| Regex (`re`) | Normalización y conversión de datos numéricos. |
| OS (`os`) | Creación y administración de directorios. |

El proyecto también utiliza `io`, `unicodedata`, `warnings` y `shutil` para gestionar archivos, normalizar texto, controlar advertencias y comprimir resultados.

## Estructura de los datos

El archivo Excel debe contener información correspondiente a los sustratos, productos, propiedades fisicoquímicas y condiciones de reacción.

Entre las columnas utilizadas por el programa se encuentran:

- Sustrato y producto.
- Número CAS del sustrato y del producto.
- Peso molecular.
- Punto de fusión.
- Punto de ebullición.
- Densidad.
- pKa.
- Momento dipolar.
- Solubilidad en agua.
- Presión de vapor.
- Temperatura de reacción.
- Tiempo de reacción.
- Medio de reacción.
- Tipo de reacción.
- Disolvente.

Los nombres de las columnas se identifican mediante un sistema de correspondencia que permite tolerar algunas variaciones en su escritura.

## Funcionamiento del programa

### 1. Importación de bibliotecas

Se importan las bibliotecas necesarias para realizar la manipulación de datos, los cálculos estadísticos y la generación de gráficas.

### 2. Carga de información

El programa permite trabajar en dos entornos:

- **Google Colab:** solicita al usuario cargar el archivo Excel mediante una ventana de selección.
- **Python local:** intenta cargar el archivo `TABLA REACCIONES PROYECTO DE QUIMICA.xlsx` desde el directorio de trabajo.

Posteriormente, se crea una carpeta denominada `figuras`, donde se almacenan las visualizaciones generadas.

### 3. Limpieza y normalización de datos

Se implementan funciones para mejorar la consistencia de los datos recopilados.

Las principales operaciones incluyen:

- Eliminación de tildes y normalización de texto.
- Conversión de notación científica a valores numéricos.
- Interpretación de temperaturas expresadas como temperatura ambiente.
- Conversión de valores con comas decimales.
- Corrección de algunas diferencias de escala en las propiedades fisicoquímicas.
- Normalización de los medios de reacción.
- Clasificación de los tipos de reacción.
- Simplificación de los nombres de solventes.

Estas operaciones permiten reducir inconsistencias provenientes de diferentes formatos de registro.

### 4. Identificación de compuestos

El programa reconoce los diez compuestos de referencia mediante sus nombres y algunas variantes de escritura.

Se identifican dos roles principales:

- **Reacción:** cuando el compuesto de referencia aparece como sustrato.
- **Obtención:** cuando el compuesto de referencia aparece como producto.

Los registros que no corresponden a ninguno de estos roles se clasifican como otros.

### 5. Consolidación de sustancias

Se combinan los datos de sustratos y productos para construir una tabla de sustancias únicas.

La identificación se realiza mediante el número CAS, con el propósito de evitar duplicaciones en el análisis de correlaciones.

### 6. Análisis estadístico

El programa calcula frecuencias, porcentajes y correlaciones para identificar tendencias en las propiedades químicas y las condiciones experimentales.

Entre los análisis realizados se encuentran:

- Frecuencia de los tipos de reacción.
- Distribución de los medios de reacción.
- Probabilidad condicional del medio según el tipo de reacción.
- Correlación entre peso molecular y punto de ebullición.
- Relación entre presión de vapor y punto de ebullición.
- Relación entre momento dipolar y solubilidad.
- Comparación de puntos de fusión y ebullición.
- Matriz de correlación de Spearman.
- Distribución de temperaturas según el medio de reacción.
- Distribución acumulada de temperaturas.
- Diferencias de peso molecular entre sustratos y productos.

## Gráficas generadas

El proyecto genera doce visualizaciones estadísticas.

| Código | Gráfica | Descripción |
|---|---|---|
| G01 | Frecuencia por tipo de reacción | Compara la cantidad y el porcentaje de cada tipo de reacción. |
| G02 | Medio por sustancia | Representa la distribución porcentual de los medios de reacción. |
| G03 | Sustancia vs. tipo de reacción | Presenta un mapa de calor de los tipos de reacción registrados para cada compuesto. |
| G04 | Probabilidad condicional del medio | Analiza la probabilidad de encontrar un medio determinado según el tipo de reacción. |
| G05 | Peso molecular vs. punto de ebullición | Evalúa la relación entre ambas propiedades mediante una regresión lineal. |
| G06 | Presión de vapor vs. punto de ebullición | Estudia la relación entre volatilidad y temperatura de ebullición. |
| G07 | Momento dipolar vs. solubilidad | Analiza la relación entre polaridad molecular y solubilidad en agua. |
| G08 | Punto de fusión y ebullición | Compara las temperaturas características de las sustancias de referencia. |
| G09 | Matriz de correlación de Spearman | Examina las relaciones estadísticas entre las propiedades fisicoquímicas. |
| G10 | Temperatura por medio de reacción | Compara la distribución de temperaturas entre medios ácido, básico y neutro. |
| G11 | Distribución acumulada de temperatura | Representa la probabilidad acumulada de las temperaturas de reacción. |
| G12 | Diferencia de peso molecular | Compara el cambio de peso molecular entre sustratos y productos. |

### Interpretación estadística

Para las correlaciones se utilizan dos métodos principales:

- **Correlación de Pearson:** empleada para analizar relaciones lineales entre variables.
- **Correlación de Spearman:** empleada para evaluar relaciones monotónicas entre propiedades fisicoquímicas.

En algunas gráficas se utiliza la transformación logarítmica de la presión de vapor y la solubilidad para facilitar la visualización de datos con escalas amplias.

## Archivos de salida

Al finalizar la ejecución, el programa genera los siguientes archivos:

```text
figuras/
├── g01_tipo_reaccion.png
├── g02_medio_por_sustancia.png
├── g03_sustancia_vs_tipo_limpio.png
├── g03_prob_condicional_medio_tipo.png
├── g05_pm_vs_teb.png
├── g06_pv_vs_teb.png
├── g07_dipolo_vs_solubilidad.png
├── g08_tf_teb_referencia.png
├── g09_correlacion.png
├── g10_temp_por_medio.png
├── g11_ecdf_temperatura.png
└── g12_delta_pm.png
```

También se generan:

| Archivo | Descripción |
|---|---|
| `tabla_limpia.csv` | Base de datos original procesada y normalizada. |
| `sustancias_unicas.csv` | Tabla consolidada de sustancias únicas y sus propiedades. |
| `figuras.zip` | Archivo comprimido con las gráficas generadas en Google Colab. |

Los archivos CSV se exportan con codificación UTF-8 compatible con caracteres especiales.

## Requisitos previos

Se recomienda utilizar Python 3.10 o una versión posterior compatible con las bibliotecas utilizadas.

Las dependencias principales pueden instalarse mediante:

```bash
pip install numpy pandas matplotlib seaborn openpyxl
```

`openpyxl` permite leer archivos Excel en formato `.xlsx` mediante Pandas.

## Ejecución del proyecto

### Opción 1: Google Colab

1. Abrir el notebook del proyecto en Google Colab.
2. Ejecutar las celdas en orden.
3. Cuando el programa lo solicite, cargar el archivo Excel con los datos químicos.
4. Esperar a que finalice el procesamiento.
5. Descargar las gráficas y los archivos CSV generados.

### Opción 2: Ejecución local

1. Instalar Python y las bibliotecas requeridas.
2. Ubicar el archivo Python y el Excel en el mismo directorio.
3. Verificar que el Excel tenga el nombre esperado:

   `TABLA REACCIONES PROYECTO DE QUIMICA.xlsx`

4. Ejecutar el programa:

```bash
python analisis_grafico_quimica_organica.py
```

5. Consultar los resultados en la carpeta `figuras` y los archivos CSV generados.

## Consideraciones y limitaciones

- El programa realiza análisis sobre los datos suministrados; no consulta directamente CAS SciFinder.
- La recopilación de información química debe realizarse previamente y organizarse en el Excel.
- La precisión de los resultados depende de la calidad y consistencia de los datos originales.
- Los valores faltantes pueden afectar el número de registros disponibles para cada análisis.
- Las correlaciones estadísticas identifican asociaciones entre variables, pero no demuestran causalidad química.
- La conversión automática de valores y escalas debe verificarse para evitar alteraciones de datos válidos.
- Los resultados dependen de las columnas disponibles y de la correcta identificación de las sustancias.

## Autor

**Moises David Acuña Salas**

Proyecto final de Química Orgánica.

Análisis estadístico y visualización de propiedades fisicoquímicas de compuestos orgánicos mediante Python.
