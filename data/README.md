# Carpeta `data`

Esta carpeta contiene todos los conjuntos de datos utilizados en el proyecto de Aprendizaje Automático: "Predicción de la Tasa de Ocupación Hotelera y de Plazas en Tierra del Fuego".

La estructura de esta carpeta está diseñada para organizar los datos según su estado de procesamiento, facilitando la trazabilidad y la reproducibilidad del proyecto.

## Contenido de las Subcarpetas:

* **`raw/`**:
    * Contiene los archivos de datos originales (`.xlsx` y sus primeras unificaciones en `.csv`) tal como fueron adquiridos de sus fuentes primarias (Instituto Provincial de Estadística y Censos - IPIEC).
    * Aquí también se encuentran los resultados del preprocesamiento inicial realizado con KNIME.
    * Para más detalles sobre el origen y el preprocesamiento inicial, consulte el `README.md` dentro de la carpeta `raw/`.

* **`processed/`**:
    * Alberga los datasets finales que han sido completamente limpiados, transformados y preparados para el entrenamiento y evaluación de los modelos de Aprendizaje Automático.
    * Estos archivos son el resultado de un preprocesamiento avanzado (incluyendo imputación de valores y One-Hot Encoding) realizado principalmente con Python.
    * Para una descripción detallada de los datasets finales y el proceso de preprocesamiento aplicado, consulte el `README.md` dentro de la carpeta `processed/`.

## Flujo de Datos

Los datos se obtienen inicialmente en formato bruto y se almacenan en `data/raw/`. Luego, pasan por etapas de preprocesamiento (inicialmente en KNIME y luego de forma avanzada en Python) hasta que están limpios y estructurados. Estos datasets procesados finales se guardan en `data/processed/`, desde donde son cargados por los scripts de modelado.

Este enfoque modular garantiza que el flujo de datos sea claro y que cualquier usuario pueda entender fácilmente el estado y la ubicación de los datos en cualquier punto del pipeline del proyecto.
