# Descripción del Proyecto: Comparación y Evaluación de Modelos para Rusty Bargain

## Introducción

En este proyecto, nuestro objetivo es evaluar y comparar varios modelos de aprendizaje automático para predecir una variable objetivo para el negocio **Rusty Bargain**. Se consideran varios modelos de regresión, cada uno con sus fortalezas, debilidades y características únicas. Los modelos probados incluyen **Regresión Lineal**, **Random Forest Regressor**, **CatBoost Regressor**, **LightGBM Regressor** y **XGBoost Regressor**. El objetivo es determinar el modelo más eficaz para la predicción, equilibrando la precisión (medida por RMSE) y la eficiencia (medida por el tiempo de entrenamiento y predicción).

### Objetivo

El objetivo de este proyecto es:
1. Evaluar la precisión predictiva de diferentes modelos de aprendizaje automático.
2. Comparar el rendimiento de los modelos antes y después de la sintonización de los hiperparámetros.
3. Determinar el modelo más adecuado según la precisión, el tiempo de entrenamiento y el tiempo de predicción para la implementación en producción en Rusty Bargain.

## Metodología

El proyecto sigue un proceso estructurado que incluye la preparación de los datos, el entrenamiento de los modelos, la sintonización de los hiperparámetros, la evaluación del rendimiento y la comparación de resultados.

### Preparación de los Datos

Los datos fueron preparados para el modelado mediante:
- **Limpieza y preprocesamiento** de los datos para asegurarse de que fueran adecuados para entrenar los modelos de aprendizaje automático.
- **Selección de características** para reducir la dimensionalidad y garantizar que solo se usen las características relevantes.
- División de los datos en **conjunto de entrenamiento** y **conjunto de prueba** para el entrenamiento y la evaluación del modelo.

### Selección de Modelos

Se seleccionaron cinco modelos de aprendizaje automático para esta evaluación:
1. **Regresión Lineal** – Un modelo simple y fácil de interpretar.
2. **Random Forest Regressor** – Un modelo de ensamblaje que funciona bien con una variedad de tipos de datos.
3. **CatBoost Regressor** – Un modelo de boosting de gradiente conocido por manejar bien las variables categóricas y por su alto rendimiento.
4. **LightGBM Regressor** – Otro modelo de boosting de gradiente, optimizado para velocidad y rendimiento en conjuntos de datos grandes.
5. **XGBoost Regressor** – Un modelo de boosting de gradiente poderoso, comúnmente utilizado en competiciones de Kaggle.

### Sintonización de Hiperparámetros

Para cada modelo, aplicamos **GridSearchCV** para encontrar la mejor combinación de hiperparámetros. Las cuadrículas de hiperparámetros consideradas para cada modelo fueron:
- **Random Forest Regressor**: `n_estimators` (número de árboles) y `max_depth` (profundidad de cada árbol).
- **LightGBM Regressor**: `n_estimators` y `max_depth`.
- **XGBoost Regressor**: `n_estimators` y `max_depth`.
- **CatBoost Regressor**: `iterations` (número de rondas de boosting) y `depth` (profundidad del árbol).

### Métricas de Evaluación

Los modelos fueron evaluados en base a:
- **RMSE (Raíz del Error Cuadrático Medio)**: Una métrica común para los modelos de regresión, donde los valores más bajos indican un mejor rendimiento del modelo.
- **Tiempo de Entrenamiento**: El tiempo que tarda cada modelo en aprender de los datos de entrenamiento.
- **Tiempo de Predicción**: El tiempo que tarda cada modelo en predecir el objetivo en datos no vistos.

### Procedimiento

1. **Entrenar y Evaluar Modelos Base**: Cada modelo fue entrenado sin sintonización de hiperparámetros para establecer una referencia.
2. **Sintonización de Hiperparámetros**: Usando **GridSearchCV**, afinamos los hiperparámetros de los modelos para identificar la configuración óptima para cada uno.
3. **Comparación de Rendimiento**: Comparamos el RMSE, el tiempo de entrenamiento y el tiempo de predicción de los modelos base y ajustados.

## Resultados

### Puntuación RMSE

