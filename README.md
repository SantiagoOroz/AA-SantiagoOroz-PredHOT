# Predicción de la Tasa de Ocupación Hotelera y de Plazas en Tierra del Fuego

<a target="_blank" href="https://cookiecutter-data-science.drivendata.org/">
    <img src="https://img.shields.io/badge/CCDS-Project%20template-328F97?logo=cookiecutter" />
</a>

Este repositorio contiene la estructura base para un proyecto de Machine Learning centrado en la predicción de la Tasa de Ocupación Hotelera (TOH%) y la Tasa de Ocupación de Plazas (TOP%) mensual en las ciudades de Ushuaia y Río Grande, Tierra del Fuego. El objetivo es utilizar técnicas avanzadas de aprendizaje automático e integrar datos de clima, transporte terrestre/aéreo y variables temporales.

## Descripción del Proyecto

El turismo es un pilar fundamental en la economía de Tierra del Fuego, contribuyendo con el 25% del PIB provincial. La ocupación hotelera presenta fluctuaciones significativas debido a factores como el clima extremo, la estacionalidad turística y eventos imprevistos. Este proyecto busca superar las limitaciones de los métodos tradicionales (ej. promedios históricos) mediante el desarrollo de un modelo de regresión no lineal que prediga la TOH% y TOP% con precisión.

El modelo propuesto es XGBoost Regressor, reconocido por su capacidad para manejar relaciones no lineales y datos tabulares, incluso con valores faltantes. Esto lo diferencia de los análisis estadísticos tradicionales que a menudo asumen relaciones lineales.

## Definición de Variables Objetivo

* **TOH% (Tasa de Ocupación Hotelera):** Porcentaje de habitaciones ocupadas en los hoteles durante un mes específico. Por ejemplo, si un hotel tiene 100 habitaciones y 80 están ocupadas, el TOH% es 80%.
* **TOP% (Tasa de Ocupación de Plazas):** Porcentaje de camas o plazas ocupadas en los hoteles durante un mes. Considera la capacidad total de personas que pueden alojarse, no solo las habitaciones. Por ejemplo, si un hotel tiene 200 plazas y 150 están ocupadas, el TOP% es 75%.

## Pipeline de Aprendizaje Automático (Propuesto)

1.  **Integración de Datos:** Unificación de datasets de meteorología (temperatura, precipitaciones, días con nieve), transporte terrestre (entrada de personas por San Sebastián) y aéreo (desembarco en aeropuertos de Ushuaia y Río Grande), junto con TOH% y TOP% históricos.
2.  **Preprocesamiento:** Normalización de variables numéricas (StandardScaler) y codificación de variables temporales (mes como variable cíclica).
3.  **Entrenamiento y Validación:** Split temporal (Entrenamiento: 2009-2019, Validación: 2020-2021, Test: 2022). Métricas: RMSE, MAE, $R^2$ ajustado. Optimización de hiperparámetros mediante búsqueda grid.

## Estructura del Repositorio

La plantilla de este proyecto está diseñada para organizar el flujo de trabajo de Machine Learning de manera clara y eficiente.

La plantilla de este proyecto está diseñada para organizar el flujo de trabajo de Machine Learning de manera clara y eficiente.

`````
├── data/                  # Almacena datos del proyecto
│   ├── raw/               # Datos originales (no modificados) de entrada (ej. meteorología, transporte, TOH/TOP histórico)
│   └── processed/         # Datos limpios y preprocesados, listos para el modelado
├── notebooks/             # Cuadernos Jupyter para exploración de datos, prototipado y análisis interactivo
├── models/                # Modelos de Machine Learning entrenados y serializados
├── reports/               # Informes, presentaciones, gráficos y visualizaciones de resultados
├── src/                   # Código fuente de Python organizado en módulos
│   ├── init.py        # Hace que 'src' sea un paquete Python
│   ├── data_processing.py # Scripts para unificación y preprocesamiento de datos
│   └── model_training.py  # Scripts para el entrenamiento y evaluación del modelo (XGBoost)
├── tests/                 # Pruebas unitarias para asegurar la calidad del código
├── .gitignore             # Archivo para ignorar directorios y archivos específicos en Git (ej. datos grandes, modelos)
├── LICENSE.md             # Información sobre la licencia del proyecto
├── requirements.txt       # Lista de dependencias de Python necesarias para ejecutar el proyecto
└── README.md              # Descripción general del proyecto y su estructura
`````
