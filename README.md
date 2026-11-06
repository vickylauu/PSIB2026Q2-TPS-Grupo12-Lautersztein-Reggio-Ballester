# PSIB2026Q2 · TPS · Grupo 12

**Caracterización de la carga cognitiva mediante análisis espectral del EEG durante aritmética mental**

16.63 Procesamiento de Señales e Imágenes Biomédicas · ITBA · 2026 Q2

Integrantes: Victoria Lautersztein (62437), María Reggio (62303), Rosario Ballester (62648)

## Descripción

Análisis espectral del EEG para cuantificar los cambios en los ritmos cerebrales (delta, theta, alfa, beta) entre reposo y cálculo mental, por región del cuero cabelludo, y evaluar su significancia estadística y su relación con el desempeño en la tarea. Como objetivo secundario, se estudia cuánto dependen los resultados del filtro y del estimador de la PSD elegidos.

## Datos

*EEG During Mental Arithmetic Tasks* v1.0.0 (Zyma et al., PhysioNet, doi:10.13026/C2JQ1P): 36 sujetos, 19 canales del sistema 10-20, 500 Hz, un registro de reposo (`SubjectNN_1.edf`) y uno de cálculo mental (`SubjectNN_2.edf`) por sujeto. Según `subject-info.csv`, 26 sujetos tienen buen desempeño (grupo G) y 10 bajo (grupo B).

Los datos **no se incluyen en el repositorio**. El primer notebook los descarga automáticamente de PhysioNet en la carpeta `eegmat/`.

## Estructura

```
notebooks/
  01_contextualizacion_preprocesamiento.ipynb  Módulo 1: contextualización, verificación de los filtros de la base,
                                               diseño de filtros FIR/IIR y segmentación en épocas
  02_ritmos_cerebrales.ipynb                   Módulo 2: PSD con 4 estimadores (periodograma, Welch, Blackman-Tukey,
                                               AR con orden por AIC) y potencia por banda
  03_mapas_estadistica.ipynb                   Módulo 3: índices θ/α y θ/β, mapas topográficos, Wilcoxon (por
                                               electrodo y región), Mann-Whitney G vs. B y corrección FDR
requirements.txt                               Dependencias
```

Los notebooks se suben **ejecutados**, así que los resultados se pueden ver sin correrlos.

## Flujo de datos entre notebooks

Cada módulo guarda su salida en la carpeta de trabajo y el siguiente la lee:

| Notebook | Lee | Genera |
|---|---|---|
| 01 | `eegmat/*.edf`, `eegmat/subject-info.csv` | `modulo1_epocas.npz` (épocas de 4 s y marca de atípicas), `modulo1_sujetos.csv` |
| 02 | `modulo1_epocas.npz`, `modulo1_sujetos.csv` | `modulo2_potencias.csv` (potencia por sujeto, condición, canal y banda) |
| 03 | `modulo2_potencias.csv`, `modulo1_sujetos.csv` | `modulo3_metricas.csv`, `modulo3_diferencias.csv` (métricas y cambio tarea − reposo), `modulo3_wilcoxon.csv`, `modulo3_wilcoxon_regiones.csv`, `modulo3_mannwhitney.csv` (resultados de los tests) |

## Instalación y ejecución

**Opción 1: Google Colab (recomendada).** Correr los notebooks **en orden y en la misma sesión** (Entorno de ejecución → Ejecutar todas en cada uno). La primera celda del notebook 01 instala MNE y descarga la base (~180 MB). Los archivos intermedios se borran al cerrar la sesión de Colab: para conservarlos, montar Google Drive y trabajar en una carpeta de Drive, o subir a mano los archivos que pide cada notebook.

**Opción 2: local**, con Python 3.10 o superior:

```bash
pip install -r requirements.txt
cd notebooks
jupyter notebook
```

y ejecutar 01 → 02 → 03 en orden. La descarga usa `wget`; si no está disponible (por ejemplo, en macOS), bajar la base desde https://physionet.org/content/eegmat/1.0.0/ y descomprimirla en `notebooks/eegmat/`.

Tiempo aproximado: 01 ≈ 1 min (más la descarga), 02 ≈ 15 s, 03 ≈ 30 s.

## Estado

| Módulo | Contenido | Estado |
|---|---|---|
| 1 | Contextualización, verificación del preprocesamiento, diseño de filtros y segmentación en épocas | Hecho |
| 2 | Análisis de ritmos cerebrales (PSD: periodograma, Welch, Blackman-Tukey, AR) y potencia por banda | Hecho |
| 3 | Mapas topográficos y análisis estadístico | Hecho |
| 4 | Análisis de sensibilidad metodológica | Pendiente |
