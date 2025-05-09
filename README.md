
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

## 📁 Estructura de carpetas


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


## 🏗️ Instalación
 
Clona este repositorio:

```bash
git clone https://github.com/tu_usuario/iris-api.git
cd iris-api
```

Sigue estos pasos para configurar el entorno de desarrollo local con Anaconda y Python:


1. ⚙️ **Crear y activar un entorno virtual con Anaconda**:

```bash
python -m venv venv
source venv/bin/activate  
```
En Windows: ```venv\Scripts\activate```

2. **Navegar en la carpeta del proyecto**: 

```bash
  cd machine__learning_api
```

3. **Instala las dependencias necesarias**:

```bash
pip install -r requirements.txt
```

## 🤖 Modelos de Machine Learning

Para generar y entrenar los modelos de clasificación, ejecuta el siguiente script:

```bash
python iris_models.py
```
La respuesta es la evaluacion del modelo. 

Por ultimo resta levantar el servidor ejecutando:

## 🚀 Iniciar el servidor Flask:

```bash
python app.py
```

La API estará disponible en:

```http://127.0.0.1:5000/```

## 📈 Endpoints disponibles

Cada endpoint corresponde a un modelo de clasificación diferente:

| Método | Endpoint                   | Descripción                                    |
|--------|----------------------------|------------------------------------------------|
| POST   | `/predict/logistic`        | Predicción con Regresión Logística             |
| POST   | `/predict/decision_tree`   | Predicción con Árbol de Decisión               |
| POST   | `/predict/svm`             | Predicción con Máquina de Vectores de Soporte  |
| POST   | `/predict/random_forest`   | Predicción con Bosque Aleatorio                |

## 🧪 Ejemplo de solicitud

```json
POST /predict/logistic
{
  "sepal_length": 5.1,
  "sepal_width": 3.5,
  "petal_length": 1.4,
  "petal_width": 0.2
}
```

## 🐳 **Docker**

Docker es una plataforma para desarrollar, empaquetar y ejecutar aplicaciones dentro de contenedores. Un contenedor es un entorno ligero, portátil y aislado que incluye todo lo necesario para ejecutar una aplicación: código, dependencias, sistema de archivos, etc.

Para ejecutar el proyecto en Docker debemos crear dos archivos, ```Dockerfile``` y ```docker-compues.yml```. 

```Dockerfile ```

```bash
FROM python:3.10

WORKDIR /app

# Copiar archivos
COPY app.py .
COPY models/ ./models/

# Instalar dependencias
RUN pip install flask joblib scikit-learn

EXPOSE 5001

# Comando de inicio
CMD ["python", "app.py"]

```

```docker-compose```

```bash
version: "3.8"

services:
  iris-api:
    build: .
    ports:
      - "5001:5001"
    volumes:
      - ./models:/app/models
 ```

En la estructura del proyecto ya se encuentran, para correr los contenedores ejecutar desde lla carpeta del proyecto, esto ejecutara los contenedores: 

```bash
docker-compose up --build
```

