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

- **Lenguaje:** Python 3.10 o superior
- **Procesamiento y análisis:** NumPy, SciPy, pandas
- **Visualización:** Matplotlib, MNE-Python
- **Estadística:** SciPy, statsmodels
- **Entorno de desarrollo:** Google Colab

## Base de datos

Zyma et al. (2018). *EEG During Mental Arithmetic Tasks* v1.0.0. PhysioNet. **DOI:** https://doi.org/10.13026/C2JQ1P

36 sujetos, 19 canales del sistema 10-20, 500 Hz; un registro de reposo (`SubjectNN_1.edf`) y uno de cálculo mental (`SubjectNN_2.edf`) por sujeto. Según `subject-info.csv`, 26 sujetos tienen buen desempeño (grupo G) y 10 bajo (grupo B).

Los datos **no se incluyen en el repositorio**: el notebook 01 los descarga automáticamente de PhysioNet en la carpeta `eegmat/`.

## Archivos

```
notebooks/
  01_contextualizacion_preprocesamiento.ipynb  Módulo 1: contextualización, verificación de filtros, diseño FIR/IIR y épocas
  02_ritmos_cerebrales.ipynb                   Módulo 2: PSD con 4 estimadores y potencia por banda
  03_mapas_estadistica.ipynb                   Módulo 3: índices θ/α y θ/β, mapas topográficos, Wilcoxon y Mann-Whitney con FDR
  04_sensibilidad_metodologica.ipynb           Módulo 4: sensibilidad de los resultados al estimador, al filtrado FIR/IIR,
                                               a las épocas marcadas, al denominador de la potencia relativa y a la duración de época
requirements.txt                               Dependencias
```

Los notebooks se suben **ejecutados**, así que los resultados se pueden ver sin correrlos.

## Flujo de datos entre notebooks

| Notebook | Lee | Genera |
|---|---|---|
| 01 | `eegmat/*.edf`, `eegmat/subject-info.csv` | `modulo1_epocas.npz`, `modulo1_sujetos.csv` |
| 02 | `modulo1_epocas.npz`, `modulo1_sujetos.csv` | `modulo2_potencias.csv` |
| 03 | `modulo2_potencias.csv`, `modulo1_sujetos.csv` | `modulo3_metricas.csv`, `modulo3_diferencias.csv`, `modulo3_wilcoxon.csv`, `modulo3_wilcoxon_regiones.csv`, `modulo3_mannwhitney.csv` |
| 04 | `modulo1_epocas.npz`, `modulo1_sujetos.csv`, `modulo2_potencias.csv` (y, si están, los CSV estadísticos del 03) | `modulo4_*.csv` (potencias por método, pruebas por método y controles de robustez) |

## Instalación y ejecución

El proyecto está desarrollado en Python 3 y organizado en cuatro notebooks que deben ejecutarse secuencialmente.

### Dependencias

Las bibliotecas necesarias se encuentran especificadas en el archivo `requirements.txt`.

Para ejecutar el proyecto localmente, clonar el repositorio e instalar las dependencias:

```bash
git clone https://github.com/vickylauu/PSIB2026Q2-TPS-Grupo12-Lautersztein-Reggio-Ballester.git
cd PSIB2026Q2-TPS-Grupo12-Lautersztein-Reggio-Ballester
pip install -r requirements.txt
```

### Ejecución en Google Colab

1. Abrir los notebooks desde la carpeta `notebooks/` en Google Colab.
2. Ejecutarlos en orden, desde el Módulo 1 hasta el Módulo 4.
3. Cargar los archivos solicitados por cada notebook cuando corresponda.
4. Conservar los archivos generados por cada módulo, ya que se utilizan como entrada en los siguientes.

### Ejecución local

Los notebooks también pueden abrirse mediante Jupyter Notebook o JupyterLab, siempre que se encuentren instaladas las dependencias correspondientes.

Para ejecutar localmente, se deben disponer de los archivos de entrada y adaptar las celdas de carga específicas de Google Colab cuando sea necesario.

## Autoras

- Victoria Lautersztein (62437)
- María Reggio (62303)
- Rosario Ballester (62648)

**Instituto Tecnológico de Buenos Aires (ITBA) — 2026**
