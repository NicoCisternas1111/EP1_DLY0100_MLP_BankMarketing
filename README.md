# EP1 DLY0100 — MLP para predecir la contratación de un depósito a plazo

Evaluación Parcial 1 de **DLY0100 Deep Learning** (Duoc UC). Red neuronal multicapa (MLP) en TensorFlow/Keras que estima, **antes de llamar**, qué clientes de un banco tienen más probabilidad de contratar un depósito a plazo.

**Integrantes:** Nicolás Cisternas · Francisco Gaete · Sebastian Lagos

## Contenido del repositorio

| Archivo | Descripción |
| --- | --- |
| `EP1_DLY0100_MLP_BankMarketing.ipynb` | Notebook completo (informe): EDA, preprocesamiento, experimentos controlados, funciones, optimización, regularización, búsqueda de hiperparámetros, evaluación y conclusiones |
| `bank_marketing.csv` | Dataset entregado por el docente (Bank Marketing, UCI, 45.211 filas) |
| `requirements.txt` | Dependencias para ejecutar en local |
| `EP1_DLY0100_Presentacion.pptx` | Presentación de la defensa |

## Cómo ejecutar

### Google Colab (recomendado)

1. Abrir el notebook en Colab: **Archivo → Abrir cuaderno → GitHub** y pegar la URL de este repositorio.
2. Subir `bank_marketing.csv` al panel de archivos. Si no se sube, el notebook descarga el dataset original desde la UCI.
3. Ejecutar **Entorno de ejecución → Ejecutar todo**.

### Local

```bash
pip install -r requirements.txt
jupyter notebook EP1_DLY0100_MLP_BankMarketing.ipynb
```

### Tiempo de ejecución

La ejecución completa tarda unos 50–70 minutos en CPU (3 semillas por experimento). Para una prueba rápida, en la celda de parámetros globales usar `N_SEEDS = 1` y `EPOCHS = 20`.

El notebook se entrega **con todas las salidas ya ejecutadas**. Las cifras de la presentación corresponden a esa ejecución; una nueva ejecución puede variar en milésimas por diferencias de CPU/GPU o de versión de TensorFlow.

## Resultado principal

Modelo final: MLP 128-64, ReLU, BatchNorm, Dropout 0,2, L2 1e-4, Adam (lr 1e-3), batch 512, pesos de clase, Early Stopping y umbral 0,71 elegido en validación.

| Métrica (conjunto de prueba) | Valor |
| --- | --- |
| F1 | 0,461 |
| Precision | 0,465 |
| Recall | 0,458 |
| PR-AUC | 0,424 |
| F1 en validación cruzada (5 pliegues) | 0,477 ± 0,017 |

Llamando al 20 % de clientes con mayor puntaje se captura el 60 % de las contrataciones (4 veces más eficiente que llamar al azar).

## Referencias

- Moro, S., Cortez, P. y Rita, P. (2014). *A data-driven approach to predict the success of bank telemarketing.* Decision Support Systems, 62, 22–31.
- UCI Machine Learning Repository — Bank Marketing: https://archive.ics.uci.edu/dataset/222/bank+marketing
- Documentación de TensorFlow/Keras: https://www.tensorflow.org/api_docs
- Material de la asignatura DLY0100, unidad EA1 (apuntes 1.1.1 a 1.6.2).
