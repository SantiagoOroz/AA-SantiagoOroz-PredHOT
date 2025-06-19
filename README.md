# Predicción de la Tasa de Ocupación Hotelera y de Plazas en Tierra del Fuego

<a target="_blank" href="https://cookiecutter-data-science.drivendata.org/">
    <img src="https://img.shields.io/badge/CCDS-Project%20template-328F97?logo=cookiecutter" />
</a>

Este repositorio contiene la estructura base para un proyecto de Machine Learning centrado en la predicción de la Tasa de Ocupación Hotelera (TOH%) y la Tasa de Ocupación de Plazas (TOP%) mensual en las ciudades de Ushuaia y Río Grande, Tierra del Fuego. El objetivo es utilizar técnicas avanzadas de aprendizaje automático e integrar datos de clima, transporte terrestre/aéreo y variables temporales.
  
Video explicando todo el proyecto: [enlace al video](https://drive.google.com/file/d/1oyp6yUB_TXYK7mxjjqIG3RwDrH2tRaWK/view?usp=sharing)

## Abstract (english)
This project uses Machine Learning (a type of artificial intelligence) to predict hotel and bed occupancy rates in Ushuaia and Río Grande, which are vital tourist spots where fluctuating tourist arrivals and limited tourism data make occupancy planning difficult. The goal is to support proactive planning and resource management in the hotel sector. These models can estimate future occupancy accurately. The official data, including weather and transport figures, was prepared using KNIME and Python. Missing values were filled using Machine Learning methods. Four XGBoost models were built. Data was split for training and testing. The settings were optimized for robustness. The models showed strong predictive power (with R2 Scores between 0.88 and 0.94). Also, low RMSE and MAPE values confirmed consistent accuracy. “Air travelers” numbers significantly influenced Ushuaia's occupancy, while the "year" was key for Río Grande. These validated Machine Learning models provide valuable tools for strategic tourism management. They should help with resource optimization and decision-making by anticipating demand. Future work could explore adapting these models for real-time predictions, allowing for immediate insights into occupancy changes.

## Abstract (español)
Este proyecto utiliza aprendizaje automático (un tipo de inteligencia artificial) para predecir las tasas de ocupación hotelera y de camas en Ushuaia y Río Grande. Estas ciudades son puntos turísticos vitales donde la fluctuación de las llegadas de turistas y la limitada disponibilidad de datos turísticos dificultan la planificación de la ocupación. El objetivo es apoyar la planificación proactiva y la gestión de recursos en el sector hotelero. Estos modelos pueden estimar con precisión la ocupación futura. Los datos oficiales, incluidas las cifras meteorológicas y de transporte, se prepararon utilizando KNIME y Python. Los valores faltantes se completaron utilizando métodos de aprendizaje automático. Se construyeron cuatro modelos XGBoost. Los datos se dividieron para entrenamiento y prueba, y la configuración se optimizó para garantizar la solidez. 
Los modelos mostraron un fuerte poder predictivo, con valores de R2 entre 0.88 y 0.94. Además, los bajos valores de RMSE y MAPE confirmaron una precisión constante. El número de "viajeros aéreos" influyó significativamente en la ocupación de Ushuaia, mientras que el "año" fue clave para Río Grande.

## Descripción del Proyecto

El turismo es un pilar fundamental en la economía de Tierra del Fuego, contribuyendo con el 25% del PIB provincial. La ocupación hotelera presenta fluctuaciones significativas debido a factores como el clima extremo, la estacionalidad turística y eventos imprevistos. Este proyecto busca superar las limitaciones de los métodos tradicionales (ej. promedios históricos) mediante el desarrollo de un modelo de regresión no lineal que prediga la TOH% y TOP% con precisión.

El modelo propuesto es XGBoost Regressor, reconocido por su capacidad para manejar relaciones no lineales y datos tabulares, incluso con valores faltantes. Esto lo diferencia de los análisis estadísticos tradicionales que a menudo asumen relaciones lineales.


## Estructura del Repositorio

La plantilla de este proyecto está diseñada para organizar el flujo de trabajo de Machine Learning de manera clara y eficiente.

La plantilla de este proyecto está diseñada para organizar el flujo de trabajo de Machine Learning de manera clara y eficiente.

`````
├── data/                  # Almacena datos del proyecto
│   ├── raw/               # Datos originales (no modificados) de entrada (ej. meteorología, transporte, TOH/TOP histórico)
│   └── processed/         # Datos limpios y preprocesados, listos para el modelado
├── docs/                  # Documentación adicional (si aplica)
│   └── images/            # Imágenes para READMEs u otra documentación
├── notebooks/             # Cuadernos Jupyter para exploración de datos, prototipado y análisis interactivo
├── models/                # Modelos de Machine Learning entrenados y serializados
├── reports/               # Informes, presentaciones, gráficos y visualizaciones de resultados
├── src/                   # Código fuente de Python organizado en módulos
│   ├── init.py            # Hace que 'src' sea un paquete Python
│   ├── data_processing.py # Scripts para unificación y preprocesamiento de datos
│   └── model_training.py  # Scripts para el entrenamiento y evaluación del modelo (XGBoost)
├── tests/                 # Pruebas unitarias para asegurar la calidad del código
├── .gitignore             # Archivo para ignorar directorios y archivos específicos en Git (ej. datos grandes, modelos)
├── LICENSE.md             # Información sobre la licencia del proyecto
├── requirements.txt       # Lista de dependencias de Python necesarias para ejecutar el proyecto
└── README.md              # Descripción general del proyecto y su estructura
`````

## Definición de Variables Objetivo

* **TOH% (Tasa de Ocupación Hotelera):** Porcentaje de habitaciones ocupadas en los hoteles durante un mes específico. Por ejemplo, si un hotel tiene 100 habitaciones y 80 están ocupadas, el TOH% es 80%.
* **TOP% (Tasa de Ocupación de Plazas):** Porcentaje de camas o plazas ocupadas en los hoteles durante un mes. Considera la capacidad total de personas que pueden alojarse, no solo las habitaciones. Por ejemplo, si un hotel tiene 200 plazas y 150 están ocupadas, el TOP% es 75%.
