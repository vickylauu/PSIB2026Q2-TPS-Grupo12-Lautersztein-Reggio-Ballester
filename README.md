# PSIB2026Q2 · TPS · Grupo 12

**Caracterización de la carga cognitiva mediante análisis espectral del EEG durante aritmética mental**

16.63 Procesamiento de Señales e Imágenes Biomédicas · ITBA · 2026 Q2

Integrantes: Victoria Lautersztein (62437), María Reggio (62303), Rosario Ballester (62648)

## Descripción del proyecto

Este proyecto tiene como objetivo caracterizar las variaciones en la actividad cerebral asociadas a la carga cognitiva mediante el análisis espectral de señales de electroencefalografía (EEG).

Se utiliza la base de datos [EEG During Mental Arithmetic Tasks](https://doi.org/10.13026/C2JQ1P) de PhysioNet, que contiene registros de 36 participantes durante dos condiciones experimentales: reposo con ojos cerrados y realización de cálculos mentales.

El análisis se centra en las variaciones de potencia de los ritmos cerebrales delta, theta, alfa y beta, su distribución espacial y su posible relación con el desempeño durante la tarea.

## Objetivos

- Cuantificar las diferencias de potencia espectral entre reposo y cálculo mental.
- Analizar la potencia absoluta y relativa de las bandas de frecuencia y los índices theta/alfa y theta/beta.
- Caracterizar la distribución regional de los cambios mediante mapas topográficos.
- Evaluar la significancia estadística de las diferencias intra-sujeto y entre grupos de desempeño.
- Analizar la influencia del preprocesamiento y los métodos de estimación espectral sobre los resultados.

## Estructura del proyecto

El procesamiento se organiza en cuatro módulos:

### Módulo 1 — Contextualización y preprocesamiento
Caracterización de los registros EEG, verificación espectral del preprocesamiento original, evaluación exploratoria de la calidad de las señales y segmentación temporal.

### Módulo 2 — Análisis de ritmos cerebrales
Estimación de la densidad espectral de potencia (PSD), cálculo de potencias absolutas y relativas por banda y obtención de los índices theta/alfa y theta/beta.

### Módulo 3 — Mapas topográficos y análisis estadístico
Visualización espacial de las variaciones espectrales, análisis regional y comparaciones estadísticas mediante las pruebas de Wilcoxon y Mann-Whitney, con corrección FDR y tamaños de efecto.

### Módulo 4 — Análisis de sensibilidad metodológica
Comparación de los métodos de estimación espectral (Welch, periodograma, Blackman-Tukey y modelos autorregresivos) y evaluación de su influencia sobre las características espectrales y los resultados estadísticos.

## Herramientas utilizadas

- **Lenguaje:** Python 3
- **Procesamiento y análisis:** NumPy, SciPy, Pandas
- **Visualización:** Matplotlib, MNE-Python
- **Estadística:** SciPy, statsmodels
- **Entorno de desarrollo:** Google Colab

## Base de datos

Zyma et al. (2018). *EEG During Mental Arithmetic Tasks*. PhysioNet.

**DOI:** https://doi.org/10.13026/C2JQ1P

## Autoras

- Victoria Lautersztein
- María Reggio
- Rosario Ballester

**Instituto Tecnológico de Buenos Aires (ITBA) — 2026**

| Módulo | Contenido | Estado |
|---|---|---|
| 1 | Contextualización, verificación del preprocesamiento, diseño de filtros y segmentación en épocas | Hecho |
| 2 | Análisis de ritmos cerebrales (PSD: periodograma, Welch, Blackman-Tukey, AR) y potencia por banda | Hecho |
| 3 | Mapas topográficos y análisis estadístico | Hecho |
| 4 | Análisis de sensibilidad metodológica | Pendiente |
