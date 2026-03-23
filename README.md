# Laboratorio 4 - Mineria de Datos

Arboles de decision y metodos de ensamble aplicados al dataset SmartStay.

## Descripcion

Este laboratorio implementa y compara modelos basados en arboles (arboles de regresion, arboles de clasificacion y Random Forest) para predecir el precio de propiedades tipo Airbnb. Los resultados se contrastan con la regresion lineal del laboratorio anterior.

## Dataset

`data/listings.RData` — Datos de propiedades SmartStay con atributos de anfitrion, disponibilidad, ubicacion y precio por noche.

**Variables objetivo:**
- `price` (continua): precio en USD por noche
- `price_category` (categorica): Low / Intermedia / High, derivada de cuantiles de precio

## Estructura del notebook

`mod/smartStay_decision_tree.ipynb`

1. Limpieza y preprocesamiento de datos
   - Conversion de porcentajes, booleanos y variables ordinales
   - Creacion de flags de valores faltantes e imputacion
2. Analisis exploratorio
3. Arboles de regresion — sin limite de profundidad y con `max_depth` controlado
4. Arboles de clasificacion — modelo base, validacion cruzada (5 folds) y tuneo de profundidad
5. Random Forest — regresor y clasificador
6. Comparacion final de algoritmos

## Resultados

### Regresion (prediccion de precio)

| Modelo | RMSE | R2 |
|---|---|---|
| Regresion lineal (lab anterior) | $3,484 | 0.3481 |
| Arbol de regresion (base) | $1,713 | 0.8424 |
| Random Forest | $1,437 | 0.8891 |

### Clasificacion (categoria de precio)

| Modelo | Accuracy |
|---|---|
| Arbol de clasificacion (base) | 72.0% |
| Arbol de clasificacion (max_depth=20) | 72.8% |
| Random Forest | 79.5% |

Random Forest es el mejor modelo en ambas tareas gracias a la reduccion de varianza por promediado de 100 arboles (parametro de arboles base).

## Dependencias

```
pandas
numpy
matplotlib
seaborn
scipy
scikit-learn
pyreadr
```
