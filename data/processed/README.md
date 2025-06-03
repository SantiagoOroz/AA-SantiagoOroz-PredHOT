# Descripción de la Carpeta `processed`

La carpeta `processed` contiene los datasets finales que han pasado por todas las etapas de preprocesamiento y están listos para ser utilizados en el entrenamiento y evaluación de modelos de Aprendizaje Automático para la predicción de la Tasa de Ocupación Hotelera y de Plazas en Tierra del Fuego.

## Archivos Contenidos

Esta carpeta contiene los siguientes datasets procesados, listos para el modelado:

* `RG_completo_renombrado.csv`: Dataset final para la predicción de ocupación hotelera en Río Grande, con 23 características.
* `USH_completo_renombrado.csv`: Dataset final para la predicción de ocupación hotelera en Ushuaia, con 23 características.

Estos archivos representan el producto de un preprocesamiento riguroso, asegurando la calidad y el formato adecuado para el entrenamiento de modelos de Aprendizaje Automático.

## Descripción General del Dataset Procesado

El dataset principal utilizado en este proyecto es una compilación de diversas fuentes de datos provinciales de Tierra del Fuego, Argentina. Ha sido consolidado y preprocesado para servir como base para la predicción de variables clave en el ámbito turístico.

* **Número de Instancias (Filas)**: 170
* **Número de Características (Columnas) Iniciales**: 12
* **Número de Características (Columnas) Finales (post-One-Hot Encoding)**: 23
* **Tipos de Datos**: Incluyen valores numéricos (temperaturas, lluvias, personas, porcentajes) y categóricos (meses del año).

A continuación, se presenta una tabla con las características finales del dataset después del preprocesamiento, incluyendo la aplicación de One-Hot Encoding para la variable 'mes':

| Nombre de la Columna        | Tipo de Dato | Origen Original           | Descripción                                                                                                                                                                                                                                                                 |
| :-------------------------- | :----------- | :------------------------ | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| anio                        | int          | Todos los datasets        | Año del registro (2013-2022)                                                                                                                                                                                                                                                |
| mes_Enero                   | int          | Original: mes (object)    | Variable binaria (0 o 1) resultante de One-Hot Encoding para el mes de Enero.                                                                                                                                                                                                                         |
| mes_Febrero                 | int          | Original: mes (object)    | Variable binaria (0 o 1) resultante de One-Hot Encoding para el mes de Febrero.                                                                                                                                                                                                                         |
| ...                         | int          | Original: mes (object)    | Variables binarias similares para todos los meses restantes.                                                                                                                                                                                                                                            |
| temp_media                  | float        | Dataset Meteorología      | Temperatura media promedio (°C)                                                                                                                                                                                                                                             |
| temp_max                    | float        | Dataset Meteorología      | Temperatura máxima media promedio (°C)                                                                                                                                                                                                                                      |
| temp_min                    | float        | Dataset Meteorología      | Temperatura mínima media promedio (°C)                                                                                                                                                                                                                                      |
| lluvia_mm                   | float        | Dataset Meteorología      | Precipitaciones en milímetros                                                                                                                                                                                                                                               |
| dias_nieve                  | int          | Dataset Meteorología      | Días con nieve en el mes                                                                                                                                                                                                                                                    |
| entrada_san_sebastian       | int          | Dataset Transporte Terrestre | Personas entradas por paso fronterizo. Valores ausentes imputados con un modelo Random Forest.                                                                                                                                                                                                        |
| desembarco_aeropuerto_ciudad | int          | Dataset Transporte Aéreo  | Pasajeros desembarcados en aeropuerto local (referente a la ciudad específica, Ushuaia o Río Grande).                                                                                                                                                                        |
| desembarco_aeropuerto_ush   | int          | Dataset Transporte Aéreo  | Pasajeros desembarcados en aeropuerto USH (solo para RG, ya que los movimientos de pasajeros en un aeropuerto pueden influir en la ocupación hotelera de la otra ciudad, dada la proximidad geográfica entre Río Grande y Ushuaia). |
| toh                         | float        | Dataset Turismo           | Tasa de Ocupación Hotelera (%). Valores ausentes para 2009-2010 imputados con la mediana mensual del período 2011-2022.                                                                                                                                                                                                        |
| top                         | float        | Dataset Turismo           | Tasa de Ocupación de Plazas (%). Valores ausentes para 2009-2010 imputados con la mediana mensual del período 2011-2022.                                                                                                                                                                                                           |

## Proceso de Preprocesamiento Aplicado

Los datasets en esta carpeta son el resultado de un exhaustivo proceso de preprocesamiento, que incluyó:

* **Unificación de Datos**: Combinación de datos de diversas fuentes (Meteorología, Turismo, Transporte Aéreo y Terrestre) en una única estructura, realizada manualmente en un archivo Excel (`Columnas_unificadasUSHyRG.xlsx`) debido a los formatos no estándar de los datos originales.
* **División por Ciudad**: Los datos unificados se dividieron en dos archivos CSV, uno para Ushuaia (`Columnas_unificadasUSH.csv`) y otro para Río Grande (`Columnas_unificadasRG.csv`), para facilitar su manejo.
* **Preprocesamiento Inicial con KNIME**: Se realizaron tareas de limpieza y preparación, como el renombrado de columnas y la conversión de tipos de datos, para estandarizar el dataset. Los archivos resultantes de esta etapa están presentes en la carpeta `raw` (`Prepro_AATOH_knime_rg.csv` y `Prepro_AATOH_knime_ush.csv`).
* **Procesamiento Avanzado con Python (Google Colab)**:
    * **Imputación de Valores Ausentes**:
        * Las tasas de ocupación (TOH% y TOP%) para los años 2009-2010, que presentaban ausencia total, fueron imputadas utilizando la mediana mensual del período 2011-2022, dada la estacionalidad del turismo.
        * Los valores ausentes de entradas por San Sebastián para Río Grande fueron imputados utilizando un modelo de Random Forest, adecuado para relaciones no lineales.
    * **Codificación de Variables Categóricas**: La característica 'Mes' fue transformada mediante One-Hot Encoding, convirtiendo una variable categórica en múltiples columnas binarias (0 o 1). Esto es esencial para que los algoritmos de Aprendizaje Automático puedan procesar esta información sin asumir una relación ordinal incorrecta entre los meses.