- **Mejor Desempeño (Ajustado)**: El **CatBoost Regressor** logró la puntuación RMSE más baja de **USD 1604** después de la sintonización, mostrando una mejora significativa desde su puntuación base de **USD 1686**.
- **Segundo Mejor Desempeño**: El **XGBoost Regressor** tuvo una puntuación RMSE base de **USD 1712** y una RMSE ajustada de **USD 1643**, siendo el segundo mejor rendimiento.
- **Tercer Mejor Desempeño**: El **Random Forest Regressor** obtuvo una RMSE de **USD 1697** (base) y **USD 1659** (ajustado).
- **Cuarto Mejor Desempeño**: El **LightGBM Regressor** obtuvo una puntuación RMSE de **USD 1774** (base) y **USD 1679** (ajustado).
- **Peor Desempeño**: **Regresión Lineal** obtuvo el peor rendimiento con una RMSE de **USD 3345**, significativamente más alta que cualquier otro modelo.

### Tiempo de Entrenamiento

- **Más Rápido**: **Regresión Lineal** fue el más rápido para entrenar, tardando solo **0.13 segundos**.
- **Segundo Más Rápido**: **LightGBM Regressor** entrenó en **0.7 segundos** (base) y **0.5 segundos** (ajustado).
- **Moderadamente Rápido**: **XGBoost Regressor** tardó **0.4 segundos** (base) y **0.8 segundos** (ajustado).
- **Más Lento**: **CatBoost Regressor** tardó **13.0 segundos** (base) y **15.1 segundos** (ajustado).
- **El Más Lento**: **Random Forest Regressor** fue el más lento, requiriendo **49.0 segundos** (base) y **17.9 segundos** (ajustado).

### Tiempo de Predicción

- **Más Rápido**: **CatBoost Regressor** fue el más rápido para predecir, tomando **0.01 segundos** (base) y **0.03 segundos** (ajustado).
- **Segundo Más Rápido**: **Regresión Lineal** siguió de cerca con un tiempo de predicción de **0.04 segundos**.
- **Moderadamente Rápido**: **XGBoost Regressor** tardó **0.45 segundos** (base) y **0.82 segundos** (ajustado).
- **Más Lento**: **LightGBM Regressor** tardó **0.74 segundos** (base) y **0.51 segundos** (ajustado).
- **El Más Lento**: **Random Forest Regressor** fue nuevamente el más lento, con tiempos de predicción de **1.63 segundos** (base) y **0.65 segundos** (ajustado).

## Conclusión

### Resumen del Rendimiento del Modelo

- **CatBoost Regressor** demostró el mejor equilibrio entre **precisión (RMSE)** y **eficiencia (tiempo de predicción)**. Con una RMSE ajustada de **USD 1604**, superó a los otros modelos mientras mantenía tiempos de predicción rápidos de **0.03 segundos**.
- **XGBoost Regressor** fue el segundo mejor con una RMSE ajustada de **USD 1643**, pero tuvo tiempos de predicción más altos que CatBoost.
- **Random Forest Regressor** fue el más lento tanto en tiempo de entrenamiento como de predicción, aunque aún logró un buen rendimiento con una RMSE ajustada de **USD 1659**.
- **LightGBM Regressor** fue razonablemente rápido, pero no tuvo un rendimiento tan bueno en términos de precisión en comparación con los otros modelos.
- **Regresión Lineal** tuvo el peor rendimiento en general, con una RMSE significativamente más alta de **USD 3345**.

### Recomendación Final

Basado en la evaluación tanto de **RMSE** como de **eficiencia en tiempo**, el **CatBoost Regressor** es el modelo óptimo para su implementación en Rusty Bargain. Este modelo ofrece la mejor relación entre precisión predictiva y velocidad, lo que lo hace ideal para aplicaciones en tiempo real donde se necesitan predicciones rápidas. Antes de finalizar la implementación, se podría realizar una sintonización adicional para mejorar su rendimiento, especialmente en términos de reducción de la RMSE.

### Consideraciones Futuras

- Se podría realizar una **sintonización adicional de hiperparámetros** en el **CatBoost Regressor** para mejorar aún más el rendimiento, considerando diferentes tasas de aprendizaje y ingeniería de características.
- Se podrían explorar **métodos de ensamblaje** o la combinación de múltiples modelos para mejorar el rendimiento si fuera necesario para el negocio.

Este proyecto identificó con éxito el mejor modelo y proporcionó un análisis detallado de su rendimiento, ofreciendo a Rusty Bargain una herramienta poderosa para el modelado predictivo en sus operaciones comerciales.
