
## 🌸 API de Clasificación de Flores Iris – Machine Learning

Esta API permite predecir la especie de una flor del género *Iris* a partir de cuatro características morfológicas. Utiliza modelos de clasificación previamente entrenados con el **Iris Dataset**, y está diseñada para ejecutarse en un entorno local o en un entorno distribuido con **Docker**.

## 🏢 Estructura del Proyecto

Este proyecto utiliza **cuatro modelos de clasificación previamente entrenados** con el conjunto de datos Iris. Los modelos empleados incluyen:  
- Regresión Logística  
- Árbol de Decisión  
- Bosque Aleatorio (Random Forest)  
- Máquina de Vectores de Soporte (SVM)

Cada modelo está almacenado en un archivo individual con extensión `.h5` o `.pkl`, listo para ser cargado por la API.

La aplicación expone **cuatro endpoints**, uno por cada modelo, permitiendo realizar predicciones con el algoritmo seleccionado:

- `/predict/logistic`  
- `/predict/randomforest`  
- `/predict/svm`  
- `/predict/tree`

Los parámetros de entrada necesarios para realizar una predicción pueden enviarse mediante **query parameters** o en formato **JSON**. Los campos requeridos son:

- `sepal_length`  
- `sepal_width`  
- `petal_length`  
- `petal_width`

# 📁 Estructura de carpetas


```
/machine__learning_api/
│
├── models/
│   ├── model_logistic.h5       # Modelo de Regresión Logística
│   ├── model_forest.h5         # Modelo de Bosque Aleatorio
│   ├── model_svm.h5            # Modelo de SVM
│   ├── model_tree.h5           # Modelo de Árbol de Decisión
│
├── app.py                      # Script principal que lanza la API Flask
├── iris_models.py              # Lógica para cargar y utilizar los modelos
└── requirements.txt            # Lista de dependencias necesarias
```

## 🧰 Tecnologías y herramientas utilizadas

- Python 3.x  
- Scikit-learn  
- Flask  
- Pandas, NumPy  
- Modelos guardados en formato `.h5` o `.pkl`  
- Docker (opcional)
