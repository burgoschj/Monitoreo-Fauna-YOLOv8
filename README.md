# Monitoreo de Fauna con YOLOv8

## 1. Descripción del proyecto

Proyecto académico de visión por computadora orientado a la detección de fauna en imágenes mediante modelos de detección de objetos de la familia YOLOv8.

El sistema procesa imágenes de cámaras trampa para detectar animales y otras categorías incluidas en el conjunto de datos. Las detecciones generadas se utilizan para evaluar el rendimiento del modelo y realizar análisis exploratorios por especie, imagen y franja horaria.

El proyecto se desarrolla en **Google Colab**, utiliza **Google Drive** para el almacenamiento persistente y mantiene en GitHub el notebook y la documentación del trabajo.

## 2. Objetivos

- Preparar un conjunto de imágenes anotadas en formato YOLO.
- Entrenar y evaluar detectores de objetos basados en YOLOv8.
- Comparar el rendimiento en ubicaciones conocidas y en ubicaciones no vistas durante el entrenamiento.
- Analizar las diferencias de rendimiento entre clases y tamaños de objetos.
- Generar tablas y resúmenes de las detecciones para explorar posibles patrones de actividad.
- Documentar el procedimiento experimental y sus limitaciones para facilitar la reproducibilidad.

## 3. Dataset

Se utiliza el conjunto de datos ECCV Camera Traps, con anotaciones preparadas para el entrenamiento y la evaluación del detector.

El conjunto de datos preparado contiene **15 clases**:

`badger`, `bird`, `bobcat`, `car`, `cat`, `coyote`, `deer`, `dog`, `fox`, `opossum`, `rabbit`, `raccoon`, `rodent`, `skunk` y `squirrel`.

### Distribución de imágenes

| Subconjunto | Imágenes |
|---|---:|
| Entrenamiento (`train`) | 12.099 |
| Validación en ubicaciones conocidas (`val_cis`) | 1.665 |
| Evaluación en ubicaciones no vistas (`val_trans`) | 1.533 |

El procesamiento registrado incluyó la conversión de las anotaciones al formato YOLO, con 12.617 cajas válidas en entrenamiento, 1.763 en `val_cis` y 1.673 en `val_trans`.

Las imágenes, anotaciones originales y condiciones de uso deben consultarse en las fuentes oficiales del dataset antes de redistribuir estos materiales.

## 4. Metodología

El procedimiento de trabajo comprende las siguientes etapas:

1. Preparación de imágenes y anotaciones.
2. Conversión y organización del dataset en formato YOLO.
3. Entrenamiento de los modelos y ejecución de experimentos.
4. Evaluación mediante precisión (*precision*), exhaustividad (*recall*), mAP@50 y mAP@50–95.
5. Evaluación adicional en ubicaciones no vistas durante el entrenamiento.
6. Análisis del rendimiento por clase y por tamaño de objeto.
7. Generación de detecciones y resúmenes exploratorios por especie.
8. Documentación de resultados, limitaciones y conclusiones.

## 5. Resultados experimentales

### 5.1. Evaluación en ubicaciones conocidas

Los resultados registrados para `val_cis` fueron los siguientes:

| Modelo | Precisión | Recall | mAP@50 | mAP@50–95 |
|---|---:|---:|---:|---:|
| `entrenamiento_v1` | 0,850 | 0,696 | 0,774 | 0,504 |
| `experimento_416` | 0,858 | 0,755 | 0,814 | 0,536 |

En esta evaluación, `experimento_416` obtuvo mejores valores en las cuatro métricas registradas. Estos resultados describen el rendimiento en ubicaciones conocidas y no deben interpretarse como una garantía de rendimiento en otras ubicaciones.

### 5.2. Evaluación en ubicaciones no vistas

La comparación registrada para `val_trans`, evaluada con tamaño de inferencia de 416 píxeles, fue:

| Experimento | Precisión | Recall | mAP@50 | mAP@50–95 |
|---|---:|---:|---:|---:|
| `experimento_320` | 0,466 | 0,383 | 0,408 | 0,272 |
| `experimento_416` | 0,380 | 0,458 | 0,362 | 0,229 |

