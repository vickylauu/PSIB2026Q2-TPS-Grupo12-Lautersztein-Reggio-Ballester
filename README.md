# PSIB2026Q2 · TPS · Grupo 12

**Caracterización de la carga cognitiva mediante análisis espectral del EEG durante aritmética mental**

16.63 Procesamiento de Señales e Imágenes Biomédicas · ITBA · 2026 Q2

Integrantes: Victoria Lautersztein (62437), María Reggio (62303), Rosario Ballester (62648)

## Descripción

Análisis espectral del EEG para cuantificar los cambios en los ritmos cerebrales (delta, theta, alfa, beta) entre reposo y cálculo mental, por región del cuero cabelludo, y evaluar su significancia estadística y su relación con el desempeño en la tarea.

## Datos

*EEG During Mental Arithmetic Tasks* v1.0.0 (Zyma et al., PhysioNet, doi:10.13026/C2JQ1P): 36 sujetos, 19 canales del sistema 10-20, 500 Hz, registros de reposo y de cálculo mental.

Los datos **no se incluyen en el repositorio**. El primer notebook los descarga automáticamente de PhysioNet en la carpeta `eegmat/`.

## Estructura

```
notebooks/
  01_contextualizacion_preprocesamiento.ipynb   Módulo 1: contextualización, verificación de filtros y segmentación en épocas
requirements.txt                                Dependencias
```

## Instalación y ejecución

**Opción 1: Google Colab (recomendada).** Abrir el notebook en Colab y ejecutar todas las celdas en orden (Entorno de ejecución → Ejecutar todas). La primera celda instala MNE y descarga la base.

**Opción 2: local**, con Python 3.10 o superior:

```bash
pip install -r requirements.txt
jupyter notebook notebooks/01_contextualizacion_preprocesamiento.ipynb
```

En la ejecución local, la descarga usa `wget`; si no está disponible, bajar la base desde PhysioNet y descomprimirla en `eegmat/`.

## Estado

| Módulo | Contenido | Estado |
|---|---|---|
| 1 | Contextualización, verificación del preprocesamiento y segmentación en épocas | Hecho |
| 2 | Análisis de ritmos cerebrales (PSD: Welch, periodograma, Blackman-Tukey, AR) | Pendiente |
| 3 | Mapas topográficos y análisis estadístico | Pendiente |
| 4 | Análisis de sensibilidad metodológica | Pendiente |
