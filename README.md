# Predicción de Fuga de Clientes 

Este proyecto tiene como objetivo predecir la salida de clientes del banco Beta Bank utilizando modelos de clasificación. El objetivo principal es alcanzar un valor F1 de al menos 0.59 y comparar esta métrica con AUC-ROC.

## Contenido
- Preparación de datos
- Análisis del desbalanceo de clases
- Modelado (modelo base, upsampling, ponderación)
- Evaluación y selección del mejor modelo
- Conclusión

## Dataset
Archivo: `Churn.csv`

### Columnas principales:
- `CreditScore`, `Geography`, `Gender`, `Age`, `Tenure`, `Balance`, `NumOfProducts`, `HasCrCard`, `IsActiveMember`, `EstimatedSalary`
- Objetivo: `Exited` (1 = cliente que se fue, 0 = cliente que se quedó)

## Tecnologías utilizadas
- Python 3
- pandas, numpy
- scikit-learn

## Procedimiento de preparación
1. Eliminación de columnas irrelevantes (`RowNumber`, `CustomerId`, `Surname`)
2. Relleno de valores nulos en `Tenure` con la mediana
3. Codificación de variables categóricas con One-Hot Encoding
4. Escalado de variables numéricas con `StandardScaler`
5. División de datos en entrenamiento y prueba (75/25)

## Manejo del desequilibrio de clases
Se implementaron dos técnicas:
- **Upsampling**: duplicar ejemplos de la clase minoritaria
- **Ponderación de clases**: `class_weight='balanced'` en el modelo

## Modelos entrenados
- Random Forest (modelo base)
- Random Forest con upsampling
- Random Forest con ponderación

## Resultados finales
**Mejor modelo:** Random Forest con ponderación de clases

- F1 para clase 1: `0.56`
- AUC-ROC: Aproximadamente `0.83`
- Accuracy general: `0.86`

**Matriz de confusión:**
```
[[1907   58]
 [ 302  233]]
```

## Conclusión
El modelo logra buenos resultados generales, pero queda ligeramente por debajo del umbral F1 requerido para la clase positiva. Se recomienda:
- Probar XGBoost o GradientBoosting
- Realizar búsqueda de hiperparámetros
- Ajustar el umbral de clasificación para mejorar el recall

## Autor
Proyecto desarrollado como parte del Sprint 6 de Data Science.