En esta evaluación, `experimento_320` obtuvo mejores valores de precisión y mAP, mientras que `experimento_416` obtuvo mayor recall. La elección del modelo depende, por tanto, del equilibrio deseado entre las detecciones correctas, la cobertura de objetos y la métrica de evaluación priorizada.

Los nombres de los experimentos se mantienen tal como aparecen en los registros. Las métricas de ambas evaluaciones deben interpretarse considerando el subconjunto, el modelo y la configuración utilizados.

### 5.3. Análisis complementarios

El proyecto incluye análisis exploratorios adicionales:

- Rendimiento por clase.
- Detección según el tamaño de los objetos.
- Exploración de oclusiones.
- Visualización e inspección mediante Grad-CAM.
- Resúmenes de detecciones por especie, imagen y franja horaria.

Estos análisis tienen alcances y tamaños muestrales diferentes. En particular, el análisis de oclusión se realizó sobre una muestra reducida de 18 objetos, por lo que sus resultados son exploratorios y no permiten establecer conclusiones generales.

## 6. Tecnologías

- Python
- Google Colab
- Google Drive
- PyTorch
- Ultralytics YOLOv8
- Pandas
- Herramientas de visualización y análisis de datos

## 7. Ejecución del proyecto

El notebook principal de consulta y revisión de resultados es:

[`notebooks/Monitoreo_Fauna_YOLOv8_limpio.ipynb`](notebooks/Monitoreo_Fauna_YOLOv8_limpio.ipynb)

Para utilizarlo:

1. Abre el notebook desde GitHub o mediante Google Colab.
2. Ejecuta la preparación del entorno y conecta Google Drive.
3. Verifica que existan las rutas del dataset, los modelos y los resultados guardados.
4. Consulta las métricas de evaluación y los informes de monitoreo ecológico disponibles.

El notebook está preparado para consultar resultados existentes. La inferencia nueva está desactivada por defecto y no es necesario volver a entrenar los modelos para revisar los informes guardados.

Las rutas del proyecto corresponden a la estructura configurada en Google Drive y pueden requerir ajustes si se utiliza otra cuenta o ubicación de almacenamiento.

## 8. Estructura del proyecto

La organización de referencia en Google Drive es:

```text
Monitoreo_Fauna_YOLOv8/
├── 00_datos_originales/
├── 01_datos_yolo/
├── 02_modelos/
│   ├── entrenamiento_v1/
│   └── experimento_416/
├── 03_resultados/
│   └── monitoreo_ecologico/
├── 04_informes/
└── 05_registros/
```

El repositorio de GitHub contiene el notebook y la documentación. El dataset, los pesos entrenados y los resultados voluminosos se conservan en Google Drive y no se incluyen directamente en GitHub.

## 9. Alcance y limitaciones

El rendimiento de los detectores puede variar según la ubicación de las cámaras, el tamaño de los animales, las condiciones de iluminación, las oclusiones y las diferencias entre los datos de entrenamiento y los de evaluación.

Las detecciones automáticas son predicciones del modelo, no un conteo definitivo de individuos. La cantidad de detecciones no equivale necesariamente a abundancia poblacional, ya que un mismo animal puede aparecer en múltiples imágenes y no todos los individuos tienen la misma probabilidad de ser detectados.

Los análisis de actividad temporal deben interpretarse como exploratorios y considerando la disponibilidad de imágenes, el funcionamiento de las cámaras, los posibles sesgos de muestreo y los errores de detección y clasificación.

## 10. Reproducibilidad y uso de los datos

El proyecto utiliza Google Colab como entorno de ejecución y Google Drive como almacenamiento persistente. Para reproducir los experimentos es necesario disponer de los datos, las anotaciones, los pesos correspondientes y las configuraciones utilizadas en cada evaluación.

Antes de redistribuir datos o modelos, deben revisarse las licencias y condiciones de uso de sus fuentes originales.

## 11. Estado del proyecto

Proyecto académico con modelos entrenados, evaluaciones registradas, análisis complementarios y un notebook organizado para consultar los resultados existentes. La documentación continúa orientada a mejorar la trazabilidad experimental y la reproducibilidad del procedimiento.

## 12. Repositorio

GitHub: https://github.com/burgoschj/Monitoreo-Fauna-YOLOv8
