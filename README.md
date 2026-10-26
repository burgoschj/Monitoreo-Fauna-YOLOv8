# Monitoreo de Fauna con YOLOv8

## 1. Descripción del proyecto

Proyecto académico de visión por computadora orientado al monitoreo de fauna mediante detección de objetos con YOLOv8. El sistema identifica animales en imágenes y genera resultados que permiten analizar la distribución de las detecciones por especie y explorar patrones de actividad.

El proyecto se ejecuta en **Google Colab**, con almacenamiento persistente en Google Drive.

## 2. Objetivos

- Implementar un detector de fauna basado en YOLOv8.
- Preparar y evaluar un conjunto de datos anotado.
- Comparar el rendimiento en ubicaciones conocidas y en ubicaciones no vistas durante el entrenamiento.
- Generar tablas, métricas y visualizaciones para analizar las detecciones.
- Documentar un procedimiento reproducible de ejecución.

## 3. Dataset

Se utiliza un conjunto de imágenes de fauna asociado al proyecto ECCV Camera Traps. El conjunto preparado contiene 15 clases:

`badger`, `bird`, `bobcat`, `car`, `cat`, `coyote`, `deer`, `dog`, `fox`, `opossum`, `rabbit`, `raccoon`, `rodent`, `skunk` y `squirrel`.

La preparación registrada incluye 12.099 imágenes de entrenamiento, 1.665 imágenes de validación de ubicaciones conocidas y 1.533 imágenes de evaluación de ubicaciones no vistas.

Se deben consultar las fuentes y condiciones de uso del dataset antes de redistribuir sus imágenes o anotaciones.

## 4. Metodología

1. Preparación de imágenes y anotaciones en formato YOLO.
2. Entrenamiento y ajuste experimental del detector.
3. Evaluación mediante precisión, recall, mAP@50 y mAP@50–95.
4. Evaluación adicional en ubicaciones no vistas.
5. Generación de detecciones, resúmenes por especie y análisis exploratorio.
6. Elaboración del informe académico.

## 5. Tecnologías

- Python
- Google Colab
- Google Drive
- PyTorch
- Ultralytics YOLOv8
- Pandas y herramientas de visualización

## 6. Ejecución

El procedimiento de instalación y ejecución en Google Colab se documentará en este repositorio cuando se complete la organización del código.

Los pesos entrenados, el dataset y los resultados voluminosos se conservarán en Google Drive; no se incluirán directamente en el repositorio.

## 7. Estructura del proyecto

La estructura definitiva de carpetas y módulos se incorporará una vez organizado y validado el código existente.

## 8. Alcance y limitaciones

El rendimiento puede variar según la ubicación de las cámaras, el tamaño de los animales, las condiciones de iluminación y las oclusiones. Las detecciones automáticas son estimaciones del modelo y no constituyen, por sí solas, evidencia definitiva de abundancia poblacional o comportamiento ecológico.

## 9. Estado del proyecto

Proyecto académico en proceso de organización, validación y documentación para su ejecución reproducible en Google Colab.
# Monitoreo-Fauna-YOLOv8
