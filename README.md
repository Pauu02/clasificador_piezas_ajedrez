# Clasificador de piezas de ajedrez mediante Redes Neuronales

Proyecto de **clasificación de imágenes** desarrollado con **Python y PyTorch** para identificar automáticamente diferentes piezas de ajedrez.

El proyecto comenzó con una CNN desarrollada desde cero y evolucionó hacia el uso de modelos preentrenados mediante *transfer learning* y *fine-tuning*. El modelo final utiliza **ResNet50** y alcanza una **accuracy del 94,66 %** sobre el conjunto de test.

## Tecnologías

* Python
* PyTorch
* Torchvision
* NumPy
* Jupyter Notebook
* Deep Learning
* Computer Vision

## Dataset

El dataset contiene imágenes correspondientes a **6 clases de piezas de ajedrez**.

Los datos se dividieron en:

* 70 % para entrenamiento
* 10 % para validación
* 20 % para test

Durante el entrenamiento se utilizaron diferentes técnicas de *data augmentation*.

## Evolución del proyecto

### V1 - CNN desde cero

Primera CNN desarrollada desde cero, con dos capas convolucionales.

**Accuracy: 48,09 %**

### V2 - Aumento de profundidad

Se añadió una tercera capa convolucional para aumentar la capacidad de representación del modelo.

**Accuracy: 49,62 %**

### V3 - Schedulers

Se probaron diferentes estrategias para ajustar el *learning rate*.

| Versión | Scheduler           |    Accuracy |
| ------- | ------------------- | ----------: |
| V3.1    | `StepLR`            |     47,33 % |
| V3.2    | `ReduceLROnPlateau` | **50,38 %** |

### V4 - Transfer Learning con ResNet18

Se sustituyó la CNN por una **ResNet18 preentrenada en ImageNet**.

* V4.1: Transfer Learning + Data Augmentation: **63,36 %**
* V4.2: Fine-tuning + Dropout + Cosine Annealing + Early Stopping: **86,26 %**

### V5 - ResNet50

Versión final basada en **ResNet50 preentrenada**, realizando *fine-tuning* de las capas `layer3`, `layer4` y `fc`.

También se incorporaron:

* Data augmentation
* `WeightedRandomSampler` para compensar el desbalance entre clases
* Label smoothing
* Dropout
* AdamW
* Cosine Annealing
* Early stopping

**Accuracy: 94,66 %**

## Comparación de resultados

| Versión | Modelo                       |    Accuracy |
| ------- | ---------------------------- | ----------: |
| V1      | CNN                          |     48,09 % |
| V2      | CNN                          |     49,62 % |
| V3.1    | CNN + StepLR                 |     47,33 % |
| V3.2    | CNN + ReduceLROnPlateau      |     50,38 % |
| V4.1    | ResNet18 + Transfer Learning |     63,36 % |
| V4.2    | ResNet18 + Fine-tuning       |     86,26 % |
| **V5**  | **ResNet50 + Fine-tuning**   | **94,66 %** |

## Evaluación

El modelo final se evaluó mediante:

* Accuracy
* Matriz de confusión
* Curvas de Loss y Accuracy durante el entrenamiento

**Accuracy final: 94,66 %**

## Autores

**Paula Santana García**

**Andrés Barroso Soriano**
